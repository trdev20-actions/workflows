# Workflows

## Format

This workflow formats the code and commits the changes.

### Inputs

| Name                  | Description                                                | Required | Default                |
| --------------------- | ---------------------------------------------------------- | -------- | ---------------------- |
| `commit-message`      | The commit message used when pushing formatted changes     | No       | `"style: format code"` |
| `no-ci`               | Whether to add `[no-ci]` to the commit message             | No       | `true`                 |
| `check-format-script` | The npm/yarn script name to check if code needs formatting | No       | `"check-format"`       |
| `format-script`       | The npm/yarn script name to format the code                | No       | `"format"`             |
| `app-id`              | GitHub App ID for authentication                           | No       | -                      |

### Secrets

| Name          | Description                               | Required |
| ------------- | ----------------------------------------- | -------- |
| `private-key` | GitHub App private key for authentication | No       |
| `token`       | GitHub token for authentication           | No       |

### Notes

- You can provide a token to use instead of the default `github.token` or you can provide a GitHub App ID and private key to generate a token for the workflow.

### How It Works

1. Using `trdev20-actions/csi` → Checks out the repository → Sets up NodeJS → Installs dependencies
2. Runs the check format script to determine if formatting is needed

3. If formatting is needed:
   - Runs the format script
   - Commits and pushes the changes

### Requirements

- Your project must have scripts defined in `package.json` for:

  - Checking if code needs formatting (default: `"check-format"`)

  - Formatting code (default: `"format"`)

### Optionally

- The workflow can either take:

  - A GitHub App ID and private key

  - A PAT with the necessary permissions

## License

MIT
