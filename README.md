# Setup GIT
This GitHub Action will automatically setup following git configs
- User Config
  - `user.name` value depends on [`user`](#inputs)input field
  - `user.email` value depends on [`user`](#inputs) input field
- **Push Config**
  - `push.autoSetupRemote`: `true`

# Inputs
- `user` valid values
  - `bot` _(default)_ - configure `github-actions[bot]` as git user
  - `actor` - configure [github actions context](https://docs.github.com/en/actions/learn-github-actions/contexts#github-context) `github.actor` as git user
  - `committer` - configure committer from `HEAD` commit as git user
  - `USER_NAME <USER_EMAIL>` - configure git user explicitly

### Example
```yaml
jobs:
  basic-ubuntu-20:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: qoomon/actions--setup-git@v1
        with:
          user: bot

      - runs: |
          date > dummy.txt
          git add dummy.txt
          git commit -m "chore: update dummy"
          git push
```

## Development

### Release New Action Version

Trigger [Release Version workflow](/actions/workflows/action-release.yaml)
