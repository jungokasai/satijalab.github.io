---
layout: software_layout
title: FAQ
permalink: /software/faq
---
# Frequently Asked Questions

### 1. What's new in the latest version of Seurat?
* **New functionality**
	* **Graph-based clustering**: We previously clustered cells based on their relative position in the tSNE plot. In our updated version, we now use the tSNE exclusively for visualization, and cluster based on a 'community detection' approach similar to one previously proposed for analyzing CyTOF data [Levine et al, Cell 2015](http://www.cell.com/cell/references/S0092-8674(15)00637-6). Importantly, our distance metric between cells is still computed in PCA space, as in [Macosko et al, 2015](http://www.ncbi.nlm.nih.gov/pubmed/26000488). While the new approach often returns similar results, and is consistent with the tSNE visualization, we have found that graph-based clustering can more sensitively detect subtle sources of heterogeneity between cell populations.
	* **Methods for removing unwanted sources of variation**: Use *RegressOut()* can be used to mitigate confounding sources of noise (batch, cell cycle, variation in alignment rate, etc.)
	* **PCA**: PCA  models each cell as a linear combination of genes and we've added support for the irlba package in *PCAFast().*
* **Speed improvements**
	* All function support sparse matrices
		* Dramatically reduces memory footprint
		* Large datasets can be analyzed on a personal computer
	* Faster object creation and data retrieval
* **Stylistic improvements**
	* **Consistent naming conventions**: All functions have been renamed to follow a style consistent with [Google's R style guide](https://google.github.io/styleguide/Rguide.xml).
	* **Minor visualization improvements**:
		* *PCHeatmap()* can now take multiple PCs as an argument and will plot a grid of heatmaps
		* Plotting functions now all utilize ggplot2
	* **General improvements to documentation and small bug fixes**


### 2. How do I select which PCs to use for clustering?
* A key step to our clustering approach involves selecting a set of principal components (PCs) for downstream clustering analysis. Essentially, each PC represents a robust 'metagene' --- a linear combination of hundreds to thousands of individual transcripts --- that is robust to drop-out events in any individual gene. However, estimating the true dimensionality of a dataset is a challenging and common problem in machine learning. We have three main approaches for trying to estimate this parameter.
	1. Jackstraw: This is a statistical resampling procedure which is used to essentially construct a null distribution for PC
	scores and will associate each PC with a p-value to enable the assessment of signficance in a more formal statistical framework.
	2. Elbow Plot: We have found that the percent of variance explained by each PC tends to flatten out and become negligible in
	comparison to higher components after a certain point. Also, this point generally corresponds pretty well with the significant PCs
	and is much faster to compute than running Jackstraw.
	3. Supervised analysis: To be sure that you are including the right PCs, a supervised look at several features is recommended.
	First, by plotting a heatmap of the PCs using *PCHeatmap()* is often useful to see where the signal is degrading beyond the point
	of being informative. Also, looking at the genes that define each PC can be useful to help exclude PCs that may be driven primarily
	by things like ribosomal/mitochondrial genes or cell cycle genes.

* In our latest [tutorial]({{ "pbmc-tutorial.html" | prepend: site.software_nav }}), we examine all three options. We strongly encourage users, regardless of their method of choosing PCs,
to visualize and explore these dimensions in their data, rather than blindly trusting the output of a statistical test or scree plot. Seurat
provides a number of functions (PCHeatmap, VizPCA, PrintPCA) to assist in this.

### 3. How do I select my set of variable genes?
* Seurat provides the function *MeanVarPlot()* to help in variable gene selection. This function displays dispersion (a measure of to cell-to-cell variation) as a function of average expression for each gene. Our goal is to identify a set of high-variance genes, and we recommend setting the cutoff parameters in this function by visually evaluating this plot to define outliers. However, particularly when using UMI data, we often obtain similar results including much larger gene sets, including the entire transcriptome.

### 4. Any new features coming soon?
* New statistical methods for data normalization, variable gene selction, and differential expression based on a stastical framework
for UMI count data.
* Tutorials for much larger datasets, stay tuned
