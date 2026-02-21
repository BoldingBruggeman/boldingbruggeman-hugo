# Bolding & Bruggeman ApS — Website

Hugo-based company website. Small, compact, intentional.

## Structure

```
├── hugo.toml              # Site configuration
├── content/               # Markdown pages (minimal frontmatter only)
│   ├── _index.md          # Home
│   ├── people.md
│   ├── projects.md
│   ├── software.md
│   └── contact.md
├── data/
│   ├── people.yaml        # ← EDIT TEAM MEMBERS HERE
│   └── projects.yaml      # ← EDIT PROJECTS HERE
├── assets/css/main.css    # Single stylesheet
├── layouts/               # Hugo templates
│   ├── _default/
│   │   ├── baseof.html    # Base layout (nav + footer)
│   │   └── single.html    # Fallback single page
│   ├── index.html         # Homepage
│   ├── people/single.html # People page (reads data/people.yaml)
│   ├── projects/single.html # Projects page (reads data/projects.yaml)
│   ├── software/single.html
│   └── contact/single.html
└── static/
    └── favicon.svg
```

## Editing content

### Team members — `data/people.yaml`

```yaml
people:
  - name: "Full Name"
    role: "Job Title"
    focus: "Short focus line (italic subtitle)"
    bio: >
      Longer bio paragraph(s). Use > for multi-line strings.
    email: "name@bolding-bruggeman.com"
    github: "github-username"   # leave empty string "" to hide
    orcid: "0000-0000-0000-0000"  # leave empty string "" to hide
    photo: ""                   # future: path to photo in static/
```

### Projects — `data/projects.yaml`

```yaml
projects:
  - title: "Project Title"
    description: >
      Project description paragraph.
    period:
      start: "2023"
      end: "2026"          # leave blank for ongoing
    status: "active"       # "active" or "completed"
    funding_short: "EU Horizon Europe"    # short label shown in header row (~40 chars max)
    funding: >                             # full text shown in expanded panel (optional)
      This work was funded by ...
    responsible: "Person Name"
    official_website: "https://..."   # leave "" to hide button
    our_website: "https://..."        # leave "" to hide button
    partners:
      - "Partner 1 (CC)"
      - "Partner 2 (CC)"
```

## Local development

```bash
hugo server -D
```

## Build for production

```bash
hugo --minify
```

Output goes to `public/`. Deploy to any static host (Netlify, GitHub Pages, etc.).

## Notes

- Fonts load from Google Fonts — replace with local fonts for fully offline use
- No JavaScript dependencies except inline accordion script on projects page
- CSS uses `resources.Get` (Hugo Pipes) — requires Hugo extended for minification
  in production; standard Hugo works fine for development
