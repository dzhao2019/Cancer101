# Module 8 — Genomic Biomarkers and Mutational Signatures

**Week 10 of 16 · ~5 hours · Prerequisites: Modules 3, 5, 7**

| Activity | Time |
|---|---|
| Lesson notes | 1.5 h |
| Reading: Alexandrov et al. 2020 (core) + Weinberg Ch 12 (revisit selected sections) | 1 h |
| Hands-on exercise (COSMIC Signatures, cBioPortal, 96-channel matrix from a VCF) | 1.5 h |
| Quiz (`quizzes/quiz_08.md`) + flashcards (tag `M08`) | 0.5 h |
| Buffer | 0.5 h |

**Reading strategy.** Module 5 taught *which* damage and repair processes leave *which* mutations. This module turns those patterns into **numbers that drive treatment** — TMB, MSI, HRD — and into the formal language of **mutational signatures**. Weinberg's Ch 15 (tumour immunology) is optional background for why TMB and MSI predict immunotherapy response.

Coordinates are **GRCh38** unless stated otherwise.

---

## Learning objectives

By the end of this module you can:

1. **Calculate** tumour mutational burden (TMB) from a somatic VCF and **explain** why WGS, exome and panel TMB values are not interchangeable.
2. **Explain** the biology linking MMR deficiency to MSI and immunotherapy response, and **compare** IHC, PCR and NGS-based MSI testing.
3. **Describe** how HRD is measured — genomic scars (LOH, TAI, LST), SBS3 and composite classifiers — and **explain** why a scar is not the same as current HR status.
4. **Construct** a 96-channel SBS mutation profile from a VCF and **interpret** signature exposures, distinguishing extraction from fitting.
5. **Recognise** major copy-number and structural patterns (aneuploidy, WGD, chromothripsis, kataegis, tandem duplicator phenotype, ecDNA) and **name** the processes that cause them.

---

## 1. What makes a genomic biomarker

A **biomarker** is a measurable feature that tells you something clinically useful. In cancer genomics there are three kinds:

| Kind | Question it answers | Examples |
|---|---|---|
| **Predictive** | Will this drug work? | EGFR mutation → EGFR inhibitors; MSI-H → checkpoint inhibitors; HRD → PARP inhibitors |
| **Prognostic** | How will the disease behave regardless of treatment? | POLE-ultramutated endometrial cancer (favourable); TP53/17p loss in CLL and myeloma (adverse) |
| **Diagnostic** | What tumour is this? | 1p/19q codeletion → oligodendroglioma; IDH mutation in glioma; fusions defining leukaemia subtypes (Module 10) |

Modules 3–6 focused on **single-gene** biomarkers. This module is about **genome-wide** ones: features summarising thousands of mutations. These are where WGS has the biggest advantage over gene panels — the whole genome gives far more mutations to count and pattern-match.

---

## 2. Tumour mutational burden (TMB)

### Biology

Proteins with mutations can be cut into short peptides that the immune system recognises as foreign — **neoantigens**. More mutations, more chances of a neoantigen. **Immune checkpoint inhibitors** (anti-PD-1, anti-PD-L1, anti-CTLA-4) release brakes on T cells. They work best when T cells have something to recognise. TMB is a crude proxy for "how much there is to recognise".

### Definition

> **TMB = number of somatic mutations ÷ size of the region examined (in megabases, Mb)**

The details matter:

| Choice | Options | Effect |
|---|---|---|
| Which variants | Non-synonymous only, or all coding, or all SNVs + indels genome-wide | Changes the count several-fold |
| Denominator | Panel (~1 Mb), exome (~30–50 Mb), genome (~2,800–3,000 Mb callable) | Small panels give noisy estimates |
| Filters | Exclude germline, known hotspots (panels often do), low VAF cut-offs | Shifts values, especially in low-purity samples |

A US FDA approval (2020) of pembrolizumab for solid tumours with **TMB ≥ 10 mutations/Mb** was based on a specific panel assay (FoundationOne CDx). That threshold is defined **for that assay**. A WGS genome-wide TMB of 10/Mb is not automatically the same thing. Harmonisation efforts (e.g. Friends of Cancer Research) exist because of this.

