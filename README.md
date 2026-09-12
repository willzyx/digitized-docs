# Digitized documents

Scanned official documents turned into text: OCR followed by page-by-page proofreading against the
original. The source scans are images with no text layer — you cannot search them, quote from them,
or diff one edition against another. This repository holds the same documents as Markdown.

Easier to read on the site: **https://willzyx.github.io/digitized-docs/**

## Contents

| Document | Date | Languages |
|---|---|---|
| [Cyprus–Russia agreement on the avoidance of double taxation](cyprus-russia-dta-1998/) | 5 December 1998 | English, Russian |

## Layout

```
<document-folder>/
├─ index.md   what the document is, where the scan came from, how it was digitized
├─ en.md      text in one of the original languages
├─ ru.md      text in the other
└─ source/    the original scan
```

A new document is a new folder of the same shape, plus a row in the tables in `index.md` and
`README.md`.

## How a document is digitized

1. Pages are rendered from the PDF to 300 dpi PNG: `pdftoppm -r 300 -gray -png file.pdf pages/p`
2. Each page goes through Tesseract with the appropriate language model:
   `tesseract pages/p-NN.png ocr/p-NN -l rus --psm 6`
3. Each page is then proofread by hand against its image. This is the bulk of the work — without it
   the output is not trustworthy.
4. The structure of the document is carried into Markdown: articles become headings, numbered
   paragraphs and sub-paragraphs become lists.

Proofreading rules:

- OCR defects are corrected (`Govemment` → `Government`, a Cyrillic «а» standing in for `(a)`);
- **typos present in the printed edition are preserved** and flagged with an HTML comment next to
  them — the point of the archive is to match the paper, not to improve on it;
- illegible passages are marked `<!-- illegible: ... -->` rather than guessed at;
- running heads and page numbers are dropped; paragraph breaks follow the original.

## Source and rights

Official documents — statutes, international treaties and similar acts — are not subject to
copyright, and the underlying texts here are already in the public domain. No rights are claimed over
the digitization itself either: this repository is released under [CC0 1.0](LICENSE).

The provenance of every scan is recorded on the document's own page. If you spot an OCR error, please
open an issue quoting the page number of the printed edition — that is the most useful contribution
you can make.
