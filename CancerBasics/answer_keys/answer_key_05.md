# Answer Key — Quiz 5

Section references point to `module_05_mutation_and_repair.md`.

---

**Q1 — B. C>T at CpG.**
Methylated cytosine at CpG can lose an amine group and become thymine, leaving a T:G mismatch. This is repaired less efficiently than ordinary C→U deamination. Because it happens steadily over time, it underlies the clock-like signature SBS1. *(Section 2)*

**Q2 — B.**
8-oxoguanine frequently pairs with adenine. After replication, the original G:C pair becomes T:A, a G>T substitution (written C>A in the pyrimidine convention). BER enzymes OGG1 and MUTYH normally prevent this. *(Sections 2–3)*

**Q3 — Nucleotide excision repair (NER).**
NER removes bulky, helix-distorting lesions. A transcription-coupled branch of NER preferentially repairs the strand used as the template for transcription in expressed genes. Damage on the transcribed strand is therefore fixed more often, so surviving mutations are enriched on the non-transcribed strand — a strand asymmetry seen in UV and tobacco signatures. *(Sections 2–3)*

**Q4 — B.**
MMR corrects mismatches and slippage loops left after replication. Without it, microsatellites gain or lose units (MSI), giving many ±1 bp indels, plus an elevated SNV rate. Option C describes POLE ultramutation. *(Section 4.1)*

**Q5 — Model answer.**
The most likely cause is **sporadic MLH1 promoter hypermethylation**, which silences both MLH1 copies without changing the DNA sequence. This is why RNA expression is low but no mutation is found, and it is strongly associated with BRAF V600E.

This is usually **not inherited**, so the family risk is generally not raised. However, Lynch syndrome is ruled out formally through clinical germline testing and established triage algorithms, not by this inference alone. *(Section 4.1; worked example, Tumour A)*

**Q6 — C.**
POLE exonuclease-domain hotspots (e.g. P286R, V411L) disable proofreading. This produces ultramutation with characteristic SNV contexts but few indels, so the tumour is MSS. Lynch (A) would give MSI. Tobacco (B) is unlikely in endometrium. FFPE (D) gives low-VAF C>T, not this spectrum. *(Section 4.2)*

**Q7 — Model answer.**
PARP inhibitors trap PARP1 on single-strand breaks. When a replication fork reaches the trapped complex, it collapses into a double-strand break. Normal cells repair these breaks accurately by homologous recombination, which needs BRCA1/2. BRCA-deficient tumour cells cannot, so the breaks accumulate or are mis-repaired, and the cells die. Two survivable defects combining into a lethal one is called **synthetic lethality**. *(Section 4.3)*

**Q8 — Model answer.**
Likely a **BRCA2 reversion mutation**: a secondary deletion (or insertion) that, combined with the original frameshift, restores the reading frame, so a functional or near-functional BRCA2 is made and HR returns.

What to check:
- Confirm that both changes are on the **same reads/allele** (phasing).
- Check that the **combined length change is a multiple of 3**.
- Predict the resulting protein.
- RNA, if available, can confirm the restored transcript.

*(Section 4.3)*

**Q9 — B.**
Damage to one strand of the original fragment (FFPE deamination, 8-oxoG) is copied into every amplified descendant of that strand, so the ALT appears only in one F1R2/F2R1 class. True mutations sit on both strands of the duplex and appear in both orientations. Option A describes strand bias, a different filter. *(Section 5)*

**Q10 — Model answer.**

Evidence (any three):
- Are the ALT reads balanced across **both orientations**? Did the calls **fail the `orientation` filter**?
- The **VAF distribution**: artifacts pile up at very low VAF, unrelated to tumour purity or clonal structure.
- **Context**: FFPE C>T spreads across many contexts, unlike the CpG-focused SBS1 pattern.
- **Reproducibility** in an independent library or a fresh-frozen sample.
- **Absence from the PoN**, together with good base and mapping quality.

Lab mitigation: **UDG treatment** of FFPE DNA before library prep (or better fixation and storage practices). *(Section 5)*
