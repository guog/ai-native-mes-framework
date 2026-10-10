# 全量 ADR 与规格章节追踪矩阵（V0.2）

**说明：** 下列是每章重点 ADR 范围；同一 ADR 可跨章引用；本文件同时检查所有 130 项均至少被映射一次。机器可读完整映射见 `../adr/traceability.json`。

## 第 1 章 · 总体说明

- **路径：** [`docs/01-context.md`](01-context.md)
- **关联 ADR：** ADR-001, ADR-002, ADR-003, ADR-004, ADR-005, ADR-006, ADR-007, ADR-012, ADR-013, ADR-014, ADR-015, ADR-021, ADR-058, ADR-065, ADR-066, ADR-098, ADR-100, ADR-106

## 第 2 章 · 质量属性与架构约束

- **路径：** [`docs/02-quality-attributes.md`](02-quality-attributes.md)
- **关联 ADR：** ADR-006, ADR-038, ADR-040, ADR-046, ADR-047, ADR-057, ADR-070, ADR-091, ADR-098, ADR-099, ADR-107, ADR-108, ADR-109, ADR-112, ADR-113, ADR-114, ADR-119, ADR-120, ADR-125, ADR-126, ADR-128, ADR-129, ADR-130

## 第 3 章 · 系统总体架构

- **路径：** [`docs/03-system-architecture.md`](03-system-architecture.md)
- **关联 ADR：** ADR-002, ADR-007, ADR-008, ADR-011, ADR-013, ADR-014, ADR-016, ADR-022, ADR-023, ADR-024, ADR-026, ADR-027, ADR-030, ADR-031, ADR-038, ADR-058, ADR-063, ADR-065, ADR-066, ADR-074, ADR-098, ADR-101, ADR-103

## 第 4 章 · 最小内核与模块体系

- **路径：** [`docs/04-kernel-and-modules.md`](04-kernel-and-modules.md)
- **关联 ADR：** ADR-007, ADR-009, ADR-017, ADR-018, ADR-024, ADR-025, ADR-032, ADR-033, ADR-034, ADR-053, ADR-054, ADR-058, ADR-059, ADR-060, ADR-061, ADR-062, ADR-073, ADR-087, ADR-100

## 第 5 章 · 动态插件

- **路径：** [`docs/05-plugin-runtime.md`](05-plugin-runtime.md)
- **关联 ADR：** ADR-009, ADR-017, ADR-018, ADR-024, ADR-025, ADR-028, ADR-032, ADR-033, ADR-034, ADR-042, ADR-043, ADR-045, ADR-048, ADR-055, ADR-059, ADR-060, ADR-062, ADR-078, ADR-079, ADR-082, ADR-083, ADR-088, ADR-089, ADR-093, ADR-096, ADR-104, ADR-105, ADR-110, ADR-111, ADR-130

## 第 6 章 · GraphQL 与统一业务动作

- **路径：** [`docs/06-graphql-and-actions.md`](06-graphql-and-actions.md)
- **关联 ADR：** ADR-010, ADR-019, ADR-026, ADR-035, ADR-036, ADR-044, ADR-056, ADR-066, ADR-068, ADR-069, ADR-070, ADR-071, ADR-072, ADR-078, ADR-079, ADR-080, ADR-084, ADR-085, ADR-088, ADR-089, ADR-090, ADR-091, ADR-095, ADR-115, ADR-116

## 第 7 章 · 多数据库持久化与事务

- **路径：** [`docs/07-persistence.md`](07-persistence.md)
- **关联 ADR：** ADR-015, ADR-020, ADR-025, ADR-029, ADR-040, ADR-047, ADR-049, ADR-054, ADR-055, ADR-060, ADR-086, ADR-091, ADR-093, ADR-102, ADR-105, ADR-107, ADR-109, ADR-112, ADR-113, ADR-114, ADR-117, ADR-118, ADR-119, ADR-120, ADR-121, ADR-122, ADR-123, ADR-124, ADR-126, ADR-127, ADR-129

## 第 8 章 · 工厂自治与集团同步

