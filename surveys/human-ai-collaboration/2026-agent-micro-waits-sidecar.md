**English** | [日本語](2026-agent-micro-waits-sidecar.ja.md)

# Too Long to Watch, Too Short to Leave: Designing for Agent Micro-Waits

## Overview

- **What it is**: A Google DeepMind and University of Toronto paper on "micro-waits", the minute or two a user waits per agent turn, and Sidecar, a side chat built for that time.
- **What it says**: In a within-subjects study (N=16), time spent switched away from the agent tab fell from 35% to 13% with Sidecar, which reads the agent's run, surfaces implicit decisions and suggests next directions.
- **Caveat**: It is a small, single-session lab study, Sidecar's parts were not separated, and participants reported higher mental demand; the text was read via a summarizing tool.

## Key points for people and PMOs

- **What we learned**: when an AI agent works for a minute or two per turn, users are stuck in a "micro-wait": too long to watch, too short to do something else. The authors built **Sidecar**, a side chat in the same tab that reads the agent's run, surfaces decisions the agent made implicitly, and suggests next directions. In a within-subjects study (N=16), time spent switched away from the agent tab fell from 35% to 13% of wait time, and participants reported making more progress and noticing under-specification in their own prompts.
- **What it's useful for**: a concrete design vocabulary for waiting time in agent tools (read-only side channel, decision cards, explore cards, suggestions kept small and grounded in the live run). Also a reminder that "agent is slow" and "user is idle" are separate problems.
- **Caution**: small lab study (16 participants, one session, one company), tasks were short and deliberately under-specified, and Sidecar's components were not separated, so we cannot say which part caused the effect. Participants also reported **higher** mental demand with Sidecar. Five participants cited novelty.
- **Next step**: none done. No reproduction, no implementation, no check of whether Sidecar is publicly released.

## Survey record

