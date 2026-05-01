# Operation Point Library

Select 8-15 operation points per Level-3 function from the groups below. Organize selected points into coherent groups in the description.

**Minimum coverage rule:** maintenance + retrieval + audit trail. For task/pipeline types, also add exception compensation.

---

## Type A: Management/Config (管理台/配置类)

Rules, strategies, resources, accounts, permissions, configuration items.

**Maintenance Group:**
- 创建 / 编辑 / 复制 / 禁用 / 启用 / 归档 / 恢复 / 批量更新字段

**Retrieval Group:**
- 列表展示 / 详情查看 / 分页 / 排序 / 多条件筛选 / 模糊搜索 / 保存筛选条件

**Batch & Import/Export Group:**
- 批量导入 / 批量导出 / 批量启停 / 批量标签分组 / 批量校验

**Validation & Preview Group:**
- 字段校验 / 依赖校验 / 冲突检测 / 命中预览（模拟试跑）/ 风险提示

**Permission & Scope Group:**
- 可见范围配置 / 角色授权 / 操作权限 / 数据范围隔离 / 敏感字段保护

**Audit Trail Group:**
- 变更记录 / 操作日志 / 版本记录 / 审批记录

---

## Type B: Template (模板类)

Custom templates, report templates, field mapping templates. Must be "thicker" — at minimum cover version capabilities.

- 模板结构维护（字段、校验规则、默认值、映射关系）
- 模板版本生成 / 版本列表 / 版本对比 / 差异摘要
- 指定版本回滚 / 恢复
- 模板发布 / 生效范围
- 引用关系查看（被哪些规则/任务/报表引用）
- 历史统计展示（版本变更次数、引用次数）

---

## Type C: Task (任务类)

Dispatch/flow/execute/collect. Must write "dispatch + flow + product collection", otherwise reads like a process step.

**Dispatch & Flow Group:**
- 创建 / 配置 / 派发 / 领取（认领）/ 转派 / 退回 / 催办 / 节点流转

**Execution & Progress Group:**
- 开始 / 暂停 / 继续 / 终止 / 进度更新 / 节点状态 / 处理耗时统计

**Result & Collection Group:**
- 提交结果 / 验收 / 回写 / 入库 / 产物生成（报告、数据包、记录）

**Exception Compensation Group:**
- 失败原因记录 / 失败重试 / 补采 / 补跑 / 断点续跑 / 异常回收

---

## Type D: Backend Data Pipeline (后台数据链路类)

Collection, recognition, detection, storage. For modules without visible UI buttons — write pipeline actions.

- 数据来源配置（增量/全量、触发/定时）
- 采集 / 解析（格式识别、字段抽取、分片/分块）
- 识别 / 检测（质量检测、敏感识别、异常标记、规则命中记录）
- 入库 / 索引 / 元数据登记 / 状态回写
- 批次记录、失败原因、补采/重跑/断点续跑

---

## Type E: Dashboard/Screen (看板/大屏类)

Must cover three categories of operations:

**Display Operations Group:**
- 按维度展示 / 筛选 / 排序 / 钻取 / 趋势查看 / 明细下钻 / 导出

**Backend Processing Group:**
- 指标口径计算 / 聚合 / 映射 / 分层 / 刷新频率 / 延迟提示

**Progress Linkage Group:**
- 关联任务 / 链路批次进度 / 显示节点状态 / 异常数量 / 卡点定位

**Strong Rule:** One classification dimension (with different data/metrics) = one independent function point. Do NOT repeat the same data with multiple classifications.

---

## Type F: Operations/Growth Incentive (运营/增长激励类)

- 规则配置（条件、口径、周期、范围、对象）
- 规则下发 / 启停 / 变更留痕
- 命中记录展示 / 执行记录 / 结算记录
- 异常命中处理 / 回收 / 纠偏

---

## Quick-Reference: Common Verbs

创建、编辑、复制、启用、禁用、归档、恢复、发布、撤回、回滚、对比、预览、校验、导入、导出、批量处理、筛选、排序、分页、钻取、下钻、派发、领取、转派、退回、催办、验收、回写、入库、重试、补采、重跑、断点续跑、联动、通知、记录、追踪

## Quick-Reference: Common Audit Fields

操作人、时间戳、变更前后差异、版本号、生效范围、引用对象、任务批次、节点状态、失败原因、结果码、处理耗时
