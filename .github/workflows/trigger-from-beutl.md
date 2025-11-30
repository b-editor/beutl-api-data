# Trigger API Docs Update from Beutl Repository

To automatically trigger API documentation updates when Beutl is released, add the following workflow to `b-editor/beutl/.github/workflows/`:

## trigger-api-docs.yml

```yaml
name: Trigger API Docs Update

on:
  release:
    types: [published]

jobs:
  trigger-api-docs:
    runs-on: ubuntu-latest
    steps:
      - name: Trigger beutl-api-data update
        uses: peter-evans/repository-dispatch@v3
        with:
          token: ${{ secrets.REPO_DISPATCH_TOKEN }}
          repository: b-editor/beutl-api-data
          event-type: beutl-release
          client-payload: '{"ref": "${{ github.ref }}", "version": "${{ github.event.release.tag_name }}"}'
```

## Required Secrets

1. **REPO_DISPATCH_TOKEN**: A Personal Access Token (PAT) with `repo` scope
   - Create at: https://github.com/settings/tokens
   - Add to repository secrets in both:
     - `b-editor/beutl` (to trigger beutl-api-data)
     - `b-editor/beutl-api-data` (to trigger beutl-web-docs)

## Setup Steps

1. Create a Personal Access Token with `repo` scope
2. Add `REPO_DISPATCH_TOKEN` secret to `b-editor/beutl`
3. Add `REPO_DISPATCH_TOKEN` secret to `b-editor/beutl-api-data`
4. Add the workflow file to `b-editor/beutl/.github/workflows/trigger-api-docs.yml`
