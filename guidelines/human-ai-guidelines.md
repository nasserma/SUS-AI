# SUS-AI Guidelines for (Humans) Using AI Tools

Basic guidelines for humans using AI tools to avoid loss of skills, judgment, or
data unintentionally. These guidelines are deliberately brief: the **SUS checks**
in [`checks/`](../checks/) are for more detailed audit and voluntary compliance.

---

## 1. Attempt first, assist second

Try to complete tasks yourself before resorting to an AI tool. Write the paragraph,
attempt the derivation, draft the code, before you resort to AI assistance. Guardrailed AI use (attempt, then check) is what the learning evidence supports; consumption
of pre-made answers is what the learning evidence warns against. (Maps to check H7.)

Your attempt does not need to be successful, but engaged and disciplined problem-
solving is how we learn and maintain our cognitive abilities. If you cannot remember
your last unassisted attempt at a task that you routinely delegate to AI tools
(or other humans!), that is a signal that you should attempt it yourself.

## 2. Verify anything "load-bearing"

Any outcomes and outputs resulting from your AI tool use are **your responsibility.**
Whether they be go/no-go decisions, numerical data, reports, code, you must
carefully verify all outcomes and outputs against direct sources and your own
judgement. The test is not "does it sound reasonable," it is instead "what would
the consequences be for myself and others if this is wrong."

Verification is proportionate: a draft output that will not be acted on can stay
unverified. However, quantities, calculations, citations in a written deliverable
or code in a production-ready software system get verified and validated. AI tools
can assist in drafting, but are not authoritative. (Maps to check H2.)

## 3. Delegate drudgery, not decisions

Repeated tasks that do not involve judgement and can be easily verified or reviewed
are often where AI helps most. Recommendations, evaluations, and judgement or anything
you would be personally responsible for may use AI for advice, but you decide and take
responsibility. (Maps to check H3.)

## 4. Match the model to the task

Small and local for routine work; large and/or cloud only when needed for the complexity
of the task. Defaulting all of your AI use to the largest and most capable AI model
costs energy, money, and data exposure for no real benefit. If you are unsure about
whether the AI tool you are using is well-matched to the task, or how the data provided
to it will be handled once it leaves your system, that should be corrected. (Maps to checks T7, T1.)

## 5. Treat prompts as publication

Assume anything you type into a cloud AI tool could be read by a stranger, retained
indefinitely, and used in training. Do not provide secrets, sensitive personal data
(yours or others) or anything else that you would be uncomfortable putting on a
postcard and dropping in the mail. Sensitive data should be reserved for local self-
hosted AI tools with known data paths and boundaries. (Maps to checks T1, T2.)

## 6. Keep receipts

Keep adequate records of what your AI tools have done including: which tool/model,
which task, and what you changed afterwards. Your work using AI tools should be
understandable by you (now or in six months!) and explainable to others. Document
enough to audit but not so much as to build a surveillance archive of your activities
and interactions. Documentation includes what you retain, not just what the
systems log. (Maps to check T6.)

## 7. Disclose when it matters

Where the audience would reasonably want to know (academic work, professional
deliverables, published writing, anything someone might rely on), say how AI
tools were used with the understanding that disclosures do not reduce responsibility
and accountability. (Maps to check H9.)

## 8. Review and re-verify continuously

AI tools change and evolve constantly, especially those hosted in the cloud/off-premises.
AI models are swapped, providers change retention and privacy policies, features disappear
and reappear with new names and behavior. The setup you vetted six months ago might not be
the setup you are running now. Re-run the [SUS checks](../checks/) on a schedule, or have your
supervised AI act for you and flag what changed. (Maps to checks H10, T10.)
