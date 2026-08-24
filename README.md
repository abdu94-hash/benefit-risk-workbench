# Benefit–Risk Workbench — deployment

Companion tool to *Practical Benefit–Risk Assessment in Pharmacovigilance: From Safety
Signals to Regulatory Decisions*, Dr. Hafez Selim, MD, PhD, Selim Medical Press.

Everything here is a static site. There is no build step and no server code — the whole
tool is one self-contained `index.html` with no external requests.

---

## Publish it on GitHub Pages

You are signed in as **abdu94-hash**, so the address these files are already configured
for is:

```
https://abdu94-hash.github.io/benefit-risk-workbench/
```

If you use a different repository name, change it in three files before publishing:
`index.html` (the `og:url`, `canonical` and `og:image` lines), `sitemap.xml`, and
`robots.txt`.

### Click by click

1. Go to <https://github.com/new>.
2. **Repository name:** `benefit-risk-workbench`
3. Set it to **Public**. Do not tick "Add a README" — you already have one.
4. Click **Create repository**.
5. On the new empty repository page, click **uploading an existing file**.
6. Drag in every file from this folder: `index.html`, `og-image.png`, `robots.txt`,
   `sitemap.xml`, `404.html`, `README.md`, and `.nojekyll`.
   - `.nojekyll` is a hidden file. If your file picker will not show it, create it in
     GitHub instead: **Add file → Create new file**, name it `.nojekyll`, leave the body
     empty, and commit. It stops GitHub from running Jekyll over the site.
7. Click **Commit changes**.
8. Go to **Settings → Pages**.
9. Under **Build and deployment**, set **Source** to *Deploy from a branch*, then
   **Branch** to `main` and the folder to `/ (root)`. Click **Save**.
10. Wait one to two minutes, then open
    <https://abdu94-hash.github.io/benefit-risk-workbench/>.

### Confirm it worked

- The page opens on the acceptance gate, and **Begin** stays disabled until the
  acknowledgement box is ticked.
- <https://abdu94-hash.github.io/benefit-risk-workbench/og-image.png> loads the link-preview
  card.
- Paste the site address into a chat or social post and check that the preview card shows
  the title and image.

---

## After it is live: switch the book's links on

The manuscript currently prints a red placeholder marker wherever the tool address should
appear, so no reader ever meets a dead link. Once the site is up, rebuild the book with the
real address:

```bash
cd /path/to/brbook
TOOL_URL="https://abdu94-hash.github.io/benefit-risk-workbench/" \
TOCMAP=./tocmap.json node build.js
```

Every reference in the book becomes a working hyperlink automatically. There is one source
of truth — the `TOOL_URL` environment variable — so there is nothing to find and replace.

---

## Search-engine indexing

`robots.txt` allows all crawlers and points at `sitemap.xml`. To speed indexing up, add the
site to [Google Search Console](https://search.google.com/search-console) and submit
`sitemap.xml` once.

## Corrections

Error reports and corrections: **abdu94@gmail.com**

## Licence and notice

© Dr. Hafez Selim. The tool is for education only. It is not medical advice, not clinical
decision support, not a medical device, and not validated regulatory submission software.
All worked-example data are fictional. The views expressed are the author's personal views
and do not represent any current or former employer, client, institution, professional
society or regulatory body. The full terms are in the tool itself, under **Full terms** on
the acceptance gate.
