# fakechat for OpenAgent

Local web chat for exercising OpenAgent message channels.

Install the release archive through OpenAgent Integrations → Plugins. This is an independent adaptation.

## Setup

- Node.js and a free loopback port (default 8787); run the desktop start command before sending messages.

Run /fakechat:setup. Package state and credentials belong in the active OpenAgent home at plugin-data/fakechat/. Never place secrets in plugin.json or commit them. Refresh the plugin after changing credentials.

Run /fakechat:start in a local desktop conversation. channel_bind saves that owner and workspace. Approved inbound peers get separate durable child conversations; replies use the upstream reply tool. Use channel_unbind from the owner to stop dispatch. Access state is plugin-data/fakechat/channel/access.json. Remote messages cannot change access policy or resolve OpenAgent approvals; resolve approvals in the desktop. Pending dispatch failures are logged by the adapter. Delivery deduplication retains the latest 1000 dispatched message IDs; crash recovery has at-least-once semantics.

## Verification

bun test tests

Bundled tests cover immutable artifacts, config conversion and peer isolation, deduplication, owner binding and failed dispatch recovery. Runtime acceptance also verifies a real staged installation, slash-command catalog and integration_status. External account authentication, real provider operations and macOS permissions require the prerequisites above; package tests do not claim those credentials are available.

## 中文

用于验证 OpenAgent 消息通道的本地网页聊天。 安装发布包后运行 /fakechat:setup 查看配置要求。凭据和状态保存在当前 OpenAgent 数据目录的 plugin-data/fakechat/ 下，修改后刷新插件。在本机管理会话运行 /fakechat:start 完成绑定；远程消息不能更改访问权限。

Upstream source and exact revision are recorded in provenance.json. Bundled source remains available for inspection.
