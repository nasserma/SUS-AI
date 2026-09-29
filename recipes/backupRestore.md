# Recipe R8: Backup Proven By Restore

**Date:** 2026-09-20 | **Checks targeted:** T9 (P8) | **MVP:** yes | **Status:** draft for maintainer review

## Goal

Identify the most important state in the AI setup and prove, by actually restoring
it, that the backup works. A backup that has never been restored is a hypothesis;
this recipe turns it into evidence.

## SUS checks targeted

- **T9, Backup proven by restore.** The most important state (configs, credentials
  inventory, knowledge bases) has been restored from backup at least once.

## Recipe (give this to your supervised AI)

Help me establish what must be backed up in my AI setup and prove the backup works
by restoring it. Do not transmit any backup or credential off my machine; backups
go where I direct.

1. **Inventory the important state.** With me, list what would genuinely hurt to
   lose: harness and model-serving configuration, the documentation from recipe R7,
   the credential inventory (names and locations, never values, per recipe R2),
   knowledge bases and long-lived documents, configuration of integrations, and
   anything else I cannot stand to rebuild from scratch.

2. **Classify by rebuild cost.** For each item: is it (a) regenerable from the
   documentation alone (cheap: rebuildable per recipe R7), (b) regenerable with
   effort but not from documentation alone (accumulated state, tuning, history),
   or (c) irreplaceable (data with no copy anywhere)? The second and third classes
   are what backups are for; the first class needs only the documentation to be
   kept current.

3. **Design the backup.** For the (b) and (c) items: what backs them up, to where,
   how often, encrypted how, and who can read the backup medium. Keep it as simple
   as the risk allows; a backup system too complex to maintain is a backup that
   silently stops.

4. **Run the restore.** This is the recipe's core. Perform one real restore of each
   backed-up class into a scratch location: restore the files, verify the content
   is complete and readable, and confirm any credential references resolve to the
   credential store (recipe R2), not to copies in the backup. Record date, scope,
   and result.

5. **Schedule it.** Agree on a restore-test interval (a restore that passed once in
   2024 is a hypothesis again) and what triggers an off-schedule test: any change
   to what counts as important state.

## Constraints (what the supervised AI must never do)

- Never include live credential values in any backup this recipe creates; the
  credential inventory is names and locations. Secrets are replaced from the
  credential store at restore time, never from backup media.
- Do not send any backup to a cloud location I have not explicitly approved;
  confirm the destination for each backup class with me.
- Do not delete or overwrite any existing backup without my confirmation.

## Verification (run after the setup)

- **T9:** For each item in the (b) and (c) classes: has it been restored from
  backup at least once, into a scratch location, with the restore verified complete?
  The record of that restore (date, what was restored, where) is the evidence.
  Passes when every non-regenerable item has one dated restore test.

## Known gaps

- Backup media rot silently: a scheduled restore test is the only honest evidence,
  and the interval must be short enough that a dead backup is discovered before it
  is needed. Six months is a reasonable default; shorter if the state changes fast.
- Restores are the moment backup scope errors surface (something important was
  never in the backup). Treat every restore test as also a scope review.