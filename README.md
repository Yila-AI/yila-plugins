# Yila 插件 · Yila Plugins

[中文](#中文) · [English](#english)

<a id="中文"></a>

## 中文

在你的 AI 助手里用 [Yila](https://yila.ai) 做科研：查中英文文献、读全文、核验引用、排参考文献，画能逐元素编辑的科研图。用的是你自己的 Yila 账号和积分，不需要 API 密钥。

> **公测中。**功能和价格可能每周调整。遇到问题请在反馈群里说，或者提 [Issue](https://github.com/Yila-AI/yila-plugins/issues)。

### 能做什么

**画图，画布就在对话旁边**
- 附上论文，说要什么图，Yila 画图形摘要、机制图、流程图（一般 1.5–3 分钟）。
- 宿主有内置浏览器时（例如 Codex 桌面版），Yila 画布直接在旁边打开，自动登录。
- 把导师或审稿人的意见整段贴过去，新版本出现在旧版本旁边。
- 在画布里导出可编辑的 PPTX 和 SVG。

**你的 Agent 背后的研究工作台**
- 深度检索：Yila 的检索 Agent 自己规划检索，中英文文献（含万方）一起找，几分钟后给一张带理由的排序表。
- 读全文：每次最多 4 篇并行读，回答带页码。
- 核验引用：逐条标出真实、信息有误、查无此文。
- 排参考文献：2,800 多种格式，含 GB/T 7714。
- 结果都存在你的 Yila 项目里，网页上能接着看、接着改。

### 安装

服务地址：`https://mcp.yila.ai/mcp`（Streamable HTTP，OAuth 授权）

| AI 助手 | 怎么装 |
|---|---|
| **Codex** | 在任意任务里发送：`/goal 读 https://github.com/Yila-AI/yila-plugins/blob/main/AGENTS.md，为 Codex 安装 Yila 插件，并新建一个任务运行它的默认连接提示。`<br>或者命令行：`codex plugin marketplace add Yila-AI/yila-plugins`，再 `codex plugin add yila@yila-plugins` |
| **Claude Code** | `claude plugin marketplace add Yila-AI/yila-plugins`，再 `claude plugin install yila@yila-plugins` |
| **WorkBuddy** | 连接器 → 自定义连接器 → 配置 MCP，粘贴：`{"mcpServers":{"yila":{"type":"streamableHttp","url":"https://mcp.yila.ai/mcp"}}}` |
| **Claude 网页版 / 桌面版** | 设置 → 连接器 → 添加自定义连接器，填入服务地址 |
| **ChatGPT** | 开发者模式 → 添加自定义 MCP 服务器，名称填 Yila，填入服务地址 |
| **其他支持远程 MCP 的客户端** | 添加一个 HTTP 类型的 MCP 服务器，地址同上 |

第一次使用时，浏览器会打开 Yila 授权页：确认账号，点“允许”。之后在“设置 → 已连接的 Agent”里能看到每个 Agent 花了多少积分，随时断开。

### 积分和隐私

- 读论文、理解你的要求、写要点，用的是你自己 AI 助手的额度；Yila 只在出图、检索这些成品上扣 Yila 积分，每次都会告诉你扣了多少。
- 同一个请求只扣一次；失败的任务自动退回积分。
- 你交给 Yila 的论文和数据只用来完成这次任务，存在你自己的 Yila 账号里，可以随时删除。

### 这个仓库里有什么

```
.agents/plugins/marketplace.json   Codex 插件市场清单
.claude-plugin/marketplace.json    Claude Code 插件市场清单
AGENTS.md                          给“一句话安装”读的安装说明
plugins/yila/                      插件本体：MCP 地址、图标和 5 篇 skill
connectors/workbuddy/              WorkBuddy 连接器包（草稿）
```

插件本身只有清单和写给 AI 助手的使用说明（skill），没有服务端代码，也不包含任何密钥。

### 许可证

[MIT](LICENSE)

---

<a id="english"></a>

## English

Use [Yila](https://yila.ai) for research inside your AI agent: search English and Chinese literature, read full texts, verify citations, format references, and draw scientific figures you can edit element by element. It uses your own Yila account and credits. No API key needed.

> **Public beta.** Features and prices may change weekly. Report problems in the feedback group or open an [issue](https://github.com/Yila-AI/yila-plugins/issues).

### What it does

**Figures, with the canvas beside the chat**
- Attach a paper and say what you need; Yila draws graphical abstracts, mechanism diagrams and flowcharts (usually 1.5–3 minutes).
- In hosts with a built-in browser (such as the Codex desktop app), the Yila canvas opens beside the conversation, already signed in.
- Paste your advisor's or reviewers' comments; the new version appears next to the old one.
- Export editable PPTX and SVG from the canvas.

**A research workbench behind your agent**
- Deep search: Yila's search agent plans its own queries across English and Chinese sources (including Wanfang) and returns a ranked table with reasons in a few minutes.
- Full-text reading: up to 4 papers at a time, answers cite pages.
- Citation checks: every reference marked real, mismatched or not found.
- References in 2,800+ styles, including GB/T 7714.
- Everything stays in your Yila project, ready to continue on the web.

### Install

Server URL: `https://mcp.yila.ai/mcp` (Streamable HTTP, OAuth)

| Agent | How to install |
|---|---|
| **Codex** | Send this in any task: `/goal Read https://github.com/Yila-AI/yila-plugins/blob/main/AGENTS.md to install the Yila plugin for Codex and set up a new task that runs its default connection prompt.`<br>Or from the command line: `codex plugin marketplace add Yila-AI/yila-plugins`, then `codex plugin add yila@yila-plugins` |
| **Claude Code** | `claude plugin marketplace add Yila-AI/yila-plugins`, then `claude plugin install yila@yila-plugins` |
| **WorkBuddy** | Connectors → Custom connector → Configure MCP, then paste: `{"mcpServers":{"yila":{"type":"streamableHttp","url":"https://mcp.yila.ai/mcp"}}}` |
| **Claude (web or desktop)** | Settings → Connectors → Add custom connector, then enter the server URL |
| **ChatGPT** | Developer mode → Add a custom MCP server named Yila with the server URL |
| **Other remote-MCP clients** | Add an HTTP MCP server with the URL above |

On first use your browser opens the Yila authorization page: check the account and select **Allow**. In **Settings → Connected agents** you can see what each agent spent and disconnect it at any time.

### Credits and privacy

- Reading papers, understanding your request and writing the outline use your own agent's quota; Yila charges Yila credits only for results such as figures and searches, and every result says what it charged.
- The same request is never charged twice; failed jobs are refunded automatically.
- Papers and data you give Yila are used only for that task, stay in your own Yila account, and can be deleted at any time.

### What's in this repository

```
.agents/plugins/marketplace.json   Codex plugin marketplace
.claude-plugin/marketplace.json    Claude Code plugin marketplace
AGENTS.md                          Install instructions for the one-line install
plugins/yila/                      The plugin: MCP server URL, icon and 5 skills
connectors/workbuddy/              WorkBuddy connector package (draft)
```

The plugin contains only manifests and instructions for your agent (skills). There is no server code and no secret in this repository.

### License

[MIT](LICENSE)
