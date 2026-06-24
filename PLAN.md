# Plan

## Now
- [ ] **Part 2 demo — translation + ORF** (`screen.py`): take the sequence as
      input, do 6-frame translation, extract the longest ORF, print the protein.
- [ ] **Part 2 demo — protein homology**: run the ORF protein through a public
      search (BLASTp via `Bio.Blast.NCBIWWW`, or a documented alternative);
      capture top hits (identity, coverage, e-value, hit description + organism).
- [ ] **Record real outputs** from the mystery sequence into the writeup.
- [ ] **Part 1 writeup** (`WRITEUP.md`): ~100–200 word step-by-step approach.
- [ ] **Flag / no-flag decision** with reasoning, given the asymmetry.

## Next
- [ ] Sanity checks: confirm the long ORF / frame; note codon-usage skew (AT-rich)
      as the evasion signal that motivates searching at the protein level.
- [ ] Document any tool gotchas (NCBI rate limits, BLAST submission quirks) in a
      `*_REFERENCE.md` and add it to `INDEX.md`.
- [ ] Final pass: ensure no credentials anywhere; outputs reproducible.

## Done
- [x] Scaffold project from the new-agent schema (docs skeleton + agent protocol), git repo local + remote
- [x] Capture the assessment prompt in `ASSESSMENT.md`
- [x] Fill in project-specific docs (`CLAUDE.md`, `CONTEXT.md`) from the assignment
