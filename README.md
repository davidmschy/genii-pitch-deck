# Genii Investor Pitch Deck

Interactive investor presentation built with Reveal.js.

## View Live

Once GitHub Pages is enabled, the presentation will be available at:
**https://davidmschy.github.io/genii-pitch-deck/**

## Features

- 10 professionally designed slides covering Genii's value proposition
- Royal blue (#003399) branding with smooth transitions
- Fully responsive design
- Keyboard navigation (arrow keys)
- Touch/swipe support on mobile

## Setup GitHub Pages

1. Go to repository Settings
2. Navigate to Pages (left sidebar)
3. Under "Build and deployment":
   - Source: GitHub Actions
4. The workflow will automatically deploy on every push to main

## Manual Deployment Workflow

Create `.github/workflows/deploy.yml` with:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        
      - name: Setup Pages
        uses: actions/configure-pages@v4
        
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: '.'
          
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

## Local Development

Simply open `index.html` in a browser, or serve via:

```bash
python3 -m http.server 8000
```

Then navigate to `http://localhost:8000`

## Navigation

- **Arrow keys**: Navigate between slides
- **Space**: Next slide
- **Esc**: Overview mode
- **F**: Fullscreen

---

**Confidential** - March 2026
