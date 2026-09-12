---
title: Digitized documents
---

Scanned official documents turned into text: OCR followed by page-by-page proofreading against the
original. These texts can be searched, quoted and diffed line by line — unlike the source scans,
which carry no text layer at all.

## Documents

| Document | Date | Languages | Status |
|---|---|---|---|
| [Cyprus–Russia agreement on the avoidance of double taxation](cyprus-russia-dta-1998/) | 5 December 1998 | English, Russian | fully proofread |

## How this is done

Every document follows the same route: pages are rendered from the PDF to 300 dpi images, put through
Tesseract with the appropriate language model, and then each page is proofread by hand against its
image. Anything OCR mangles gets fixed: substituted letters, run-together paragraphs, Latin and
Cyrillic sub-paragraph markers swapped for one another.

Typos belonging to the printed edition itself are **kept**, flagged with an HTML comment in the text.
The point of the archive is for the text to match the paper, not to improve on it.

## Rights

Official documents — statutes, international treaties and similar acts — are not subject to
copyright. No rights are claimed over the digitization either: this archive is released under
[CC0 1.0](LICENSE), that is, dedicated to the public domain.
