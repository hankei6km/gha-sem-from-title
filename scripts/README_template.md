# sem-from-title

GitHub Action to extract semantic information from the title

<!-- INSERT -->

## Example usage

Example of relabeling a pull request based on the Scope included in the PR title:

(`sem-from-title` action does not require permissions such as `pull-requests: write` if you only use it)

```yaml
name: "relabel by sem pr"
on:
  - pull_request_target

jobs:
  relabel:
    permissions:
      contents: read
      pull-requests: write
    runs-on: ubuntu-latest
    steps:
      - name: info
        id: info
        uses: hankei6km/gha-sem-from-title@v0
        with:
          title: ${{ github.event.pull_request.title }}
      - name: edit
        uses: hankei6km/gha-sem-pr-labeler@v0
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          repo: ${{ github.repository }}
          pr_num: ${{ github.event.pull_request.number }}
          type: ${{ steps.info.outputs.type }}
          is_breaking_change: ${{ steps.info.outputs.is_breaking_change }}
```

## Related

- [sem-pr-labeler](https://github.com/hankei6km/gha-sem-pr-labeler)

## Licenses

MIT License

Copyright (c) 2023 hankei6km
