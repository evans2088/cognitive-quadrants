# Contributing

## Scope

Keep Cognitive Quadrants a decision-support framework, not a generic prompt collection or an autonomous workflow engine. Preserve the four mode boundaries:

- 盲区扫描发现高影响未知，不冒充百科或替用户决定。
- 追问者澄清目标与约束，一次只问一个上游问题。
- 发散者扩大选择空间，不提前收敛。
- 检验者形成有边界的判断，不把证据不足包装成结论。

任务定向是四个模式之前的路由层，不是第五种模式。它可以决定由助手主导生成方向，或决定先检验已有方案，但不能改变四个模式的职责边界。

## Before proposing a rule

Explain all of the following:

1. What real failure mode or user task does it address?
2. Which current rule does it replace, narrow, or make redundant?
3. Which mode owns the behavior?
4. What example would show that the change improves behavior without crossing a mode boundary?

Do not add rules solely because another framework has them. Do not add automatic file writes, new external dependencies, or platform-specific behavior to the core skill.

新增参考文档前，先确认现有文件无法清晰承载该行为；新文件必须从 `SKILL.md` 或其直接引用的 reference 可达，并说明它解决的具体失败模式。不要在仓库外维护另一份规则副本。

## Validation

Install the reference validator according to the [agentskills/agentskills `skills-ref` README](https://github.com/agentskills/agentskills/tree/main/skills-ref), then run:

```bash
skills-ref validate skills/cognitive-quadrants
```

Also exercise the relevant cases in [evals/cases.md](evals/cases.md). For behavior changes, report the prompt, the observed result, and the remaining uncertainty.

涉及任务定向、反馈纠偏、策略探索或已有方案检验的改动，必须至少回归对应的“用户没有答案”“低价值反馈”“范围纠偏”和“已有方案检验”案例；不能只用 frontmatter 或 Markdown 结构校验代替行为验证。

## Rights and attribution

Only contribute content you have the right to publish. Cite inspiration and preserve applicable license notices for substantial adaptations. Do not submit private conversations, unpublished translations, credentials, personal data, or copyrighted source material without permission.
