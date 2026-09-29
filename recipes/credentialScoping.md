# Recipe R2: Credential Inventory and Scoping

**Date:** 2026-09-20 | **Checks targeted:** T3, T4 (P6) | **MVP:** yes | **Status:** draft for maintainer review

## Goal

Move every credential the AI setup uses into a proper credential store, scoped to the
minimum each task requires, and verify that nothing shareable contains a live secret.
A reader who completes this recipe can name every credential their AI setup uses,
where it lives, and what it can reach.

## SUS checks targeted

- **T3, Secrets inventoried and scoped.** After this recipe, every API key, token,
  and password the system uses is in a credential store (not a config file that
  travels, not a shell history), each scoped to the minimum the task requires.
- **T4, No secrets in anything shareable.** Configs that could be published, prompts,
  transcripts, logs, and screenshots contain no live credentials, verified by
  actually searching.

## Recipe (give this to your supervised AI)

Help me inventory and consolidate the credentials used by my AI setup. Work locally;
do not transmit any credential value to any endpoint, including yours.

1. **Inventory.** Help me enumerate every credential my AI setup touches: provider
   API keys, model-serving tokens, harness integrations, webhook URLs, database
   passwords. For each, record: what it authenticates, where it currently lives
   (config file, environment variable, shell profile, credential store), and what
   the minimum scope for its actual use would be.

2. **Classify exposure.** Flag every credential that is (a) in a file that could
   travel (dotfiles, project configs, sync folders), (b) in shell history reach,
   or (c) broader in scope than its use requires (for example a full-account key
   where a scoped token would serve).

3. **Migrate.** One credential at a time: move it into my operating system's
   credential store or my harness's supported secret mechanism, update the consumer
   to read it from there, verify the consumer still works, and only then remove the
   old copy. Never print the secret value in a command, log, or transcript during
   this; refer to it by name only.

4. **Scope down.** For each credential that can be replaced by a narrower one
   (read-only token, per-project key, short-lived credential), generate the narrower
   one, switch the consumer, and revoke the broad one. Where the provider offers no
   scoping, record that fact: it becomes the blast-radius note in recipe R10.

5. **Purge copies.** After migration, help me search shell histories, editor
   backups, and sync directories for copies of the removed secrets and delete them.
   Do not search cloud services I have not approved.

## Constraints (what the supervised AI must never do)

- Never echo, print, or transmit any credential value, including in examples,
  error messages, or verification output. Refer to credentials by name only.
- Never write a secret value into any file, even temporarily.
- Never send any secret to an external endpoint for "validation" or testing.
- If you encounter a credential in a file you were not asked to process, report its
  location to me; do not move, copy, or transmit it.

## Verification (run after the setup)

- **T3:** Name every credential your AI setup uses. Each one answers: stored where
  (credential store name), scoped how, consumed by what. Passes when none lives in
  a config file that travels or in shell history, and each is scoped to minimum.
- **T4:** Actually search, with your supervised AI's help or your own grep: your
  shareable configs, a recent prompt transcript, and your log directory, for the
  first eight characters of each credential (never the whole value). Zero hits,
  verified by searching rather than assuming, is the pass.

## Known gaps

- Some harnesses require secrets in environment variables; a shell-environment
  secret is acceptable under T3 when set by the credential store at session start
  and not stored in any profile file. The check is storage location and lifetime,
  not mechanism.
- Credential stores differ across operating systems; this recipe is deliberately
  store-agnostic. Your supervised AI should discover and use the native mechanism on
  your platform rather than installing a new one.