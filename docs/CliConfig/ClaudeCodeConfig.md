# Claude Code Setup

Claude Code is Anthropic's official command-line tool for using Claude AI directly from a terminal.

## Installation

```bash
npm install -g @anthropic-ai/claude-code
```

## Configuration

### Windows

1. Open the `.claude` folder in your user directory:

    ```text
    C:\Users\your-username\.claude
    ```

    You can also press `Win + R` and enter:

    ```text
    %userprofile%\.claude
    ```

2. Open `settings.json` and replace its contents with:

    ```json
    {
      "env": {
        "ANTHROPIC_AUTH_TOKEN": "your-api-key-here",
        "ANTHROPIC_BASE_URL": "https://newtonrouter.com",
        "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1"
      },
      "permissions": {
        "allow": [],
        "deny": []
      }
    }
    ```

!!! tip
    If the file is not visible, enable hidden files. If it still does not exist, create it manually.

### macOS

1. Open Finder, press `Command + Shift + G`, and enter:

    ```text
    ~/.claude
    ```

    If the directory does not exist, run this command in Terminal:

    ```bash
    mkdir -p ~/.claude
    ```

2. Open `settings.json` and replace its contents with:

    ```json
    {
      "env": {
        "ANTHROPIC_AUTH_TOKEN": "your-api-key-here",
        "ANTHROPIC_BASE_URL": "https://newtonrouter.com",
        "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1"
      },
      "permissions": {
        "allow": [],
        "deny": []
      }
    }
    ```

## Common commands

| Command | Description |
| --- | --- |
| `claude` | Start an interactive session |
| `claude -p "question"` | Ask one question and exit after the response |
| `claude -c` | Resume the most recent session |
| `claude --model sonnet` | Use a specific model |
| `claude mcp` | Manage MCP server connections |
