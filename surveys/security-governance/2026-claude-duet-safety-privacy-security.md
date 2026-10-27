**English** | [日本語](2026-claude-duet-safety-privacy-security.ja.md)

# Claude Duet safety, privacy and security

- [Anthropic product article](https://claude.com/resources/articles/claude-duet-safety-privacy-and-security), October 23, 2026. Vendor description, not a peer-reviewed paper.
- Scope: article read; implementation, effectiveness, contractual terms and enterprise operation not independently verified. Duet was a research preview at the article date.

## Seven-line practical reading

1. Duet uses connected applications and a cloud computer to execute tasks while the user is away.
2. It is designed to request approval for sensitive messages, payments and deletion, showing recipients and content.
3. Separate classifiers check intent and sensitive information, but Anthropic acknowledges misses and false positives.
4. The vendor describes isolating passwords, browser cookies and service tokens from the agent.
5. Disconnecting an app stops new access; retained memory persists until reset.
6. Before business use, check permitted connectors, least privilege, classification, approval, retention and deletion.
7. These claims apply to Duet and are not automatically guarantees for Claude Code, Cowork or other deployments.

## Design and boundaries

The browser uses a separate cloud VM with limited commands. Connected-service credentials are injected by a proxy outside the agent machine. Page text and downloads are still processed, so credential isolation does not eliminate prompt injection or sensitive-data exposure.

The separate classifier is designed to prohibit sharing certain credentials and financial identifiers and require consent for other sensitive information; a user's direct request can constitute consent. Some actions, such as securities trading and banking transfers, remain prohibited even with approval. The vendor acknowledges possible misses and overflags.

Connected apps carry over between Claude and Duet. Disconnecting stops future access but does not automatically erase previously learned memory. Verify actual contract and retention terms rather than generalizing to every enterprise product.

## Proposed enterprise checks, not performed

- Confirm company approval, contract, region and data handling before work use.
- Minimize connector permissions and define human authorization for external messages and destructive actions.
- Restrict sensitive data to approved deployments; check history, memory, deletion, audit and retention.
- Combine AI checks with company access controls, DLP and monitoring.

This vendor account is not an independent efficacy evaluation. [Claude Code publication leak paths](2026-claude-code-publication-leak-paths.md) describes a different product and workflow.

[Theme index](README.md)
