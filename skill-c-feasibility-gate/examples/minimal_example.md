# 最小调用示例（示意，非正式案例结果）

> 本示例仅说明接口与产物形态；文献、判定与数字均为虚构示意，不代表任何真实案例的运行结果。

## 输入

- `/input/task.md`："提案：6 个月内用公开数据集训练 Z 模型并部署到边缘设备。评估可行性。附件为 5 篇相关文献与约束说明。"
- `/input/case.json`：`{"case_id":"demo-201","constraints":{"deadline_months":6,"gpu":"1×消费级"},"output_contract":{"case_id":"...","status":"...","decision":"...","gates":"...","conditions":"...","risks":"...","uncertainty":"...","sources":"..."}}`

## 调用方式

Agent 加载本 Skill 后按 SKILL.md 七阶段执行：result.json 骨架 → decision_frame.md → premise_ledger.md → gates.md → risk_register.md → baseline_scan.md → 带条件结论回填。

## 示意输出（截选，已标注为示例）

```json
{
  "case_id": "demo-201",
  "status": "success",
  "decision": "conditional-go",
  "gates": {
    "G1_data": {"verdict": "pass", "basis": "Q1[来源:dataset_notes.md §2] 公开数据集 12k 条可下载"},
    "G2_compute": {"verdict": "conditional", "basis": "Q4[假设:pilot 实测] 文献 R3 报告同类训练需 4×A100，与约束 1×消费级相差约一个数量级；缓解=蒸馏小模型+pilot 测耗时"},
    "G4_time": {"verdict": "conditional", "basis": "6 个月窗口内含 2 个月缓冲，依赖 G2 的 pilot 结果"}
  },
  "conditions": ["第 4 周前完成 pilot 训练并实测单轮耗时，超过预算 2 倍则触发降级方案（F2）"],
  "risks": ["F2：全尺寸训练超时→蒸馏小模型，残余风险中"],
  "uncertainty": "部署端延迟无文献数据，记 [假设:第 8 周真机 profiling]。【示例】"
}
```
