# Claude Code 常见问题

## 遇到 `Invalid API Key · Please run /login` 错误？

这通常表示 Claude Code 没有检测到环境变量。请检查：

- 是否正确设置了 `ANTHROPIC_AUTH_TOKEN` 和 `ANTHROPIC_BASE_URL`。
- 环境变量值是否正确，令牌通常以 `sk-` 开头。
- 修改配置后是否已经重启终端。

## 为什么显示 `offline` 状态？

Claude Code 会通过连接 Google 来判断网络状态。显示 `offline` 通常不影响正常使用，只是表示它无法连接到 Google。

## 为什么浏览网页的 Fetch 会失败？

Claude Code 在访问网页前需要调用 Claude 服务进行安全检查。你可以检查：

- 是否保持稳定的国际互联网连接。
- 是否需要使用全局代理。
- API 转发地址是否可用。

## 连接超时或错误怎么办？

请按下面顺序检查：

1. 确认网络连接正常。
2. 确认 `ANTHROPIC_BASE_URL` 设置为 [https://newtonrouter.com](https://newtonrouter.com)。
3. 如果使用代理，确认代理配置正确。
4. 尝试关闭 VPN 或代理后重试。

## API 报错如何处理？

可能是转发代理不稳定导致的，建议：

1. 退出 Claude Code，例如按 `Ctrl + C`。
2. 重新运行 `claude` 命令。
3. 如果问题持续，稍后再试。
