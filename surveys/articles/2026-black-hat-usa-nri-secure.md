**English** | [日本語](2026-black-hat-usa-nri-secure.ja.md)

# Black Hat USA 2026: Review of NRI Secure's Conference Report

## Summary and source type

This review connects agent execution boundaries, authentication implementation, and intelligence on malware suppliers. Its practical question is how to examine permissions, identity validation, and monitoring alongside model instructions and authentication choices.

This is a **conference-article survey**, not a peer-reviewed paper or systematic review. It contains an original summary and analysis, not a reproduction of the article, images, or tables. It is not counted as an academic paper.

## 1. Bibliography and verification

- **Article:** Black Hat USA 2026参加レポート｜AIエージェント・パスキー・AD脆弱性など注目5セッションと企業の対策
- **Publisher:** NRI Secure blog.
- **Authors, as published:** 高須賀 昌烈、豊原 宗一郎、高塚 大輝、吉田 竜一、住友 孝彰.
- **Published / updated:** 2026-10-20. Checked 2026-10-20 JST.
- **Source:** https://www.nri-secure.co.jp/blog/black-hat-usa-2026
- **Status:** article body checked. No comprehensive slide verification, product testing, or exploitation.
- **Additional checks:** Adam Shostack's PHANTOM-B introduction and relevant sections of Semperis's Identity Crisis research. Not every session was verified against primary material.
- **Question:** what architecture and operating concerns can be extracted across these five sessions?
- **Method / data:** participant-selected session summaries and commentary, not a controlled experiment or systematic sample of the conference.
- **Usage:** proposed / not trialed / not adopted. Operational ideas below remain untested.

## 2. Five sessions

| Session | Article's account | Verification and qualification |
|---|---|---|
| Threat Modeling LLMs: The PHANTOM-B model | Eight perspectives for eliciting LLM-specific threats | Creator's introductory blog checked; whitepaper and effectiveness evaluation not checked |
| Pass-the-Passkey Family of Attacks | Implementation and endpoint boundaries can undermine passkey deployments | Slides and SpecterOps whitepaper not checked; affected products, permissions, and remediation require confirmation |
| Identity Crisis | KerberLoss and ResetNightmare exploit identity-processing inconsistencies in AD | Relevant Semperis research checked; Microsoft affected-version and KB mapping not checked |
| Caging the Agent | Roblox combines sandbox layers with gateway-side credential injection | Based on NRI's account; slides and implementation not independently verified |
| A Front-Row Seat to APT Operations | Supplier-focused CTI complements tracking individual operations | Primary talk material not checked; attribution and observation coverage not established here |

### PHANTOM-B

