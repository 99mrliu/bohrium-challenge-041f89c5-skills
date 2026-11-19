# feasibility-gate-decision-memo

门控式科研选题可行性决策 Skill。把"能不能做成"拆成可核查前提的合取，五道门逐门判定，输出带条件的 go / conditional-go / no-go / indeterminate 结论。

## 安装与调用

- 安装：本目录作为 Skill 加载（评测环境安装于 `/skills/weekly-skill`）。无代码依赖、无网络要求。
- 调用：Agent 读取 SKILL.md 后按七个阶段执行，无需额外提示。

## 输入 / 输出

- 输入：`/input/task.md`、`/input/case.json`（含 `case_id`、`output_contract`、约束场景）、文献与数据说明材料。
- 输出：`/app/output/result.json`（case_id + 契约全部字段 + status + sources + uncertainty），以及前提台账、门判定表、风险登记、参照系扫描等过程物证（按契约要求放入 `/app/output`）。

## 方法要点

1. 决策问题陈述：成功判据、最低可接受结果、终止条件。
2. 前提台账：每条前提三态标记——[来源:定位] / [推断:推理链] / [假设:验证方式]。
3. 五道门：数据、算力、实验条件、时间窗、人员与方法；逐门 pass/conditional/fail/unknown，判定引用前提编号。
4. 风险登记：失败模式、触发信号、影响、具体缓解、残余风险。
5. 参照系：最近工作的数据规模与资源需求扫描；提案差异点回链风险。
6. 带条件结论：go / conditional-go（条件清单）/ no-go（障碍清单）/ indeterminate（缺口清单）。

## 适用范围与限制

- 适用：立项前可行性论证、带约束场景（数据/算力/周期/团队）的选题评估、投稿前可复现性自查。
- 不适用：纯文献综述；无任何资源约束的开放式脑暴。
- 已知限制：约束场景缺失时相应门判 unknown 并全部转假设，结论强度相应降级——这是设计行为而非缺陷。

## 失败处理与自查

异常（约束缺失、文献未报资源、证据冲突、材料不可读、权限不足、预算将尽）按 SKILL.md 异常处理执行；交付前过 `checklists/gate_final_checklist.md`。示例见 `examples/minimal_example.md`（示意输出已标注为示例）。

## 维护

版本 1.0（2026-11）。台账、门表与风险登记模板为本 Skill 自有资源，可独立复用。
