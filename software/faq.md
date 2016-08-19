---
layout: software_layout
title: FAQ
permalink: /software/faq
---
# Frequently Asked Questions

1. **What's new in the latest version of Seurat?**
	* **New functionality**
		* **Graph-based clustering**: A new clustering approach has been implemented that makes use of graph based clustering techniques.
		Briefly, a k-nearest neighbor graph is constructed based on the PC loadings for each cell. From this, cells are connected based
		on the overlap in their neighborhoods to form the SNN graph. This serves as the input for the modularity optimization function
		which iteratively groups cells into clusters based on the change in the density of connections within a cluster versus between clusters.
		* **Easy removal of technical artifacts**: The *RegressOut()* function has been added to enable removing unwanted effects from the
		data through linear regression.
		* **PCA**: The *PCA()* function has been changed so that it now models each cell as a linear combination of genes.
	* **Speed improvements**
		* Faster object creation
		* Faster data retrieval - speeds up many operations including many of the plotting functions
		* Support for sparse matrices
	* **Stylistic improvements**
		* **Consistent naming conventions**: All functions have been renamed to follow a style consistent with [Google's R style guide](https://google.github.io/styleguide/Rguide.xml).
		* **Minor visualization improvements**:
			* *PCHeatmap()* can now take multiple PCs as an argument and will plot a grid of heatmaps
			* Plotting functions now all utilize ggplot2
		* **General documentation improvement**


2. **How do I select which PCs to use?**
	* Our rationale is that downstream analyses like clustering and tSNE benefit from dimensional reduction because it dramatically reduces
	the technical noise associated with single cell RNA-sequencing data. Essentially, each PC represents a robust 'metagene' --- a linear
	combination of hundreds to thousands of individual transcripts --- that is robust to drop-out events in any individual gene. However,
	this PCA step introduces a key parameter choice of how many PCs to use in downstream steps. Estimating the true dimensionality
	of a dataset is a challenging and common problem in machine learning. We have three main approaches for trying to estimate this
	parameter.
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
	to visualize and explore these dimensions in their data, rather than blinding trusting the output of a statistical test or scree plot. Seurat
	provides a number of functions (PCHeatmap, VizPCA, PrintPCA) to assist in this.

3. **How do I select my set of variable genes?**
	* Seurat provides the function *MeanVarPlot()* to help in variable gene selection. This function displays dispersion vs average expression. We recommend setting the cutoff parameters in this function visually by evaluating this plot for outliers. We recommend erring towards
	more rather than fewer variable genes because in our experience, running the PCA on all genes generally gives comparable results to a well selected variable gene set.

4. **What's different about the new clustering approach**
	* We previously clustered cells based on their relative position in the tSNE plot. In our updated version, we now use the tSNE exclusively
	for visualization, and cluster based on a 'community detection' approach similar to one previously proposed for analyzing CyTOF data
	[Levine et al, Cell 2015](http://www.cell.com/cell/references/S0092-8674(15)00637-6). Importantly, our distance metric between cells
	is still computed in PCA space, as in [Macosko et al, 2015](http://www.ncbi.nlm.nih.gov/pubmed/26000488). While the
	new approach often returns similar results, and is consistent with the tSNE visualization, we have found that graph-based clustering
	can more sensitively detect subtle sources of heterogeneity between cell populations.

5. **Any new features coming soon?**
	* New statistical methods for data normalization, variable gene selction, and differential expression based on a stastical framework
	for UMI count data.
	* Support and tutorials for laptop computer processing of large datasets (>50,000 cells)
