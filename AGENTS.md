# Agent Instructions for Little Orchard

## Project Architecture & Layout
- **Stack:** Jekyll static site, GitHub Pages, Ruby 3.2, Bundler.
- **Directory Structure:** Source files are within the `website/` directory. DO NOT manually edit generated files under `website/_site/`.
- **Key Files:** 
  - Layouts: `website/_layouts/default.html`, `website/_layouts/page.html`
  - Components: `website/_includes/header.html`, `website/_includes/footer.html`
  - Global CSS: `website/assets/css/style.css`
  - Config/Navigation: `website/_config.yml`

## Development Workflows
Run these commands from the repository root:
- **Install Dependencies:**
  ```bash
  cd website && bundle install
  ```
- **Local Development Server:**
  ```bash
  cd website && bundle exec jekyll serve --config _config.yml,_config.local.yml
  ```
- **Manual Build:**
  ```bash
  cd website && bundle exec jekyll build
  ```

## Coding Conventions & Patterns
- **Routing & Links:** Use the Liquid `relative_url` filter for all internal links and assets so `baseurl` works correctly across environments (e.g., `{{ '/about/' | relative_url }}`).
- **CSS & UI:** 
  - Extend existing utility patterns and reuse design tokens in `:root` (found in `style.css`) instead of creating one-off styles.
  - Keep animations subtle. Maintain a mobile-first approach and validate behavior across common breakpoints.
- **HTML & Accessibility:** Avoid heavy JS frameworks. Prefer plain semantic HTML (`header`, `nav`, `main`, `section`, `footer`). Add meaningful `alt` text for images and ensure interactive controls maintain visible focus states.
- **Content:** Keep page front matter as valid YAML. Copy should be family-friendly, consistent with a preschool site.

## CI/CD Dependencies
- Deployments are handled via GitHub Actions (`.github/workflows/build-deploy.yml`). Pushes to `main` use a `JEKYLL_ENV=production` environment, so avoid making assumptions based only on local dev environments.
