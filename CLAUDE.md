# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is the **documentation repository** for OpenGRC, a Laravel/Filament-based Governance, Risk, and Compliance (GRC) web application. Documentation is built with MkDocs and deployed to https://docs.opengrc.com.

**Important**: The OpenGRC application codebase may be soft-linked into this repository for reference purposes. Do NOT edit the OpenGRC application code—it is here only to help write accurate documentation.

## Documentation Build Commands

```bash
# Serve documentation locally (default port 8000)
mkdocs serve

# Build static documentation site
mkdocs build

# Deploy to GitHub Pages (if configured)
mkdocs gh-deploy
```

## Project Structure

```
docs/               # Markdown documentation files
  index.md          # Landing page
  installation.md   # Installation guide
  foundations.md    # Core GRC concepts (Programs, Standards, Controls, etc.)
  updating.md       # Update procedures
  configuration.md  # AWS S3 and other configuration
  api.md            # REST API documentation
  sso/              # Single Sign-On guides (Azure, Okta, Google, Auth0)
mkdocs.yml          # MkDocs configuration (ReadTheDocs theme)
```

## Documentation Guidelines

- The site uses the ReadTheDocs theme
- Navigation is defined in `mkdocs.yml` under the `nav:` key
- Add new pages by creating `.md` files in `docs/` and updating `mkdocs.yml`
- Images go in `docs/img/`

## OpenGRC Application Context

When writing documentation, reference these key OpenGRC concepts:

- **Programs** - Organizational groupings for compliance initiatives
- **Standards** - Compliance frameworks (NIST, ISO, CMMC, etc.)
- **Controls** - Individual security requirements within standards
- **Implementations** - How controls are actually implemented
- **Audits** - Assessment processes with audit items
- **Risks** - Risk management entities

The application is built with Laravel 11 and Filament 3, uses Sanctum for API authentication, and supports MySQL/MariaDB/SQLite databases.
