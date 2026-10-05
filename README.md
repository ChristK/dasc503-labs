# DASC503 Data Labs — interactive practice

Self-check activities for the MSc module *Using Routine Data for Public Health*,
one page per week, published with GitHub Pages:

**https://christk.github.io/dasc503-labs/**

| Week | Page |
|---|---|
| 1 — Introduction to R | [week1.html](https://christk.github.io/dasc503-labs/week1.html) |
| 2 — Working with tables using `data.table` | [week2.html](https://christk.github.io/dasc503-labs/week2.html) |

Each page is a single self-contained HTML file. R runs **in the student's
browser** via [webR](https://docs.r-wasm.org/webr/latest/) (R compiled to
WebAssembly), so students need nothing installed. Nothing they type is stored
or transmitted.

## Embedding in Canvas

Canvas strips `<script>` from pages and, on our instance, will not run scripts
in uploaded HTML files either — so pages are hosted here and embedded with an
iframe. In a Canvas page's HTML editor:

```html
<p><a href="https://christk.github.io/dasc503-labs/week1.html" target="_blank"
      rel="noopener">Open the Week 1 practice page in a new tab</a></p>
<p><iframe src="https://christk.github.io/dasc503-labs/week1.html"
           width="100%" height="1200" loading="lazy"
           title="DASC503 Week 1 interactive practice"
           style="border:1px solid #d9dee6;border-radius:6px"></iframe></p>
```

Keep the link as well as the iframe: it still works if a browser or a Canvas
security setting blocks the frame.

## Adding a week

Copy `week1.html` to `weekN.html`, change the content, add a row to the list in
`index.html` and to the table above, and push. Pages republishes in about a
minute; the URL pattern stays the same.

## Maintenance notes

- **webR is pinned** (`WEBR_VERSION` near the top of the script) so an upstream
  release cannot change behaviour mid-term. Bump it deliberately, then test.
- **Two download sources.** R is fetched from `webr.r-wasm.org`, retried once,
  then from jsDelivr. jsDelivr's fallback uses its `+esm` endpoint because the
  npm package's own `dist/webr.mjs` is the Node build and cannot load in a
  browser.
- **First load is about 30 MB** (cached afterwards) and takes 5–15 seconds.
  Safari occasionally drops a large download part-way; the page retries,
  fails over, and otherwise shows a plain-English message with a *Try again*
  button.
- If the scripts are blocked, a visible notice with a link to this site
  appears instead of silently empty sections.
