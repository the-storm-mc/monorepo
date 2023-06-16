# Documentation

[![Netlify Status](https://api.netlify.com/api/v1/badges/0495746a-9a90-43a0-a262-e49ac217f814/deploy-status)](https://app.netlify.com/sites/tsmc-docs/deploys)

This repository contains documentation for The Storm.

## Requirements

You'll need to install the following software:

- [Earthly](https://earthly.dev/)
- [Docker](https://www.docker.com/)

You'll need some secrets set with Earthly secrets:

- `sj/mkdocs_gh_token`: A GitHub token that has permission to pull [squidfunk/mkdocs-material-insiders](https://github.com/squidfunk/mkdocs-material-insiders)

## Usage

```
# Build the documentation
earthly +build

# Start a live-reloading server
# MKDOCS_GH_TOKEN must be set to a GitHub token that has permission to pull [squidfunk/mkdocs-material-insiders](https://github.com/squidfunk/mkdocs-material-insiders)
pipenv install
earthly +dev
```
