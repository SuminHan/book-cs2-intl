# book-cs2-intl

KSA Computer Science 2 (CS2), International track — supplementary notes. mdBook.

**Live:** https://smhanlab.com/book-cs2-intl/
(served automatically under the personal-account custom domain — path must
match the repo name exactly, including case)

Not a replacement for class. Underlying course content has mixed authorship
(includes material originated by Sanghyun Yoon); this project only edits/organizes.
Instructor-only material (diagnostic pretests, answer keys) is intentionally excluded.

Korean track (국내반) lives separately at [book-cs2](https://github.com/SuminHan/book-cs2).

## Structure

```
book.toml       — mdBook config (build-dir = "docs", served by GitHub Pages)
src/
  SUMMARY.md    — table of contents
  intl/         — Week00-15
  general/      — track-agnostic CS concepts (e.g. bit-width, w/ Manim video)
docs/           — mdbook build output. Committed (Pages serves it directly).
```

## Build locally

```bash
mdbook build       # generates docs/
mdbook serve        # local preview, http://localhost:3000
```

## Deploy

GitHub Pages: **Settings → Pages → Deploy from a branch → `main` / `/docs`**.
Commit `docs/` and push to `main`. No GitHub Action needed.

## ⚠️ Note

- This repo and the personal homepage repo (`suminhan/suminhan.github.io`,
  a real live Hugo blog) are **completely separate**. Never push to the
  personal homepage repo.
- To add a chapter: edit `src/intl/*.md` only → `mdbook build` to regenerate
  `docs/` → commit `docs/` too. Don't hand-edit `docs/` (next build overwrites it).
