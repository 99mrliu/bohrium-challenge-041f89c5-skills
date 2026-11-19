# claim-centric-novelty-audit

主张对账式的科研创新点边界审计 Skill。把待评估提案拆成原子创新主张，逐条与最近邻已有工作对账，输出带边界的创新性判定。

## 安装与调用

- 安装：本目录作为 Skill 加载（评测环境安装于 `/skills/weekly-skill`）。无代码依赖、无网络要求。
- 调用：Agent 读取 SKILL.md 后按七个阶段执行，无需额外提示。

## 输入 / 输出

- 输入：`/input/task.md`、`/input/case.json`（含 `case_id`、`output_contract`、提案文本）、文献材料。
- 输出：`/app/output/result.json`（case_id + 契约全部字段 + status + sources + uncertainty），以及主张台账、最近邻表、反证登记等过程物证（按契约要求放入 `/app/output`）。

## 方法要点

1. 主张分解：创新陈述 → 原子主张（编号、类别、可判定陈述）；隐含前提单列。
2. 最近邻对账：每条主张按 任务→对象→方法族→指标 逐级放宽找 1–3 篇最近工作；找不到时留查找动作痕迹，措辞限定为"未见覆盖（边界：…）"。
3. 四态判定：covered / partially_covered / not_covered / undeterminable，每条附固定句式边界声明。
4. 反证登记：主动寻找并登记冲突文献，取舍留理由。
5. 派生交付：归并可检验研究问题；可行性前提逐条标 [来源]/[假设]，结论带条件。

## 适用范围与限制

- 适用：含创新陈述的提案评估、投稿前新颖性自查、立项创新性论证。
- 不适用：无创新陈述的纯摘要任务；无需对照已有工作的综述。
- 已知限制：判定强度受输入文献集边界约束，Skill 对每条 not_covered 显式声明边界而非外推。

## 失败处理与自查

异常（无显性创新陈述、文献过少、证据冲突、材料不可读、权限不足、预算将尽）按 SKILL.md 异常处理执行；交付前过 `checklists/audit_checklist.md`。示例见 `examples/minimal_example.md`（示意输出已标注为示例）。

## 维护

版本 1.0（2026-11）。台账与模板为本 Skill 自有资源，可独立复用。