**Typical ranges (orders of magnitude):** melanoma and smoking-related lung cancers are high (UV and tobacco signatures); MSI and POLE tumours are very high; paediatric cancers, AML and many sarcomas are low (often < 1/Mb).

**Established vs debated.** TMB-high predicts response in some tumour types better than others, and the best threshold likely differs by tumour type. This is still debated.

> **Pipeline connection — computing TMB from your VCF**
> - Count **PASS** somatic SNVs + indels; divide by the **callable** genome size (positions with adequate depth in both tumour and normal — not 3,100 Mb blindly).
> - Example: 30,000 SNVs + 3,000 indels across 2,900 callable Mb → **~11.4 mutations/Mb**.
> - **Purity matters.** At low purity, subclonal and low-VAF mutations drop out, so TMB is underestimated. Report TMB together with purity.
> - **Tumour-only** TMB is inflated by private germline variants that population filters miss — worse for under-represented ancestries (Module 4).

---

## 3. Microsatellite instability (MSI)

### Biology (from Module 5)

Mismatch repair (MLH1, MSH2, MSH6, PMS2) fixes polymerase slippage at repeats. Without it, **microsatellites** change length in every division, and frameshifts accumulate in genes with coding repeats. Frameshifts create long stretches of novel protein — highly immunogenic neoantigens. That is why **MSI-high / dMMR tumours respond so well to checkpoint inhibitors**. In 2017 the FDA approved pembrolizumab for MSI-H/dMMR solid tumours regardless of tissue — the **first tissue-agnostic approval**.

### How MSI is tested

| Method | What it measures | Notes |
|---|---|---|
| **MMR immunohistochemistry (IHC)** | Presence of the four MMR proteins in tumour nuclei | Loss pattern points to the gene: MLH1 and PMS2 lost together (MLH1 problem); MSH2 and MSH6 together (MSH2 problem); isolated PMS2 or MSH6 loss. Cheap, fast |
| **PCR fragment analysis** | Length shifts at a set of microsatellites (commonly five mononucleotide repeats) vs normal | Classic gold standard; MSI-H if ≥ 2 unstable markers in common panels |
| **NGS-based** | Proportion of unstable microsatellite sites (MSIsensor, MSIsensor-pro, MANTIS, others) | Thousands of sites in WGS; thresholds are tool- and assay-specific |
| **Signatures** | Indel signatures ID1/ID2 excess; SBS6, 15, 21, 26, 44 | Supports MSI calls; distinguishes dMMR from POLE |

**After finding MSI or MLH1 loss in colorectal cancer**, clinicians test **BRAF V600E** and **MLH1 promoter methylation**. Either favours a **sporadic** cause; their absence raises suspicion of **Lynch syndrome** (Module 9) and triggers germline testing.

---

## 4. Homologous recombination deficiency (HRD)

### Biology (from Module 5)

Without BRCA1/BRCA2/PALB2-driven homologous recombination, double-strand breaks are repaired by error-prone end-joining. Over many divisions this leaves **scars** across the genome. HRD tumours are sensitive to **PARP inhibitors** and **platinum** (synthetic lethality, Module 5).

### Ways to measure HRD

| Approach | Measures | Notes |
|---|---|---|
| **Gene status** | Biallelic loss of BRCA1, BRCA2, PALB2 (and possibly RAD51C/D, others) | Need both hits — germline/somatic mutation + LOH or second mutation (Modules 6, 9). A heterozygous BRCA2 variant without LOH may not cause HRD |
| **Genomic scar scores** | **LOH** (number of large LOH regions), **TAI** (telomeric allelic imbalance), **LST** (large-scale state transitions) | Summed into a score; a commercial version uses ≥ 42 as HRD-positive in ovarian cancer |
| **Mutational signatures** | SBS3; ID6 (deletions with microhomology); rearrangement signatures (small tandem duplications for BRCA1, deletions for BRCA1/2) | Needs WGS for the full picture |
| **Composite classifiers** | Combine the above (HRDetect, CHORD) | WGS-based; CHORD also separates BRCA1-type from BRCA2-type |
| **Functional assays** | RAD51 foci formation in tumour tissue | Measures **current** HR, not history; research/emerging |

