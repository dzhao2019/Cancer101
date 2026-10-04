# Quiz 1 — DNA, Genes and the Central Dogma

10 questions · ~20 minutes · closed book. Answer key: `answer_keys/answer_key_01.md`.
Coordinates are GRCh38. You may use the codon table from Module 1 for Q5, Q6 and Q8.

---

**Q1. (Multiple choice)** The two strands of a DNA double helix are:

- A. Parallel and identical
- B. Antiparallel and complementary
- C. Antiparallel and identical
- D. Parallel and complementary

**Q2. (Short answer)** Write the reverse complement of `5′-ATGGCC-3′`, 5′→3′.

**Q3. (Multiple choice)** A read in your BAM has FLAG 16. Its SEQ field contains:

- A. The bases exactly as the sequencer read them
- B. The reverse complement of what the sequencer read, so it matches the + strand of the reference
- C. The complement (not reversed) of what the sequencer read
- D. The reversed (not complemented) sequence

**Q4. (Multiple choice)** Which statement about exons is true?

- A. Exons always encode protein
- B. Exons are removed during splicing
- C. Exons can consist partly or entirely of UTR sequence
- D. Exons always begin with the dinucleotide GT

**Q5. (Short answer)** Translate this mRNA into amino acids (one-letter or three-letter codes): `5′-AUG GCU UGG UAA-3′`

**Q6. (Multiple choice)** In a coding sequence, the codon GGT changes to GGC. This change is:

- A. Missense
- B. Nonsense
- C. Synonymous
- D. Frameshift

**Q7. (Multiple choice)** KRAS lies on the − strand. Your annotated report says `KRAS c.35G>A`. In the VCF, REF>ALT at that position is:

- A. G>A
- B. C>T
- C. G>T
- D. C>A

**Q8. (Short answer, 4 parts)** BRAF V600E is `c.1799T>A`. BRAF is on the − strand.

- (a) Which `c.` positions make up codon 600?
- (b) Which position within the codon does c.1799 occupy (1st, 2nd or 3rd)?
- (c) What REF>ALT would the VCF show?
- (d) The wild-type codon 600 is GTG. What is the mutant codon, and which amino acid does it encode?

**Q9. (Short answer)** Two labs analyse the same tumor and report the same genomic variant (same chromosome, position, REF and ALT) with different `c.` names. Neither lab made an error. Explain how this can happen, and what you would recommend so it doesn't happen again.

**Q10. (Short answer)** A blacklist BED file contains the line `chr12  25245349  25245350`. Which VCF `POS` does it cover? Explain the conversion in one sentence.

---

**Score:** ____ / 10 (Q8 counts as 1 point: 0.25 per part)
Record your score in `progress_tracker.md`.
