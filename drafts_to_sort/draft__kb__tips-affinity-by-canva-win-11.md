<!-- 🔗 Custom Stylesheet -->
<link rel="stylesheet" href="../../_css/main.css">
<!-- 🖼️ Site Logo -->
!Site Logo{height=32}

<!-- 📝 Title -->

# HOW-TO: 📘 Safely Install And Navigate The New Affinity By Canva On Windows

**Version:** 1.1

> Optimized for: VSCode on Windows 11 + Git Bash (SSH)

<!-- 🧭 Navigation -->

### [🏚️ Home](../README.md) | [📁 HOW-TO](index.md)

<!-- 👤 Metadata -->
| **Author**: | Eric L. Hepperle |
| :-- | :-- |
| **Date Created**: | 2026-01-21 |
| **Date Updated**: | 2026-01-21 |
| **AI Assistant**: | ChatGPT (GPT-5.2) |


***

<!-- SECTION: Tags -->
<section id="sec-tags">


## Tags:


- Affinity
- Affinity by Canva
- Canva Acquisition
- Windows Software
- Installation
- Branding
- Serif


</section>

***

## 📌 Overview

This article answers **two closely related questions** for Windows users working with Affinity after the Canva acquisition and late‑2025 rebrand:

- How can you **safely install and manage** Affinity on Windows when moving between legacy Serif builds and the new Affinity by Canva?
- How can you **instantly tell** whether you are running an older Serif‑branded Affinity app or the newer “Affinity by Canva” incarnation?

As of **January 2026**, Canva owns the Affinity suite and has relaunched it as an “all‑new Affinity” experience, built around a unified app and a new brand identity, while older Serif V1/V2 desktop apps remain usable on Windows as separate, locally installed executables. This KB explains what changed (ownership, branding, free pricing, unified app) and what did not (local desktop installs, side‑by‑side behavior), then shows quick visual cues—icons, naming, and branding—so you can immediately recognize which incarnation you are using.[^1][^2][^3][^4][^5][^6]

***

## 🔍 TL;DR (Quick Answers)


