# Prompt: KB Wiki Article (2025-12-09)

```md
Create a wiki-style kb in the given template format with the given source content with these requirements:

09/26/26 Requirements:

- CONTENT: If 'CONTEXT' section exists below, use it. Otherwise Use the full previous chat as the context.
- Ensure Title is title case, never snake case
- Metadata Table: Dates should always go in the second column
- Ensure everything is validated as accurate against today's date
- Do not use any JavaScript in the resulting markdown document -- only markdown, inline CSS, and HTML are allowed
- Create a working TOC that is collapsible and doesn't use any JavaScript (is there a native HTML tag as of today that does this?)
- Indent the TOC appropriately
- All bullets must be hyphen bullets only
- Reorganize content for better logical flow
- Expand the Overview/intro section
- Wherever an image is required by missing use placeholder instead
- Create a robust references section categorized by topic
- Ensure every plugin or website name is hyperlinked


Template format:


<!-- 🔗 Custom Stylesheet -->
<link rel="stylesheet" href="../../_css/main.css">


<!-- 🖼️ Site Logo -->
!Site Logo{height=32}


<!-- 📝 Title -->
# HOW-TO: 📘 TOPIC: Title_Case_Title


**Version:** 1.0


> Optimized for: VSCode on Windows 11 + Git Bash (SSH)


<!-- 🧭 Navigation -->
### [🏚️ Home](../README.md) | [📁 [CATEGORY <SOP, HOW-TO, etc.](index.md)


<!-- 👤 Metadata -->
| **Author**:        | Eric L. Hepperle |
| ------------------ | ---------------- |
| **Date Created**:  | YYYY-MM-DD       |
| **Date Updated**:  | --               |
| **AI Assistant**: | --               |


---


<!-- SECTION: Tags for short related (1-3 word phrase per tag) concepts (long titled articles belong in the References / See Also section above) -->
<section id="sec-tags">


## Tags:


- Topic2
- Topic2
- Topic3



</section>


---


<!-- 🔍 Content Section Heading -->


## 📌 Overview


// ADD_CONTENT


---


<!-- 📚 References (Optional) -->
## 📚 References / See Also



- Placeholder 1
- Placeholder 2



---


## ✅ Revision History



| Version | Date       | Author           | Changes Made          |
| ------- | ---------- | ---------------- | --------------------- |
| 1.00    | YYYY-MM-DD | Eric L. Hepperle | Initial draft created |
| 1.01    | --         | --               | --                    |
etc...

---

CONTENT:

```