- **Status**: primary HTML checked through a summarizing fetch tool (about 100,000 of 104,005 characters covered; the last ~4,000 were not read). Not read line by line, PDF not cross-checked, cited works not read, not reproduced. Numbers below are as reported by that extraction and should be re-checked against the PDF before being quoted.
- **Title, authors, year, venue, DOI / arXiv ID, primary URL**: *Too Long to Watch, Too Short to Leave: Designing for Agent Micro-Waits* / Kevin Pu (University of Toronto; work done during an internship at Google DeepMind), Anh Truong, Michael Terry, Carrie J. Cai, Michael Xieyang Liu, Savvas Petridis (Google DeepMind; Petridis and Pu co-last authors) / 2026 / cs.HC preprint. The page still contains template placeholder text (conference name, DOI, CCS codes), so **venue is unconfirmed**. [arXiv:2610.27170v1](https://arxiv.org/abs/2610.27170v1) (submitted 2026-10-19), [HTML](https://arxiv.org/html/2610.27170).
- **Date checked and version examined**: 2026-10-22 / v1.
- **Research questions** (user study):
  - RQ1: How does Sidecar affect attention allocation and focus, and at what cost in mental effort?
  - RQ2: How does Sidecar affect users' ability to make forward progress while waiting?
  - RQ3: How do participants use Sidecar in their thinking and agent navigation, and what usage patterns emerge?
  - Underlying question: what do agent micro-waits look like for daily users, and can a parallel assistant make them productive without risking unwanted actions on the artifact?
- **Method, data, and comparison conditions**:
  - **Formative study (§3)**: interviews with 12 users of agentic tools at a large tech company (11 of them used these tools multiple times a day), critical-incident recall, reflexive thematic analysis (13 themes from about 60 codes), plus short follow-up sessions on in-progress prototypes.
  - **System (§4)**: Sidecar is a Chrome extension (62 JavaScript modules, service worker proxying LLM calls). A wait opens when a prompt is sent and closes when the response stream ends. The context bundle includes the conversation, prompt in flight, unsent composer text, reasoning trace, editor/canvas contents, streamed code, previews, and elapsed time. **Decision cards** name implicit choices the agent made; **Explore cards** name paths the user has not committed to. Suggestions appear as small text below the chat (no pop-ups), are suppressed while the user types, and stale ones are retired. Models as reported: gemini-3.5-flash-lite (suggestions, situation inference) and gemini-3.1-flash-lite-image (Visualize); median generation 1.46 s text, 3.99 s image.
  - **User study (§5)**: 16 participants from a large tech company (8 video generation, 8 web prototyping), about 60 minutes each, $25 compensation. Within-subjects, Latin-square counterbalanced: Sidecar vs. baseline (same platform without Sidecar). Under-specified tasks (three related video clips; a potluck dish-assignment tool; an interactive browser game). Data: 7-point Likert items with selected NASA-TLX items, interaction logs, think-aloud, exit interviews. Analysis: two-sided Wilcoxon signed-rank tests with Benjamini–Hochberg correction (q = .05).
- **Claims and evidence** (all as reported by the extraction; the statistic type, median or mean, for the survey scores was not confirmed):
  - Behavior across 119 logged waits (56 baseline, 63 Sidecar): median wait was similar (76 s vs. 72 s). Time switched away from the agent tab fell from 35% to 13%. Participants left the tab in 26 of 56 baseline waits vs. 7 of 63 Sidecar waits.
  - Of 112 suggestions shown (58 explore, 54 decision), 45 (40%) were expanded, 28 were staged to the main composer, 14 of those were sent without further editing, and 5 (4.5%) were explicitly dismissed. 14 of 16 participants typed in the Sidecar chat at least once (54 messages).
  - Survey (7-point scales):

    | Measure | Sidecar | Baseline | p |
    |---|---:|---:|---:|
    | Attention fragmentation (lower is better) | 3.0 | 6.0 | 0.018 |
    | Progress made while the agent worked | 5.0 | 2.0 | 0.004 |
    | Involvement in what the AI was doing | 5.0 | 3.5 | 0.005 |
    | Considered alternatives they would not have thought of | 6.0 | 4.0 | 0.021 |
    | Mental demand (higher is worse) | 5.0 | 2.5 | 0.003 |

  - Qualitative: a read-only, ambient design let people stash rough ideas without fear of changing the artifact. Decision cards exposed unspecified choices; six participants caught an unwanted decision mid-run. Suggestions reaching too far ahead, or arriving in quick succession, raised cognitive load. Switching away was more common in video tasks (mostly a spinner) than in prototyping (agent trace to watch).
- **Limitations and threats to validity** (authors, §7.4): 16 participants in one lab session, durability unknown, five cited novelty; little personal stake and short tasks, learning the interface and feeling rushed may have raised reported workload; the integrated design does not isolate which component drives the effect (shared context, side chat alone, suggestion cards, task domain); predicting wait duration from early-run signals was not accurate enough for pacing. The authors recommend a longer deployment on participants' own tasks. **Our additions**: one company, the baseline is "no intervention" rather than another distraction aid, and the mental-demand result points the opposite way from the other measures.
- **Comparison with related work**: not checked. The excerpt we read did not expose the related-work section in a form we verified, and we did not search for prior work on wait-time interfaces. Do not treat Sidecar as "first" of anything.
- **Free-to-run reproduction plan**: the study cannot be reproduced as is (internal participants, Sidecar release status unconfirmed, paid model calls). A free substitute is a paper-and-notes diary: for one week, log each agent wait (length, what you did, whether you switched away, whether you noticed an unstated decision afterwards). This tests the micro-wait characterization on one person and measures nothing about Sidecar. Untested.
- **Usage status**: proposed (design ideas below); not trialed.
- **Unconfirmed points and next checks**: venue and acceptance; the last ~4,000 characters of the HTML (end of discussion or appendix); PDF cross-check of every number above; whether Sidecar code or prompts are public; the exact statistic (median or mean) in the survey table; related-work section.

## Design ideas worth trying (not demonstrated by the paper)

1. Keep the side channel **read-only** toward the main artifact, so brainstorming is safe.
2. Show the agent's implicit decisions as short cards while the run is still going, so wrong turns are caught early.
3. Tune suggestion distance and frequency: one step ahead is comfortable; bursts are costly.
4. Treat waiting as two parallel monitoring jobs (agent progress and own thinking), not a clean handoff.

## Summary

The paper characterizes agent micro-waits (a minute or two per turn) from interviews with 12 daily agent users and tests Sidecar, a same-tab side chat that reads the agent's run, with 16 participants in a within-subjects lab study. Reported effects: time away from the agent tab fell from 35% to 13%, attention fragmentation ratings improved, participants reported more progress and involvement, and decision cards helped them notice under-specified prompts, while mental demand ratings rose. The study is small, single-company, and does not separate Sidecar's components. Primary HTML checked through an extraction tool, numbers not cross-checked against the PDF, no reproduction, venue unconfirmed.

[Collection index](README.md) | [Reading list](../../docs/reading-list.md)
