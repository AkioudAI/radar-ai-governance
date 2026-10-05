# RADAR

Governance evidence for AI applications and agents, made by AKIOUD AI.
[Version française](README.fr.md)

RADAR is the black box and the logbook of a company's AI. The black box records
what the AI did; the logbook keeps what people decided about it. Together they
help the company answer, with evidence in hand: what does your AI do, and who
controls it?

This repository presents the product. It contains no source code.

## Who it is for

Companies that run generative-AI applications or AI agents, or build them for
others, and need to show how that AI is overseen. The evidence is organised
around the EU AI Act and the GDPR. Its users are the governance or compliance
lead, the developer who connects the application, and auditors with read-only
access. RADAR is not intended for live monitoring of biometric,
emotion-recognition, computer-vision or physical systems.

## What a customer does with it

1. Installs RADAR on its own server, where the data stays, with a 30-day
   evaluation licence.
2. Creates accounts (viewer, operator, administrator) with a password and, for
   privileged accounts, a six-digit code.
3. Registers the AI application: its purpose, what it must never do, who is
   responsible. For example: "it never grants a refund on its own".
4. Goes through a fixed set of points drawn from the EU AI Act and the GDPR,
   stating for each whether it applies and why, and names who oversees the
   application and with what authority.
5. Connects the application with a few lines of code. Each action of the AI then
   sends RADAR a record: what it did, and whether a human took part.
6. RADAR stores each record in tamper-evident form and analyses it. Signals
   appear, such as a possible IBAN in a conversation, or a decision taken
   without the required human approval.
7. A named reviewer takes the signal from a review queue, decides, and writes
   down why.
8. If it is serious, the reviewer opens an incident: facts, impact, a corrective
   action with an owner and a due date, and a recorded decision on whether to
   inform an authority.
9. When asked to account for the AI, the company generates an evidence pack for
   one application and one period, as PDF, HTML and JSON, in French and
   English: what the system is, what it did, what people decided, what is
   missing.
10. An auditor sees who decided what and when, and RADAR's integrity check shows
    whether any record was changed since.

RADAR also shows, for each requirement, which evidence is present or missing,
and handles retention,
legal hold, controlled deletion, backup and restore. After the licence ends,
data stays readable and exportable; nothing new is recorded.

## How it connects to an AI application

RADAR does not sit between the application and the model. It intercepts no call
and never talks to the model.

The application reports what happened. Where the AI acts, the developer adds a
call that sends a record: the system and its version, the type of action,
whether a human intervened, and the content the company chose to send. For each
system, the company sets whether raw content is kept, redacted where supported,
or dropped after analysis. The call goes through the Python library supplied
with RADAR, or a plain HTTP request from any language.

As a result:

- RADAR does not depend on a particular model, provider or agent framework.
  Supported combinations are listed in the compatibility matrix delivered with
  the product.
- RADAR has no control over the application. If RADAR stops, the application
  keeps running; the Python library holds records and sends them later.
- RADAR sees only what it is sent. It flags gaps in the sequence and late
  records, but cannot guess a record that was never sent.

## What RADAR guarantees, and what it does not

- **Deterministic analysis.** No generative AI: written rules, namely
  personal-data detectors, fixed checks and the monitoring policies the company
  configures. The same record always gives the same result, and each result
  names the rule and its version.
- **A signal is a hint, not a verdict.** RADAR writes "possible IBAN", not
  "personal data confirmed". A person decides, and RADAR keeps that decision.
- **No promise to detect everything.** A rule finds only what it was written
  for; no signal does not mean no problem. The product says so next to each
  result and in each evidence pack.
- **Tamper-evident, not immutable.** A later change to a record shows up in the
  integrity check. RADAR is no witness to activity it was never sent.
- **Not done, by design.** RADAR does not block or filter the AI, certify
  compliance, replace legal advice, decide the company's legal role, notify any
  authority on its behalf, or decide in place of a person.

What the company gets is evidence that it monitors its AI with a method, that
named people review and decide, and that a later rewrite of the record would
show.

## Status and access

RADAR is in early access, on request, for companies established in France.
After a short qualification, a company runs a self-directed 30-day evaluation
on its own infrastructure, on terms agreed in writing. There is no public
download and nothing is sold online. Continued use is covered by a separate
written agreement.

Ask for access: <https://www.akioud.ai/contact>

## Source code

The RADAR source code is proprietary and is not in this repository. See
[LICENSE](LICENSE).

RADAR is made by AKIOUD AI, a French company. <https://www.akioud.ai>
