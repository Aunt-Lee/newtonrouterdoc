# Codex 工具配置

Codex 是 OpenAI 官方提供的命令行工具，通过牛顿 AI 中转站可以配置自定义模型服务。

## 安装

```bash
npm install -g @openai/codex
```

## 配置

### Windows

1. 进入用户目录下的 `.codex` 文件夹：

    ```text
    C:\Users\你的用户名\.codex
    ```

2. 找到 `config.toml` 文件，改为以下内容：

    ```toml
    model_provider = "newtonrouter"
    model = "gpt-5.5"
    model_reasoning_effort = "high"
    disable_response_storage = true

    [model_providers.newtonrouter]
    name = "newtonrouter"
    base_url = "https://newtonrouter.com/v1"
    wire_api = "responses"
    requires_openai_auth = true
    ```

3. 找到 `auth.json` 文件，改为以下内容：

    ```json
    {
      "OPENAI_API_KEY": "your-api-key-here"
    }
    ```

4. 完全退出 Codex 后重新打开。

!!! tip
    如果没有看到文件，先开启隐藏文件显示；还是没有的话，可以手动创建。

### macOS

1. 创建 `.codex` 文件夹：

    ```bash
    mkdir -p ~/.codex
    ```

2. 创建 `config.toml`：

    ```bash
    cat > ~/.codex/config.toml << 'EOF'
    model_provider = "newtonrouter"
    model = "gpt-5.5"
    model_reasoning_effort = "high"
    disable_response_storage = true

    [model_providers.newtonrouter]
    name = "newtonrouter"
    base_url = "https://newtonrouter.com/v1"
    wire_api = "responses"
    requires_openai_auth = true
    EOF
    ```

3. 创建 `auth.json`：

    ```bash
    cat > ~/.codex/auth.json << 'EOF'
    {
      "OPENAI_API_KEY": "your-api-key-here"
    }
    EOF
    ```

4. 完全退出 Codex 后重新打开。

!!! tip
    如果连接不上，检查 `config.toml` 中的 `base_url` 是否填写正确。
