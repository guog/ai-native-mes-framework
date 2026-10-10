# 第 15 章 · 技术选型、版本与兼容性

**状态：** 技术路线说明；组件集成仍待验证。**ADR：** 012～015、020、029、047、066、086、100～102、112、115～118、123～124、127、129。

## 15.1 已确认的架构技术路线

- 后端：Node.js / TypeScript，成熟组件构成轻量宿主；HTTP 采用 **Fastify**，GraphQL 采用 **GraphQL Yoga + GraphQL Tools**，动态 Schema 由 MES 框架管理版本快照。
- 主 API：**GraphQL**；REST 和 MCP 为适配入口，业务动作契约为权威来源。
- 动作类型/校验：**Zod** 为 TypeScript 运行时 Schema 主工具；跨协议转换需验证类型保真。
- 前端：**Vue** 统一应用壳，可选推送，低信任插件 UI 独立隔离。
- 数据库：正式目标 **PostgreSQL / SQL Server / MySQL / 达梦**，每实例选择一种主业务库。
- 查询：**Kysely 优先**；达梦以 `dmdb` 验证自定义 Dialect，失败时按 ADR-123 以受控 dmdb/SQL 适配保留支持范围。
- 异步：独立 Worker，以主库最小持久化任务/Outbox 为默认；不强制 Redis/消息总线。
- 交付：Linux + Docker；Monorepo 管理内核、SDK、官方模块和应用；动态插件签名、不可变、版本化交付。

## 15.2 冻结的决策 vs 未认证实现

- **已批准技术方向** ≠ 已验证具体版本或生产可用。
- GraphQL Yoga/Fastify 需要验证请求上下文、插件热启停、高可用多实例快照切换、错误传播及资源限制。
- Kysely 官方 Dialect 覆盖 PostgreSQL/MySQL/SQL Server，但达梦不具备官方内置 Dialect 保证；`dmdb` 驱动存在不代表所有数据库契约通过。
- Zod 到 JSON Schema/GraphQL 需要处理不可表示类型及验证语义差异。
- 四数据库是否具备已认证同步持久化 HA，以及达到标准/HA RTO，必须逐版本逐部署组合取证。

## 15.3 数据库版本支持条目的最小要求

每一条认证记录包含：`databaseVendor`、`certifiedMajorVersion`、`patchWindow`、`driverVersion`、`queryAdapterVersion`、`frameworkVersion`、`deploymentMode`、`HAStack`、`OSContainerPlatform`、`testedCapabilities`、`testEvidence`、`supportFrom/Until`、`status`。

状态至少区分：`candidate`（候选）、`tested`（已测试但未授权）、`certified`（经审查正式认证）、`unsupported`（不支持）、`expired`（认证过期）；这些是文档结构建议，不代表已经存在认证条目。

## 15.4 验证范围

- 驱动连通、Unicode/decimal/时间类型、事务与隔离、并发、分页、锁/租约、迁移重跑与 DDL 失败、Outbox/审计原子性。
- 数据库故障切换、脑裂隔离、同步副本故障拒写、提交结果未知的业务恢复。
- 插件最小数据库权限、表所有权和动态安装迁移身份。
- 性能基线在共同参考业务模块、统一硬件/数据规模下比较；禁止用未对齐的厂商基准推断真实 MES 性能。

## 15.5 替代路线和审批

- 达梦 Dialect 遇到 P0 能力不一致时，启用 ADR-123 指定的适配路线；不改变四库支持目标，但仍需要新的认证证据。
- 未进入正式认证矩阵的特定数据库或 HA 组合不得在文档、产品或交付中标注为“已支持”。
- 任何改变 GraphQL 主接口、模块化单体、四数据库支持目标等已确认决策，必须通过正式 ADR 替代流程，不允许仅在本章改字。

## 15.6 官方技术资料（仅用于组件事实，不是项目认证证据）

- Kysely 官方 Dialect 接口：https://kysely-org.github.io/kysely-apidoc/interfaces/Dialect.html
- Kysely 官方数据库内置支持：https://www.kysely.dev/docs/getting-started
- Kysely 迁移适配：https://kysely-org.github.io/kysely-apidoc/interfaces/DialectAdapter.html
- 达梦 Node.js dmdb：https://eco.dameng.com/document/dm/zh-cn/pm/nodejs-rogramming-guide
- Zod JSON Schema：https://zod.dev/json-schema

**待补充：** Fastify、Yoga、GraphQL Tools 的精确版本及集成验证、数据库和驱动的已认证版本表。暂不猜测可用版本号。