**A scar is history, not current state.** Scars accumulate while HR is broken and **persist** after a reversion mutation restores BRCA function (Module 5). A tumour can therefore be scar-positive yet PARP-inhibitor-resistant. Only a functional readout, or finding the reversion, reveals that.

> **Pipeline connection — HRD from a tumour–normal WGS**
> - The LOH/TAI/LST components come straight from your **allele-specific CN segments**. Wrong purity/ploidy (Module 7) produces wrong HRD scores — WGD especially inflates naïve LST counts if not handled.
> - SBS3 is flat and featureless, so it is hard to fit reliably from a few hundred SNVs. Indel and SV evidence are often more convincing.
> - Report the **BRCA1/2 allelic status** (mono- vs biallelic) alongside the score.

---

## 5. Mutational signatures

### The idea

Each mutational process (Module 5) produces mutations with a characteristic **pattern**. A tumour's mutations are a **mixture** of several processes. Signature analysis unmixes them.

**Analogy.** A signature is like a "spectral fingerprint" — think of each process as an instrument and the tumour as a recording. Signature analysis is source separation: which instruments played, and how loud.

### The 96-channel SBS profile

1. Take each SNV and its **immediate 5′ and 3′ neighbours** in the reference.
2. Write the mutated base as a **pyrimidine** (C or T); if the reference is G or A, reverse-complement the whole trinucleotide (Module 3).
3. That gives 6 substitution classes × 4 possible 5′ bases × 4 possible 3′ bases = **96 channels**, e.g. `T[C>T]G` or `A[C>A]A`.

Other COSMIC catalogues:

| Catalogue | Channels | Captures |
|---|---|---|
| **SBS** (single-base substitutions) | 96 (also 288/1536 extended) | Most processes |
| **DBS** (doublet base substitutions) | 78 | UV CC>TT (DBS1), tobacco, platinum |
| **ID** (small insertions/deletions) | 83 | MMR slippage (ID1/ID2), HR microhomology deletions (ID6), tobacco (ID3) |
| **CN** (copy-number) | 48 | Ploidy, LOH, WGD, chromothripsis patterns |
| **SV** (rearrangements) | 32 | Tandem duplications, deletions, clustered rearrangements |

### Extraction vs fitting

| | **De novo extraction** | **Fitting (refitting, assignment)** |
|---|---|---|
| Question | What signatures exist in this cohort? | How much of each *known* signature is in this sample? |
| Method | Non-negative matrix factorisation (NMF) on many samples | Non-negative least squares or similar against the COSMIC reference |
| Needs | Hundreds of samples | One sample is fine — but more mutations = more reliable |
| Tools | SigProfilerExtractor, SignatureAnalyzer | SigProfilerAssignment, deconstructSigs, MutationalPatterns, sigminer |

For a clinical single sample you are almost always **fitting**. Over-fitting is the main risk: with many similar flat signatures (SBS3, SBS5, SBS40), a fitter will happily assign small, meaningless amounts of each. Restrict to signatures plausible for the tumour type and treat small exposures sceptically.

### Signatures worth knowing on sight

