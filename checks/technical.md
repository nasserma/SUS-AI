# SUS Checks — Technical

Is your AI use technically sustainable, including privacy, data sovereignty,
credentials, energy, and access? This checklist is meant to help you find out;
run it top to bottom, per AI tool or harness in use, with every item pass/fail.
**Any fail motivates action and does not constitute a crisis.** See the [recipes](../recipes/)
to fix these.

Each item in the checklist maps to the principle(s) it tests.

---

**T1 — Data path known.** (P5) For each kind of data this tool touches, I can state
where it physically goes — device → harness → API → provider → retention — in one
sentence, without looking it up.

**T2 — Sensitive work has a local path.** (P3, P5) For workloads involving personal,
confidential, or legally sensitive data, a local or self-hosted processing option
exists and is the default — cloud is the exception that must be justified case-by-case,
not the default.

**T3 — Secrets inventoried and scoped.** (P6) Every API key, token, and password the
system uses is in a credential store (not a config file that travels, not a shell
history), and each is scoped to the minimum the task requires.

**T4 — No secrets in anything shareable.** (P6) Configs I could publish, prompts,
transcripts, logs, and screenshots contain no live credentials — verified by
actually searching, not by assuming.

**T5 — Retention known and acceptable.** (P5) I know what the provider retains, for
how long, and how my data is used. I have checked this within the last 6 months.

**T6 — Logging: enough to audit, no more.** (P7) The system keeps enough history to
answer "what did it do and why" — and does not keep sensitive data from myself or
others.

**T7 — Energy conscious.** (P3) Routine low-complexity tasks do not default to an AI
tool or model that is overly capable; model choice per task class is a decision
that I made or verified, not a default setting.

**T8 — Rebuildable from documentation.** (P8) This setup could be reconstructed
from scratch, from its documentation alone, by myself or someone else, and that
documentation exists and is up-to-date.

**T9 — Backup proven by restore.** (P8) The most important state (configs,
credentials inventory, knowledge bases) has been restored from backup at least
once in the past 6 months.

**T10 — Change detection.** (P9) I have processes in place to be made aware of
when a provider changes terms, retention, or pricing that affects my AI setup.

**T11 — Failure blast radius known.** (P6, P5) If this tool, its secrets, or its
provider were compromised tomorrow, I can name what is exposed and how far it
reaches. What I can name as exposed is an acceptable risk to me.
