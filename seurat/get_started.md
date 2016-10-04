---
layout: software_layout
title: Get Started
---

# Getting Started with Seurat

The input to Seurat is a gene expression matrix, where the rows are genes and the columns are single cells. To get started, first [install]({{"/seurat/install/" | prepend: base.url}}) the software and load the package library.

## Guided Analyses
The first tutorial walks through analyzing a dataset of 2,700 Peripheral Blood Mononuclear Cells (PBMCs) made publically available by 10X Genomics using Seurat. The raw data can be found [here](https://s3-us-west-2.amazonaws.com/10x.files/samples/cell/pbmc3k/pbmc3k_filtered_gene_bc_matrices.tar.gz). The tutorial is also available as an R markdown file [here](https://raw.githubusercontent.com/satijalab/satijalab.github.io/master/seurat/pbmc-tutorial.Rmd ). This tutorial is the most detailed and new users should start with this one. The first command list below analyzes a dataset of 33,000 PBMCs also made publically available by 10X genomics. This command list can be helpful for users wanting to analyse larger single cell datasets. The raw data can be found [here](https://s3-us-west-2.amazonaws.com/10x.files/samples/cell/pbmc33k/pbmc33k_filtered_gene_bc_matrices.tar.gz) and the final object [here](https://www.dropbox.com/s/4cams873t2azmpf/pbmc33k.Rda?dl=0). The second command list analyzes a dataset of 8,500 single cells from human pancreas made available by the [Yanai lab](https://yanailab.org/). The raw data can be found [here](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE84133) and the final object [here](https://www.dropbox.com/s/av5p7d3ro4m0fb5/pancreas.Rda?dl=0).

<div id="tutorials">
	<div class="tutorial-image">
		<a href="{{ "pbmc-tutorial.html" | prepend: site.seurat_nav }}">
			<img src="{{"/img/pbmc-tutorial.svg" | prepend: site.imgurl }}" alt= "PBMC Tutorial" />
		</a>
	</div>
	<div class="tutorial-image">
		<a href="{{ "pbmc-tutorial.html" | prepend: site.seurat_nav }}">
			<img src="{{"/img/pbmc33k-cl.svg" | prepend: site.imgurl }}" alt= "PBMC Tutorial" />
		</a>
	</div>
	<div class="tutorial-image">
		<a href="{{ "pbmc-tutorial.html" | prepend: site.seurat_nav }}">
			<img src="{{"/img/pancreas-cl.svg" | prepend: site.imgurl }}" alt= "PBMC Tutorial" />
		</a>
	</div>
</div>


Seurat combines dimensionality reduction and graph-based partioniong algorithms for unsupervised clustering of single cells. The approach can be described briefly:

1. Identification of highly variable genes
2. Linear dimensionality reduction (PCA) on variable genes
3. Determine significant principal components
4. Graph based clustering to classify distinct groups of cells
5. Non-linear dimensional reduction (t-SNE) for cluster visualization
6. Marker discovery, visualization, and downstream analysis


## Previous versions and tutorials
All of the old tutorials be found [here]({{ "/seurat/old-get-started/" | prepend: base.url  }}) and all of the code is available on [github](https://github.com/{{ site.github_username }}/seurat).
