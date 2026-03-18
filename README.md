# Little Orchard

A GitHub Pages website for Little Orchard, built with Jekyll.

## Live Site

The site is published at: <https://sps23.github.io/little-orchard>

## Prerequisites

- [Ruby](https://www.ruby-lang.org/) 3.2+
- [Bundler](https://bundler.io/)

## Build Locally

1. Install dependencies:

   ```bash
   cd blog
   bundle install
   ```

2. Build the site:

   ```bash
   cd blog
   bundle exec jekyll build
   ```

   The generated site will be in `blog/_site/`.

3. Serve locally with live reload:

   ```bash
   cd blog
   bundle exec jekyll serve --config _config.yml,_config.local.yml
   ```

   Then open <http://localhost:4000/little-orchard> in your browser.

## Deploy to GitHub Pages

Deployment is automated via the GitHub Actions workflow defined in
`.github/workflows/build-deploy.yml`.

Every push to the `main` branch triggers:

1. **build-jekyll** – installs Ruby gems and runs `bundle exec jekyll build`.
2. **deploy** – uploads the built site to GitHub Pages using the official
   `actions/deploy-pages` action.

> **Note:** GitHub Pages must be configured to deploy from **GitHub Actions**
> in the repository settings (*Settings → Pages → Source → GitHub Actions*).

Pull requests run the build step only (no deployment) so you can verify the
site builds correctly before merging.