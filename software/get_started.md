---
layout: software_layout
title: Get Started
---

# Getting Started with Seurat

The input to Seurat is a gene expression matrix, where the rows are genes and the columns are single cells. To get started, first [install]({{"/software/install/"" | prepend: base.url}}) the software and load the package library.

## Tutorial -- Guided Clustering of 3K PBMC
This tutorial walks through analyzing a dataset of 2,700 Peripheral Blood Mononuclear Cells (PBMCs) made publically available by 10X Genomics using Seurat. The raw data can be found [here](https://s3-us-west-2.amazonaws.com/10x.files/samples/cell/pbmc3k/pbmc3k_filtered_gene_bc_matrices.tar.gz). The tutorial is also available as an R markdown file [here](https://raw.githubusercontent.com/satijalab/satijalab.github.io/master/software/pbmc-tutorial.Rmd ).

[![PBMC-Tutorial]({{"/img/pbmc-tutorial.svg" | prepend: site.imgurl }})]({{ "pbmc-tutorial.html" | prepend: site.software_nav }})

Seurat combines linear and non-linear dimensionality reduction algorithms for unsupervised clustering of single cells. The approach can be described briefly:

1. Identification of highly variable genes
2. Linear dimensionality reduction (PCA) on variable genes
3. Determine significant principal components
4. Graph based clustering to classify distinct groups of cells
5. Non-linear dimensional reduction (t-SNE) on the significant PC scores (i.e. spectral t-SNE) for cluster visualization
6. Marker discovery, visualization, and downstream analysis


## Previous versions and tutorials
All of the old tutorials be found [here]({{ "/software/old-get-started/" | prepend: base.url  }}) and all of the code is available on [github](https://github.com/{{ site.github_username }}/seurat).
