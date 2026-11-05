# WorkBuddy 连接器包（草稿）· WorkBuddy connector package (draft)

中文：按 [WorkBuddy 开放平台连接器规范](https://open.workbuddy.cn/docs/connector) 准备的连接器包，采用 MCP + Skill 方案和云端 OAuth（`auth_mode: "server-side"`，`auth_type: "mcp_oauth"`，由 WorkBuddy 云端动态注册客户端）。Yila 的授权服务器对公开客户端开放动态注册，WorkBuddy 不需要预先登记。提交 WorkBuddy 审核前，先用自定义连接器在 WorkBuddy 里完整走一遍授权、画图和打开画布。

English: A connector package prepared to the [WorkBuddy open platform connector spec](https://open.workbuddy.cn/docs/connector), using MCP + Skill with cloud OAuth (`auth_mode: "server-side"`, `auth_type: "mcp_oauth"`; WorkBuddy's cloud registers its client dynamically). Yila's authorization server accepts dynamic registration from public clients, so WorkBuddy needs no prior registration. Before submitting for review, run the whole flow once in WorkBuddy as a custom connector: authorization, a figure and opening the canvas.
