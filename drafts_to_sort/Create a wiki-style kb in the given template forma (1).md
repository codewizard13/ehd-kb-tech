<!-- 🔗 Custom Stylesheet -->
<link rel="stylesheet" href="../../_css/main.css">

<!-- 🖼️ Site Logo -->
![Site Logo](height=32)

<!-- 📝 Title -->
# HOW-TO: 📘 Managing Boss Timeline Expectations

**Version:** 1.0

> Optimized for: VSCode on Windows 11 + Git Bash (SSH)

<!-- 🧭 Navigation -->
### [🏚️ Home](../README.md) | [📁 [HOW-TO](index.md)

<!-- 👤 Metadata -->
| **Author**:        | Eric L. Hepperle |
| ------------------ | ---------------- |
| **Date Created**:  | 2026-04-16       |
| **Date Updated**:  | --               |
| **AI Assistant**:  | Perplexity       |

---

<details open>

<summary>Table of Contents</summary>

- [Overview](#📌-overview)
- [Core Strategy](#🎯-core-strategy)
- [Escalation Ladder](#🚨-ghosting-escalation-ladder)

</details>


<!-- SECTION: Tags for short related (1-3 word phrase per tag) concepts (long titled articles belong in the References / See Also section above) -->
<section id="sec-tags">

## Tags:
- Estimate Management
- Scope Negotiation
- Boss Communication
- WordPress Development
- Timeline Expectations
- Mental Model Gap

</section>

---

## 📌 Overview

When managers with limited technical experience (e.g., [Dreamweaver](https://en.wikipedia.org/wiki/Adobe_Dreamweaver) era static site skills) request features for complex dynamic applications like [WordPress](https://wordpress.org/) directory-style many-to-many web apps, they often underestimate implementation complexity by orders of magnitude.

**Core Problem**: Boss sends vague request expecting 2-day delivery → Developer provides detailed breakdown showing 2.5-day realistic timeline → Radio silence → Angry "why isn't it done?" email days later.

**Solution Framework**: 
- Respond immediately with **binary scope choices** tied to boss's implied timeline
- Force decision with auto-deadlines ("confirm by EOD")
- Document assumption if ghosted ("assuming MVP")
- Deliver partial value first to build trust

This KB provides exact message templates that short-circuit the expectation whack-a-mole while maintaining professionalism and covering your back with paper trails.

---

## 🎯 Core Strategy

**Lead with boss's timeline reference** to show alignment, then present MVP vs Full scope options. Never send detailed breakdowns without forcing a scope decision first.

**Revised Template (Immediate Reply to Vague Ask):**

```

Hey [Boss], got your note on the [directory feature]. To hit your implied 2-day timeline, we'd need MVP (display-only, no new DB logic).

**Quick scope options:**

- **MVP** (view-only): 4-6 hours → Done EOD tomorrow
- **Full** (relationships + testing): 1.5-2.5 days → Done COB Thursday

Which scope works? Confirming by EOD today so I can start.

```

---

## 🛠️ Breakdown Template (Detailed Version)

Use only *after* scope approval:

```

**Quick breakdown:**

- **Core implementation** (DB relationships + templates): 4-6 hours
- **Edge cases \& testing** (multi-user conflicts, mobile): 4-8 hours
- **Deployment \& QA** (staging + feedback): 2-4 hours

**Total: 1.5-2.5 days** assuming no [custom [WordPress](https://wordpress.org/) plugin] surprises.

```

---

## 🚨 Ghosting Escalation Ladder

When boss ignores your scope request:

1. **Hour 4**: "Assuming MVP scope unless I hear otherwise—starting now."
2. **Day 1**: "On track with MVP. Ping if you want full scope."
3. **Day 2.5**: "MVP delivered. Full scope ready if approved now."

---

## 💡 Why This Works

- **Cognitive ease**: Binary choice (MVP/Full) vs complex breakdown
- **Timeline anchor**: References boss's "2 days" expectation explicitly  
- **Paper trail**: Forward ignored thread when questioned later
- **Value first**: MVP delivery builds trust even if ghosted
- **Control illusion**: Boss feels they chose the scope

---

## 📚 References / See Also

### Communication Patterns
- [Under-Promise Over-Deliver Anti-Pattern](https://example.com/estimates)
- [Scope Creep Prevention](https://example.com/scope-creep)

### WordPress Development
- [WordPress Plugin Directory](https://wordpress.org/plugins/)
- [Advanced Custom Fields](https://www.advancedcustomfields.com/)
- [WP Query Documentation](https://developer.wordpress.org/reference/classes/wp_query/)

### Management Psychology
- [Mental Model Mismatches](https://example.com/mental-models)
- [Decision Forcing Techniques](https://example.com/decision-forcing)

---

## ✅ Revision History

| Version | Date       | Author           | Changes Made             |
|---------|------------|------------------|--------------------------|
| 1.00    | 2026-04-16 | Eric L. Hepperle | Initial draft created    |
| 1.01    | --         | --               | --                       |