| Signature | Pattern | Aetiology | Seen in |
|---|---|---|---|
| **SBS1** | C>T at CpG | 5mC deamination; clock-like | All tissues |
| **SBS5** | Flat | Unknown; clock-like | All tissues |
| **SBS2, SBS13** | C>T and C>G at TCW | APOBEC3A/3B | Bladder, breast, cervix, head & neck, lung, myeloma |
| **SBS3** | Flat | HR deficiency | BRCA-deficient breast, ovarian, pancreatic, prostate |
| **SBS4** | C>A, strand-biased | Tobacco smoke | Lung, head & neck, liver |
| **SBS6, 15, 21, 26, 44** | C>T and T>C variants | MMR deficiency | MSI colorectal, endometrial, gastric |
| **SBS7a–d** | C>T at dipyrimidines | UV | Melanoma, cutaneous SCC |
| **SBS10a/b** | C>A at TCT, C>T at TCG | POLE proofreading loss | Ultramutated endometrial, colorectal |
| **SBS11** | C>T | Temozolomide | Treated glioma |
| **SBS18, SBS36** | C>A | ROS damage; MUTYH deficiency (SBS36) | Many; MUTYH-associated polyposis |
| **SBS22** | T>A | Aristolochic acid | Upper tract urothelial, liver (esp. East Asia) |
| **SBS24** | C>A | Aflatoxin | Liver |
| **SBS31, SBS35** | C>T, C>A | Platinum chemotherapy | Treated tumours |
| **SBS84, SBS85** | — | AID (activation-induced cytidine deaminase) | Lymphomas, CLL, myeloma |
| **SBS88** | T>C, T>G at specific motifs | Colibactin (genotoxic *E. coli*) | Colorectal — exposure often in childhood |

The COSMIC catalogue is versioned (v3.5 was released in November 2025). Signature numbers are stable, but new signatures are added and some have been split (e.g. SBS7 → 7a–d, SBS40 → 40a–c). Always state which version you fitted against.

---

## 6. Copy-number and structural patterns

| Pattern | What it is | Process / association | How it looks in WGS |
|---|---|---|---|
| **Aneuploidy / CIN** | Whole-chromosome or arm gains and losses | Chromosome mis-segregation | Many arm-level CN changes; high fraction genome altered |
| **Whole-genome doubling** | Entire set duplicated (Module 7) | TP53 loss | Ploidy ~3–4; m = 2 vs 1 clusters |
| **Focal amplification** | High CN of a small region | Selection for an oncogene (ERBB2, MYC, EGFR, CCND1, MDM2) | Narrow high-CN segment; may be ecDNA |
| **Homozygous deletion** | Both copies gone | Loss of a TSG (CDKN2A, PTEN) | CN 0; zero depth after purity correction |
| **Chromothripsis** | One or few chromosomes shattered and reassembled in a single event | Micronucleus formation, telomere crisis | Many clustered breakpoints; CN oscillating between 2 (sometimes 3) states; alternating LOH |
| **Kataegis** | Clusters of mutations ("showers") | APOBEC acting on single-stranded DNA near breaks | Rainfall plot: tight runs of C>T/C>G at TCW, often near SV breakpoints |
| **Tandem duplicator phenotype** | Many tandem duplications | **Small (~10 kb)**: BRCA1 loss. **Large (hundreds of kb–Mb)**: CDK12 loss (prostate, ovarian) | Duplication-type SV junctions in a size class |
| **ecDNA** | Circular amplicons outside chromosomes | Selected amplification; high heterogeneity (Module 7) | Very high CN + circular SV structure |

**Recurrent arm-level patterns act as diagnostic biomarkers:**

- **1p/19q codeletion** — oligodendroglioma (with IDH mutation).
- **+7/−10** — IDH-wild-type glioblastoma.
- **3p loss** — clear cell renal carcinoma (with VHL).
- **Odd-numbered trisomies (hyperdiploidy)** — one of the two main myeloma subgroups.
- **del(17p), del(13q14), +12, del(11q)** — prognostic in CLL.

> **Tumor spotlight — biomarkers by cancer type**
> - **Colorectal:** ~15% MSI (Module 5); MSI-H → immunotherapy. POLE-ultramutated subset. SBS88 colibactin in some.
> - **Breast:** HRD (BRCA1/2, PALB2), APOBEC SBS2/13 especially in metastatic ER+ disease; BRCA1-type small tandem duplications.
> - **Lung:** SBS4 + high TMB in smokers; APOBEC common; never-smoker EGFR-mutant tumours have low TMB and respond poorly to immunotherapy alone.
> - **Prostate:** HRD (BRCA2 most often); CDK12 large tandem duplications; MSI in a small minority.
> - **Pancreatic:** HRD in a subset (often germline BRCA2/PALB2) → platinum/PARP; MSI is rare but important when present.
> - **GBM:** +7/−10, CDKN2A deletion, EGFR amplification (often ecDNA); post-temozolomide hypermutation (SBS11) with MMR loss.
> - **Heme:** AML has very low TMB; CLL and myeloma carry AID (SBS84/85) and APOBEC (myeloma, especially with MAF translocations); copy-number/arm-level changes drive CLL and myeloma prognosis.

