# Recipe R1: Model Routing and Right-Sizing

**Date:** 2026-09-20 | **Checks targeted:** T7 (P3) | **MVP:** yes | **Status:** draft for maintainer review

## Goal

Configure model selection so that routine low-complexity tasks run on the smallest
capable model (local or small-tier when available), and large or reasoning models are
a justified exception rather than the default. A reader who completes this recipe can
answer, for each task class they run through AI, which model serves it and why.

## SUS checks targeted

- **T7, Energy conscious.** After this recipe, routine tasks do not default to the
  largest available model; model choice per task class is a decision someone made,
  not a leftover default.

## Recipe (give this to your supervised AI)

Set up model routing for my supervised AI using the following requirements. Do not
hardcode any product names I have not given you; adapt to whatever serving stack I
describe. Ask me before transmitting anything to a cloud provider.

1. **Inventory my task classes.** Ask me to list the recurring task types I send
   through AI (examples: short questions, drafting and summarizing, code assistance,
   document analysis, hard reasoning). Record the list with me.

2. **Map each task class to a model tier.** Propose, for each class, the smallest
   model tier that plausibly completes it, on this ladder:

   - **Local small model** for routine, low-stakes, high-volume tasks (classification,
     formatting, short questions, boilerplate). This is the default for anything
     where a wrong answer is cheap to detect and fix.
   - **Local or cloud mid-tier model** for standard drafting, summarizing, and
     code assistance, where quality matters but reasoning chains are short.
   - **Large or reasoning model, cloud** reserved for tasks that earn it: hard
     analysis, multi-step reasoning, high-stakes drafting. Reasoning models
     substantially increase energy cost per query relative to standard models of
     the same size; treat every reasoning-model invocation as a purchase with real
     cost, not a habit.

3. **Configure the routing decision in my harness.** Where my harness supports
   model-per-task or per-conversation model selection, set the defaults according to
   the mapping. Where it does not, write me a one-page decision card (task class,
   model, why) that I can consult until selecting the model is habit.

4. **Add a review trigger.** Tell me what would make a routing mapping stale (a new
   cheaper capable model, a provider change, a new task class) so I can re-run this
   recipe rather than silently drifting.

## Constraints (what the supervised AI must never do)

- Do not transmit any API keys, tokens, or credentials while configuring routing;
  if a provider key is needed, stop and ask me to enter it through my credential
  store, never into the chat.
- Do not send my existing configuration files, workspace paths, or conversation
  history to any cloud endpoint.
- Do not enable data-retention or training-consent settings on any provider account
  without asking me first.
- Do not delete or downgrade any existing model configuration without showing me the
  mapping and getting my confirmation.

## Verification (run after the setup)

Run these from the SUS checks:

- **T7:** For each task class you listed in step 1, name the model now serving it.
  Every class has a named model that is not the largest available one, and you can
  say why it is enough. Passes when no routine task class routes to the largest
  model by default.

Also re-run **T1** (data path known) afterwards: changing model routing changes where
prompts physically go. If any newly routed class now sends data to a provider whose
data path you cannot state in one sentence, fix the routing or the data path before
considering this recipe done.

## Known gaps

- Quantified per-query energy varies by provider, model, and reasoning mode by an
  order of magnitude or more; this recipe deliberately gives the practice (right-size,
  default small, reasoning as exception) rather than numbers that rot. Re-run this
  recipe when your provider lineup changes.
- Harnesses without model-selection capability (single-model products) cannot express
  routing; for those, the decision card (step 3) is the deliverable and T7 passes only
  when the single model is justified for the task mix.