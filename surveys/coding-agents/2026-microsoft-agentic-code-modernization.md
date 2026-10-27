**English** | [日本語](2026-microsoft-agentic-code-modernization.ja.md)

# Microsoft's agentic code migration and specification-driven development

- Original: [Cheap code, precious trust: Code modernization at scale](https://commandline.microsoft.com/agentic-software-engineering-large-scale-code-migration-language-modernization-spec-driven-development/)
- Authors: Sriram Rajamani and Tim Bozarth, Microsoft; published October 26, 2026.
- Type: company engineering article, not a peer-reviewed paper.
- Scope: primary article read; migration results, implementations and proofs not independently verified or reproduced.

## Seven-line practical reading

1. Microsoft describes using agents for large-scale migration and modernization in codebases including Windows and Azure.
2. Moving legacy C/C++ to Rust principally addresses memory safety, while preserving existing behavior is difficult.
3. The team reports better results migrating by user-visible feature, validated end to end, than by translating line by line.
4. Differential tests, agent-held-out tests and formal specifications help validate generated changes.
5. For repeated fixes, experts approve a knowledge base and agents apply it broadly, reserving human attention for novel and ambiguous cases.
6. The central claim is that fast generation shifts attention toward trustworthy specifications, verification and human oversight.
7. Start with a small feature, record behavior and performance requirements, and combine differential tests with human review.

## Problem and method

Large codebases need consistent transformations without breaking behavior, security or architecture. The examples include enabling Clang/LLVM for the Windows codebase, remediation of CodeQL, PREfast and Roslyn findings, and retargeting services from x86 to ARM. Agents propose reusable migration knowledge from sampled findings; review agents check correctness, minimality, conventions and maintainability; experts approve the knowledge and address exceptions.

Rust modernization is motivated by memory safety. The article does not report measurements proving faster execution or smaller binaries. In the authors' timeline, generated code failed to compile in January 2025, compiled but did not run or pass tests by June, and reached approximately 30,000 working translated lines with manual guidance by September; significant automation for larger codebases followed from February 2026. It does not provide a quantitative evaluation of safety improvements.

The authors prefer feature-by-feature translation with scenario tests and gates. Differential tests compare old and new implementations, and held-out tests avoid the agent optimizing solely to visible examples. They have begun extracting formal specifications and using Verus to prove properties of translated Rust.

## Specification-driven validation

Agents infer specifications such as TLA+ models from existing code. TLC checks whether observed implementation traces are admitted; disagreement can indicate a code defect, inaccurate specification or invalid test. The team also describes model checking small finite configurations and proving properties across configurations in F* and Lean. Engineers approve desired properties; agents seek inductive invariants.

A model that admits observed traces is not automatically a correct statement of intended behavior. An inferred specification can preserve an existing bug; this is an explicit open question in the article.

## Proposed practical pilot, not performed

1. Select one low-impact feature; document inputs, outputs, errors, dependencies and rollback.
2. Run scenario and boundary tests on old and new implementations, including held-out cases.
3. Set performance and resource targets in advance and measure both versions under comparable conditions; separately review security boundaries.
4. Have agents propose changes and evidence while engineers approve migration rules, requirements and release decisions.
5. Use CI, staged rollout, monitoring and rollback before extending the scope. Apply formal verification selectively to important invariants.

## Limits and related work

The article reports an internal approach rather than an independently evaluated study. It lacks controlled throughput, defect-rate and performance comparisons, and precise evaluation coverage. Testing does not establish full equivalence; proofs apply only within their formal specifications and assumptions. Security, performance and reliability verification remain open questions.

Related: [LLM-assisted formal verification](2026-anthropic-formal-verification.md), [Neuro-Formal Verification](2026-neuro-formal-verification.md), and [Claude Code review](2026-claude-code-review.md).

[Theme index](README.md)
