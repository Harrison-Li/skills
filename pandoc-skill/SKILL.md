---
name: pandoc
description: >
  Convert documents between formats using pandoc. Supports HTML, Markdown, DOCX, PDF, EPUB, LaTeX,
  ODT, RST, Org, MediaWiki, JIRA, CSV, Jupyter notebooks, and many more — any direction pandoc supports.
  Use this skill whenever the user wants to convert, transform, or export a document from one format to
  another, even if they don't mention pandoc explicitly. Triggers include: "convert this to PDF",
  "make a Word doc from this markdown", "export as EPUB", "turn this HTML into a PDF", "transform",
  "generate PDF", "render to", or any request involving document format conversion. Also use when the
  user wants to apply custom styling, add a table of contents, use a template, or set metadata during
  conversion.
metadata:
  version: 1.0.2
  author: Oliver Herklotz (oliver-hrkltz)
  homepage: https://github.com/hrkltz/pandoc-skill
compatibility: >
  Requires: pandoc (https://pandoc.org).
  Optional PDF engines: xelatex (texlive-xetex, recommended for Unicode/fonts),
  lualatex (texlive-luatex, complex typography), tectonic (self-contained TeX workflow),
  pdflatex (texlive-latex-base, fastest for ASCII), weasyprint (CSS Paged Media, Python-based),
  wkhtmltopdf (WebKit-based HTML/CSS rendering), prince (commercial HTML/CSS renderer).
---

# Pandoc Document Converter

Convert documents between any formats pandoc supports, with full control over styling, templates,
table of contents, metadata, and PDF engine selection.

## Common Conversion Patterns

### HTML → PDF
```bash
pandoc input.html -o output.pdf --pdf-engine=weasyprint -s
```
If the HTML uses external CSS, include it:
```bash
pandoc input.html -o output.pdf --pdf-engine=weasyprint -s --css=style.css
```

### Markdown → PDF
```bash
pandoc input.md -o output.pdf --pdf-engine=xelatex -s --toc --toc-depth=3
```

### Markdown → DOCX
```bash
pandoc input.md -o output.docx -s
```
To use a reference (template) document for styling:
```bash
pandoc input.md -o output.docx --reference-doc=template.docx
```

### Markdown → HTML
```bash
pandoc input.md -o output.html -s --css=style.css --toc
```

### DOCX → Markdown
```bash
pandoc input.docx -o output.md --extract-media=./media
```

### Markdown → EPUB
```bash
pandoc input.md -o output.epub -s --toc --epub-cover-image=cover.jpg
```

### LaTeX → PDF
```bash
pandoc input.tex -o output.pdf --pdf-engine=xelatex
```

### CSV → HTML table
```bash
pandoc input.csv -o output.html -s
```

## Advanced Features

### Table of Contents
Add `--toc` and optionally `--toc-depth=N` (default 3):
```bash
pandoc input.md -o output.pdf --pdf-engine=xelatex -s --toc --toc-depth=2
```

### Metadata
Set title, author, date via YAML frontmatter in the source file or via `-M`:
```bash
pandoc input.md -o output.pdf --pdf-engine=xelatex -s \
  -M title="My Report" -M author="Jane Doe" -M date="2026-03-15"
```

### Filters and Lua filters
Pandoc supports filters that transform the AST. Lua filters are self-contained:
```bash
pandoc input.md -o output.pdf --lua-filter=my-filter.lua
```

### Multiple input files
Pandoc concatenates multiple inputs:
```bash
pandoc chapter1.md chapter2.md chapter3.md -o book.pdf --pdf-engine=xelatex -s --toc
```

### Extracting media from DOCX/EPUB
```bash
pandoc input.docx -o output.md --extract-media=./media
```

## Troubleshooting

| Problem | Likely cause | Fix |
|---|---|---|
| PDF has missing characters | Font doesn't support the glyphs | Use `--pdf-engine=xelatex` with `-V mainfont="DejaVu Serif"` |
| PDF conversion fails | No compatible PDF engine installed | Check `which xelatex lualatex tectonic pdflatex weasyprint wkhtmltopdf prince` and install one that matches your output needs |
| DOCX looks unstyled | No reference doc | Create a styled DOCX template and pass `--reference-doc` |
| HTML images missing | Relative paths broken | Use `--self-contained` to embed images as base64 |
| CSS has no effect on PDF | LaTeX PDF engine selected | Use `--pdf-engine=weasyprint`, `--pdf-engine=wkhtmltopdf`, or `--pdf-engine=prince` |
| Table of contents empty | No headings in source | Ensure source uses `#` headings (Markdown) or `<h1>`–`<h6>` (HTML) |

## Format Reference

For a full list of supported input and output formats, see `references/formats.md`.