- **路径：** [`docs/08-factory-sync.md`](08-factory-sync.md)
- **关联 ADR：** ADR-008, ADR-014, ADR-016, ADR-022, ADR-023, ADR-030, ADR-031, ADR-039, ADR-040, ADR-041, ADR-049, ADR-050, ADR-051, ADR-052, ADR-067, ADR-076, ADR-097, ADR-099, ADR-121

## 第 9 章 · 持久化任务与 Worker

- **路径：** [`docs/09-worker.md`](09-worker.md)
- **关联 ADR：** ADR-034, ADR-040, ADR-045, ADR-049, ADR-061, ADR-074, ADR-082, ADR-092, ADR-103, ADR-118, ADR-121, ADR-122

## 第 10 章 · AI Native 产品运行时

- **路径：** [`docs/10-ai-runtime.md`](10-ai-runtime.md)
- **关联 ADR：** ADR-004, ADR-010, ADR-019, ADR-026, ADR-027, ADR-028, ADR-035, ADR-036, ADR-037, ADR-044, ADR-056, ADR-065, ADR-071, ADR-080, ADR-084, ADR-087, ADR-095, ADR-096, ADR-097, ADR-103, ADR-110

## 第 11 章 · Vue 与声明式 UI

- **路径：** [`docs/11-frontend.md`](11-frontend.md)
- **关联 ADR：** ADR-005, ADR-032, ADR-048, ADR-063, ADR-064, ADR-066, ADR-069, ADR-070, ADR-072, ADR-075, ADR-081, ADR-085, ADR-088, ADR-090, ADR-094

## 第 12 章 · 身份、安全与审计

- **路径：** [`docs/12-security-audit.md`](12-security-audit.md)
- **关联 ADR：** ADR-018, ADR-019, ADR-021, ADR-026, ADR-036, ADR-039, ADR-041, ADR-042, ADR-043, ADR-044, ADR-048, ADR-052, ADR-055, ADR-056, ADR-062, ADR-067, ADR-072, ADR-077, ADR-083, ADR-084, ADR-095, ADR-097, ADR-109, ADR-110, ADR-130

## 第 13 章 · 部署、运维与可靠性

- **路径：** [`docs/13-operations-reliability.md`](13-operations-reliability.md)
- **关联 ADR：** ADR-006, ADR-013, ADR-014, ADR-016, ADR-023, ADR-038, ADR-046, ADR-057, ADR-067, ADR-077, ADR-098, ADR-099, ADR-105, ADR-107, ADR-108, ADR-109, ADR-112, ADR-113, ADR-114, ADR-119, ADR-120, ADR-124, ADR-126, ADR-129

## 第 14 章 · AI Native 软件工程体系

- **路径：** [`docs/14-ai-native-engineering.md`](14-ai-native-engineering.md)
- **关联 ADR：** ADR-004, ADR-005, ADR-028, ADR-037, ADR-059, ADR-080, ADR-081, ADR-087, ADR-096, ADR-100, ADR-104

## 第 15 章 · 技术选型与兼容性

- **路径：** [`docs/15-technology-compatibility.md`](15-technology-compatibility.md)
- **关联 ADR：** ADR-012, ADR-015, ADR-020, ADR-029, ADR-047, ADR-066, ADR-086, ADR-100, ADR-101, ADR-102, ADR-112, ADR-115, ADR-116, ADR-117, ADR-118, ADR-123, ADR-124, ADR-127, ADR-129

## 第 16 章 · 质量验证、风险与实施路线

- **路径：** [`docs/16-validation-roadmap.md`](16-validation-roadmap.md)
- **关联 ADR：** ADR-006, ADR-037, ADR-038, ADR-040, ADR-046, ADR-047, ADR-057, ADR-087, ADR-098, ADR-099, ADR-106, ADR-107, ADR-108, ADR-109, ADR-112, ADR-113, ADR-114, ADR-119, ADR-120, ADR-121, ADR-122, ADR-123, ADR-124, ADR-125, ADR-126, ADR-127, ADR-128, ADR-129, ADR-130


## 覆盖检查

- ADR 总数：130
- 已映射：130
- 未映射：无
