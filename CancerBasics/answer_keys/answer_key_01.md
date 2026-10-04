# Answer Key — Quiz 1

Each answer points back to the section of `module_01_central_dogma.md` to revisit if you missed it.

---

**Q1 — B. Antiparallel and complementary.**
One strand runs 5′→3′, the other 3′→5′ (antiparallel), and the bases pair A–T and G–C (complementary), so each strand determines the other. They are not identical: one strand is the reverse complement of the other. *(Section 2)*

**Q2 — `5′-GGCCAT-3′`.**
The complement of ATGGCC is TACCGG, read 3′→5′. Reversing it to write 5′→3′ gives GGCCAT. A common mistake is to stop after complementing (TACCGG); that string is written in the wrong direction. *(Section 2)*

**Q3 — B.**
FLAG 0x10 (16) means the read aligned to the reverse strand. The SAM spec stores SEQ and QUAL on the forward (+) strand of the reference, so the aligner reverse-complements the read. To recover the original read you must reverse-complement it back. *(Section 2, pipeline box)*

**Q4 — C.**
Exons are the segments kept in mature mRNA, and that includes the 5′ and 3′ UTRs. The other options are wrong:
- A: KRAS exon 1 is entirely non-coding.
- B: Introns are removed, not exons.
- D: GT is the first dinucleotide of an *intron*, not an exon.
*(Sections 3–4)*

**Q5 — Met–Ala–Trp–Stop (M A W \*).**
AUG = Met, GCU = Ala, UGG = Trp, UAA = Stop. In RNA, U replaces T; read the DNA codon table by swapping U→T. Translation ends at the stop codon; the stop is not an amino acid. *(Section 5)*

**Q6 — C. Synonymous.**
GGx encodes glycine whatever the third base, so GGT→GGC leaves the amino acid unchanged. This illustrates third-position degeneracy. Synonymous is not automatically harmless, but the protein sequence is unchanged. *(Section 5; misconception 5)*

**Q7 — B. C>T.**
The VCF reports the + strand. KRAS is on the − strand, so the coding-strand G>A appears as its complement on the + strand: G→C for REF and A→T for ALT. This is the worked example. *(Worked example, Step 2)*

**Q8**
- **(a) c.1798–c.1800.** Codon *n* spans c.(3n−2) to c.3n, and 3×600 − 2 = 1798.
- **(b) 2nd position.** ((1799 − 1) mod 3) + 1 = 2.
- **(c) A>T.** The coding-strand T>A on a − strand gene is complemented on the + strand: T→A for REF, A→T for ALT.
- **(d) GAG, glutamate (Glu, E).** Changing the middle T of GTG to A gives GAG = Glu. That is p.Val600Glu, i.e. V600E.

*(Section 6; worked example)*

**Q9 — Different transcripts (or transcript versions).**
`c.` positions are counted along the coding sequence of one specific transcript. If the two labs annotated against different transcripts, the same genomic base gets a different `c.` number. Possible differences include:
- different RefSeq vs Ensembl transcripts
- different isoforms
- different versions of the same transcript

The `p.` name and even the consequence class can also differ.

Recommendation: report the **transcript ID with version** alongside every `c.`/`p.` name, include the genomic (`g.`) description, and default to **MANE Select** (plus MANE Plus Clinical where needed). *(Section 7)*

**Q10 — POS 25245350.**
BED is 0-based and half-open: `start=25245349, end=25245350` covers exactly one base. In 1-based coordinates (VCF), that base is start + 1 = 25245350. Coincidentally, this is the KRAS c.35 position from the worked example. *(Section 6, pipeline box in Section 7)*
