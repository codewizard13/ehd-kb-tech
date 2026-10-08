<!-- 🔗 Custom Stylesheet -->
<link rel="stylesheet" href="../../_css/main.css">

<!-- 🖼️ Site Logo -->
![Site Logo](/_pix/logos/logo-ehw-kb.svg){height=32}

<!-- 📝 Title -->
# HOW-TO: 📘 CSS Gotcha: Why Inline Icons Refuse to Vertically Center (And How `line-height` Fixes It)

> 🔗 **Alt Titles:** 
> - *CSS Baseline Alignment: Fixing Inline Icon Spacing in Markdown*
> - *When `vertical-align` Fails: Solving Inline Icon Spacing by Resetting `line-height`*
> - *The Inline Icon Trap: Baseline Alignment, Markdown, and the Hidden Role of `line-height`*

**Version:** 1.1

> Optimized for: VSCode on Windows 11 + Git Bash (SSH)

<!-- 🧭 Navigation -->
### 🏚️ Home | 📁 HOW-TO

<!-- 👤 Metadata -->
| **Author**:        | Eric L. Hepperle |
| ------------------ | ---------------- |
| **Date Created**:  | 2025-12-23       |
| **Date Updated**:  | 2025-12-23       |
| **AI Assistance**: | ChatGPT |

---


<!-- SECTION: Tags -->
<section id="sec-tags">


## Tags:


- CSS
- Markdown
- Inline elements
- Baseline alignment
- Icons



</section>


---


<!-- 🔍 Content Section Heading -->

## 📌 Overview

When rendering inline icons (e.g., a folder icon) next to text in Markdown that supports inline HTML/CSS, you may observe **unwanted space below the icon**, even though it visually appears on the same line.

This happens because:
- Inline or `inline-block` elements align to the **text baseline** by default, not the visual center.
- Browsers reserve space beneath inline elements for text descenders like `g`, `y`, etc.
- Markdown renderers typically apply a non-zero default `line-height`, making the gap more noticeable.

This HOW-TO explains why conventional approaches like `vertical-align: middle` appear ineffective, and it provides **reliable, JavaScript-free CSS solutions** for vertically centering icons beside text in Markdown and static HTML.

---

## 🧭 Table of Contents

<details>
<summary><strong>Click to expand / collapse</strong></summary>

- Overview
- Problem Description
- Root Cause Analysis
- Use Case: VSCode + Markdown Preview on Windows 11
- Why Common Fixes Fail
- Recommended Solutions
  - Solution 1: Zero the Line Height
  - Solution 2: Use Inline Flexbox
  - Solution 3: Target the Image Element
- Renderer Notes
- Best Practices
- References / See Also

</details>

---

## ❗ Problem Description

When using a span or inline HTML block for an icon inside a Markdown document, e.g.:

