# SUS-AI Recipes

Recipes are the setup layer of SUS-AI: harness-agnostic instructions for building
AI infrastructure that satisfies the SUS checks. A recipe states what a setup must
achieve, written so the user hands it to their own primary supervised AI, which
performs the actual setup and configuration on the user's system. SUS-AI writes the
recipe once; the user's AI adapts it to whatever harness they run.

You reach for a recipe when a SUS check fails and the fix is a setup change, not a
behavior change: a credential store to put secrets in, a data-path map, a backup
scheme that has actually been restored. The finished setup owes you a passing run of
the checks it targets — that run is the acceptance test, not the recipe author's
assurance.

## How a recipe is used

1. Pick the recipe matching the component you are setting up.
2. Give it to your supervised AI as the instruction for the setup task.
3. When the supervised AI reports the setup complete, run the SUS checks it targets;
   the checks are the acceptance test.
4. Fix what fails; re-run until the checks pass.

## Recipe template

1. **Goal**: what this recipe achieves and for whom.
2. **SUS checks targeted**: which checks from [`checks/`](../checks/) this setup is
   built to pass.
3. **Recipe**: the setup instructions themselves, written as instructions to an AI
   supervised AI: complete, annotated, with every credential as a placeholder and every
   non-public endpoint generalized.
4. **Constraints**: what the supervised AI must never do: transmit secrets, retain
   credentials, send data anywhere the recipe does not name.
5. **Verification**: which SUS checks to run on the finished setup, and what pass
   looks like.
6. **Known gaps**: where the recipe is honest about its limits: what it cannot
   cover, what decays, what the reader must supply.

## The scrubbing rule (hard requirement)

Recipes are **written from scratch against upstream documentation**: never
copy-sanitized from a live working setup. Live files leak in ways their owners do
not notice: tokens in environment defaults, internal hostnames, usernames, workspace
paths that identify people. A recipe written from scratch starts with placeholders
and adds only what the documentation says is needed; a sanitized live file starts
with everything and removes what the author remembered to remove.

A recipe must also never instruct the user's AI to transmit secrets anywhere, retain
credentials, or send data to any endpoint the recipe does not explicitly name.
