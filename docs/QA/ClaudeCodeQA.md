# Claude Code FAQ

## What should I do if I see `Invalid API Key · Please run /login`?

This usually means Claude Code did not detect the required environment variables. Check that:

- `ANTHROPIC_AUTH_TOKEN` and `ANTHROPIC_BASE_URL` are set correctly.
- The environment variable values are correct. Tokens usually begin with `sk-`.
- You restarted the terminal after changing the configuration.

## Why does Claude Code show `offline`?

Claude Code checks its network status by connecting to Google. An `offline` status usually does not affect normal use; it only indicates that Google could not be reached.

## Why does web Fetch fail?

Claude Code calls the Claude service for a security check before accessing a web page. Check that:

- Your international internet connection is stable.
- A global proxy is enabled if required.
- The API forwarding endpoint is available.

## What should I do if the connection times out or fails?

Check the following in order:

1. Confirm that your network connection is working.
2. Confirm that `ANTHROPIC_BASE_URL` is set to [https://newtonrouter.com](https://newtonrouter.com).
3. If you use a proxy, verify its configuration.
4. Try disabling the VPN or proxy, then retry.

## How should I handle API errors?

The forwarding proxy may be temporarily unstable. Try the following:

1. Exit Claude Code, for example by pressing `Ctrl + C`.
2. Run the `claude` command again.
3. If the issue continues, wait a moment and retry.
