# SUS Checks — How to Run Them

**SUS checks** are short, binary (pass/fail) checklists for evaluating whether your use of AI is
sustainable from two perspectives:

- **[Human interaction](human-interaction.md)** — is your AI use sustainable for *you*?
  Skills development and retention, judgment, learning, autonomy.
- **[Technical](technical.md)** — is your AI use sustainable for *everything else*?
  Privacy, data sovereignty, credentials, energy, rebuildability.

## When to run them

- **When setting up** a new AI tool, harness, or workflow.
- **On a schedule** thereafter — at least every 6 months, because tools and terms of service
  change faster than configurations do (P9).
- **After any material change**: new provider, new model, new integration, new data
  sensitivity.

## What passing means

Passing does not correspond to certification and decays in time. A check you pass today
can fail tomorrow because a provider changed a retention policy, not because you did anything.
The purpose is to make the failure visible and motivate you to mitigate or repair it. The recipes
in [`recipes/`](../recipes/) exist to fix the technical ones, and the guidelines in
[`guidelines/`](../guidelines/) exist to fix the human ones.

## Adding checks

Checks are deliberately few. A checklist that covers everything gets skimmed. New
checks are added only when they test something a person can actually verify in under
a minute and would otherwise plausibly get wrong — see [CONTRIBUTING.md](../CONTRIBUTING.md).
