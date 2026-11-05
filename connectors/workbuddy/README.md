# WorkBuddy 连接器包（草稿）· WorkBuddy connector package (draft)

中文：按 [WorkBuddy 开放平台连接器规范](https://open.workbuddy.cn/docs/connector) 准备的连接器包，采用 MCP + Skill 方案和云端 OAuth（`auth_mode: "server-side"`，`auth_type: "mcp_oauth"`，由 WorkBuddy 云端动态注册客户端）。上架前，Yila 的授权服务器要把注册方名称 WorkBuddy / CodeBuddy 和 WorkBuddy 的回调域名加入白名单，然后提交 WorkBuddy 审核。

English: A connector package prepared to the [WorkBuddy open platform connector spec](https://open.workbuddy.cn/docs/connector), using MCP + Skill with cloud OAuth (`auth_mode: "server-side"`, `auth_type: "mcp_oauth"`; WorkBuddy's cloud registers its client dynamically). Before listing, Yila's authorization server must allowlist the client names WorkBuddy / CodeBuddy and WorkBuddy's callback domains; then the package is submitted to WorkBuddy for review.
