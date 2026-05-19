---
name: mini-app-evaluator
description: Evaluate and prioritize mini web app ideas with a six-dimension weighted rubric for lead-generating Web Demo / 小微应用 decisions. Use when Codex needs to score one selected app idea, judge whether it is worth building, compare or rank a list of candidate mini app ideas, select the top 3 or top 5 most suitable options, or explain risks around spreadability, immediate user value, lead capture, technical feasibility, quality control, and follow-up conversion.
---

# Mini App Evaluator

## Core Rule

Read `references/evaluation-rubric.md` before scoring. Use it as the source of truth for dimensions, weights, score meanings, decision bands, and veto rules.

This skill supports two common modes:

- **Single idea evaluation**: Score one chosen topic/app idea and decide whether it is worth building.
- **List screening**: Score multiple candidate ideas, apply veto rules, rank them, and recommend the top 3/top 5 or the requested number of options.

## Workflow

1. Identify the mode from the user request.
2. Normalize each idea into a compact scenario brief:
   - `场景名称`
   - `一句话描述`
   - `目标用户`
   - `输入`
   - `输出`
   - `传播 hook`
   - `技术依赖`
   - `留资时机`
3. If key information is missing, make light assumptions for quick screening. Ask only when the missing detail would change the decision, especially data availability, target user, output shape, or whether contact capture is allowed.
4. Score each dimension from 1 to 5 using integer scores:
   - 传播适配度, weight 25%
   - 即时感知价值, weight 20%
   - 线索获取能力, weight 20%
   - 技术可行性, weight 15%
   - 交付质量可控度, weight 10%
   - 后续转化路径, weight 10%
5. Calculate weighted score:

```text
weighted_score =
  传播适配度 * 0.25 +
  即时感知价值 * 0.20 +
  线索获取能力 * 0.20 +
  技术可行性 * 0.15 +
  交付质量可控度 * 0.10 +
  后续转化路径 * 0.10
```

6. Apply veto rules after scoring. A veto overrides the weighted score.
7. Return a decision that is useful for action, not just a number.

## Output Rules

For a single idea, lead with the decision:

- `优先做`: weighted score >= 4.0 and no veto.
- `值得做`: weighted score 3.0-3.9 and no veto.
- `暂缓`: weighted score 2.0-2.9, unless one dimension scores 5 and the shortcoming is fixable.
- `不做`: weighted score < 2.0 or any veto applies.

Then include:

- A compact score table with reasons.
- Veto check result.
- The shortest viable MVP shape.
- The biggest risk and the first validation step.

For list screening:

- State the recommended top options first.
- Show a ranked table with weighted score, decision, veto status, and one-line reason.
- Separate `推荐做`, `可观察`, and `先不做`.
- Explain why the top 3/top 5 are stronger than the rest.
- Suggest how to improve promising but flawed ideas.

## Judgement Style

- Be strict on lead capture, technical feasibility, and quality control. A flashy idea that cannot reliably collect qualified leads is not a strong Web Demo.
- Do not rank by technical ease alone. Prefer ideas with strong spreadability, fast perceived value, and a natural next-step conversation.
- Treat the score as decision support, not false mathematical precision. Give concrete reasons for every 1, 2, or 5.
- If the user is choosing what to build next, recommend the simplest high-score MVP rather than the most ambitious concept.
