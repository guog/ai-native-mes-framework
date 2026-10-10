# AI Native MES 技术基础框架 · 架构文档集

**版本：V0.2（架构设计草案，2026-10-10）**

这是一个**仅包含架构文档、契约草案、风险及验证计划的仓库**。不包含实际 MES 代码，不应当宣称已经通过生产认证。

## 从这里开始

1. [完整 16 章架构规格书](docs/architecture.md)
2. [ADR-001～ADR-130 决策基线](adr/baseline-v1.md)（全部 Accepted，规范化摘要；以用户确认原文为准）
3. [模块/插件/动作/事件/任务/持久化/UI 等契约](contracts/README.md)
4. [ADR 跨章节追踪索引](docs/adr-traceability.md)
5. [认证与验收计划](verification/verification-plan.md)
6. [待验证风险](quality/risk-register.md)
7. [Mermaid 图集](diagrams/README.md)

## 技术路线

- TypeScript + Node.js / Fastify + GraphQL Yoga + GraphQL Tools / Zod / Vue。
- GraphQL 为主要业务 API；REST 和 MCP 作为协议适配入口。
- 模块化单体 + 可签名动态插件；可信扩展可同进程，低信任隔离运行。
- Kysely 为优先数据访问路线；达梦 dmdb Dialect 待验证，失败按既有 ADR 使用受控 dmdb/SQL 适配。
- PostgreSQL / SQL Server / MySQL / 达梦四种主业务库支持目标；每实例选择一种。
- 工厂自治、异步集团同步、事务审计/Outbox、主库持久化 Worker、独立 AI Runtime。

## 维护纪律

1. ADR-001～ADR-130 不得擅自改写；新意见应提交单独的 ADR 变更提案。
2. 所有文档使用 Markdown/Mermaid，避免依赖图像或横向宽表。
3. “已设计”“待验证”“已认证”不可混用，任何数值承诺必须与证据相连。
4. 不提交凭据、真实生产数据或客户内部细节。
5. 当前文档并未获得工程实现授权，`AGENTS.md` 仅用于阅读和文档维护。

## GitHub 提交

期望仓库：`guog/ai-native-mes-framework`，**private**。若目标仓库不存在，请先创建空私有仓库，再按 `GITHUB_IMPORT.md` 将整个目录作为首次文档提交。
