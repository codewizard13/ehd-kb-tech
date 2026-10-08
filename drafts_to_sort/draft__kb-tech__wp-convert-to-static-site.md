<!-- 🔗 Custom Stylesheet -->
<link rel="stylesheet" href="../../_css/main.css">


<!-- 🖼️ Site Logo -->
!Site Logo{height=32}


<!-- 📝 Title -->
# HOW-TO: 📘 WORDPRESS: Save Site As Static Snapshot


**Version:** 1.0


> Optimized for: VSCode on Windows 11 + Git Bash (SSH)


<!-- 🧭 Navigation -->
### [🏚️ Home](../README.md) | [📁 [CATEGORY <HOW-TO>](index.md)


<!-- 👤 Metadata -->
| **Author**:        | Eric L. Hepperle |
| ------------------ | ---------------- |
| **Date Created**:  | 2026-03-26       |
| **Date Updated**:  | --               |
| **AI Assistant**: | ChatGPT          |


---


<section id="sec-tags">


## Tags:


- WordPress
- Static Sites
- HTTrack
- Security
- Portfolio


</section>


---


## 📌 Overview


Creating a **static snapshot of a WordPress website** is a highly effective way to preserve the **visual design and front-end experience** of a site while eliminating the risks associated with running a dynamic WordPress installation.

This approach is especially valuable when:

- Working with **legacy WordPress versions** (e.g., WP 5.1.1)
- Avoiding **plugin compatibility issues**
- Reducing **security vulnerabilities** (bots, exploits, malware)
- Showcasing **portfolio work** without maintaining backend infrastructure

In this case, the WordPress site:

- Was restored from an older backup
- Runs on outdated WordPress, PHP, and MySQL versions
- Previously experienced a **security breach**
- Needs to be preserved as a **front-end design artifact only**

Because of these constraints, **installing modern WordPress plugins for static export was not practical or safe**.

👉 The chosen solution: **external site crawling using HTTrack**

This method avoids modifying the WordPress environment entirely and instead captures a **fully rendered snapshot** of the site as static HTML, CSS, and JavaScript files.

---

<details open>
<summary><strong>📚 Table of Contents</strong></summary>

- Overview
- Use Case
- Constraints And Risks
- Available Methods
  - WordPress Plugin Approach
  - External Crawler Approach
- Recommended Solution (HTTrack)
- Step-By-Step Instructions
- Known Limitations
- Validation Checklist
- Hosting Static Output
- Troubleshooting
- References
</details>

---


## 🎯 Use Case


- Preserve a **client website design**
- Display work in a **portfolio**
- Eliminate backend dependencies
- Prevent future hacks or malware infections

---

## ⚠️ Constraints And Risks


- WordPress version is outdated (WP 5.1.1)
- Plugins show compatibility warnings
- Updating WordPress could:
  - Break layout
  - Break theme functionality
  - Break legacy plugins
- Site has **history of being hacked**
- Must avoid exposing site publicly during process

---

## 🧠 Available Methods


### 🔌 WordPress Plugin Approach (Not Used)


Common plugins:

- <a href="https://wordpress.org/plugins/simply-static/" target="_blank">Simply Static</a>
- <a href="https://wordpress.org/plugins/staatic/" target="_blank">Staatic</a>

**Pros:**
- Integrated into WordPress
- Easy export workflow
- Designed specifically for static generation

**Cons (critical in this case):**
- Require modern WordPress versions
- Risk of breaking legacy site
- Plugin conflicts likely
- Not safe for outdated environments

👉 **Conclusion:** Not practical due to legacy system constraints

---

### 🌐 External Crawler Approach (Chosen Method)


Tool used:

- <a href="https://www.httrack.com/" target="_blank">HTTrack Website Copier</a>

**Pros:**
- Works independently of WordPress
- No need to install plugins
- Zero risk to original site
- Compatible with any WP version
- Captures rendered front-end exactly

**Cons:**
- Can be slow for large sites
- Requires configuration tuning
- Some dynamic features won’t function

👉 **Conclusion:** Best option for legacy and high-risk environments

---

## ✅ Recommended Solution (HTTrack)


HTTrack works by:

- Crawling the site like a browser
- Downloading all assets (HTML, CSS, JS, images)
- Rebuilding the site locally as static files

**Key requirement:**

The WordPress site must be accessible via a local server URL:

```text
http://localhost/yoursite
````

---

## 🪜 Step-By-Step Instructions

### 1. Run Local WordPress Site

* Use XAMPP, WAMP, or similar
* Confirm site loads in browser:

```text
http://localhost/yoursite
```

---

### 2. Prepare Site

* Log out of admin
* Open site in incognito mode
* Navigate key pages to ensure rendering
* Ensure no admin bars or debug info visible

---

### 3. Configure HTTrack

* Set project URL:

  * `http://localhost/yoursite`
* Set scan depth:

  * High or unlimited
* Enable:

  * Download all site assets
* Optional filters:

```text
-*/wp-admin/*
-*/wp-login.php*
```

---

### 4. Start Crawl

* Run HTTrack
* Allow process to complete

⚠️ Note:

* Large sites may take significant time
* Status: **In progress (evaluation ongoing)**

---

### 5. Review Output

Open:

```text
index.html
```

Validate:

* Navigation works
* Layout is intact
* Images and styles load correctly

---

## ⚠️ Known Limitations

* Forms will not function
* Search will not function
* Login/admin areas removed
* Some JavaScript features may degrade

---

## ✅ Validation Checklist

* Site visually matches original
* No broken images
* No missing CSS
* Internal links work
* No references to `localhost` (or minimal)

---

## 🚀 Hosting Static Output

Recommended platforms:

* <a href="https://www.netlify.com/" target="_blank">Netlify</a>
* <a href="https://pages.github.com/" target="_blank">GitHub Pages</a>
* <a href="https://vercel.com/" target="_blank">Vercel</a>

**Benefits:**

* Free hosting
* HTTPS enabled
* No backend vulnerabilities
* Fast global CDN

---

## 🛠️ Troubleshooting

### Issue: Missing Styles or Images

* Re-run crawl with deeper scan
* Ensure asset downloading enabled

---

### Issue: Links Point to Localhost

* Enable relative URL rewriting in HTTrack
* Or manually replace paths

---

### Issue: Duplicate Pages

* Caused by query parameters
* Safe to ignore or clean manually

---

## 📚 References / See Also

### WordPress Static Plugins

* <a href="https://wordpress.org/plugins/simply-static/" target="_blank">Simply Static Plugin</a>
* <a href="https://wordpress.org/plugins/staatic/" target="_blank">Staatic Plugin</a>

---

### Static Site Tools

* <a href="https://www.httrack.com/" target="_blank">HTTrack Official Website</a>

---

### Hosting Platforms

* <a href="https://www.netlify.com/" target="_blank">Netlify</a>
* <a href="https://pages.github.com/" target="_blank">GitHub Pages</a>
* <a href="https://vercel.com/" target="_blank">Vercel</a>

---

### General Concepts

* Static Site Generation
* WordPress Security Best Practices
* Website Archiving Techniques

---

## ✅ Revision History

| Version | Date       | Author           | Changes Made                     |
| ------- | ---------- | ---------------- | -------------------------------- |
| 1.00    | 2026-03-26 | Eric L. Hepperle | Initial draft created            |
| 1.01    | --         | --               | Pending HTTrack crawl validation |

