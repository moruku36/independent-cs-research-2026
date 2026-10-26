**English** | [日本語](2026-claude-code-review.ja.md)

# How the Claude Code team does code review

- Type: company engineering article and operational case study, not a peer-reviewed paper.
- Authors: Addy Osmani, Morgan Westlee Lunt, Qing Wang; published October 15, 2026.
- Primary article: https://claude.dev/blog/solving-code-review-at-anthropic/
- Requested post: https://x.com/addyosmani/status/2114604912520921136?s=20
- Scope: the company article was read. The X post could not be retrieved and text extraction from the supplied PDF failed; a third-party reference associates the post with the article, but exact correspondence with the post and images is unverified. No replication or independent audit.

## Seven-line practical reading

1. The article describes how the Claude Code team reviews large volumes of agent-generated changes.
2. Pre-PR verification, AI bug and security review, CI, human approval, and staged release form layers.
3. The number of human approvals depends on risk; sensitive paths retain human oversight.
4. The team reports that merged PRs more than doubled from June to September 2026 while the share reverted fell by over 40%.
5. This is an internal observational report, not proof that the individual practices caused the improvement.
6. Start on one repository: record purpose, test evidence, risk, and rollback; combine AI findings with human decisions.
7. Track review time alongside reversions, incidents, false positives, and review rounds.

## Question and conclusion

Review both catches defects and spreads shared understanding. The authors allocate scarce human attention to direction, risky changes, architecture, evidence, and accountability while automated checks handle routine findings. Reduced review time is not a gain if incidents shift the cost downstream.

## The layered workflow

1. Before a PR, agents execute tests, builds, or UI checks and present evidence; a fresh-context agent reviews the diff.
2. AI review checks intent and surrounding code. Several agents find issues and a separate group verifies findings; every finding is fixed or resolved with a reason.
3. Dedicated security review, lint, types, tests and builds gate merging. The PR records testing and rollback.
4. Risk determines approval: low-risk changes can proceed without human approval under specified conditions; medium-risk changes require one person and high-risk changes two. Lighter paths apply to trusted authors; sensitive paths and CI retain human review. An agent does not occupy a required human slot, and certain new commits require renewed approval.
5. A merge queue retests against main. Flags, internal use, staged release, monitoring and fast rollback address failures that escape earlier checks.

## Improving and limiting review

Past incidents and reverts become an evaluation set; comment responses help identify noise. To stop agent authors and reviewers looping indefinitely, the team caps rounds, reviews subsequent diffs, and avoids duplicate findings. One example exceeded 50 rounds.

The team also recognizes loss of shared context when machines read most diffs. It reports using on-demand AI explanations and open work channels, while acknowledging there is no formal knowledge-sharing mechanism. AI explanations need verification, especially for historical rationale.

## Proposed adoption, not yet performed

- Add purpose, test evidence, risk and rollback to PR templates; keep mandatory human review for authentication, billing, CI and release paths.
- Pilot AI review in one repository; add recurrent false positives and missed incidents to concise instructions and evaluation cases.
- Measure approval count and waiting time together with revert and incident rates and finding quality.
- Consider automatic merging only for low-risk changes after establishing access controls, incident response and rollback.

## Limits and related work

The figures are self-reported, observational and lack enough information to establish causality or transferability. This team already has extensive tests, CI, security review, internal usage and release infrastructure. The article says automatic tightening of approval rules in response to adverse metrics is not yet implemented.

Related: [Meta RADAR](2026-radar-low-risk-code-review.md), [Anthropic source control](2026-anthropic-scion-source-control.md), and [Agentic code review](2026-agentic-code-review-eras.md).

[Theme index](README.md)
