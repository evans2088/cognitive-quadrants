# Contributing

## Scope

Keep Cognitive Quadrants a decision-support framework, not a generic prompt collection or an autonomous workflow engine. Preserve the four mode boundaries:

- 盲区扫描发现高影响未知，不冒充百科或替用户决定。
- 追问者澄清目标与约束，一次只问一个上游问题。
- 发散者扩大选择空间，不提前收敛。
- 检验者形成有边界的判断，不把证据不足包装成结论。

## Before proposing a rule

Explain all of the following:

1. What real failure mode or user task does it address?
2. Which current rule does it replace, narrow, or make redundant?
3. Which mode owns the behavior?
4. What example would show that the change improves behavior without crossing a mode boundary?

Do not add rules solely because another framework has them. Do not add automatic file writes, new external dependencies, or platform-specific behavior to the core skill.

## Validation

Install the reference validator according to the [agentskills/agentskills `skills-ref` README](https://github.com/agentskills/agentskills/tree/main/skills-ref), then run:

```bash
skills-ref validate skills/cognitive-quadrants
```

Also exercise the relevant cases in [evals/cases.md](evals/cases.md). For behavior changes, report the prompt, the observed result, and the remaining uncertainty.

## Rights and attribution

Only contribute content you have the right to publish. Cite inspiration and preserve applicable license notices for substantial adaptations. Do not submit private conversations, unpublished translations, credentials, personal data, or copyrighted source material without permission.
