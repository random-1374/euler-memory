# Euler: memory / session handover

> **PUBLIC FILE.** Read by the read-only `@Euler` workflow at the start of every run.
> Only write what is already fine on public PR #65: decisions, status, open items, log.
> Never: test items, item text or hashes, library content, keys or tokens, student data, personal details.

Raw URL: https://raw.githubusercontent.com/random-1374/euler-memory/main/EULER_STATE.md
New session: "You are Euler, Rachel's agent. Read EULER_STATE.md in random-1374/euler-memory and continue."

## Session protocol (no memory between sessions: this file IS the memory)
1. Read this file in full.
2. Read only the NEWEST reviews on ETH-StudyHub PR #65 (e.g. get_reviews perPage 5 on the last page; #65 has 70+ reviews), then check the open items.
3. Before ending: update **Status**, **Open items** and **Log**, then commit here (sessions with write access only; the workflow is read-only).
4. Billing: Rachel does NOT want API credits used. API-based sessions (client.beta.sessions) bill the API key. Prefer Claude Code logged in with Pro, or the @Euler workflow (Pro OAuth token). Keep reads small.

_Last updated: 22 Nov 2026, ~23:27 Zurich_

## Identity
- I am **Euler**, **Rachel's** agent (GitHub account `random-1374`), not the repo owner's.
- Owner of the site repo: `mrisrijgd1` ("Srish"). Their AI = "Maintainer AI" (posts as `mrisrijgd1`).
- Other agents: Okta = Jamie's agent (`9hjcsbgv2k-code`); Tartaruga (`TartarugaGemini`) supports Okta; Gemini-1 (Srish) was stopped 22 Nov.

## Repos and what goes where
| Repo | Visibility | What |
|---|---|---|
| `mrisrijgd1/ETH-StudyHub` | PUBLIC, `main` deploys to Pages | specs/eval *designs* in `handoff/`, mailbox. No items, no secrets, no student data, no training anything |
| `random-1374/euler-memory` (this repo) | PUBLIC | this memory file only |
| `random-1374/apertusTuning_env` | PRIVATE | **held-out test items**, harness code, run outputs |

- Mailbox = PR **#65**. Post as a **review with event COMMENT**. Sign "— Euler (Rachel's agent)", end with `<!-- euler-bot -->`.
- `main` does NOT require PRs (ruleset blocks only deletion/force-push). Never push to main anyway. Never merge.
- Ask first before `.github/workflows/`, `connector/`, SQL/Supabase, site-wide assets. Hands off: `FlashcardsAnalysis_designspace/`, `dive/`.
- A post that claims an action happened must come AFTER the action succeeds.

## Decisions (all from #65, 22 Nov)
- **Fine-tuning: PARKED.** Prepare no training env or data.
- **Budget (H1):** pilot on free Infomaniak credits → estimate → up to ~CHF 150 approved → more needs asking.
- **One eval plan** on Infomaniak: Apertus-v1.5-70B (thinking on/off), Qwen3.5-397B, Mistral-Small-4, Gemma-4-31B, Kimi-K2.6, Claude as ceiling. Harness: Inspect. Spec = `handoff/` on main (v2).
- **Item checkers:** Srish = maths, Rachel = physics, batches of ~10; nothing during 25 Jan–19 Feb 2027.
- **Infomaniak key:** after the team's edu setup. Until then no model runs.

## Status
- **#154 merged:** `.github/workflows/euler.yml` (read-only: contents: read, only writes = reviews on #65). Not live until the secret exists.
- **#155 merged:** handoff v2 is on main.
- **#153:** closed unmerged by the maintainer (22 Nov).
- **Library repo (`mrisrijgd1/ETH-StudyHub-library`, private):** Srish asked if past exams/scripts help. Answered YES on #65 (22 Nov, 23:18): read-only, for calibration only. Past exams/mocks (Analysis I, Lineare Algebra I, Physik I) for style/difficulty/topic weighting; scripts for notation and syllabus position; Übungsblätter/quizzes/`mcq/` only as inspiration for typical mistakes. Items stay newly written; verbatim or lightly changed items marked per item; each item records its calibration source (folder + file). Nothing into the library, nothing from it into the public repo.

## Open items
- [ ] **Waiting on Maintainer/Srish:** OK for the `euler.yml` prompt change (read this file at start + library rule), asked on #65 (review 6014849826). If yes, maintainer opens `euler/workflow-memory`.
- [ ] **Rachel:** `claude setup-token` (Pro) → send the token to Srish PRIVATELY → Srish adds secret `EULER_CLAUDE_CODE_OAUTH_TOKEN`.
- [ ] First `@Euler` mention = live test. Reply on #65 so the maintainer confirms bot reviews wake it (fallback: @-mention `@mrisrijgd1`).
- [ ] Cleanup (Rachel/Srish): delete branches `euler/mention-workflow`, `euler/handoff-companion-evals`, `euler/handoff-v2`.
- [ ] Create `eval/` in apertusTuning_env (README "never use as training data", item format, hash list) via branch + PR in this repo.
- [ ] First batch of ~10 maths items → Srish; ~10 physics items → Rachel.
- [ ] Scaffold Inspect harness in apertusTuning_env (no runs until the key exists). Pre-registration doc.

## Log (newest first)
- **22 Nov, 23:26:** Asked on #65 to add two lines to the workflow prompt: (0) WebFetch this file as memory; library = read-only calibration. Permissions unchanged.
- **22 Nov, ~23:25:** Memory moved to this public repo so the `@Euler` workflow can read it; apertusTuning_env keeps only a pointer.
- **22 Nov, 23:18:** Answered Srish's library question on #65 (review 6014819201): yes, read-only, calibration only (see Status). Posted from a Claude chat session acting as Euler, with Rachel's OK on the exact text.
- **22 Nov, ~22:35:** Maintainer merged #154 (euler.yml) and #155 (handoff v2). Rachel raised API-credit concern → session ended to save credits.
- **22 Nov, ~22:30:** Rebuilt v2 on a fresh branch → #155. Close of #153 refused; posted a correction on #65.
- **22 Nov, 22:25:** euler.yml made read-only and posted on #65.
- **22 Nov, evening:** #152 v1, point-by-point reply, first workflow file.
