# Yila 插件 · Yila Plugins

[中文](#中文) · [English](#english)

<a id="中文"></a>

## 中文

在你的 AI 助手里用 [Yila](https://yila.ai) 画科研图：你的助手读完论文写好要点，Yila 画出图形摘要、机制图、流程图，存进你的 Yila 项目，能编辑的 Yila 画布就在对话旁边打开。用的是你自己的 Yila 账号和积分，不需要 API 密钥。

> **公测中。**功能和价格可能每周调整。遇到问题请在反馈群里说，或者提 [Issue](https://github.com/Yila-AI/yila-plugins/issues)。

### 能做什么

**画图，画布就在对话旁边**

- 附上论文，说要什么图，Yila 画图形摘要、机制图、流程图（一般 1.5–3 分钟）。
- 宿主有内置浏览器时（例如 Codex 桌面版），Yila 画布直接在旁边打开，已经登录好；没有内置浏览器时，点助手给的链接打开。
- 把导师或审稿人的意见整段贴过去，新版本出现在旧版本旁边，旧版本保留。
- 在画布上逐个元素修改，导出可编辑的 PPTX 和 SVG。

**即将上线**：中英文文献深度检索、读全文、核验引用、排参考文献（含 GB/T 7714）。

### 安装

服务地址：`https://yila.ai/api/mcp`（Streamable HTTP，OAuth 授权）

| AI 助手         | 怎么装                                                                                                                                                                       |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Codex**       | `codex plugin marketplace add Yila-AI/yila-plugins`，再 `codex plugin add yila@yila-plugins`<br>只要连接、不要 skill：`codex mcp add yila --url https://yila.ai/api/mcp` |
| **Claude Code** | `claude plugin marketplace add Yila-AI/yila-plugins`，再 `claude plugin install yila@yila-plugins`<br>只要连接：`claude mcp add --transport http yila https://yila.ai/api/mcp` |
| **WorkBuddy**   | 连接器 → 自定义连接器 → 配置 MCP，粘贴：`{"mcpServers":{"yila":{"type":"streamableHttp","url":"https://yila.ai/api/mcp"}}}`                                               |
| **其他客户端**  | 添加一个 HTTP 类型的远程 MCP 服务器，地址同上                                                                                                                                |

第一次使用时，浏览器会打开 Yila 的登录和授权页：确认账号，点“允许”。之后在 Yila 网站的“设置 → 已连接的 Agent”里能看到每个 Agent 近 30 天花了多少积分，随时断开。

Claude 网页版、ChatGPT 这类在云端连接的客户端还没有测试。

### 积分

- 读论文、理解你的要求、写要点，用的是你自己 AI 助手的额度；Yila 只在画图和改图时扣 Yila 积分（一般每张 300），图存进你的项目后才扣，每次都告诉你扣了多少。
- 同一个请求只扣一次；失败或取消的任务不扣积分。
- 画出的图存在你自己的 Yila 账号里，在网页上能接着看、接着改。

### 这个仓库里有什么

```
.agents/plugins/marketplace.json   Codex 插件市场清单
.claude-plugin/marketplace.json    Claude Code 插件市场清单
AGENTS.md                          给“一句话安装”读的安装说明
plugins/yila/                      插件本体：MCP 地址、图标和 3 篇 skill
connectors/workbuddy/              WorkBuddy 连接器包（草稿）
```

插件本身只有清单和写给 AI 助手的使用说明（skill），没有服务端代码，也不包含任何密钥。

### 许可证

[MIT](LICENSE)

---

<a id="english"></a>

## English

Draw scientific figures with [Yila](https://yila.ai) inside your AI agent: your agent reads the paper and writes the outline, Yila draws graphical abstracts, mechanism diagrams and workflows, saves them in your Yila project, and opens the editable Yila canvas beside the conversation. It uses your own Yila account and credits. No API key needed.

> **Public beta.** Features and prices may change weekly. Report problems in the feedback group or open an [issue](https://github.com/Yila-AI/yila-plugins/issues).

### What it does

**Figures, with the canvas beside the chat**

- Attach a paper and say what you need; Yila draws graphical abstracts, mechanism diagrams and workflows (usually 1.5–3 minutes).
- In hosts with a built-in browser (such as the Codex desktop app), the Yila canvas opens beside the conversation, already signed in. Elsewhere, click the link your agent gives you.
- Paste your advisor's or reviewers' comments; the new version appears next to the old one, which stays.
- Edit element by element on the canvas and export editable PPTX and SVG.

**Coming soon:** deep literature search across English and Chinese sources, full-text reading, citation checks and references in 2,800+ styles including GB/T 7714.

### Install

Server URL: `https://yila.ai/api/mcp` (Streamable HTTP, OAuth)

| Agent             | How to install                                                                                                                                                                       |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Codex**         | `codex plugin marketplace add Yila-AI/yila-plugins`, then `codex plugin add yila@yila-plugins`<br>Connection only, without the skills: `codex mcp add yila --url https://yila.ai/api/mcp` |
| **Claude Code**   | `claude plugin marketplace add Yila-AI/yila-plugins`, then `claude plugin install yila@yila-plugins`<br>Connection only: `claude mcp add --transport http yila https://yila.ai/api/mcp` |
| **WorkBuddy**     | Connectors → Custom connector → Configure MCP, then paste: `{"mcpServers":{"yila":{"type":"streamableHttp","url":"https://yila.ai/api/mcp"}}}`                                     |
| **Other clients** | Add a remote HTTP MCP server with the URL above                                                                                                                                      |

On first use your browser opens Yila's sign-in and authorization page: check the account and select **Allow**. In **Settings → Connected agents** on the Yila website you can see what each agent spent in the last 30 days and disconnect it at any time.

Cloud-connected clients such as Claude on the web and ChatGPT have not been tested yet.

### Credits

- Reading papers, understanding your request and writing the outline use your own agent's quota; Yila charges Yila credits only for drawing and revising figures (usually 300 each), only once the figure is saved in your project, and every result says what it charged.
- The same request is never charged twice; failed or cancelled jobs charge nothing.
- Your figures stay in your own Yila account, ready to view and continue on the web.

### What's in this repository

```
.agents/plugins/marketplace.json   Codex plugin marketplace
.claude-plugin/marketplace.json    Claude Code plugin marketplace
AGENTS.md                          Install instructions for the one-line install
plugins/yila/                      The plugin: MCP server URL, icon and 3 skills
connectors/workbuddy/              WorkBuddy connector package (draft)
```

The plugin contains only manifests and instructions for your agent (skills). There is no server code and no secret in this repository.

### License

[MIT](LICENSE)
