**English** | [日本語](2026-ai-native-coworker-qualities.ja.md)

# What Makes a Great Co-Worker in an AI-Native Workplace?

## Overview

- **What it is**: A Microsoft arXiv preprint on what knowledge workers value in a co-worker in an AI-native workplace, covering both human and AI co-workers.
- **What it says**: From 22 interviews and a survey of 1,534 knowledge workers, it builds the BACI framework of 75 observable co-worker qualities and shows which qualities are prioritized for humans versus AI.
- **Caveat**: It is a single-organization study based on self-reports, not observation of team performance, and the raw data are proprietary.

## Key points for people and PMOs

- **What we learned**: A two-phase mixed-methods study at Microsoft (22 exploratory interviews followed by a between-subjects survey of $N = 1,534$ knowledge workers: $n = 732$ rating a human co-worker, $n = 802$ rating an AI) mapped what workers value in human and AI contributors. The study introduces the **BACI framework** of 75 observable co-worker qualities across four buckets—**B**enevolence (23), **A**bility (16), **C**ooperativeness (21), and **I**ntegrity (15)—grouped under two broad motives (*getting ahead* and *getting along*). Crossing priority bands across referents yielded **11 co-worker archetypes**: 4 prioritized for both humans and AI (*Safe Pair of Hands*, *Fair Dealer*, *Craftsperson*, *Explorer*), 2 prioritized for humans (*Stand-Up Colleague*, *Perseverer*—where 59% of AI-side rationales insisted accountability must remain human), 2 prioritized for AI (*Navigator*, *Straight Talker*—demanding provenance, explicit uncertainty, domain knowledge, and non-sycophancy), and 3 lower-priority/conditional archetypes (*Glue*, *Satisficer*, *Room-Maker*). Furthermore, 17 qualities were contested for AI (10 in Benevolence, 6 in Cooperativeness, 1 in Ability, 0 in Integrity). Finally, qualitative coding of 991 responses established a **taxonomy of AI work etiquette** (4 themes, 15 sub-themes): 63.6% of respondents required senders to read and verify AI-supported work before sharing, 21.8% required senders to understand and answer for it, and 18.9% warned that unverified "workslop" merely shifts verification labor downstream and erodes trust.
- **What it is useful for**: Designing worker-centric AI assistants and team handoff norms: build AI around *Safe Pair of Hands*, *Craftsperson*, *Navigator*, and *Straight Talker* qualities (observable actions, explicit uncertainty, provenance, non-sycophancy) rather than forced social warmth (*Glue*), and establish explicit team handoff checklists so upstream AI speed does not become downstream verification debt.
- **Caution**: Single-organization study (Microsoft) relying on self-reported survey ratings and free-text reflections rather than behavioral observation of team performance. Between-subjects survey design (10.7% initial response rate; 71.5% usable after quality screens) compares separate respondent groups rather than within-subject paired ratings. Qualitative coding used a human-supervised 3-model AI council (Claude Opus 5, GPT 5.6, Gemini Flash 3.6) after initial human codebook construction.
- **Next step**: Primary source (arXiv PDF v1) read in full. Supplemental instruments are cited by the authors, though raw employee survey data remain proprietary.

## Survey record

