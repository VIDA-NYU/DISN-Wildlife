# DISN Wildlife Research Project

A modern, responsive Hugo-based website for the DISN Wildlife Research Project.

## Project Structure

```
.
├── archetypes/              # Content templates
├── content/                 # Markdown content files
│   ├── _index.md            # Homepage content
│   ├── team/                # Team member pages (one .md per person)
│   │   ├── _index.md        # Team list page
│   │   ├── juliana-freire.md
│   │   └── ...
│   ├── publications/        # Publication pages (one .md per publication)
│   │   ├── _index.md        # Publications list page
│   │   └── ...
│   └── news/                # News pages (one .md per news item)
│       ├── _index.md        # News list page
│       └── ...
├── data/                    # (empty - content is in markdown files)
├── layouts/                 # HTML templates
│   ├── _default/            # Default layouts
│   ├── partials/            # Reusable components
│   └── index.html           # Homepage layout
├── static/                  # Static assets
│   ├── css/                 # Stylesheets
│   ├── js/                  # JavaScript
│   ├── images/              # Images
│   ├── img/                 # Additional images (logos)
│   └── files/               # PDF files
├── hugo.toml                # Hugo configuration
└── README.md                # This file
```

## Getting Started

### Prerequisites

- [Hugo](https://gohugo.io/installation/) (v0.120.0 or later recommended)

### Installation

```bash
# Clone the repository
git clone https://github.com/VIDA-NYU/DISN-Wildlife-website.git
cd DISN-Wildlife-website

# Start the development server
hugo server
```

Open http://localhost:1313/ in your browser.

### Building for Production

```bash
hugo --minify
```

The built site will be in the `public/` directory.

---

## Content Management

All content is managed through individual Markdown files. Each team member, publication, and news item has its own `.md` file.

### Adding a New Team Member

1. Create a new file in `content/team/` with a slug-friendly name:
   ```bash
   touch content/team/firstname-lastname.md
   ```

2. Add the following frontmatter and content:

```markdown
---
title: "Full Name"
image: "/images/photo-filename.jpg"
role: "Position Title"
affiliation: "University/Institution"
website: "https://personal-website.com"
weight: 12  # Controls display order (lower = first)
---

Biography text goes here. This will be displayed on the team page.
```

3. Add the team member's photo to `static/images/`

**Frontmatter fields:**
| Field | Required | Description |
|-------|----------|-------------|
| `title` | Yes | Full name of the team member |
| `image` | Yes | Path to photo (relative to static folder, start with `/`) |
| `role` | Yes | Position/title (e.g., "Principal Investigator", "PhD Candidate") |
| `affiliation` | Yes | University or institution name |
| `website` | No | Personal website URL (leave empty string if none) |
| `weight` | Yes | Display order (1 = first, higher numbers appear later) |

---

### Adding a New Publication

1. Create a new file in `content/publications/`:
   ```bash
   touch content/publications/short-title-year.md
   ```

2. Add the following frontmatter and content:

```markdown
---
title: "Full Publication Title"
authors: "Author 1, Author 2, Author 3"
venue: "Journal or Conference Name"
year: "2025"
image: "/images/publication-thumbnail.png"
paper_url: "https://link-to-paper.com"
code_url: "https://github.com/repo"
weight: 1  # Controls display order (lower = first)
---

Optional description or abstract of the publication.
```

3. Add a thumbnail image to `static/images/` (recommended size: 400x300px)

**Frontmatter fields:**
| Field | Required | Description |
|-------|----------|-------------|
| `title` | Yes | Full title of the publication |
| `authors` | Yes | Comma-separated list of authors |
| `venue` | Yes | Journal, conference, or workshop name |
| `year` | Yes | Publication year |
| `image` | No | Thumbnail image path |
| `paper_url` | No | Link to paper (PDF or publisher page) |
| `code_url` | No | Link to code repository |
| `weight` | Yes | Display order (1 = first) |

---

### Adding a News Item

1. Create a new file in `content/news/`:
   ```bash
   touch content/news/event-name-year.md
   ```

2. Add the following frontmatter and content:

```markdown
---
title: "Event or News Title"
date: 2025-04-15  # YYYY-MM-DD format
image: "/images/event-photo.jpg"
excerpt: "Short description for the card preview (1-2 sentences)."
presentation_url: "https://link-to-slides.com"
poster_url: "https://link-to-poster.com"
workshop_url: "https://workshop-website.com"
paper_url: "/files/paper.pdf"
weight: 1  # Controls display order (lower = first)
---

Full description of the event or news item. This appears in the modal popup when users click on the news card.
```

3. Add the event image to `static/images/`

**Frontmatter fields:**
| Field | Required | Description |
|-------|----------|-------------|
| `title` | Yes | Event or news title |
| `date` | Yes | Date in YYYY-MM-DD format |
| `image` | Yes | Event image path |
| `excerpt` | Yes | Short preview text (shown on card) |
| `presentation_url` | No | Link to presentation/slides |
| `poster_url` | No | Link to poster |
| `workshop_url` | No | Link to workshop website |
| `paper_url` | No | Link to paper PDF |
| `weight` | Yes | Display order (1 = first) |

---

## Editing Existing Content

Simply edit the corresponding `.md` file in the `content/` directory. Changes will be reflected immediately when running `hugo server`.

### Example: Update a team member's bio

1. Open `content/team/juliana-freire.md`
2. Edit the content below the frontmatter `---`
3. Save the file

---

## Adding Images

1. Place images in `static/images/`
2. Reference them in markdown with `/images/filename.jpg`

**Recommended image sizes:**
- Team photos: 400x400px (square, will be cropped to circle)
- Publication thumbnails: 400x300px
- News images: 800x450px (16:9 aspect ratio)

---

## Configuration

Edit `hugo.toml` to change:

```toml
baseURL = "/"                    # Change for deployment
title = "DISN Wildlife Research Project"

[params]
  description = "..."            # Site description for SEO
  github = "https://github.com/..." # GitHub repository link
  nsfAward = "https://..."       # NSF award page link

[menu]
  [[menu.main]]
    name = "Home"
    url = "/"
    weight = 1
  # Add more menu items...
```

---

## Features

- **Responsive Design**: Works on mobile, tablet, and desktop
- **Dark Mode**: Automatic system preference detection with manual toggle
- **Modern UI**: Clean cards, smooth animations, hover effects
- **SEO Optimized**: Proper meta tags and semantic HTML
- **Fast Loading**: Optimized CSS, minimal JavaScript
- **Accessible**: ARIA labels and keyboard navigation

---

## Deployment

### GitHub Pages

1. Build the site:
   ```bash
   hugo --minify
   ```

2. Push the `public/` directory to your GitHub Pages branch

### Netlify

1. Connect your repository to Netlify
2. Build command: `hugo --minify`
3. Publish directory: `public`

### Vercel

1. Import your repository
2. Framework preset: Hugo
3. Build command: `hugo --minify`
4. Output directory: `public`

---

## License

This project is part of the DISN Wildlife Research Project funded by the [National Science Foundation](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2146306).
