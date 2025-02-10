## Releasing a new version of perses/cli-actions

- Append a commit "Prepare release vX.Y.Z" to the main branch that changes the `ref` number in [action.yaml](action.yaml) to the new version vX.Y.Z.
- Create the release from github UI ("Draft a new release").
  - Create a new tag named vX.Y.Z targetting the main branch.
  - Fill title & desc
  - Publish