# Quiz 2 — Human Genome Organization and Reference Genomes

10 questions · ~20 minutes · closed book. Answer key: `answer_keys/answer_key_02.md`.
Coordinates are GRCh38 unless stated.

---

**Q1. (Multiple choice)** Which human chromosome is the shortest?

- A. chr22
- B. chr21
- C. chrY
- D. chr19

**Q2. (Multiple choice)** Human telomeres consist mainly of tandem repeats of:

- A. CAG
- B. TTAGGG
- C. the ~171 bp α-satellite unit
- D. Alu elements

**Q3. (Short answer)** In 3–4 sentences: what is the end-replication problem, how do most cancers overcome it, and how does the remaining minority do it? Name one gene whose loss is associated with the minority route.

**Q4. (Multiple choice)** BWA assigns a read MAPQ 0. The most likely explanation is:

- A. The read has many sequencing errors
- B. The read aligns equally well to two or more genomic locations
- C. The read is from the mitochondrial genome
- D. The read is a PCR duplicate

**Q5. (Short answer)** Why is short-read variant calling in the 3′ exons of PMS2 unreliable? Name one way clinical labs work around this.

**Q6. (Multiple choice)** GRCh38 analysis sets hard-mask the pseudoautosomal regions on chrY. The main purpose is:

- A. To hide sex-chromosome information for privacy
- B. To make PAR reads map uniquely to chrX instead of being split between X and Y with MAPQ 0
- C. To reduce the size of the BWA index
- D. Because the PARs contain no genes

**Q7. (Short answer, 3 parts)** The TERT promoter mutation "C228T":

- (a) Which genome build do the numbers in its name come from?
- (b) Why does it appear as G>A, not C>T, in a GRCh38 VCF?
- (c) Give one biological and one technical reason it matters to your pipeline.

**Q8. (Multiple choice)** Hyperdiploid multiple myeloma typically shows:

- A. Loss of chromosomes 7 and 10
- B. Gains of odd-numbered chromosomes such as 3, 5, 7, 9, 11, 15, 19 and 21
- C. A single t(9;22) translocation
- D. Whole-genome doubling only

**Q9. (Short answer)** A colleague lifts a GRCh37 somatic VCF to GRCh38. At some sites the VCF's REF base no longer matches the GRCh38 reference, and a few variants have disappeared. Give two biological or assembly reasons for each problem.

**Q10. (Short answer)** Your pipeline uses a GRCh38 FASTA that contains ALT contigs, but BWA was run without the `.alt` file and no post-processing was done. What happens to reads from the HLA region and other ALT-covered loci, and what are two ways to fix it?

---

**Score:** ____ / 10 (Q7 counts as 1 point: one-third per part)
Record your score in `progress_tracker.md`.
