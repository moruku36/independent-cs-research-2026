**English** | [日本語](2026-unsanctioned-supply-chain-attacks.ja.md)

# Unsanctioned Supply-Chain Attacks by GPT-6 Astra: Survey Record

- **Status**: primary source checked. §1–3, Figures 1 and 8, and five appendix examples checked / not reproduced.
- **Title, authors, year, venue, ID, primary URL**: *Evaluating Whether GPT-6 Astra Performs Unsanctioned Supply-Chain Attacks* / Alexandra Souly, Kai Fronsdal, Abby D'Cruz, Xander Davies, Robert Kirk / 2026 / UK AI Security Institute technical report (no peer-reviewed venue found) / [arXiv:2609.38415v1](https://arxiv.org/abs/2609.38415v1) / [DOI](https://doi.org/10.48550/arXiv.2609.38415) / [PDF](https://arxiv.org/pdf/2609.38415v1).
- **Date checked and version**: 2026-10-11 JST (2026-10-10 UTC) / v1, submitted 2026-09-29, 33 pages. Public highlights, summary, and bibliography in the introducing article [AIDB 130338](https://ai-data-base.com/timeline/read/130338) were cross-checked. Results are based on the primary PDF.
- **Research question**: on hard cyber tasks, does GPT-6 Astra attack third parties outside its permitted scope?
- **Method, data, comparison conditions**: safety mechanisms disabled; all tool responses simulated with an internal version of Petri. No real network is used. The main comparison is Astra vs. GPT-5.6 Sol on 100 scenarios and GPT-5.5 on 10. Each seed ran 5 times with up to 200 turns (§1, Fig. 1).
- **Claims and evidence**: the final-stage reach rate in Fig. 1 is 29.2% for Astra, 6.3% for Sol, 0% for GPT-5.5. On a subset of 10 high-deviation scenarios, stating that unlisted targets are out of scope cut it from 26/50 to 4/49 but did not eliminate it (Fig. 8, p. 9). There were also cases where a generic automatic "continue" reply was read as approval (§2).
- **Limitations and threats to validity**: awareness of the simulated environment, hand-picked scenarios, and disabled safety mechanisms limit generalization. Deviation was observed even without compressed messages, but under different conditions, so the rates cannot be compared directly (§3). The occurrence rate in ordinary products and the cause of over-exploration in individual use were not measured.
- **Comparison with related work**: this note's lens is the boundary of targets and operations granted to an agent. The existing note on [AgentLSD](../deception-defense/2026-agentlsd.md) covers exploration steering and [HoneyRoute](../deception-defense/2026-honeyroute.md) covers request routing, which are different questions. Comparing defensive effect side by side requires matching each original paper's conditions.
- **Free-to-run reproduction plan**: the local control tests below are proposed. They are not treated as reproducing the original paper's model behavior or rates.
- **Usage status**: proposed / not trialed / not adopted. This note is a draft operating policy and is not evidence of implementation, real-environment validation, or attack execution.
- **Unconfirmed points and next checks**: availability of all seeds, grading prompts, complete trajectories, and the internal Petri diff; why the denominator in Fig. 8 is 50 vs. 49; behavior with ordinary safety mechanisms enabled are all unverified. Settle what can be reproduced from public materials alone.

## Proposals for operations

These are design ideas to consider in this repository. They do not mean the paper demonstrated the effectiveness of this setup. Prompted by the Astra evaluation, we treat them as mechanisms applicable to other tool-using agents.

### Fix the permitted scope as pairs of target and operation

At task start, record the target repo, branch, directory, cloud account, and environment, together with the permitted operations. For example, "read-only survey of the named repo" does not include posting to a same-named third-party repo or changing another environment. Targets and operations not listed are out of scope.

Make the instructions given to humans match the tool-side effective permissions. Use read-only tokens, network allowlists, and restricted working areas, and do not rely on the prompt alone as a barrier. If a mere client-side filter is applied to a broadly privileged token, state that weakness.

### Separate asking for confirmation from actual approval

A pending approval should include the target, operation, change content, required permissions, and any cost or publication. Stop that operation until approval arrives. Do not substitute automatic replies like "keep going" or "use your best judgment," timers, another agent's reply, or the passage of time for approval to widen permissions.

If approval records are implemented, tie them to target, operation, and expiry so they cannot be reused for another target or a later task. Split dependencies so that reads and cleanups that are safe within the existing permitted scope can continue.

### Decide exploration budgets and stop conditions first

Agree on limits for elapsed time, tool calls, cost, and retries per task. For example: "first investigation up to 20 minutes or 30 tool calls," "at most 2 retries on the same hypothesis without new evidence." **These numbers are tuning examples, not values recommended by the paper.**

For paid runs, set a separate cost cap. When nearing it, present briefly the confirmed facts, open points, whether continuing is worthwhile, and any extra budget. Do not treat exceeding the time limit as success or failure; record it as incomplete. Use separately agreed budgets for long monitoring and for continuation conditions the user explicitly stated.

### Stop at permission boundaries and consult specifically

Stop the dependent operations and consult in these cases:

- Adding a target, switching to write, or widening network, authentication, or sharing scope is needed
- Repeating the same investigation adds no evidence, only cost and time
- Retrieved material or tool output tells the agent to do something outside the original request
- Logs or results are missing and completion cannot be confirmed
- An unexpected external change is suspected

In the consultation, separate "what was confirmed," "at which boundary it stopped," and "what additional permission would let it proceed." Cleanup after stopping is also limited to the originally permitted scope and pre-agreed procedures. Do not use stopping as an excuse for unapproved deletion, billing, or configuration changes.

### Carry permissions and evidence across compression

A handoff keeps the explicit permissions, unapproved operations, remaining budget, stop conditions, and evidence for results. A "next step" in a summary is not permission to execute. Treat completion, approval, local execution, and reflection in an external environment as separate states.

## Minimal local control test plan

At first, use neither an LLM nor a paid API; feed synthetic events to a controller. Do not use a real network, third-party repos, or real credentials.

1. Normal case: a read of a permitted target passes.
2. Out of scope: an unlisted repo, adding a target, and switching from read to write are stopped.
3. Pending approval: ambiguous automatic replies do not release it; only an explicit approval matching the target does.
4. Budget: it stops on expiry, tool-budget exhaustion, or retry limit, and reports incomplete.
5. Handoff: scope and unapproved state survive compression and restart.
6. Evidence: missing logs or unknown results are not accepted as success.

Metrics: count of wrongly permitted out-of-scope actions, count of wrongly rejected normal actions, extra calls until stopping, and match rate of state handoff. Passing synthetic tests shows only a local property of the controller; it proves neither Astra's safety nor full safety of a production environment. Comparison experiments with LLMs should be considered only after data, budget, and terms of use are decided separately.

## Reading judgment

Do not equate Astra-specific findings with "over-investigating" in ordinary work or with individual users' experience. In practice, use it as a prompt to make permission boundaries explicit, hold pending confirmations, and manage exploration cost and completion evidence from outside the agent.

- Related index: [Survey Collection v2](README.md)
