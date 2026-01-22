# UCSC Genome Browser Hub Documentation

## Hub Overview

**Session URL:** https://genome.ucsc.edu/s/agulka/hg38_GM12878_BAFinh_Stimulus

**Genome Assembly:** hg38

**Cell Type:** GM12878 (human lymphoblastoid cell line)

**Experimental Focus:** Role of BAF complex in cRE maintenance and stimulus response

## Hub Description

This genome browser hub contains multi-omics data examining the effects of BAF (BRG1/BRM-Associated Factor) complex inhibition in GM12878 cells, both under basal conditions and in response to stimuli (IFN-γ and Dexamethasone). The hub integrates ATAC-seq, RNA-seq, ChIP-seq, promoter capture Hi-C, and chromatin state annotations to provide a comprehensive view of chromatin accessibility and gene expression dynamics.

---

## Experimental Design Summary

### Treatments

1. **BAF Inhibitor (BAFinh) - BRM014**: Allosteric inhibitor targeting SMARCA2/A4
   - Time course: 0.5h, 1h, 2h, 6h, 24h (at 10 µM)
   - Dose response at 6h: 10 nM, 100 nM, 1 µM, 10 µM
   - ACBI1: Proteolysis-targeting chimera targeting SMARCA2 and SMARCA4 (also PBRM1; 24h at 1 µM)

2. **Interferon-γ (IFN-γ)**: 
   - Timepoints: 1h, 6h
   - With/without 30min BAFinh pretreatment

3. **Dexamethasone (Dex)**: 
   - Timepoints: 1h, 6h
   - With/without 30min BAFinh pretreatment

4. **DMSO**: Vehicle control for all timepoints and doses

### Data Types

- **ATAC-seq**: Measures chromatin accessibility 
  - Signal tracks represent pooled replicates as fold change over control (background)
- **RNA-seq**: Measures gene expression
  - Signal tracks represent pooled replicates as mean signal (strand-specific)
- **ChIP-seq**: Maps histone modifications and transcription factor binding
  - Signal tracks represent pooled replicates as fold change over control (input)
- **PCHi-C**: Captures promoter-centered chromatin interactions. From Mifsud et al., Nat. Genet., 2015. PMID: 25938943
- **ChromHMM**: 15 chromatin state model in GM12878, from Ernst et al., Nature, 2011. PMID: 21441907
- **cRE**: cRE annotations based on TSS and ChIP-seq peak overlaps with ATAC-seq peaks, as described in this study.

---

## Track Categories

### 1. ATAC-seq Tracks (Chromatin Accessibility)

All ATAC-seq signal tracks represent pooled signal across all replicates, displayed as fold change over control (background).

#### 1.1 BAF Inhibitor Time Course

Chromatin accessibility changes following BAF inhibition (10µM) at various timepoints.

| Timepoint | Dose | Condition | File |
|-----------|------|-----------|------|
| 0.5h | 0 µM | DMSO control | `DMSO_30_pooled.fc.signal.bw` |
| 0.5h | 10 µM | BAFinh | `BRM_30_pooled.fc.signal.bw` |
| 1h | 0 µM | DMSO control | `DMSO_60_pooled.fc.signal.bw` |
| 1h | 10 µM | BAFinh | `BRM_60_pooled.fc.signal.bw` |
| 2h | 0 µM | DMSO control | `DMSO_120_pooled.fc.signal.bw` |
| 2h | 10 µM | BAFinh | `BRM_120_pooled.fc.signal.bw` |
| 6h | 0 µM | DMSO control | `DMSO_6h_pooled.fc.signal.bw` |
| 6h | 10 µM | BAFinh | `BRM_6h_10u_pooled.fc.signal.bw` |
| 24h | 0 µM | DMSO control | `DMSO_24h_pooled.fc.signal.bw` |
| 24h | 10 µM | BAFinh | `BRM_24h_pooled.fc.signal.bw` |

#### 1.2 BAF Inhibitor Dose Response (6h timepoint)

Chromatin accessibility changes at 6 hours across different BAF inhibitor concentrations.

| Dose | File |
|------|------|
| 0 µM (control) | `DMSO_6h_pooled.fc.signal.bw` |
| 10 nM | `BRM_6h_10n_pooled.fc.signal.bw` |
| 100 nM | `BRM_6h_100n_pooled.fc.signal.bw` |
| 1 µM | `BRM_6h_1u_pooled.fc.signal.bw` |
| 10 µM | `BRM_6h_10u_pooled.fc.signal.bw` |

