<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# move toc to before tags sec. also, expand details about usiage in calc and excel

```markdown
<!-- 🔗 Custom Stylesheet -->
<link rel="stylesheet" href="../../_css/main.css">

<!-- 🖼️ Site Logo -->
![Site Logo](placeholder-logo.png){height=32}

<!-- 📝 Title -->
# HOW-TO: 📘 Dollar Sign ($): The Great Gotcha

**Version:** 1.0

> Optimized for: VSCode on Windows 11 + Git Bash (SSH)

<!-- 🧭 Navigation -->
### [🏚️ Home](../README.md) | [📁 [HOW-TO](index.md)

<!-- 👤 Metadata -->
| **Author**:        | Eric L. Hepperle |
| ------------------ | ---------------- |
| **Date Created**:  | 2026-01-16       |
| **Date Updated**:  | --               |
| **AI Assistant**:  | Perplexity AI    |

---

<details>
<summary>📋 Table of Contents (Click to Expand)</summary>

- [📌 Overview](#📌-overview)
- [💻 Calc/Excel Usage](#💻-calcexcel-usage)
- [📚 References / See Also](#📚-references--see-also)
- [✅ Revision History](#✅-revision-history)

</details>

---

<!-- SECTION: Tags for short related (1-3 word phrase per tag) concepts (long titled articles belong in the References / See Also section above) -->
<section id="sec-tags">

## Tags:
- Absolute Reference
- Excel Gotcha
- LibreOffice Calc
- Spreadsheet Formulas
- Dollar Sign

</section>

---

## 📌 Overview

The dollar sign (`$`) creates massive confusion across programming and spreadsheets because it means **completely opposite things** in each world:

- **Programming**: `$` = *variable* (dynamic value)  
- **Excel/LibreOffice Calc**: `$` = *locked reference* (absolute/fixed position)  

This "Gotcha" trips up developers learning spreadsheets (and vice versa) constantly. A coder sees `$B$3` and thinks "variable B3" when it's actually "NEVER MOVE from cell B3 no matter where you copy this formula."

**Core Mappings:**
| Context | `$` Meaning | Example | Behavior |
|---------|-------------|---------|----------|
| PHP/Bash/Perl | Variable marker | `$version` | Contains dynamic value |
| Excel/Calc | Absolute lock | `$B$3` | Fixed cell reference |
| Regex | End anchor | `\.csv$` | Match at string end |
| Everything | Extension filter | `ext:xlsx` | File type search |

---

## 💻 Calc/Excel Usage

**Four Reference Types:**
```text
$B$3  → Column B + Row 3 BOTH locked (Absolute)
B$3   → Column floats, Row 3 locked (Mixed)  
$B3   → Column B locked, Row floats (Mixed)
B3    → Both float (Relative)
```

**Practical Examples:**


| Formula in C4 | Copied to D5 | Result |
| :-- | :-- | :-- |
| `=A1` | `=B2` | Both column+row shift |
| `=$A1` | `=B1` | Column shifts, row locked |
| `=A$1` | `=A2` | Row shifts, column locked |
| `=$A$1` | `=$A$1` | Both locked |

**Sheet References:**

```text
='Version Log'.B3      → Sheet name + relative cell
='Version Log'.$B$3    → Sheet name + absolute cell
=$'Version Log'.$B$3   → Locked sheet + absolute cell
```

**F4 Key Magic (Excel/Calc):** Press **F4** while editing formula to cycle: `B3` → `$B$3` → `B$3` → `$B3` → `B3`

**Copying Behavior Test:**

1. Put `=YEAR(TODAY())` in A1
2. Copy to B1 → Still `=YEAR(TODAY())`
3. Put `=$A$1` in C1 → Always shows A1 value when copied anywhere

---

## 📚 References / See Also

### Spreadsheet Tools

- [LibreOffice Calc Documentation](https://documentation.libreoffice.org/en/english-documentation/calc/)
- [Microsoft Excel Help: Cell References](https://support.microsoft.com/en-us/office/cell-references-in-excel-4f7d9a79-55e8-4d19-b9b1-67e0c95b82c3)
- [VoidTools Everything Search Syntax](https://www.voidtools.com/support/everything/searching/)


### Programming Languages

- [PHP Variables](https://www.php.net/manual/en/language.variables.php)
- [Bash Variables](https://www.gnu.org/software/bash/manual/bash.html#Shell-Variables)

---

## ✅ Revision History

| Version | Date | Author | Changes Made |
| :-- | :-- | :-- | :-- |
| 1.00 | 2026-01-16 | Eric L. Hepperle | Initial draft created |
| 1.01 | -- | -- | -- |

```
```

