**English** | [日本語](2026-chat-first-worry-later.ja.md)

# Chat First, Worry Later: Individuals' Privacy Perceptions of ChatGPT at Work (user study, N=224)

## Overview

- **What it is**: An arXiv preprint reporting a questionnaire study of 224 European workers on their privacy perceptions of using ChatGPT at work.
- **What it says**: Workers whose organization had a GenAI policy scored slightly higher on knowledge of ChatGPT's data handling and used it for more use cases, yet average knowledge was low (36% correct).
- **Caveat**: It is cross-sectional and self-reported, so it cannot show that policies cause better knowledge, and the full-sample model's fit does not meet the authors' own cut-offs.

## Key points for people and PMOs

- **What we learned**: a questionnaire study of 224 European workers who use ChatGPT at work. The group that reported an organizational GenAI policy (n=103) scored slightly higher on knowledge of ChatGPT's data handling (policy → knowledge, β=.15) and used ChatGPT for more use cases (β=.23). Knowledge is low overall, though: the mean share of correct answers is 36%. Stronger privacy concerns go with lower usage frequency and fewer use cases (β=−.14, −.17). By group, the effect of concerns is significant only in the group without a policy (n=121).
- **What it is useful for**: a concrete example of the authors' claims and study design when drafting organizational GenAI guidelines that include training and settings education, not only prohibitions; and a list of commonly misunderstood points (is anonymization guaranteed, who secures the communication channel).
- **Caution**: this is a cross-sectional, self-reported survey and cannot show causation (the authors themselves list as a limitation that organizations with policies may already be more privacy-sensitive). The fit indices of the full-sample path model do not meet the authors' own stated cut-offs (below). We also found mismatches between text and tables in item counts and in one mean.
- **Next step**: this record reflects a reading of the primary source (arXiv HTML v1 and PDF v1) only. No replication or re-analysis was done (the paper says data and analysis syntax are in supplementary material, which we did not obtain).

## Survey record

- **Status**: fully read (arXiv HTML v1 in full; the main text and Figures 2, 3 and 4 of PDF v1 were checked by eye). The reference list was read through, but the individual cited works were not read closely. No replication or re-analysis.
- **Title, authors, year, venue, DOI / arXiv ID, primary URL**: *Chat First, Worry Later: Understanding Individuals' Privacy Perceptions Using ChatGPT in a Work Context* / Christoph Nirschl, Magdalena Glas, Gerhard Messmann, Günther Pernul (University of Regensburg) / 2026 / peer-reviewed venue unconfirmed (arXiv preprint, cs.HC, cross-lists cs.CR and cs.CY). [arXiv:2608.20789v1](https://arxiv.org/abs/2608.20789v1) (submitted 2026-08-21 UTC), [HTML v1](https://arxiv.org/html/2608.20789v1), [PDF](https://arxiv.org/pdf/2608.20789v1), [DOI](https://doi.org/10.48550/arXiv.2608.20789) (issued by arXiv).
- **Date checked and version examined**: 2026-10-16 (abs page re-fetched at 11:03 UTC) / v1. The submission history lists only [v1] 2026-08-21, so v1 was the latest version available at the time of checking. We do not claim that no later version will appear. No venue (peer review or acceptance) was stated on the page, and it remains unconfirmed.
- **Research question** (§4.2):
  - RQ1: how do organizational policies affect employees' ChatGPT proficiency (explicit knowledge of how ChatGPT collects, stores and processes data and where liability lies)?
  - RQ2: how do policies, integrated privacy concerns and proficiency affect usage frequency and the number of use cases?
  - RQ3: do the effects of concerns and proficiency in RQ2 differ depending on whether a policy exists?
  - RQ4: does usage behavior differ by policy type (usage constraints vs. user constraints)?
  - No formal hypotheses are stated.
