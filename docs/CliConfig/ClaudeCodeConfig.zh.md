# Claude Code 工具配置

Claude Code 是 Anthropic 官方提供的命令行工具，可以让你直接在终端中使用 Claude AI。

## 安装

```bash
npm install -g @anthropic-ai/claude-code
```

## 配置

### Windows

1. 进入用户目录下的 `.claude` 文件夹：

    ```text
    C:\Users\你的用户名\.claude
    ```

    也可以按 `Win + R`，输入：

    ```text
    %userprofile%\.claude
    ```

2. 找到 `settings.json` 文件，改为以下内容：

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
    如果没有看到文件，先开启隐藏文件显示；还是没有的话，可以手动创建。

### macOS

1. 打开 Finder，按 `Command + Shift + G`，输入：

    ```text
    ~/.claude
    ```

    如果目录不存在，在终端执行：

    ```bash
    mkdir -p ~/.claude
    ```

2. 找到 `settings.json` 文件，改为以下内容：

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

## 常用命令

| 命令 | 说明 |
| --- | --- |
| `claude` | 启动交互式会话 |
| `claude -p "问题"` | 单次问答模式，回答后直接退出 |
| `claude -c` | 恢复最近一次会话 |
| `claude --model sonnet` | 指定使用的模型 |
| `claude mcp` | 管理 MCP 服务器连接 |
