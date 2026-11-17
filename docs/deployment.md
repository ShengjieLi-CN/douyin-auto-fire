# 本仓库的 Actions 配置

在仓库 Actions Secrets 中配置 `DOUYIN_COOKIE`（Cookie JSON 数组）、
`DOUYIN_CONFIG_MORNING`（早间好友与消息配置 JSON）和
`DOUYIN_CONFIG_EVENING`（晚间好友与消息配置 JSON）。凭据和好友信息不提交到仓库。

手动运行 **Send Douyin Messages** 时，`dry_run` 默认开启：检查登录状态和
目标好友，不发送消息。`period` 选择 `morning` 或 `evening`。
确认检查通过后，可关闭 `dry_run` 进行真实发送。

每天自动发送由 Actions Variable `DOUYIN_AUTO_SEND_ENABLED` 控制，只有值为
`true` 时定时任务才会执行。当前计划为每天北京时间 **08:00**（早间配置）和
**23:00**（晚间配置），定义在 `.github/workflows/send.yml`，显式使用
`Asia/Shanghai` 时区。未配置该变量时仍可手动运行检查。

GitHub Actions 定时任务可能排队延迟，无法保证精确到分钟。

本仓库关闭浏览器 trace，失败时只上传日志与结果 JSON，不上传可能含私信
或会话凭据的截图与浏览器跟踪文件。好友昵称使用上游已有的别名脱敏机制。

上游完整教程见 [GitHub Actions 使用教程](github-actions.md)。
