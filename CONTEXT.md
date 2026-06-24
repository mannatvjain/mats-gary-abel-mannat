# Context

## What this is

A MATS assessment (mentor: Gary Abel). The scenario: I'm the biosecurity officer
screening orders at a small DNA synthesis company. A submitted "mystery" DNA
sequence returned **no close matches** from the company's internal screening
tool. I must determine (a) what the sequence codes for and (b) whether to flag
it as a potential biosecurity concern. The full prompt lives in `ASSESSMENT.md`.

## The deliverable
- **Part 1 (~10–20 min):** a concise (~100–200 word) written sketch of the
  investigation steps — for each step, what information it yields and how that
  information is used toward the flag / no-flag decision.
- **Part 2 (~20–40 min):** a short Python script implementing one or a few of
  those steps using publicly available tools, taking the sequence as input.
  Share the script, inputs, the **real outputs** from the mystery sequence, and
  what can (or cannot) be concluded. A quick demo — depth over completeness, but
  it must actually return a result. No credentials in the answer.

## What the prompt states about evaluation
- Flagging is **asymmetric**: the prompt says false positives are also costly, so
  a sequence should only be flagged with sufficient confidence of a biosecurity
  risk.

## Constraints
- Publicly available tools/libraries only; **no access credentials** committed or
  in the writeup.
- Quick demo, not a production screener — implement a couple of steps well.
- Network access needed if running remote BLAST against NCBI.

## Who's who
- **Mannat** — building this (AI-safety MATS applicant).
- **Gary Abel** — MATS mentor / assessor.
