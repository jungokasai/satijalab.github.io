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


<br>

# Installation on Windows
1. Install [R](https://www.r-project.org/) (v >= 3.2)
2. Recommended : Install [R Studio](https://www.rstudio.com/)
3. Ensure that Java is installed.
	* Open CommandPrompt and type ```java -version```
	* If this doesn't return a version of java >= 1.6, download the latest [Java SDK from Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) and run the installer.
	* Restart the R session
4. Install the “devtools” package from Hadley Wickham. There have been some issues with the latest CRAN version of devtools and the latest R release on Windows that cause issues when trying to install all the package dependencies. The latest devtools version on github has addressed this issue. We recommend installing the github version as follows:
	* Clone the repo or download the ZIP at [https://github.com/hadley/devtools](https://github.com/hadley/devtools/archive/master.zip)
	* Install devtools manually

	* ```r
   install.packages("PATH_TO_DEVTOOLS_DIR", type = "source", repos = "NULL")
   library(devtools)
   ```
5. Install Seurat - directly from [Github](https://github.com/{{ site.github_username }}/seurat).

   ```r
   install_github("satijalab/seurat")
   library(Seurat)
   ```
