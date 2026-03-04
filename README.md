# AskQA Plugin for Claude Code

Official Claude Code plugin for [AskQA](https://askqa.ai) - automated website testing and monitoring.

## Quick Start

### 1. Add the marketplace

```bash
/plugin marketplace add AlexSugak/askqa-plugins
```

### 2. Install the plugin

```bash
/plugin install askqa
```

### 3. Configure MCP server (easy way)

Run the setup skill to automatically configure your API key:

```bash
/askqa:setup-mcp
```

This will guide you through getting your API key and configure the MCP server automatically.

### 3. Manual configuration (alternative)

Or manually add to your `.mcp.json`:

```json
{
  "mcpServers": {
    "askqa": {
      "command": "node",
      "args": ["${CLAUDE_PLUGIN_ROOT}/askqa/server.js"],
      "env": {
        "AUTOQA_API_URL": "https://api.askqa.ai",
        "AUTOQA_API_KEY": "aq_..."
      }
    }
  }
}
```

Get your API key from [askqa.ai/account](https://askqa.ai/account).

## Available Skills

### `/askqa:setup-mcp`
Automatically configure the AskQA MCP server with your API key. Detects whether you're in a git repo (configures `.claude/.mcp.json`) or using Desktop (configures global settings).

### `/askqa:setup-slack`
Configure Slack notifications for test failures. Guides you through:
- Creating a Slack incoming webhook
- Adding the notification channel
- Testing the integration

### `/askqa:shopify-add-to-cart`
Set up automated monitoring for Shopify add-to-cart flows. Guides you through:
- Creating a test for your Shopify store
- Running the test to verify it works
- Scheduling hourly monitoring
- Setting up failure alerts

## Available MCP Tools

Once configured, you also get access to MCP tools for test management:

- `list_templates` - List available test templates
- `create_test` - Create a new test
- `screenshot_url` - Screenshot a URL and extract page structure
- `validate_test` - Dry-run custom test code before saving
- `list_tests` - List all saved tests
- `get_test` - Get full details of a test
- `update_test` - Update an existing test
- `delete_test` - Delete a test
- `run_test` - Run a test and get results
- `get_test_screenshots` - Get screenshots from a test run
- `schedule_test` - Schedule recurring test runs
- `list_schedules` - List all test schedules
- `update_schedule` - Pause or resume a schedule
- `delete_schedule` - Delete a schedule
- `get_test_results` - View test run history
- `add_notification_channel` - Configure email, Telegram, or Slack alerts
- `list_notification_channels` - List notification channels
- `remove_notification_channel` - Remove a notification channel
- `test_notification_channel` - Send a test notification

## About AskQA

AskQA is an automated website testing and monitoring service. Create tests using natural language or custom Playwright code, schedule them to run on an interval, and get notified when something breaks.

Visit [askqa.ai](https://askqa.ai) to learn more.

## License

MIT
