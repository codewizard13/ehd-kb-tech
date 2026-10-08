<!-- 🔗 Custom Stylesheet -->
<link rel="stylesheet" href="../../_css/main.css">


<!-- 🖼️ Site Logo -->
!Site Logo{height=32}


<!-- 📝 Title -->
# HOW-TO: 📘 WORDPRESS PERFORMANCE: Diagnose And Optimize Page Speed With Lighthouse


**Version:** 1.0


> Optimized for: VSCode on Windows 11 + Git Bash (SSH)


<!-- 🧭 Navigation -->
### [🏚️ Home](../README.md) | [📁 HOW-TO](index.md)


<!-- 👤 Metadata -->
| **Author**:        | Eric L. Hepperle |
| ------------------ | ---------------- |
| **Date Created**:  | 2026-03-05       |
| **Date Updated**:  | --               |
| **AI Assistant**:  | ChatGPT          |


---


<section id="sec-tags">

## Tags:

- WordPress
- Page Speed
- Lighthouse
- Performance
- Image Optimization
- Caching

</section>


---


<details open>
<summary><strong>📑 Table Of Contents</strong></summary>

- 📌 Overview
- 🔍 Understanding Lighthouse Performance Metrics
  - Key Web Performance Metrics
  - What Slow Metrics Actually Mean
- 🧪 Establishing A Performance Baseline
  - Running A Lighthouse Audit
  - Identifying Server Response Bottlenecks
- ⚙️ Diagnosing WordPress Performance Issues
  - Using Query Monitor
  - Detecting Slow Plugins
  - Checking External API Calls
  - Separating Server And WordPress Delays
- 🖼️ Image Optimization Strategy
  - Understanding Image Dimensions Vs File Size
  - Identifying Oversized Images
  - Recommended Image Sizes For Websites
  - Compression And Modern Image Formats
- ⚡ Enabling Browser Caching
  - Why Cache Headers Matter
  - Example Apache Configuration
- 🧰 WordPress Tools For Optimization
  - Database Optimization
  - Image Optimization Plugins
- 📊 Performance Optimization Workflow
- 📚 References / See Also
  - Performance Testing
  - WordPress Optimization Tools
  - Image Optimization
  - Web Performance Learning Resources
- ✅ Revision History

</details>


---


## 📌 Overview

Website performance is a critical component of modern web development. Slow page loads negatively impact user experience, search engine rankings, and overall site usability. Tools such as Google Lighthouse provide developers with a structured way to analyze performance issues and identify opportunities for improvement.

This guide documents a practical workflow for diagnosing and improving performance on a WordPress website. The context originates from troubleshooting performance metrics on a site built with Elementor and the Astra theme. Initial Lighthouse testing revealed extremely slow server response times (Time To First Byte), which prompted deeper investigation into WordPress runtime behavior, plugin performance, caching configuration, and image optimization practices.

The troubleshooting process revealed an important insight: apparent server bottlenecks are not always caused by the hosting environment or the page builder itself. Instead, performance problems often originate from a combination of factors such as large image assets, missing browser caching headers, external scripts, or inefficient plugin execution.

This document outlines a systematic method for diagnosing WordPress performance problems using Lighthouse and other tools. Topics include identifying server response delays, auditing plugin behavior with Query Monitor, optimizing image assets, enabling browser caching, and establishing a repeatable workflow for performance analysis.

Although the examples referenced here originate from a specific portfolio website, the methods described apply broadly to most WordPress sites.

<img src="https://via.placeholder.com/900x400" alt="Lighthouse Performance Report Example">


---


## 🔍 Understanding Lighthouse Performance Metrics


### Key Web Performance Metrics

Google Lighthouse reports several key metrics that measure page rendering speed and responsiveness.

- **First Contentful Paint (FCP)**  
  Time required for the first visible element to appear on the page.

- **Largest Contentful Paint (LCP)**  
  Time required for the largest visible element (often a hero image or major section) to render.

- **Speed Index**  
  Measures how quickly the page visually fills with content.

- **Total Blocking Time (TBT)**  
  Time during which JavaScript blocks the main browser thread and prevents interaction.

- **Cumulative Layout Shift (CLS)**  
  Measures unexpected layout movement during page loading.

These metrics help identify whether performance problems originate from server latency, client-side scripts, or heavy media assets.


### What Slow Metrics Actually Mean

Certain metrics often point directly to common causes:

- Slow **TTFB** may indicate server processing delays or heavy plugin execution.
- High **LCP** is often caused by large images or slow font loading.
- High **TBT** usually indicates excessive JavaScript execution.


---


## 🧪 Establishing A Performance Baseline


### Running A Lighthouse Audit

Lighthouse audits can be run through Chrome DevTools or the web interface:

- <a href="https://developer.chrome.com/docs/lighthouse/overview/" target="_blank">Google Lighthouse</a>

Steps:

- Open Chrome DevTools
- Navigate to the **Lighthouse** panel
- Select **Performance**
- Run the audit


### Identifying Server Response Bottlenecks

One important metric is **Time To First Byte (TTFB)**.

Typical values:

- Under 200 ms: Excellent
- 200–800 ms: Good
- 800–1500 ms: Normal for uncached WordPress
- Over 3000 ms: Indicates a potential issue

Large TTFB spikes may be caused by:

- plugin initialization
- database queries
- server cold starts
- external API calls


