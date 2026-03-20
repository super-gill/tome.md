# TOME

A lightweight, zero-dependency documentation platform that turns markdown files into a polished, navigable knowledge base — entirely client-side.

TOME accepts standard markdown monoliths and presents them as structured, multi-page documents with sidebar navigation, full-text search, themed viewing, and branded PDF export. No build step, no backend, no frameworks. Just drop your `.md` files in and serve.

## Features

- **Hierarchical navigation** — H1 headings become sidebar groups, H2 headings become pages, H3-H5 generate an in-page table of contents
- **Full-text search** — instant search across all loaded content with highlighted matches and context previews
- **7 color themes** — System (auto), Dark, Light, Midnight, Ember, Forest, Sand — persisted per user
- **PDF export** — single page or full manual with branded letterhead, cover pages, and configurable margins
- **Markdown export** — download the current page or full manual as `.md`
- **Export branding profiles** — define multiple brand configurations with custom logos, footers, page sizes, and cover pages
- **Document metadata** — extract title, version, date, and classification from markdown headers
- **Deep linking** — shareable URLs to any page via hash fragments
- **Keyboard shortcuts** — `n`/`p` to navigate, `/` to search, `Escape` to close panels
- **Responsive** — mobile drawer navigation with hamburger menu
- **Self-contained** — all dependencies (markdown-it, html2pdf) bundled locally in `/libs/`
- **Automatic updates** — checks for newer versions on load with a dismissible banner

## Quick Start

1. Clone or download the repository
2. Add your markdown files to the `Books/` directory
3. Register them in `books.json`:
   ```json
   [
     {
       "file": "Books/my-docs/manual.md",
       "title": "My Documentation"
     }
   ]
   ```
4. Serve with any static file server (or open `index.html` directly)

## Writing Content

TOME uses a simple heading convention to structure your markdown:

```markdown
Document Title: My Manual
Document Version: v1.0.0
Document Date: 20/03/2026
Document Classification: Internal

# Section Group

## Page Title

### Subheading (appears in page ToC)

Your content here — standard markdown with full HTML passthrough.

## Another Page

More content...

# Another Group

## Yet Another Page
```

- **H1** — sidebar group (collapsible)
- **H2** — sidebar page (navigable)
- **H3–H5** — in-page headings (auto-generate a table of contents if 3+ are present)
- **Metadata lines** — optional, placed at the top of the file before any headings

## Configuration

### `tome.json`

Platform-level branding and behavior:

```json
{
  "branding": {
    "defaultTitle": "TOME Markdown",
    "classification": "",
    "favicon": "favicon.svg"
  },
  "pdf": {
    "logo": "letterhead_logo.png",
    "footer": ["Line 1", "Line 2", "Line 3"]
  },
  "splash": {
    "minDurationMs": 2000
  }
}
```

### Export Branding

Create custom PDF brand profiles in `export-branding/`:

1. Add a folder under `export-branding/` with a `brand.json`:
   ```json
   {
     "label": "My Brand",
     "pageSize": "a4",
     "orientation": "portrait",
     "margins": { "top": 20, "right": 10, "bottom": 15, "left": 10 },
     "header": {
       "logo": "media/logo.png",
       "logoWidth": 40,
       "logoAspect": 4.04,
       "x": 15,
       "y": 8
     },
     "footer": {
       "lines": ["Company Name", "", ""],
       "fontSize": 9,
       "color": 80
     },
     "coverPage": true,
     "coverTitle": null
   }
   ```
2. Register the folder name in `export-branding/brands.json`

## Project Structure

```
tome.md/
├── index.html          # Application shell
├── index.js            # All application logic
├── styles.css          # Complete styling
├── tome.json           # Platform configuration
├── books.json          # Book manifest
├── version.json        # Current version
├── libs/               # Bundled dependencies (markdown-it, html2pdf)
├── export-branding/    # PDF brand profiles
│   ├── brands.json     # Brand manifest
│   ├── default/        # Minimal (no branding)
│   └── .../            # Additional brand profiles
└── Books/              # Markdown content
    └── .../            # Your documentation files
```

## Deployment

TOME is fully static — deploy it anywhere that serves files:

- GitHub Pages
- Any web server (nginx, Apache, IIS)
- Local file system (open `index.html` directly)
- Network share

No build step, no Node.js, no dependencies to install.

## License

Proprietary. Copyright Jason Mcdill.
