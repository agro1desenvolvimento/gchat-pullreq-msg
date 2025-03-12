# Google Chat Pull Request Message

A GitHub Action to notify Google Chat when a pull request is opened, reopened, or ready for review.

## Inputs

| Name         | Description                           | Required |
|--------------|---------------------------------------|----------|
| `webhook-url`| Google Chat webhook URL for notifications | Yes      |

## Usage Example

Create a new webhook in Google Chat and add the URL to your repository secrets.

```yaml
name: PR Notification
on:
  pull_request:
    types: [opened, reopened, ready_for_review]

jobs:
  notify-gchat:
    runs-on: ubuntu-latest
    steps:
      (...)
      - name: Send PR notification to Google Chat
        uses: agro1desenvolvimento/gchat-release-msg@v1
        if: github.event.pull_request.draft == false # remove that line to notify on draft PRs too
        with:
          webhook-url: ${{ secrets.GOOGLECHAT_WEBHOOK_PR_URL }}
      (...)
```
