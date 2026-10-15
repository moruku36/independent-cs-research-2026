**English** | [日本語](2024-dwave-annealing-rsa.ja.md)

# Reference Candidate: Quantum Annealing and RSA Integer Factorization on D-Wave Advantage

**Status: limited coverage via a news article. Primary paper unread, bibliography unconfirmed, no replication. Checked 2026-10-15 UTC.**

This is not a fully checked survey. It is a reference candidate for future PQC (post-quantum cryptography) research. It is not added to the read status or count of the existing seven surveys.

## Source and what was checked

| Item | What could be confirmed this time |
|---|---|
| Introducing source | [GIGAZINE, "Chinese researchers build a method for breaking RSA encryption with a quantum computer"](https://gigazine.net/news/20241015-rsa-encryption-quantum-computer/) (2024-10-15) was read |
| Paper title as given by the article | 基于 D-Wave Advantage 的量子退火公钥密码攻击算法研究 (research on a quantum annealing attack on public-key cryptography based on D-Wave Advantage). Not yet matched against the journal's own listing |
| Path to the primary paper | The [official PDF on the journal site](http://cjc.ict.ac.cn/online/onlinepaper/wc-202458160402.pdf) linked directly from the article. Retrieval failed this time, so the text is unread |
| Authors and venue | The article names Wang Chao and colleagues at Shanghai University and the Chinese Journal of Computers. The authoritative author list, year, volume, and pages are unconfirmed |
| DOI and version | Not confirmed from a primary source, so not recorded as final bibliography |

## What the article says was reported

The article describes the work as reporting integer factorization of 22 bits with D-Wave Advantage quantum annealing, and 50 bits when combined with classical computation. These figures are **the article's statements**. They are not verified against the paper's text and are not results of our own replication.

Do not treat this as a demonstration of breaking practical RSA-2048, as proof that the approach scales to practical sizes, or as evidence of quantum advantage over the best classical methods. Do not confuse quantum annealing and hybrid optimization with gate-based Shor's algorithm.

## Next checks and use (proposals only)

Before a close reading with the [survey template](../../surveys/template.md), match title, authors, year, volume, pages, DOI, and version against the official text. Then check how the target integers were chosen, preprocessing assumptions, the role of classical computation, total runtime, success rate, comparison conditions, and quantum resources. Do not extrapolate from small-integer experiments to the cost or timing of attacking RSA-2048.

The intended use is finding references when assessing reports about cryptanalysis. It is not adopting new attack code or PQC features. The next free step is matching the bibliography against the public text and building a conditions table. No access to D-Wave hardware and no experiments have been started.

[Reading list](../reading-list.md) | [Collection index](../../surveys/collection-v2/README.md) | [README](../../README.md)
