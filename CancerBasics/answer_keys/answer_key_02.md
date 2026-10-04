# Answer Key — Quiz 2

Section references point to `module_02_genome_organization.md`.

---

**Q1 — B. chr21.**
chr21 is about 46.7 Mb and chr22 about 50.8 Mb. Chromosomes were numbered by their apparent size under the microscope before sequencing, and chr21 and chr22 were ranked the wrong way round. chrY (~57 Mb) is also larger than chr21. *(Section 2)*

**Q2 — B. TTAGGG.**
Telomeres are thousands of tandem TTAGGG repeats, protected by the shelterin complex.
- The ~171 bp α-satellite unit (C) is the building block of centromeres.
- CAG repeats (A) are a microsatellite type.
- Alus (D) are a SINE transposable element.
*(Sections 2 and 4)*

**Q3 — Model answer.**
DNA polymerase cannot fully copy the end of a linear chromosome, so telomeres shorten with every division. When they become critically short, the cell senesces or dies, which limits normal cells to a finite number of divisions. About 85–90% of cancers reactivate **telomerase** (TERT + TERC), which re-extends the telomeres. The remaining ~10–15% use **ALT**, a recombination-based lengthening mechanism associated with loss of **ATRX** or **DAXX**. *(Section 4)*

**Q4 — B.**
MAPQ is the aligner's confidence that the placement is correct. MAPQ 0 means at least one other location fits equally well, which is typical of repeats, segmental duplications and pseudogenes. Sequencing errors (A) lower alignment scores but don't by themselves produce MAPQ 0 at a unique locus. Duplicates (D) are flagged separately, not through MAPQ. *(Section 8)*

**Q5 — Model answer.**
PMS2's 3′ exons are nearly identical to the nearby pseudogene **PMS2CL**, a product of segmental duplication. Reads fit both copies equally well, get MAPQ 0, and are filtered by callers. Real PMS2 variants can therefore be missed, or pseudogene sequence mis-assigned to PMS2. Labs confirm with specialised methods such as **long-range PCR** that amplifies only the true gene before analysis. *(Section 6, mini case)*

**Q6 — B.**
PAR sequence is identical on X and Y. If both copies stay unmasked, PAR reads match two places and get MAPQ 0. Masking the chrY copy makes them map uniquely to chrX. The PARs do contain genes (D is false). Privacy (A) and index size (C) are not the purpose. *(Section 5)*

**Q7**
- **(a) GRCh37/hg19.** C228T and C250T refer to chr5:1,295,228 and 1,295,250 in GRCh37. In GRCh38 they are at 1,295,113 and 1,295,135.
- **(b)** TERT is on the − strand. The C>T is described on TERT's coding strand, while VCFs report the + strand, so you see the complement: G>A.
- **(c)** Either of these biological reasons:
  - It creates a new ETS/GABP transcription-factor binding site that reactivates telomerase — a non-coding driver of replicative immortality.
  - It is a diagnostic feature of IDH-wildtype glioblastoma.

  Any one of these technical reasons:
  - The promoter is GC-rich, giving low coverage.
  - It is not targeted in exomes or most coding panels.
  - It is annotated as upstream/5′ flank and often dropped by coding-only report filters.

*(Worked example)*

**Q8 — B.**
Hyperdiploid myeloma gains odd-numbered chromosomes, typically 3, 5, 7, 9, 11, 15, 19 and 21. The other options describe different cancers:
- A is a distorted version of glioblastoma's +7/−10, which is a *gain* of 7 with loss of 10.
- C is CML.
- D is not specific to myeloma.

*(Section 3, tumor spotlight)*

**Q9 — Model answer.**

*REF mismatches:*
- GRCh38 corrected sequencing errors and replaced some rare alleles present in GRCh37, so the reference base itself changed.
- Segments that were inverted between builds flip strand, so the base must be complemented.

*Lost variants:*
- The region has no equivalent in GRCh38 (removed, rebuilt or placed on an unlocalised contig).
- The region maps to more than one place, e.g. duplicated or moved sequence, so liftover refuses it.

The best practice for somatic work is to **re-align and re-call** on GRCh38 rather than lift over. *(Section 7)*

**Q10 — Model answer.**
Reads from HLA and other ALT-covered loci match both the primary chromosome and the ALT contig. Without alt-aware handling, BWA treats these as genuine multi-mapping, so MAPQ drops (often to 0). Callers then discard the reads, and coverage and variant calls are lost exactly where ALTs exist.

Fixes:
1. Use a **no-alt analysis set**.
2. Keep the ALTs but run BWA in **alt-aware mode with the `.alt` file and post-alt processing**.

Either way, keep the reference consistent with the PoN, the germline resource and the intervals. *(Section 7, analysis sets)*
