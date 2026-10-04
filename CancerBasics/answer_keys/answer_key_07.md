# Answer Key — Quiz 7

Section references point to `module_07_evolution_purity_vaf.md`.

---

**Q1 — B.**
Truncal (clonal) mutations arose in the founder clone or its ancestors, so every cancer cell inherits them. VAF depends on purity and copy number, so it is not fixed at 0.5 (C). An inherited variant is germline (D). *(Section 1)*

**Q2 — 0.35.**
VAF = 0.7 × 1 / (0.7 × 2 + 2 × 0.3) = 0.7 / 2.0 = **0.35** — the familiar p/2. *(Section 3)*

**Q3 — CCF ≈ 0.40; subclonal.**
CCF = VAF × (p·C + 2(1 − p)) / (p·m) = 0.10 × (1.0 + 1.0) / 0.5 = **0.40**. About 40% of cancer cells carry it, so it is subclonal — provided the copy number and purity are right. *(Section 3)*

**Q4 — Model answer.**
A VAF well above p/2 in a tumour suppressor suggests **loss of the wild-type allele** — the second hit (Module 6).
- Copy-neutral LOH with the mutant duplicated (C = 2, m = 2) gives 0.60.
- Deletion of the wild-type allele (C = 1, m = 1) gives 0.43.

0.55 fits copy-neutral LOH best. Check the CN/LOH output for the segment: total CN ≈ 2 and **BAF split / LOH** (minor allele CN = 0) at heterozygous SNPs. Also confirm the normal VAF is 0, to exclude a germline variant. *(Section 3; Module 6 Section 6)*

**Q5 — B (≈ 0.11).**
0.6 × 1 / (0.6 × 8 + 0.8) = 0.6 / 5.6 ≈ **0.107**. It is clonal but looks subclonal if you ignore copy number. *(Section 3 table)*

**Q6 — Model answer.**
Depth ratios are **relative** to the sample's average copy number. Doubling every segment's CN and lowering purity can reproduce exactly the same ratios (e.g. p 0.80/ploidy 2 vs p 0.67/ploidy 4), and allelic BAF patterns double too. Tie-breakers:
- clonal SNV **multiplicity clusters** (e.g. a cluster at m = 1 of 4 supports WGD);
- odd allelic states that are implausible in one solution;
- orthogonal purity evidence — pathology, a known clonal driver's VAF, flow-cytometry DNA index.

*(Section 4)*

**Q7 — B.**
The mutation was present on the chromosome before it was copied, so the doubling duplicated it (m = 2). A mutation after the doubling hits one of the four copies (m = 1). This is the basis of multiplicity timing. *(Sections 3 and 7)*

**Q8 — About 0.58.**
Binomial(60, 0.05): expected 3 ALT reads, and P(≥ 3) ≈ 0.58. So a true 5% VAF variant is missed roughly 40% of the time at this depth (more with real-world error). A negative result at a hotspot is **weak evidence of absence** for low-VAF subclones; consider purity, review the locus in IGV, or use a deeper targeted assay or RNA. *(Section 6)*

**Q9 — Model answer.**
- (a) T790M is the **gatekeeper** residue in the EGFR kinase. Methionine restores ATP affinity, so ATP out-competes reversible first-generation inhibitors. Signalling resumes despite the drug.
- (b) L858R is **truncal** (all cancer cells, often with the mutant allele gained). T790M is in a **resistant subclone** selected by the drug, so its CCF < 1 and its VAF is lower. Lower purity in the progression biopsy also contributes.
- (c) Germline suspicion: T790M at VAF ~0.5 in the **matched normal**, or present **before any EGFR-inhibitor treatment** at ~0.5 in the tumour. Germline T790M is rare and linked to familial lung cancer risk.

*(Worked example; Section 5)*

**Q10 — C.**
Non-mutational epigenetic reprogramming changes gene expression without changing DNA sequence, so WGS cannot see it directly; methylation and RNA data can. A, B and D are earlier hallmarks/enabling characteristics with clear genomic footprints. *(Section 8)*
