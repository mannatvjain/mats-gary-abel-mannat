# MATS Assessment — DNA Synthesis Order Screening

**Mentor:** Gary Abel

## Scenario

You're the biosecurity officer in charge of screening orders at a small DNA
synthesis company. While reviewing an order you encounter the following mystery
sequence that didn't return any close matches to known sequences using the
company's internal sequence screening tool.

```
ATGAATCAACATAATACCCAAATCAATAAATTTATCTTTTTTAGTAGCTTCAGAATCATCAGTACCACCCCAATTCAATTTATCAACAATAATAGGACCAGCAACAGCAATAGCAACATATTCATCATTAGAAGCAGGAGAATTCAAAACAATACCAACAGCTTTTTTATTATCAGCAGTATTCCAAGTTTTACAAACAGCACCATTAGAATTACCTTTTTCACAATCACCAGCATGCAAATTATCAATACCAGAATTTTTATGAGATCTAATATGAACCAAACCCAT
```

## Part 1 (~10–20 min)

Sketch out your approach by briefly describing the steps you would take to
investigate the mystery sequence, with the goal of determining (a) what it codes
for, and (b) whether it should be flagged for follow-up as a potential
biosecurity concern. (Sequences should only be flagged if there is sufficient
confidence that they pose a biosecurity risk, as false positives are also
costly). Include a short description of what information you expect to gain from
each step, and how you would use that information in the investigation. A concise
list is fine (~100–200 words total).

## Part 2 (~20–40 min)

Write a short python script that implements one or more steps from your answer in
Part 1 using publicly available tools and libraries, and taking the sequence as
an input. Share the script, the input(s), the outputs you got from the mystery
sequence, and what (if anything) you can conclude from the outputs. This is meant
to be a quick demo, so pick one or a few steps and focus on getting them to
return a result, rather than implementing the entire process in detail. (And
please don't share any access credentials in your answer).
