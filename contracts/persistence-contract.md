# 四数据库持久化契约 · Draft V0.2

**ADR：** 020、047、049、054～055、086、093、102、105、107、109、112、117、119～124、126～127、129。

## 必须认证的能力

- 稳定类型映射（Unicode、decimal、时间、二进制、主键）、参数化查询、分页与确定性排序。
- 事务开始/提交/回滚、隔离级别、提交结果未知时的查询策略；本地业务+关键审计+幂等记录+Outbox 同事务。
- 版本化迁移锁、DDL 失败恢复、Expand–Migrate–Contract、插件对象所有权与权限。
- Worker 锁/租约及过期保护、Outbox 至少一次投递、接收端去重。
- 关键事务零已确认提交丢失的同步持久化路径及失效时拒写；标准 RTO≤4h、HA≤15m 的场景验证。

## 适配与失败路线

Kysely 优先；`dmdb` 达梦 Dialect 包含 driver/compiler/adapter/introspector 且须验证迁移锁。不能通过时依据 ADR-123 改为受控 dmdb/SQL 后端，公开持久化契约不变。

## 认证条目

每个 `database×databaseVersion×driver×frameworkVersion×deploymentMode` 组合独立记录候选、测试、已认证、过期状态，证据覆盖迁移、并发写入、故障切换、脑裂、提交中断及恢复核验。**当前没有任何已认证条目。**
