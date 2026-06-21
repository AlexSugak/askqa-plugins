# @askqa/mcp

MCP server for [AskQA](https://askqa.ai) — monitor websites with automated tests by chatting with AI.

## Setup

Add to your MCP client config (e.g. Claude Code, Claude Desktop, Cursor):

```json
{
  "mcpServers": {
    "askqa": {
      "command": "npx",
      "args": ["-y", "@askqa/mcp"],
      "env": {
        "AUTOQA_API_URL": "https://api.askqa.ai",
        "AUTOQA_API_KEY": "aq_..."
      }
    }
  }
}
```

Get your API key from [askqa.ai](https://askqa.ai) after signing in.

## Environment Variables

| Variable         | Required | Description                                |
| ---------------- | -------- | ------------------------------------------ |
| `AUTOQA_API_KEY` | Yes      | Your AskQA API key                         |
| `AUTOQA_API_URL` | No       | API URL (default: `http://localhost:8081`) |

## Tools

| Tool                          | Description                                             |
| ----------------------------- | ------------------------------------------------------- |
| `list_tests`                  | List all saved tests                                    |
| `get_test`                    | Get full details of a test                              |
| `create_test`                 | Create a test from a template or custom Playwright code |
| `update_test`                 | Update an existing test                                 |
| `delete_test`                 | Delete a test (with confirmation)                       |
| `run_test`                    | Run a test and wait for results                         |
| `get_test_results`            | Get recent test run results with step details           |
| `heal_test`                   | Diagnose a layout-change regression and help fix selectors |
| `get_test_screenshots`        | Get screenshots from a test run                         |
| `list_templates`              | List available test templates                           |
| `screenshot_url`              | Screenshot a URL and extract page structure             |
| `validate_test`               | Dry-run custom test code before saving                  |
| `schedule_test`               | Create a recurring schedule for a test                  |
| `list_schedules`              | List all test schedules                                 |
| `update_schedule`             | Pause or resume a schedule                              |
| `delete_schedule`             | Delete a schedule                                       |
| `add_notification_channel`    | Add a Telegram notification channel                     |
| `list_notification_channels`  | List notification channels                              |
| `remove_notification_channel` | Remove a notification channel                           |
| `test_notification_channel`   | Send a test notification                                |
| `share_test_run`              | Make a test run publicly shareable, returns a share URL |
| `unshare_test_run`            | Revoke public sharing for a test run                    |
| `get_shared_run`              | Fetch a shared run by URL or token (no API key needed); includes test code to recreate it |

## Example Conversations

**Check if something is working:**

> "Is checkout working on my site?"

The AI will call `list_tests` to find a matching test, then `get_test_results` to check the latest run.

**Create a new monitor:**

> "Monitor https://example.com — check that the homepage loads and has a sign-in button"

The AI will use `screenshot_url` to inspect the page, write custom Playwright code, `validate_test` to verify it works, then `create_test` and `schedule_test`.

**Debug a failing test:**

> "Why is my checkout test failing?"

The AI will call `get_test_results` and `get_test_screenshots` to analyze the failure.

**Share a test run:**

> "Share my latest checkout run with the client"

The AI will call `get_test_results` to find the run, then `share_test_run` to generate a public link. Use `unshare_test_run` to revoke access later.

**Copy a shared test into your account:**

> "I got this link — can you set up the same test for my site? https://askqa.ai/r/..."

The AI will call `get_shared_run` to read the test code from the shared link (no API key needed), then `create_test` to add it to your account.

## Privacy Policy

This extension only makes HTTPS requests to the AskQA API. It does not access files on your computer or collect analytics.

For full details, see the [Privacy Policy](https://askqa.ai/privacy).

## Support

- **Website**: [askqa.ai](https://askqa.ai)
- **Issues**: [GitHub Issues](https://github.com/askqa-ai/askqa-plugins/issues)
- **Email**: support@askqa.ai

## License

MIT
