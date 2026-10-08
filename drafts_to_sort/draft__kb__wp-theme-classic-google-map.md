<!-- 🔗 Custom Stylesheet -->
<link rel="stylesheet" href="../../_css/main.css">

<!-- 🖼️ Site Logo -->
![Site Logo](/_pix/logos/logo-ehw-kb.svg){height=32}

<!-- 📝 Title -->

# HOW-TO: 📘 WORDPRESS CLASSIC THEME — Dynamic Food Truck Location Maps (Database-Decoupled)

**Version:** 1.0

> Optimized for: VSCode on Windows 11 + Git Bash (SSH)

<!-- 🧭 Navigation -->

### 🏚️ Home | 📁 HOW-TO

<!-- 👤 Metadata -->
| **Author**: | Eric L. Hepperle |
| :-- | :-- |
| **Date Created**: | 2025-12-30 |
| **Date Updated**: | 2025-12-30 |
| **AI Assistant**: | ChatGPT (GPT-5.2) |

---

<!-- SECTION: Tags -->
<section id="sec-tags">

## Tags:

- WordPress
- Classic Theme
- Google Maps
- Decoupled Architecture
- Food Truck
- Non-Technical Client
- No-Database
- No-JavaScript

</section>

---

<!-- 🔍 Content Section Heading -->

## 📌 Overview

This guide documents a **production-ready, database-decoupled approach** to implementing **dynamic location maps** in a **classic WordPress theme** for a **mobile food truck business** whose location changes **multiple times per day**.

The case study demonstrates how to balance:

- **Zero database reliance**
- **No JavaScript in content**
- **No plugin lock-in**
- **No Google Maps API keys or billing**
- **Ease of use for non-technical clients**
- **Version-controlled, code-centric theming**

The core architectural insight is this:

> **Separate “location editing” from WordPress entirely**, while keeping **rendering logic inside the theme**.

This is achieved by combining:
- A centralized `theme-data.php` configuration file
- **Google My Maps** as a visual, client-friendly “location CMS”
- A lightweight iframe embed rendered by PHP helpers
- Graceful fallbacks and usability enhancements (directions, lazy loading)

This pattern is ideal for **single-page classic themes**, **stateless deployments**, and **clients who must update content frequently without developer involvement**.

---

## 🗂️ Table of Contents

<details>
<summary><strong>Expand / Collapse</strong></summary>

