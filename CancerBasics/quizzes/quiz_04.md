# Quiz 4 — Germline vs Somatic Variation

10 questions · ~20 minutes · closed book. Answer key: `answer_keys/answer_key_04.md`.

---

**Q1. (Multiple choice)** A child carries a heterozygous variant in every cell tested; neither parent carries it. This is best described as:

- A. Somatic
- B. Mosaic
- C. De novo germline
- D. Clonal haematopoiesis

**Q2. (Multiple choice)** Tumour purity is ~50%. Which result is most consistent with a clonal somatic heterozygous mutation in a diploid region?

- A. Tumour VAF 0.48, normal VAF 0.51
- B. Tumour VAF 0.25, normal VAF 0.00
- C. Tumour VAF 0.92, normal VAF 0.49
- D. Tumour VAF 0.03, normal VAF 0.06

**Q3. (Short answer)** A germline heterozygous variant shows VAF 0.50 in the normal and 0.85 in the tumour. What happened in the tumour, and why does this matter if the gene is a tumour suppressor?

**Q4. (Multiple choice)** The main purpose of a panel of normals (PoN) in Mutect2 is to:

- A. Remove the patient's own germline variants
- B. Flag recurrent technical artifacts seen across many unrelated normals processed the same way
- C. Estimate tumour purity
- D. Identify CHIP variants

**Q5. (Short answer)** How does Mutect2 use a population germline resource such as gnomAD? Why can patient ancestry affect how well this works?

**Q6. (Multiple choice)** Which genes are most frequently mutated in clonal haematopoiesis (CHIP)?

- A. KRAS, BRAF, EGFR
- B. DNMT3A, TET2, ASXL1
- C. BRCA1, BRCA2, PALB2
- D. APC, SMAD4, CDKN2A

**Q7. (Short answer)** Why is peripheral blood a problematic matched normal for a patient with AML or myeloma? Name two alternative normal sources.

**Q8. (Short answer)** Across a tumour–normal pair, dozens of high-confidence mutations show tumour VAF ~0.3 and normal VAF ~0.03–0.05, proportionally. Several known drivers were filtered as `normal_artifact`. What is the likely biology, and what would you do?

**Q9. (Multiple choice)** Cross-individual contamination of the tumour sample typically produces:

- A. A few high-VAF calls in driver genes
- B. Many low-VAF "somatic" calls at sites that are common germline SNPs in the population
- C. Loss of all calls on chrY
- D. Increased Ti/Tv ratio

**Q10. (Short answer)** Your tumour–normal analysis shows a pathogenic BRCA2 frameshift at VAF ~0.5 in the normal. List three things that must happen before (or instead of) simply reporting it.

---

**Score:** ____ / 10
Record your score in `progress_tracker.md`.
