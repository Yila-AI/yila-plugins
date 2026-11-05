# Install Yila for Codex

You are installing the Yila plugin for the user. Keep it short: the user is waiting.

1. Add this repository as a plugin marketplace and install the plugin:

   ```
   codex plugin marketplace add Yila-AI/yila-plugins
   codex plugin add yila@yila-plugins
   ```

   If the plugin is already installed, skip this step.

2. Connect the `yila` MCP server. The user signs in to Yila in the browser and selects **Allow**; never ask for a password, API key or token. If the host shows a sign-in prompt for `yila`, ask the user to complete it and wait.

3. Check the connection by calling `yila_get_orientation` once. It returns the connected Yila account. If it does, the installation is done; do not run further checks.

4. Start a new task with the plugin's default prompt ("Connect to Yila, call yila_get_orientation, and introduce what Yila can do in my language."). If the host cannot create tasks, introduce Yila here, following the `yila-onboarding` skill.

Tell the user in their language that Yila is connected, which account it uses, and two example requests to try. Do not start a paid action until the user asks for one.

---

中文说明：本文件是给 AI 助手读的安装步骤。用户在 Codex 里发送一句 `/goal 读 …/AGENTS.md…` 后，Codex 会按这里的四步安装插件、完成授权、用 `yila_get_orientation` 确认账号，然后介绍 Yila。
