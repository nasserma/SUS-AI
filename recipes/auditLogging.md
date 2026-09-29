# Recipe R6: Audit Logging Without Surveillance

**Date:** 2026-09-20 | **Checks targeted:** T6 (P7) | **MVP:** yes | **Status:** draft for maintainer review

## Goal

Configure logging that answers "what did my AI system do and why" while keeping no
record it has no use for: no other people's transcripts, no keystrokes, no
collected-because-we-could data. The audit side of P7 is what a recipe can set up;
the restraint side is the rule this recipe encodes.

## SUS checks targeted

- **T6, Logging: enough to audit, no more.** The system keeps enough history to
  answer "what did it do and why," and does not keep transcripts of other people,
  keystrokes, or data it has no use for.

## Recipe (give this to your supervised AI)

Help me configure audit logging for my AI setup. Confirm each retention decision
with me before applying it.

1. **Inventory current logging.** With me, list what my AI setup already logs and
   where: harness logs, provider-side history, conversation transcripts, error
   logs, integration webhooks. For each, note what it records and who can read it.

2. **Define the audit question.** Agree with me on what the log must be able to
   answer: at minimum, "which model handled this request, when, with what data
   kinds, and what did the system do with it." Everything logging must record to
   answer that is in scope; everything else is a candidate for deletion.

3. **Configure retention per log.** For each log in the inventory: keep it if it
   serves the audit question, scope it to what serves the question, and set a
   retention period we agree on. Default proposal: error and action logs kept
   months, full conversation transcripts kept only where I consciously need them,
   and nothing kept solely by habit.

4. **Apply the restraint line.** Audit what MY system does with MY interactions.
   It does not log other people: no transcripts of other people's interactions
   with me, no keystroke capture, no recording of data my setup has no use for.
   If any current logging captures other people's content (shared conversations,
   meeting transcripts, contact data), flag it for my decision on removal.

5. **Write the log policy down.** One page: what is logged, where, retention, who
   can read it, and the P7 line ("enough to audit, not enough to surveil") as the
   test for any future log source. Save it with my setup documentation.

## Constraints (what the supervised AI must never do)

- Do not enable any provider-side history, training, or analytics setting while
  configuring logging; provider-side retention is recipe R3's territory and this
  recipe covers only what my system itself records.
- Do not read other people's data or messages to demonstrate what logging captures.
- Do not delete any existing log without my confirmation; propose, I decide.

## Verification (run after the setup)

- **T6:** For each log in the inventory: does it serve the audit question, and is
  its retention period set? Does any log capture other people's interactions or
  data it has no use for? Passes when the answer to the first question is yes for
  every log and the second is no.

## Known gaps

- Provider-side conversation history is not under this recipe's control; the map
  from recipe R3 records it, and turning provider history off is a T5/T1 concern.
  This recipe owns what your system itself stores.
- Some harnesses log by design with no retention configuration; where retention
  cannot be set, the honest outcome is a recorded exception in the log policy and
  a T6 answer that names the limitation.