# Recipe R4: Sensitive-Work Boundary

**Date:** 2026-09-20 | **Checks targeted:** T2 (P3, P5) | **MVP:** yes | **Status:** draft for maintainer review

## Goal

Establish a sensitive-work boundary: a named, enforced zone in your workflow where
personal, confidential, or legally sensitive data is processed locally by default,
with cloud processing becoming the justified exception rather than the default. A
reader who completes this recipe can state which kinds of work never leave their
device, and what has to happen for that to change.

## SUS checks targeted

- **T2, Sensitive work has a local path.** For workloads involving personal,
  confidential, or legally sensitive data, a local or self-hosted processing option
  exists; cloud is the justified exception, not the default.

## Recipe (give this to your supervised AI)

Help me define and implement a sensitive-work boundary for my AI use. This recipe
changes defaults; confirm each change with me before applying it.

1. **Classify my work.** With me, sort my recurring AI task classes (the list from
   recipe R1, plus anything else I name) into three buckets: nonsensitive (shareable
   with a cloud provider under its standard policy), personal (my own private data,
   not for other eyes), confidential (professional, legal, or third-party data with
   obligations attached). When I am unsure where a kind belongs, treat it as the
   stricter bucket and tell me why.

2. **Establish the local path.** For the personal and confidential buckets, establish
   what local processing exists on my machine: a locally served model of adequate
   capability for the task, or non-AI tooling. If my machine cannot serve a
   sufficient local model, say so plainly and present the options (a smaller local
   model, upgrading local hardware, or a self-hosted service I control) rather than
   defaulting the work to a cloud provider.

3. **Write the boundary rule.** Produce a short standing rule in my words, of the
   form: "Data kinds X and Y are processed locally by default. Cloud processing of
   them requires a named justification (no local capability, one-off scale need) and
   my explicit choice at the time." Have me confirm the rule.

4. **Implement the friction.** Configure my harness so that the default path for
   marked data kinds is the local one: local model defaults, prompts that carry
   sensitive data routed or refused per my rule. Where the harness cannot enforce
   this, give me the decision card version: what to ask for and what never to paste.

5. **Record the exceptions.** Every time cloud processing of marked data is
   justified later, it is a decision, recorded with its reason. The boundary is
   working when the exceptions are visible and rare.

## Constraints (what the supervised AI must never do)

- Never send data I have marked personal or confidential to any cloud endpoint,
  including for analysis of this very recipe, unless I explicitly approve that
  specific transfer at the time.
- Do not read or copy confidential files to demonstrate capability; if a sample is
  needed, I provide a synthetic or redacted one.
- Do not configure any provider integration for marked data kinds without showing
  me its data path first (recipe R3's map).

## Verification (run after the setup)

- **T2:** Name the processing path for each personal and confidential data kind on
  your list. Each has a local or self-hosted default, and cloud use of it requires
  a justification you can state. Passes when the boundary rule exists, is
  implemented in the harness or the decision card, and the defaults hold.

## Known gaps

- Local model capability is the binding constraint: some confidential work
  (large-document analysis, high-stakes drafting) may exceed what a local model
  serves well. The recipe's honest answer is that T2 then passes only if the work
  waits for local capability or the data is de-identified first; convenience is not
  a justification. Where that tradeoff is unacceptable to a reader, that is a
  known, visible exception to record, not a silent default to override.
- This is the hardest recipe to generalize; boundary placement is personal. The
  recipe supplies the structure (buckets, default, exception record); the reader
  supplies the classification.