---

## Worked example: four tumours with "high TMB" — four different stories

All four have genome-wide TMB > 10 mutations/Mb. The *reason* changes the clinical meaning.

| | Tumour A | Tumour B | Tumour C | Tumour D |
|---|---|---|---|---|
| Type | Colorectal | Endometrial | Recurrent GBM | Lung squamous |
| TMB | ~40/Mb | > 100/Mb | ~50/Mb | ~15/Mb |
| Indels | **Many**, at homopolymers (ID1/ID2) | Few | Moderate | Some (ID3) |
| Dominant SBS | SBS44, SBS15/26 | **SBS10a/b** | **SBS11** | **SBS4** |
| MSI test | **MSI-H** | MSS | Often MSI-low/MSS | MSS |
| Key gene finding | **BRAF V600E**; MLH1 not mutated | **POLE P286R** (exonuclease domain) | MSH6 mutation (acquired) | TP53, no repair defect |
| Interpretation | **Sporadic dMMR** via MLH1 promoter methylation (check methylation; Lynch unlikely) | **POLE ultramutated** — favourable prognosis in endometrial cancer | **Therapy-induced hypermutation** after temozolomide, selected via MMR loss | **Exogenous mutagen**; TMB high without repair defect |
| Immunotherapy relevance | Strong (MSI-H/dMMR) | Plausible; evidence is smaller | Generally **poor** responses despite high TMB (active research) | TMB/PD-L1 used together; varies |

POLE P286R: `NM_006231.4:c.857C>G`, `p.(Pro286Arg)`. It disables proofreading while keeping the polymerase active — the cell copies DNA fast and carelessly.

**Lessons:**
- TMB is a number; **signatures explain it**.
- Tumour C shows that **mutation count alone** does not guarantee immune response: temozolomide-induced mutations are largely subclonal, and the brain immune environment is different.
- The same high TMB in colorectal cancer could be Lynch (germline) or sporadic — the BRAF/methylation check decides who needs genetic counselling (Module 9).

---

## Common misconceptions

1. **"TMB 10 is TMB 10."** It depends on the assay, the variant set and the denominator. Panel thresholds don't transfer automatically to WGS.
2. **"High TMB = MSI."** POLE, tobacco, UV and temozolomide all raise TMB without MSI. MSI is about indels at repeats.
3. **"A positive HRD score means a PARP inhibitor will work."** Scars persist after reversion; and HRD-positive does not equal BRCA-mutant.
4. **"Signature fitting tells you exactly which exposures happened."** It estimates contributions; flat signatures are poorly identifiable and small exposures are often noise.
5. **"Signatures are only about SNVs."** Indel, doublet, copy-number and SV signatures are often more specific (ID6 for HRD, DBS1 for UV).
6. **"MLH1 loss means Lynch syndrome."** In colorectal cancer most MLH1 loss is sporadic promoter methylation.

---

## Hands-on exercise (~1.5 h)

### Part A — Explore the signature catalogue (20 min)

1. Open https://cancer.sanger.ac.uk/signatures (COSMIC Mutational Signatures).
2. Open **SBS4**, **SBS3**, **SBS10a** and **SBS44**. For each, note: the dominant channels, the proposed aetiology, and the tissues where it is found.
3. Open **ID6** and **DBS1**. Why are they more specific than SBS3 and SBS7a respectively?

### Part B — TMB, MSI and POLE in cBioPortal (25 min)

1. In cBioPortal, open the TCGA uterine corpus endometrial carcinoma PanCancer Atlas study.
2. In **Plots**, put **TMB** (nonsynonymous) on one axis and an **MSI score** (MANTIS or MSIsensor, if available) on the other.
3. Colour points by **POLE** mutation status (query POLE first).
4. Identify three clusters: MSS/low TMB, MSI-H/high TMB, and POLE/ultra-high TMB/MSS. Which POLE variants appear in the ultra-high cluster?

