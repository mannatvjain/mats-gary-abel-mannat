# mats-gary-abel-mannat

MATS assessment (mentor: Gary Abel). Play a DNA-synthesis-company biosecurity
officer: investigate a "mystery" DNA order that the internal screening tool
returned **no close matches** for, determine what it codes for, and decide
whether to flag it as a biosecurity concern — accepting that **false positives
are costly**, so a flag requires sufficient confidence. Deliverable is a short
written investigation plan (Part 1) plus a small Python demo (Part 2). See
`ASSESSMENT.md` for the full prompt.

## Stack
- **Language**: Python 3
- **Key dependencies**: Biopython (`Bio.Seq` for translation/ORF work, `Bio.Blast.NCBIWWW`/`NCBIXML` for remote BLAST), `requests` for NCBI E-utilities if needed. No DB; the sequence is the input.
- **Targets**: runs locally / in a notebook; uses **publicly available** tools only. No access credentials in any committed file or in the writeup.

## Architecture

```
  mystery DNA (ASSESSMENT.md)
        │
        ▼
  6-frame translation        ── nucleotide-level screen missed it; the internal
  + ORF extraction              tool likely keys on DNA identity, so a codon-
        │                       reoptimized / AT-rich rewrite can evade it.
        ▼                       Translating to protein recovers conserved signal.
  protein homology search    ── BLASTp (or hmm/profile) against public protein
  (remote BLAST / DBs)          DBs → candidate function + source organism.
        │
        ▼
  interpret hits  ──►  flag / no-flag decision
  (identity, coverage, e-value, what the top hit IS, organism risk)
```

Key hypothesis to test, not assume: a DNA-level miss + visibly AT-rich/skewed
codon usage is the classic *homology-evasion-by-recoding* pattern — confirm or
refute it by searching at the **protein** level.

## Conventions
- **No LaTeX in chat.** Use Unicode (ρ, σ, ·, ², ∑) or ASCII code blocks instead.
- **No credentials, ever.** Don't commit API keys / NCBI accounts; don't paste them in the writeup (explicit assessment requirement).
- **Confidence over recall.** Flagging is asymmetric: only flag with sufficient evidence; document the reasoning either way.
- **Reproducible demo.** The Part 2 script takes the sequence as input and prints its outputs; capture real outputs in the writeup.
- **Minimal & fast.** Few moving parts; pick a couple of steps and get them returning real results rather than building the whole pipeline.

## Dev commands
```bash
# setup
python3 -m venv .venv && .venv/bin/pip install biopython requests

# run the screening demo on the assessment sequence
.venv/bin/python screen.py            # (script TBD — see PLAN.md)
```
<!-- update once screen.py and any helpers exist -->

---

## Agent Protocol

You are one of many short-lived Claude sessions working on this project. The user relies on Claude to write code — knowledge must transfer between sessions via docs, not memory. You will not remember prior conversations. The docs are your memory.

### Before starting work
1. Read `INDEX.md` to understand the repo layout.
2. Read `PLAN.md` to see what's done and what's next.
3. Read `LOG.md` (latest entry) to understand where the last session left off.
4. Read any `*_REFERENCE.md` files listed in `INDEX.md` before writing code that touches those domains. Do not guess at APIs or platform behavior — it's documented there for a reason.
5. Read `CONTEXT.md` if it exists — it describes the problem domain and any external systems.

### During work

#### Planning (required for non-trivial tasks)
Before making changes, write a short ASCII plan and show it to the user:

```
+-------------------------------------+
| Task: <short description>           |
+-------------------------------------+
| 1. <step>                           |
| 2. <step>                           |
|    - <substep>                      |
| 3. <step>                           |
+-------------------------------------+
```

Wait for confirmation before proceeding. Keep plans concise.

#### Recap (required after completing each action)
After completing work, show an ASCII recap:

```
+-------------------------------------+
| Recap: <short description>          |
+-------------------------------------+
| Files edited:                       |
|  * path/to/file                     |
|    - <what changed>                 |
| Insights saved:                     |
|  > REFERENCE_DOC.md                 |
|    - <what was documented>          |
+-------------------------------------+
```

#### Documenting new knowledge
When you learn something non-obvious — a platform gotcha, an API quirk, a pattern that works — write it to the appropriate `*_REFERENCE.md` file immediately. If no reference doc exists for that domain yet, create one and add it to `INDEX.md`. This is how you pass knowledge to the next session.

### Handoff (end of every conversation)
When the user runs `/close` or the conversation is ending, complete this checklist:
1. Update any `*_REFERENCE.md` files with patterns learned this session.
2. Update `PLAN.md` — mark completed items `[x]`, add new items if the plan changed.
3. Append a dated entry to `LOG.md`: what changed, what's unfinished, what the next session should pick up.
4. Update `INDEX.md` if any files were added or removed.
5. If anything is half-finished, note it clearly in `LOG.md` so the next agent doesn't have to guess.
