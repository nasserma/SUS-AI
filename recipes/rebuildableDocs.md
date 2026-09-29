# Recipe R7: Rebuildable From Documentation

**Date:** 2026-09-20 | **Checks targeted:** T8 (P8) | **MVP:** yes | **Status:** draft for maintainer review

## Goal

Bring the AI setup to the state where it could be reconstructed from scratch, from
its documentation alone, by someone who is not you. That is the only backup test
that proves anything, and the discipline that makes the setup owned rather than
occupied.

## SUS checks targeted

- **T8, Rebuildable from documentation.** The setup could be reconstructed from
  scratch, from its documentation alone, by someone who is not you, which also
  means the documentation exists.

## Recipe (give this to your supervised AI)

Help me bring my AI setup's documentation to rebuildable state. Work from my
existing configuration as the reference, but write documentation, never copy config
fragments (the scrubbing rule applies to the documentation too).

1. **Inventory the setup's moving parts.** With me, list what would have to be
   reconstructed: the harness and its configuration, model serving, integrations,
   credential dependencies (names and locations, never values, per recipe R2),
   data locations, and any scheduled tasks.

2. **Test the documentation honestly.** For each moving part, check whether
   documentation exists that a competent stranger could follow. Mark each as
   documented, underdocumented, or undocumented. Do not flatter my existing docs.

3. **Write what is missing.** For each gap, write the missing piece as a
   from-scratch guide: what to install, what to configure, what values are chosen
   freely versus required, and where credentials come from (by reference to the
   store, never by value). One file per component, short enough to follow.

4. **Record the choices.** Where a setting is a choice rather than a requirement
   (thresholds, timeouts, model routing defaults), record the chosen value and the
   reason. A rebuild needs the reasons, not just the values.

5. **Schedule the proof.** The documentation claim is proven by an actual rebuild,
   not by writing. Agree with me on when the first from-scratch rebuild test runs
   (a quiet weekend, a spare machine or a container), and record the result. T9
   (recipe R8) covers restoring state; T8 is about the instructions being complete.

## Constraints (what the supervised AI must never do)

- Never copy lines out of my live configuration files into the documentation;
  write from scratch against what each setting does. Live files leak in ways
  owners do not notice.
- Never include a credential value, hostname, or identifying path in documentation;
  placeholders only.
- Do not modify my live configuration while documenting; read it, describe it,
  change nothing.

## Verification (run after the setup)

- **T8:** Hand the documentation to the test: could someone who is not you rebuild
  the setup from these files alone? The practical pass, short of a full rebuild, is
  the walkthrough test: for each moving part, the documentation names every step
  and every freely-chosen value, and nothing references "the thing on my machine"
  without saying where it lives. Full proof comes at the scheduled rebuild (step 5).

## Known gaps

- Documentation decays at the speed of configuration change (P9). Tie the
  documentation to a re-check: any functional change to the setup (recipe R9's
  change detection) re-opens the corresponding documentation section.
- A rebuild test that has never run is documentation that has never been read
  critically; treat T8 as provisional until the first rebuild has been attempted.