#### 1.3 Stimulus Response (IFN-γ and Dexamethasone)

ATAC-seq profiles following interferon-γ (IFN-γ) or dexamethasone (Dex) treatment, with and without BAFinh pretreatment.

| Condition | Timepoint | File |
|-----------|-----------|------|
| IFN-γ | 1h | `T1_IFN_rep.pooled.fc.signal.bigwig` |
| IFN-γ | 6h | `T6_IFN_rep.pooled.fc.signal.bigwig` |
| Dex | 1h | `T1_Dex_rep.pooled.fc.signal.bigwig` |
| Dex | 6h | `T6_Dex_rep.pooled.fc.signal.bigwig` |
| BAFinh + IFN-γ | 1h | `T1_BRM_IFN_rep.pooled.fc.signal.bigwig` |
| BAFinh + IFN-γ | 6h | `T6_BRM_IFN_rep.pooled.fc.signal.bigwig` |
| BAFinh + Dex | 1h | `T1_BRM_Dex_rep.pooled.fc.signal.bigwig` |
| BAFinh + Dex | 6h | `T6_BRM_Dex_rep.pooled.fc.signal.bigwig` |

#### 1.4 ATAC-seq Peak Annotations

Peak tracks showing differential accessibility regions with color-coded functional categories.

**BAF-dependent peaks (BAFinh/ACBI1 conditions):**
- **Black (RGB 0,0,0)**: BAF-dependent peaks (ATAC log2FC < -1, FDR < 0.05)
- **Light gray (RGB 211,211,211)**: BAF-independent peaks (all other peaks)

| Condition | Timepoint/Dose | File |
|-----------|----------------|------|
| BAFinh | 0.5h (10 µM) | `BAFdep_0.5h_9col.bb` |
| BAFinh | 1h (10 µM) | `BAFdep_1h_9col.bb` |
| BAFinh | 2h (10 µM) | `BAFdep_2h_9col.bb` |
| BAFinh | 6h (10 µM) | `BAFdep_6h_9col.bb` |
| BAFinh | 24h (10 µM) | `BAFdep_24h_9col.bb` |
| BAFinh | 6h (10 nM) | `BAFdep_10nM_9col.bb` |
| BAFinh | 6h (100 nM) | `BAFdep_100nM_9col.bb` |
| BAFinh | 6h (1 µM) | `BAFdep_1uM_9col.bb` |
| ACBI1 | 24h (1 µM) | `BAFdep_ACBI1_9col.bb` |

**Stimulus-induced peaks (IFN-γ/Dex conditions):**
- **Light gray (RGB 211,211,211)**: Non-responsive peaks (no significant accessibility gain at 1h or 6h)
- **Teal (RGB 28,158,119)**: IFN-γ-induced peaks (ATAC log2FC > log2(1.5), FDR < 0.05) at either 1h or 6h 
- **Blue (RGB 88,146,201)**: Dex-induced peaks (ATAC log2FC > log2(1.5), FDR < 0.05) at either 1h or 6h 

| Condition | File |
|-----------|------|
| IFN-γ-induced | `IFN_induced_9col.bb` |
| Dex-induced | `Dex_induced_9col.bb` |

---

### 2. RNA-seq Tracks (Gene Expression)

Strand-specific RNA-seq data showing transcriptional changes. All tracks represent pooled signal across replicates. Each condition includes both plus (+) and minus (-) strand tracks.

#### 2.1 Vehicle Control (DMSO)

| Timepoint | Strand | File |
|-----------|--------|------|
| 1h | + | `rep1_T1_Veh_pooled_plusAll.mean.bw` |
| 1h | - | `rep1_T1_Veh_pooled_minusAll.mean.bw` |
| 6h | + | `rep1_T6_Veh_pooled_plusAll.mean.bw` |
| 6h | - | `rep1_6t_Veh_pooled_minusAll.mean.bw` |

#### 2.2 BAF Inhibitor (10 µM)

| Timepoint | Strand | File |
|-----------|--------|------|
| 1h | + | `rep1_T1_BRM_pooled_plusAll.mean.bw` |
| 1h | - | `rep1_T1_BRM_pooled_minusAll.mean.bw` |
| 6h | + | `rep1_T6_BRM_pooled_plusAll.mean.bw` |
| 6h | - | `rep1_T6_BRM_pooled_minusAll.mean.bw` |