### Part C — Build a 96-channel profile (45 min)

Use a VCF you are allowed to analyse — a pipeline test sample, a public cell-line VCF, or the example data bundled with the Bioconductor package **MutationalPatterns**.

Minimal Python (with `pysam`) that counts trinucleotide contexts for PASS SNVs:

```python
import collections, pysam

fa = pysam.FastaFile("GRCh38.fa")          # must match the VCF's reference
comp = str.maketrans("ACGT", "TGCA")
counts = collections.Counter()

for rec in pysam.VariantFile("tumour.somatic.vcf.gz"):
    if list(rec.filter.keys()) != ["PASS"]:
        continue
    ref, alt = rec.ref, rec.alts[0]
    if len(ref) != 1 or len(alt) != 1:       # SNVs only
        continue
    ctx = fa.fetch(rec.chrom, rec.pos - 2, rec.pos + 1).upper()   # 3 bases centred on the SNV
    assert ctx[1] == ref
    if ref in "GA":                          # pyrimidine convention
        ref, alt = ref.translate(comp), alt.translate(comp)
        ctx = ctx.translate(comp)[::-1]
    counts[f"{ctx[0]}[{ref}>{alt}]{ctx[2]}"] += 1

for k, v in sorted(counts.items()):
    print(k, v, sep="\t")
```

Then:

1. Check that the counts sum to your PASS SNV count and that there are at most 96 keys.
2. Fit the profile to COSMIC SBS signatures with **SigProfilerAssignment** (Python) or **MutationalPatterns** (R, `fit_to_signatures`). Restrict to signatures plausible for the tumour type.
3. Compute genome-wide TMB using the callable genome size from your pipeline.

### Record your answers

| Item | Your answer |
|---|---|
| A3: why ID6 and DBS1 are specific | |
| B4: clusters and POLE variants | |
| C: top 3 signatures and exposures | |
| C: TMB (mut/Mb) and callable size used | |

---

## Self-test

- Quiz: `quizzes/quiz_08.md` → answer key `answer_keys/answer_key_08.md`
- Flashcards: `flashcards.csv`, tag `M08`

---

## Further reading

1. **Alexandrov LB, et al. The repertoire of mutational signatures in human cancer. *Nature.* 2020;578(7793):94–101.** Core — the PCAWG signature paper (introduced in Module 5).
2. **Weinberg RA. *The Biology of Cancer*, 2nd ed. 2014. Ch 12 (Maintenance of Genomic Integrity).** Revisit for repair biology behind MSI and HRD. Ch 15 (tumour immunology) optional, for why TMB/MSI predict immunotherapy response — note that checkpoint-inhibitor content post-dates the book.
3. **Chalmers ZR, et al. Analysis of 100,000 human cancer genomes reveals the landscape of tumor mutational burden. *Genome Med.* 2017;9:34.** TMB distributions across tumour types and links to MSI.
4. **COSMIC Mutational Signatures website** (https://cancer.sanger.ac.uk/signatures) — the living reference; check the version.

---

## Facts to double-check (accuracy log)

- **FDA approvals:** pembrolizumab for MSI-H/dMMR solid tumours (2017) and for TMB-H ≥ 10 mut/Mb by FoundationOne CDx (2020). Confirm labels and any updates; other countries differ.
- **HRD score cut-off ≥ 42** — the commercial genomic instability score used in ovarian cancer trials; check the current companion-diagnostic label.
- **POLE P286R HGVS** (`NM_006231.4:c.857C>G`) — confirm transcript version and coordinate in ClinVar/Ensembl.
- **COSMIC signature version** (v3.5, November 2025 at time of writing) and aetiologies listed in the table — confirm on the COSMIC site.
- **Tandem duplication size classes** (~10 kb for BRCA1; large for CDK12) — approximate; check Menghi et al. and PCAWG SV papers if you need numbers.
- **"~15% of colorectal cancers are MSI"** — varies by stage (higher in stage II, lower in metastatic disease).
- **Immunotherapy response in temozolomide-induced hypermutated glioma** — an area of active research; check recent studies.
