# sem-from-title

GitHub Action to extract semantic information from the title

<!-- INSERT -->

## Example usage

```yaml
- name: info
  id: info
  uses: hankei6km/gha-sem-from-title@v0
  with:
    title: ${{ github.event.pull_request.title }}
- name: edit
  uses: hankei6km/gha-sem-pr-labeler@mv0
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
