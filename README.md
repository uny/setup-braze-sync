# setup-braze-sync

GitHub Action to install [braze-sync](https://github.com/uny/braze-sync) CLI.

## Usage

```yaml
permissions:
  contents: read

steps:
  - uses: uny/setup-braze-sync@v1
  - run: braze-sync validate
  - run: braze-sync diff --fail-on-drift
    env:
      BRAZE_DEV_API_KEY: ${{ secrets.BRAZE_DEV_API_KEY }}
```

The default `GITHUB_TOKEN` is sufficient: release assets are pulled from the
public `uny/braze-sync` repository, so no extra token scopes are required.

### Pin to a specific version

```yaml
- uses: uny/setup-braze-sync@v1
  with:
    version: "0.1.0"
```

## Inputs

| Name | Description | Default |
|---|---|---|
| `version` | Version to install (e.g. `0.1.0`) | `latest` |
| `token` | GitHub token for downloading release assets | `${{ github.token }}` |

## Outputs

| Name | Description |
|---|---|
| `version` | The version that was installed |
