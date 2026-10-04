# Answer Key — Quiz 4

Section references point to `module_04_germline_vs_somatic.md`.

---

**Q1 — C. De novo germline.**
The variant is in every cell, so it was present in the zygote, which means it arose in a parental egg or sperm. Because neither parent carries it, it is *de novo* rather than inherited. Mosaic variants (B) are present in only a subset of cells. *(Section 1)*

**Q2 — B.**
A clonal heterozygous somatic mutation in a diploid region has an expected VAF of about purity ÷ 2 = 0.25, and should be absent from the normal. The other options:
- A is a germline heterozygous pattern.
- C is germline plus LOH.
- D looks like CHIP.

*(Section 2)*

**Q3 — Model answer.**
The tumour has undergone **loss of heterozygosity (LOH)**: it lost the copy carrying the reference (wild-type) allele, so the variant allele dominates. In a tumour suppressor, this is the classic **second hit**. The inherited variant inactivated one copy, and losing the other copy removes the remaining function. It strongly suggests the germline variant is relevant to this tumour. *(Section 2; worked example, story 3)*

**Q4 — B.**
A PoN is built from many unrelated normals run through the same pipeline. Sites that appear variant in several of them reflect technical problems such as mapping, chemistry or reference errors. The patient's own germline variants (A) are removed using the matched normal and the population resource. *(Section 4; misconception 1)*

**Q5 — Model answer.**
Mutect2 uses population allele frequencies as prior evidence that an allele is germline. A common allele at a tumour VAF consistent with heterozygosity is likely germline, even if the normal has few reads at that site. That evidence feeds the `germline` filter.

Ancestry matters because population databases under-represent many ancestries. Rare variants common in an under-represented group may be missing from the resource. If the normal's coverage also happens to be thin, those germline variants can leak through as false somatic calls. *(Sections 4 and 5.3)*

**Q6 — B. DNMT3A, TET2, ASXL1.**
These epigenetic-regulator genes dominate CHIP. PPM1D and TP53 clones are enriched after chemotherapy or radiotherapy. The other options list common solid-tumour drivers (A, D) and hereditary-cancer genes (C). *(Section 5.2)*

**Q7 — Model answer.**
In AML or myeloma the malignant cells, or their precursors, circulate in the blood and bone marrow, so a blood "normal" contains tumour DNA. True somatic mutations then appear in the normal and get filtered (tumour-in-normal).

Alternatives (any two):
- cultured **skin fibroblasts**
- **nails** or hair
- sorted non-tumour cells, e.g. T cells, depending on the disease

Saliva and buccal swabs are weaker choices because they contain leukocytes. *(Section 3)*

**Q8 — Model answer.**
The pattern of many mutations whose normal VAF is a consistent small fraction of the tumour VAF points to **tumour-in-normal (TiN) contamination**: tumour cells or tumour DNA are present in the normal sample. Mutect2 treats ALT reads in the normal as evidence against a somatic call, so real drivers were filtered.

Actions:
- Check what tissue the normal is.
- Estimate the TiN fraction (e.g. with deTiN).
- Review and rescue variants consistent with that fraction.
- If needed, obtain a better normal.

*(Section 5.1; worked example, story 4)*

**Q9 — B.**
The contaminating person's germline heterozygous and homozygous alleles appear at low VAF wherever they differ from the patient, and those sites are mostly common population SNPs. GATK's `GetPileupSummaries` + `CalculateContamination` quantify this from allele fractions at known common sites. *(Section 5.4)*

**Q10 — Model answer (any three).**
- Check the **consent**: did the patient agree to receive germline findings?
- Follow the lab's **germline / secondary-findings policy**, including which genes are reportable (e.g. the current ACMG SF list).
- Arrange **confirmation in an accredited clinical germline test** if the finding came from a research or somatic pipeline.
- **Refer to genetic counselling**: the result affects the patient's management and **blood relatives**' risk.
- Verify sample identity (tumour–normal concordance, no swap) before anything is communicated.

*(Section 6)*
