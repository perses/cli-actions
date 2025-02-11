# Perses CLI Actions

A GitHub Actions library for working with `percli`.

For each utility provided, check the source file to see the list of parameters available.

## Workflows

### [`dac`](.github/workflows/dac.yaml)

A standard workflow that should suit in most cases: The default behavior for it is:
- for a PR: build + validate + preview + diff
- on default branch: build + validate + deploy

## Actions

### [`apply_resource`](./actions/apply_resources/action.yaml)

Wrapper around the `percli apply` command.

### [`build_dac`](./actions/build_dac/action.yaml)

Wrapper around the `percli dac build` command.

### [`diff_dashboards`](./actions/diff_dashboards/action.yaml)

Wrapper around the `percli dac diff` command. It appends the generated diffs as a comment in the pull-request.

### [`install_percli`](./actions/install_percli/action.yaml)

Install percli. Prerequisite to run the other actions.

### [`login`](./actions/login/action.yaml)

Wrapper around the `percli login` command.

### [`preview_dashboards`](./actions/preview_dashboards/action.yaml)

Wrapper around the `percli dac preview` command. It appends the links to the generated preview dashboards as a comment in the pull-request.

### [`validate_resources`](./actions/validate_resources/action.yaml)

Wrapper around the `percli lint` command.



