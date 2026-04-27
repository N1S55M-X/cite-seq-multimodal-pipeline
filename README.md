# 🧬 CITE-seq Multimodal Pipeline

Multimodal single-cell analysis pipeline integrating RNA and protein (CITE-seq) using Muon and Scanpy for clustering, marker discovery, and pathway interpretation.

---

## 📌 Overview

This project implements an end-to-end multimodal single-cell analysis pipeline using CITE-seq data (RNA + protein).

### Workflow:

- Quality control (cell and gene filtering)
- RNA and protein preprocessing
- Dimensionality reduction (PCA, UMAP)
- Multimodal integration using Weighted Nearest Neighbors (WNN)
- Cell clustering (Leiden)
- Marker gene identification
- Pathway enrichment analysis (KEGG, GO, Reactome)

---

## 📊 Dataset

- PBMC 5k CITE-seq dataset (10x Genomics)
- Species: *Homo sapiens*
- Loaded automatically using `mudatasets`

---

## 🧪 Data Processing Details

### RNA
- Normalization: `normalize_total`
- Log transformation (`log1p`)
- Highly variable gene selection

### Protein (ADT)
- Normalization: library size normalization
- Log transformation (`log1p`)

> Note: Advanced normalization methods such as DSB can improve protein signal quality.

---

## 🧠 Methodological Insight

Clustering is performed on a **multimodal neighbor graph** using **Weighted Nearest Neighbors (WNN)**.

Each cell dynamically weights:
- RNA (transcription)
- Protein (phenotype)

👉 Result:
- More accurate cell-type identification
- Better biological separation

---

## 📈 Results

### 🔹 Cell Clustering (WNN UMAP)

Clear separation of immune populations:
- T cells
- B cells
- NK / cytotoxic cells
- Monocytes / myeloid cells

---

### 🔹 Marker Genes

| Cell Type | Markers |
|----------|--------|
| Monocytes | S100A8, S100A9, CD14, LYZ |
| T cells | CD3D, CD3E, IL7R |
| NK cells | NKG7, GNLY, PRF1 |
| B cells | MS4A1, CD79A |

---

## 🔹 Pathway Enrichment

Top pathways identified:

- Cytoplasmic translation
- Peptide chain elongation
- Ribosome-related processes

> Pathway enrichment is dominated by ribosomal genes (RPL/RPS), reflecting global protein synthesis rather than cell-type-specific biology.

---

## 🔬 Advanced Multi-Omics Interpretation

### Possible RNA–Protein Scenarios

#### 1. Potential Mutated Gene → Misfolded Protein (Hypothesis)
- RNA expressed
- Protein dysfunctional
- Possible mutation or folding issue

#### 2. RNA Present, Protein Absent
- Transcription active
- Translation blocked

#### 3. Protein Present, RNA Absent
- Protein persists after RNA degradation

#### 4. RNA High, Protein Low
- Strong transcription
- Weak translation

#### 5. RNA Low, Protein High
- Protein accumulation or slow degradation

#### 6. Drug Action
- RNA present, protein suppressed

#### 7. Post-Translational Modifications
- Protein altered without RNA change

#### 8. Stress States
- Protein response without RNA reflection

#### 9. Immune Activation
- RNA = cytokines
- Protein = surface markers

#### 10. Cell Fate Decisions
- RNA = lineage
- Protein = identity

---

## ✨ Key Insight

- RNA → what the cell plans to do  
- Protein → what the cell is doing  

👉 Multimodal integration reveals both **cause and effect**

---

## ⚙️ Features

- Automated dataset loading
- Quality control
- RNA + protein analysis
- WNN integration
- Clustering (Leiden)
- Marker detection
- Pathway enrichment

---

## ⚠️ Limitations

- Pathway results dominated by ribosomal genes
- Not fully cell-type-specific enrichment

---

## 🔧 Future Improvements

- Remove ribosomal genes before enrichment
- Add doublet detection
- Extend to RNA + ATAC multi-omics
- Perform per-cluster pathway analysis