```html
<span class="folder-icon">
  <img src="folder.png" alt="Folder">
</span>
````

A visible gap appears beneath the icon even though it is on the same line. Attempts to adjust padding, margin, or simple vertical alignment often do not eliminate the gap.

---

## 🔬 Root Cause Analysis

### Inline Formatting Context

CSS inline formatting places boxes horizontally and aligns them to a line box that is sized based on `line-height`. Replaced inline elements like images also generate a baseline context. ([MDN Web Docs][1])

### Baseline vs Visual Center

By default, `vertical-align` is set to `baseline`, meaning elements align based on the text baseline, not visual center. This means smaller icons appear “too high” and leave visible space below them. ([MDN Web Docs][2])

### Markdown Line-Height Interaction

Markdown renderers often use `line-height: normal` or values around `1.4-1.6`, increasing the line box height and highlighting baseline spacing. Setting `line-height: 0` removes the space reserved for descenders.

---

## 🛠️ Use Case: VSCode + Markdown Preview on Windows 11

In **Visual Studio Code’s built-in Markdown Preview** on **Windows 11**, the following was observed:

* Without custom CSS, folder icon images had an unwanted space underneath.
* Applying `line-height: 0` to the wrapping inline-block eliminated the baseline gap.
* This validated that the root cause was **baseline alignment + nonzero line-height**, not incorrect padding/margins or Markdown rendering quirks.

This behavior was confirmed repeatedly while testing during 2025 in VSCode’s preview and matches community discussions about inline icon alignment. ([Reddit][3])

---

## 🚫 Why Common Fixes Fail

* `vertical-align: middle` aligns to text baseline plus half x-height, which doesn’t guarantee true visual centering. ([CSS-Tricks][4])
* `position: relative; top: ...` only visually shifts the image without changing the underlying line box.
* Masoning vertical positioning with CSS offsets becomes brittle across font changes and Markdown renderers.

---

## ✅ Recommended Solutions

All of these methods are valid as of **December 2025**, require **no JavaScript**, and are compatible across modern browsers/renderers.

### ✔️ Solution 1: Zero the Line Height (Most Reliable)

```css
.folder-icon {
  display: inline-block;
  width: 24px;
  line-height: 0;
  vertical-align: middle;
}
```

This works because eliminating the line height prevents the baseline from reserving additional space.

---

### ✔️ Solution 2: Use Inline Flexbox

```css
.folder-icon {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 24px;
  vertical-align: middle;
}
```

`inline-flex` avoids the baseline alignment entirely while remaining inline.

---

### ✔️ Solution 3: Target the Image Element Directly

```css
.folder-icon img {
  display: block;
}
```

By default `<img>` is inline and participates in baseline alignment; setting it to `display: block` removes the gap.

---

## 🧩 Renderer Notes

* **GitHub Markdown**: Often uses 1.4–1.6 line height; solutions above work well.
* **Obsidian**: Themes may override defaults; inline-flex is robust.
* **Static Site Generators**: Ensure custom CSS is enabled and `line-height: 0` applies to icon containers.

---

## 🧠 Best Practices

* Treat icons as layout elements, not text.
* Avoid relying solely on `vertical-align` keywords for final visual centering.
* Test with real Markdown renderers for the target platform.
* Use semantic CSS class names for icons (e.g., `.folder-icon`).

---

## 📚 References / See Also

### Official Docs

* MDN Web Docs – [`vertical-align` CSS property](https://developer.mozilla.org/en-US/docs/Web/CSS/vertical-align) – explains alignment relative to baseline and line box. ([MDN Web Docs][2])
* MDN Web Docs – [Inline formatting context](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_inline_layout/Inline_formatting_context) – how inline boxes are laid out. ([MDN Web Docs][1])
* CSS-Tricks – *What is Vertical Align?* – classic explanation of how baseline and vertical align interact. ([CSS-Tricks][4])

### Community Posts / Blog Articles (Relevant to the Issue)

* **Vertical Alignment Bug with Icons** – RIMdev blog discussing line-height impacts on icon alignment and the need to set explicitly. ([rimdev.io][5])
* **Stack Overflow Discussion: Inline SVG & line-height** – community-described issue of SVG/inline icons affecting line height and alignment. ([Stack Overflow][6])
* **Reddit Discussion on Centering Inline Icons/Images** – real-world users struggle with icon vertical alignment next to text; includes solutions like `inline-flex`. ([Reddit][3])

---

## ✅ Revision History

| Version | Date       | Author           | Changes Made                             |
| ------- | ---------- | ---------------- | ---------------------------------------- |
| 1.00    | 2025-12-22 | Eric L. Hepperle | Initial draft created                    |
| 1.01    | 2025-12-23 | Eric L. Hepperle | Added Use Case & blog references section |

---


[1]: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_inline_layout/Inline_formatting_context?utm_source=chatgpt.com "Inline formatting context - CSS | MDN"
[2]: https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/vertical-align?utm_source=chatgpt.com "vertical-align - CSS | MDN"
[3]: https://www.reddit.com//r/css/comments/1gg7lqs/centering_inline_iconsimages_with_a_line_of_text/?utm_source=chatgpt.com "Centering Inline Icons/Images with a line of text"
[4]: https://css-tricks.com/what-is-vertical-align/?utm_source=chatgpt.com "What is Vertical Align? - CSS-Tricks"
[5]: https://rimdev.io/vertical-alignment-bug-with-icons?utm_source=chatgpt.com "Vertical Alignment Bug with Icons | RIMdev Blog"
[6]: https://stackoverflow.com/questions/69916171/css-inline-svg-interferes-with-line-height?utm_source=chatgpt.com "html - CSS - inline SVG interferes with line-height? - Stack Overflow"
