# Yila 插件 · Yila Plugins

[中文](#中文) · [English](#english)

<a id="中文"></a>

## 中文

在你的 AI 助手里用 [Yila](https://yila.ai) 做科研：画能在 Yila 画布上接着改的科研图，查中英文文献、核验引用、按 2,800 多种格式排参考文献，把综述、PPT、海报这类整件事交给 Yila 跑。用的是你自己的 Yila 账号和积分，不需要 API 密钥。

> **公测中。**功能和价格可能每周调整。遇到问题请在反馈群里说，或者提 [Issue](https://github.com/Yila-AI/yila-plugins/issues)。

### 能做什么

**画图，画布就在对话旁边**

- 附上论文，说要什么图，Yila 画图形摘要、机制图、流程图（一般 1.5–3 分钟）。
- 宿主有内置浏览器时（例如 Codex 桌面版），Yila 画布直接在旁边打开，已经登录好；没有内置浏览器时，点助手给的链接打开。
- 把导师或审稿人的意见整段贴过去，新版本出现在旧版本旁边，旧版本保留。
- 在画布上逐个元素修改，导出可编辑的 PPTX 和 SVG。

**查文献、核验、排参考文献**

- 你的助手写好检索式，Yila 查 OpenAlex、PubMed、Google Scholar 和万方（中文），返回带引用键（如 [Wan24]）、DOI 和摘要的论文列表，整张表存进项目（含 Excel）。
- 把 DOI、题名或整段参考文献表变成准确的文献信息。
- 逐条核验参考文献：真实、信息有误（给出正确的年份或 DOI）、查无此文。
- 按 2,800 多种格式排参考文献，中文默认 GB/T 7714。
- 把论文存进“我的文献库”，把笔记存进项目。

**整件事交给 Yila 跑**

- 深度检索、带真实引用的完整综述、PPT、学术海报、数据分析：Yila 自己的研究 Agent 在你的账号里跑（网站的任务列表里能看到），跑完把回复和文件交回给你的助手。
- 你给一个积分上限，按实际用量扣，到上限就暂停；跑完还能接着让它改。
- Yila 中途提问时，在任务页里回答。

**还没接入插件**：上传你自己的文件给 Yila 读，目前在 Yila 网页里用。

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

- 读论文、理解你的要求、写要点，用的是你自己 AI 助手的额度。Yila 只在这些成品上扣 Yila 积分，每次都告诉你扣了多少：画图或改图一般每张 300（图存进项目后才扣）；检索每个有结果的来源 30；核验每条 10；交给 Yila 的任务按实际用量扣，不超过你给的上限。查找、排版、文献库和笔记免费。
- 同一个请求只扣一次；失败或取消的任务不扣积分。
- 画出的图存在你自己的 Yila 账号里，在网页上能接着看、接着改。

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

Use [Yila](https://yila.ai) for research inside your AI agent: draw scientific figures you keep editing on the Yila canvas, search English and Chinese literature, check references and format them in 2,800+ styles, and hand whole jobs such as a review, a deck or a poster to Yila. It uses your own Yila account and credits. No API key needed.

> **Public beta.** Features and prices may change weekly. Report problems in the feedback group or open an [issue](https://github.com/Yila-AI/yila-plugins/issues).

### What it does

**Figures, with the canvas beside the chat**

- Attach a paper and say what you need; Yila draws graphical abstracts, mechanism diagrams and workflows (usually 1.5–3 minutes).
- In hosts with a built-in browser (such as the Codex desktop app), the Yila canvas opens beside the conversation, already signed in. Elsewhere, click the link your agent gives you.
- Paste your advisor's or reviewers' comments; the new version appears next to the old one, which stays.
- Edit element by element on the canvas and export editable PPTX and SVG.

**Literature: search, check, format**

- Your agent writes the queries; Yila searches OpenAlex, PubMed, Google Scholar and Wanfang (Chinese) and returns papers with citation keys like [Wan24], DOIs and abstracts, saving the whole table (also as Excel) in your project.
- Turn DOIs, titles or a pasted reference list into exact records.
- Check every reference: real, details wrong (with the correct year or DOI), or not found.
- Format references in 2,800+ styles, GB/T 7714 by default for Chinese.
- Save papers to My Library and notes to the project.

**Hand whole jobs to Yila**

- A deep literature search, a full review with real citations, a slide deck, an academic poster, a data analysis: Yila's own research agent runs it in your account (it shows in your task list on the website) and hands its answer and files back to your agent.
- You set a credit cap; the task is charged by actual usage and pauses at the cap. You can keep asking for changes afterwards.
- When Yila asks a question along the way, you answer it on the task page.

**Not yet in the plugin:** uploading your own files for Yila to read; use the Yila web app for now.

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

- Reading papers, understanding your request and writing the outline use your own agent's quota. Yila charges Yila credits only for these results, and every result says what it charged: a figure or figure edit usually 300 (only once it is saved in your project); a search 30 for each source that returns papers; a reference check 10 each; a task handed to Yila by actual usage, never above the cap you set. Lookup, formatting, the library and notes are free.
- The same request is never charged twice; failed or cancelled jobs charge nothing.
- Your figures stay in your own Yila account, ready to view and continue on the web.

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
