# Contributing to the SUS-AI Project

The SUS-AI project is an evolving body of knowledge, not a software project:
**submissions are documentation only.**

---

## What can be contributed

Suggested changes to principles or guidelines should be suggested through raising
issues, with discussion to follow. Standard contributions include:

- **Recipes** (`recipes/…`) for AI infrastructure components which are harness-agnostic,
  written for the user to execute themselves or with AI assistance.
- **SUS checks** — additions to the check lists in `checks/`: binary, pass/fail items
  a person can run against their own AI use. Rarely accepted; every proposal goes
  through the bar below.
- **Translations** of existing content.

## The recipe template

Every recipe follows this structure, in this order:

1. **Goal** — one paragraph: what this setup achieves and for whom.
2. **SUS checks targeted** — explicit mapping to the checks in `checks/`. If a setup
   fails a check it does not target, say so in a *Known gaps* section rather than
   staying silent.
3. **Recipe** — setup instructions, written as instructions to be executed with the
   assistance of the user's supervised AI: complete and annotated, with every
   credential as a placeholder and every non-public endpoint generalized.
4. **Constraints** — what the supervised AI must never do: transmit secrets, retain
   credentials, send data anywhere the recipe does not name.
5. **Verification** — which sus checks to run on the finished setup and what pass
   looks like. The user's own check run is the verification.

## The scrubbing rule (hard requirement)

Guides are **written from scratch against upstream documentation** — never
copy-sanitized from a live working setup. Before submitting, verify your guide contains:

- no tokens, keys, or passwords, including "test" ones;
- no usernames, email addresses, or internal hostnames;
- no workspace paths that identify you or your organization;
- no provider endpoints that are not genuinely public.

## How contributions are vetted

The maintainers vet every contribution. Translations and evidence pointers need
only the scrubbing rule and an accurate source. New check proposals go through
the bar below. **Recipes**, the contribution type that can actually harm a reader,
must follow the recipe template and the scrubbing rule above, and satisfy the
vetting questions below.

Vetting then asks three questions, applied in order: is it safe (scrubbing holds,
nothing exposes a reader whose AI follows it exactly), is it checkable (the targeted
checks actually test what the recipe claims), is it consistent (no contradiction
with principles, guidelines, or other recipes — deliberate differences are argued in
the recipe).

Accepted recipes are marked with the review date. Rejection comes with reasons; a
revised resubmission is always welcome.

## The bar for new sus checks

A new check is accepted only if it tests something a person can **verify in under a
minute** and would **plausibly get wrong** without the check. Checks are few on
purpose and are not meant to replace rigorous verification, validation, and certification.

## License

By contributing, you agree your contribution is released under the repository
license ([CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)).
