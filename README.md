github-action-release
======

Composite GitHub Action to release and deploy a brdgm.me application.

Usage example:

```yaml
name: Release and Deploy

on:
  workflow_dispatch:

jobs:
  release:
    runs-on: ubuntu-latest
    environment:
      name: Production
      url: "https://brdgm.me/${{ steps.package_json.outputs.appDeployName }}"

    permissions:
      contents: write

    steps:
      - uses: brdgm/github-action-release@v1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          gh-site-deploy-pat: ${{ secrets.GH_SITE_DEPLOY_PAT }}
          gh-site-deploy-username: ${{ secrets.GH_SITE_DEPLOY_USERNAME }}
          gh-site-deploy-email: ${{ secrets.GH_SITE_DEPLOY_EMAIL }}
          gh-site-deploy-name: ${{ secrets.GH_SITE_DEPLOY_NAME }}
```
