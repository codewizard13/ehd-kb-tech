# AIX / RS/6000 Help Desk Field Guide

> **Modern reference edition:** 2026-09-26  
> Recreated from the historical `helpfuld.md` / `eh_helpfuld_r071701.01.html` notes.

This is a practical, searchable reference for maintaining legacy IBM AIX / RS/6000 environments. The source was written for a specific IBM site and era; hostnames, paths, support queues, phone numbers, passwords, and internal URLs are therefore not assumed to work today.

## How to use this guide

- **Read-only first:** run inspection commands before changing a system.
- **Root required:** commands that change filesystems, accounts, ACLs, daemons, boot settings, or caches must be reviewed and run by an authorized administrator.
- **Legacy warning:** AFS, DFS/DCE, VM, X11, `rsh`, `telnet`, and several vendor tools are obsolete or site-specific. Prefer SSH, TLS-based transfer, modern identity systems, and current vendor documentation on maintained systems.
- **Verify syntax:** AIX command behavior varies by release and installed filesets. Use `man`, `smit`, `smitty`, and the local change procedure before execution.
- **Historical links:** inaccessible source links and local/network destinations are cataloged in [helpfuld_2026_legacy-links.md](helpfuld_2026_legacy-links.md).

## Contents

| Area | Use it for |
| --- | --- |
| [Incident triage](#incident-triage) | A repeatable first pass |
| [Printing](#printing) | Queue inspection, stuck jobs, and printer setup |
| [AIX command quick reference](#aix-command-quick-reference) | Common inspection and administration commands |
| [Filesystems, storage, and quotas](#filesystems-storage-and-quotas) | Space, paging, mounts, permissions, and AFS quotas |
| [AFS and DFS/DCE](#afs-and-dfsdce) | Tokens, ACLs, cache, volume, and service checks |
| [Hardware and boot recovery](#hardware-and-boot-recovery) | LEDs, diagnostics, displays, and removable media |
| [Networking and performance](#networking-and-performance) | Connectivity, routes, processes, and paging |
| [NIM, installs, and software](#nim-installs-and-software) | Installation diagnostics and fileset checks |
| [Mail, VM, and file transfer](#mail-vm-and-file-transfer) | Historical VM/AFS workflows |
| [X11, desktops, and applications](#x11-desktops-and-applications) | Display, X lock, Notes, and legacy tools |
| [Historical context](#historical-context) | What should not be treated as current procedure |

## 🧭 Incident triage

Use this order before changing anything:

1. Record the hostname, AIX level, time, user impact, and the exact error.
2. Check network reachability and name resolution.
3. Check local filesystems and paging space.
4. Check recent errors and active processes.
5. Check the relevant daemon, mount, queue, token, or license service.
6. Capture outputs before remediation.
7. Make one reversible change, retest, and document the result.

```sh
hostname
uname -a
oslevel -s                 # if supported by the installed AIX level
date
df -k
lsps -a
errpt | head -30
ps -ef
netstat -rn
```

## 🖨️ Printing

### Inspect and submit jobs

| Task | Command or note |
| --- | --- |
| List AIX queues | `enq -A` or `lpstat` |
| Print to a named queue | `lpr -P queue file` |
| Print a large file | `lpr -s -P queue file` where supported |
| List a queue | `lpq -P queue` |
| Cancel one job | `lprm -P queue job_id` or `cancel job_id` |
| Cancel all jobs on a queue | `qcan -X -P queue` |
| Show queue configuration | `cat /etc/qconfig` |
| Check the queue daemon | `ps -ef | grep '[q]daemon'` |
| Start the queue daemon | `startsrc -s qdaemon` |

Before removing spool files, confirm that the queue has no active jobs and that the files are genuinely stale. Historical spool locations include `/var/spool/qdaemon`, `/var/spool/lpd/qdir`, and `/var/spool/lpd`.

```sh
df -k /var
enq -A
lpstat
ps -ef | grep '[q]daemon'
```

Common source-era observations:

- AIX hostnames and queue names may be case-sensitive.
- A full `/var` filesystem can produce misleading printing and DCE errors.
- A PostScript or 3820 conversion problem may be a binary-transfer problem, a backend problem, or a printer mode problem rather than a queue problem.
- For skewed output, verify the printer's paper and auto-carriage-return settings before changing software.

## 🛠️ AIX command quick reference

### Identity, system, and process state

| Command | Purpose |
| --- | --- |
| `date` | Current date and time |
| `hostname` | Local hostname |
| `uname -a` | Kernel and platform information |
| `bootinfo -p` | Platform information on supported RS/6000 systems |
| `uptime` | Uptime and load |
| `who` / `where` | Logged-in users and session locations |
| `ps -ef` / `ps aux` | Processes |
| `fuser -u /filesystem` | Users/processes using a filesystem |
| `kill PID` | Request process termination |
| `kill -9 PID` | Force termination; use only after normal termination fails |
| `rsh host command` | Historical remote execution; replace with SSH where possible |
| `telnet host` | Historical remote login; do not use on untrusted networks |

### Files and search

```sh
ls -l                       # detailed listing and permissions
ls -lt                      # newest entries first
ls -ld directory            # directory's own permissions
find . -name 'filename' -print
du -sk directory            # size in KiB, where supported
du -sk * | sort -n          # quick directory comparison
cmp -l old_file new_file    # differing byte positions
whereis command
```

Use `rm -i` for an interactive safety check. Treat `rm -rf` as destructive and verify the path, mount, and current directory first.

### Device, filesystem, and paging inspection

| Command | Purpose |
| --- | --- |
| `df -k` | Filesystem space |
| `lsps -a` | Paging-space status |
| `vmstat 5` | Repeated virtual-memory and CPU sample |
| `lspv` | Physical volumes |
| `lsvg -l rootvg` | Logical volumes/filesystems in `rootvg` |
| `lscfg` | Hardware configuration |
| `fsck` | Filesystem consistency check; normally run offline |
| `showmount -e host` | NFS exports on a server |
| `ifconfig tr0` | Historical token-ring interface details |
| `netstat -rn` | Routing table |
| `errpt` / `errpt -a -j ID` | Error report summary/details |

Do not run `fsck`, change boot lists, or alter a mounted filesystem during production use without an approved outage procedure.

## 💾 Filesystems, storage, and quotas

### Space triage

1. Start with `df -k` and identify the full filesystem.
2. Find large entries without crossing filesystem boundaries where the local tool supports it.
3. Check `/var`, `/tmp`, `/usr`, `/var/cache`, and paging space separately.
4. Check for open deleted files with the platform's `fuser`/process tools.
5. Remove or archive only identified, approved data.

The original environment used a site helper similar to `find.big.files`; its historical path is recorded in the companion link register. On a current system, use an approved local equivalent.

### Mounts and NFS

```sh
showmount -e server
mkdir -p /mnt/example
mount -o soft -n server:/export/path /mnt/example
df -k /mnt/example
umount /mnt/example
```

Use `soft` mounts only when their failure behavior is understood; a hard mount may be safer for some data workloads. Confirm export permissions, identity mapping, and a writable test file before relying on a mount.

### Permissions

```sh
ls -ld directory
ls -l file
chown owner file
chmod 600 file
umask
```

Numeric permissions are additive: read = 4, write = 2, execute = 1. Avoid `chmod 777`; grant only the access required. Treat password files, sudo authorization, and ACL changes as controlled security changes.

### Paging and cache

High paging or slow performance should be correlated with `lsps -a`, `vmstat 5`, `ps`, and `errpt`. The source contains AFS/DFS cache-sizing procedures, but those procedures depend on obsolete site layouts and must not be copied blindly. Preserve the current cache configuration, calculate the target from available space, and schedule a reboot if the platform requires it.

## 🔐 AFS and DFS/DCE

These commands are retained for historical systems only. Confirm the cell, identity, token lifetime, server, and target path before changing anything.

### Tokens and service state

| Task | Historical command |
| --- | --- |
| Start AFS | `/etc/startafs` |
| Refresh AFS credentials | `klog` |
| Discard credentials | `unlog` |
| Login to a cell | `dce_login /.../<cell>/<userid>` |
| Check AFS quota | `fs lq path` |
| List ACLs | `fs la path` |
| Set ACLs | `fs sa path userid rights` |
| Locate a volume | `fs whereis path` |
| List mounts | `fs lsm path` |
| Check servers | `fs checks` |
| Check a DFS client | `ls /:` and `df` |
| Restart DFS health checks | `/etc/dce_health` |
| Restart DFS daemons | site-specific `restart-dfs` helper |

### ACL caution

`fs sa`, recursive ACL tools, and DCE ACL commands can expose data broadly or remove access unexpectedly. Test on a temporary directory, record the existing ACL, and verify with a second account. The source specifically warns to verify recursive changes after using a walk-subtree helper.

### Volume and temporary-disk concepts

- AFS volume operations affect availability and data placement; use the site's approved volume-management tooling.
- A `tdisk` was historically temporary and **not backed up**. Treat deletion or expiration as data loss unless a verified backup exists.
- Before a volume split, identify the largest directories and preserve mount-point metadata.
- A "no such device" result may indicate a stale mount point or a volume/database mismatch; do not remove it until the volume identity is confirmed.

### DFS troubleshooting sequence

1. Confirm the workstation is reachable.
2. Check whether DFS startup is still running: `ps -ef | grep '[s]tartdfs'`.
3. Check `df` for the DFS mount.
4. Run the approved local health check.
5. Capture `/var/dce` logs and `dfstrace` output if enabled.
6. Escalate when initialization loops, server calls wait, or the cell database is inconsistent.

## 🖥️ Hardware and boot recovery

### RS/6000 LED notes

The source records legacy LED meanings including `223`, `227-229`, and `888`. Treat them as diagnostic clues, not a complete repair procedure:

1. Record every code in order.
2. Capture model, firmware, recent changes, and attached devices.
3. Try one controlled power cycle only when approved.
4. Consult the model-specific service guide and hardware support process.

### Display, keyboard, and mouse

- Inspect hardware with `lscfg`.
- Use SMIT's graphic-input and display menus for supported AIX releases.
- Legacy diagnostic helpers included `/usr/lpp/diagnostics/da/dkbd` and `dmouse`; verify they exist and match the release before use.
- For an off-screen X window, the source used `Alt+F7` plus the center mouse button.

### CD-ROM and removable media

The historical workflow was: define the device in SMIT, create a CD-ROM filesystem, mount it, use it, then unmount before ejecting. On current systems, verify the device name and mount point with `lsdev`, `lsfs`, and `mount` rather than assuming `cd0` or `/cdrom`.

### Reboot and shutdown

```sh
shutdown -F
reboot
```

The historical environment used local wrappers such as `/usr/local/etc/reboot` and `/etc/reboot`; check their behavior before substituting them. Always warn logged-in users and verify application/database shutdown requirements.

## 🌐 Networking and performance

### Connectivity

```sh
ping host
netstat -rn
traceroute host
ifconfig -a
hostname
```

If an address appears duplicated, power down the suspected endpoint only under an approved test plan and confirm whether the address remains reachable. Record the source and destination addresses, timestamps, and traceroute results.

### Performance first pass

```sh
df -k
lsps -a
ps aux
netstat -p udp
vmstat 5
errpt
```

Look for full filesystems, high paging, runaway processes, high page-in/page-out rates, and network errors. A single sample is weak evidence; capture several samples and compare with a known-good period.

### X11 security

Avoid historical `xhost +`; it allows unrestricted display connections. Prefer MIT-MAGIC-COOKIE authentication with `xauth`, SSH X forwarding where available, and a narrowly scoped `DISPLAY` value.

## 📦 NIM, installs, and software

### Installation checks

```sh
lsnim -l machine_object
bootinfo -p
lslpp -l
lppchk -v
```

The source used `wsinstall`, `getinstallrec`, `csreq`, and site-specific NIM masters. Those names and server addresses are historical; confirm current NIM resources, spot servers, and authorization before using any equivalent.

### Filesets and libraries

- `lslpp -l` lists installed filesets.
- `lppchk -v` verifies fileset consistency.
- For loader errors, inspect the executable with `dump -H` and inspect candidate libraries with `nm`.
- Confirm architecture, runtime library level, and `LIBPATH` before replacing a library.
- Put installation images in an approved repository; do not rely on old AFS release paths.

### Cron

```sh
crontab -l
crontab -e
```

Back up a crontab before editing. If cron says the user is unauthorized, inspect the local `cron.allow` / `cron.deny` policy. Root jobs and boot-time jobs should be managed through the site's current configuration standard, not copied from the old `root.local` convention without review.

## ✉️ Mail, VM, and file transfer

The source describes VM `SMSG`, RSCS, `sendfile`, `rcv`, `afs get`, and `afs put`. These are site-specific legacy workflows. Keep the concepts, but use approved modern transfer and mail gateways where available.

```text
FTP concepts from the source:
  binary       transfer non-text files without conversion
  ascii        transfer text with conversion
  get file     download a file
  put file     upload a file
```

Check `.netrc` carefully when historical FTP authentication fails; it may contain stale or unsafe credentials. Do not place passwords in scripts, shell history, or documentation.

## 🪟 X11, desktops, and applications

### X lock and display

- Historical `xlock` could destroy AFS tokens; current authentication behavior must be verified before relying on any `+unlog`-style option.
- Check `DISPLAY`, X authorization, and the owning user before changing `/dev/hft/0` or other device permissions.
- Use `xset -q` to inspect display settings and `xset fp+ path` to append a font path where supported.
- For fonts, `xlsfonts | grep pattern` and `xfd -fn 'font-name'` were common inspection tools.

### Lotus Notes and other obsolete clients

The source records `kill_ln`, `notes.ini`, `names.nsf`, `cache.dsk`, and Notes PTFS. These are diagnostic clues for an archived AIX client only. Before renaming or deleting Notes files, stop the client, make a backup, and confirm the data is synchronized.

### Archives and tape

```sh
tar -cvf /dev/rmt0 path
tar -tvf /dev/rmt0
tar -xvf /dev/rmt0
```

Use the actual tape device and verify media before writing. For compressed archives, identify the compression format first; do not assume `.Z` and `.gz` use the same tools.

## 🗃️ Historical context

The original document was revision `R071701.01` and included IBM Rochester/Austin operations, VM/AFS/DFS infrastructure, OS/2, X stations, WinCenter, Lotus Notes, MDA tools, and local support contacts. Those sections are retained here as terminology and troubleshooting context, not as evidence that the systems or procedures still exist.

### Source status legend

| Marker | Meaning |
| --- | --- |
| **Current-shaped** | Generic Unix/AIX concept likely to remain recognizable; verify locally |
| **Legacy-only** | AFS, DFS/DCE, VM, X11, NIM, or site helper; use only on matching systems |
| **Historical** | Host, phone, person, URL, drive, or path from the former environment |

For the complete destination inventory, see [helpfuld_2026_legacy-links.md](helpfuld_2026_legacy-links.md). The untouched conversion remains available as [helpfuld.md](helpfuld.md) for archival comparison.
