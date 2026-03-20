# Copilot Instructions for Little Orchard

These instructions guide AI-assisted changes in this repository.

## 1) Project Context

- Stack: **Jekyll** static site, served via **GitHub Pages**.
- Runtime for CI: **Ruby 3.2** with Bundler.
- Site source lives in `website/`.
- Main layout and shared components:
  - `website/_layouts/default.html`
  - `website/_layouts/page.html`
  - `website/_includes/header.html`
  - `website/_includes/footer.html`
- Global styling: `website/assets/css/style.css`.
- Production deploy uses `.github/workflows/build-deploy.yml`.

## 2) Repository Rules

- Never edit generated output in `website/_site/`.
- Keep changes minimal and focused; avoid broad rewrites unless requested.
- Preserve existing structure and naming conventions.
- Do not add heavy JavaScript frameworks or build tooling unless explicitly requested.
- Prefer plain HTML, Liquid, and CSS that match the existing codebase style.

## 3) Jekyll and Liquid Best Practices

- Keep page front matter valid YAML when needed.
- Use `relative_url` for internal links and assets so `baseurl` works correctly.
  - Example: `{{ '/about/' | relative_url }}`
- Reuse shared layouts and includes instead of duplicating markup.
- Keep navigation in `website/_config.yml` as the source of truth.
- If adding new pages, ensure links and titles remain consistent across nav and content.
- Preserve plugin compatibility (`jekyll-feed`, `jekyll-seo-tag`).

## 4) HTML, Content, and Accessibility

- Use semantic HTML (`header`, `nav`, `main`, `section`, `footer`, etc.).
- Ensure heading hierarchy is logical (single `h1` per page where practical).
- Add meaningful `alt` text for all informative images.
- Keep interactive controls keyboard accessible and preserve visible focus states.
- Keep `aria-*` usage accurate; avoid adding ARIA when native semantics already cover the case.
- Use clear, family-friendly copy and keep tone consistent with a preschool website.

## 5) CSS and UI Guidelines

- Reuse design tokens in `:root` (colors, spacing, shadows, typography) before adding new ones.
- Prefer extending existing utility and section patterns over creating one-off styles.
- Keep mobile-first behavior intact and validate at common breakpoints.
- Avoid fixed heights that can break content on small screens.
- Keep animations subtle and avoid effects that reduce readability.

## 6) Performance and SEO

- Prefer optimized image formats and reasonable dimensions.
- Avoid large external dependencies for simple interactions.
- Keep metadata meaningful (`title`, page `description`, and existing SEO tags).
- Preserve `{% seo %}` and `{% feed_meta %}` in layouts.

## 7) Local Development and Validation

Use these commands from repository root:

```bash
cd website
bundle install
bundle exec jekyll build
bundle exec jekyll serve --config _config.yml,_config.local.yml
```

Before finalizing changes, verify:

- Site builds without errors.
- Internal links resolve with `baseurl: "/little-orchard"`.
- Navigation works on desktop and mobile.
- No regressions in header/footer layout.

## 8) GitHub Actions and Deployment Awareness

- PRs to `main` run build checks only.
- Pushes to `main` trigger build + Pages deploy.
- CI uses production environment (`JEKYLL_ENV=production`), so avoid relying on dev-only behavior.
- Keep deployment assumptions aligned with `.github/workflows/build-deploy.yml`.

## 9) Safe Change Checklist for Copilot

When generating changes, Copilot should:

1. Modify only files relevant to the requested task.
2. Keep diffs small and easy to review.
3. Prefer consistency with existing patterns over introducing new abstractions.
4. Mention follow-up tasks if a change impacts content, navigation, or assets.
5. Flag uncertainties instead of guessing project-specific facts.

## 10) Useful Enhancements (When Requested)

Good improvements to suggest proactively:

- Add a lightweight accessibility pass (contrast, heading order, focus visibility, alt text).
- Add structured content patterns for repeated sections (cards, CTAs, page heroes).
- Improve image loading strategy for gallery pages.
- Add a short contribution guide for content editors.

