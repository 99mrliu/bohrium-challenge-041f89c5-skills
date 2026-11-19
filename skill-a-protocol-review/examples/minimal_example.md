# 最小调用示例（示意，非正式案例结果）

> 本示例仅说明接口与流程形态；其中文献与数字均为虚构示意，不代表任何真实案例的运行结果。

## 输入

- `/input/task.md`："评估提案『用图神经网络预测 X 材料带隙』的创新性与可行性，文献集见附件。"
- `/input/case.json`：`{"case_id":"demo-001","output_contract":{"case_id":"...","status":"...","problem_statement":"...","comparison":"...","novelty_assessment":"...","feasibility":"...","uncertainty":"...","sources":"..."}}`
- `/input/papers/`：8 篇 PDF。

## 调用方式

Agent 加载本 Skill 后无需额外指令，直接按 SKILL.md 六阶段执行：先写 result.json 骨架，再依次产出 question_frame.md → protocol.md → screening_log.md → evidence_matrix.md → synthesis.md，最后回填 result.json。

## 示意输出（截选，已标注为示例）

```json
{
  "case_id": "demo-001",
  "status": "partial",
  "problem_statement": "在 X 类无机材料上，GNN 相比描述符+梯度提升基线是否降低带隙预测 MAE，可通过同分布测试集 MAE 对比检验。【示例】",
  "novelty_assessment": "主张'首次将 GNN 用于 X 材料带隙'：已被覆盖（证据矩阵 R3，该文 2023 年已做同任务）；差异点仅在特征构造，判为部分覆盖。【示例】",
  "feasibility": "有条件可行：数据前提满足（R2 报告公开数据集 4k 条）；算力前提为假设（输入未提供算力信息，标[假设]）。【示例】",
  "uncertainty": "纳入文献仅 5 篇且均来自输入文献集，'未见覆盖'类判断限于此边界；2 篇 PDF 解析失败已登记。【示例】"
}
```
