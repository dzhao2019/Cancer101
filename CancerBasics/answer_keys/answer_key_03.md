# Answer Key — Quiz 3

Section references point to `module_03_variant_types_hgvs.md`.

---

**Q1 — B. An MNV, likely caused by UV light.**
UV light links adjacent pyrimidines, and mis-repair produces CC>TT doublets — a signature of sun-exposed skin cancers. Calling the change as two independent SNVs (A) loses the fact that it was one event, and if both bases sit in one codon, it can give the wrong amino-acid prediction. *(Section 2)*

**Q2 — C. C>T.**
Transitions stay within a chemical class: purine↔purine (A↔G) or pyrimidine↔pyrimidine (C↔T). C>A, G>T and A>T all cross classes, so they are transversions. C>T is the most common substitution, largely because of deamination of methylated CpG. *(Section 2)*

**Q3 — Model answer.**
- (a) **Exon 3:** the premature stop is far upstream of the last exon–exon junction, so the mRNA is degraded by **nonsense-mediated decay (NMD)**. Little or no protein is made — loss of function.
- (b) **Exon 11 (the last exon):** there is no downstream exon junction, so NMD does not trigger. The mRNA is translated into a **truncated protein**, which may keep partial function or even act dominant-negatively.

*(Section 3.3)*

**Q4 — B.**
15 is a multiple of 3, so the reading frame is preserved and five codons' worth of amino acids are removed (the EGFR exon 19 example). Depending on where the deletion starts relative to the codons, the amino acids at the junction can also change, giving a `delins` at the protein level. A frameshift (A) needs a length that is not a multiple of 3. *(Sections 3.1 and worked example)*

**Q5 — Model answer.**
p53 works as a **tetramer**. A missense mutant subunit is still made and can bind the normal subunits, poisoning the whole complex — a **dominant-negative** effect that is stronger than simply losing one copy. Some mutants also gain new oncogenic functions, and the missense hotspots cluster in the DNA-binding domain, where single changes (contact or structural) destroy DNA binding. *(Section 3.4)*

**Q6 — `c.103del`; the VCF places it at the leftmost position.**
HGVS shifts a deletion as far **3′ as possible relative to the transcript**. For a + strand gene that is the last A of the run, c.103. A left-normalised VCF shifts it **left on the genome**, anchoring it at the base just before c.100. For a − strand gene the two conventions would coincide. *(Section 10)*

**Q7 — B.**
A balanced translocation exchanges segments without gaining or losing DNA, so read depth stays flat (A is wrong). The evidence comes from **discordant pairs** (one mate on chr9, the other on chr22) and **split reads** (soft-clipped reads with supplementary alignments, SA tag) pinpointing the junction. *(Sections 7 and 9)*

**Q8 — Model answer.**
1. **Kinase fusion → constitutive activation.** The 3′ partner contributes an intact kinase domain, and the 5′ partner contributes a promoter and a dimerisation domain, so the kinase is always on. The fusion must be in frame. Examples: BCR::ABL1 (CML), EML4::ALK (lung).
2. **Promoter/enhancer swap → overexpression.** A strong regulatory element is placed next to an intact oncogene. Examples: TMPRSS2::ERG (prostate; androgen-driven ERG), IGH::CCND1 t(11;14), IGH::MYC t(8;14).

*(Section 8)*

**Q9 — B.**
EML4 and ALK both sit on the short arm of chr2 and point in opposite directions. Only an **inversion** flips one segment so that both pieces read in the same direction, giving an in-frame EML4–ALK transcript. You confirmed the strands in Exercise Part D. *(Sections 7–8)*

**Q10 — Model answer.**
Variants that destroy the exon 14 splice donor, acceptor or branch point (SNVs, indels or larger deletions) make the spliceosome **skip exon 14**. The resulting protein is in frame and keeps its kinase activity, but loses the juxtamembrane **CBL docking site** that tags MET for degradation. MET therefore accumulates and signals persistently.

The causal DNA variants are diverse and some are hard to call, whereas **RNA directly shows the exon 13–exon 15 junction**, confirming the functional outcome regardless of which DNA variant caused it. *(Section 4)*