- **Q1 – Can I safely install the new Affinity by Canva without breaking my existing Serif Affinity apps on Windows?**  
  - Yes. Legacy Serif Affinity apps (Designer/Photo/Publisher V1/V2) are local desktop installs that live in their own directories, and newer Affinity builds install **side‑by‑side** where supported, without auto‑removing or overwriting older versions. [cgchannel](https://www.cgchannel.com/2025/10/why-has-serif-stopped-selling-its-affinity-software/)
  - You generally **do not need to uninstall** existing versions first; keep at least one stable legacy build while you test newer Affinity versions, and only clean up older installs later if you are tight on disk space or want to reduce icon/file‑association clutter. [cgchannel](https://www.cgchannel.com/2025/10/why-has-serif-stopped-selling-its-affinity-software/)

- **Q2 – How do I tell at a glance whether I’m using legacy Serif Affinity or the new Affinity by Canva?**  
  - Legacy Serif builds show **three separate, angular triangle icons** (blue Designer, purple Photo, red Publisher) and identify themselves as “Designer/Photo/Publisher 2” with Serif credited in About dialogs. [itsnicethat](https://www.itsnicethat.com/articles/affinity-rebrand-canva-graphic-design-product-design-project-301025)
  - Affinity by Canva uses a **single unified Affinity app** with a lowercase serif “a” logo, Canva branding, and “all‑new Affinity” messaging, reflecting the 2025 relaunch and free‑to‑use model. [uxpilot](https://uxpilot.ai/blogs/canva-affinity)

***

## 🧭 Table of Contents

<details open>
```
<summary><strong>Click to expand</strong></summary>
```

- [HOW-TO: 📘 Safely Install And Navigate The New Affinity By Canva On Windows](#how-to--safely-install-and-navigate-the-new-affinity-by-canva-on-windows)
    - [🏚️ Home | 📁 HOW-TO](#️-home---how-to)
  - [Tags:](#tags)
  - [📌 Overview](#-overview)
  - [🔍 TL;DR (Quick Answers)](#-tldr-quick-answers)
  - [🧭 Table of Contents](#-table-of-contents)
  - [🏷️ Current Affinity Status After Canva Acquisition (2026)](#️-current-affinity-status-after-canva-acquisition-2026)
    - [What Changed After The Canva Acquisition](#what-changed-after-the-canva-acquisition)
    - [What Did Not Change](#what-did-not-change)
  - [💻 Installation Behavior On Windows](#-installation-behavior-on-windows)
    - [Side-by-Side Installation](#side-by-side-installation)
    - [Licensing And Activation](#licensing-and-activation)
  - [❓ Do You Need To Uninstall Existing Versions?](#-do-you-need-to-uninstall-existing-versions)
    - [Recommended Scenarios (No Uninstall Required)](#recommended-scenarios-no-uninstall-required)
    - [Optional Cleanup Scenarios](#optional-cleanup-scenarios)
  - [Recognizing “Affinity By Canva” Vs Legacy Serif Affinity](#recognizing-affinity-by-canva-vs-legacy-serif-affinity)
    - [Branding Generations At A Glance](#branding-generations-at-a-glance)
    - [Visual Cues On Desktop And Taskbar](#visual-cues-on-desktop-and-taskbar)
    - [In-App Cues: Splash, Naming, And About Boxes](#in-app-cues-splash-naming-and-about-boxes)
    - [Quick Identification Checklist](#quick-identification-checklist)
  - [Placeholder Images](#placeholder-images)
  - [⭐ Best Practices For Windows Users](#-best-practices-for-windows-users)
  - [📚 References / See Also](#-references--see-also)
    - [Affinity \& Serif (Legacy Context)](#affinity--serif-legacy-context)
    - [Canva, Acquisition, And New Affinity](#canva-acquisition-and-new-affinity)
    - [Affinity Branding And Rebrand Details](#affinity-branding-and-rebrand-details)
    - [HTML Details/Summary For TOC (JS-Free)](#html-detailssummary-for-toc-js-free)
    - [Windows Software Management](#windows-software-management)
  - [✅ Revision History](#-revision-history)

</details>

***

## 🏷️ Current Affinity Status After Canva Acquisition (2026)

### What Changed After The Canva Acquisition

- **Canva acquired Affinity** (formerly Serif’s Affinity suite) in 2024, gaining ownership of Affinity Designer, Photo, and Publisher.[^3][^7][^8][^1]
- In late 2025, Canva launched the **“all‑new Affinity”**, a unified app with a new brand identity and made it free to use for professional designers worldwide.[^2][^5][^6]
- The new branding centers on a custom lowercase serif **“a”** logomark and a visual system that positions Affinity as a pro sibling to Canva’s broader design platform.[^2]


### What Did Not Change

- Legacy Affinity desktop apps for Windows (Designer, Photo, Publisher V1/V2) continue to run as **local installs**; they are not automatically converted into Canva‑style apps.[^4][^3]
- Legacy apps still appear as **separate programs** (Designer, Photo, Publisher) and can coexist alongside any newer Affinity builds where supported.[^4]
- Existing perpetual licenses for Serif‑era Affinity remain valid under their original terms; Canva’s new free model applies going forward rather than revoking older entitlements.[^6][^4]

***

## 💻 Installation Behavior On Windows

### Side-by-Side Installation

- Legacy Affinity installers on Windows (for example, V1 vs V2) install into **separate directories** and do **not** automatically uninstall previous major versions.[^4]
- User data such as brushes, assets, and presets remains largely **per‑version**, so testing a newer version while keeping an older, stable one installed is a common and supported workflow.[^4]


### Licensing And Activation

- Legacy versions continue to sign in and activate using existing **Affinity/Serif accounts** associated with purchased licenses.[^4]
- Canva accounts are relevant for the **new free Affinity experience** and Canva ecosystem features, but are not retroactively required to run previously licensed desktop builds that were purchased before the Canva‑era launch.[^5][^6]

***

## ❓ Do You Need To Uninstall Existing Versions?

### Recommended Scenarios (No Uninstall Required)

- You are installing a **newer Affinity build** (for example, evaluating the Canva‑era Affinity) and want to migrate gradually from Serif V2 without risking project compatibility.[^5][^4]
- You maintain **older client projects** that must remain openable in a specific version due to plugin, font, or color‑management constraints.[^4]
- You are benchmarking performance, UI, or feature differences between legacy Serif builds and the new Canva‑era Affinity on the same machine.[^5][^4]


### Optional Cleanup Scenarios

You may choose to uninstall older Serif versions if:

- Disk space is limited and you no longer need historical versions.
- All active projects have been safely migrated to the newer Affinity build and tested end‑to‑end.
- You want to avoid **UI confusion** (multiple Affinity icons, duplicate file associations, or ambiguous “.afdesign” handler).

Uninstallation can be safely performed via:

- **Windows Settings**
    - Apps
    - Installed Apps
    - Select the Affinity app
    - Uninstall

This process leaves remaining Affinity versions intact and does not affect Canva’s web platform or account status.[^3][^4]

***

## Recognizing “Affinity By Canva” Vs Legacy Serif Affinity

### Branding Generations At A Glance

| Aspect | Legacy Serif Affinity (V1/V2) | Affinity By Canva (All‑New Affinity) |
| :-- | :-- | :-- |
| Brand owner | [Serif Europe](https://en.wikipedia.org/wiki/Serif_Europe) | [Canva](https://www.canva.com/) (Affinity division) |
| Era | Initial releases through Affinity V2 (pre‑relaunch)[^4] | Relaunched Oct–Nov 2025 as “all‑new Affinity”, globally free to use[^5][^6][^2] |
| Core logo motif | Sharp, **angular** triangle icons per app (blue Designer, purple Photo, red Publisher)[^2][^4] | Custom lowercase serif **a** logo with swooping curves and precise points[^2] |
| Product structure | Three distinct desktop apps: Designer, Photo, Publisher[^4] | Unified multi‑tool Affinity app (“Affinity Studio” experience)[^9][^5] |
| Colour personality | Saturated neon‑style gradients and strong color splits[^2][^4] | Muted materials palette (charcoal/graphite/putty) with lime‑green accent pops[^2] |
| Pricing model (2026) | Historic perpetual licenses; no longer sold new after Canva relaunch[^4] | Free to download and use; Canva commits publicly to keeping Affinity free[^5][^6] |

### Visual Cues On Desktop And Taskbar

- **Icon shape and count**
    - Legacy Serif installs typically show **three separate icons**: angular triangles in blue (Designer), purple (Photo), and red (Publisher).[^2][^4]
    - Canva‑era Affinity appears as a **single app icon** using the lowercase serif “a”, representing the unified suite of tools.[^9][^2][^5]
- **Colour and personality**
    - Legacy icons lean heavily into sharp facets and bright gradients common to earlier pro design tools.[^2][^4]
    - The new Affinity branding is more playful and refined, using a bespoke serif typeface and lime‑accented materials palette that stands apart from the old “angular” look.[^2]


### In-App Cues: Splash, Naming, And About Boxes

- **Product naming**
    - Legacy apps identify themselves specifically as “Affinity Designer 2”, “Affinity Photo 2”, or “Affinity Publisher 2” in splash screens and title bars.[^4]
    - Canva‑era builds emphasize “Affinity” as a single unified product, often described as the “all‑new Affinity” or “Affinity Studio” in marketing and onboarding flows.[^10][^9][^5]
- **Ownership and messaging**
    - Legacy “About” dialogs and documentation reference **Serif (Europe) Ltd.** as the publisher.[^4]
    - New materials connect Affinity explicitly to **Canva**, highlighting that Affinity is now free and part of Canva’s broader mission to empower designers at every level.[^6][^3][^5]


### Quick Identification Checklist

- From the taskbar or dock:
    - If you see **three angular triangle icons** (blue/purple/red) as separate apps, you are using legacy Serif Affinity.[^2][^4]
    - If you see **one serif “a” icon** representing everything, you are using the newer Affinity by Canva.[^9][^5][^2]
- From inside the app:
    - If “Designer/Photo/Publisher 2” appears prominently and Serif is credited in About, it is a legacy build.[^4]
    - If “all‑new Affinity” messaging, Canva references, and unified Affinity naming dominate, it is the Canva‑era incarnation.[^6][^5][^2]

***

## Placeholder Images

- Affinity by Canva logo sample:
    - `![Affinity by Canva Logo Placeholder](placeholder-affinity-canva-logo.png)`
- Legacy Serif Affinity triangle icons sample (Designer, Photo, Publisher):
    - `![Legacy Serif Affinity Icons Placeholder](placeholder-affinity-serif-triangles.png)`

***

## ⭐ Best Practices For Windows Users

- Keep **at least one stable legacy build** installed while you evaluate the Canva‑era Affinity to avoid project disruption.
- Back up custom assets (brushes, macros, assets, palettes) before uninstalling any Affinity version or testing a new major generation.
- Use icon and naming differences (triangles vs serif “a”; three apps vs one app) to quickly confirm which environment you are in before opening critical production documents.[^5][^2][^4]
- Monitor official Affinity and Canva announcements for any future changes to installers, migration tools, or deeper Canva Cloud integration.[^1][^3][^6][^5]

***

## 📚 References / See Also

### Affinity \& Serif (Legacy Context)

```
- <a href="https://affinity.serif.com" target="_blank">Affinity Official Website</a>[^4]
```

```
- <a href="https://affinity.serif.com/en-us/support/" target="_blank">Affinity Support</a>[^4]
```

```
- <a href="https://en.wikipedia.org/wiki/Serif_Europe" target="_blank">Serif Europe (Wikipedia)</a>[^11]
```

```
- <a href="https://www.cgchannel.com/2025/10/why-has-serif-stopped-selling-its-affinity-software/" target="_blank">Why has Serif stopped selling its Affinity software?</a>[^4]
```


### Canva, Acquisition, And New Affinity

```
- <a href="https://www.canva.com/newsroom/" target="_blank">Canva Newsroom</a>[^6][^5]
```

```
- <a href="https://www.canva.com" target="_blank">Canva</a>[^5][^6]
```

```
- <a href="https://www.canva.com/newsroom/news/all-new-affinity/" target="_blank">Introducing the all‑new Affinity: Professional design, now free for all</a>[^5]
```

```
- <a href="https://www.canva.com/newsroom/news/affinity-free/" target="_blank">Why we made Affinity free, and how we’ll keep it that way</a>[^6]
```

```
- <a href="https://www.theverge.com/2024/3/26/24112277/canva-affinity-acquisition-design-software-suite-adobe-rival" target="_blank">Canva acquires Affinity to fill the Adobe‑sized holes in its design suite</a>[^3]
```

```
- <a href="https://techcrunch.com/2024/03/26/with-affinity-acquisition-canva-should-be-able-to-compete-better-with-adobes-creative-tools/" target="_blank">With Affinity acquisition, Canva should be able to compete better with Adobe</a>[^7]
```

```
- <a href="https://fortune.com/2024/03/26/canva-acquires-design-software-provider-affinity/" target="_blank">Canva acquires design software provider Affinity</a>[^8]
```


### Affinity Branding And Rebrand Details

```
- <a href="https://www.itsnicethat.com/articles/affinity-rebrand-canva-graphic-design-product-design-project-301025" target="_blank">Bold.af: the Affinity rebrand blends personality and precision</a>[^2]
```

```
- <a href="https://www.creativebloq.com/design/branding/im-absolutely-loving-the-affinity-rebrand" target="_blank">I’m absolutely loving the Affinity rebrand</a>[^12]
```


### HTML Details/Summary For TOC (JS-Free)

```
- <a href="https://utilitybend.com/blog/the-details-element-collapsing-content-without-the-hassle/" target="_blank">The details element, collapsing content without the hassle</a>[^13]
```

```
- <a href="https://dev.to/ilham-bouktir/creative-ways-to-style-the-html-details-tag-3c5k" target="_blank">Creative Ways to Style the HTML Details Tag</a>[^14]
```


### Windows Software Management

```
- <a href="https://learn.microsoft.com/windows/apps" target="_blank">Microsoft Windows App Management Documentation</a>[^14]
```


***

## ✅ Revision History

| Version | Date | Author | Changes Made |
| :-- | :-- | :-- | :-- |
| 1.00 | 2026-01-21 | Eric L. Hepperle | Initial draft created (installation focus) |
| 1.10 | 2026-01-21 | Eric L. Hepperle | Integrated branding/identification section for Affinity by Canva |

<span style="display:none">[^15][^16]</span>

<div align="center">⁂</div>

[^1]: https://www.constellationr.com/blog-news/insights/canva-acquires-affinity-move-better-target-designers

[^2]: https://www.itsnicethat.com/articles/affinity-rebrand-canva-graphic-design-product-design-project-301025

[^3]: https://www.theverge.com/2024/3/26/24112277/canva-affinity-acquisition-design-software-suite-adobe-rival

[^4]: https://www.cgchannel.com/2025/10/why-has-serif-stopped-selling-its-affinity-software/

[^5]: https://www.canva.com/newsroom/news/all-new-affinity/

[^6]: https://www.canva.com/newsroom/news/affinity-free/

[^7]: https://techcrunch.com/2024/03/26/with-affinity-acquisition-canva-should-be-able-to-compete-better-with-adobes-creative-tools/

[^8]: https://fortune.com/2024/03/26/canva-acquires-design-software-provider-affinity/

[^9]: https://uxpilot.ai/blogs/canva-affinity

[^10]: https://www.youtube.com/watch?v=lTeperbIZBc

[^11]: https://en.wikipedia.org/wiki/Serif_Europe

[^12]: https://www.creativebloq.com/design/branding/im-absolutely-loving-the-affinity-rebrand

[^13]: https://utilitybend.com/blog/the-details-element-collapsing-content-without-the-hassle/

[^14]: https://dev.to/ilham-bouktir/creative-ways-to-style-the-html-details-tag-3c5k

[^15]: https://www.reddit.com/r/Affinity/comments/1okxvll/now_we_know_what_the_software_is_but_what_do_you/

[^16]: https://javascript.plainenglish.io/html-tips-expandable-content-with-details-summary-3e85fdd8eaf1

