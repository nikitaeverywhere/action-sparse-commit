# Sparse commit GitHub action

Use this action to commit a single file into another git repository, for instance, for automation purposes to trigger
the workflow run.

## Usage

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
