# Recipe R3: Data-Flow Mapping

**Date:** 2026-09-20 | **Checks targeted:** T1, T5 (P5) | **MVP:** yes | **Status:** draft for maintainer review

## Goal

Produce and maintain a data-flow map: for each kind of data the AI setup touches, a
one-sentence statement of where it physically goes, plus the provider retention
state, re-verified on a schedule. A reader who completes this recipe can pass T1 and
T5 from knowledge, and knows when to re-check.

## SUS checks targeted

- **T1, Data path known.** For each kind of data this tool touches, you can state
  where it physically goes (device, harness, API, provider, retention) in one
  sentence, without looking it up.
- **T5, Retention known and acceptable.** You know what the provider retains, for
  how long, and whether your data trains anything, checked within the last 6 months.

## Recipe (give this to your supervised AI)

Help me build a data-flow map for my AI setup. Work from documentation, not from my
live files; do not transmit any of my data while doing this.

1. **List the data kinds.** Ask me what kinds of data flow through my AI use
   (examples: prompts and conversations, documents I upload, code, credentials
   metadata, personal notes, other people's information). Record the list.

2. **Trace each path.** For each data kind, walk the chain with me and write one
   sentence per kind in this shape: "kind X: entered on my device, processed by my
   harness locally, sent to provider Y's API, retained Z days, used for training:
   no." Use the provider's published data policy as the source; do not guess, and
   tell me when a provider's policy is ambiguous so I can check it myself.

3. **Mark the sensitive ones.** Mark each kind as nonsensitive, personal, or
   confidential per my own classification. Anything confidential or legally
   sensitive gets flagged for recipe R4 (sensitive-work boundary).

4. **Record retention per provider.** For each provider in the map: retention
   period, training-use policy, and the URL of the policy page you read, with the
   date you read it. This is the T5 evidence.

5. **Make the map maintainable.** Save the map as a file I keep with my setup
   documentation, with a re-verify date 6 months out, and tell me what should
   trigger an earlier re-check (a provider announcement, a new integration, a new
   data kind).

## Constraints (what the supervised AI must never do)

- Do not transmit any of my actual data, files, or prompts to any endpoint while
  mapping; the map is built from documentation and my answers, not from live data.
- Do not fetch provider policy pages through any account or session of mine;
  plain public web access only.
- Do not state a retention or training fact from memory. If you cannot source a
  policy claim to a page you can show me, say so.

## Verification (run after the setup)

- **T1:** For each data kind on the list, state the path in one sentence without
  opening the map. Passes when you can do this for every kind.
- **T5:** Open the map's retention section. Each provider row has a policy URL and
  a reading date within the last 6 months, and you can say whether your data trains
  anything. Passes when no provider row is stale.

## Known gaps

- Provider policies change without notice; the 6-month re-verify (T10's practice,
  recipe R9) is what keeps this map honest. A map is a snapshot, not a certificate.
- Enterprise and educational provider tiers often differ from consumer tiers; the
  map must record which tier each of your accounts is on, or it will be wrong.