NRI describes prompt injection, hallucination, anthropomorphization, non-explainability, training issues, overreliance, missing security engineering, and bias. The [creator's introduction](https://shostack.org/blog/why-phantom-b/) confirms its purpose as an LLM-focused threat-elicitation tool. It should not be interpreted as replacing ordinary identity, permissions, or network review. Claims about adoption speed or effectiveness were not tested here.

### Authentication and AD: preserve prerequisites

The passkey discussion does not establish that FIDO2 cryptography is broken or that all synchronized credentials are unsafe. Endpoint compromise, assertion handling, RP verification, synchronization, and recovery need separate examination. Article-specific assertion lifetimes and patch statements are not universal product properties.

[Semperis's research](https://www.semperis.com/blog/identity-crisis-novel-vulnerabilities-leading-to-kerberos-downgrade-dos-and-full-domain-takeover/) identifies KerberLoss as CVE-2026-25177 and ResetNightmare as CVE-2026-27912. ResetNightmare has prerequisites including relevant object-write permissions and a password-age condition. It is not an unconditional attack available to every ordinary user.

That research discusses DC updates and attribute-change auditing. Event ID 5136 requires appropriate audit configuration and object SACLs; watching an event number alone is insufficient. Microsoft product and KB applicability still needs checking.

### Agents: secret custody and authorization differ

NRI describes behavioral guidance, host isolation, network restrictions, central control, and visibility. Instructions such as CLAUDE.md do not themselves enforce an execution boundary.

Gateway-side credential injection can reduce exposure of long-lived third-party secrets inside the agent environment. However, preventing secret access does not prevent misuse of the authority exposed by the gateway. User, operation, and resource authorization, token revocation, auditing, and gateway protection remain separate design concerns. This is our analysis, not a demonstrated defect in Roblox's implementation.

VMs, containers, WSL, and macOS restrictions should not be assumed to provide identical boundaries. Kernel sharing, mounts, sockets, privileges, and network access require explicit examination.

## 3. Cross-topic synthesis and related records

NRI proposes shifts toward infrastructure enforcement, continued authentication/session validation, and supplier-oriented CTI. These are the authors' interpretations, not experimental proof of one optimal enterprise configuration.

| Existing record | Complementary perspective |
|---|---|
| [GitInject](../agent-safety/2026-gitinject.md) | Pair CI/CD instruction-injection risks with enforceable execution and permission boundaries |
| [Unsanctioned supply-chain attacks](../agent-safety/2026-unsanctioned-supply-chain-attacks.md) | Evaluate agent behavior separately from infrastructure restrictions on possible actions |
| [SlopCodeBench](../coding-agents/2026-slopcodebench.md) | Treat security boundaries and secret handling as acceptance axes alongside correctness and code quality |

This is a thematic comparison, not a comparison of success rates under equivalent conditions.

## 4. Proposed operational review

No configuration changes or production testing were performed.

| Area | Review question | Evidence to retain |
|---|---|---|
| Agent environment | Actual filesystem, host sharing, sockets, egress, privilege paths | Architecture, permission table, expected allow/deny outcomes |
| API/MCP gateway | Secret location, user binding, operation/resource authorization | Authorization specification and sanitized audit examples |
| Passkeys | Authenticator type, endpoint protection, RP checks, recovery, privileged access policy | Product specifications and official remediation mapping |
| AD | All DC versions/updates, attribute-write permissions, auditing and SACLs | Update inventory, permission review, synthetic-log results |
| CTI | Relationships among supplier, tool, operation, and IOC | Sources, confidence, and observation dates |

## 5. Free-to-start checking plan

1. Draw a fictional agent architecture and separate LLM-specific threats from conventional access-control threats.
2. Review gateway authorization on paper without real tokens. Define what happens when a read-only agent requests a write.
3. Use synthetic AD modification logs to test detection expectations without modifying real directory objects or reproducing attacks.
4. Label evidence as article-derived, primary-source-checked, proposed, or unverified.

This is a preliminary review exercise, not reproduction of the talks. No additional paid services or API subscriptions are assumed.

## 6. Limitations and next checks

The participant-selected five sessions need not represent the conference as a whole. Category counts, attendance, and implementation duration were not independently verified or used as effectiveness evidence.

Distinguish research findings, attendee impressions, article recommendations, and this review's proposals. Current passkey and AD decisions require vendor guidance and environmental prerequisites. Roblox's architecture and the CTI case require primary-material follow-up; neither complete exfiltration prevention nor error-free attribution is established.

## 7. References and reading status

- [NRI Secure article](https://www.nri-secure.co.jp/blog/black-hat-usa-2026): body checked.
- [Why PHANTOM-B?](https://shostack.org/blog/why-phantom-b/): creator's introduction checked.
- [Semperis Identity Crisis](https://www.semperis.com/blog/identity-crisis-novel-vulnerabilities-leading-to-kerberos-downgrade-dos-and-full-domain-takeover/): relevant prerequisites, CVEs, auditing, and remediation discussion checked; no exploitation.
- [PHANTOM-B whitepaper](https://i.blackhat.com/BH-USA-26/Presentations/BHUS26-Shostack-ThreatModelAI-PHANTOMB-WP.pdf): article-listed primary-source candidate; unread.
- [Pass-the-Passkey whitepaper](https://specterops.io/wp-content/uploads/sites/3/2026/08/Pass-the-Passkey_A4_v2.pdf): article-listed candidate; unread.
- [Caging the Agent slides](https://i.blackhat.com/BH-USA-26/Presentations/US-26-Kumar-Caging-The-Agent-Thur.pdf): article-listed candidate; unread.
- [Black Hat schedule](https://blackhat.com/us-26/briefings/schedule/index.html): accessed, but extracted text did not establish the relevant session details.

[Collection index](README.md) | [Reading list](../../docs/reading-list.md) | [Repository README](../../README.md)
