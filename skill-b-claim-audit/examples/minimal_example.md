# 最小调用示例（示意，非正式案例结果）

> 本示例仅说明接口与产物形态；文献、判定与数字均为虚构示意，不代表任何真实案例的运行结果。

## 输入

- `/input/task.md`："评估以下提案的创新性：『我们首次提出用多模态大模型审校 Y 领域论文图表，预期将审校准确率提升 30%』，并对照附件文献。"
- `/input/case.json`：`{"case_id":"demo-101","output_contract":{"case_id":"...","status":"...","claims":"...","novelty_boundaries":"...","counter_evidence":"...","feasibility":"...","uncertainty":"...","sources":"..."}}`
- `/input/papers/`：6 篇 PDF。

## 调用方式

Agent 加载本 Skill 后按 SKILL.md 七阶段执行：result.json 骨架 → claim_ledger.md → nearest_neighbor 表 → 逐条判定与边界声明 → 反证登记 → 问题定义与可行性对账 → 收口回填。

## 示意输出（截选，已标注为示例）

```json
{
  "case_id": "demo-101",
  "status": "success",
  "claims": [
    {
      "id": "C1",
      "statement": "用多模态大模型审校 Y 领域论文图表",
      "category": "场景迁移",
      "verdict": "partially_covered",
      "nearest_neighbors": ["W1:paper3.pdf p.2 §1（L2：图表审校任务相同，领域不同）"],
      "boundary": "主张 C1 超出 W1 之处仅在应用领域（Y 领域）；该差异可通过在 Y 领域论文集上的对照实验验证；此判断在输入 6 篇文献范围内成立。【示例】"
    },
    {
      "id": "C2",
      "statement": "审校准确率提升 30%",
      "category": "结论修正",
      "verdict": "undeterminable",
      "boundary": "输入文献未报告 Y 领域的审校基线准确率，缺口=基线数据；补足后按 C2 对账。【示例】"
    }
  ],
  "counter_evidence": "CE1：paper5.pdf p.4 报告多模态模型在小样本领域审校上低于规则法，与 C2 预期方向冲突；取舍：C2 降级为 undeterminable。【示例】"
}
```
