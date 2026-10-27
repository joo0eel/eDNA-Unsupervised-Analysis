# Unsupervised Discovery of Taxonomic Structure & Biodiversity from Indian Ocean eDNA

Metabarcoding and unsupervised machine learning pipeline for grouping environmental DNA (eDNA) sequences into taxon-like clusters, identifying biodiversity gradients across the 110°E meridian transect (Eastern Indian Ocean), and detecting candidate novel or undocumented taxa.

---

## 📌 Project Overview

Environmental DNA (eDNA) sequencing produces mixed genetic material across thousands of organisms simultaneously. Sequences arrive unlabeled, and reference-database matching frequently fails for uncatalogued marine biodiversity.

This project implements an unsupervised learning workflow to:
1. **Cluster unlabeled Amplicon Sequence Variants (ASVs)** purely from intrinsic sequence properties ($k$-mer nucleotide frequencies) and sample-abundance profiles.
2. **Track biodiversity gradients** (Alpha & Beta diversity, Shannon/Simpson indices) across oceanographic sampling stations along the 110°E meridian.
3. **Detect candidate novel or poorly documented taxa** via anomaly and novelty detection algorithms.
4. **Validate clusters** against taxonomic ground truth (`occurrence.txt`) held out during model training.
5. **Interactive Visualization**: An interactive HTML dashboard presenting 2D & 3D PCA and t-SNE projections with cluster and taxonomic overlays.

---

## 📂 Repository Contents

| File | Description |
|---|---|
| `eDNA_Unsupervised_Project.ipynb` | Complete end-to-end Jupyter Notebook covering EDA, distance metrics, clustering, dimensionality reduction, anomaly detection, and validation. |
| `edna_pca_tsne_dashboard.html` | Standalone interactive 2D/3D visualization dashboard generated from PCA and t-SNE embeddings. |
| `dnaderiveddata.txt` | Raw DNA-derived sequence read table from OBIS (18S rRNA V4 marker). |
| `occurrence.txt` | Ground-truth taxonomy and occurrence table held out during training. |
| `asv_clusters.csv` | Output ASV assignments across unsupervised clustering models. |
| `cluster_profiles.csv` | Summary profile metrics and sequence characteristics per cluster. |
| `station_biodiversity.csv` | Station-level diversity indices across the Indian Ocean transect. |
| `novelty_candidates.csv` | Flagged outlier sequences identified as candidate novel taxa. |
| `requirements.txt` | Python package dependencies. |

---

## 🔬 Methodology & Pipeline

1. **Preprocessing & Feature Extraction**:
   - $k$-mer frequency vectorization ($k=4, 5, 6$) capturing sequence compositional motifs.
   - Normalization, variance thresholding, and TF-IDF scaling.
2. **Distance & Similarity Metrics**:
   - Cosine similarity, Euclidean, and Bray-Curtis dissimilarity matrices.
3. **Clustering Algorithms**:
   - $k$-Means (from scratch and Scikit-learn), $k$-Medoids, MiniBatch $k$-Means.
   - Agglomerative Hierarchical Clustering, DBSCAN, and Gaussian Mixture Models (GMM).
   - Optimal cluster selection via Silhouette Analysis, Davies-Bouldin Index, and Calinski-Harabasz score.
4. **Dimensionality Reduction**:
   - Principal Component Analysis (PCA), t-SNE, UMAP, and Autoencoder embeddings.
5. **Novelty & Anomaly Detection**:
   - Isolation Forest, Local Outlier Factor (LOF), and One-Class SVM to flag atypical genetic signatures.
6. **Validation & Assessment**:
   - Post-hoc validation using Adjusted Rand Index (ARI), Normalized Mutual Information (NMI), and V-measure against OBIS taxonomic designations.

---

## 🚀 Quickstart & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/joo0eel/eDNA-Unsupervised-Analysis.git
cd eDNA-Unsupervised-Analysis
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Open the Notebook
```bash
jupyter notebook eDNA_Unsupervised_Project.ipynb
```

### 4. Interactive Dashboard
Open `edna_pca_tsne_dashboard.html` directly in any modern web browser to interactively explore clusters, stations, and latent projections.

---

## 📊 Dataset & Citation
- **Data Source**: Ocean Biodiversity Information System (OBIS)
- **Marker**: 18S rRNA V4 (Illumina MiSeq)
- **Study Transect**: Latitudinal eukaryote micro- and mesoplankton diversity along the 110°E meridian in the Eastern Indian Ocean.