- **Method, data, and comparison conditions**:
  - **Survey**: an online questionnaire for people who regularly use ChatGPT at work (Google Forms, one-time links). Pilot with N=11. Recruitment used Prolific Academic together with targeted email outreach (§5.1). The ChatGPT version was not recorded. The paper says ChatGPT Enterprise was not widely available at the time and was not considered (§8).
  - **Quality control**: two attention checks (failing one led to exclusion), no submission with incomplete answers, and responses with conflicting ratings on thematically related items were omitted (§5.1). The number excluded could not be found in the text.
  - **Sample**: final N=224. Two participants with missing education were excluded (§5.3). Gender: male 133 / female 89 / non-binary 2. Age: 18–24 = 69, 25–34 = 105, 35–44 = 32, 45+ = 18. Education: foundational 49 / advanced 14 / academic 161. Sector (not used in the analysis): IT & technology 75, engineering & manufacturing 26, education & research 25, finance & banking 12, business & consulting 15, healthcare & pharmaceuticals 14, arts & entertainment 13, other 44 (Tables 2 and 3; each column sums to 224).
  - **Measures** (§5.2, Appendix C):
    - Organizational policies: multiple response (Appendix C.1 has eight options, including "No restrictions"; Table 4 lists the seven others). Items 3–6 are classed as usage constraints and items 1–2 as user constraints; item 7 (other) is excluded from RQ4.
    - Integrated privacy concerns: six items on a five-point scale (three reverse-scored); exploratory factor analysis (principal axis factoring, promax) gave one factor, α=.86.
    - ChatGPT proficiency: eleven true/false items sourced from OpenAI's public policies (True / Wrong / Unsure). "Unsure" counts as incorrect. The score is the percentage correct. Two authors reviewed the items iteratively. The answer key is not in the appendix.
    - Frequency of use: four levels (less than once a week to daily). Use cases: multiple response (Appendix C.5 has 10 items; §5.2 says "eight types").
  - **Analysis** (§5.3): descriptives, t-tests for background variables (dummy-coded), correlations (all / with policy / without policy), and five Mplus 8 path models (full sample: RQ1 and RQ2; with vs. without policy: RQ3; usage vs. user constraints within the policy group: RQ4). Only significant background variables were controlled. Fit cut-offs set by the authors: 0 ≤ χ²/df ≤ 2, CFI ≥ .97, NNFI ≥ .97, RMSEA ≤ .05, SRMR ≤ .05.
  - **Ethics** (§5.4): the paper says the study was designed according to the guidelines of the first author's institutional ethics committee, with explicit consent, optional answers, and Prolific IDs used only to match compensation and deleted afterwards.
