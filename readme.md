# Sparse commit – GitHub Action

The quickest way to commit to another repository to, for instance, trigger a workflow run in it.

<img width="829" alt="image" src="https://user-images.githubusercontent.com/4989256/160355592-4873f626-1d17-4006-ac10-876590dd2357.png">

Use this action to commit a single file into another git repository, for instance, for automation purposes to trigger
the workflow run.

Features:

+ 🪶 The quickest possible commit using `git sparse-checkout` (it doesn't download entire repository).
+ 🏎 Lightning-fast: no external dependencies in this GitHub Action.
+ ⚠️ Uses external `git` (make sure to properly provide credentials to this action or configure git yourself before this action).

## Usage

Minimalistic example:

```yaml
      - uses: zitros/action-sparse-commit@v1
        with:
          repository: https://${{ secrets.GITHUB_TOKEN }}@github.com/ZitRos/action-sparse-commit
          filename: docs/refs/${{ github.repository }}
          file-content: ${{ github.sha }}
          git-user-name: zitros-bot
```

More options with comments:

```yaml
      - uses: zitros/action-sparse-commit@v1
        with:
          # URL of a repository to check out. Include credentials to this URL if needed.
          repository: https://${{ secrets.GITHUB_TOKEN }}@github.com/ZitRos/action-sparse-commit

          # A file name to commit.
          filename: docs/refs/${{ github.repository }}

          # File content to commit.
          file-content: ${{ github.sha }}

          # Required. A user name to use for commits.
          git-user-name: zitros-bot

          # Optional. A temp directory where repository will be checked out.
          temp-dir: temp-git-sparse-commit-${{ github.sha }}

          # Optional. The user email that will appear in git commit.
          git-user-email: ${{ inputs.git-user-email }})@users.noreply.github.com

          # Optional. A commit message to use.
          git-commit-message: Automated file update
```

## Contributing

Any contributions are welcome, please open a pull request or an issue to discuss new changes.
