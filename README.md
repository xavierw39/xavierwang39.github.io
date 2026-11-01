# Xavier Wang's Portfolio

A responsive, static portfolio for GitHub Pages. No installation or build step is required.

## Preview

From this directory, run `python -m http.server 8000`, then visit http://localhost:8000. The root entry redirects to `frontend/src/pages/index.html`. Stop the server with Ctrl+C. You can also open `frontend/src/pages/index.html` directly in a browser.

## Pages

All page HTML lives in `frontend/src/pages/`:

- `index.html`: home, project filters, and resume
- `coding.html`: Twitter Text Analysis
- `bi.html`: Colombia Conflict Analysis, with links to the uploaded PDF story, Tableau workbook, and ACLED
- `creative.html`: space for future writing, fiction, and AI short films
- `about.html`: About Me, including experience cards, education, and skills
- `resume.html`: compatibility entry for the About Me content
- `knowledge.html`: a compact list of public readings connected to experience and projects

## File organization

```text
/
├── index.html                  # Small GitHub Pages redirect to the homepage
├── frontend/
│   ├── public/
│   │   ├── images/
│   │   │   ├── companies/      # Employer logos
│   │   │   └── projects/       # Future project screenshots and artwork
│   │   └── documents/
│   │       └── xavier-wang-resume.pdf
│   └── src/
│       ├── components/
│       │   └── portfolio.js    # Reusable project cards and sections
│       ├── pages/
│       │   ├── *.html          # All seven page HTML files
│       │   ├── portfolio.js    # Home, project collections, and creative work
│       │   └── resume.js       # Resume, education, and knowledge page content
│       ├── styles/
│       │   ├── styles.css
│       │   └── resume.css
│       └── main.js             # Shared setup, rendering, and interactions
├── .local/                     # Ignored tools and source materials; not published
├── _config.yml
├── .gitignore
└── README.md
```

This is a plain HTML, CSS, and JavaScript frontend. It does not require React, Vite, a package manager, or a build step. All seven page HTML files live in `frontend/src/pages/`, alongside the page-rendering scripts. They load the shared components, page functions, and then `frontend/src/main.js` using deferred scripts. Navigation links are between sibling HTML files; stylesheet and script paths are relative to the pages folder. Image and document links use `../../public/`.

The root `index.html` only redirects visitors to `frontend/src/pages/index.html` so GitHub Pages still opens the homepage. The JavaScript redirect preserves query parameters and fragment anchors; a meta refresh and clickable link provide fallbacks. Other pages are now addressed as `frontend/src/pages/about.html`, `frontend/src/pages/resume.html`, and so on.

Project cover artwork is illustrative, not a visualization of source data. Creative categories intentionally have no invented work. Add API services or React hooks only if the site eventually needs those features.

## Update the resume

Replace `frontend/public/documents/xavier-wang-resume.pdf` with the latest PDF to keep all resume links working. The stable filename avoids changing links for each update. If you choose another filename, update the `resume` constant in `frontend/src/main.js` and the fallback resume link in each HTML file. Update experience, education, and reading-list content in `frontend/src/pages/resume.js`.

## Publish

Commit and push the website files and resume PDF to the branch configured for this repository's GitHub Pages deployment. The site uses relative links and works without a custom domain. Google Fonts is optional; system fonts are used when unavailable.

## Logos and public reading

The experience cards use the supplied PG&E and BMO images and an XPENG image extracted from the supplied saved webpage. Logos live in `frontend/public/images/companies/`, identify the employers, and do not imply endorsement. The original saved webpage is retained in `.local/sources/`, and temporary PDF-reading tools are in `.local/pdf-tools/`. The entire `.local/` folder is excluded from Git and Jekyll publication.

Experience summaries paraphrase the supplied resume at a general level. Linked articles provide industry context and do not document internal employer systems or individual contributions. Review the downloadable PDF itself before publishing.

The About Me navigation opens experience and education directly. PDF viewing and downloading are available in the top-right header on every page. The older `resume.html` entry still displays the same content for existing links.

The Colombia story uses `frontend/public/documents/Colombia Conflict Data Story.pdf`; keep that file when publishing. Its project dialog links directly to the PDF, provides the Tableau workbook download, and cites ACLED. The Knowledge page renders an extensible list of public links rather than resource cards.
