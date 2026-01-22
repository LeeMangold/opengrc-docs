# OpenGRC Documentation

This repository contains the documentation for [OpenGRC](https://github.com/LeeMangold/OpenGRC), a cyber Governance, Risk, and Compliance (GRC) web application for small businesses and teams.

**Live documentation**: https://docs.opengrc.com

## Local Development

This documentation site is built with [MkDocs](https://www.mkdocs.org/).

```bash
# Install MkDocs Material theme (includes MkDocs)
pip install mkdocs-material

# On some systems (e.g., Debian/Ubuntu), you may need:
# pip install mkdocs-material --break-system-packages
# Note: This bypasses system package protection. Consider using a virtual environment instead.

# Serve locally with live reload
mkdocs serve

# Build static site
mkdocs build
```

The local server runs at http://127.0.0.1:8000 by default.

## Production Deployment

For production, use a virtual environment to avoid system package conflicts:

```bash
# Create and set up venv (one-time)
python3 -m venv .venv
.venv/bin/pip install mkdocs-material

# Build the site
.venv/bin/mkdocs build --clean
```

### Automated Builds with Cron

To automatically rebuild the docs when changes are pushed to the repository:

```bash
*/15 * * * * cd /var/www/html/sites/OpenGRC-docs && git pull --ff-only && .venv/bin/mkdocs build --clean >> /var/www/html/sites/OpenGRC-docs/cron-build.log 2>&1
```

Build output is logged to `cron-build.log`. Monitor this file to troubleshoot build failures:

```bash
tail -f /var/www/html/sites/OpenGRC-docs/cron-build.log
```

## Contributing

1. Fork this repository
2. Create a branch for your changes
3. Add or edit Markdown files in the `docs/` directory
4. Update `mkdocs.yml` navigation if adding new pages
5. Test locally with `mkdocs serve`
6. Submit a pull request

## License

This documentation is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International license, consistent with the OpenGRC project.
