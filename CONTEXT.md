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

## How it's evaluated (inferred)
- Flagging is **asymmetric**: false positives are explicitly called costly, so a
  flag needs sufficient confidence; a defensible no-flag with reasoning is valid.
- Reasoning quality matters as much as the result — why each step, what it tells
  you, and honest handling of uncertainty.

## The investigation, in shape (not yet executed)
1. **Translate, 6 frames + find ORFs** — a clean long ORF in one frame says it's
   a protein-coding sequence and gives the amino-acid sequence to search.
2. **Search at the protein level** (BLASTp / profile search) — the internal tool
   missed it at the DNA level; codon-reoptimized or AT-rich rewrites evade
   nucleotide identity while the protein stays conserved. Protein homology
   recovers candidate **function** and **source organism**.
3. **Interpret hits** — identity, query coverage, e-value, and crucially *what*
   the top hit is and *what organism* it's from → drives the risk judgment.
4. **Decide** — flag only with sufficient confidence of biosecurity risk;
   otherwise document why it's benign / inconclusive.

## Domain vocabulary
- **Synthesis screening** — checking ordered DNA against known hazards before
  manufacture (cf. IGSC / SecureDNA-style screening).
- **6-frame translation** — translating all three reading frames on both strands.
- **ORF** — open reading frame; a start→stop stretch that may encode a protein.
- **Homology search / BLAST** — finding similar known sequences; BLASTp = protein
  vs protein, BLASTn = nucleotide vs nucleotide.
- **Homology evasion / codon reoptimization** — rewriting codons (often toward a
  skewed, e.g. AT-rich, usage) so DNA-level identity drops but the protein is
  unchanged — a known way to slip past naive nucleotide screens.
- **Select agent / sequence of concern** — the toxin/pathogen categories a flag
  would escalate toward.

## Constraints
- Publicly available tools/libraries only; **no access credentials** committed or
  in the writeup.
- Quick demo, not a production screener — implement a couple of steps well.
- Network access needed if running remote BLAST against NCBI.

## Who's who
- **Mannat** — building this (AI-safety MATS applicant).
- **Gary Abel** — MATS mentor / assessor.
