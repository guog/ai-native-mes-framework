# AI Native MES 技术基础框架架构设计规格书

- **文档版本：** V0.2 / Draft（全部 16 章已编制，待架构评审）
- **架构基线：** ADR-001～ADR-130 / Accepted，不得在本文中擅自改变。
- **验证状态：** 规格文档完成；技术 PoC、真实四数据库集成、高可用故障注入与安全/性能认证均**未执行**。
- **边界：** 本项目当前仅编制架构规格，未开发 MES 程序代码。

## 正式规格书 16 章

1. [总体说明](01-context.md) — 已编制，待评审
2. [质量属性与架构约束](02-quality-attributes.md) — 已编制，待评审
3. [系统总体架构](03-system-architecture.md) — 已编制，待评审
4. [最小内核与模块体系](04-kernel-and-modules.md) — 已编制，待评审
5. [动态插件](05-plugin-runtime.md) — 已编制，待评审
6. [GraphQL 与统一业务动作](06-graphql-and-actions.md) — 已编制，待评审
7. [多数据库持久化与事务](07-persistence.md) — 已编制，待评审
8. [工厂自治与集团同步](08-factory-sync.md) — 已编制，待评审
9. [持久化任务与 Worker](09-worker.md) — 已编制，待评审
10. [AI Native 产品运行时](10-ai-runtime.md) — 已编制，待评审
11. [Vue 与声明式 UI](11-frontend.md) — 已编制，待评审
12. [身份、安全与审计](12-security-audit.md) — 已编制，待评审
13. [部署、运维与可靠性](13-operations-reliability.md) — 已编制，待评审
14. [AI Native 软件工程体系](14-ai-native-engineering.md) — 已编制，待评审
15. [技术选型与兼容性](15-technology-compatibility.md) — 已编制，待评审
16. [质量验证、风险与实施路线](16-validation-roadmap.md) — 已编制，待评审

## 附属规范

- [ADR-001～ADR-130 规范化摘要](../adr/baseline-v1.md)（已确认决策摘要，非逐字访谈）
- [ADR 全量追踪索引](adr-traceability.md)
- [公开契约规范](../contracts/README.md)
- [质量风险记录](../quality/risk-register.md)
- [验证计划](../verification/verification-plan.md)
- [验收用例集](../verification/acceptance-cases.md)
- [认证组合模板](../verification/certification-matrix.md)
- [架构图](../diagrams/README.md)

## 规范解释

- **ADR 强制约束**：已确认方向与系统行为，不得在下级规范中变更。
- **规格草案**：对 ADR 的技术表达/约束细化；不构成新增 ADR，须经架构评审方可冻结。
- **待验证风险**：路线已选但没有工程证据；任何项目不得据此宣称通过认证。
- **实现阶段**：只有取得用户另行批准后方可开始写代码、部署或真实数据库测试。

## 重要设计不变量

1. 工厂本地生产事务权威与离线自治；集团侧只有异步指令和汇总视图。
2. 关键业务事务、执行记录、审计和必要 Outbox 在同库事务提交；已确认关键事务在已认证故障范围内零丢失。
3. GraphQL 作为主业务 API，业务动作契约为唯一写操作权威；REST/MCP 只是适配入口。
4. 最小内核、静态依赖无环、插件可信等级分离、生产关键写入受控。
5. AI Runtime 与 MES 核心独立；Agent 权限、审批、幂等和审计由 MES 确定性机制执行。
6. PostgreSQL、SQL Server、MySQL、达梦为初期正式支持目标，具体版本和部署组合须经认证。
