Help for movemove                        

|     |     |     |
| --- | --- | --- |
| **New Search:** | [This Book](http://w3.rchland.ibm.com///.../rchland.ibm.com/fs/common/dev/local/html/) | [Other Hits](http://w3/projects/dev2000/cgi-bin/dv2help?move!aix!#otherhits) |

##                                                              [](http://www-3.ibm.com/services/learning/spotlight/pseries/)

 

AIX & RISC/6000 Admin. Help File:  
 

\--------------------------------------------------------------------  
Do you have suggestions to help us improve this web-site?  Please visit our  
[guestbook](file:///C:/Windows/Desktop/eh_helpfuld_r071701.01.html#VERY TOP) and let us know how we are doing.

NOTE:  This is revision **_R071701.01_  Click here to view the document [History](file:///C:/Windows/Desktop/eh_helpfuld_r071701.01.html#HISTORY).**  
\--------------------------------------------------------------------

1)    [PRINTING](file:///C:/Windows/Desktop/eh_helpfuld_r071701.01.html#PRINTING:)  
2)    [AIX COMMANDS](file:///A:/EHHELP~1.HTM#AIX CMDS)  
3)    [HARDWARE](file:///A:/EHHELP~1.HTM#HARDWARE)  
4)    [SECURITY](file:///A:/EHHELP~1.HTM#SECURITY)  
5)    [VOLUME CREATION AND MANAGEMENT](file:///A:/EHHELP~1.HTM#VOLMGT)  
6)    [USER ID CREATION AND ADMINISTRATION](file:///A:/EHHELP~1.HTM#UIDADM)  
7)    [WINCENTER (WTS & ICA)](file:///A:/EHHELP~1.HTM#WINCENTER)  
8)    [AFS](file:///A:/EHHELP~1.HTM#AFS)  
9)    [DFS/DCE](file:///A:/EHHELP~1.HTM#DFS)  
10)  [COMMERCIAL SOFTWARE SUPPORT](file:///A:/EHHELP~1.HTM#CMRCSFT)  
11)  [USER & CONTRIBUTED TOOLS](file:///A:/EHHELP~1.HTM#CONTRIB)  
12)  [INTERNET & WEB APPLICATIONS](file:///A:/EHHELP~1.HTM#WEB)  
13)  [MISCELLANEOUS](file:///A:/EHHELP~1.HTM#MISC)  
14)  [DEV/2000](file:///A:/EHHELP~1.HTM#DEV2K)  
15)  [SERVERS](file:///A:/EHHELP~1.HTM#SERVER)  
16)  [DEFINITIONS AND TERMINOLOGY](file:///A:/EHHELP~1.HTM#DEFNTERMS)  
17)  [HELP DESKS](file:///A:/EHHELP~1.HTM#HELPDSKS)

*   [AUSTIN](file:///A:/EHHELP~1.HTM#AUSTIN_MAIN)
*   [PC](file:///A:/EHHELP~1.HTM#HELPDSKS)
*   [WINCENTER](file:///A:/EHHELP~1.HTM#HELPDSKS)
*   [ETC.](file:///A:/EHHELP~1.HTM#HELPDSKS)

  
18)  [OPERATING SYSTEMS](file:///A:/EHHELP~1.HTM#OSS)  
19)  
   
   
 

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

**[PRINTING:](file:///A:/EHHELP~1.HTM#PRINTING:)**

enq  -A -- Check queues \[e.g. print\] on your system (same as lpstat)     04/98 dkm

lpr -- Print a file on a local or remote printer\[e.g. eng01\] (lpr -P eng01 .cshrc).  
          lpr -s for large files.

to cut and print a window --> xv ?  (put in background)         08/98 dkm  
                                            then select right mouse button

To print screen from vm: add this to .Xdefaults: X3270\*printCommand:    lpr -P laser

xdpr - prints window

Printing from WordPerfect: need to verify they have 'Rochester Named Print Queue Support' selected. This is found under Pulldowns: File,  
PortControl

Print Room:  
  3-5318  (202-2 B301)

PRINT WEBSITES

Two places to check for print answers:  
1)  [http://w3.rchland.ibm.com/~csc/print.prob.deter/print.prob.html](http://w3.rchland.ibm.com/~csc/print.prob.deter/print.prob.html)  
2)  [http://w3.rchland.ibm.com/projects/IT/PRINT/](http://w3.rchland.ibm.com/projects/IT/PRINT/)  
 

AFS PRINTER CONTROL TOOL

If users receive the following error message when accessing the web-based  
AFS Printer Control Tool --> "unknown host: C csb\_errno=5", do the following:  
1)   Telnet to the workstation, and sign on as root.  
2) Key "ps -ef   | grep rmtd"  
3) If no process, key /usr/tools/etc/startrmtd  
 (this should have been started from /etc/rc.local at boot time)   07/98 dkm

JAWS or JAWS2 print host owner can be reached 6-6100.   05/99 cs

if users receive a message similar to this one:  
"xxxxxxxx has been received by mvsprint queue server and is at queue position: 259"  
log on to your VM system and enter :  batch query class l.  
"Jobs queued = xxx"  should be a small number (under 10).  
 If it is not, contact either the CAC (3-5544, Option 2) or call Steve Tasson directly.

\[Vicky Giffords help file\]RUN:ez ~gifford/misc-notes/print.d   -- Vicky's Gifford help file

\[MVSPRINT Restart Instructions\]RUN:ez ~gifford/misc-notes/printps.restart.instructions  -- MVSPRINT description and printps restart  
instructions

Check MVS print queue:  cd ~printps/spool/mvsjobs  
this is the directory where jobs are held until a process from printps pulls them to VM.  This directory should be empty or almost empty, as  
files should be going in and out all of the time.

To check queues on vm run:   on the P2, do CP SMSG RSCS CMD RCHVMP2 Q RCHVSA F, adding the F only give the stats and not  
every file that's queued

Print queue types:    1) local  2) Remote     3) MVS

If you have problems printing and see (from conslog) the msg: "could not load rchbak, and could not find libdb2.a", you should check for the  
presence of /usr/lib/libdb2.a. If it doesn't exist, do the following: ln -s /usr/lpp/db2\_01\_01\_0000/lib/libdb2.a /usr/lib/libdb2.a

Locating printers-->   ?URL:[http://w3.rchland.ibm.com/~csc/print.prob.deter/avail.prt.html](http://w3.rchland.ibm.com/~csc/print.prob.deter/avail.prt.html)\>

If user is getting "bogus" messages about  "you are queued at xxx", chances are that the user's  
print queue is currently defined as rchxxxx (xxxx being 4 numbers) and needs to be redefined to dupxxxx;  
follow directions on web page --> ?URL:[http://w3.rchland.ibm.com/~csc/print.prob.deter/redefine.prtqueue.html](http://w3.rchland.ibm.com/~csc/print.prob.deter/redefine.prtqueue.html)\>

Defining Network Printers (43xx) -->?URL:[http://w3.rchland.ibm.com/~csc/print.prob.deter/define.prtqueue.html](http://w3.rchland.ibm.com/~csc/print.prob.deter/define.prtqueue.html)\>

Delete a job from the prints queue: Printer tool or rroot lprm -P?queuename> jobID  or cancel jobID

To cancel all jobs queued on printer:   qcan -X -P(queue name)

View status of print queue:      lpstat  
     print queue status definitions -->?URL:[http://w3.rchland.ibm.com/~csc/print.prob.deter/status.lpstat.html](http://w3.rchland.ibm.com/~csc/print.prob.deter/status.lpstat.html)\>

Help print - this command will give you help on problems with printing.

.dvi files:  The program dvips converts a DVI file file\[.dvi\] produced by TeX (or by some other processor like GFtoDVI) and converts it to  
PostScript, normally sending the result directly to the laserprinter.  To convert .dvi files to postscript file use DVIPS.   For more info:  \[HELP  
dvips\]RUN:help dvips

If a print queue needs to be deleted, be sure there are no jobs currently hanging on -- look  
both in /var/spool/qdaemon and /var/spool/lpd.  The best way to delete these jobs would be  
with the following command:  rroot rprm -Pqueuename job#.

to show how printer is defined on  queue:   cat /etc/qconfig

if print queue name is more than 7 chars,  use qdef del 'queuename' to remove it from queue.

For proprinters that show data 'skewed':  Have them turn 'auto carriage return' ON.  (look in the manual, it is something on the printer  
(hardware)) .  In the proprinterII, it is switch 6 'ON'

Printer help text   help faq-print (ez ~/print/faq-print.help)

To change the priority of a job (drops to end of queue):  qpri -# jobnum -a 1   08/99 jns

Check if print daemon active ps -ef|grep qdaemon if not active have to restart  
 restart by using this command:    startsrc -s qdaemon       06/99 dkm

Printps info: printps pw is in **/afs/rchland.ibm.com/usr4/printps/spool/mvsdata/pfile**

To display number of print jobs queued on RT printserver ----> on the RT execute "/etc/lpc status"

To show names of print jobs queued on RT cd /usr/spool/lpd/prt

To print screen from vm: add this to .Xdefaults: X3270\*printCommand:    lpr -P laser

Distribution Code for Printing, (for the banner page)   04/98  dkm  
Use the following command to check the user's routecodes on VM:

        grep   -i   ^userid   ~htadmin/public/RCHVM\*.\*

lpr looks at DIST environment variable first for routing information. If it is not set, it will look to VM.  
Dist codes are set on ea. vm system. rcmd qacc looks in alphabetical order, check the code on all of the VM systems.

From VM:  DIRM REV  You will get a note back:  look at Account info.  To change DIST code VM:  DIRM DIST ?code>, (no brackets).  The  
code consists of 3digitlockbox#, 1digitsecuritylevel, and 3digitdeptno.

From Workstation:  RCMD QACC ?userid> (no brackets)  
from VM: to find VM distribution code: dirm dist ?

set distibution code on workstation  setenv DIST lllsddd put this in .login if permanent

Banner page is printed over and over  
There is a slide on the paper tray that has the paper size on it.   This must be set to 11 inches, not over.

'Full' errors when trying to print:  
All files go through /var on local disk.  use the 'df' command to check out size of /var directory  
if %used is high then follow the next 3 sections.

Prints banner pages, then one page, Then more banner pages  
power off the printer, then back on

Checking '/var/spool/qdaemon' for old file.  
use 'ls /var/spool/qdaemon' to see if any files are in this directorys.  
if 'lpstat' does not show any files queued but, files exist in this directory, remove them all.

Checking '/var/spool/lpd/qdir' for old files.  
use 'ls /var/spool/qdir' to see if any files are in this directory.  
if 'lpstat' does not show any files queued but, files exist in this directory, remove them all.

Checking '/var/spool/lpd' for old files.  
use 'ls /var/spool/lpd/df\*' to check for the folowing filenames.  
Filenames will appear in the following format:  
 dfxxxxxxx@hostname.rchland.ibm.com  
 

Set from VM to RT print queue: lprset printerqueuename rtxstationname (perm

I/S Printer definitions:

For special print requests (Drilled and/or simplex) define the following queues to your system.  
host:  
     itprt01  
 queues:  
      rchdps  - duplex  
      rchddps - duplex drilled  
      rchsps  - simplex  
      rchsdps - simplex drilled  
(drilled = three hole punch for binders)  
NOTE: printer types vary for the special requests:  
3130dp  duplex  
3130dr  drilled duplex  
3130sm  simplex  
3130ds  drilled simplex

eg:  qdef add rchdps itprt01 rchdps 3130dp

How to print from the Web Explorer on an OS2 machine to a printer attached to a rs6000:  
The printer has to be defined to the lan server, Don Tomlinson 3-6231.  
The name that is defined to the lan server is the name you have to  
use when you print from the Web Explorer.

On RS/6000s, host names and print queue names are case sensitive. This means host name 'printsps' is different than 'PRINTPSs'.

VM-related printing to I/S printers:

Link/Access TCP/IP disk:  Add the following to your PROFILE EXEC --   VMLINK TCP

From the VM command line: To set your default printer (this only needs to be done once):  
LPRSET rchdps printps (PERM

When printing to the I/S printers, your distribution code is  required.  Following is a sample LPR command which includes  your distribution  
code:  
LPR fn ft fm (CLASS 206U77N PRINTER rchdps HOST printps

The printer and host flags are not required if you use LPRSET: LPR fn ft fm (CLASS 206U77N

LPR in Rochester does not allow printing more than one file at a time.  Our local backend doesn't  
support it -- This is a local restriction.  Alternate suggestion would be to cat the files, then lpr them like so: cat .login preferences | lpr  
\-Plaser.

NOTE: Do not print LIST3820 files to the highspeed postscript printers on printps.

The lpr backend will convert 3820 to ps if you are sending a 3820 file to a ps printer. HOWEVER -- the 3820 file must have been  
downloaded to AFS using the binary option.  The backend will run the lp3820 program for you.

To convert a list3820 file to a postscript file use the lp3820 command tool.

PostScript files submitted to RCH4001 will be automatically rerouted to the I/S printers.  Duplex, not drilled, is the default.

splp - If the customer is having problems with submitting postscript jobs to a printer, telnet to the host where the printer is connected and  
type splp.  If you see a  '-p !  pass-through'  instead of   '-p +  pass-through', enter the command: splp -p+

To print from VM to local printer: add to $$print file on VM  
TEST    020-2 Camaro                1403 EXEC LPROFS camaro laser

To define a print queue - qdef add laser  camaro laser 4019ps  
Usage: qdef  add name unixhost  qname type \[banner\]  
        qdef  add name local lpN type \[nobanner\]  
         qdef  add rchXXXX mvs  
         qdef  delete | del name  
         qdef  up | start name  
         qdef  down | stop name  
         qdef  reset name  
         qdef  q | query  
         qdef  ls  
         qdef  view  
         qdef  reg  regname

examples:  (duplex) ---> qdef add laser camaro laser 4039dp  
               (simplex) -->  qdef add lasersm camaro laser 4039sm

NOTE: An admin type qdef command is:

qadm -U queuename:devicename  (to bring queue up)  
qadm -D queuename:devicename  (to bring queue down)  
   
 

Setting up a local RT printer --- from the host machine:  qdef add Qname RTname ascii type

Remove jobs from the print queue:  lprm -P (print queue name) (job #)

Remove jobs from RT work stations:  
 1). logon to the RT station with my userid  
 2). Ask user what printer is attached locally  
   ie: ASCII, 4019e, ETC  
 3). List printer queue - lpq -P (queue name)  
 4). rroot lprm -P (print queue name) (job #)

Printing from Messages: Messages doesn't read /etc/qconfig but instead looks at the files in /config/printqs/

If someone is having trouble printing (tty) --> ?URL:[http://w3.rchland.ibm.com/~csc/print.prob.deter/console.html](http://w3.rchland.ibm.com/~csc/print.prob.deter/console.html)\>

\[Printing / Plotting\]?URL:[http://w3.rchland.ibm.com/projects/IT/PRINT](http://w3.rchland.ibm.com/projects/IT/PRINT)/>  01/98 -- erh  
MDA users typically print to the postscript printers listed below, although any postscript printer can be used.  I have always defined the  
queues with the name shown below.  These are the names they are looking for in the selection lists presented by the MDA applications.  
First determine that the correct queue is defined and running on the user's workstation.  If the user continues to have trouble  
printing/plotting from Catia, the contact is Jeremy Brezovan, 3-5095.  For all other MDA applications the contact is Eric Hepp, 3-2728.  
 server   queues   location  type  owner  
 super-slam  doris / ddoris   050-3/A202  4039  Barry Shepherd  
 itprt04   sim0002 / dup0002 050-3/C108  4039  Dick Koenigs  
 caste   afsps   050-3/D212  4029  Eric Hepp  
 itprt05   sim2055 / dup2055 107-2/H313  4039  Dick Koenigs  
 autriche  afsps   107-1/D210  4019  Jeremy Brezovan  
 itprt03   sim0011 / dup0011 103-1/B202  4039  Dick Koenigs  
   
   
   
   
 

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
 

**[AIX COMMANDS AND TIPS](file:///A:/EHHELP~1.HTM#AIX CMDS)**

AIX Helpful Hints ? Commands

**aix.level** -- to see current aix level      04/98 dkm

**[chfs](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?chfs!aix!) -a size = +8192 /user** -- this can be used to increase the filesystem size by adding  
                                              free physical partitions to it.   Must use a factor of 8192 (number  
                                              of 512 byte blocks in a 4MB PP.  For instance, to add 100MB:  
                                              would be like adding 25PPs or 25\*8192-> 204800)  
                                              # chfs -a size=+204800 /usr        04/98 dkm

**[chdev](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?chdev!aix!) -l sys0 -a maxuproc=xxx** -- to increase limit on number of processes running,  
           this command needs to be run as root (normal number is 140).

**[clock](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?clock!aix!)** -- Clocks are set by the AFS cache manager. The AFS servers are sync'd to a  
master time source inside IBM, and that's sync'd to a atomic clock on  
the internet. The AFS cache manager tweaks the clocks and keeps them all  
in sync.   To directly check an individual rs/6k against the atomic clock, run the  
following command as root:     /usr/afs/etc/ntp -f -s ks5    05/98 dkm

**[date](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?date!aix!)** -- Display the current system date and time (date)    04/98 dkm

**[df](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?df!aix!)**\-- Reports information about space on your file systems (df).      04/98 dkm

**[du](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?du!aix!)** -- Shows directory size in 512 byte blocks (du -s). or eg: du -k /var/spool      04/98 dkm

**[du -a](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?du -a!aix!)** -- Search a directory tree recursively. List all files size in 512 byte blocks    04/98 dkm

**[echo](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?echo!aix!)** -- Write to standard output (echo $HOME)

**[enq  -A](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?enq!aix!)** -- Check queues \[e.g. print\] on your system (same as lpstat)     04/98 dkm

**[env](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?env!aix!)** --  List current environment variable values (env)      04/98 dkm

**exit** -- Terminates a process (e.g. use to exit out of a su after signed on and done).      04/98 dkm

**[find](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?find!aix!)** -- searches directory tree for file;  fine . -name filename print

**[fsck](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?fsck!aix!)** or **dfsk**  -- Checks file system consistency and interactively repairs the file system.  
Syntax:  
       fsck \[ -n \] \[ -p \] \[ -y \] \[ -dBlockNumber \] \[ -f \] \[ -iI-NodeNumber \] \[ -o Option ... \]  
       \[ -t File \]  \[ -V VfsName \] \[ FileSystem1 - FileSystem2 ... \]

**[fuser](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?fuser!aix!) -u /filesystem** --This cmd will tell you who is in a file system--eg: fuser -u /var

**[ftp](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?ftp!aix!)** -- File Transfer a file or multiple files to another AIX computer.     04/98 dkm

**[tftp](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?tftp!aix!)** -- on the machine that runs the tftp daemon, there is a file that is used /etc/tftpaccess.ctl and  
it has entries that ALLOW .... those are the only ones that he can tftp.    08/98 dkm

**[hop](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?hop!aix!)** -- opens a typescript on your display, running from a remote system  
  hop will fail if the users home dir doesn't have sytem:anyuser with at least look, or l permissions.  
  hop -v will display any error messages you may be getting.

**[kill](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?kill!aix!)** -- kill a process (kill id) or (kill -9 id) suspend process (kill -17 id)  restart process (kill -19 id)  04/98 dkm  
  go to /usr/include/sys/signal.h to find various kill options.  
                 If there are many similar processes to be killed (such as framemaker pid), use the following:  
                 1.  ps -ef | grep frame | awk '{print $2}' > whatever  
                 2.  kill -9 \`cat whatever\`  (those are backward quotes)

**[ln](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?ln!aix!)** -- sets up link  
 To set up symbolic link  
 ln -s 'destination path' 'source path'  
 ln -s /tmp/toc toc  or exmp: ln -s ~spillman/private/.netrc .netrc

 This creates the symbolic link, toc, in the current directory. The toc file points to the /tmp/toc file.  
  If the /tmp/toc file exists, the cat toc command lists its contents.

 To achieve identical results without designating the TargetFile parameter, enter:  
 ln -s /tmp/toc

**[lpr](file:///A:/http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?lpr!aix!/w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?lpr!aix!)** -- Print a file on a local or remote printer\[e.g. eng01\] (lpr -P eng01 .cshrc).  
          lpr -s for large files.

**[ls](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?ls!aix!)** --  list files        04/98 dkm  
 ls -l filename gives rights  
 ls -lt  gives date  
        ls -lt a gives date in ascending order

**[lscfg](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?lscfg!aix!)** -- Will show you the configuration address of all hardware components for the machine you are on.

**[lsps](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?lsps!aix!) -a** list page space

**[lspv](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?lspv!aix!) hdisk0, lspv hdisk1** -- list free space

**[lsvg](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?lsvg!aix!) -l rootvg** -- list all devices/filesystems on rootvg

**[pdf](http://www.webopedia.com/TERM/P/PDF.html)** -- Portable document format  (uses adobe-acrobat reader)  
           use acroread to read this files  06/98 dkm

**[pg](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?pg!aix!)** -- Display contents of a file one page at a time (pg test.file)

**[ping](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?ping!aix!)**  -- See if another AIX machine is on the network (ping vegra).

**[ps](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?ps!aix!)** -- Show the processes running on your workstation (ps aux, ps -aef)

**[rcmd](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?rcmd!aix!)** -- Execute a command on VM without logging onto VM (rcmd tele otto).

**[rm -rf](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?rm -rf!aix!) (directory name)**\-- will delete a directory and all of the contents of that directory.  You may have to use the ezafs tool to give yourself  
recursive rights.

**[rm -i](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?rm -i!aix!)** -- will prompt you before the removal of file.

**[rsh](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?rsh!aix!)** -- Remote execute an AIX command on another host.

**[setpackage](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?setpackage!aix!) prod** (or **dev**) --  to set software package.  Let reboot.

**showconfig** -- showconfig runs against file at:  /afs/rch/common/config/cfg.all   02/98--dkm  
                 if a machine has been powered down for some time, WSUPDATE will delete  
                 the information from showconfig.  08/98 dkm

**[su](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?su!aix!)** -- Sign on temporarily as another user (su userid).

**swlevel** -- to see level of software; use setpackage to change

**[sys](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?sys!aix!)** -- Display the level of operating system you are running (sys).

**[telnet](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?telnet!aix!)** -- Logon to another AIX workstation (telnet vegra).

**top10vm -a** -- will show you the top 10 paging space using processes

**[uptime](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?uptime!aix!)** -- Shows how long the system has been up (uptime).

**[vmstat 5](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?vmstat 5!aix!)** --to see Page space being used

**[where](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?where!aix!)** -- Display where a user is logged on and xlock information (where).

**[whereis](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?whereis!aix!)** -- Finds source/binary and manuals sections in your path (whereis ez).

**[who](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?who!aix!)** -- See who is logged onto the workstation (who).

**[whois](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?whois!aix!)** -- Display user information (whois vegra or whois rgotto or whois otto).

**[xrooms](http://w3.rchland.ibm.com/projects/dev2000/cgi-bin/dv2help?xrooms!aix!)** -- Organizes windows into related groups (/usr/contrib/bin/xrooms).  
 

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
 

**[HARDWARE:](file:///A:/EHHELP~1.HTM#HARDWARE)**

rrsinfo -- LOTS of HW information

hardware upgrades:  
If a customer is wanting to upgrade the hardware for a machines, ie memory, disk, ...etc, they will need to contact: Gary Gerber for  
programming, Jim Dunlap for Engineering, Greg Geerdes for in Manufacturing.

How to service bad P200 displays:    07/98 ram  
Customer should  call 1-800-ibm-serv for the repairs.  The customer will get a new display  
shipped directly to them.  They will then put their old display in the box that the new one  
came in and ship it back.   A shipping instruction form will have to be done.  If the customer  
is not familiar with the shipping instruction process, they can contact Ann Meech  
 (v2ad653@ibmusm07).  Gary Gerber is the backup person when Ann is not available.  
 If the customer has everything repackaged and the labels put on the box, Ann or Gary would  
pick up the display and do the shipping instructions.

How to service bad 6091 displays:    07/98 ram  
As long as the supply of 6091 displays stays healthy, Dept LELA will swap them out.  
Also, the following people have 6091 displays available -- Ann Meech (2579) or Mark Kalmes (4990)  10/98 dkm  
 

MULLIGAN Boxes:  orange is IN, should go into the wall. switch position 1

Command to reset mouse and keyboard telnet to user's system, then issue one or both of these commands:  
Ths may not work on 4.1  
/usr/lpp/diagnostics/da/dkbd  
/usr/lpp/diagnostics/da/dmouse  
NOTE: on 4.1 systems, these commands will NOT work until the user logs off to a green screen.

If you want to change the typamatic rep/delay rates of your keyboard, you may need to use the chhwkbd command.  It is in /usr/bin and is  
readable and executable only by root.  If you execute "smit devices" on the console (/dev/lft0), then choose "Graphic Input Devices", then  
choose "Keyboard", you should be able to do what you want.  smit on the console screen runs with root authority.

Keyboard functions in the X-Windows environment are set in the .xinitrc file....look for the xset command.  
 

If these commands do not work,  kill the process, then do  /etc/reboot on user's system

RS6000 LED  
'223' '229' LED readout. (start system)  
223     SCSI devices selected for ipl  
229     a normal mode device list is present but has no entries (null  
       list) or none of the valid entries succeeded in ipl

        ACTION:  
If the system halts with this value in the three digit display either the NVRAM device list is empty, the devices specified in the list are not  
valid boot devices, or there is a problem with the devices in the list. To determine if there is a problem with the devices in the list, refer to  
the hardware problem determination procedures in the RIOS Diagnostics Programs Operators Guide.  
 1.  Try power off  and power back on in normal mode.  
 2.  If that doesn't work-- have Rich or Pat make a housecall  
 

227-229  (usually occurs in 4.1 installs)  
1.  hit yellow button once, immediately turn to SECURE  
2.  Wait for 200 in the LED  
3.  Turn to key to service and hit yellow button once.  
4.  Install menu will come up:  
    a) Language = English  
    b) 99 - back to main menu  
    c) option 1 -- select boot/startup device (tr)  
       -- set or change network address (4M or 16M)  
       -- client address  009 005 \_\_\_ \_\_\_  (I.P. Address)  
       -- 009 005 100 100\* (telnet to install1, use:  "lsnim -t standalone|grep wsname " to find  actual wsname  
                                                                                 use that name in this command:  lsnim -l wsname)  
    (look at the "spot" line.  if it says "version\_disp," then bootp address is 100.100  
            if it says "version\_inst1," then bootp address is 100.101  
            if it says "version\_inst2," then bootp address is 100.102)  
       -- 009 005 \_\_\_\_ 001 (gateway)  
    d) 99 to main menu  
    e) option 3 to test transmission (start ping)  
       If ping test fails, user may need to fill in the addresses again under this option (have  
       user check to see if addresses appear as zeros under option 3).  
       -- option 4 to start ping test  
       -- wait for successful ping test (approx 15 seconds)  
             (if unsuccessful, have user double-check the ipl addresses he/she keyed in)  
    f) 99 to main menu  
    g) exit main menu and start system  
    h) turn key to normal and press enter  
 

        -- wsinstall should take about 60-90 minutes  
   
   
 

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
 

**[SECURITY](file:///A:/EHHELP~1.HTM#SECURITY)**

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
 

**[VOLUME CREATION & MANAGEMENT](file:///A:/EHHELP~1.HTM#VOLMGT)**

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

![](eh_helpfuld_r071701.01_files/rs6k_43p150.jpg)  
 

**[USER ID CREATION & ADMINISTRATION](file:///A:/EHHELP~1.HTM#UIDADM)**

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  

**[WINCENTER](file:///A:/EHHELP~1.HTM#WINCENTER)**

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
  
 

**[AFS](file:///A:/EHHELP~1.HTM#AFS)**

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
 

**[DFS/DCE](file:///A:/EHHELP~1.HTM#DFS)**

To dce\_login to another cell:  
dce\_login /.../<cellname>/<userid>  
...where  <cellname> = rchland, austin, endicott, etc ...  
... and      <userid>       = AFS/DFS userid for that cell.  (elh, 07/18/01)  
 

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
 

**[COMMERCIAL SOFTWARE SUPPORT](file:///A:/EHHELP~1.HTM#CMRCSFT)**

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
 

**[USER & CONTRIBUTED TOOLS](file:///A:/EHHELP~1.HTM#CONTRIB)**

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
 

**[INTERNET & WEB APPLICATIONS](file:///A:/EHHELP~1.HTM#INET)**

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
 

**[MISCELLANEOUS](file:///A:/EHHELP~1.HTM#MISC)**

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
 

**[DEV/2000 & CMVC](file:///A:/EHHELP~1.HTM#DEV2K)**

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
 

**[SERVERS](file:///A:/EHHELP~1.HTM#SERVER)**

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
 

**[DEFINITIONS AND TERMINOLOGY](file:///A:/EHHELP~1.HTM#DEFNTERMS)**

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

![](eh_helpfuld_r071701.01_files/rs6k_43p150.jpg)  
 

**[HELP DESKS](file:///A:/EHHELP~1.HTM#HELPDSKS)**

\---------

  
 

**[AUSTIN:](file:///A:/EHHELP~1.HTM#AUSTIN_MAIN)**

            Austin AFS Help Desk:   678-1600 (this has been disconnected)  
      dial 1-888-IBM-HELP         (06/99 -- dkm)

To reset your password in the Austin cell:  
telnet to dcservices.austin.ibm.com  
sign on as " services " :  select option1, then option 5, then option 1

08/99 dkm  
If you send a note to AFSADMIN@AUSTIN.IBM.COM ... this is the response you will receive back:  
       Your mail has been received by AFSADMIN.  Please note  
         that this is a service ID only.  Once your request has  
         been processed, you will be notified.

        \*\* All requests must be submitted by a manager! \*\*

        If you are a manager and your mail was for a one of the  
        following items, your request will be processed within  
       2 business days:  
             AFS/DCE ID Reinstatement  
            AFS/DCE ID Rename  
            AFS/DCE ID Suspension  (removal)  
            AFS/DCE ID Transfer  
            Austin (supported) AIX Server ID problems  
           Austin Mail Gateway ID problems

      All other service requests ? questions should be re-directed  
      to the Austin Site Customer Support Center at t/l 793-HELP  
      (outside line 512-793-HELP).

      You may also find helpful information at the following URL's:

      For the "DAAT" ID tool services:  
      [http://w3.austin.ibm.com/daat](http://w3.austin.ibm.com/daat)

    AFS Austin policies/processes:  
    [http://w3.austin.ibm.com/afs/austin/afs/doc/afs\_html/afs\_processes.toc.html](http://w3.austin.ibm.com/afs/austin/afs/doc/afs_html/afs_processes.toc.html)

    Austin DCE Home Page:  
      [http://w3.austin.ibm.com/dce](http://w3.austin.ibm.com/dce)

    Austin Mail Gateway Information Page:  
      [http://w3.austin.ibm.com/site/mail.html](http://w3.austin.ibm.com/site/mail.html)

    Thank you,  
     Austin Registration Administration  
     for AFS, DCE, AIX server ? Austin Mail Gateway  
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
  
 

**[OPERATING SYSTEMS](file:///A:/EHHELP~1.HTM#OSS)**

[Windows Family:](file:///A:/EHHELP~1.HTM#WINFAM)

The command - NET USE -, will allow you to view settings for existing file systems  
and add new file system.

**net use f: /afs/rchland.ibm.com/usr7/rolandw**:  
This will add the file system, /afs/rchland.ibm.com/usr7/rolandw, to the the F drive.  
 

[Apple OS:](file:///A:/EHHELP~1.HTM#APPLEOS)  
 

[Linux Family:](file:///A:/EHHELP~1.HTM#LINUXFAM)  
 

[UNIX General:](file:///A:/EHHELP~1.HTM#UNIXGEN)  
 

\----------

[Back to Top](file:///A:/EHHELP~1.HTM#VERY TOP)  
 

  
 

**[DOCUMENT HISTORY](file:///A:/EHHELP~1.HTM#HISTORY)**

R070501          Basic document format/design created by: Eric Hepperle  
R071701.01     Topic graphics harvesting completed and applied.  
 

\----------  
   
   
 

\[Second-Level Support Personnel\]?URL:[http://w3.rchland.ibm.com/~uidadm/RESTRICTED/support-form.html](http://w3.rchland.ibm.com/~uidadm/RESTRICTED/support-form.html)\>  01/98--dkm  
(actual text for support personnel is kept in ~uidadm/data/phonebook.txt)  
\[AFSPAGER Notes\]RUN:ez ~admin/doc/pager.notes.d  
\[4.1.5. Install on 7043-140\]RUN:ez  ~pats/7043\_rspc\_install.d  
   
 

To relocate screen or bring the top bar of a window back onto the screen, press the ALT + F7, along with the center mouse button.  
(01/98--dkm)

to find machine information on a machine that is not showing up with wslevel --  
 1. log onto the machine you need the info from.  
 2. Enter the command                  uname -m  
 (note you will get a number - 000112204200 - the number you want to look at for the model number will be the fourth and third number  
from the last.  In this example we will use the number 42)  
 3. view the file /usr/local/bin/wslevel  
 4. Search for the fourth and third number from the last that you got from the uname command.

reboot workstation /usr/local/etc/reboot, if logged in as root use /etc/reboot  
 /usr/local/etc/reboot run package first, at the beginning of the reboot, so only 1 reboot happens, while /etc/reboot reboots, and then runs  
package which reboots again. so /usr/local/etc/reboot is faster

shutdown workstation /usr/local/etc/shutdown if logged in as roots use /etc/shutdown

Newuser command creates initialization files from the examples in ~admin/proto/newusers/rs.

To find the biggest files on a local  file system  ~csc/bin/find.big.files ?filesystem> -h  (05/18-rdl)  
 where filesystem could be /, /usr, /var, /tmp, /var/cache, or any filesystem

To find the largest dir in an AFS volume  adu -vk ~?userid> | awk '$1 > 10000'      (05/18-rdl)  
              to find out what files are over 10M on userid's home directory

Monitor AFS Partitions -- The program that monitors for free space only does anything when free space drops below 90M.  Use 'fs diskfree  
\[DIRECTORY\]', where DIRECTORY is an optional parm about which directory you want to check. Look under the 'avail' colume for free  
space left on partition in k-bytes.

Password File (etc/passwd)

Master /etc/passwd path is /afs/.rchland.ibm.com/common/prod/etc/passwd.  To edit the master passwd file, use ~admin/bin/pw\_edit.  
(01/98--dkm)

To see if the master password file is lock, cd  /afs/.rchland.ibm.com/common/prod/etc  
Check for this file --> password.lock.

To find out a group id number, issue the following command:  dcecp -c group show ?userid>  (01/99-dkm)

08/98 jpj  
To give yourself access to a dfs home directory, issue the following command after you do dce\_login:  
 dcecp -c acl modify ?filename> -add '{user adianem rw}'  
To remove access:  
 dcecp -c acl modify ?filename>  -remove '{user adianem}'  
To show:  
 dcecp -c acl show ?filename>

If the password file is current; but still not allowing customer to signon.  Customer is probably getting invalid userid.  Run this command to  
massage the password file ==> /etc/mkpasswd /etc/passwd  
(01/98--dkm)

su Problems  
If you get sorry when you do the su command for root, and you know you put the correct word in; try these commands:   (01/98--dkm)  
(setenv AUTHSTATE compat; su)    use if running csh  Note:() included in command  
(export AUTHSTATE compat; su)    use if running ksh  Note:() included in command

Filesystems ? permissions:  
umask -- Used to set permissions on new files/directories. This is what controls new permissions. Default in rochester is 077, which is a  
permission of 700 (777-077 = 700). Default UNIX is 022, which is a permission of 755 (777-022=755).  Controlled in global.login. Can see  
what it is set to by typing 'umask'

/ file system need to have these permissions:  
drwxr-xr-x 23 bin                      1536 Jun 26 16:51 /

To move a filesystem from one vgroup to another, you can use smit, and move a  
physical volume. You can choose \*what it is you want to move\* from the current pvolume  
to the destination pvolume.

change owner of file:   chown  ?new-owner-userid> ?filename>      (01/98--dkm)

change permission bits of file:   chmod 600 ?filename>  
 600 gives only owner permission to read and write file.    (01/98--dkm)  
          \_\_ \_\_ \_\_  
          4   2  1   If someone wants rwx, you would chmod to 7, (4+2+1). eg:  
         rwxrwxrwx = chmod 777  
         rw-r-xr-- = chmod 654

         To get rid of an 's' bit, you can do a -s with the chmod command (eg, chmod g-s file.name)

Using chmod to change serveral file:  (11/98  ---rww)  
           What you want to do is a ls command in the directory that you want to change the file permissions on  
 and then pipe the ls command to xargs. The command is as follows using an example directory of \\:  
    ls \\ | xargs chmod 755

to list access rights on LOCAL DISK:  /bin/ls -l

to list dir. access rights -- ls -ld

permits file   /etc/user.permits  This is a Rochester-modified login file.  The norm is NOT to have this file on a work station; however, if a  
user wants to isolate the work station from other people using it,  this file can be created  as root .  Put just the userids in the  
/etc/user.permits file -- one userid per line (be sure to include your own userid and root).  The login program was modified to look for the  
presence of this file on hdisk, and will give anyone not in the user.permits file the following message if they try to log on:  
"userid must be in user.permits or you must have a loadleveler job on this machine."   03/98 - dkm

sudo  file is stored in /var/sudo/sudo.authorized  
master copy of sudo file is in: /afs/rchland.ibm.com/usr0/admin/sudo/sudo.authorized  
to copy the master file to a host, telnet to host as root, run this command:  
cp ~admin/sudo/sudo.authorized  /var/sudo/sudo.authorized.

If sudo does not seem to work on 4.2 workstations, issue the following command:  
    cm setsetuid /usr/loca/bin/sudo  (see Rich Wales for further explanation)

Cannot Log on as ROOT -- do the following 3 steps:  
   1.  sign on to the ws with a global sudo userid  
   2.  remove /etc/security/passwd  
   3.  reboot

to increase local disk space:  
Go into smit select the following  
   System Storage Management (physical ? logical storage)  
   file systems  
   add/change/show/delete file systems  
   journaled file system  
  change, show characteristics of a journaled file system  
   select the file system  
   increase by 512 byte blocks  
   number will be rounded up to the next page size chunk

increase /home:  
   To increase the size of /home in 4 megabytes increments, execute the following command:  
 ~> bumphome

 The maximum size of /home that bumphome will allow is 12 megabytes

You can perform all functions under SMIT as root when you are at the greenscreen. You are acting as root within SMIT.  You are NOT  
acting as root for anything else.

To see log of what happenend during smit:  read smit.log in user's home volume.

Shells

bsh is the Bourne shell, ksh is the Korn shell.  
Your default shell is set in /etc/passwd, which is copied to your workstation every night. andrew-reqeust will update the "master" copy of  
/etc/passwd for you. To change your default shell, send a note to andrew-request.

ksh runs ".profile" when you log in and ".kshrc" every time you create a new shell. csh runs ".login" and ".cshrc".

noclobber : Noclobber allows the shell to overwrite an existing file when you redirect.  i found it in .kshrc, does it work in cshell also?  Yep.  
set noclobber. I think we set it by default  Otherwise you need to run cmd >! file to overwrite a file.

To set variables permanently in the shell:  
In csh, you do setenv blah  
In ksh, you do export blah=jfjfj

Time Zone (TZ) is set up when machine is originally installed.   If a user has the time zone set to eastern (TZ=EST5EDT)and wants it to be  
central (TZ=CST6CDT), this must be done through SMIT.   (Adding it as "setenv" will last only until the user reboots again.)

Installs/Upgrades

Micro Code Update for 43P-140 RS6000  
Run this commands as root to determine if customer has a 140.  
bootinfo -p

Then run this command to see if you have a 150.  
lsattr -l sys0 -E -a modelname -F value  
 

wsinstall -al - Administrator's  Install Tool

For multi-installs with same parameters (like hard drives), see ~lampat/public/chesnutt\_install  (4/99 rl) (3/01 elh)  
 (sudo wsinstall -alf ~lampat/public/autoinstall)

You can find more samle in  ~csc.  For example, the stand-alone example is located at:  
~csc/wsmulti\_install.stndalone.sample.  
 

7043-150 installs  (06/99 jb)

Fireworx on dispatch, loader1, and install5.  This will allow users to execute specific commands on any of these NIM Masters from their  
AFS/DFS client machines.

We will be allowing people to run the script /nim/scripts/change.to.chrp.  This script changes the platform of a machine object in the NIM  
database from rspc or rs6k to chrp.  chrp is relatively new and wsinstall has not been updated yet to handle it.  The main group of people  
who will use this will be those who are using wsinstall -al to define new machines for installation.  After they run wsinstall -al and get the  
bootp server, they will need to make one of the following calls, from an AFS/DFS client (and they don't need to be root) depending on what  
their bootp server is:

csreq install.100.chrp 10 makechrp {machine\_short\_hostname}  
csreq install.101.chrp 10 makechrp {machine\_short\_hostname}  
csreq install.104.chrp 10 makechrp {machine\_short\_hostname}

csreq install.115.chrp 10 makechrp {machine\_short\_hostname}  
csreq install.116.chrp 10 makechrp {machine\_short\_hostname}

csreq install.43.chrp 10 makechrp {machine\_short\_hostname}  
csreq install.195.chrp 10 makechrp {machine\_short\_hostname}

where {machine\_short\_name} is the the result of doing 'hostname -s' on the machine that is being installed.  Basically, it't the machine  
name without the domain attached to the end of it.

Notice that each call contains the last part of a spot server address in the install.XXX.chrp field.

Any of the first three calls will go to dispatch because dispatch's address ends with 100 and the addresses of the spot servers under  
dispatch end with 101 (install1) and 104 (install4).  
The fourth and fifth calls will go to install5 because install5's address ends with 115 and the address of the spot server under install5 ends  
in 116 (install6).  
The sixth and seventh calls will go to loader1 because loader1's address ends with 43 and the address of the spot server under loader1  
ends in 195 (loader2).  
 

Install Fail  
 1)  locate the machine object by keying this command:  
   /usr/lpp/wsinstall/bin/getinstallrec ?hostname.rchland.ibm.com>  
 2)  then key lsnim -l ?machine\_object\_name) on the NIM master  
 3)  check for error messages and talk to your level 2 AIX folks!

Not Owner:  Telnet to the user's workstation as root and run:  
   /usr/lpp/wsinstall/bin/wsdbclientck

For more information regarding wsinstalls -->  \[WSINSTALLS\]?URL:[http://w3.rchland.ibm.com/~csc/aix.prob.deter/wsinstall.html](http://w3.rchland.ibm.com/~csc/aix.prob.deter/wsinstall.html)\>  
 

888 --> When users get flashing  888's in the LED, have them  press the yellow  
              button and record the codes until they get the 888's again.  
              They should then power the machine down and back up again to recover.  
               If the first code after the 888 is a "103",  the problem is usually hardware.  
               If the first code after the 888 is a "102",  the problem usually is software.  
              This process is described in the "Operator Guide".  Each diagnostic message is  
              defined in the Common Diagnostic and Service Guide.  
 

Remote mounting of filesystems

to mount a vm disk:  vmmount rchvmp2.spillman.191 spillman myvmpassword  
 look at help for vmmount, vmumount

NFS mount a filesystem  (look at a hardrive from one rs6k to the other)  
    smit mknfsexp

Verify that the NFS server has exported the directory:    showmount -e systemname  
eg: showmount -e volleyball  
showmount: no exported file systems for volleyball  
This command displays the names of the directories currently exportd from the NFS server. If the directory you want  to mount is not listed,  
export the directory from the server by following these instructions:  
 In smit select the following:  
      Communications Applications and Services  
      NFS  
      Network File System (NFS)  
      Add a Directory to Export List

Command to mount a remote directory:  
 mount -o soft -n odo /local /mnt  
    where:  
 soft = type of mount  
 odo = the remote machine  
 /local = the remote filesystem name, volume grp exported on remote system  
 /mnt = the local mounts point

Mounting PC directory: (look at PC dir FROM RS6k)

1.  nfsd, inetd, and portmapper must be running on PC.  
     (look in tcpip configuration setup on PC)

2\. Establish the local mount point using the mkdir command.  For NFS to complete a mount successfully,  
    a directory that acts as the mount point (or place holder) of an NFS mount must be present. This  
    directory should be empty.  This mount point can be created like any other directory, and no  
    special attributes needed for this directory.

3.  Enter --  
          mount ServerName:remotedirectory\\\\ /localdirectory  
    eg:  mount roland:c:\\\\ /pc

    where ServerName is the name of the PC, remotedirectory\\\\  is the directory on the PC that you  
    want to mount, and /localdir is the local mount point, or directory

To look at RS6k from PC:  
  1. nfsctl must be running on PC  
  2. must export directories from 6k that you want to work with  
  3. mount drive: remotesystem directory -----> eg: mount f: volleyball /tmp  
  4. at USERNAME and PASSWORD prompts hit ENTER.  DO NOT ENTER UID ? PW

MatLab program install -- cannot be run from a typescript; has to be an aixterm or xterm.  
                                       it sues the cursor library.  06/98 dkm

Standalone systems

If you cannot determine if a workstation is a standalone, do a cd to /usr/common/config.  Do an ls on this directory.  Depending on the  
version of AIX the ws is on, you can grep for it in one of the files listed (example,  
a workstation on 4.1.4.1  -- cat cfs.rs\_aix41 | grep ?workstationname>).

On standalone 4.1 systems , the man (info) pages have not been installed (they needed 200m).  If a user  
wants them installed, telnet to the workstation using their root password, do a lsvg rootvg to make sure 200m  
is available. then issue the command  
        mount  -o  soft  -n  stingray  /aix  /mnt

Then go into smit and custom install.  Input file is /mnt/414/lpp and use F4 for list of info items  
to install.

On standalone systems, some AIX lpps are not installed. x\_st\_mgr is one of them. If a standalone system would like to have an xstation  
logged off of it, you must install the lpp. To install the lpp you need to set up a mount to stingray (sw repository) and then install x\_st\_mgr  
via smit. To mount:  
/etc/mount -o soft -n stingray /aix /mnt

Logging onto stand-alone machines:  log on as root -- password is "default"

Diagnostics/Troubleshooting Down Systems

To enter in IP address and name of system when ctrl-c not working or system down:  
You boot the system up, unattached, and when you do the ctl-c, you type in NOAFS to boot it without afs. Then it boots up, you have the  
login prompt, you go in as root, and go into smit mktcpip, or run mktcpip from the command line.

To get into filesystem when system is down:  
bring up w/boot diskettes (service mode)  
@ menu, select limited shell  
@ shell, 'get rootfs'

/usr should NEVER be at 100% used.    Sometimes filesystems such as "/" or "/var" fill up.  
(The "/" could be due to the /etc/passwd file growth.)   It is helpful to be able to identify the largest  
files in the filesystems to see if anything can be removed.  
1\. Telnet to the workstation as root.  
2.  Issue this command:   ~csc/bin/find.big.files ?filesystem> -h  
 where filesystem could be /, /usr, /var, /tmp, /var/cache, or any filesystem

"find.big.files" will create a list of the biggest files in the specified filesystem (only).  It will not  
traverse into other fs nor into AFS, DFS, or NFS.    Sizes will be in bytes.  Largest files will  
appear first in the list.    (For more information, see append on priv.csc.helpdesk by Dave Nordgren,  
dated 04/06/98).   04/98 dkm

"command is respawning too rapidly" usually indicates one of the entries in /etc/inittab is crashing and restarting. In some cases , this is a  
DCE processes - is DFS working on that machine?  10/98 dkm

Credentials cache IO Operation failed XXX (DCE/KRB)"  indicates /var is full   01/99 dkm

Cache info - 3.2 ? 4.1 Systems

To flush the cache  
cat  /usr/vice/etc/cacheinfo to find present cachesize  
fs setcache 1000 to flush the cache.  
after the cache is reduced do a fs setcache 'size of cache returned from cacheinfo'.

If you do listing on volume and some files are not seen/found, try flushing the cache of the host machine.

"cache partition is full" (after 4.3 installs) should be solutioned with these steps:   02/99 dkm  
   1) telnet to workstation as root  
   2) use this command -->   df -k /var/cache    (write that number down, example -- 500,000)  
   3) calculate 85% of this number (exampe -- 85% of 500,000 ==>  425,000)  
        caches have 15% overhead, so we need to make allowance for this  
   4) get numbers from these two commands  
 a)  cat /usr/vice/etc/cacheinfo   (example -- 400.000)  
 b)  cat /etc/dce/CacheInfo (example 200,000)  
   5) add the above two numbers (400,000 + 200,000 = 600,000).  If the sum (600,000) is  
       greater than the 85% number (425,000), this will cause caching to crash.

   To correct:  
   1) take the 85% number (425,000) and subtract the dfs cache (200,000)  
       (example-- 425,000 - 200,000 ==> 225,000, giving you the truly correct cache number)  
   2) take care of the currently running environment by issusing this command  
 "fs setcache 225,000"  
   3) then to take care of permanently, you will need to vi  /usr/vice/etc/cacheinfo,  
       and plug in the correct cache number (example 225,000)  
   4) reboot the workstation.

To flush a volume from the cache ----  
run fs flushvolume: flush all data in volume  
Usage: fs flushvolume \[-path ?dir/file path>+\] \[-help \]  
 

To increase cache:

 1.  telnet to user's workstation, sign on as root

 2.  Use lsvg rootvg to see available free space.  (Showconfig  
     will not work if customer has more than a rootvg file system.)

 3.  showconfig to get the following pieces of info:

     a) AFS Cache Usage:  xxMB of total xxMB  
     b) DFS Cache Usage:  xxMB of total xxMB  
        (can also use cachesize query to find present cache sizes)

     c) Are they a current DFS user?  Can we steal from their DFS  
        cache?  Check to see if "Package File: /afs/rch/wsadmin/etc/prod"  
        says either preproddfs or /etc/dev.  If it does, then they are  
        more than likely using DFSs -- do not steal from that source

       On 4.1 systems, 20M of the /var/cache is allocated for DFS.

 \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
 STOP -- go on to the next step ONLY if space  
                available is more than 20M.  
                if none is available, could also check  
                paging (lsps -a).  
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

 3.  go into smit (physical and logical storage, file systems,  
     add/change/show/delete file systems, journaled file systems,  
     change/show characteristics, select /var/cache).

      -- time for math;  if free space is 40MB, in SMIT it will be  
          appear doubled (in 512-bytes) -- 80 512-byte blocks.

      -- you will want to leave 20MB, so you know out of 40MB free,  
           you have 20MB to work with.  Now double that in get into  
           512-byte blocks.

     -- add 40 to the total showing under SIZE of file system.

 4.  Once that is increased, pf10 to exit smit.  Do lsvg rootvg

 5.  If you are going to steal from DFS cache, do it at this time  
     by using the cachesize dfs ?reducedvalue>.

 6.  Now it is time to increase afs cache.  Use  
     cachesize afs ?newvalue>  ... newvalue should be the combination  
     of the dfs cache that you "stole" and the amount you increased  
     in smit.

 7.  In order to activate the new cache, either reboot the workstation  
     or use the command "fs setcachesize ?newvalue>."  
     This is just to set cache for the current session.  After reboot, cachesize  
      will come from the cacheinfo file.

 NOTE:   1 Megabyte == (1)x1024  (under lsvg rootvg - free partitions)  
              1 Megabyte == (2) x 512  (under smit)

         ------------------------------------------------------------  
                  Old instructions for increasing cache (before 10/10/96):  
                   - cat  /usr/vice/etc/cache info to find present cachesize  
                   - increase size in cacheinfo. (vi /usr/vice/etc/cacheinfo) ,  
                     size in cacheinfo should be approx 12% less than  
                     size in /usr/vice/cache (size in smit)  
                     (ex. /usr/vice/cache from smit = 100mb /usr/vice/etc/cachinfo = 88mb  
                  - Go into smit increase the size of /usr/vice/cache (/var/cache on 4.1)  
                     New size in cacheinfo plus 15% (increase 100000 to 115000)  
           ------------------------------------------------------------.

One thing to check:  that the /usr/vice/cache filesystem is mounted. We have seen some number of workstations in the past that have  
started AFS without the filesystem mounted.  Go into smit, physical...,  
logical volume mgr, logical volume list.  If they do have filesystems not mounted, ask if they need them.  
If not, get rid of it to get that storage.

A.  boot without afs......  
     1.  go to /etc  
     2.  ls init\*  
     3.  cp inittab inittab-afs  
     4.  mv inittab-noafs inittab  
     5.  cat inittab and verify that afs daemons won't be started

B.  umount /usr/vice/cache  
    1.  ls /usr/vice/cache  
    2.  cd /usr/vice  
    3.  rm -r cache  
    4.  mkdir cache  
    5.  mount /usr/vice/cache

C.  Do opposite of A (ie, boot with AFS)  
     1.  cp inittab inittab-noafs  
     2.  mv inittab-afs inittab

AIX LPPs

3.25. LPPS are stored on camaro  
4.1.4 LPPs are stored on stingray

SNA: (3.2.5 systems)  
mount -o soft -n camaro /aix /mnt  
/mnt/325/lpp/snaxxxxx  
umount /mnt

Post to advisor.general for questions regarding SNA -- fixes will be supported, but  
other than that, support is limited.

Netbios Docs:  
  \[Netbios Install 3.2.5 Documentation\]RUN:ez ~csc/support/netbios.d  
  \[Netbios Install 4.1.4 Documentation\]RUN:ez ~xr2/admin/procedures/netbios.product.install.414.doc

xr2 -- this is a problem with the netbios install which is suppose to set 777 into the  
          /etc/mcstab.  If you get a call that xr2 will not come up, telnet to the affected  
          workstation as root and do "chmod 777 /etc/mcstab."

Put lpps in /usr/sys/inst.images

lslpp -l will list the licensed program products on your local machine  
lppchk -v will verify your software validity  
 

TCP/IP - name resolution information

To find the IP address of a RS/6K enter ifconfig tr0

To see routing information enter 'netstat -rn'

use ctrl-c at "verifying IP address" to change the ip address

to find the hostname of a RS/6K enter hostname

To see latest copy of host file:  go to AFS /usr/common/etc/hosts.  This file is on AFS, not the local disk.  (the whole path is  
/afs/rchland.ibm.com/common/prod/etc.  SU to root and you can copy the file to the local workstation.  
 

Process information

KPROC - kernel process that is always running.  The process ID of 514 indicates kproc as an idle process.  Note that the %CPU reflects  
the % of CPU time used since start of kproc process

DOSPRT:  
processes by J.Greene, Hien, tool to monitor stats on AFS time/rpc's.  
shouldnt' effect CPU status very much

to look at the size of the processes, ps avxw (look at pagein's and size column)  
ps aux list processes

Performance/Virtual Memory

to increase page space:  
SMIT WSINSTALL or

 Go into smit select the following  
   physical ? logical storage  
   logical volume manager  
   paging space  
   pages are 4meg each

Compilers, libraries

If you see an error of this type:  
Could not load program /usr/local/bin/gs  
Symbol XtStrings in ghostview is undefined  
Symbol XtShellStrings in ghostview is undefined  
Error was: Exec format error

dump -H /usr/andrew/bin/help (the actual executable) (eg: dump -H /usr/local/bin/rchbak)  
Look to see if function is loaded as part of its library. Go to /usr/lib.  Run nm -e libXm.a (or whatever library you are looking in) and grep for  
the function that you are looking for. EG: nm -e libXm.a |grep XmStrings

xlc libraries and includes:

/usr/include  
/usr/lib

License server for C-compiler   (07/30 rdl)

File which contains pointer to site license server - /etc/ncs/glb\_site.txt

To see if header is included, look in /usr/include. Also do lslpp -f and grep for .h file.

xlc help (xslC for C++) can be obtained via infoexplorer and also by dv2init and then help xlc  
info -l cset

To see level of Compiler that you are using:  
 what /usr/lpp/xlC/exe/xlCentry

Misc. AIX helpful hints

Callup on AFS   (06/98 dkm)  
    Rochester Callup entries get  updated every night.  
    Offsite Callup entries are updated once a week on Sunday.  
         You can use the following command to verify that offsite users are  
          in okay -->  call -l xxxxxx   yyyyyy  (where xxxxxx is the name of the  
                                                                   offsite directory, and yyyyyy is  
                                                                   person's last name)

To get serial number of employees on AIX, use the following:     01/99 dkm  
    $  call -l rochester -c'name,serial' harrison bill

                   name                                              serial  
                   Harrison, William O.                          240637

To find out if they are a manager:  
   $ usr/local/bin/call -c ismgr,mgr -w "serial='120818'"

Flickering display screen:  
   1) find out what type of graphic display screen they have  
   2) telnet to workstation as root and go into smit  
   3) under devices, then under graphic display  
   4) select display types and put correct type in there  
   5) reboot workstation

LED codes: help rs-leds

To list bootdevice:   /usr/sbin/bootinfo -b

bootlist: Alters the list of boot devices (or the ordering of devices on the list) available to the system.

to view systems at 4.1 level: grep 4.1.xx.xx /afs/rch/common/config/cfg.all. where xxx= software level  
4.1 Test system: protozoa

Finding machines with 4.1

        1) telnet to dispatch  
        2) smit nim  
       3) Select Manage Resource Objects  
        4) list all machine objects  
        5) f4 - select standalone

to find out how many systems are still at a certain level , you can issue the following command: grep 3.2.5.x   /usr/common/config/cfg.all |  
wc

To look at log of who has been on your system, go to /tmp, ls -al

Looking system error logs:  
 1) telnet to host  
 2) type: errpt - locate the error number and copy it using the mouse.  
 3) From the prompt type: errpt -a -j (error number)

To clear the errpt:  
 type: errclear 0

You can perform all functions under SMIT as root when you are at the greenscreen.  
You are acting as root within SMIT.  You are NOT acting as root for anything else.

To install an ASCII terminal:  
Need to do setup on the terminal itself, (ctrl-setup)  
Need to do setup on the RS6k via smit:  
smit, devices, tty, add tty, tty rs232, sa0,  
port number s1,  
terminal type (if 3153, wyse60; if 3151, ibm3151)  
enable login  
\*note\* the terminal cable needs to have a 'null modem' plug that attaches to the monitor and the cable. This null modem does some pin  
swapping.

RSH command will let you run processes on another machine:  
 ex: rsh (hostname) ls -a  
  rsh (hostname) errpt  
  rsh (hostname) ps -aux

Last reboot  - rsh 'machine name' w

DOSREAD:   To read diskette files --  
                     DOSREAD has two argumnets, the name of the file to be read and the  
                     name of the file to which it should be copied.  
                           > dosread    file.dos    file.from dos  
                           > ls -l file.from.dos

                     The  file size and content are unchanged

DOSWRITE :  To write an AIX file to diskette --  
                          > doswrite    file.aix    from.aix

DOSDIR:   This tool is provided by AIX to list the files on a diskette.  
DOSFORMAT:  This tool is provided by AIX to format a blank diskette for use by DOS.  
DOSDEL:   This tool is provided by AIX to delete files on a diskette.

dosreadall  /usr/contrib/bin

dosformat --> to format diskettes on RS/6000

echo $CLASSPATH gives the paths in effect  
 

Ultimedia Adapter Card: these are sound cards; device is baud0. The UMS software needs to be installed if using the card on a 3.2  
system. On 3.2 or 4.2, you need to also create this link: ln -s /dev/baud0 /dev/acpa0.  
 

Using the CD-ROM on an RS6000  
 

1.  User should shutdown workstation  
2.  Plug in cdrom and turn the cdrom on  
3.  Power up workstation  
4.  Make sure that there is a CD-ROM installed and defined on the RS6000  
 a) Log onto the WS as root  
 b) Run smit  
 c) In smit choose:  Devices ->  
                                       CD ROM Drive ->  
                                         List All Defined CD ROM Drives  
 d) The output should look something like this:  
           cd0 Available 04-C0-00-3,0 SCSI Multimedia CD-ROM Drive

       note:   If a CD-ROM drive is not defined you must choose  Add a CD ROM Drive

5.  Before the installed and defined CD-ROM can be used you must mount the CD-ROM filesystem  
 a)   in smit, choose:  System Storage Management (Physical ? Logical Storage)->  
                                         File Systems ->  
                                          Add /Change/Show/Delete File Systems ->  
                                     CDROM File Systems ->  
                                                Add a CDROM File System  
 b)   You should have a screen up with three fields:  
   DEVICE name:  
   MOUNT POINT:  
   Mount AUTOMATICALLY at system restart:

                -- The DEVICE name is the name of the installed and defined cd-rom,  
                     the easiest way to specify the DEVICE name is to use the  list command (pf4)  
                      to choose from a list of defined  cd-rom names, a typical device name is  cd0.

        --  The MOUNT POINT is the directory path that the user is going to have  
                      to cd to in order to access the data on the cd-rom, you   can call this  
                     mount point anything that you want, most people call the mount point  
                     cdrom because it is easy to remember.

      -- Mount AUTOMATICALLY at system restart:  no  
   should be "no"

  For Example:  
   If you make the mount point:     cdrom  
   a filesystem called cdrom will be created off the   ' / '  directory on the RS6000

6.  Exit smit and have the user type:   rroot mount ?filesystem name>  on the RS6000 that  
you want to use the CD-ROM drive.   For Example:   If in the previous step you called the MOUNT POINT   cdrom  the user would type:  
rroot mount  /cdrom  on the RS6000 that you want to use the CD-ROM drive

7\. To access the cd-rom in the drive  the user will have to cd to the directory path that the filesystem was mounted.    For Example:  If in  
step 4 you made the MOUNT POINT  cdrom, the user would type:  cd   /cdrom    this would change there current directory to the cd-rom  
drive.

Once in the cdrom directory the user can do such things as:  ls,   cp,  ez ?filename>,  and many more commands.

NOTE:  You must have a cd-rom in the drive before you can cd to the cdrom directory!!!!

8\. To open the cd-rom drive and remove the cd, you must UNMOUNT the file system. To do this have the user type: rroot umount  
?filesystem name> on the WS. The door to the cd-rom drive will then open when the button is pushed.  
 

Cannot telnet to machine, get msg: telnet: connect: A remote host refused an attempted connect operation.  Means that the the process  
that is supposed to accept remote connection is not running.  The process is inetd, which then starts telnet. Reboot to start process.

Catastrophe in realloc: invalid storage ptr -- starting and stopping inetd should fix this problem.  06/98 dkm  
          stopsrc -s inetd  
          startsrc -s inetd

Archive data to tape.  
tar -cvf /dev/rmt1 filename  
tar tvf /dev/rmt0 - to list table of contents

To list directories and files tar tvfZ x.tar.Z where x.tar.Z is file name.

To uncompress a tar file, simply key uncompress ?filename>     05/98 -- dkm  
To uncompress and build directory structure starting with current directory( directory currently cd'd too) and load files tar xvfZ x.tar.Z

.Z is a compression operator for postscript files.  In order to print one of these files, it must be decompressed  
first.

tar -xvf /dev/rmt0 - to uncompress a file.  
device needs to be defined and available.

May need to do gunzip first if it has a naming convention like n405.tar.gz; then do the tar -xvf command.  
08/98 dkm  
 

Crontab

To add new jobs to crontab execute crontab -l  save those values in a file 'filename'. (Example--> crontab /tmp/test).   Edit file 'filename' (eg,  
/tmp/test) to add the commands needed. Then execute crontab 'filename' (eg, crontab /tmp/test) to set those values in user crontab file in  
/var/spool/cron/crontabs/'userid'

Help crontab

crontab -e  
vi filename  
crontab filename

If the cron jobs are not working, be sure to check permissions for system:anyuser.  It should be  
system:anyuser rl        05/98 dkm

For adding root crontab jobs (such as /etc/reboot): you will need to create a root.local file. This crontab listing will be appended to the root  
crontab file at each reboot, otherwise the reboot wipes out changes made to the root crontab job.

Seeing this error:  
\# crontab -l  
crontab: 0481-109 You are not authorized to use the cron command.  
Look in /var/adm/cron. Look for a cron.allow file. See who is in that file.

FYI -- each AFS/DFS workstation has a crontab set up that has "wsupdate" in it.  The purpose of  having this in the ws crontab jobs is to  
give AFS/DFS team a way to propagate changes to all workstations overnight.

'/usr/local/bin/rroot wsupdate'  will correct problems with passwd files that are not updated correctly.  
 

Problem logging on to machine:

 symptom:  
  1) User trys to log on and gets a % sign (percent) for a prompt.  
 possible solution:  
  1) This usually means that the user can not access their home directory.  Check to make sure that he has his .login , .cshrc or .kshrc and  
all other basic login files.  If these  are missing try and see if they are in the .OldFiles if not there have customer submit a request to  
Andrew-Request to have his Volume restored.  
                  2) Another possibility is that DCE is not running ... log on as root  
  a. Telnet to the workstation  
  b. run "df" . Check if /var/dce is at 100% full.  
  c. If at 100 % run  "~csc/bin/find.big.files /var/dce"  
  d. look for the biggest file which is usually a core file and do a "rm ?file name>"  
  e. ask customer to log out.  
  f. run dce\_health.  
                    (RDL 03/28/01)  
 

AFS

If someone is coming up without AFS, you can telnet as root to their workstation and issue the  
following command:  /etc/startafs   (this should get them started or give you an error message).

Also, if AFS is not running on a machine, check the  /etc/environment file. Check the size of the file against a working machine. You may  
have to ftp the /etc/environment file from a working machine.  Make sure the versions on the two machines match.

FS command: file system -- type fs help for more information

fs sa set access rights

Removing negative rights, or restoring rights you have denied:  
If you have denied a user access to a directory by using "-negative", you must also restore the rights using -negative. EG: fs sa  
/afs/andrew/usr/jbRo/notes -negative spillman none

fs la  list access rights  
fs lq  list quota and shows what volume you are on  
fs sq  increase user's quota of a tdisk or volume  
fs lsm  list all volume mounts  
   eg: fs lsm ~spillman/\*  
vos listvldb ?results of fs lsm>  
adu -vk ~winterfi | awk '$1 > 10000'  to find out what files are over 10M on userid's home directory  
                                                          before doing a volume split.   10/98 ram  
fs rmm -dir remove mount point  
vos remove -s ?machine name> -p ?partition name> -id ?volume name or id>  to remove volume  
fs lv  list volumes  
fs checks  checks status of servers.  Is run on cache mgr. every 3 min.  If a server goes down and comes back up and you don't want to  
wait the 3 min,. then telnet to host and run the fs checks command.  
Another command that can be run is:   rxdebug ?server> -noconns (where server is like rios19).  The last  
line shows the number of waitprocs, and it should say "0 calls waiting" if everything is okay.   05/98  dkm  
fs whereis  tells what server you are on  
   eg: fs whereis ~spillman  
 

VOS command: volume server (/usr/afs/etc/vos) -- type vos help for more information

vos e volname   shows what server you are on  
     eg: vos e user.spillman  
     eg: vos e user.belt.backup shows last time .OldFiles were backed up

If you see this error from a 'vos e', for example:  
 Could not fetch the information about volume 541277182 from the server: No such  device Volumes does not exist on the site indicated by  
the VLDB  
       It means that the VLDB is not in sync with server.  This means that the VLDB does not know about the volume that REALLY does  
exist.

       Issue the  following commands:

       1)  grep  VOLUME ~tapebk/reports/data/listvol/DATE  
           (date is of form: yyyy.mmm.d\[d\], and should be today's date    e.g. 1997.Jun.7  
       2)  from the previous command determine server and partition of the volume  
       3)  run ~admin/bin/chkvldbvol SERVER PARTITION (where SERVER and PARTITION are from step 2)  
       4)  The only volume that should be listed in step 3 is the one on which you are working.  
           If there are multiple entries, consult with the AFS team  
       5)  IF there is only one volume listed from step 3, run '/usr/afs/etc/vos syncvldb SERVER PARTITION -v'  
       6)  Check the output from step 5. There should only be one line with 'invalid' in it, and it should  
           be for the volume you are processing.  
 

If you see the following error message (highlited in red):

    ls -alt  
    postpd\_vim: No such device  
    Total: 13 kbytes  
    d           2 goziemki                 2048 Jul 15 09:42 goziemki\_tdisk

it means that the volume either no longer exists or that the VLDB is not in synch with the server.  You should use the following command to  
determine the volume name, and then you should do the above procedures starting with the 'vos e' (volume name highlited in red):

    fs lsm postpd\_vim  
    'postpd\_vim' is a mount point for volume '#x.409pe101002.v2cib52'

vos listvldb   shows what server you are on  
     eg: vos listvldb user.spillman  
     eg: vos listvldb -server rios80 | pipescript

If you are unable to get to the entire file path -- do a cd as far as you can.  (example --> entire path  
is /afs/rchland.ibm.com/rel/common/proj/ioasim/dram/prod/,  
but you can only cd to /afs/rchland.ibm.com/rel/common/proj/ioasim/ --  
then do fs lsm dram to find out what volume that file is on.  Should be able to do a  
vos listvldb on that volume.

Volist- list volumes:  
set volist = \`grep "rios36 /vicepi" ~tapebk/reports/data/listvol/1995.Feb.15.00 | grep RW | awk '{print$3}'\`  
echo $volist  
foreach volume ($volist)  
vos ex $volume >>?! /tmp/check  
end  
vi /tmp/check

PTS command: protection server -- type pts help for more information

pts cg   creategroup eg: pts cg frerichs:frerichsgroup -o frerichs  
NOTE:  normal users (w/out admin) must give their group a prefix.  The pts server will not accept a group name with out a prefix.

pts createuser   createuser If someone had deleted their ID, but their orphaned ID number still exists and you want to restore it, do a pts  
createuser and specify the id.  
eg: pts cu spillman 25620

pts ad    adduser eg: pts ad -u spillman dianem -g frerichs:frerichsgroup

pts chown   change ownership of a group  
 

BOS command:

to check status on a server: bos status ?servername> gives you status on server -- eg: bos status rios23

MOUNT POINTS

To list mount points under home directory:  
 unmount .OldFiles  
 find . -type d -exec fs lsm {} \\;  
 remount .OldFiles

ERROR: NO SUCH DEVICE: Probably means that the file is a mount point for a volume that no longer exists. Do a fs rmm on that  
directory.

OLDFILES

To mount a backup volume:  
 fs sa ~kewegner/dev2000 spillman write  
 fs mkm ~kewegner/dev2000/.OldFiles duser.kewegner.dev2000.backup  
 fs sa ~kewegner/dev2000 spillman none

QUOTAS

bumpquota:    increase user's volume size

To increase Quotas on a tdisk or a volume use:  
 fs setq -max ######  
 ex: fs sq ~spillman/libuser 100000

Customer' can now increase quota on any volume they have write access to with this command.

 /usr/local/bin/volumemgt resize ~/directory name \[QUOTA  specified in k bytes\]     quota is option  (default is 25 meg and max is 300 meg)  
rdl 11/24/99

To find the largest files in their volume use  
 find . -type f -ls -xdev | sort -nr -k 7 | awk '{print $7"\\t"$11}' | pipescript  
this will open a pipescript containing all the users files listed in order by size (use heysend to send to a  user)  
 P.A.M. 5/15/98  
 

TDISK  
Tdisks by definition are not backed up.  Therefore, the only way that the data would be recoverable is if by some freak chance the volume  
did not get removed yet.  I checked it out (might as well), but the data had been deleted.  Once a volume is removed by vos remove it is  
gone - no getting it back (except from a backup copy)

command syntax:

     tdisk create directory \[size \[days\]\] \[-a \[ACLdirectory\]\]  
       size is specified in 1K blocks and must be between 1 and 200000  
       default size is 25000  
       days must be between 1 and 14  
       default days is 1

     tdisk delete directory

 Remove tdisks: ---that are hanging around after tdisk delete  
     fs rmm ~admin/tdisk/volumes/'tdiskname'  
     rm ~admin/tdisk/mounts/'tdiskname'  
     vos ex 'tdiskname'  
     vos remove 'server' 'partition' 'tdiskname'

     tdisk query \[userid\] \[-s\]  
       where -s indicates to just print volume name, erase date, and mount point.

     tdisk resize directory \[new\_quota\]

 tdisk extend extend tdisk life

    The correct syntax for tdisk.extend is: tdisk extend mountpoint newdate \[-c\] Where -c lets you do a test run  
    Where newdate is the new expiration date; specified as follows:  
    3 characters - 1 for month and 2 for day for January 1, use 101, for October 5, use a05, for November 15, use b15, and for December  
24, use c24  
   The tdisk will expire at 2:00 am on the specified day.  
   eg:  
   tdisk extend ~belt/projects/tdisk/test1 c30 -c  
 

To change tdisk mountpoint:  
     fs rmm ~'olddirname'  
     fs mkm 'newdirname' 'tdiskname'  
     vi ~admin/tdisk/mounts/'tdiskname' --- change the user mountpoint to 'newdirname'

Exempt a server as a TDISK server.  
check to see if the server is a tdisk server you enter the command - grep (servername) ~admin/bin/partinfo/serverlist

make a server exempt form the tdisk pool - ~admin/bin/partinfo/request.part chgstat (servername) exempt  (if you make a server exempt  
make sure you send Jennie Belt or someone on the afs team a note that you have made that server exempt.)

TDISK MONITORING:  
A program that goes out every 1/2 hour and checks out the activity on the tdisk servers which are currently tapebk3, tapebk5, tapebk1, and  
tdisk2.  If any are overloaded, a lock file will be touched called /tmp/tdisk.lockfile.  This will tell the machine not to accept anymore requests  
for tdisk.   Five minutes later the lockfile is removed.  This gives the busy machine time to catch up with the many requests.

 Here are examples:

Before the  program uses rsh to execute "touch /tmp/tdisk.lockfile" on the busy machine, you will get this type of a hey:

Tue Feb 21 09:45:06 CST 1995 tapebk1 may be experiencing a slowdown, touching locks file /tmp/tdisk.lockfile

After the rsh command, you will get this type of a message:

Tue Feb 21 09:46:36 CST 1995 locked tapebk1

About five minutes later, you will get this type of a message:

Tue Feb 21 09:51:54 CST 1995 removed lockfile /tmp/tdisk.lockfile from tapebk1

Note that depending on how slow the machine is running, the time between the first and the second heys could be several minutes.

If all but the overloaded tdisk server machines have lockfiles on them, the overloaded machine cannot be locked and you will get a hey like  
this:

tapebk1 is experiencing a slowdown, but couldn't lock it because all of the other tdisk servers have the lockfile /tmp/tdisk.lockfile

This has never happened, but if it does, you can check out the activity on all of the tdisk servers which are listed in  
~admin/tdisk/config/tdiskservers and remove lockfiles on the least active machines.

After this monitoring program checks out all of the activity on the tdisk servers, (adding and removing lockfiles if needed), it will send the  
results to the bulletin board priv.admin.tdisk.  You can check out the posts with the subject tdisk processes.

Blue Pages Queries  
ldapsearch -h bluepages.ibm.com -b "ou=bluepages,o=ibm.com" ibmserialnumber=?serial#>

ldapsearch -h bluepages.ibm.com -b "ou=bluepages,o=ibm.com" uid=?serial#>?country code>

ldapsearch -h bluepages.ibm.com -b "ou=bluepages,o=ibm.com" sn=?last name>

SECURITY--Administration

 If someone has a need to have a userid created TODAY rather than overnight, the  
       "~uidadm/bin/createuser.pl uid" command  can be run from your admin userid.  You may  
        need to issue the "vos release root.usrx" (where x is 0,1,2,3,4,5,6,7, or 8) if you  
        cannot cd to the home directory after running this command.  (02/98 -- dkm)

To see log of admin activities:  ~admin/private/\*activ\*

System Administrator Procedures can be found on NetScape -->  
    [http://d27db001.rchland.ibm.com/p\_dir/pctips2.nsf/ef670a05f97c6e8e862567c3006d69ec/04881103d2e8ba75862568e7006fa18e?OpenDocument](http://d27db001.rchland.ibm.com/p_dir/pctips2.nsf/ef670a05f97c6e8e862567c3006d69ec/04881103d2e8ba75862568e7006fa18e?OpenDocument)        (02/98 -- dkm)  
 

andrew-request  (rchland)

  1) Tdisk request.  
  2) Volume request (deletion, creations, restoration).  
  3) Quota requests.  
  4) AFS/AIX request that is not sent to afsadmin.

Volume Splits --

Following information is needed for volume creations:     06/98 dkm  
 1)  Path  
 2) Mount point (nonexistent directory)  
 3) Size of volume (up to 100M)

AIX users, who want more space because of their ~/notesr4 (Lotus Notes directory) will need to do volume splits. There are all kinds of  
subdirectories where the volume split can be done. Please, use a tool like '/usr/local/bin/adu' or '~rawales/bin/du.volume' to assist the user  
in deciding where to split the volume.  
Please, observe the standard 100M volume limit in dealing with these requests.   All exception requests should be sent to the AFS team  
(Rich Wales).

Token Extension--  
If a user needs to have the token lifetime of one of their userids extended they should send a note to rchaix@us.ibm.com - If you come  
across a token extension request on a bboard please forward that request to rchaix@us.ibm.com.

If  you want to do the extension yourself please use ~admin/bin/admin\_tasks (select the "Tokens"  button on the main menu)  and then file  
the note in the tokenext notelog on afsadmin.191.  The admin\_tasks tool  updates the admin activity log and sends a confirmation notice to  
the user that requested the change.

Passwords

           passwd command to change password.

          To change password for wincent -- RCHDNT, use this url: \[pc passwd\]?URL:[http://w3pclan/cgi-bin/pwchange](http://w3pclan/cgi-bin/pwchange)\>    (02/98 -- dkm)

           If alt\_passwd does not work use: /usr/local/bin/kpasswd -x root-wsname-rchland-ibm-com.  
        or  kas setpassword root-workstatonname-rchland-ibm-com newpassword -admin adianem  
           -password\_for\_admin   adminpassword

           To see alt-root for a particular machine,  
            do a pts mem admin:root-volleyball-rchland-ibm-com

           To reset login access for users which has been locked after 5 trys:  
               /usr/afs/etc/kas unlock (userid)            (02/98 -- dkm)

            If this does not work, you may need to telnet to their workstation as root.  
            Then go into smit, select "Security ? Users," then select "Users", and then  
            "Reset User's Failed Login Count" -- just fill in the userid and press ENTER.  
            This will reset the userid's failed login count back to zero.  
 

           To kas unlock alternate root  
            kas unlock root-ciscoe-rchland-ibm-com where ciscoe is the workstation name

To change password in another cell:  passwd userid -c cellname.

EG:  passwd spillman -c austin.ibm.com.  OR, you can telnet to a machine in that cell, log in as

the userid to the cell, and run the passwd program.  
   
   
   
 

To change your Rochester AFS password from another cell:  
kpasswd userid -c rchland.ibm.com

To run the reset yourself: ~admin/bin/reset\_pw

To change the amount of time before the password expires for a particular userid, go into kas and issue the following command:  
  "setfields -name ?userid> -pwexpires ?number of days>"

To look for a workstation in another cell:  grep austin /usr/vice/etc/CellServDB  
CellServDb file: each workstation has a copy in /usr/vice/etc/CellServDB

If there is a CellServDB problem:  
  First fix --> 1) telnet ?name of workstation>  
                      2) cp  /afs/rch/common/prod/etc/CellServDB   /usr/vice/etc/CellServDB  
  Second fix -->  1) reboot  
                            2) verifying IP address .... ?ctrl+c>  
                            3) "do you want to modify current settings y/n" ....NOAFS  
                            4) "do you want to do this?" ....y  
                            5) "do you still want to modify setting y/n .... n  
                            6) ftp ?your ws>   login as root  
                            7) get /user/vice/etc/CellServDB  
                            8) bye  
                            9) check file   cd /usr/vice/etc/  ; ls -al  
                           10) /etc/reboot

to be able to display windows from other workstation xhost +in typescript of local machine.  
Once connected to remote machine in telnet window issue the following----  
on csh use  setenv DISPLAY A:0   A is machine where you are sitting(viewing)  
on ksh use  export DISPLAY=A:0

The xhost command adds and deletes hosts on the list of machines from which the X Server accepts connections. This command must be  
executed on the machine to which the display is connected.

.Xauthority file:  
The new X security mechanism uses it. Everyone should have it unless they runx -nosecure.  
It is in private because it contains a humungous random number that clients must present to the server to connect. That means AFS  
protects your X server. runx, the Xstation and CD-ROM logins all create it.  This file is in your private directory. The file should have  
permission bits of rw-  
 

AFS Server Hints

to free up space on the servers use the program frlclfs to free up space on the servers when the disk space in one of these four local  
filesystems ( /usr, /tmp, /home and /var)  is low.  For example,  If the /tmp file system is being filled up,  you can type "frlclfs /tmp" to clean  
up stale files in that directory.

If /tmp is 100%, cd to that directory and try to find a directory underneath that has a large log that could  
be deleted.

AFS Helpful Hints ? Commands

/etc/startafs   to get AFS going on a machine after a reboot if AFS  is not there  
unlog to run without tokens  
klog  to refresh tokens

to access another cell   klog userid -c 'cellname'  need userid ? password in other cell to get at any protected data.

DFS note on accessing other cells:  
Cannot access another cell in DFS using the above command.   DFS/DCE only recognizes one identity  
at a time.  However, the need to access other cells is no longer needed with the way acls are set  
up will determine what others can see without accessing other cells.

To request a DFS userid on the Austin cell:  Use daat - [http://w3.austin.ibm.com/daat/](http://w3.austin.ibm.com/daat/)  
Click the login button to get a new DCE ID.     07/98  oester  
 

To view other cells in DFS:    ls  /.../austin.ibm.com/fs    (changing austin for whatever cell you want)

to start afs-nfs translator:  Touch file .translator ? reboot

to see a list of AFS servers contacted since last reboot : rxdebug lohr 7001 -onlyport 7000 -all|grep connect

to see a log of deleted volumes and the partition/server the volume was located: go to /afs/rchland.ibm.com/usr1/tapebk/reports/data/listvol  
\-- grep for the USERID from the date of deletion file

writeaccess - to find it.  
to get write access to directories  run ~admin/bin/write.access -name of directory

to move an AFS volume -- The bottom line is while using this flag in the move.volume command, you can request  
to have a volume moved to the lowest accessed server/partition in a group (i.e. prod,  
temp, eng, etc.) instead of moving it to the least booked server/partition in that group.  
The new syntax of move.volume is:

~admin/bin/move.volume  ?volume\_name> \[?server> ?partition> | \[-p ?pool>\] \[-perf\]\] \[-n\]

It is very important now more than ever to use move.volume whenever moving a volume,  
since the database will now update the accesses for a partition with every volume move  
along with the space.

to check on volume which where lost due to server problems - telnet to tapebk5  and  enter cat /tmp/listvldb. This will show you the  
volumes that are queued for restoration.

to release a volume:   volumemgt release /usr/local/bin

to delete a volume: run "~admin/bin/delete.volume -d directory"  
This will remove the mount point and schedule the volume for deletion.  
This keeps us from having to do tape restores in case someone else wants the data.  
See  the ADMIN procedures guide for more detail.

to bring up  EZ WINDOW for setting AFS rights: ezafs

to set recursive permissions use the ws (walk subtree)command to propagate ACLs  
to many subdirectories (help ws).  02/98--dkm  
 ws ?directory> -d "fs sa %f ?userid> ?access rights>"  
 eg: ws  /afs/rchland.ibm.com/usr5/rgotto -d "fs sa %f rgotto write"  
Be very careful with the ws command when setting access rights.  You may want to run fsreport after using this command to verify access  
rights have been set correctly.  Execute help protection for more help on directory protection.

to list all the servers that are on the system and what there basic  
operational function is: cat ~admin/bin/partinfo/serverlist  Use the information that is shown using this command with the scout tool  The  
servers that we need to be concerned with are the ones that say prod or prg.

to search Error codes for AFS: cat /usr/include/sys/errno.h  
eg: afs failed to store file (13)  
grep 13 /usr/include/sys/errno.h  
#define EACCES 13 /\* Permission denied

to check status of hosts:  
~oester/bin/checkhosts  
~oester/bin/checkcalls

Changing User Names: /afs/rchland.ibm.com/usr5/rawales/howto/change.user.names.d.

ATK applications

aheyd

Problems with HEYs:  
1.  check to see if zhm process is running  
2.  check to see if aheyd or xheyd is running.

ZHM is started at boot times, there is one zhm process per workstation.  This stands for Zeyphyr Host Manager.  zephyr servers track the  
location of where the users is running the "aheyd" process and the hey processes uses them to locate where to send messages

AHEYD is started by user, usually in .xinitrc file.

Restart zhm and aheyd -  
 as root run /usr/dev/local/etc/restart\_zhm  
 have the user run /usr/contrib/bin/restart\_aheyd

NOTE: Do a zlocate on the userid to see which machine the user is logged onto.

Sending messages using heysend:  /usr/contrib/bin/heysend nordgren ?

Different ways to send heys:  (with a smiley face) ==> put in your .cshrc  file:  
                                                           alias heysm '~massaro/bin/heysm'  
                                           (with a sad face) ====> put in your .cshrc file:  
                                                           alias heysad  '~massaro/bin/heysad'  
                                           to send the last text you have in your "paste" buffer ==>  
                                                           heycut

if you want to hey part of a screen, use the following command, which will give you  
a corner bracket (use the right mouse button to drag the portion you want sent) --  
you will then be prompted who to send the hey to:

/usr/contrib/bin/xsnap -atk -noshow | xcut | /afs/rchland.ibm.com/usr4/massaro/bin/heysnd.rexx ?

to cut and paste a window --> xwd | xwd2atkimage | xcut     08/98 dkm  
   
 

calendar

Hard time reading your calendar  
From your $home AFS directory do a symbolic link to create a file called ~/Calendar.  The file ~/Calendar  file points to the VM node were  
you keep your PROFS calendar.  
ln -fs userid@nodeid Calendar

where:  userid - The VM userid that you use for your PROFS calendar  
  nodeid - The VM node where you keep your calendar

If you wish others to update your calendar then there are 2 ways that you can set up your PROFS calendar:

1\. Give all users the ability to view and change your calendar. Probably, only the nonrestricted data.  
2\. Give the user TCPCAL the authority to view and change your calendar.

If the customer is getting other calendars popping up on his unit, look in the .cshrc file for xhost +, which opens up his unit to allow anyone  
to put a window on his system.  Comment this out, and refresh his/her session.

If the data is coming from OV/VM, then TCPCAL will screen out CONF and PERS entries for everyone but the owner.  If storing the data in  
AFS, there's no way to control it - either others can see nothing or everything.  
If an entry is marked confidential or personal in OV/VM (under its rules), then TCPCAL won't show it to anyone but DCNAATZ on any  
Rochester node (including rchland).

ez -- Robert Kemmettmueller

To get help using ez, go to netscape and use this following path:  
"[http://w3.rchland.ibm.com/projects/dev2000/current/usered/AIX32/ez\_main.html](http://w3.rchland.ibm.com/projects/dev2000/current/usered/AIX32/ez_main.html)"

dv2 : dtez listens for 'edit' tooltalk messages and starts a new ez window when requested.  
It's the same as ez, except it's tooltalk-enabled.  When devmgr or the ez command sends a tooltalk signal, dtez hears it and pops open  
another window on that file.  (Side note: if the ez command can't find a tooltalk session (e.g. you didn't dv2init), it automagically brings up a  
regular ol' standalone ez session)

to create Footnotes within a ez section:  
  1) Use mouse menu option and select page  
  2) open footer, insert footer, close footer

MAIL

xagent service machine Steve Bussan, Marty Cormack

If mail can not be sent FROM vm TO rchland, but it can be sent from messages to the user on rchland, then the userid is missing from the  
tables on the rchgate system.  In Rochester, the user can register themselves to XAGENT by typing the following three commands from  
their preferred RCH VM node:

1)  SM RSCS CMD RCHLAND FORWARD ADDMAIL ?tcpid> MAIL0.RCHLAND.IBM.COM SMTP  
2)  SM RSCS CMD RCHLAND FORWARD ADDFILE ?tcpid> MAIL0 SMTP  
3)  SM RSCS CMD RCHLAND FORWARD ADDTELL ?tcpid> MAIL0 IMSG

In addition, either Bob Oesterlin and Diane McCaslin are authorized to issue registration requests for customers using the following:

1) SM RSCS CMD RCHLAND FORWARDU ADDMAIL ?vmid> ?tcpid> MAIL0.RCHLAND.IBM.COM SMTP  
    (OWNER vmnode vmid  
2) SM RSCS CMD RCHLAND FORWARDU ADDFILE ?vmid> ?tcpid> MAIL0 SMTP (OWNER vmnode vmid  
3) SM RSCS CMD RCHLAND FORWARDU ADDTELL ?vmid> ?tcpid> MAIL0 IMSG (OWNER vmnode vmid

This command will check on their mail status --> smsg rscs cmd rchland q u ?userid>

If additional help is needed on XAGENT tables, contact either Fred MacNear (8-293-8952) or Vivian Piper (8-293-7072) in  
Poughkeepsie.    Another name is David Rebovich (8-855-7678).

to change how name appears in 'from' field when sending messages, send a note to andrew-request asking the entry in /etc/passwd to be  
changed.

Bulletin Boards   04/98 dkm

Do not add new bulletin boards ... see Bob Oesterlin about putting possibl new bbs on LotusNotes.

BBoard locations:  ~bboard/.MESSAGES/priv

POSTING to extbboards:  look at help externalbb

deleting posts to bboards: Log onto uid postman, bring up messages and then delete the post. Passwd in /.Password on mail0

How to search for information on BBoards: /usr/contrib/bin/findmsg

to find out who owns a BB(bboard):   bbaccess  'name of bb'

to add someone to the access list of a bulletin board (like priv.admin.addusers), do a cd to ~bboard/.MESSAGES/priv/admin/addusers.  
Then as your admin userid, do fs sa addusers userid all.

RCV:

Doing rcv on the command line should bring files in from the Filebox directory.  If it does not, check  
for the following:  
1) make sure the user is logged as the userid that the files were sent to (example, if files were sent  
     to dianem, trying to rcv in adianem will not do it).  
2) if rcv does not work, try the following command "receive  ~/Filebox/\* ~/src".  This decodes the  
     first file in the queue and puts it input the src working directory.

the presence of .sendnomsg in Filebox directory will prevent the notification notice from being placed in your mailbox when you rcv files

to forward mail  wpi -A -u userid -f Fwd userid@node      02/98--dkm

to see if mail is being forwarded: wpq spillman (name)  you can also try: forward -r -u userid   02/98--dkm

if an account is disabled in wpq but should not be, issue this command from your admin userid:  
      ~postman/bin/unexpiremail ?userid>  (userid of the account that is disabled)

This is a program that actually edits the ~postman/wpbuild/hist/passwd.chg and deletes the two  
   lines referring to a disabled userid.  (THIS IS AN OVERNIGHT PROCESS.)

to forward mail to vm: Delegate

to cancel mail forwarding: forward -z  (this is an overnight process)

to display hey messages blownaway :    cat ~/private/hey.log

to create a message link button in a message:  
 1) Press the ESC + TAB key  
 2) Type: LINK  
 3) Use mouse to link and change button options

to fix messages after getting flames  have user run : ~oester/bin/reconstruct\_mail

to get runbutton in ez or messages escape/tab type runbutton at the prompt follow prompts after that.

to use a pts group as a mailing list:  
          To: "+fs-members+ptsgroupname"

zlocate -will show you which machine the customer is logged onto.

Sendfile  
To VM:  sendfile afs\_filename to vm\_userid@vm\_nodeid  
To AFS: from fulist: sendf / afs\_userid at rchland, eg: sendf / spillman at rchland

MIME:  Multipurpose Internet Mail Extensions  
 A new standards-track Internet format defined by an Internet Engineering Task Force  
Working Group, offers a simple standardized way to represent and encode a wide variety of  
 media types, including textual data in non-ASCII character sets, for transmission via Internet mail.  
AFS can handle MIME, but the mail needs to go the an AFS account, not a VM account.  
In Preferences file: mailsendingformat: ask Controls whether AMS clients write out data  
in the old (ATK) format or a MIME-compliant format.  MIME is a proposed Internet  
standard for multipart, multimedia mail.  The possible values for this preference are:

"ask" -- WHENEVER formatted mail is about to be sent out, regardless of any  
             format-forcing codes in a user's .AMS\_aliases file, give the user the  
             choice of the old Andrew or the new MIME format.  
"andrew"  -- behave as before, asking the user about sending formatted mail to  
                    non-local recipients, and using the old ATK data format whenever  
                    formatted mail is sent.  
"mime" -- behave as before, asking the user about sending formatted mail to  
                non-local recipients, but use the new MIME data format whenever  
                formatted mail is sent.  
"mime-force" -- Always use the MIME format, and don't even bother to ask  
                      about stripping to plain text.  This should become an increasingly  
                      plausible option as time goes on, if MIME support becomes  
                      widespread, because the MIME format Andrew generates always  
                      begins with a readable text-only version of the message.

NETWORK ? PERFORMANCE  
 

Network

to get to IBMNET   xant rchis1 ? or x3270 rchis1 ? then key in "nva"  
                   fill in appropriate information  (userid/password)  
                   next screen, key "ddf"

if user looks like they are having network problems:  
1) ping workstation  
2) do a grep on first 3 chars of ip address (ex, grep 9.5.55 /etc/network.config)  
     this will show the machine size and ring number, as well as other information.  
3) Check to make sure cable connection is tight.

"Noise on port" error messages: could mean that there is a bad IP address or a duplicate IP address. Have user power system off and see  
if you can still ping the IP address. If you find a dup. contact the network support persons to track down the culprit

If the user has both a PC and a RS/6K on a mulligan box, have them power off PC first.  Then disconnect at the way.  Plug it back in.  Do  
NOT power PC back up yet.  Reboot the RS/6K with the yellow  
button.  If this fails, then it might be time to call in the network team (Tracy Offutt 3-2764, Jay Welch 3-8809,  
or Ronda Marshall 3-1646).

Performance

Slow performance: some things to look at:  
1\. df  display file info  
2\. lsps -a list page space  
3.     ps aux      any big processes running  
4.     netstat -p udp    (protocol will show datagram activity)  
5.     vmstat -3      (look at page-in, page-out, and cpu idle times)

You can also use ~dianem/public/findBigFiles to look at all files in a subtree and provide a list with                  the files sorted so that the  
largest are at the top.

virtual memory utilization high -- to check on virtual storage (or paging), you can issue these commands -- lsps -a  or top10vm -a.  Also you  
may want to look at the errpt (can do  
errpt -a -j  ?problemid#>.  Other options:

   get out of x windows  
   run /usr/contrib/bin/Xsize  
   bump swap space

If the following process shows up as the top10vm process and is slowing the performance, you  
can have the user log off and log back on.  This is the process started by the runx command:  
 /usr/lpp/X11/bin/X -x dps -x pcsim -D /usr/lib/X11/rgb -x pcsim -x dps -T -bs -f

If you cannot track the problem to the users workstation, they can run perfprob, program will post to priv.andrew-perform.

Network performance Dean Krueger(netperf)  Tracy Offutt(offutt)

Router information can be found in Offutt/maker

to trace network route: /usr/local/etc/traceroute helpdesk.rchland.ibm.com  
you can do a traceroute to see where the failure is occurring

/usr/local/etc/traceroute 129.35.148.210  
traceroute to 129.35.148.210 (129.35.148.210), 30 hops max, 40 byte packets  
 1  9.5.77.2 (9.5.77.2)  4 ms  4 ms  4 ms  
 2  9.254.1.1 (9.254.1.1)  43 ms \* \*  
 3  \* \* \*  
 4  \* \* \*  
 5  \* \* \*  
 6  \* \* bet2betbb.mpn.ibm.com (9.158.1.2)  49 ms !N  
 7  \* bet2betbb.mpn.ibm.com (9.158.1.2)  50 ms !N \*  
 8  \* \* \*  
 9  \* \* \*  
10  \* \* \*  
11  \* \* \*  
12  \* \* \*  
13  bet2betbb.mpn.ibm.com (9.158.1.2)  51 ms !N \* \*

\--->> In this case, the !N \* \* output from the traceroute indicates a "network unreachable" error -  that this router is not reachable.

In critical performance situation,  have the user run /usr/etc/swat on his/her workstation when you suspect the problem might be  
performance related.  But be aware that this not only captures performance data, it will also page the SWAT TEAM, who will be requested  
to look at the problem immediately.  
Following is their process --  
To make  quick diagnosis you need only look into 3 files. All these three file have the date-time ( in the form of MMDDhhmmYY) of the  
moment when the swat program  is executed as the suffix of their file names.  
     First file is gtprc.0912094594 ( the 2nd part, after the period,  of the file name will differ from the example  here). This file contains the  
top 20 processes in the workstation. These processes are sorted according to their CPU usage in percentage.  It helps you to identify any  
single process is hogging the CPUpig.  
     Second file is ping.MMDDhhmmYY. you can find out, from the first half of the data in this file, the connectivity between client and  the  
active servers and router. Normally the ping time is less than 10 ms for the workstation in Rochester.  The second half of the data are the  
AFS fileserver RPC times. It indicates some sort of  fileserver performance problem if you see the number is larger than 500(ms).  
Below is  the sample  content of  ping.MMDDhhmmYY:  
     9.5.25.25 is alive (3 msec)  
     9.5.25.14 is alive (3 msec)  
     9.5.16.251 is alive (4 msec)  
     9.5.25.21 is alive (2 msec)  
     9.5.113.2 is alive (2 msec) -- This is the router.  
     9.5.18.11 is alive (3 msec)  
     9.5.16.251 30  
     9.5.18.11 120  
     9.5.25.14 10  
     9.5.25.21 6  
     9.5.25.25 25  
     The last file of interest is rxdebug.MMDDhhmmYY. You can ignore the first half of this file. It simply  lists the active fileserver  
connections in that particular client. The second half of the file tells you whether there is any wait\_proc present in the fileserver(s)  which  
the client is actively connected to.  Normally , the calls waiting for the threads should be zero(0).   Below is a sample content of  
rxdebug.MMDDhhmmYY:  
     Connection from host 9.5.16.251, port 7000, Cuid bd92da3c/b9f52c44  
     Connection from host 9.5.25.14, port 7000, Cuid 9cec7523/b9ffe49c  
     Connection from host 9.5.25.21, port 7000, Cuid 8e4df1a5/b9f4c108  
     Connection from host 9.5.18.11, port 7000, Cuid 9f969dfe/b9ea9d40  
     Connection from host 9.5.25.25, port 7000, Cuid 9fb90665/b9d29630  
     9.5.16.251  0 calls waiting for a thread  
     9.5.18.11  0 calls waiting for a thread  
     9.5.25.14  0 calls waiting for a thread  
     9.5.25.21  0 calls waiting for a thread  
     9.5.25.25  0 calls waiting for a thread

Server problems:  
If a ka server is having problems you can check the server that the user is on by issueing the command: /bin/rxdebug (hostname) 7001  
\-onlyp 7003. If you want to move the individual to a new KA server issue: /bin/fs newcell rchland.ibm.com ks1 ks2 ks3 ks4 ks5  
 

MVS netmon  Kevin Westling

MVS, VM TCP/IP question Tracy Offutt

TOOLS

SOM:

SOM= System Object Modelling tool.  Check to see if it is being sources or referred

read advisor.som, you will need to set up some ENV variables on your system.  Not an officially supported LPP in 3.2.x

piranha: bboard = superior.piranha  
Questions/concerns on piranha should probably be handled by Darin Anderson or Kirby Bakken.

for access to superior bboards, contact member of this group:  pts mem d4a3:currentowner  
(currently ?04/96> shows asmodeus, who is Ken Allen)

Mathcad  -- Our version of Mathcad for AIX is 7 years old and has died.  It did not survive the upgrade to the AIX 4.3 on the license  
servers.  Mathcad has long since dropped support for Unix versions and has moved to Win and NT platforms.  We are working on a NT  
floating license install (Jim Dunlap 3/18/99)

Cadence support  
This is an engineering item -- can try Ronda Marshall,  Bill Oswald, or Chris Stein.   02/99 dkm

Rem  
Rem is supposed to refrain from using machines that are not xlocked and have someone logged in running an Xserver.  There are two files  
that rem looks for to determine this.

/etc/locks/xrunning  
/etc/locks/xlock

you can force REM to be kicked off by running the "reclaim" command.

If the xrunning file is there that means someone is running an Xserver on that machine.  If rem sees this file it then looks for the xlock file.  If  
it is there it assumes the machine is xlocked and thus free to use for it's purposes.  So, there are two usual ways to fix the above problem:

1.  If the user is indeed running an Xserver, make sure the xrunning file is there.  If not, touch the file and chown it to the user.

2.  If the xrunning file is there and the user is not xlocked, make sure the xlocks file is not there.  If it is, removes it (sometimes xlocks dies  
before it can clean up this file).  Altnernatively, simply have the user xlock and immediately unlock, that too should remove the file (but  
double check to make sure).

 \*\* look for loadlevler and rem processes running:  
 \*\* ps -aef |grep loadlevler  
 \*\* REM and Loadlevler will distribute processing jobs to machines that are idle.  (ie: machines that are                  xlocked or don't have  
xserver running)  Loadlevler will cause CPU % to rise.

Tools for locating free servers: REM or /usr/tools/etc/rcomp 'command'

nobutler: touch /etc/locks/nobutler and /.nobutler

LOADLEVELER --Gary Skouson

LOADL:  loadl daemon will always be running, when keyboard/mouse activity is suspended, loadl will begin running process. When activity  
resumes, the loadl process will suspend. It may take a min. for the paging space to clear out and return to user's applications.  Users may  
complain of performance problems. Can talk to Gary Skouson. Used to run processor development jobs, such as simulation, vhdl compiles  
and timing jobs.

When users send jobs to mips or beast machines, they should be able to log onto the system that has their programs running. There is a  
program called login.exit that gets run every time some is trying to get onto these machines. We put what ever algorithm we want in there  
(it's a hook provided to us by Bob Oesterlin). The program is called /etc/login.exit.

To check if a workstation is on loadleveler, use the following command:

     grep wsname  ~loadl/loadl\_admin        or       grep wsname   ~loadl2/loadl\_admin

The following command when run from a user's typescript will bring up another window that allows the user to specify not to have  
loadleveler running on your workstation for a while (up to a period of 2 hours)  by clicking on the FLUSH or SUSPEND -->  
/afs/rchland.ibm.com/rel/rs\_aix31/dev/eda/bin/llfsr

Put the following line in .xinitrc if experiencing bad perforance with loadleveler /afs/rch/rel/common/loadl/bin/kbd\_access : place in .xinitrc  
before the call to X windows.   -- Phillip Marsh 4/8/98

LICENSED PROGRAMS

WORDPERFECT -  this has been turned off by Jim Dunlap, it has reached the end of life and is not supported.

To check who has licenses:  
rsh talos sudo /usr/lpp/flexlm/lmstat -c /usr/lpp/flexlm/license.dat.talos -a

License Server:  talos.  This server has 123 license on it, along with other programs.  Jim Dunlap is owner of this machine.  May see msg:  
123: can't contact license server.  Telnet to talos and run ps -ef |grep 123.  Look for 123 daemon, flexlm.  This starts lmgrd (license mgr.  
daemon) al ninas also supports.

ROSE: Sorry about the problem with the Rose license server, it is fixed now and Rose should be accessible again. Techie  
DetailsEngineering took down the license server on Friday afternoon. Our license server runs off of the same software as their. When that  
happens our license server needs to be restarted. This did not happen because our license machine was not setup properly. (Which Todd  
Mitchell and I have now fixed.)

LOTUS123 not available on AFS clients in Rochester. APPLIX is a spreadsheet that can be used.

FRAMEMAKER:  
to invoke framemaker: maker

For FrameMaker problems contact Al Ninas  (3-2097) or have the customer contact Al.

TGIF files: Importing to Maker:  
1\. First you have to enter the following command:

tgif -print  
 -ps file

This will create a .ps file from the .obj file.  However, you still won't be able to pull it into FrameMaker.  To get it into your FrameMaker  
document, you will have to replace the fist line of the new .ps file with this line:  
2.  %!PS-Adobe-2.0 EPSF-1.2

SOFTWIN: (softwin, softwin2)

Softwindows is a PC emulator.  See help softwin.

To install softwindows run: softwin2

The installation process will create a softwindows volume and mount it under your home directory. The directory is a mount point.  To  
remove the softwindow directory and mount points run :  softwin-delete (for softwin2, there is not a script yet for deleting volumes, you must  
manually remove the mount point ~/SoftWindows2 and also remove the volume)

When a user calls because all the licenses are in use, for any limited LPP, we should check the license server to find users that have had  
the LPP up for days and send that user a hey, to free up the license for the person that is waiting.

You can telnet to the license server, currently talos, log in as root and run the command, lmstat or you can run the following from your  
command line:

rsh talos sudo /usr/lpp/flexlm/lmstat -c /usr/lpp/flexlm/license.dat -a | pipe

This will show you the active licenses for everything running on the server, but you can scroll to the beginning and make sure you see that  
Insignia is up, and scroll near the bottom and check the number of users against the total number of licenses, listed in parenthesis.  Then,  
check the users and if there are any that have been up for days, contact them via hey or phone or whatever and tell them to get off.  (If  
they are a really bad offender and you cannot reach them, I believe we have Jim's permission to actually kill the process on that user's  
machine, but this situation is rare).  Usually people are surprised when contacted that they even still have a license checked out.

FILE TRANSFERS

FTP rchvmp2  or ftp rchland   (subcommands entered @ prompt:  binary,ascii->default)

ftp \[  -d \] \[  -g \] \[  -i \] \[  -n \] \[  -v \] \[  HostName \]

ftp> put, get ex: get profile.exec

If the ftp appears to go okay, but the file comes in the directory as "0" (empty) -- the user  
may need to increase their quota (do an "fs lq")

Check the user private directory for a .netrc file is ftp seems to fail.  If the ftp command finds a $HOME/.netrc automatic login entry for the  
specified host, the ftp command attempts to use the information in that entry to log in to the remote host.  The information may be wrong in  
this file.

Process for using ftp  
ftp -i rchvmp2  
Connected to rchvmp2.rchland.ibm.com.  
220-FTPSERVE at RCHVMP2.rchland.ibm.com, 12:07:41 CDT WEDNESDAY 04/06/94  
220 Connection will close if idle for more than 5 minutes.  
Name (rchvmp2:costello):  
331 Send password please.  
Password:

230-COSTELLO logged in; working directory = COSTELLO 191 (ReadOnly)  
230 write access currently unavailable due to other links  
ftp> mget d\*.exec

~{';'}~

AFS PUT/AFS GET

on VM:  afs log  
issue following commands on VM  
afs get afs\_filename fn ft fm (options  
ex: afs get preferences pref afs a (char

NOTE:  For help on afs put and afs get type help afs from VM

OTHER TOOLS/APPLICATIONS  
 

LOTUS NOTES:

NOTES.45.LOCAL -- this came from Dave Nordgren for the purpose of reducing the occurrences of notes crashing when xlocked.   It is to  
be used instead of notes45 from their typescript, but the recommendation is that they always use it from the same workstation since a local  
copy of desktop.dsk is used/maintained.  09/98 dkm

"Incorrect list entry count text\_list is invalid" error message when trying to run Notes on AIX.  
Do the following:  
1) try the kill\_ln command; if that does not fix it ... go to step 2  
2) try restarting xwindows manager; if that does not fix it... go to step 3  
3) try a reboot; if that does not fix it.... go to step 4  
4) rename names.nsf to names1.nsf, reset the notes.ini, and restart notes.  THIS SHOULD WORK.  
If not, get in touch with the LotusNotes Help Desk, 4-0297.   09/98 dkm

AIX LotusNotes -- Error loading USE LSX module when trying to access mail.  User was a notes 4.1.  The mail template needs notes45.  
10/98 dkm

AIX LotusNotes -- is user gets error message "unknown os error"  and then gets big red flag --> sorry an uncorrectable error has occurred.  
Null object handle.  Press Enter to abort the application, but the solid hourglass is on.   The solution is to reboot.     10/98 dkm

/usr/contrib/bin/kill\_ln is designed to kill notes and clean up the shared memory and semaphores. It tries to guess at which key belongs to  
Notes in the semaphore and shared memory lists, but could miss some if they change from what the developer has hard coded in the script  
.

An environment variable can be set to limit the colors that are used by the Notes/AIX client.  
       export MAX\_NOTES\_COLORS=22 (minimum of 22)

To install NOTES ptfs:

first check to see ixit  
f the pts were installed:  
/usr/sbin/instfix -ik IX55587

If the fixes are not installed, the user will need to execute this command from the green console screen (and the system will be rebooted  
automatically when it completes):  
rroot inst.fix.lotus install

If the system doesn't have adequate free space, a message will be displayed.  The best bet then is to reinstall the system with smaller  
paging or cache, in order to free up 12MB or to install with the new 4.1.4.1 image which has the fixes.

OR, this command will install the ptfs:

installp -acgX -d /afs/rchland.ibm.com/rs\_aix41/fix/lotus.fix all

reboot and than try the /usr/local/bin/notes4 command

To kill notes and clean up notes files:

/usr/contrib/bin/kill\_ln

you will be prompted for user id running notes.

Other applications on Lotus (like, Word Pro, Freelance, etc) -- the only help available  
is through the Lotus Support 800 numbers:  1-800-343-5414 or 1-800-346-2219.  
For VERY technical issues, have them dial  1-978-988-2500.   If the user does not  
get any help from these numbers, they need to contact Sara Grossen.    04/98 dkm

     another option would be to have Ken or Don give them a new profile if they are getting  
     a "splash" screen immediately.  This has sometimes worked in the past, especially for  
    Lotus 1-2-3.    11/98 dkm

Xlock --  (03/98 dkm)

The unlog option causes xlock to destroy your authentication tokens (-unlog is the default). Use +unlog to prevent the destruction of your  
tokens.

    xlock -mode blank +unlog    (will xlock your ws without destroying tokens)

The default for Xlock is to destroy tokens.  If you don't specify +unlog and you are trying to run workbench, dev2000 you will get error msg.  
saying that you need to klog.  However, you don't need to klog because by signing back on, you reauthenticate yourself.  The processes  
(compiles) that were trying to run when you were xlocked however will fail.

problem relogging on xlocked rs/6k  
        1) Unlock user  
        2) Check to make sure that the user has a typescript  
        3) Have user relock/unlock  
        4) Ask user if he is using an alias for xlock  
        5) Ask user how he is issuing the xlock ie typescript etc  
        6) find out what mode the user is running the xlock in.  
        7) Name of rs/6K login host if workstation is xstation.

if rem jobs come into machine that isn't xlocked--try locking/unlocking.  
Also check /etc/locks and look for a xlock file. If it exists rm it.

trouble xlocking: sometiems see this msg:  
 open system call to "/dev/hft/0" failed ioctl call to get hft ring failed with 9

someone else possibly logged onto your "green screen" (and perhaps logged out).  
You need to be logged onto the 'green screen' for xlock to work.  
The login/logout processes assign ownership of the hft device to root.  
If you log off of the green screen, root has the device.  Login briefly gives root ownership and then assigns it to user.  This device is  
opened and written to when xlock is invoked.  This is to lock out the hft ring to prevent toggling to greenscreens when the system is  
xlocked.  You can lock the display only by using xlock +hft.  This turns off aixhft hiding.

The hft device needs to be owned by the user who is xlocking.

ls -l /dev/hft/0  
crw------t  1 spillman              18,   0 Mar  9 11:56 /dev/hft/0

The simplest "fix" is to logout and login again.  Another workaround is to run this command: (as root)  
chown userid /dev/hft/0  
chmod +w /dev/hft/0

x3270 valid screen sizes for x3270 are 24x80, 32x80, 43x80, 62x80, 27x132, (27x133 needed in some cases)

ENV VAR for x3270, x5250 : XFILESEARCHPATH  
Most Motif apps look for files in $XFILESEARCHPATH, where %T expands to "app-defaults", %N expands to the name of the app  
(uppercased first letter), and %S expands to nothing.

Help xant, help x3270 -- for standard 3270 keyboard functions (such as  PA1 might be  
ctrl-F1 or ctrl-Z)

To set cursor color colors for x3270: x3270 -sk -cr white -ms white rchvmp2  
(This can be done normally in the user's .dt/sessions/sessionetc file)

To change cursor speed:  
      From the green screen, before you bring up a window manager, run  smit  
      and follow this path:  
 devices.GraphicInputDevices.Keyboard.Change/ShowCharacteristics of the Keyboard.  
     Use tab key to change values.  
   
   
 

How to find where a program is located:  
/usr/local/bin> cat rroot.cmds |grep softpc This is the file that contains all of the rroot aliases.

Issues DataBase -- if you discover an issue locked  and want it unlocked, do a cd ~csc/issues/AIX\_AFS.  Find the locked issues and then  
do a RM on it.

LotusNotes

LN PROBLEM DETERMINATOIN:

1)   incorrect list entry count text\_list is invalid :  
when an AIX user gets this error message it means his names.nsf file is corrupt.  In order to fix the problem you need to have the user make  
sure notes is shut down (kill\_ln command is good for this) then go into his notesr4 directory and find his names.nsf file.  Rename the nsf file  
to names1.nsf than type in e notes.ini to edit the ini file.  Delete everything except for these lines in the ini file (they may not be in this order,  
the items in  
blue  will be different for all users)  
\[Notes\]  
KitType=1  
Directory=/afs/rchland.ibm.com/usr3/v2cib227/notesr4  
IconPath=/afs/rchland.ibm.com/usr3/v2cib227/notesr4/unix  
SPELL\_LANG=2  
Preferences=2147500576

Save this file then start up notes.

Notes will come to the setup screen (like you have never run notes before)  Just fill in the info to set notes up.

When Notes is set up, you can do a file-database-open, and you will see two address books listed, one has a filename of names.nsf and  
one has a file name of names1.nsf.    Keep the names1.nsf file highlighted and choose Add Icon.

You will now see two address books on your workspace.  Go into the old address book.  Go to the people view.   Put checkmarks next to  
all the names and do a  edit-copy.  Close this address book.  Open the other address book.  Go to the people view and do an edit-paste.  
Do this for groups view also.

When done, remove the icon for the old address book from the workspace; then delete the names1.nsf file from your notesr4 dir.

The problem is fixed.    10/98 dkm

2)  If users on AIX LN get messages "freezing all server threads", they should do the /usr/contrib/bin/kill\_ln.    They may also wants to  
delete from their notesr4 directory, files like helplt4.nsf and cache.dsk.  10/98 dkm

3) When you cannot delete a document from your mail, your mailbox indexing may be corrupt.  
doing SHIFT +  F9 will clear it up.   07/99 dkm

LotusNotes DataBase -- If you have a user that wants to open up a new database (like to store  
meeting minutes).  follow the path FILE--DATABASE--NEW.  Keep "server" as Local; fill in "title";  
then at "template server", click and find d27db001/27/A/IBM.  Use the Documents(R4) template.  
If the user wants it to go from LOCAL so everyone can access it, call the LotusNotes Help Desk, and  
ask them for assistance.

\------------------------------------  
If the PC DESK needs an issue unlocked,  do:  
cd ~pchelp/issues/pchelp  find the locked issues and do a RM on it (as admin)  
   
 

XWD -- SnapShot:  dumps the image of an Xwindow window.  
refer to help XWD.  Commands for window Snapshots:  
       xwd | xpr -ps -device ps -portrait -top .2 | lpr -T native ?  
       /usr/contrib/bin/xsnap -xwd -noshow | xwd2atkimage | /usr/local/bin/xcut?

ECFORMS: Leung, G.S. (Gabriel)         1-507-253-3042 553-3042  GLEUNG   RCHVMP2

Bookmanager: (Vicky Gifford 253-5387)  bookmgr:  If user gets note saying that the license server is not available, the license server may  
have been down.  The note is from the license server saying a license is not available. However, a license will still be granted.  : If the  
licensec daemon is down or disconnnetced, users will be granted licenses upon request and a msg. will be sent to system owner. To  
restart the bookmgr process:

1.  telnet talos

2.   cat /etc/rc.custom  
#!/bin/csh -f  
uname -S talos.rchland.ibm.com  
/usr/lpp/flexlm/rc.start\_flexLM  
/usr/lpp/flexlm/rc.mathcad  
/usr/lpp/flexlm/rc.math  
/usr/lpp/flexlm/rc.frame  
/usr/lpp/flexlm/rc.bookmgr  
/usr/lpp/flexlm/rc.centerline  
/usr/lpp/flexlm/start\_fm4  
/afs/rch/usr2/hamel/public/tooluse 1>/dev/null 2>/dev/null ?

3.  Copy and restart the bookmgr process in the BACKGROUND  
 

Charting tools: autop2, xsched(gantt chart, proj. planning)

INFOEXPLORER: The user must have system:anyuser l access rights in their home directory to be able to run info.  Otherwise, you will get  
an ERROR 13.  To bring up infoexplorer without any windows, type info -q

C Debuggers -- xcdb, dbx

coreldraw /usr/dev/local/bin/coreldraw or corel. Jim Dunlap ? Gary Skouson

/usr/contrib/bin/niftyclean - used to clean up junk

to display colors and color names use: xco or excolors  
other options:  
showrgb  
xcoloredit  
xcolorpick  
xcolors

Colormap is a ATK command that can be used to display the number of colors allocated. Usage:  
  1) From the typescript enter colormap  
  2) You should then get another motif window, press the s key, the number of color allocated will be displayed in the upper right corner.

Messed up colors: 'Colormap' from typescript.  Place pointer in window and press 's' to see how many colors are being used.  Max is 256

crosspw -used to set passwords across all systems you are on.

show the weather forecast add the following to your preferences:  
messages.SurrogateHelpFile: /usr/common/contrib/lib/weather/data/motd

help on a tool: reuse tools  
the Reuse Browser will be started and all (or most) of the available aix/afs tools will be displayed.

To view hidden characters in a filename: ls > tmp, then mrhex the redirection file.  
or try ls |od -c

wordperfect: xwp  
 

To browse bitmaps:  xv /usr/local/bitmaps

help -s forces the help program to follow given path.  EG: help -s /afs/rchland.ibm.com/usr2/csc/helpstat rs6000.guide

Compare two files:  To display each pair of bytes that differ, enter:  
cmp -l prog.o.bak prog.o

Core file evaluation: cfa core  
after looking at core file, you can use DBX to evaluate further:  
dbx xxxxx core. where xxxx=the command line path from the core file. Type t (trace) at the dbx prompt. THis will show (reading bottom up)  
the trace of the dump.

Core file on home directory can be looked at by running a command called "strings core."  
The core file on home directories is created by AIX and will regenerate if removed.

To create a file if not previously existing, use the TOUCH command  
eg:  
touch /afs/rchland.ibm.com/usr2/shuyuan/dev2000/dev2000/v10r2m0/usr/cmvc/base.pgm/lande/remake/Main/ps/Containe.prv

scout:  monitor servers

spot:    monitors runaway processes

Support for xxxxx tool? If it is in /contrib we do not support. use WHICH ?name> or whereis ?name>

RQMS - on vm show QCB

System diagnostics: Run ~hien/public/afsnet

Fonts

Large Fonts -- If you reboot with the monitor power off and the fonts come up large, it is because the RS/6000 chose a poor default setting  
for the monitor that you have attached.  This can be remedied by either turning your monitor on and reboot your workstation, or it can be  
done without rebooting your system.  From the green screen where you log in use "smit", and find the "graphic displays" entry from the  
devices menu.  You should be able to select the display type and resolution without too much poking around.  (Setting the display type  
correctly first gives you more options for screen resolution and refresh rates.)  
 05/98 dkm

How to set MONITOR type -- correctly:  
Go into smit, then into Devices, Graphic Displays, and Select the Display Type.  
This is where some confusion may arise.  If you want to set the monitor type  
to P200, for example, when you get to this step it doesn't give monitor options.  
The only choices are for graphics adapters. Hit enter; that will bring you  
to a screen where you can then choose "Select the Display Type".

At this point, there is another element of confusion.  There is no list of  
options to select nor are there any clear instructions explaining what  
to do. Here you must press ?F4> and you will get a list of monitor types.  
Then select the monitor, (in this case "P200"), and press enter.  
01/01 elh

to list font path execute xset -q

to add to font path execute xset fp+ 'fontpath'

To find where a particular font is located  xlsfonts | grep helv18

To see what a font looks like, use xfbrows

to locate the font type in /usr/contrib/bin/whichfont fontname  
xfd  -fn "-ibm--medium-r-medium--20-14-\*-\*-c-90-ibm-850"

TODO list - todo.motif

AFS Client Code Setup (for OS/2) --look at /afs/rch/os2/afs/README.Install You can get 'afs for os/2' from the netdoor catalog

 tex files:  
/usr/contrib/bin/latex  ?=== run twice  
/usr/contrib/bin/tex    ?=== run twice  
/usr/contrib/bin/dvips

WEB BROWSERS

mosaic, netscape --Vicky Gifford

For users that need to get a newer version of netscape loaded (specifically, users from Ireland with 4.04),  
have them go to the web page -->  [http://w3.ibm.com/netscape](http://w3.ibm.com/netscape) and download a newer version.  
 07/99 dkm

cache -- if someone cannot bring up netscape, it may be that their cache directory has filled up.  
              Follow these steps when that happens:          02/99 dkm  
       1) shutdown netscape  
       2) cd .netscape  
              3) rm -rf cache  
              4) mkdir cache  
              5) start netscape

netscape -- if java or javascript needs to be enabled, on the new release of netscape, select  EDIT >  
                   PREFERENCES > ADVANCED.   03/98 -- dkm

WWW project page info located at: /usr/dev/common/www/w3root/projects

To make changes to the HelpDesk.html main page, you need to grab a copy of it  to your own  
directory, make changes, and then ask Vicky Gifford to reload it.   10/98 dkm  
    ~> cd ~dianem/public  
    .../dianem/public>  cp /usr/common/www/w3root/HelpDesk.html  work.HelpDesk.html

"[http://w3.rchland.ibm.com/](http://w3.rchland.ibm.com/)" - mapped to /usr/common/www/w3root

If someone calls and says that the WEB server in Rochester is down, check the system called w3.rchland.ibm.com located in the 020-2  
machine room. It may have to be rebooted.

WORK AROUND WHEN YOU CAN NOT GET OUTSIDE THE LOCAL URL'S  
The following is a work around when we have server problems locally and can not resolve then in a timely manner. If the customer has a  
business case they can:  
1.  In the netscape window find the option button.  
2.  Select Network Pref  
3.  Select Proxies tab  
4.  Select the Manual option, then click on view  
5.  Blank out all information in the following  
     a.  FTP Proxy:  
     b.  Gopher Proxy:  
     c.  HTTP Proxy:  
6.  Next where it says SOCKS Host:  type in   socks1.server.ibm.com   or  socks2.server.ibm.com  
7.  Leave 1080 in the port box next to the SOCKS Host:  
8.  Now select ok twice.  
This should now allow the customer to get to other web sites.

NETSCAPE128 WORK AROUND WHEN YOU CAN NOT GET OUTSIDE THE LOCAL URL'S

select   edit  
select   preferences  
select   advanced  
select   proxies  
click on ?> in front of automatic proxy configuration  
enter [http://w3.rchland.ibm.com/rch.proxy](http://w3.rchland.ibm.com/rch.proxy)  
in the Configuration locatition URL  
 

for home page, system:anyuser needs l access to dirs above WWW.  
WWW dir  needs system:anyuser rl access.  
 

PMX

\[PMX SetUp\]RUN:ez ~csc/pmx.d  
User can be directed to the Rochester Home Page on the web for instructions on using PMX --  
They need to click on  1) Help Desk  
                                 2) AIX/AFS Services  
                                 3) PC Support  
                                 4) IBM OS/2  
                                 5) Applications (under SOFTWARE)  
                                  6) PMX

Problem: ATK applications have font problems. Be sure that the font path is set to include the Rochester fonts......eg:  
E:\\TCPIP\\X11\\MISC,E:\\TCPIP\\X11\\75DPI,tcp/justv:7500 ----> The customer needs to change the TCPIP configuration file to read:  
tcp/hostname:7500, where hostname is the name of the primary rs6000 that the customer uses. ex:  
tcp/helpdesk1:7500.

TO avoid having to set the DISPLAY var. each time, add this to .login:

\# The following statements set the DISPLAY and HTP environment  
\# variable automagically when telnetting!  
if !($?DISPLAY) then  
        set disp=(\`who | awk 'BEGIN {"tty ? /dev/tty" | getline tty; sub("/dev/", "", tty)}; $2 == tty {print substr($6, 2, index($6, ".")-2)}'\`)  
        if ($#disp > 0) then  
                setenv DISPLAY "$disp\[1\]":0  
                setenv HTP 1  
        endif  
endif

To start telnet session to rs6k:  from OS/2 window:  
 xhost +  
 telnet to host  
 ON HOST: setenv DISPLAY name\_of\_pc:0  
 

TCPIPCFG from OS/2 window prompt will bring up the TCP config. menus.  Services will let you look at the host name and names server  
address.

PMX will require the following:  
    o   PS/2, 80386 processor, 25 mHz  
    o   160 MB hard file (with 35 MB free when all software is installed  
        including OS/2)  
    o   10 MB memory  
    o   OS/2 2.1  
 

Each aix RS6000 should have a fontserver process running. If the customer is getting a font server error, log onto the host machine they  
are using and check to make sure the process is running (ps -ef|grep fontserver). If the process is running kill the process and restart it  
with : nohup /usr/bin/X11/fs -config /usr/local/etc/fontserver.cfg -port 7500 > /tmp/fs.out ? . Make sure the customer has the proper  
hostname identified in the tcpip configuration table. Make sure the fontserver changes are updated in Start.cmd or  xinit.cmd if needed.

FOR 4.1 systems, the FONTSERVER process is:  nohup /usr/bin/X11/fs -config /usr/local/etc/fontserver.cfg -port 7500 > /tmp/fs.out ?

xfs server will not start if .noxdm file exists.  Check for existance of /etc/wsupdate.local file

EXCEED   2/9/98 rdl  
This URL has all the installation instructions.

[http://w3.rchland.ibm.com/rch.proxy](http://w3.rchland.ibm.com/rch.proxy)

If someone is going from their PC, using EXCEED, to a RS6K and something is amiss, have them check their configuration by going to  
START--> PROGRAMS --> EXCEED --> XCONFIG.

Lab LAN support : 930 campus: (93x rings:)  
  Landgrebe, Gary J      3-8258  
  Klein, Kent A              3-5999  
  020-1                        3-7717  
  003-1                        3-7272  
  003-1                        3-7612  
  New patch panel         3-9488  
  020-2 (afs server/network)       use pager, if no response call 3-3072

Access to 020-1 Room -- contact Jerry Knowlton and asked him to give you access to  
080100 CAT2037.   04/99 dkm  
 

\----------

\----------  
 

INTERNET

bulletin board for internet help:  
ext.ibmvm.ftpgate-forum  
ext.ibmvm.inetgate-forum

Web help for internet registration: [http://w3.nas.ibm.com/getconn/index.html](http://w3.nas.ibm.com/getconn/index.html)  
Internet rules: [http://w3.austin.ibm.com/internet/rules](http://w3.austin.ibm.com/internet/rules)

Contacts for Advantis:  
A new option to the CAC (3-5544), Option #7, for Network calls has been added.  The calls will route to a     TP Helpdesk in  
Poughkeepsie.  Marty Cormack said that people wanting to talk with Advantis should be           routed to Option #7.  These people are the  
most familiar with Advantis services.

Contacts for tollbooth:  
tollbooth.cwp.ibm.com is a supported Advantis service.  As such, you can call in problems to the Advantis help desk: Tie-Line: 566-HELP  
(566-4357) External: +1-914-684-HELP (1.914.684.4357)

When calling in a problem be prepared to supply the ip-address you are starting from and any results from any traceroutes or other  
diagnostic procedures you have attempted.

To run IREG EXEC, from VM, must be linked to utool2 disk on VM. (vmlink utool2)

reset password on tollbooth - vmtell emas@rhqvm14 resetpw afsuid rchland tollboothpassword (internet

To change registered VM internet node to registerd RCHLAND node:  Go into IREG, take PF7 from the main screen, fill in "2" and "i" in the  
top, put in your current node/user, and then put in your same userid and RCHLAND in the new user/node fields.

Support person for IREG is RoAnn MacKenzie, tl 631-9634.   06/98 dkm

Problems with RCHGATE ,  Mail errors contact Joan Demeter at JOAND@ENDVM5  
 

To change alias from AFS:  
vmtell emas@rhqvm14 alias name1 name2 name3 name4  \\( internet

To find AFS dir path for project pages (URL's starting with" //w3.rchland.ibm.com/projects") cd to  
/usr/common/www/w3root/projects in  that dir are the symbolic links to the appropriate AFS dirs.  
 

MOVING SYSTEMS  (RS6000,  RT, and XSTATION MOVES)

SELFHELP:  Support:  front end/user interface: Mike Pascoe backend: Dave Kooistra

Moving RS6000:  \[RS6000 MOVES\]RUN:ez ~csc/support/rs6000.move.d

Moving Xstation: Model 120, model 130, : CTRL/BREAK after memory check

NOTE:  The network defined on host must have the gateway address of the xstation's new location and you must have the workstation  
defined to the host if a new host is required for the move.  If you get a new host make sure the x station manager is running on the host.

ps -ef | grep x\_st\_mgr    Use this command on the host system.

Update selfhelp before the move date.  Print out the message you ge/t back from network.  You will need the information when you change  
the setup menu on the xstation.

XSTATIONS

xfindwshost  - locates host machines for xstations

xstation model 120, 130, 150:  
    If the xstations still are having problems functioning on AIX 3.2.5.4 machines perform the---- on 'rs/6k name' ls  -l /etc/x\_st\_mgr  
\---command and make sure the symbolic link is there for the xstation configuration file.

Start xdm and x\_st\_mgr

To start xdm:

/usr/local/lib/xdm/xdm.r5 -nodaemon -config /usr/local/lib/xdm/xdm-config ?

To start x\_st\_mgr:

/usr/lpp/x\_st\_mgr/bin/x\_st\_mgrd -b /usr/lpp/x\_st\_mgr/bin/x\_st\_mgrd.cf -s x\_st\_mgrd

Connecting Model 160 machines to a host:  \[160 Xstation Doc\]RUN:ez ~csc/support/160\_xstation\_screens\_for\_setup.d

for non-CDE logins, the X station font path is set in /usr/local/lib/xdm/Xsession  
   
   
 

DESKTOPS - USER ENVIRONMENTS

MWM

to get full pathname in iconbox in .Xdefaults add MWM\*icon Decoration label activelabel to have it take effect

To set up path to contrib in .login add "setenv CONTRIB yes"

xrdb -load .Xdefaults  then restart MWM

To include a telnet in .mwmrc "aixterm -e /usr/ucb/telnet rchrs448 ?"

To check bell settings  
xbell  will sound the beep  
xset -q will among other things show the environment settings for the bell(beep)  
xset b 100 400 100 set bell percent, pitch and duration respectively

If you can't hear anything when you run xbell, try a volume louder than 2% (e.g. 100%).  
If that doesn't help, extend the duration to 500ms or so.

When you find something that works, change the line in your ~/.xinitrc  
so it'll stay that way next time you runx.  
 

FVWM -- Bill Oswald

CDE- Comman Desktop Environment

With AIX 4.1.4 CDE, your ~/.Xdefaults are used (again).  When you login (or runx -cde), CDE reads your ~/.Xdefaults and merges it extras  
it thinks you need which are mostly settings from the style manager.  Apps from then on use those loaded resources.  If you edit  
~/.Xdefaults, you need to dtaction ReloadResources which will re-read your ~/.Xdefaults and re-merge the style manager settings.

start cde -- runx -cde

to enable cde -- cde enable  --must reboot  
to disable cde, -- cde disable -- must reboot

If users are on AIX 4.1.4, they have CDE ENABLED, and need to get to a green screen, you must telet to their work station and delete  
.cose.  Then reboot them.

On 4.1 systems, a log is put in ~/.dt/startlog which will give you info about desktop start up

In CDE, the Screen Lock function on the Screen icon should NOT be set to ON.  The screen lock code  
is not designed to handle AFS authentication.    This will only work on a standalone machine.

DFS/DCE

DFS/DCE equivalent commands:  
    'fs checks'            cm stat  
    'fs mkm'               fts crm  
    'fs whereis'           cm whereis  
    'fs examine'          fts lsq  
    'fs flush'               cm flush  
    'fs flushvol'           cm flushfileset  
    'fs setacl'               --> not an easy answer; need to use acl\_edit  
    'fs listacl'              acl\_edit ?dir\_name> -l  
    'vos examine'       fts lsft -file user.xxxxxxx  
    'vos listvol'           fts lsh  
    'vos listvldb'         fts lsfldb  
    'kas examine'       dcecp -c account show  
    finding path         to find the usrx or ux for dfs, do the following         01/99 dkm  
                                  1)   cd   /:  
                                  2)   ls   -d   u\*/userid    (example,  ls -d u\*/dianem )

    You need to use 'dcecp' to create/modify/delete groups.  There is a whole set of group commands.  
     In general, users cannot create groups in DFS without a special to-level group setup.  See Bob  
    Oesterlin if this needs to be done.

    More information on DFS/DCE can be found under [http://w3.rchland.ibm.com/projects/dce](http://w3.rchland.ibm.com/projects/dce).

Longer Tokens for DCE:    08/98  oester

1) Bring up an aixterm window (does not work in typescript)  
2) enter "dcecp" and hit enter  
3) at the "dcecp>" propmt enter this command:

    account modify ?userid> -maxtktlife +D-HH:MM:SS

  where: ?userid> is the ID you want to change  
         D - number of days for ticket lifetime  
         HH - number of hours for ticket lifetime  
         MM - number of minutes for ticket lifetime  
         SS - number of seconds for ticket lifetime

 So, if you wanted to make "tfrana" have a 300 hour lifetime (which is 12 days and 12 hours), you would use this command:

     account modify ?userid> -maxtktlife +12-12:00:00

4) After you enter that command, type "quit" to exit.

To check tokens to see if worked, account show ?userid> -all

Installing DCE:

1) Telnet to machine  
2) login as root  
3) mount -o soft -n camaro /aix /mnt  
4) smit  
5) take all defaults from software install

   a) Soft Install ? Main  
 b) Install ? main  
 c) Install/update soft  
 d) Install/update select soft  
 e) Install Soft Product

6) Input /mnt/325/lpp/dce13  
7) F4 - will list

Error:  If a user is getting input/output error when he tries to log on, he may need to have dfs restarted.  
          Switch to root, and then issue the following command:  /etc/dce\_health  
 (this is the old command to restart dfs: /etc/rc.dce all)

If you see that dced is being piggish, you can stop and restart dce/dfs yourself without rebooting.  
Here are a sequence of commands:

 1.  lsps -s   (look for a very high percentage)  
 2.  top10vm -a   (see if dced is the "top dog")  
 3.  rroot restart-dfs  (this will recycle the daemons)

If you cannot execute any commands, try shutting down applications such as messages,  
netscape, ez, etc.  This may free up some pages so you can run commands again.

If the  DCE/DFS problem occurs on AIX 4.1.4.0 small client and doing the /etc/dce\_health fails to start,  
check the link as follows.  It should look like this:

\# ls -ld /usr/lpp/dce  
lrwxrwxrwx   1 root     audit         43 May 19 02:13 /usr/lpp/dce -> /afs/rchland.ibm.com/rs\_aix41/dce.ptf.set10  
#

If not, do this to fix it:

1.  rm /usr/lpp/dce  
2.  ln -s  /afs/rchland.ibm.com/rs\_aix41/dce.ptf.set10 /usr/lpp/dce  
3.  Then reboot and DCE should come up OK. If this link is NOT incorrect, then contact Bob Oesterlin.

More DFS problem-solving tips ==>

1.  telnet to the workstation  
2.  use "ls /:" to get a quick status of DFS.  
3.  A good listing from ls /: should look something like:  
      cds.dfs.proxy      eng          ix86\_os2       rs\_aix41      u1  
      common            export       projects        rs\_aix42      winnt  
      dv2k                  home        rel                u0              wsadmin

     If output comes back with only /:, then something is broke.

     a.  ping the workstation to make sure the workstation is attached to the network.  
          If you cannot ping, then they cannot reach the network and that is causing the  
          problem.  (Follow procedures for checking out the network.)

     b.  If you have not done so already, telnet to the client as root.

     c.  Run ps -ef | grep startdfs.   If startdfs is running, then DFS has not finished  
          initializing.  Repeat the ps -ef | grep startdfs command until startdfs has  
          finished running.  If startdfs does not go away within 10 minutes, it is hung;  
          Call either Rich Wales or Bob Oesterlin at this point.

     d.  After startdfs has finished, run df.

          If output from df shows a line for DFS, then DFS has started okay on the ws,  
          and there is some other problem.  Do ls /: to see if you can contact anything in  
          DFS.  If you get good info from ls -l check to see if DFS file servers are up using  
          cm checks (checkservers).  If servers are down, let customer know it and make  
          sure Bob, Rich, or someone from the AFS team is aware and working on the  
          problem.  If all servers are up, then contact Bob or Rich.

          If there is NO DFS line from df, then DFS did not start.  Follow the rest of these  
          procedures.

     e.  run /etc/dce\_health

      f.  Repeat step c.  But this time, if it is still not working, try rebooting the machine and  
          go back to step b when the machines comes back up.  If you have already rebooted  
          once, and it is still not working, call Bob or Rich.

TRACE METHOD  
Use this method if you are  errors such as "Lost connection to server" or if it seems that you are having any sort of DFS server problems or  
errors.

1\. Put the syslog into a file by doing:  dfstrace dump > /tmp/d  
2.  Look into the file that you just created (/tmp/d).  
3.  Look for any entries that involve the string "Current Time".  
4\. On those entries, you will either find error codes or return codes.  Use the dce\_err command on those codes to help you  
determine            the problem. (Do this by typing dce\_err  ?error/return code>)  
5.  If there isn't anything in the syslog file, or nothing helpful, try cd /var/dce/svc.  
6.  Look for any files of type .log.  If they are not recent or they are empty, there is nothing useful in them.  
7\. If there is nothing in /var/dce/svc that is helpful, try /var/dce/dced/dced.log or /var/dce/adm/directory/cds/cdsclerk  
or                                      /var/dce/adm/directory/cds/cdsclerk and follow the same procedure in #6.  
8.  If you do find something helpful in one of these four directories, simply follow steps #3 and #4.

chgaddr, Verifying I/P address, change address when telnetting to the new hostname the old hostname shows up in the login prompt.  DCE  
or DFS  
This particular problem is a dce configuration problem after an address change.  In order to fix this problem in the future you can preform  
these steps:  
1.  Log on as root and cd to /etc/dce.  
2.  Edit the dce\_cf.db file and change the host principal name.  ie remove the last "m" from the hostname.rchland.ibm.com entry.  Save the  
file.  
3.  run /etc/chkdcecfg  
This will reconfigure dce on the host system and in almost all cases fix this particular problem.  
 

WINCENTER:

View and Increasing Wincenter Quota  
Use this link to lcheck a wincenter user's quota and/or increase it (admins only):

https://rchn2www/sec-bin/bumpquota.pl   (elh, 06/15/01)  
   
 

DEV/2000

DEV/2000 Information    (Mgr: Bill Doucette)

BBS - dev2000.user.lande, dev2000.user.wsidss, dv2help

To post problems about rcomp dev2000.special.rcomp

To set Mouse Double Click speed

MWM  ?  FVWM (this might need more testing - one user called back to say it didn't work)  
in .Xdefaults file, set the resource, Put the following line in the .Xdefaults.  
\*multiClickTime: 250  
The time is in milliseconds (250 is the default).   The new speed will take effect the next time the window manager is started.  
Mouse speed to move across the the screen is in the .xinitrc file.

CDE  
Click the style manager icon on the front panel  
Click the mouse icon in the style manager  
Set the double-click speed with the slider bar and test on the test icon.  
Changes will take effect the next time the window manager is started.  
 

To make mouse left-handed

Put this in the  .xinitrc file (takes effect when "runx" is issued):  
xmodmap -e "pointer = 3 2 1"

CD Player

To start the CD player run - run\_ums cd\_player

WinCenter -- force start-up:  
   (example below is for trying to get connected to wincenter 3)  
    1)   xhost wctr03.rchland.ibm.com  
    2)   rsh wctr03.rchland.ibm.com wincenter -display kingsland:0 -depth 4

Samba   ([http://w3/projects/samba/](http://w3/projects/samba/))

    Samba is useful for:  
    1) casual access to AFS/DFS for W95, NT and OS/2  
    2) PC users who edit Web Pages on AFS/DFS (w3.rchland.ibm.com)  
        this will eliminate most (all?) use of FTP  
    3) It allows PCs direct access to AFS/DFS files  
    4) if most of a department is on NT, using DFS, W95 users can access DFS through Samba  
    5) WinCenter users who wish to access AFS/DFS        11/98 dkm

   To find out if both samba processes are running, enter this command:  
     -> ps auxw | grep mbd  
    root   29780  0.0  0.0  472  840  - A    15:14:43  0:00 /usr/contrib/bin/nmbd -D  
    root   30288  0.0  0.0  664 1044  - A   15:14:42  0:00 /usr/contrib/bin/smbd -D

    If these processes are running and problems still persist, you may want to look  
    at the /usr/lib/samba/smb.conf file to ensure that the correct IP address exists  
    for your system.    09/98 dkm  
   
 

Mechanical Engineering Software Support -  
Search words: MDA, Catia, Cadam, Ideas, I-DEAS, password, Fluent, Icepak, Flotherm, Sysnoise  
This section maintained by Eric Hepp :  3-2728,  erhepp@ibmusm07,  ezpage erhepp  
(Note: you must have the environment variable RUNBUTTONPATH set as "setenv RUNBUTTONPATH  
/usr/local/lib/runbutton:/afs/rch/usr2/csc/bin:/usr/tools/bin:/afs/rch/rel/rs\_aix32/prod/mda/ubin" for the buttons in this document to work.)

\[Second-Level Support Personnel\]?URL:[http://w3.rchland.ibm.com/~uidadm/SupportFrames.html](http://w3.rchland.ibm.com/~uidadm/SupportFrames.html)\>  01/98--dkm  
Locate the support personnel for MDA applications such as Catia, Cadam, Fluent, Icepak, Flotherm, Sysnoise, Ansys, Icepak, I-Deas

\[MDA user password reset\]?URL:[http://w3.rchland.ibm.com/~erhepp/help/passwd.html](http://w3.rchland.ibm.com/~erhepp/help/passwd.html)\> 01/98 -- erh  
In addition to changing these passwords, users may have .netrc and RMTACC.dcls files that contain their passwords. These files must be  
updated whenever the passwords are changed. Catia users may use the "USERENV Setup" option on the \[Catia Utilities  
Menu\]RUN:ezcatusr (/afs/rch/rel/rs\_aix32/prod/mda/ubin/ezcatusr)  to do this.

\[Catia problem reporting\]?URL:[http://w3.rchland.ibm.com/projects/catia/probreporting.html](http://w3.rchland.ibm.com/projects/catia/probreporting.html)\> 01/98 -- erh  
Use this web page to report problems with Catia.  Encourage the users to access the page and report the problem themselves, but if they  
are unable to view web pages you can submit the problem report for them.  To view the list of reported problems, see the \[problem  
viewer\]?URL:[http://w3.rchland.ibm.com/projects/catia/cgi-bin/probviewer.cgi](http://w3.rchland.ibm.com/projects/catia/cgi-bin/probviewer.cgi)\>.

\[Load Leveler home page\]?URL:[http://w3.rchland.ibm.com/~loadl/](http://w3.rchland.ibm.com/~loadl/)\> 01/98 -- erh  
LoadLeveler is used to manage the workstation resource use by the Rochester Engineering Lab. Things are set up with both dedicated  
and desktop workstations being part of the LoadLeveler pool. This allows a large number of jobs to be allowed to run by using up the  
"extra" CPU from the desktop systems. The goal of the LoadLeveler configurations on the workstations is to maximize the amount of CPU  
that is utilized. There is a tool for monitoring loadleveler jobs and system performance in ~csc/bin/ezhd. \[Run ezhd\]RUN:ezhd

\[Dial / LPFK Configuration\]?URL:[http://w3.rchland.ibm.com/~erhepp/help/gioconfig.html](http://w3.rchland.ibm.com/~erhepp/help/gioconfig.html)\>  06/98 -- erh  
Some MDA users (actually some EDA users as well) have dials and lpfk peripheral devices attached to their workstations.  These can be  
attached either to a gio card which occupies a slot in the workstation, or to the serial ports on the workstation.  If a gio card is used, no  
further configuration is reqired.  However, if the devices are attached to the serial ports, the directions contained in the above URL link  
must be followed.  Contact Eric Hepp if you have questions.  
   
   
   
   
   
   
 

\=========================================================================

MISCELLANEOUS  ITEMS

 Please call Maintenance at 3-2271 for all  lighting, heating, cooling, window  
shade problems, water leaks, washroom problems, ordering power strips,  
clock requests/repairs, and carpet  repairs.   (06/98 dkm

Any questions, please call CSC Help Line 3-9700.

\# 3 possible move 's:

   [#move](http://w3.rchland.ibm.com///.../rchland.ibm.com/fs/rs_aix43/lpp/info/usr.share.man.info/en_US/a_doc_lib/cmds/aixcmds4//remove.htm)  
   [#move](http://w3.rchland.ibm.com///.../rchland.ibm.com/fs/rs_aix43/lpp/info/usr.share.man.info/en_US/a_doc_lib/cmds/aixcmds4//remove.htm)  
   [#remove](http://w3.rchland.ibm.com///.../rchland.ibm.com/fs/rs_aix43/lpp/info/usr.share.man.info/en_US/a_doc_lib/cmds/aixcmds4//remove.htm)

[AAAA](http://w3.rchland.ibm.com///.../rchland.ibm.com/fs/rs_aix43/lpp/info/usr.share.man.info/en_US/a_doc_lib/cmds/aixcmds4//remove.htm)

[GUESTBOOK](http://w3.rchland.ibm.com///.../rchland.ibm.com/fs/rs_aix43/lpp/info/usr.share.man.info/en_US/a_doc_lib/cmds/aixcmds4//remove.htm)