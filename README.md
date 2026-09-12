# Digitized documents

Scanned official documents turned into text: OCR, followed by a page-by-page correction pass done by
an AI model reading the page images. The source scans are images with no text layer — you cannot
search them, quote from them, or diff one edition against another. This repository holds the same
documents as Markdown.

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
3. Each page is then read back against its image by a vision-capable AI model (Claude Opus 5), which
   corrects the OCR output. This is the bulk of the work — raw Tesseract output on a 1998 scan is not
   trustworthy, least of all in Cyrillic.
4. The structure of the document is carried into Markdown: articles become headings, numbered
   paragraphs and sub-paragraphs become lists.

Correction rules:

- OCR defects are corrected (`Govemment` → `Government`, a Cyrillic «а» standing in for `(a)`);
- **typos present in the printed edition are preserved** and flagged with an HTML comment next to
  them — the point of the archive is to match the paper, not to improve on it;
- illegible passages are marked `<!-- illegible: ... -->` rather than guessed at;
- running heads and page numbers are dropped; paragraph breaks follow the original.

## How far to trust these texts

No human has verified these transcriptions line by line. What has been done is the AI correction pass
described above, plus mechanical checks on the assembled result: article counts and numbering,
headings matched across the language versions, and every figure in the document — rates, thresholds,
periods, dates — re-read against the scan individually.

That makes this a careful working copy, not a certified transcript. If something turns on the exact
wording — and in a tax treaty it usually does — check the scan, which is linked from every document
page. Corrections are welcome: open an issue quoting the page number of the printed edition.

## Source and rights

Official documents — statutes, international treaties and similar acts — are not subject to
copyright, and the underlying texts here are already in the public domain. No rights are claimed over
the digitization itself either: this repository is released under [CC0 1.0](LICENSE).

The provenance of every scan is recorded on the document's own page.
