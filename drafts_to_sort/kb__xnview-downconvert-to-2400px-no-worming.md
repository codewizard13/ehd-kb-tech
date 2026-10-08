<!-- 🔗 Custom Stylesheet -->
<link rel="stylesheet" href="../../_css/main.css">


<!-- 🖼️ Site Logo -->
![Site Logo](placeholder-logo.png){height=32}


<!-- 📝 Title -->
# HOW-TO: 📘 IMAGE PROCESSING: Eliminating Sharpening-Induced JPEG Artifacts in XnView MP



**Version:** 1.1


> Optimized for: VSCode on Windows 11 + Git Bash (SSH)


<!-- 🧭 Navigation -->
### 🏚️ Home | 📁 HOW-TO


<!-- 👤 Metadata -->
| **Author**:       | Eric L. Hepperle |
| ----------------- | ---------------- |
| **Date Created**: | 2025-12-22       |
| **Date Updated**: | 2025-12-22       |
| **AI Assistance**:| ChatGPT (analysis + structuring) |


---


<!-- 🔎 Table of Contents -->
<details open>
<summary><strong>Table of Contents</strong></summary>

- [HOW-TO: 📘 IMAGE PROCESSING: Eliminating Sharpening-Induced JPEG Artifacts in XnView MP](#how-to--image-processing-eliminating-sharpening-induced-jpeg-artifacts-in-xnview-mp)
    - [🏚️ Home | 📁 HOW-TO](#️-home---how-to)
  - [Tags:](#tags)
  - [📌 Overview](#-overview)
    - [Problem Statement](#problem-statement)
    - [Why the Issue Is Subtle](#why-the-issue-is-subtle)
  - [Observed Artifact Characteristics](#observed-artifact-characteristics)
  - [Root Cause Analysis](#root-cause-analysis)
    - [Sharpening-Induced Quantization Noise](#sharpening-induced-quantization-noise)
    - [Why Lanczos Is Not at Fault](#why-lanczos-is-not-at-fault)
  - [XnView MP Configuration Review](#xnview-mp-configuration-review)
  - [Corrective Actions](#corrective-actions)
    - [Option A: Correct the Sharpening Parameters (Recommended)](#option-a-correct-the-sharpening-parameters-recommended)
    - [Option B: Increase JPEG Quality](#option-b-increase-jpeg-quality)
  - [🧪 Case Study: Validated Working Sharpening Parameters](#-case-study-validated-working-sharpening-parameters)
    - [Summary of Correction](#summary-of-correction)
    - [Verified Working Settings (XnView MP)](#verified-working-settings-xnview-mp)
    - [Why This Works With Integer Radius](#why-this-works-with-integer-radius)
    - [Updated Best-Practice Recommendation (2400px JPEG Masters)](#updated-best-practice-recommendation-2400px-jpeg-masters)
  - [Best-Practice SOPs](#best-practice-sops)
    - [Web-Ready 2400px Images](#web-ready-2400px-images)
    - [Print or Archival Masters](#print-or-archival-masters)
  - [Validation Checklist](#validation-checklist)
  - [📚 References / See Also](#-references--see-also)
    - [Image Processing Theory](#image-processing-theory)
    - [Tools \& Software](#tools--software)
    - [Practical Guides](#practical-guides)
  - [✅ Revision History](#-revision-history)

</details>


---


<section id="sec-tags">


## Tags:


- XnView MP
- JPEG artifacts
- Image sharpening
- Photo downscaling
- Color management


</section>


---


## 📌 Overview


This knowledge base article documents and explains a specific class of image degradation observed when batch-downconverting photographs to a **2400px longest side** using **XnView MP**. The issue manifests as an organic, grainy, or *fingerprint-like* texture visible only at **1:1 (actual pixel) viewing**, despite the image appearing normal or sharp at smaller display sizes.

The workflow under examination is otherwise technically sound: high-quality Lanczos resampling, correct sRGB color management, 4:4:4 chroma subsampling, and optimized JPEG encoding. The degradation is therefore not the result of poor resizing or color handling, but rather a **compound interaction between sharpening and JPEG compression**.

Understanding this interaction is critical for anyone producing reusable web or archival image masters, especially when adopting a “set-and-forget” batch processing SOP.


---


### Problem Statement


After resizing high-resolution photographs to 2400px and exporting as JPEG, the resulting images exhibit:

- Grain-like whorls in skin tones
- Swirly texture in hair, water, or soft gradients
- A degradation that is *not* pixelation or aliasing

These artifacts are only visible at full resolution and are absent in the original files.


---


### Why the Issue Is Subtle


- Downsampled previews (≤600px wide) mask the issue
- The artifact emerges only after JPEG quantization
- The visual pattern resembles noise rather than compression blocks
- Many tools and tutorials misattribute this to resizing filters


---


## Observed Artifact Characteristics


- Appears as organic, non-linear texture
- Follows edges and micro-contrast regions
- Strongest in mid-tone gradients
- Invisible at reduced display sizes
- Becomes obvious at 1:1 inspection


![Artifact Example Placeholder](placeholder-artifact-example.png)


---


## Root Cause Analysis


### Sharpening-Induced Quantization Noise


The correct technical classification of the observed degradation is:

**Sharpening-accentuated JPEG quantization artifacts**

Also commonly referred to as:

- Worming
- Mosquito noise
- High-frequency ringing breakup

This occurs when **unsharp masking amplifies micro-contrast** that cannot be preserved cleanly by JPEG’s Discrete Cosine Transform (DCT), especially at mid-range quality settings.


---


### Why Lanczos Is Not at Fault


- Lanczos ringing produces symmetric halos, not organic textures
- Resampling artifacts would be visible before JPEG export
- The degradation appears only after compression
- The issue persists regardless of resize order correctness

Lanczos remains an appropriate and high-quality resampling choice.


---


## XnView MP Configuration Review


The following settings are confirmed as **correct and not causal**:

- Resize mode: Longest side
- Resample filter: Lanczos
- Gamma correction: Disabled
- Color space: sRGB via ICC convert
- Chroma subsampling: 4:4:4
- DCT method: Floating-point
- Metadata retention: Enabled

The problematic interaction lies specifically in:

- Unsharp Mask parameters
- JPEG quality level


---


## Corrective Actions


### Option A: Correct the Sharpening Parameters (Recommended)


Adjust the Unsharp Mask action to reduce high-frequency amplification:

- Radius: 0.6–0.8 *(conceptual best-practice range; see case study for XnView MP’s integer-radius limitation)*
- Amount: 2–3
- Threshold: 6–10

This protects smooth gradients and skin tones while maintaining perceived sharpness.


---


### Option B: Increase JPEG Quality


If maintaining stronger sharpening:

- Set JPEG quality to 85–90

This reduces quantization severity and preserves edge continuity at the cost of modestly larger file sizes.


---


## 🧪 Case Study: Validated Working Sharpening Parameters


### Summary of Correction


Further empirical testing confirmed that the image degradation issue was fully resolved using a **practical variation of Option A**, constrained by the actual behavior of the **XnView MP Unsharp Mask UI**.

While theoretical best practice often recommends sub-pixel radius values (for example 0.6–0.8), **XnView MP’s Radius slider only supports a 0–100 integer scale**. Despite this limitation, a stable and artifact-free result was achieved using the configuration below.


### Verified Working Settings (XnView MP)


**Unsharp Mask:**

- Radius: **1**
- Amount: **2.00**
- Threshold: **3.00**

These values:

- Preserve edge clarity without amplifying JPEG DCT boundaries
- Avoid sharpening of low-contrast skin tones and gradients
- Eliminate fingerprint-like worming artifacts at 1:1 (2400px) inspection
- Remain visually neutral at smaller display sizes


### Why This Works With Integer Radius


- A Radius of 1 approximates low-radius micro-contrast sharpening without extending across multiple DCT blocks.
- Lower Amount prevents structural edge over-accentuation.
- Moderate Threshold suppresses sharpening of noise and skin texture.
- The combination aligns sharpened detail *within* JPEG’s compression tolerance at quality ≥75.

This confirms that **the artifact was not caused by resizing, resampling, or color management**, but by **over-aggressive sharpening relative to JPEG quantization limits** in the previous configuration.


### Updated Best-Practice Recommendation (2400px JPEG Masters)


For XnView MP users constrained to integer radius values:

- Use Unsharp Mask **only if necessary**.
- Prefer the following when sharpening is desired:
  - Radius: **1**
  - Amount: **2.00**
  - Threshold: **3.00**
- Pair with JPEG quality **85** for maximum safety, or **75** if file size is critical and sharpening remains as restrained above.


---


## Best-Practice SOPs


### Web-Ready 2400px Images


- Resize → ICC convert
- **Either no sharpening**, or Unsharp Mask with the **case-study settings** (Radius 1, Amount 2, Threshold 3)
- Export JPEG at quality 85 (or 75 with conservative sharpening)
- Allow browser and display scaling to handle perceived sharpness


---


### Print or Archival Masters


- Resize → ICC convert
- Save as JPEG quality 90 **or** PNG
- Apply sharpening later, tailored to final output size and medium

This preserves maximum tonal integrity and defers irreversible processing.


---


## Validation Checklist


- Inspect output at 1:1 zoom
- Examine skin tones and gradients
- Compare sharpened vs non-sharpened exports
- Test JPEG quality increments (75 → 85 → 90)
- Confirm artifact absence before batch reuse


---


## 📚 References / See Also


### Image Processing Theory


- [JPEG Compression Overview](https://en.wikipedia.org/wiki/JPEG)
- [Unsharp Mask](https://en.wikipedia.org/wiki/Unsharp_masking)
- [Quantization (Image Processing)](https://en.wikipedia.org/wiki/Quantization_(image_processing))


### Tools & Software


- [XnView MP](https://www.xnview.com/en/xnviewmp/)
- [Lanczos Resampling](https://en.wikipedia.org/wiki/Lanczos_resampling)


### Practical Guides


- [Cambridge in Colour – Sharpening](https://www.cambridgeincolour.com/tutorials/image-sharpening.htm)
- [DPReview – JPEG Artifacts Explained](https://www.dpreview.com/learn/2799100490/jpeg-compression-artifacts-explained)


---


## ✅ Revision History


| Version | Date       | Author           | Changes Made                                                                     |
|--------|------------|------------------|----------------------------------------------------------------------------------|
| 1.00   | 2025-12-22 | Eric L. Hepperle | Initial draft created                                                            |
| 1.01   | 2025-12-22 | Eric L. Hepperle | Case study added with validated XnView MP Unsharp Mask parameters (Radius = 1)   |