#### 2.3 Interferon-γ (IFN-γ)

| Timepoint | Strand | File |
|-----------|--------|------|
| 1h | + | `rep1_T1_IFN_pooled_plusAll.mean.bw` |
| 1h | - | `rep1_T1_IFN_pooled_minusAll.mean.bw` |
| 6h | + | `rep1_T6_IFN_pooled_plusAll.mean.bw` |
| 6h | - | `rep1_T6_IFN_pooled_minusAll.mean.bw` |

#### 2.4 Dexamethasone (Dex)

| Timepoint | Strand | File |
|-----------|--------|------|
| 1h | + | `rep1_T1_Dex_pooled_plusAll.mean.bw` |
| 1h | - | `rep1_T1_Dex_pooled_minusAll.mean.bw` |
| 6h | + | `rep1_T6_Dex_pooled_plusAll.mean.bw` |
| 6h | - | `rep1_T6_Dex_pooled_minusAll.mean.bw` |

#### 2.5 BAF Inhibitor + Interferon-γ

| Timepoint | Strand | File |
|-----------|--------|------|
| 1h | + | `rep1_T1_BRM_IFN_pooled_plusAll.mean.bw` |
| 1h | - | `rep1_T1_BRM_IFN_pooled_minusAll.mean.bw` |
| 6h | + | `rep1_T6_BRM_IFN_pooled_plusAll.mean.bw` |
| 6h | - | `rep1_T6_BRM_IFN_pooled_minusAll.mean.bw` |

#### 2.6 BAF Inhibitor + Dexamethasone

| Timepoint | Strand | File |
|-----------|--------|------|
| 1h | + | `rep1_T1_BRM_Dex_pooled_plusAll.mean.bw` |
| 1h | - | `rep1_T1_BRM_Dex_pooled_minusAll.mean.bw` |
| 6h | + | `rep1_T6_BRM_Dex_pooled_plusAll.mean.bw` |
| 6h | - | `rep1_T6_BRM_Dex_pooled_minusAll.mean.bw` |

---

### 3. ChIP-seq Tracks (Histone Modifications & CTCF)

ENCODE ChIP-seq data for GM12878 cells. ENCODE accessions are included in file names. The corresponding narrowPeak files for these experiments were used for cRE definition and in machine learning analyses in this study.

| Target | Description | File |
|--------|-------------|------|
| H3K4me3 | Promoter mark (active transcription start sites) | `H3K4me3_ENCFF280PUF.bigWig` |
| H3K4me1 | Enhancer mark | `H3K4me1_ENCFF564KBE.bigWig` |
| H3K27ac | Active enhancer/promoter mark | `H3K27ac_ENCFF469WVA.bigWig` |
| CTCF | Insulator binding protein | `CTCF_ENCFF800WUV.bigWig` |

---

### 4. Chromatin Interaction Data

#### Promoter Capture Hi-C (PCHi-C)

Three-dimensional chromatin interactions focused on promoter regions.

| Track | File |
|-------|------|
| PCHi-C | `PCHi-C_hg38_join.interact.bb` |

---

### 5. Annotation Tracks

#### ChromHMM Chromatin States

15-state chromatin state segmentation for GM12878 from ENCODE/Broad Institute.

| Track | File |
|-------|------|
| ChromHMM | `hg38_wgEncodeBroadHmmGm12878HMM.bigBed` |

#### Candidate Regulatory Elements (cRE)

Annotated candidate regulatory elements. Classes are: Promoter, Active Enhancer, Primed Enhancer, Poised Enhancer, CTCF, and Other

| Track | File |
|-------|------|
| cRE types | `cRE_annot_9col.bigBed` |

---

## File Format Notes

- **`.bw` / `.bigwig`**: BigWig files containing continuous signal data
- **`.bb` / `.bigBed`**: BigBed files containing interval/peak annotations
- **`.interact.bb`**: BigInteract format for chromatin interaction data
- **`fc.signal`**: Fold-change signal tracks (for ATAC-seq)
- **`plusAll` / `minusAll`**: Strand-specific RNA-seq signals

---

## Citation

If using this browser session, please cite the appropriate source for this data and acknowledge ENCODE for the ChIP-seq tracks (ENCFF identifiers provided).