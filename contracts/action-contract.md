# 统一业务动作契约规范 · Draft V0.2

**ADR：** 035、044、056、071、080、084、091、095、097、109、121。权威定义为 TypeScript + Zod；协议适配不拥有业务语义。

## 动作定义必须表达

- `actionId`、`actionVersion`、`ownerModule`、`inputSchema`、`resultSchema` 和标准错误语义。
- `resourceScope`（工厂和资源）、`riskClass`、`requiredPermissions`、`approvalPolicy`、`actorKinds`。
- `idempotencyPolicy`、`expectedResourceVersion`、`timeoutPolicy`、`auditClass`、`sideEffects`。
- 数据校验及权限策略由服务器执行，不能以模型或前端给出的策略结果替代。

## 执行不可变次序（规范性）

1. 解析可信身份与工厂上下文；校验输入 Zod Schema；规范化参数并计算摘要。
2. 检查动作授权、限额、风险和审批；审批与动作+参数+资源版本+有效期绑定。
3. 使用稳定请求 ID 查询持久化幂等状态，拒绝相同 ID 不同参数；提交结果未知必须先核查。
4. 开启本地主库事务，执行业务规则和生产状态变更、关键审计、请求执行记录、Outbox（必要时）并原子提交。
5. 仅在持久化保证满足时确认关键成功；否则安全拒写或返回可恢复的不确定状态。
6. GraphQL Mutation / REST / MCP 返回对应的标准化状态；任何协议不得绕开以上步骤。

## Agent 专项

- 动作目录按当前可发现权限过滤，调用时重新授权。
- 长时 Agent 权限撤销阻止其后续新动作；在途事务按业务安全策略处理，已提交效果通过单独补偿动作调整。
- 不将 API tool discovery 缓存当作长期许可证。

## 必测负向用例

越权、跨工厂、参数篡改、审批过期/版本过期、提交结果未知重试、重复幂等键不同参数、权限撤销、新旧协议适配行为不一致。每项必须产生可审计拒绝证据。
