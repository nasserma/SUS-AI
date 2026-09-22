# SUS-AI Principles

The general principles of sustainable AI use. Each principle is stated so it can
be checked — every one has at least one **sus check** (in [`checks/`](checks/))
that tests it, and the recipes (in [`recipes/`](recipes/)) carry the operational
detail.

---

## P1 — Guardrails, not abstinence

Avoiding AI is not a sustainable practice; unexamined and uncritical AI use is
not either. The sustainable position is structured and disciplined use. Understand
the AI tool and constrain where it could do harm [1][2].

## P2 — Verify before trust

AI tool results are drafts and need verification and revision. Carefully and
thoroughly verify AI tool results and take responsibility for them. All facts and
claims must be verified against a source other than the AI tool that produced
it. [3]

## P3 — Right-size the AI tool to the task

AI tool usage has a significant energy and financial cost; most tasks do not need
the most computational and resource intensive AI tool or model. Choosing the
lowest-cost AI tool or model is best practice, locally-hosted when possible for
data sovereignty, cloud when unavoidable. Sustainable AI use minimizes energy around
financial cost whenever feasible.

## P4 — Keep judgment-bearing work human

AI drafts and humans decide [1][2]. Tasks that require weighing values must be left
to humans who are able to accept responsibility.

## P5 — Know where your data goes and maintain sovereignty

Every piece of data sent to a non-local (cloud) service is data leaving your
control, permanently. Understanding the path of your data (device → harness
→ API → provider → retention) is a precondition for every privacy decision.

## P6 — Secrets stay local, permissions are non-persistent

Secrets, especially credentials, live in one place locally and are scoped as
narrowly as the task allows. Secrets are never shared with untrusted tools,
especially AI tools. Any credentials that cannot maintain these strict constraints
are rotated frequently.

## P7 — Log enough to audit, not enough to surveil

Auditability of your own AI use requires records, but records of other people's
interactions require restraint. Keep enough history to answer "what did the system do
and why" for auditing purposes, but no more.

## P8 — Rebuildable beats backed-up

A configuration you cannot rebuild from its documentation is not owned, it is
borrowed, including the AI model itself. Sustainable AI infrastructure is
described well enough to be reconstructed.

## P9 — Practices decay; revisit and revise continuously

AI tools, models, providers, and terms of service change faster than configurations
do. An AI infrastructure setup that was sustainable in the past is not necessarily
one that is sustainable now.

---

Each principle maps to **sus checks** in [`checks/`](checks/) and, where setup is
involved, to a recipe in [`recipes/`](recipes/).


## References

[1] Kestin, G., Miller, K., Klales, A., Milbourne, T., Ponti, G. (2025).
"AI tutoring outperforms in-class active learning: an RCT introducing a novel
research-based design in an authentic educational setting." *Scientific Reports*,
15. DOI: [10.1038/s41598-025-97652-6](https://doi.org/10.1038/s41598-025-97652-6)

[2] Bastani, H., Bastani, O., Sungu, A., Ge, H., Kabakci, Ö. (2025).
"Generative AI Without Guardrails Can Harm Learning: Evidence from High School
Mathematics." *PNAS*, 122.
DOI: [10.1073/pnas.2422633122](https://doi.org/10.1073/pnas.2422633122)

[3] Lee, H.-P., Sarkar, A., Tankelevitch, L., Drosos, I., Rintel, S., Banks, R.,
Wilson, N. (2025). "The Impact of Generative AI on Critical Thinking:
Self-Reported Reductions in Cognitive Effort and Confidence Effects From a Survey
of Knowledge Workers." *CHI 2025*.
DOI: [10.1145/3706598.3713778](https://doi.org/10.1145/3706598.3713778)
