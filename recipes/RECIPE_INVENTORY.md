# SUS-AI Recipe Inventory (PROPOSED, for maintainer review)

**Status:** proposed; reviewed by the maintainer before any of it is final.
This is the proposed recipe inventory for the MVP; the maintainer reviews before any of it is
final. Recipes themselves are drafted under the same contract structure for the MVP-flagged set.

**Derivation sources:** the four setup areas identified in the original pre-repo
plan (model-selection, credentials, data-flow, notifications), the T1-T11 checks
needing technical fixes, and the guidelines' operational needs. Grounding reality:
the maintainer's infrastructure (a self-hosted harness on Linux with local model serving,
network-level DNS filtering, remote access, SSO, and a self-hosted cloud), generalized
per the recipe model: recipes state what a setup must achieve, not which products
provide it. The product inventory used during derivation lives in an internal
decision record, not in public repo content.

**MVP flag definition (per contract):** the recipe is needed by a first-year MVP user
to satisfy the targeted checks regardless of which harness they run.

---

## Proposed recipes

| # | Working title | One-line goal | Targeted checks | MVP | Derivable today |
|---|---|---|---|---|---|
| R1 | Model routing and right-sizing | Configure model selection so routine work runs on small/local models and large models are a justified exception | T7 (P3) | YES | YES |
| R2 | Credential inventory and scoping | Move every credential the AI setup uses into a credential store, scoped to minimum task requirements | T3, T4 (P6) | YES | YES |
| R3 | Data-flow mapping | Produce and maintain a one-sentence-per-data-kind map of where data physically goes (device, harness, API, provider, retention) | T1, T5 (P5) | YES | YES |
| R4 | Sensitive-work boundary | Establish and enforce the local-default processing path for sensitive workloads; cloud becomes the justified exception | T2 (P3, P5) | YES | YES |
| R5 | Secret-free shareables | Establish the scrubbing verification practice: searchable proof that shareable configs, prompts, transcripts, and logs contain no live credentials | T4 (P6) | YES | YES |
| R6 | Audit logging without surveillance | Configure logging that answers "what did the system do and why" without keeping other people's transcripts, keystrokes, or unneeded data | T6 (P7) | YES | YES |
| R7 | Rebuildable-from-documentation | Bring the setup to the state where it could be reconstructed from scratch from its documentation alone | T8 (P8) | YES | YES |
| R8 | Backup proven by restore | Establish the most-important-state inventory and run the restore test that proves backup works | T9 (P8) | YES | YES |
| R9 | Provider change detection | Establish the scheduled re-check and change-notification practice for provider terms, retention, and pricing | T10 (P9) | YES | YES |
| R10 | Failure blast-radius assessment | Map what is exposed if a tool, token, or provider is compromised, and reduce the answer to something acceptable | T11 (P6, P5) | YES | YES |

## Checks with no recipe (knowledge/behavioral items; guidelines-owned)

- **T1 and T5** carry knowledge-state components a setup recipe cannot install: the
  user must know the data path and retention state, and re-verify within 6 months.
  R3 and R9 establish the practices that make the knowledge current, but the checks
  ultimately test user knowledge. Noted per the contract's category wording.
- **T7** has a behavioral half (someone decides model choice per task class) that R1
  operationalizes; the decision itself is the user's.
- **T6** has a restraint component (logging OTHERS is the surveillance line) that no
  recipe enforces; R6 configures the audit side only.

## Intentionally not recipes

- **Anything H-series** (human-interaction checks): behavioral, owned by guidelines,
  not setup. No recipe can verify "I attempted before I looked."
- **Harness-specific configuration files:** excluded by Stage-0 decision 7: the user's
  primary AI adapts the recipe to their harness; SUS-AI publishes no product configs.
- **Webpage/deployment recipes:** the repo is content-only until the maintainer signals publish;
  deployment recipes would presuppose a hosting posture he has not chosen. Deferred
  decision record candidate if Stage 1 reveals demand.

## Relationship to the pre-repo plan

The original setup-area stub list (model-selection, credentials, data-flow,
notifications) from the pre-repo plan maps into this inventory as follows: model-selection → R1; credentials →
R2 + R5; data-flow → R3 + R4; notifications → R9. The remaining five recipes (R6-R10)
had no guide stub: R7 and R8 were implicit in the checks (rebuildability, restore) and
became recipes in the recipe model; R6 and R10 were promoted to explicit recipes
because T6 and T11 are the checks a prior internal review found unoccupied at
personal scale.

## Open items for the maintainer's review

1. Confirm the MVP flag set (all ten flagged YES; argument: each targets a check a
   first-year MVP user plausibly fails and can fix in minutes).
2. R4 (sensitive boundary) is the territory an internal prior review identified as
   unoccupied; confirm it ships in the MVP or is deferred as the hardest recipe to
   generalize.
3. Recipe depth: single-file per recipe (current template) vs directory per recipe with
   verification sub-files. Single-file recommended at this scale.