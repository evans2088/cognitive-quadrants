# Contributing

## Scope

Keep Cognitive Quadrants a decision-support framework, not a generic prompt collection or an autonomous workflow engine. Preserve the four mode boundaries:

- 盲区扫描发现高影响未知，不冒充百科或替用户决定。
- 追问者澄清目标与约束，一次只问一个上游问题。
- 发散者扩大选择空间，不提前收敛。
- 检验者形成有边界的判断，不把证据不足包装成结论。

任务定向是四个模式之前的路由层，不是第五种模式。它可以决定由助手主导生成方向，或决定先检验已有方案，但不能改变四个模式的职责边界。

## Three-layer architecture

Keep the project in three layers with different admission standards:

1. **Design theory:** maintainers may keep private design rationale explaining the framework's system boundary and open hypotheses. It is not a runtime dependency, a public package dependency, or required context for external contributors.
2. **Runtime protocol:** `SKILL.md` and its references contain only stable, executable rules that change behavior in a recurring or high-impact way.
3. **Evaluation and evolution:** public behavioral cases, reproducible evidence included with a contribution, real-task failures, and the changelog determine whether a runtime change actually helps. Raw discussions, detailed forward-test logs, and private audit records remain maintainer-only.

An external insight may enter design theory before a production failure is observed. It must not enter the runtime protocol merely because the theory is compelling. Route it through:

> external insight → design hypothesis → positive and negative evals → smallest runtime change → regression and forward test

When a principle is promoted to runtime, update the public runtime rule and its behavioral case. Maintainers separately update any private rationale; contributors do not need access to it. Do not make Agents load design theory by default.

## Before proposing a rule

Explain all of the following:

1. What real failure mode or user task does it address?
2. Which current rule does it replace, narrow, or make redundant?
3. Which mode owns the behavior?
4. What example would show that the change improves behavior without crossing a mode boundary?

Do not add rules solely because another framework has them. Do not add automatic file writes, new external dependencies, or platform-specific behavior to the core skill.

新增参考文档前，先确认现有文件无法清晰承载该行为；新文件必须从 `SKILL.md` 或其直接引用的 reference 可达，并说明它解决的具体失败模式。不要在仓库外维护另一份规则副本。

对“理论更完整但运行规则可能过载”的改动，优先把解释留在设计理论，把行为压缩成最小运行约束。减法门也要检查反向风险：不能因为现有规则“似乎能覆盖”就忽略稳定、可复现的行为缺口。

## Validation

Install the reference validator according to the [agentskills/agentskills `skills-ref` README](https://github.com/agentskills/agentskills/tree/main/skills-ref), then run:

```bash
skills-ref validate skills/cognitive-quadrants
```

Also exercise the relevant cases in [evals/cases.md](evals/cases.md). For behavior changes, report the prompt, the observed result, and the remaining uncertainty.

涉及任务定向、反馈纠偏、策略探索或已有方案检验的改动，必须至少回归对应的“用户没有答案”“低价值反馈”“范围纠偏”和“已有方案检验”案例；不能只用 frontmatter 或 Markdown 结构校验代替行为验证。

涉及模式路由、隐性判断、证据边界、停止条件或长期沉淀的改动，还必须同时测试：

- 正例：新增行为应当触发的场景；
- 反例：相似但不应触发、升级、持久化或切换模式的场景；
- 独立前向测试：由未参与规则编写的 Agent 直接面对原始用户提示；
- 既有行为回归：确认四个模式边界、模式推荐和按需持久化没有被新理论扩大。

## Minimal public surface and privacy

Only add or change files that are necessary for the public runtime, installation and usage guidance, compatibility, behavioral evaluation, licensing and attribution, or release notes. Do not add raw conversations, internal design or audit notes, local workflow rules, exploratory research, or full test logs to the repository.

Before opening a PR, stage an explicit file list and review both the staged names and content. Remove secrets, local absolute paths, machine usernames, personal contact or account identifiers, private organization or client details, unpublished material, and internal-only links. Anonymize examples without changing their behavioral meaning. If safe redaction would make a file misleading, exclude the file and explain the limitation instead.

## Rights and attribution

Only contribute content you have the right to publish. Cite inspiration and preserve applicable license notices for substantial adaptations. Do not submit private conversations, unpublished translations, credentials, personal data, or copyrighted source material without permission.
