# Recipe R10: Failure Blast Radius

**Date:** 2026-09-20 | **Checks targeted:** T11 (P6, P5) | **MVP:** yes | **Status:** draft for maintainer review

## Goal

Map what is exposed if a tool, token, or provider in your AI setup were compromised
tomorrow, and reduce that exposure to something you can accept and state. Blast
radius is not a number you look up; it is the consequence of choices (credential
scope, data placement, retention) that recipes R2 through R4 already made. This
recipe audits the result.

## SUS checks targeted

- **T11, Failure blast radius known.** If this tool, its token, or its provider were
  compromised tomorrow, you can name what is exposed and how far it reaches, and
  that answer is small enough to accept.

## Recipe (give this to your supervised AI)

Help me assess the failure blast radius of my AI setup, component by component.
Reason from my configuration and the R2/R3 records; do not probe any live service.

1. **Enumerate the failure points.** From the credential inventory (R2) and the
   data-flow map (R3), list every component whose compromise would matter: each
   provider token, each integration, the harness itself, the local model serving,
   each cloud provider account.

2. **Trace the exposure of each.** For each failure point, answer in writing: if
   this were compromised tomorrow, what exactly becomes readable (which data kinds
   from the R3 map), what becomes actionable (what the credential's scope permits,
   per R2), and what else it reaches (chained access: does this token open other
   doors?). Name the worst realistic case, not the worst imaginable one.

3. **Grade the answer.** For each failure point: is the blast radius small enough
   to accept (a scoped, revocable token touching nonsensitive data), or does it
   reach sensitive data or irreplaceable state? Anything reaching personal or
   confidential data kinds (R4's buckets) needs a specific justification for why
   that risk is taken.

4. **Reduce where the answer is not acceptable.** For each failure point graded
   unacceptable: apply the reduction (narrow the credential scope per R2, move the
   data per R4, remove an integration that never earned its exposure). Re-trace
   after each reduction. Where exposure cannot be reduced below acceptable, that
   is a recorded accepted risk with a reason, not a shrug.

5. **Record the map of blast radii.** One file: failure point, what is exposed,
   reach, grade, accepted-with-reason or reduced. This is the T11 evidence, and it
   doubles as the incident-response card: when something does fail, the first hour
   of response is already written down.

## Constraints (what the supervised AI must never do)

- Do not probe, test, or authenticate against any live provider to "verify"
  exposure; this assessment reasons from the inventory and the map, not from live
  attacks.
- Never print credential values while tracing scope; use the scope descriptions
  from the R2 inventory.
- Do not send any of my data or configuration off-machine while assessing.

## Verification (run after the setup)

- **T11:** For each failure point on the list: state what is exposed and how far
  it reaches, from the record, in one or two sentences. Each answer is either
  accepted-with-reason or was reduced until it was. Passes when the map exists,
  every failure point is graded, and no unacceptable grade stands without a
  recorded reason.

## Known gaps

- Blast radius is a moving target: every credential rotation (R2), provider change
  (R9), or data-kind addition (R3) moves it. Tie this map's re-check to R9's
  schedule rather than treating it as a one-time assessment.
- Compromise of the machine itself dominates every per-provider radius; this
  recipe assumes the host is intact. Full-disk encryption and OS-level hardening
  are outside its scope, and worth naming in the record as assumptions.