# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repository contains a theological study guide: "Jesus in the Book of Leviticus — The Gospel in Symbols." It consists of source course materials (.docx files) and a professionally typeset LaTeX handbook.

## Build Commands

**Compile the PDF:**
```bash
tectonic jesus_in_leviticus_handbook.tex
```

Tectonic handles all LaTeX passes automatically (including XeTeX for Hebrew support).

**Extract content from .docx files (if needed):**
```bash
pandoc "Session X.docx" -t plain --wrap=none
```

## Document Architecture

### LaTeX Structure (`jesus_in_leviticus_handbook.tex`)

**Package loading order matters:** Due to the `bidi` package (loaded by `polyglossia` for Hebrew), all other packages must be loaded BEFORE `polyglossia`. This includes `xcolor`, `hyperref`, `graphicx`, etc.

**Key custom environments and commands:**
- `\begin{scripture}...\end{scripture}` — Block quotes for Bible verses
- `\scriptureref{Reference}` — Right-aligned scripture attribution in small caps
- `\heb{Hebrew text}` — Inline Hebrew text using Times New Roman
- `\sectionbreak` — Decorative diamond separator between sections
- `\lettrine[lines=2]{\color{chaptercolor}X}{rest}` — Drop caps for chapter openings

**Color palette:**
- `chaptercolor` (RGB 139, 69, 19) — Saddle brown for chapter titles
- `sectioncolor` (RGB 102, 51, 0) — Dark brown for sections
- `quotecolor` (RGB 70, 70, 70) — Dark gray for scripture text

### Content Structure (8 Chapters)

1. The Revelation of Christ in Leviticus (foundational theology)
2. The Offerings (Lev. 1–7)
3. The Priesthood (Lev. 8–10)
4. The Day of Atonement (Lev. 16)
5. Laws of Cleansing and Holiness (Lev. 11–15, 17–20)
6. The Feasts of the Lord (Lev. 23)
7. Sabbath and Jubilee (Lev. 25–26)
8. Dedication and Vows (Lev. 27)

## Style Conventions

**Bible references:** Use abbreviated format with backslash-space: `Lev.\ 1:1`, `John\ 5:39`, `Heb.\ 9:12`

**Chapter openings:** Each chapter has:
1. An epigraph (centered scripture quote)
2. A drop cap on the first paragraph using `\lettrine`

**Tables:** Use `booktabs` rules (`\toprule`, `\midrule`, `\bottomrule`). For wide tables, use `tabularx` with `\textwidth`.

**Hebrew terms:** Format as `\heb{Hebrew} (\textit{transliteration}, meaning)`
