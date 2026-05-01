# Common Errors and Corrections

Use this reference during quality review (Step 5) to validate Level-3 output.

## Error 1: Level-3 Name is Verb-Phrase

**Wrong:** 数据下发
**Correct:** 数据分发管理 / 分发通道管理
**Rule:** Level-3 = capability domain; Level-4 = actions like 下发/撤回/重发

---

## Error 2: Description Writes Value Without Operations

**Wrong:** 提升效率、保障安全
**Correct:** 支持规则启停、命中预览、冲突检测、变更留痕、异常回滚
**Rule:** Only write what operations/processes are performed, not abstract benefits.

---

## Error 3: Task Reads Like a Process Step

**Wrong:** 任务执行：执行任务并完成闭环
**Correct:** 任务管理：创建/派发/领取/转派/退回/催办/验收/回写/入库/失败重试
**Rule:** Task type must include dispatch + flow + collection/回写. Otherwise it's just a step.

---

## Error 4: Dashboard Repeats Same Data Under Multiple Classifications

**Wrong:** 按行业/按地区/按部门展示同一指标 stacked as 3 function points
**Correct:** Each dashboard dimension maps to different data sources/metrics/products; OR collapse into one Level-3 with dimensions as Level-4 filters.
**Rule:** One classification dimension with different data/metrics = one independent point. No repetition.

---

## Error 5: Level-3 Name Contains Level-4 Actions

**Wrong:** 规则发布管理, 报表导出管理, 任务新建管理
**Correct:** 规则管理, 报表管理, 任务管理
**Rule:** Level-3 names must NOT contain CRUD, import/export, dispatch/publish, start/stop/approve, execute/re-run, compare/rollback.

---

## Error 6: Description Too Short (< 8 Operations)

**Wrong:** 支持创建、编辑、删除和查询
**Correct:** 支持创建/编辑/复制/禁用/启用/归档/恢复，支持列表展示/详情查看/多条件筛选/模糊搜索，系统自动记录变更日志和操作记录，支持批量导入/导出和数据范围隔离
**Rule:** 8-15 operation points per Level-3. Split into two Level-3 functions if exceeding 18.

---

## Error 7: Missing Audit Trail

**Wrong:** No mention of logs, version records, or change tracking
**Correct:** Include 变更记录 / 操作日志 / 版本记录 / 审批记录
**Rule:** Management/config types must have audit trail coverage.

---

## Error 8: Pipeline Type Missing Exception Handling

**Wrong:** 采集数据并完成入库
**Correct:** 采集/解析/入库，支持批次记录、失败原因记录、补采/重跑/断点续跑
**Rule:** Pipeline type must include input-output/batch/failure reason/retry.

---

## Error 9: Template Type Missing Version Capability

**Wrong:** 支持创建和编辑模板
**Correct:** 支持模板结构维护/版本生成/版本对比/差异摘要/指定版本回滚/引用关系查看
**Rule:** Template type must cover version, comparison, rollback, reference.

---

## Error 10: Dashboard Missing Backend Processing or Progress Linkage

**Wrong:** 支持按多个维度展示数据
**Correct:** 支持按维度展示/筛选/钻取，后台完成指标口径计算/聚合/刷新，关联任务/链路批次进度/显示节点状态/异常数量
**Rule:** Dashboard type must cover display + backend processing + progress linkage.
