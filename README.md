# Perses CLI Actions

A GitHub Actions library for working with `percli`.

For each utility provided, check the source file to see the list of parameters available.

## Workflows

### [`dac`](.github/workflows/dac.yaml)

A standard workflow for Dashboard-as-Code that should suit in most cases. The default behavior for it is:
- on a PR: build + validate + preview + diff
- on default branch: build + validate + deploy

On a PR, it posts a single consolidated comment listing for each dashboard: its status, a link to the preview, a link to the current version and a link to the diff (published in the workflow run summary).

Example of usage:
```yaml
jobs:
  dac:
    uses: perses/cli-actions/.github/workflows/dac.yaml@v0.1.0
    with:
      url: https://demo.perses.dev
      directory: ./dac
      server-validation: true
    secrets:
      username: ${{ secrets.USR }}
      password: ${{ secrets.PWD }}
```

## Actions

### [`apply_resource`](./actions/apply_resources/action.yaml)

Wrapper around the `percli apply` command.

Example of usage:
```yaml
steps:
  - name: Deploy the dashboards
    uses: perses/cli-actions/actions/apply_resources@v0.1.0
    with:
      directory: ./testdata/dashboards_folder
```

### [`build_dac`](./actions/build_dac/action.yaml)

Wrapper around the `percli dac build` command.

Example of usage:
```yaml
steps:
  - name: Build DaC definitions
    uses: perses/cli-actions/actions/build_dac@v0.1.0
    with:
      directory: ./testdata/dac_folder
```

### [`install_percli`](./actions/install_percli/action.yaml)

Install percli. Prerequisite to run the other actions.

Example of usage:
```yaml
steps:
  - name: Install percli
    uses: perses/cli-actions/actions/install_percli@v0.1.0
    with:
      cli-version: "latest"
```

### [`login`](./actions/login/action.yaml)

Wrapper around the `percli login` command.

Example of usage:
```yaml
steps:
  - name: Login to the API server
    uses: perses/cli-actions/actions/login@v0.1.0
    with:
      url: https://demo.perses.dev
      username: ${{ secrets.TEST_USERNAME }}
      password: ${{ secrets.TEST_PASSWORD }}
```

### [`preview_and_diff_dashboards`](./actions/preview_and_diff_dashboards/action.yaml)

Wrapper around the `percli dac preview` and `percli dac diff` commands. It posts a consolidated report of the dashboard changes as a comment in the pull-request (can be disabled with the `comment` input), with the diffs published to the workflow run summary. The preview and diff stages can be individually skipped with the `skip-preview` and `skip-diff` inputs.

Example of usage:
```yaml
steps:
  - name: Preview & diff the dashboards
    uses: perses/cli-actions/actions/preview_and_diff_dashboards@v0.1.0
    with:
      directory: ./testdata/dashboards_folder
      prefix: test-preview
```

### [`validate_resources`](./actions/validate_resources/action.yaml)

Wrapper around the `percli lint` command.

Example of usage:
```yaml
steps:
  - name: Validate dashboards
    uses: perses/cli-actions/actions/validate_resources@v0.1.0
    with:
      directory: ./testdata/dashboards_folder
```
