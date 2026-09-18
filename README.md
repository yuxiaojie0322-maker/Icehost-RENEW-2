# ❄️ IceHost 自动保活工作流

公开运行 GitHub Actions 工作流，核心运行脚本存放于统一私有仓库 `my-private-scripts/icehost` 中。
基于 SeleniumBase UC 模式与 Xvfb 虚拟桌面，通过注入登录 Cookie 自动访问 IceHost 服务器面板进行保活与巡检，支持 Telegram 状态通知与截图推送。

## 配置说明

需要在本仓库的 **Settings -> Secrets and variables -> Actions** 中配置以下 Secrets：

| Secret 名称 | 说明 | 是否必填 |
| :--- | :--- | :--- |
| `CORE_SCRIPT_TOKEN` 或 `REPO_TOKEN` | 具备读取私有仓库 `my-private-scripts` 权限的 GitHub Personal Access Token (PAT) | 必填 |
| `ICEHOST_SERVER_URL` | IceHost 服务器控制面板完整 URL | 必填 |
| `ICEHOST_COOKIES` | IceHost 登录 Cookie（JSON 格式或标准 Cookie 字符串） | 必填 |
| `TG_BOT_TOKEN` | Telegram Bot Token，用于发送保活通知与截图 | 选填 |
| `TG_CHAT_ID` | Telegram 接收通知的 Chat ID | 选填 |

## 手动触发测试

1. 打开本仓库的 **Actions** 页面。
2. 选择 **IceHost Hourly KeepAlive** 工作流。
3. 点击 **Run workflow** 手动触发测试。
4. 之后按照预设计划自动定时执行。