- **Status**: fully read (arXiv PDF v1: body, figures, tables, bibliography, and acknowledgments). No reproduction (proprietary enterprise survey and interview data).
- **Title, authors, year, venue, DOI / arXiv ID, primary URL**: *What Makes a Great Co-Worker in an AI-Native Workplace?* / Rudrajit Choudhuri (Oregon State University), Max Meijer (Microsoft), Sam Yu-Te Lee (UC Davis), Cinoo Lee, Caolan Mannion, Peter Jahn (Microsoft), Anita Sarma (Oregon State University), Christian Bird, Alice Ferng (Microsoft) / 2026 / peer-reviewed venue unconfirmed (arXiv preprint, cs.HC). [arXiv:2609.13786v1](https://arxiv.org/abs/2609.13786) (submitted 2026-09-12), [PDF](https://arxiv.org/pdf/2609.13786).
- **Date checked and version examined**: 2026-10-18 (PDF v1 checked) / v1.
- **Research questions** (§1, Figure 1):
  - RQ1 (Qualities, §4): What qualities do knowledge workers value in their co-workers in an AI-native workplace?
  - RQ2 (Priorities, §5): How are these qualities prioritized for human co-workers and AI, and how do they group into recognizable kinds of co-workers?
  - RQ3 (Variation, §6): How do knowledge worker characteristics relate to the kinds of co-workers they prioritize?
  - RQ4 (Work etiquette, §7): What do knowledge workers expect from co-workers who share AI-supported work?
- **Method, data, and comparison conditions** (§3):
  - **Phase 1 — Exploratory interviews** (§3.1): Stratified purposeful sample of 22 Microsoft knowledge workers across diverse disciplines (engineering, design, research/data science, customer-facing, business/operations, IT) and experience (1–25 years). Semi-structured 1-hour remote interviews using a "War-Story" elicitation procedure covering great/negative experiences with human co-workers and AI tools (saturation reached at 18 interviews; 4 more conducted for breadth). Analyzed via reflexive thematic analysis by two authors, checked by a bounded 3-model AI council (Claude Opus 5, GPT 5.6, Gemini Flash 3.6; Krippendorff's $\alpha = 0.84$, ~95% author codes retained), and validated via member checking (17/22 responded).
  - **Phase 2 — Confirmatory two-referent survey** (§3.2): Between-subjects survey deployed July–August 2026 to 20,000 Microsoft employees (stratified random sample). Received 2,146 responses (10.7% response rate); 612 excluded via three pre-specified quality/attention screens, leaving $N = 1,534$ valid responses ($n = 732$ Human-referent, $n = 802$ AI-referent; 71.5% usable rate). To manage cognitive load, each respondent rated 2 randomized blocks (one *getting ahead* block [Ability ♠ 16 or Cooperativeness ♣ 21] and one *getting along* block [Integrity ♦ 15 or Benevolence ♥ 23]), rating 31–44 qualities (~350–450 ratings per quality per referent) on a 5-point scale (*Detrimental* to *Essential*).
  - **Qualitative & quantitative analysis** (§3.2.4, §5–§7):
    - *Free-text corpus*: 4,352 open responses comprising 3,334 rating reflections (coded abductively with AI council support, median $\alpha = 0.88$) and 1,018 AI work etiquette responses (991 codeable; reflexive thematic analysis with AI council support, median $\alpha = 0.94$, 95% consensus retention).
    - *Priority & archetype modeling*: Qualities ranked by share rated *Very important* or *Essential* with Wilson 95% intervals. Referent distributions compared via Mann–Whitney U tests with Benjamini–Hochberg FDR correction and effect-size threshold $|\text{Cliff's }\delta| \ge 0.147$. Contested qualities defined by lower bound of Wilson interval $>10\%$ for *Not important* or *Detrimental*. All-pairs ranking bands (Li et al. procedure) crossed between referents to form 11 archetypes.
    - *Variation modeling*: 22 fractional logit models (11 archetypes $\times$ 2 referents) testing predictors across work context (discipline, experience, task interdependence, AI help), Sternberg thinking styles (rule orientation, sequencing, focus orientation, openness to new ways), motive allocation (100 points split between getting ahead vs. getting along), and whether AI felt like a co-worker.
- **Claims and evidence**: Supported by the archetype statistics, referent contrasts, fractional logit models, and etiquette taxonomy frequencies below (§§4–7).
- **Limitations and threats to validity** (§8.3):
  - *Construct validity*: "Great co-worker" was intentionally left undefined to capture respondent perceptions; measures reflect stated priorities rather than observed workplace behavior.
  - *Internal validity*: Self-selection bias within strata; between-subjects design means unmeasured differences between the Human-referent ($n=732$) and AI-referent ($n=802$) groups could affect contrasts.
  - *AI-assisted qualitative analysis*: Use of frontier LLMs (Claude Opus 5, GPT 5.6, Gemini Flash 3.6) for codebook application under human supervision; bounded by restricting models from inventing codes and requiring two-author review of every assignment.
  - *External validity*: Single-company sample (Microsoft) where AI tools are already routinized; findings may transfer less directly to smaller, non-tech, or heavily regulated organizations.
- **Comparison with related work** (§2):
  - Extends Mayer et al.'s (1995) ABI organizational trust model (Ability, Benevolence, Integrity) and Hogan & Holland's (2003) socio-analytic motives (*getting ahead* vs. *getting along*) by adding *Cooperativeness* (teamwork/coordination science from Klein et al., Johnson et al., Salas et al.) into a unified 75-quality instrument applicable to both humans and AI.
  - Synthesizes fragmented literature on AI disclosure penalties (Schilke & Reimann 2025), "workslop" burden (BetterUp/Stanford 2025), and human-AI teaming (Vaccaro et al. 2024) into an empirical recipient-centered taxonomy of AI work etiquette.
- **Free-to-run reproduction plan**: Using the published 75-quality BACI survey battery and 4-theme etiquette prompts (available in the paper's supplemental material), run a lightweight small-team survey comparing human vs. AI referent priorities on a 5-point scale.
- **Usage status**: Proposed as a framework for evaluating AI teammate behaviors and establishing team handoff norms for AI-assisted deliverables.
- **Unconfirmed points and next checks**: Formal conference publication venue (formatted in ACM conference template, likely CHI/CSCW submission); longitudinal behavioral validation of whether enforcing the etiquette taxonomy reduces downstream review friction.

### Numbers and evaluation unit

**BACI Framework and Referent Contestation Summary (§4, §5.1, Figure 2 & Figure 3)**:
- **Total survey sample**: $N = 1,534$ valid knowledge workers ($n = 732$ Human referent, $n = 802$ AI referent) out of 2,146 raw responses (20,000 invited).
- **Overall correlation of quality rankings**: Spearman's $\rho = 0.517$ (Human top-rated share range: 57%–95%; AI top-rated share range: 38%–96%).
- **Significant referent differences**: 45 of 75 qualities significant after Benjamini–Hochberg correction; **37 qualities** cleared $|\text{Cliff's }\delta| \ge 0.147$ (18 prioritized more for Humans, 19 prioritized more for AI, 38 not substantively different).

| BACI Bucket | Higher-Order Motive | Subdimensions | Total Qualities | Contested for AI ($\ge 10\%$ lower CI negative) | Key Referent Split |
|---|---|---|---|---|---|
| **Ability ♠** | Getting Ahead | Drive & exploration; Craft & execution | 16 | 1 (*Takes ownership*) | Execution, speed, and domain knowledge lean AI; ownership and curiosity lean Human |
| **Cooperativeness ♣** | Getting Ahead | Coordination & shared context; Facilitation, help & openness | 21 | 6 (*Consensus building, Win-win, Conflict mgmt, Humble, Takes initiative, Facilitation*) | Context tracking and scoping lean AI; interpersonal facilitation and openness lean Human |
| **Integrity ♦** | Getting Along | Transparency & principle; Dependability & repair | 15 | 0 | Largest average split: 7/11 transparency/provenance qualities lean AI; *Owns accountability* leans strongly Human |
| **Benevolence ♥** | Getting Along | Warmth & recognition; Restraint, receptivity & developing others | 23 | 10 (*Empathy, Caring, Social skill/sensitivity, Friendliness, Affect mgmt, Confidence building, Shares credit, Interpersonal risk, Equal turn-taking*) | Warmth, credit sharing, and talent nurturing strongly lean Human; epistemic restraint (*Self-reflection*) valued for both |

**The 11 Co-Worker Archetypes Across Priority Quadrants (§5.2, Figure 4, Tables 2–3)**:

| Priority Quadrant | Archetype (# of Qualities) | Human Mean ($\mu_H$) | AI Mean ($\mu_{AI}$) | Baseline Worker Odds Prob. (H / AI) | Core Role & Referent Rationale |
|---|---|---|---|---|---|
| **Highest for Both** *(29 qualities)* | **Safe Pair of Hands** (8) | 4.23 | **4.43** | 79% / **88%** | Technical skill, sound decision-making, follow-through, context awareness (highest mean for AI) |
| **Highest for Both** | **Fair Dealer** (7) | 4.27 | 4.32 | 78% / 82% | Reliability, honesty, error recovery, active listening, avoiding bias |
| **Highest for Both** | **Craftsperson** (10) | 4.21 | 4.34 | 77% / 84% | Thorough, safe/secure, transparent reasoning, invites dissent, clears obstacles |
| **Highest for Both** | **Explorer** (4) | **4.36** | 4.18 | **82%** / 76% | Continuous learning, curiosity, respect, collaborative solving (highest mean for Human) |
| **Higher for Human** *(9 qualities)* | **Stand-Up Colleague** (6) | 4.29 | 3.82 | 80% / 66% | Owns accountability, does not blame, pro-team, enables agency, shares credit, manages conflict |
| **Higher for Human** | **Perseverer** (3) | 4.28 | 3.91 | 80% / 68% | Takes genuine ownership, open-minded, perseverant (59% of AI rationales keep accountability human) |
| **Higher for AI** *(15 qualities)* | **Navigator** (11) | 3.91 | 4.23 | 68% / 79% | Signals uncertainty, observable actions, maintains provenance, discloses limits, repairs misalignment |
| **Higher for AI** | **Straight Talker** (4) | 3.98 | 4.35 | 71% / 84% | Domain knowledge, available/responsive, knows who knows what, non-sycophancy |
| **Lower for Both** *(22 qualities)* | **Room-Maker** (3) | 3.87 | 3.86 | 66% / 68% | Organizes/paces work, anticipates needs, equal turn-taking (AI asked to stop before seizing control) |
| **Lower for Both** | **Glue** (15) | 3.89 | 3.58 | 66% / 57% | Nurtures talent, empathy, caring, facilitation, consensus (12/15 qualities contested for AI) |
| **Lower for Both** | **Satisficer** (4) | 3.82 | 3.58 | 62% / 60% | Decisive, satisficing ("good enough"), offers/requests help, humble |

**Taxonomy of AI Work Etiquette ($n = 991$ Codeable Responses, §7, Table 4)**:
```
1. The pass you owe before sharing AI-supported work:
   - You read and verified it before you sent it: 630 respondents (63.6%)
   - You can judge it and can answer for it: 216 respondents (21.8%)
   - You pushed back on the model rather than blindly accepting it: 165 respondents (16.6%)
   - You are accountable for the check, and the check fits the stakes: 87 respondents (8.8%)
   - It still sounds like you (retains human voice/register): 59 respondents (6.0%)

2. The declaration you owe alongside it:
   - Say the tool was involved, and how much: 118 respondents (11.9%)
   - Say what you checked and show the working: 48 respondents (4.8%)
   - State the cognitive investment the work deserves: 17 respondents (1.7%)
   * Note: 50 respondents (5.0%) rejected special disclosure as unnecessary or routine.

3. The cost you pass on when you skip your duty:
   - Your saving is the reader's bill (shifting verification downstream): 187 respondents (18.9%)
   - The forensics of care (unreviewed slop [73] and stock AI tells [76] erode trust): 149 respondents (15.0%)
   - "Please verify" is not a disclosure (subcontracting checking to recipient): 14 respondents (1.4%)

4. The standing you need before using it at all:
   - The context is your work, not the AI's (fit to project/customer/audience): 96 respondents (9.7%)
   - Do not automate the relationship or aim the AI at co-workers: 58 respondents (5.9%)
   - Use AI as a bounded amplifier (within domain competence): 48 respondents (4.8%)
   - Protect confidential, private, or IP-related data and use approved tools: 32 respondents (3.2%)
```

[Survey Collection v2 Index](README.md) | [Repository README](../../README.md)
