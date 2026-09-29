# Recipe R5: Secret-Free Shareables

**Date:** 2026-09-20 | **Checks targeted:** T4 (P6) | **MVP:** yes | **Status:** draft for maintainer review

## Goal

Establish the standing practice of verifying, by actual search, that anything
shareable (publishable configs, prompts, transcripts, logs, screenshots, examples)
contains no live credentials before it leaves your machine. T4 is the search, not the
assumption; this recipe makes the search routine.

## SUS checks targeted

- **T4, No secrets in anything shareable.** Verified by actually searching, not by
  assuming.

## Recipe (give this to your supervised AI)

Help me set up a repeatable pre-share secret scan for my AI setup's shareable
artifacts. Do not transmit any file contents off my machine during this.

1. **Define the shareable set.** With me, list what I actually share or could share:
   project config files, dotfile snippets, prompt templates, conversation exports,
   log files, screenshots, public repositories, documentation. Record where each
   lives.

2. **Build the search.** For my platform, produce a small, reviewable search
   procedure (one or a few commands I can run myself) that scans those locations
   for credential-shaped strings: long random tokens, key-like prefixes my
   providers use, password-bearing lines, private-key file headers. The commands
   must be ones I can read and understand; no opaque script I would not audit.

3. **Anchor to my inventory.** Cross-check against the credential inventory from
   recipe R2: search for a distinctive fragment of each listed credential (the
   first several characters, never the full value) rather than relying only on
   generic patterns. A fragment search catches secrets a generic pattern misses.

4. **Make it habitual.** Propose how to attach the search to the moment of sharing:
   a manual checklist line, an alias, a pre-commit hook, or a scheduled scan of the
   directories where shareables live. Pick the lightest mechanism that I will
   actually use, and set it up.

5. **Handle a hit.** Tell me the procedure for when the search finds a live
   credential in something already shared: rotate the credential first (it is
   compromised, not merely exposed), then clean the artifact, then, where the
   artifact already went somewhere public, rotate regardless of cleanup.

## Constraints (what the supervised AI must never do)

- Never print a full credential value in search output or in this session; search
  by fragment or pattern and report file and line, not the value.
- Do not transmit file contents off-machine to "check them."
- Do not rotate or revoke anything without my explicit instruction; report the hit
  and stop.

## Verification (run after the setup)

- **T4:** Run the search over your shareable set, right now, once for practice.
  Zero hits after a genuine search (with the fragment list from R2) is the pass.
  The pass is the run, not the result: a search you did not run proves nothing.

## Known gaps

- Pattern-based secret scanning has false negatives (unusual credential shapes) and
  false positives; it reduces risk, it does not prove absence. The inventory-anchored
  fragment search (step 3) is the strong half; generic patterns alone under-detect.
- Screenshots are the leak path this recipe cannot search reliably; the practice is
  preventive: crop or avoid capture of credential-bearing windows rather than
  scanning after the fact.