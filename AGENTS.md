# Book Wiki Instructions

## Purpose

This project turns books in PDF or EPUB format into a concise, linked Markdown wiki of concepts and definitions. The source book is authoritative. Accuracy and traceability matter more than completeness.

## Structure

- `sources/`: original PDF/EPUB files. Treat these as read-only; never modify or replace them.
- `schema/template.md`: required format for every concept definition summarized from a book. Treat it as a formatting template; its example is illustrative, not source material or an instruction to add that example to the wiki.
- `wiki/index.md`: short catalog of books and chapter files.
- `wiki/<Book title>/`: one directory per processed book, named with a clear form of its title.
- `wiki/<Book title>/Chapter <number>. <Chapter title>.md`: chapter summaries and all definitions from that chapter, together in one Markdown file.
- `wiki/log.md`: append-only record of ingests and wiki maintenance.

Use relative Markdown links. Prefer extending an existing page over creating a duplicate. Keep the structure simple; create extra folders or page types only when the material calls for them.

## Evidence and accuracy

- Never invent, assume, or fill gaps in concepts, definitions, examples, quotations, page numbers, or bibliographic details.
- Read the relevant source passage before writing a claim. Cite the exact page number or EPUB location when available. For PDFs, use the page number printed on the page, not the PDF viewer or file page number. For each definition, cite only the first printed page where that definition appears. Keep the book identified by the chapter file and index; do not repeat its title in each definition citation. If location data is unavailable, say so; never guess.
- Preserve the author's meaning and scope. Keep the author's claims distinct from your own connective explanation. Label any interpretation as an interpretation and include its evidence; omit it if uncertain.
- If text extraction is garbled, a passage is ambiguous, or a claim cannot be verified, mark it as uncertain or leave it out. Do not silently repair source text.
- For disagreements within or between books, record each position with its own citation. Do not force a reconciliation.
- When recording a definition, copy the author's exact defining sentence or passage from the source. Do not paraphrase, condense, polish, or correct the source wording. Do not add quotation marks or a Markdown blockquote marker to the copied prose. If the book does not explicitly define a term, omit it or label that limitation instead of inventing a definition. Wrap inline mathematical notation in single-dollar LaTeX delimiters and display formulas in double-dollar delimiters. Transcribe formulas into LaTeX only when the source provides them, preserving their notation and meaning.
- Do not use web knowledge to silently supplement a book-derived page. If external research is requested, keep it clearly separated and cite it independently.

## Concision and style

- Keep pages as short as the source allows. Capture only useful concepts and definitions; avoid padding, repeated explanations, and generic introductions.
- Every book-derived definition entry in a chapter file must follow `schema/template.md`: use the concept name in place of the template's `Definition` heading, copy the concise defining passage verbatim below it without quotation marks or a blockquote marker, include a LaTeX formula only when the book provides one, and finish with only the verified page number/location in a blockquote. Do not emit an empty formula block when no formula exists.
- Preserve the template's order and basic Markdown structure. Do not copy its example definition unless that same definition is independently found in a source book being processed.
- Preserve technical terms as the author uses them. Do not broaden a definition beyond the cited passage.
- Use clear headings and relative Markdown links to chapter files or sections that exist.

## Workflows

### Ingest a book

1. Identify the supplied PDF or EPUB in `sources/`. Do not alter it. Record only bibliographic details that can be verified from the book itself or details explicitly supplied by the user.
2. Read the relevant text, including surrounding context for definitions. Use page or location references that can be checked against the source.
3. Create or update a directory named for the book under `wiki/`. Put chapter material in a chapter Markdown file within that directory. Keep all definitions from the chapter together in that file, with each definition formatted using `schema/template.md`; do not create separate concept pages or a separate books directory.
4. Cite every book-derived definition and substantive claim at the claim or paragraph. Include chapter and page/location where available.
5. Use relative Markdown links to related chapter files when useful. Update `wiki/index.md` and append an entry to `wiki/log.md`.
6. Report extraction gaps or uncertainty plainly. Never claim to have read material that was inaccessible.

When the user asks about a book without requesting wiki updates, answer concisely from the supplied source and cite its location. Ask only when a missing source or ambiguity prevents a reliable answer; otherwise state the limitation and proceed with supported material.

### Query the wiki

Start with `wiki/index.md`, then read the relevant pages and verify important claims against their cited book passages when the source is available. Answer concisely with citations. If the wiki has no support for an answer, say so rather than inventing one. Add a query-derived wiki page only when the user asks to preserve the result.

### Maintain the wiki

On request, check citations, broken links, duplicate concepts, unsupported claims, and conflicting definitions. Fix only what can be resolved from available sources; otherwise mark the gap. Update the index and append a dated log entry for maintenance.

## Index and log conventions

- Keep `wiki/index.md` as a short, categorized catalog with one-line descriptions and links.
- Keep `wiki/log.md` chronological and append-only. Use headings like `## [YYYY-MM-DD] ingest | Book title` or `## [YYYY-MM-DD] maintenance | Description`.
- Use the user's local date when recording an operation.
