# bohrium-challenge-041f89c5-skills

Bohrium Playground 竞赛题目 challenge-041f89c5「科研选题与创新性评估」的参赛 Skill 作品，包含三个相互独立的方法方向，每个目录是一个完整可独立加载的 Skill bundle：

| 目录 | 方向 | 核心方法 |
|-|-|-|
| `skill-a-protocol-review/` | 协议先行的证据综述流水线 | 问题结构化（PICO 式）→ 检索与纳排协议先于全文阅读冻结 → 筛选留痕 → 带来源定位的证据矩阵 → 综合结论与边界声明 |
| `skill-b-claim-audit/` | 主张对账式创新边界审计 | 提案拆为原子创新主张（方法/数据/场景迁移/结论修正），逐条找最近邻工作、四态覆盖判定、固定句式边界声明、反证登记 |
| `skill-c-feasibility-gate/` | 门控式可行性决策备忘录 | 前提台账三态标记（[来源]/[推断]/[假设]），数据/算力/实验条件/时间窗/人员五道门判定，失败模式登记，带条件的 go/conditional-go/no-go/indeterminate 结论 |

三个 bundle 各自独立、无相互依赖，可单独加载使用。每个 bundle 内含 `SKILL.md`（入口）、`templates/`、`checklists/`、`examples/`（示意输出已标注为示例）与 `README.md`。

运行时契约：输入 `/input/task.md`、`/input/case.json`（含 `case_id` 与 `output_contract`）及科研材料；工作目录 `/app/work`；交付 `/app/output/result.json`（含 `case_id` 与契约全部字段、status、sources、uncertainty）。详见各 bundle 的 README。
