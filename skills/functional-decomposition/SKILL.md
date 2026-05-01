---
name: functional-decomposition
description: Generate Level-3 (三级) functional names and descriptions for product capability trees / PRD feature lists. Use when the user provides Level-1 and Level-2 functions and needs to decompose them into Level-3 functions with proper names and descriptions following software product management standards. Each Level-2 function decomposes into 5 Level-3 functions. Outputs noun-structured capability unit names and operation-centric descriptions.
---

# Functional Decomposition

Generate Level-3 function names and descriptions following product capability tree / PRD standards.

## Core Rules

**Level-3 Function = Capability Unit** (manageable page, task domain, backend pipeline, dashboard, or integration surface). **NOT** a workflow step, slogan, or repeated classification.

**Naming Rules**
- Noun-phrase only (no "新建/下发/执行/导出"). 6-10 characters preferred.
- Patterns: `{对象}+管理` (模板管理), `{机制}+管理` (版本管理), `{域}+分析/监控` (行为分析), `{链路/通道}+管理` (采集链路管理), `{载体}+看板/大屏` (采集看板), `{集成}+管理` (接口管理).
- Forbidden: 新建任务, 导出报表, 数据下发, 执行采集, 提交审批 — these are Level-4 actions.

**Description Rules (4-Section Method)**
Write 1-3 sentences combining all applicable sections:
1. **Object/Scope**: what objects this manages, coverage
2. **User Operations**: grouped operation points (8-15 per Level-3)
3. **System Auto-Actions**: backend processing (采集/校验/联动/记录)
4. **Output & Exception**: output/入库/报告/日志; failure reason, retry/rollback/compensation

**Level-3 vs Level-4 Boundary**
- Level-3 names must NOT contain: CRUD, import/export, dispatch/publish, start/stop/approve, execute/re-run, compare/rollback
- Level-4 contains the actual buttons/interfaces: 新增, 编辑, 导入, 发布, 下发, 回滚, 重跑

## Workflow

Decompose a Level-2 function into 5 Level-3 functions:

1. **Determine Level-3 types** from the 6 types: 管理台/配置类, 模板类, 任务类, 后台数据链路类, 看板/大屏类, 运营/增长激励类
2. **Identify object & boundary**: what is the object? inputs/outputs? associations?
3. **Select 8-15 operation points** from the operation library (see references/operation-library.md for the full menu). At minimum cover: maintenance + retrieval + audit trail (add exception compensation for task/pipeline types)
4. **Write descriptions in platform-neutral language**: use "本项需要建设…模块，该模块支持…包括…" pattern
5. **Run self-check** against the 12-item checklist below
6. **Attach Level-4 split suggestions** if applicable

## Output Format

For each Level-3 function, output:

```
【三级功能名称】Xxxx管理/Xxxx分析/Xxxx看板
【三级功能描述】本项需要建设[对象]管理模块，该模块支持[对象]的[维护类操作]、
[检索类操作]，系统自动完成[后台处理]，输出[产物]并记录[异常处理方式]。
【可拆四级建议】[具体按钮/接口/后台动作]
```

## Delivery Checklist (12 Items)

1. Name is noun-phrase, independent (no 新建/下发/执行/导出)
2. Description defines object and scope
3. Sufficient operation points listed (>=8, grouped reasonably)
4. Operations are verifiable (page button / interface / backend action)
5. Includes query/filter/detail view (required for management types)
6. Includes batch or import/export (preferred for management types)
7. Includes change audit / log records (required for management types)
8. Task type: includes dispatch/flow/collection/入库 or 回写 (required)
9. Pipeline type: includes input-output/batch/failure reason/retry (required)
10. Template type: includes version/comparison/rollback/reference (required)
11. Dashboard type: includes display + backend processing + progress linkage (required)
12. No empty value slogans (提升效率/赋能/保障 with no concrete operations)

## Reference Files

- **references/operation-library.md**: Full operation-point menu organized by the 6 module types. Read this during Step 3 to select appropriate operation points.
- **references/common-errors.md**: Common mistakes and correction examples. Read this during Step 5 for quality review.
