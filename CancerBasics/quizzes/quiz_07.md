# Quiz 7 — Tumour Evolution, Heterogeneity, Purity, Ploidy and VAF

10 questions · ~25 minutes · calculator allowed, notes closed. Answer key: `answer_keys/answer_key_07.md`.

Use **VAF = CCF · p·m / (p·C + 2(1 − p))** where needed.

---

**Q1. (Multiple choice)** A truncal mutation is best described as one that:

- A. Is found only in metastases
- B. Arose in or before the most recent common ancestor of all cancer cells, so it is present in every cancer cell
- C. Has a VAF of exactly 0.5
- D. Was inherited from a parent

**Q2. (Calculation)** Purity 0.7, diploid region (C = 2), clonal heterozygous mutation (m = 1). What is the expected VAF?

**Q3. (Calculation)** Purity 0.5. A mutation has VAF 0.10 in a diploid region with m = 1. What is its CCF? Is it clonal?

**Q4. (Short answer)** A tumour suppressor mutation shows VAF 0.55 in a tumour of purity 0.6, where p/2 = 0.30. Give the most likely biological explanation and what you would check in the CN output to confirm it.

**Q5. (Multiple choice)** A clonal mutation sits in an 8-copy amplicon (C = 8) on only one copy (m = 1), purity 0.6. Its VAF will be approximately:

- A. 0.30
- B. 0.11
- C. 0.60
- D. 0.86

**Q6. (Short answer)** Explain why a copy-number caller can find two equally good purity/ploidy solutions (e.g. ploidy ~2 vs ~4). Name one line of evidence that can break the tie.

**Q7. (Multiple choice)** In a region gained after whole-genome doubling, a mutation found on 2 of 4 copies most likely arose:

- A. After the doubling
- B. Before the doubling
- C. In the matched normal
- D. It cannot be timed

**Q8. (Short answer)** At 60× depth, what is the approximate probability of seeing ≥ 3 ALT reads for a true variant at VAF 0.05? What does this imply about a negative result at a known hotspot?

**Q9. (Short answer)** A patient with EGFR L858R lung cancer progresses on erlotinib. A progression biopsy shows EGFR T790M at low VAF. Explain (a) the biological mechanism of resistance, (b) why its VAF is lower than L858R's, and (c) one finding that would make you suspect a germline T790M instead.

**Q10. (Multiple choice)** Which of these is proposed in Hanahan 2022 as a new dimension that is largely **invisible to WGS**?

- A. Sustaining proliferative signalling
- B. Genome instability and mutation
- C. Non-mutational epigenetic reprogramming
- D. Enabling replicative immortality

---

**Score:** ____ / 10
Record your score in `progress_tracker.md`.
