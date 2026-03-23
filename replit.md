# alex-landing-page

A minimal static landing page.

## Tech Stack

- Plain HTML5 (`index.html`)
- No build system or package manager
- Served via Python's built-in HTTP server in development

## Project Structure

```
index.html     - Main (and only) page
README.md      - Project title
.github/       - GitHub Actions workflows (Azure Static Web Apps CI/CD)
```

## Running the App

The app is served using Python's built-in HTTP server on port 5000:

```
python3 -m http.server 5000 --bind 0.0.0.0
```

## Deployment

Configured as a static site deployment with `publicDir: "."`.
