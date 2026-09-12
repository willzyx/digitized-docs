---
title: Digitized documents
---

Scanned official documents turned into text: OCR, followed by a page-by-page correction pass done by
an AI model reading the page images. These texts can be searched, quoted and diffed line by line —
unlike the source scans, which carry no text layer at all.

## Documents

| Document | Date | Languages | Status |
|---|---|---|---|
| [Cyprus–Russia agreement on the avoidance of double taxation](cyprus-russia-dta-1998/) | 5 December 1998 | English, Russian | fully proofread |

## How this is done

Every document follows the same route: pages are rendered from the PDF to 300 dpi images, put through
Tesseract with the appropriate language model, and then each page is read back against its image by a
vision-capable AI model (Claude Opus 5), which corrects what OCR mangled: substituted letters,
run-together paragraphs, Latin and Cyrillic sub-paragraph markers swapped for one another.

No human has checked these texts line by line, so treat them as a careful working copy rather than a
certified transcript. Every document page links to its scan — verify anything that turns on exact
wording, and open an issue if you find an error.

Typos belonging to the printed edition itself are **kept**, flagged with an HTML comment in the text.
The point of the archive is for the text to match the paper, not to improve on it.

## Rights

Official documents — statutes, international treaties and similar acts — are not subject to
copyright. No rights are claimed over the digitization either: this archive is released under
[CC0 1.0](https://github.com/willzyx/digitized-docs/blob/main/LICENSE), that is, dedicated to the public domain.
