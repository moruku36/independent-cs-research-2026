**English** | [日本語](2026-claude-code-publication-leak-paths.ja.md)

# Leakage paths when publishing work knowledge with Claude Code

- [Source article](https://zenn.dev/pepe_3_go/articles/claude-code-article-leak-paths), Iwai Yuu, October 26, 2026.
- Individual practitioner article, not a paper; article read, no independent replication. The author describes Windows 11, Claude Code desktop and a Team plan.

## Seven-line practical reading

1. Drafts generated from work sessions can include customer names and confidential details.
2. The author identifies four paths: prose, code, screenshots and Git metadata.
3. A private denylist checks text and code; work scripts are rewritten as minimal public examples.
4. A person checks images for customer designs and filenames.
5. Commit email and the account used for push also matter; proofreading prose does not reveal them.
6. The denylist and supporting notes can themselves contain sensitive customer information.
7. Combine company approval with inspection of changes, images, Git history and destination; a person makes the publication decision.

## Observed workflow and limits

The author describes exposing a work email in commits and needing to rewrite history. They configure a repository-local Git identity with a noreply address, inspect commit history, and check the intended GitHub authentication account on a computer with multiple credentials. They inspect screenshots manually and retain the final publishing decision. This is one user's experience, not an effectiveness study.

## Proposed enterprise practice, not performed

- Check company policy, intellectual property and customer obligations before publication.
- Use a separate publishing workspace without raw work-session records or customer data.
- Review prose, code, images, metadata, commit history and destinations. Denylists miss variants, unknown secrets and images.
- Inspect both author and committer identities and confirm the authenticated account separately. Follow company attribution rules rather than assuming a noreply address is always appropriate.
- Follow incident procedures if information is exposed. History rewriting cannot guarantee removal of clones, caches or notifications.

Git author identity and GitHub authentication are separate; a username embedded in a remote URL alone does not guarantee the account used to authenticate.

Related: [Claude Duet safety](2026-claude-duet-safety-privacy-security.md) and [shadow AI governance](2026-shadow-ai-ban-pii-governance.md).

[Theme index](README.md)
