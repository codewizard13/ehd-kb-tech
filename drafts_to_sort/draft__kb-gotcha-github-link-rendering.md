<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# I tried the latest draft and that doesn't work in github either. I'm in the edit preview window -- perhaps links don't work in preview, only after actual commit? [https://github.com/codewizard13/ehd-kb-ministry/edit/master/people/index.md\#l-old-testament](https://github.com/codewizard13/ehd-kb-ministry/edit/master/people/index.md#l-old-testament)

Exactly — you’ve nailed it.
What you’re seeing isn’t a formatting issue at all — it’s **a GitHub UI limitation**.

Here’s what’s happening:

***

### 🧩 Why the links don’t work in the edit preview

When you view a file in **GitHub’s `/edit/` mode**, such as:

```
https://github.com/<user>/<repo>/edit/master/people/index.md
```

GitHub shows a **live Markdown editor preview**, but that preview is rendered *inside a limited iframe sandbox* (their internal editor component, not the regular markdown renderer).

In that environment:

- Internal anchors (like `#l-old-testament`) **don’t trigger jumps**,
- Relative links (`../README.md`) often **don’t open**,
- And some Markdown features (like tables of contents or callouts) are **disabled**.

That’s because the Edit Preview is designed to show content visually, not to support full navigation or clicks. The links become active **only** when you view the committed file under its normal viewer URL — i.e.:

```
https://github.com/<user>/<repo>/blob/master/people/index.md
```

Once the file lives under `/blob/` and not `/edit/`, GitHub’s Markdown engine builds the proper anchor map, and `[L](#l-old-testament)` jumps will work perfectly.

***

### ✅ Quick test to confirm

1. Commit or save your file.
2. Visit it at the `blob` URL:

```
https://github.com/codewizard13/ehd-kb-ministry/blob/master/people/index.md
```

3. Click a link such as [L](#l-old-testament) directly inside the rendered view.

You’ll see that the jump now works instantly.

***

### 🔍 Summary

| Mode | URL pattern | Anchor links work? |
| :-- | :-- | :-- |
| Edit preview | `/edit/...` | ❌ No |
| File view | `/blob/...` | ✅ Yes |
| VS Code preview | `vscode://...` | ✅ Yes (locally) |


***

So your file’s Markdown is already correct — GitHub just disables those jumps in the editor stage.

```
Would you like me to show a one‑line HTML fallback trick (like `<a name="a-old-testament"></a>`) that allows jumps *even inside* the Edit Preview, as a developer convenience?
```

