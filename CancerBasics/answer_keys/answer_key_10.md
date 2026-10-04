# Answer Key — Quiz 10

Section references point to `module_10_transcriptome.md`.

---

**Q1 — B.**
Poly-A selection keeps only the 3′ ends of fragmented molecules, giving strong 3′ bias. rRNA depletion or exome capture tolerates degraded RNA. *(Section 1)*

**Q2 — Model answer.**
TPM normalises for gene length first and then scales so every sample sums to 10⁶. Each value is therefore a proportion of that sample's transcripts. FPKM totals differ between samples, so the same FPKM can mean different proportions. For formal differential expression, use raw counts with DESeq2/edgeR normalisation. *(Section 1)*

**Q3 — Any three:**
- Which **exons** are joined (e.g. EML4 exon 13 → ALK exon 20).
- Whether the junction is **in frame**.
- Whether the fusion is **expressed**, and how highly.
- **5′/3′ expression imbalance** of ALK supporting the fusion.
- Any alternative isoforms of the fusion transcript.

*(Section 3; worked example)*

**Q4 — B.**
IGH translocations in myeloma usually place an intact oncogene next to the strong IGH enhancers (enhancer hijacking). The result is overexpression of normal CCND1 protein, not a chimeric protein. *(Section 2)*

**Q5 — Model answer.**
**Nonsense-mediated decay** degrades transcripts carrying a premature stop codon more than ~50–55 nt upstream of the last exon–exon junction, so the mutant allele is under-represented in RNA. (The DNA VAF ≈ purity suggests LOH, so most tumour transcripts are mutant — NMD is doing the work.)
A premature stop in the **last exon** has no downstream junction, so it **escapes NMD** and RNA VAF ≈ DNA VAF. *(Sections 1, 5; Module 3)*

**Q6 — B.**
ADAR converts adenosine to inosine, which is read as G. A mismatch present only in RNA, with no DNA support in tumour or normal, is the RNA-editing pattern. *(Sections 1, 5)*

**Q7 — Any three:**
- Breakpoints at **canonical exon boundaries**.
- **In-frame** junction (for chimeric-protein fusions) with retained functional domains (e.g. a kinase domain).
- Both **junction reads and spanning fragments**, with good counts.
- **DNA SV support** at consistent genomic positions (WGTS).
- **Not** on a normal-tissue/read-through **blacklist**; partners not adjacent same-strand genes; not paralogues.
- A **known recurrent** oncogenic fusion for the tumour type.

*(Section 3)*

**Q8 — B.**
EGFRvIII deletes exons 2–7, producing an exon 1–8 junction and a receptor that lacks part of the extracellular domain and signals constitutively. It often occurs in EGFR-amplified GBM. *(Sections 3, 4)*

**Q9 — Model answer.**
**Epigenetic silencing** (e.g. promoter methylation) of one allele — a second hit with no sequence change. WGS reads the DNA sequence, which is unchanged; only expression or methylation data reveal it. Here the "second hit" is functional loss of the other allele, seen as monoallelic expression. *(Section 5; Module 6)*

**Q10 — Any three, with matching metrics:**
- **DNA/RNA sample swap** → wrong fusions and expression attributed to the patient. Caught by **genotype concordance** between DNA and RNA.
- **Degraded RNA** → 3′ bias, false low expression, missed 5′-partner fusions. Caught by **RIN/DV200** and **gene-body coverage**.
- **rRNA contamination or failed depletion** → too few informative reads, low sensitivity. Caught by **rRNA fraction** and **mapping rate**.
- **Wrong strandedness setting** → wrong counts for antisense/overlapping genes. Caught by a **strand-specificity check**.
- **High intronic fraction** (pre-mRNA or genomic DNA contamination) → inflated intronic/intergenic signal. Caught by **exonic/intronic/intergenic fractions**.

*(Section 1 Pipeline connection)*
