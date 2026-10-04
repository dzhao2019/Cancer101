# Answer Key — Quiz 9

Section references point to `module_09_hereditary_cancer.md`.

---

**Q1 — Model answer.**
At the **family** level, inheriting one non-functional copy is enough to raise cancer risk, and each child has a 50% chance of inheriting it — dominant inheritance.
At the **cell** level, one working copy is still enough to do the job. A tumour forms only after a **second hit** (mutation, deletion, LOH or methylation) removes the remaining copy — so the gene behaves recessively in the cell. Because every cell starts with the first hit, the second hit is needed only once, which explains earlier, multiple and bilateral cancers. *(Section 1; Module 6)*

**Q2 — B.**
BRCA1 has the higher ovarian risk (~44% vs ~17%), so A is wrong. Both genes are needed for HR (C wrong), and both are tumour suppressors (D wrong). *(Section 2)*

**Q3 — Model answer.**
EPCAM sits immediately upstream of MSH2. Deleting EPCAM's 3′ end (including its stop/polyadenylation signals) lets transcription **read through into MSH2**, which leads to **methylation and silencing of the MSH2 promoter** in tissues where EPCAM is expressed. The result is MSH2 loss without any MSH2 sequence change. *(Section 3)*

**Q4 — B.**
Low VAF in blood (higher than in the tumour), older age and prior chemotherapy are the classic CHIP pattern; the tumour signal comes from infiltrating blood cells. A germline variant would be ~0.5. It should be reviewed, not ignored (D), and a constitutional mosaic variant is possible but less likely. *(Section 4; Module 4)*

**Q5 — Model answer.**
- Mutect2 is a **somatic** caller: variants present in the matched normal are suppressed or filtered (`germline`, `normal_artifact`).
- Germline analysis may be **out of scope or not consented** for the somatic pipeline.

Add a **germline caller on the normal BAM** (e.g. HaplotypeCaller or DeepVariant), restricted to a consented gene list, plus germline CNV calling for exon-level deletions. *(Section 6 Pipeline connection)*

**Q6 — C.**
PVS1 is the very strong criterion for predicted null variants (nonsense, frameshift, canonical splice) in genes where loss of function causes the disease. BA1 and BS3 are benign criteria; PP3 is supporting computational evidence. *(Section 6)*

**Q7 — Probably not.**
- Tumour VAF 0.48 ≈ the germline-heterozygous level: (p·1 + (1 − p)) / 2 = 0.5 in a diploid region. There is **no sign of LOH**, which would push the VAF towards (1 + p)/2 = 0.8.
- **No HRD signature** — the tumour phenotype does not match BRCA2 loss.
- Colorectal cancer is **outside the core BRCA2 spectrum**.

The variant is still clinically important for the patient and family (cascade testing), but it is likely **incidental to this tumour**, and PARP-inhibitor benefit is less likely. *(Section 7)*

**Q8 — B.**
In haematological cancers the blood is the tumour. A blood "normal" contains leukaemic cells, so truncal leukaemia mutations can appear at germline-like VAFs. Cultured skin fibroblasts are the usual germline source. *(Section 5)*

**Q9 — Model answer.**
PMS2 has a highly similar pseudogene, **PMS2CL**, which shares sequence with its 3′ exons. Short reads cannot be placed uniquely. In the BAM you see **low MAPQ** (often 0), reads split between gene and pseudogene, and uneven depth — so variants can be missed or mis-assigned. Clinical labs use long-range PCR or specialised approaches. *(Section 6 Pipeline connection; Module 2)*

**Q10 — Any three of:**
- **Consent** that covers germline findings and their return.
- **Confirmation** in an accredited clinical laboratory.
- **Classification** under ACMG/AMP (and any relevant VCEP rules) — P/LP only, not VUS.
- **Genetic counselling** for disclosure, including family (cascade) implications.
- A defined institutional **policy** for which genes and findings are returned.

*(Section 8)*