- [HOW-TO: 📘 WORDPRESS CLASSIC THEME — Dynamic Food Truck Location Maps (Database-Decoupled)](#how-to--wordpress-classic-theme--dynamic-food-truck-location-maps-database-decoupled)
    - [🏚️ Home | 📁 HOW-TO](#️-home---how-to)
  - [Tags:](#tags)
  - [📌 Overview](#-overview)
  - [🗂️ Table of Contents](#️-table-of-contents)
  - [🧩 Problem Statement](#-problem-statement)
  - [🎯 Constraints and Design Goals](#-constraints-and-design-goals)
  - [❌ Why Traditional Approaches Fail](#-why-traditional-approaches-fail)
  - [✅ Recommended Architecture](#-recommended-architecture)
    - [🗺️ Data Source: **Google My Maps**](#️-data-source-google-my-maps)
    - [🧠 Theme Configuration Model](#-theme-configuration-model)
    - [🖥️ Rendering Strategy](#️-rendering-strategy)
  - [🛠️ Implementation Guide](#️-implementation-guide)
    - [🔧 Update `theme-data.php`](#-update-theme-dataphp)
    - [🧩 Map Rendering Helper](#-map-rendering-helper)
    - [🧱 Template Integration](#-template-integration)
    - [🎨 CSS Styling](#-css-styling)
  - [👤 Client Workflow](#-client-workflow)
  - [🧯 Failure Handling and Fallbacks](#-failure-handling-and-fallbacks)
  - [🧠 Why This Solution Works](#-why-this-solution-works)
  - [🚫 Anti-Patterns to Avoid](#-anti-patterns-to-avoid)
  - [🔮 Extensibility Options](#-extensibility-options)
  - [📚 References / See Also](#-references--see-also)
    - [Google Mapping](#google-mapping)
    - [WordPress Architecture](#wordpress-architecture)
    - [Decoupled Design](#decoupled-design)
  - [✅ Revision History](#-revision-history)

</details>

---

## 🧩 Problem Statement

A food truck business requires a live map showing **where the truck is parked today**.

Key challenges:

- The **location changes multiple times daily**
- The **client is not a coder**
- The theme is intentionally **decoupled from the WordPress database**
- Editing PHP files is **not acceptable for daily updates**
- Performance and simplicity are critical

---

## 🎯 Constraints and Design Goals

- **No JavaScript** in the resulting document
- **Classic WordPress theme** (non-block, non-FSE)
- **Centralized configuration** via `theme-data.php`
- **No plugins** unless absolutely unavoidable
- **No Google Maps JavaScript API**
- **No API keys or billing**
- **Client must self-manage location visually**
- **Solution must survive theme migration**

---

## ❌ Why Traditional Approaches Fail

- **ACF map fields**
  - Requires WP admin access
  - Database-dependent
  - Overkill for single location

- **Google Maps JS API**
  - Requires API key
  - Requires billing account
  - Adds JavaScript complexity
  - Performance overhead

- **Map plugins**
  - Adds unused features
  - Loads assets site-wide
  - Introduces vendor lock-in

- **Hardcoded coordinates**
  - Fragile
  - Client will break them
  - Requires redeploys

---

## ✅ Recommended Architecture

### 🗺️ Data Source: **Google My Maps**

**Google My Maps** acts as a **visual location editor** for the client.

Advantages:
- Drag-and-drop pin movement
- Public sharing
- No API keys
- No billing
- Familiar Google interface

The map becomes the **single source of truth**.

---

### 🧠 Theme Configuration Model

Location configuration lives in **`theme-data.php`**, maintaining the project’s decoupled design.

```php
'map' => [
    'embed_url' => 'https://www.google.com/maps/d/u/0/embed?mid=XXXXXXXXXXXX',
    'height' => 360,
    'fallback_address' => '123 Main St, Ozark, AL 36360',
],
````

Only **one string** ever changes: `embed_url`.

---

### 🖥️ Rendering Strategy

* Use an **iframe embed**
* Render via PHP helper
* Lazy load by default
* Provide “Get Directions” CTA
* Fail silently if missing

---

## 🛠️ Implementation Guide

### 🔧 Update `theme-data.php`

Add the map configuration under the `business` key.

No database. No admin UI.

---

### 🧩 Map Rendering Helper

Add to `functions.php`:

```php
function ehd_render_map(array $map = []) {
    if (empty($map['embed_url'])) {
        return;
    }

    $height = intval($map['height'] ?? 360);
    $address = urlencode($map['fallback_address'] ?? '');

    echo '<section class="map-section">';
    echo '<div class="map-embed">';
    echo '<iframe src="' . esc_url($map['embed_url']) . '" width="100%" height="' . esc_attr($height) . '" style="border:0;" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>';

    if ($address) {
        echo '<div class="map-actions">';
        echo '<a href="https://www.google.com/maps/dir/?api=1&destination=' . $address . '" target="_blank" rel="noopener">Get Directions</a>';
        echo '</div>';
    }

    echo '</div></section>';
}
```

---

### 🧱 Template Integration

```php
$theme = include get_template_directory() . '/theme-data.php';
ehd_render_map($theme['business']['map']);
```

---

### 🎨 CSS Styling

```css
.map-embed {
  border-radius: 14px;
  overflow: hidden;
  box-shadow: 0 10px 28px rgba(0,0,0,.15);
}
```

---

## 👤 Client Workflow

* Open **Google My Maps**
* Move the pin to today’s location
* Click **Share**
* Ensure public visibility
* Copy embed URL
* Paste into config file
* Save

No WordPress login required.

---

## 🧯 Failure Handling and Fallbacks

* Missing embed URL → map section does not render
* Broken map → “Get Directions” still works
* Offline editing → last known location remains visible

---

## 🧠 Why This Solution Works

* Stateless
* Version-controlled
* Client-proof
* Performance-friendly
* No JavaScript dependency
* No WordPress admin reliance

This is **how you build for mobile businesses without abusing WordPress**.

---

## 🚫 Anti-Patterns to Avoid

* Plugin-heavy mapping solutions
* Database-stored coordinates
* Admin-only content pipelines
* API-key-dependent embeds
* Over-engineering with CPTs

---

## 🔮 Extensibility Options

* AM/PM location rotation
* Multiple pins per day
* Time-based embeds
* Headless reuse via JSON config
* Mobile-only “Open in Maps” CTA

---

## 📚 References / See Also

### Google Mapping

* **Google My Maps**
  [https://www.google.com/mymaps](https://www.google.com/mymaps)
  Visual map editor for non-technical users

* **Google Maps Embed Documentation**
  [https://developers.google.com/maps/documentation/embed](https://developers.google.com/maps/documentation/embed)
  Official embed behavior and parameters

### WordPress Architecture

* **WordPress Theme Developer Handbook**
  [https://developer.wordpress.org/themes/](https://developer.wordpress.org/themes/)
  Canonical guidance for classic themes

* **WordPress Coding Standards**
  [https://developer.wordpress.org/coding-standards/](https://developer.wordpress.org/coding-standards/)

### Decoupled Design

* **Stateless WordPress Themes**
  [https://developer.wordpress.org/rest-api/](https://developer.wordpress.org/rest-api/)
  Concepts applicable to headless and low-DB designs

---

## ✅ Revision History

| Version | Date       | Author           | Changes Made          |
| :------ | :--------- | :--------------- | :-------------------- |
| 1.00    | 2025-12-30 | Eric L. Hepperle | Initial draft created |
| 1.01    | --         | --               | --                    |

---

