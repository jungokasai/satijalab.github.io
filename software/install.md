---
layout: software_layout
title: Install
---

# Installation Instructions for Seurat
If you have installed a previous version of Seurat, it is recommended that you restart your R session before loading the new version.

1. Install [R](https://www.r-project.org/) (v >= 3.2)
2. Recommended : Install [R Studio](https://www.rstudio.com/)
3. Install the “devtools” package from Hadley Wickham

   ```r
   # Enter commands in R (or R studio, if installed)
   install.packages("devtools")
   library(devtools)
   ```
4. Install Seurat - directly from [Github](https://github.com/{{ site.github_username }}/seurat).


   ```r
   install_github("satijalab/seurat")
   library(Seurat)
   ```
