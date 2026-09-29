# Recipe R9: Provider Change Detection

**Date:** 2026-09-20 | **Checks targeted:** T10 (P9) | **MVP:** yes | **Status:** draft for maintainer review

## Goal

Establish the practice that notices when a provider changes terms, retention,
pricing, or capabilities in ways that affect your setup, before those changes
surface as breakage. This is P9's operational half: practices decay, and the decay
is usually announced somewhere you are not watching.

## SUS checks targeted

- **T10, Change detection.** You have a way to learn when a provider changes terms,
  retention, or pricing that affects this setup: a check on a schedule, a
  subscription to changelogs, or a review date in the calendar.

## Recipe (give this to your supervised AI)

Help me set up change detection for the providers my AI setup depends on. Work from
the provider list in my data-flow map (recipe R3); do not sign me up for anything.

1. **List the dependencies.** From the R3 map, list every provider my setup depends
   on: model APIs, serving platforms, credential providers, and any service whose
   change would alter where my data goes or what my setup costs. For each: what
   would change that matters to me (terms, retention, pricing, model availability).

2. **Pick a detection channel per provider.** For each, the lightest reliable
   channel: official status/changelog feeds, announcement pages, or (where none
   exists) a scheduled manual check. Prefer channels that notify me over channels
   I must remember to visit; set up only what I approve.

3. **Set the re-check schedule.** For the practices themselves (the R3 map, the R1
   routing, the R2 credential scopes): a scheduled re-run, at least every 6 months
   per H10, sooner for providers that change often. Put the dates in my calendar,
   not in a file I will forget.

4. **Define the supervised AI-assisted re-check.** Per P9, my supervised AI may act for
   me: on its own schedule it re-reads the providers' policy pages, compares
   against my recorded policy facts (URLs and dates from R3), and flags material
   differences to me when they surface, without waiting for the scheduled date.
   Record this delegation explicitly: what it may read (public policy pages only),
   what it may not do (change anything, transmit my data), and that it reports to
   me.

5. **Write the response rule.** Agree on what happens when a change is detected:
   which changes are informational (price slightly up), which re-open a recipe
   (retention change re-opens R3's map; model availability change re-opens R1), and
   which stop my use of that provider until reviewed.

## Constraints (what the supervised AI must never do)

- Do not create accounts, subscriptions, or email signups on my behalf; propose the
  channel, I click.
- Do not transmit my identity, my data, or my provider account details to any
  endpoint while checking policy pages; public pages, plain access only.
- Do not modify my configuration in response to a detected change without my
  explicit approval; detection reports, it does not act.

## Verification (run after the setup)

- **T10:** Name, for each provider in the R3 map, how you would learn about a
  change that matters: the channel, and the date of the last check. Passes when
  every provider has a named channel, and at least one scheduled or
  supervised-AI-assisted re-check has a recorded date.

## Known gaps

- Not every provider publishes a reliable changelog; where the channel is a
  scheduled manual check, the schedule is the discipline and the calendar entry is
  the evidence. Supervised-AI-assisted re-checking (step 4) reduces the burden but
  still reports rather than enforces.
- Change detection covers what providers announce. Silent degradations (model
  quality shifts, unannounced deprecations) surface through your own use; T10's
  honest scope is announced change.