---


## ⚙️ Diagnosing WordPress Performance Issues


### Using Query Monitor

The most effective debugging tool for WordPress runtime performance is:

- <a href="https://wordpress.org/plugins/query-monitor/" target="_blank">Query Monitor</a>

This plugin reveals:

- page generation time
- database query counts
- slow queries
- HTTP API calls
- plugin execution timing


### Detecting Slow Plugins

Query Monitor allows developers to view database queries grouped by plugin. This makes it possible to quickly identify which plugin contributes the most processing time.

Common offenders include:

- SEO analysis plugins
- backup plugins
- dynamic page builders
- security scanners


### Checking External API Calls

Plugins sometimes call remote services during page load. Query Monitor’s HTTP API section reveals requests such as:

- license checks
- analytics calls
- SEO scoring requests

These calls may delay page rendering if the remote service responds slowly.


### Separating Server And WordPress Delays

A simple diagnostic test involves creating a minimal PHP file.

Example:

```

test.php

```
```

<?php
echo "Server time: " . microtime(true);
```

If this file loads instantly while WordPress pages load slowly, the issue likely originates inside WordPress rather than the server environment.


---


## 🖼️ Image Optimization Strategy


### Understanding Image Dimensions Vs File Size

Image dimensions and file size are separate concerns.

Example:

| Image | Width | File Size |
|------|------|-----------|
| Image A | 2400px | 150 KB |
| Image B | 2400px | 620 KB |

Both display identically, but the larger file takes much longer to download.


### Identifying Oversized Images

Lighthouse reports commonly reveal large image assets such as:

- portfolio mockups
- screenshots
- hero images

These can exceed 500 KB each and significantly increase page weight.

Developers can inspect loaded images using Chrome DevTools:

- Right click page
- Select **Inspect**
- Open **Network**
- Filter by **Img**
- Sort by file size


### Recommended Image Sizes For Websites

Typical optimized sizes:

| Use Case | Recommended Width |
|--------|------------------|
| Hero images | 1600–2000 px |
| Portfolio images | 800–1200 px |
| Blog images | 800–1200 px |
| Thumbnails | 300–600 px |


### Compression And Modern Image Formats

Modern formats dramatically reduce file sizes.

Example conversion:

600 KB PNG → 140 KB WebP

Modern formats include:

- WebP
- AVIF


---


## ⚡ Enabling Browser Caching


### Why Cache Headers Matter

Without cache headers, browsers must re-download every resource on each visit.

Cache headers allow browsers to reuse previously downloaded files, reducing load times for returning visitors.


### Example Apache Configuration

```
<IfModule mod_expires.c>
ExpiresActive On
ExpiresByType image/webp "access plus 1 year"
ExpiresByType image/png "access plus 1 year"
ExpiresByType image/jpg "access plus 1 year"
ExpiresByType text/css "access plus 1 month"
ExpiresByType application/javascript "access plus 1 month"
</IfModule>
```


---


## 🧰 WordPress Tools For Optimization


### Database Optimization

A common maintenance plugin for database cleanup is:

- <a href="https://wordpress.org/plugins/wp-optimize/" target="_blank">WP-Optimize</a>

It can remove:

- orphaned tables
- post revisions
- transient cache entries


### Image Optimization Plugins

Dedicated image optimization plugins often produce better results than general performance plugins.

Examples:

- <a href="https://wordpress.org/plugins/shortpixel-image-optimiser/" target="_blank">ShortPixel Image Optimizer</a>
- <a href="https://wordpress.org/plugins/imagify/" target="_blank">Imagify</a>

These tools provide:

- aggressive compression algorithms
- WebP conversion
- automated bulk optimization


---


## 📊 Performance Optimization Workflow

A reliable workflow for WordPress performance optimization:

- run Lighthouse audit
- check server response time
- audit plugin execution with Query Monitor
- identify oversized images
- compress and convert images to WebP
- enable browser caching
- retest performance metrics

This iterative approach allows developers to isolate bottlenecks and confirm improvements after each change.


---


## 📚 References / See Also


### Performance Testing

- <a href="https://developer.chrome.com/docs/lighthouse/overview/" target="_blank">Google Lighthouse Documentation</a>
- <a href="https://pagespeed.web.dev/" target="_blank">Google PageSpeed Insights</a>


### WordPress Optimization Tools

- <a href="https://wordpress.org/plugins/query-monitor/" target="_blank">Query Monitor Plugin</a>
- <a href="https://wordpress.org/plugins/wp-optimize/" target="_blank">WP-Optimize Plugin</a>


### Image Optimization

- <a href="https://wordpress.org/plugins/shortpixel-image-optimiser/" target="_blank">ShortPixel Image Optimizer</a>
- <a href="https://wordpress.org/plugins/imagify/" target="_blank">Imagify Image Optimizer</a>


### Web Performance Learning Resources

- <a href="https://web.dev/performance/" target="_blank">web.dev Performance Guide</a>
- <a href="https://developer.mozilla.org/en-US/docs/Web/Performance" target="_blank">MDN Web Performance Documentation</a>


---


## ✅ Revision History


| Version | Date       | Author           | Changes Made |
| ------- | ---------- | ---------------- | ------------ |
| 1.00    | 2026-03-05 | Eric L. Hepperle | Initial draft created |
| 1.01    | --         | --               | -- |

