# Codex Setup

Codex is OpenAI's official command-line tool. You can connect it to a custom model service through Newton AI Router.

## Installation

```bash
npm install -g @openai/codex
```

## Configuration

### Windows

1. Open the `.codex` folder in your user directory:

    ```text
    C:\Users\your-username\.codex
    ```

2. Open `config.toml` and replace its contents with:

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

3. Open `auth.json` and replace its contents with:

    ```json
    {
      "OPENAI_API_KEY": "your-api-key-here"
    }
    ```

4. Quit Codex completely, then reopen it.

!!! tip
    If the files are not visible, enable hidden files. If they still do not exist, create them manually.

### macOS

1. Create the `.codex` folder:

    ```bash
    mkdir -p ~/.codex
    ```

2. Create `config.toml`:

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

3. Create `auth.json`:

    ```bash
    cat > ~/.codex/auth.json << 'EOF'
    {
      "OPENAI_API_KEY": "your-api-key-here"
    }
    EOF
    ```

4. Quit Codex completely, then reopen it.

!!! tip
    If Codex cannot connect, verify the `base_url` value in `config.toml`.