- **Claims and evidence**: based on the tables below and §6 (the authors' claims). The recorder's inferences are kept in a separate item.
- **Limitations and threats to validity** (§8, the authors' wording): ChatGPT only; Europe only; few participants aged 45+; ambiguity of sector labels (students may have chosen "education"); policy effects may partly reflect organizations that were already privacy-sensitive; ChatGPT Enterprise not considered; use-case items not validated; limits on generalizing across GenAI tools and over time. We did not find a passage that lists self-reporting itself as a limitation, within the parts we read.
- **Comparison with related work** (§3, the authors' positioning):
  - General LLM privacy risks ([25], [61]) and a review of privacy-enhancing technologies for text ([56]).
  - Chatbot acceptance: TAM extensions examining concerns ([65], [52]), trust ([13]), Twitter data plus a survey on concerns ([2]), and UTAUT ([34]).
  - An interview study on ChatGPT adoption at work [27] (Kimbel, Glas, Pernul 2024; Glas and Pernul are also authors of this paper), a qualitative study of disclosure behavior [73] (Zhang et al. 2024), and a study of perceptions of custom GPTs [31] (Ma et al. 2025).
  - The authors argue that TAM targets initial adoption and does not fit established users, so they build a new model, and they claim to be the first to give quantitative insight into privacy-driven behavior of ChatGPT users at work ("to the best of our knowledge"). That novelty is the authors' claim; we did not verify it with an exhaustive prior-work search.
- **Free-to-run reproduction plan**: not done. The paper says the dataset and the SPSS and Mplus 8 syntax are in supplementary material (§5.3), but we did not obtain or check it. If obtainable, recomputing descriptives and correlations is a candidate (Mplus is paid software; approximating the path models with free tools is a separate question).
- **Usage status**: proposed only (no evidence of trial or adoption).
- **Unconfirmed points and next checks**: availability and content of the supplementary material, existence of v2 or later, peer-review or acceptance information, the coefficient-to-path mapping in Figures 2 and 4 (below), the content of the individual references, and the number of excluded respondents.

### Numbers and evaluation unit

**Sample and descriptives** (text §6.1, Tables 2–4 and 5–7; percentages and means checked against the text and tables, arithmetic rechecked by the recorder)

| Item | Value |
|---|---|
| Analyzed | N=224 (after excluding 2 with missing data) |
| No policy (or unaware) | 121 (54%); means: concerns 3.83, proficiency 34%, frequency 2.52, use cases 2.66 (Table 7) |
| Policy present | 103 (46%); means: concerns 3.93, proficiency 39%, frequency 2.46, use cases 3.31 (Table 6) |
| Integrated privacy concerns, overall | M=3.88, SD=0.81 |
| Proficiency, overall | mean 36%, SD=18% (Table 5: 0.36, 0.18) |
| Frequency of use | less than weekly 50 (22.3%) / weekly 47 (21.0%) / several times a week 94 (42.0%) / daily 33 (14.7%) |
| Number of use cases | one 29 (12.9%) / two 62 (27.7%) / three 68 (30.4%) |

- The 36% is the mean share of correct answers over all eleven items. Because "unsure" counts as incorrect, **lack of knowledge and misconception are not distinguished** (the recorder's note).
- Misconceptions (text §6.1): 90% wrongly believed the privacy policy guarantees anonymization of personal information (item 9), and 84% wrongly assumed OpenAI states that it secures online communication channels (item 4). Both are the authors' statements; the correct answers rest on the authors' reading of the policies.
- Policy types (Table 4, multiple response): de-identification or anonymization of input data 47, explicit prohibition of personal information in input 43, usage limited to documents up to a confidentiality level 41, restrictions on sharing generated content 36, restriction to specific departments or users 33, prior training or awareness required 12, other 13. 47/103 = 46%, consistent with the text.
- Use cases (Table 4, multiple response): brainstorming 141, language translation and communication 111 (consistent with 49.6% = 111/224 in the text), content polishing 83, e-mail 74, code 74, data analysis 46, content generation 43, decision-making 41, support 35, meeting 15.

**Correlations** (Pearson r)

| Pair | All, N=224 | No policy, n=121 | Policy, n=103 |
|---|---:|---:|---:|
| Concerns–frequency | −.14* | −.23* | n.s. (−.01) |
| Concerns–use cases | −.16* (text) / −.15* (Table 5) | −.26** | n.s. (−.09) |
| Proficiency–frequency | .08 (n.s.) | .20* | −.06 (n.s.) |
| Frequency–use cases | .42** | .49** | .39** |
| Policy–proficiency | .15* | – | – |
| Policy–use cases | .23** | – | – |

- Values for the policy group were transcribed from Tables 6 and 7 (rows checked by eye in the extracted text).
- Background variables (t-tests): foundational education means lower concerns (t=−2.89, p<.01, d=.45), academic education means higher concerns (t=2.55, p<.05, d=.37), and age 45+ means lower frequency (t=−2.71, p<.01, d=.69).

**Path models (standardized coefficients, β)**

- Figure 2 (RQ1 and RQ2, N=224, education controlled): policy → proficiency .15* (RQ1), policy → use cases .23***, policy → frequency −.04, policy → concerns .05, concerns → frequency −.14*, concerns → use cases −.17** (text), and proficiency → frequency / use cases not significant (.09 / .10 in the figure). **In the figure the labels near "−.09" and ".10" overlap, and we cannot say from the PDF image alone which path each value belongs to.** The text says only that proficiency has no significant effect. Education → concerns β=−.19** (text).
  - **Fit**: χ²/df=2.03, CFI=.96, NNFI=.81, RMSEA=.07, SRMR=.03. Against the authors' cut-offs (§5.3), χ²/df (>2), CFI (<.97), NNFI (<.97) and RMSEA (>.05) fall outside; only SRMR is within. We found no passage in the text or captions that discusses this deviation ("fit" appears only in §5.3, the captions, and the saturated-model note in Appendix B).
- Figure 4 (RQ3, Appendix B; both models are saturated, so no fit indices):
  - Without policy (n=121): concerns → frequency −.23**, concerns → use cases −.26**, proficiency → frequency .20*, proficiency → use cases .15†.
  - With policy (n=103): the figure shows −.01, .05, −.09 and −.06, and the text says none of the effects is significant. **The labels overlap, and we cannot say from the figure which of −.09 and −.06 belongs to concerns → use cases and which to proficiency → frequency.**
- Figure 3 (RQ4, n=103; model fit for usage / user constraints: χ²/df=1.00 / 1.27, CFI=1.00 / .94, NNFI=1.00 / .71, RMSEA=.00 / .05, SRMR=.04 / .04):
  - usage constraints (bold) / user constraints (italic): policy type → use cases .17† / .06, → frequency .11 / .03, → concerns .02 / −.07, → proficiency .07 / −.06; concerns → frequency −.02 / −.01, concerns → use cases −.10 / −.08; proficiency → frequency −.06 / −.05, proficiency → use cases .04 / .05.
  - No path is significant at p<.05; only .17† is a weak trend. The CFI and NNFI for the user-constraints model fall outside the authors' cut-offs (we found no comment by the authors on this).

### Separating the paper's claims from the recorder's inferences

**The paper's claims**

- Policies are positively associated with proficiency and with a wider range of use cases; rather than restricting use, they provide a framework that supports safe exploration. Concerns reduce use, and when no policy exists, concerns and knowledge shape use (§7).
- The existence of a policy matters more than its type (interpretation of RQ4).
- Recommendations (§7): a full ban is not effective because of the risk of moving to other tools (Samsung and JPMorgan are cited); local models are hard for small organizations; the authors recommend practical, mandatory training, risk judgment by sensitivity, privacy settings (disabling history, opting out of training), and privacy-enhancing tools such as client-side filters. Awareness alone is not enough, and usage-restricting measures are also needed.
- Conclusion: only about half of participants reported knowing of a policy (46% reported one).

**The recorder's inferences** (not the paper's claims)

- Policy presence is self-reported, and "no policy" and "unaware of one" are not distinguished (the text says "or they were not aware of those"). The group difference may therefore reflect how well a policy is communicated as well as whether one exists.
- Because the full-sample model misses the authors' fit cut-offs, the coefficients in Figure 2 should be interpreted with care.
- The coefficients are small (|β| roughly .14–.26). We did not assess the practical size of the effects in this record.

### Text/table mismatches (recorded unresolved)

Checked in the original HTML and PDF. We did not resolve them by guessing.

1. **Number of policy options**: §5.2 says eight options, and Appendix C.1 also has eight (including "No restrictions"). Table 4 lists seven, without "No restrictions". This reads less like a count mismatch than a table that omits one item, but since the number of "No restrictions" respondents is not in the table, we cannot check directly how it maps to the definition of the policy groups (103 / 121).
2. **Number of use cases**: §5.2 says eight types, but Appendix C.5 and Table 4 have ten items.
3. **Mean number of use cases**: the text says M=3.00, Table 5 says 2.96. The selection counts in Table 4 sum to 663, and 663/224 = 2.96, which agrees with Table 5 (the text's 3.00 does not agree with this check).
4. **Concerns–use cases correlation**: r=−.16 in the text, −.15 in Table 5.
5. **Display of RQ2 effects**: labels overlap in Figure 2, so some coefficients cannot be assigned to a path (above).
6. **Basis of proficiency scoring**: the "correct" answers are not in the appendix. Of the eleven items, the text gives misconception rates only for items 4 and 9.
7. **RQ3 statistics**: the paper estimates two separate models and compares their significance; we found no description of a direct test of the difference between groups.

### Scope of verification

- Checked: bibliographic data (title, authors, version, date, categories), N=224 and the breakdown sums, the 36% (SD 18), group sizes (121 / 103), consistency of Table 4 counts with the text percentages, the correlation tables, the coefficients in Figures 2, 3 and 4 (by eye on the PDF), fit cut-offs and values, the item-count and mean mismatches, and the ethics and data statements.
- Not checked: the contents of the supplementary material, the individual references, the paths whose labels overlap in the figures, and v2 or later.

### Scope of the repository duplicate check

We searched the full text of a tarball of the **main branch only** of the public repository moruku36/independent-cs-research-2026 (retrieved 2026-10-16) and found no mention of arXiv ID 2608.20789. Other branches, open PRs and forks were not covered.

## Applying this to this repository's practice

These are **this record's proposals**, not measures whose effect the paper demonstrated. Implementation, adoption and effect measurement are not done.

1. Define guideline documents with input-data sensitivity classes, anonymization procedures and settings (history, training opt-out) together with training, not only prohibition items (a proposal in line with the paper's recommendations).
2. In user-facing notices, treat "anonymization is not guaranteed" and "securing the communication channel is not stated in the policy" as commonly misunderstood points (these had high error rates in the survey; the correct answers rest on the authors' interpretation).
3. If running a similar survey in-house, record policy "existence" and "awareness" as separate items, and fix the source of the proficiency answers (policy version and date).

## 日本語

[Chat First, Worry Later](2026-chat-first-worry-later.ja.md)（arXiv:2608.20789v1、cs.HC、2026-08-21投稿、プレプリント・会場未確認）：欧州の職場でChatGPTを使う224人への質問票調査。ポリシーのある組織ほど知識（β=.15）とユースケース数（β=.23）が高いが、知識の平均正答率は36%。懸念は利用頻度・ユースケース数を下げる（−.14／−.17）が、有意なのはポリシー無し群のみ。全体モデルの適合は著者基準外。本文と表の項目数・平均の不一致あり。再現なし。

Source sections: [§4.2](https://arxiv.org/html/2608.20789v1#S4.SS2) · [§5](https://arxiv.org/html/2608.20789v1#S5) · [§6](https://arxiv.org/html/2608.20789v1#S6) · [§7](https://arxiv.org/html/2608.20789v1#S7) · [§8](https://arxiv.org/html/2608.20789v1#S8) · [Appendix A–C](https://arxiv.org/html/2608.20789v1#A1)

[Collection index](README.md) | [Reading list](../../docs/reading-list.md)
