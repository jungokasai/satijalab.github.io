---
layout: software_layout
title: Install
---

# Installation Instructions for Seurat
If you have installed a previous version of Seurat, it is recommended that you restart your R session before loading the new version. First install R and the devtools package.

1. Install [R](https://www.r-project.org/) (v >= 3.2)
2. Recommended : Install [R Studio](https://www.rstudio.com/)
3. Install the “devtools” package from Hadley Wickham

   ```r
   # Enter commands in R (or R studio, if installed)
   install.packages("devtools")
   library(devtools)
   ```


## Instructions for Mac

### Install From Release Binaries


Install Seurat - directly from [Github](https://github.com/{{ site.github_username }}/seurat).

```r
install_url("https://github.com/satijalab/seurat/releases/download/v1.4.0/Seurat_1.4.0.11.tgz", binary = TRUE)
library(Seurat)
```

You will need to be running the latest version (R 3.3.1) for this to work properly. You can find that [here](https://cloud.r-project.org/bin/macosx). If you want to use a different version of R, you will need to install from source.


### Install From Source

Install Seurat - directly from [Github](https://github.com/{{ site.github_username }}/seurat).

```r
install_github("satijalab/seurat")
library(Seurat)
```

This may cause errors on some standard Mac installs due to R being compiled using gfortran-4.8. They will look something like

```r
-L/usr/local/lib/gcc/x86_64-apple-darwin13.0.0/4.8.2'
ld: library not found for -lgfortran
```

To fix this, refer to the following [blog post](http://thecoatlessprofessor.com/programming/rcpp-rcpparmadillo-and-os-x-mavericks-lgfortran-and-lquadmath-error/). NOTE: you will need sudo permissions.

<br>

## Installation on Windows
1. Install [R](https://www.r-project.org/) (v >= 3.2)
2. Recommended : Install [R Studio](https://www.rstudio.com/)
3. Install the “devtools” package from Hadley Wickham

   ```r
   # Enter commands in R (or R studio, if installed)
   install.packages("devtools")
   library(devtools)
   ```
4. Install [Rtools](http://cran.r-project.org/bin/windows/Rtools/)

5. Ensure that Java is installed.
	* Open CommandPrompt and type ```java -version```
	* If this doesn't return a version of java >= 1.6, download the latest [Java SDK from Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) and run the installer.
	* Restart the R session

6. Install Seurat - directly from [Github](https://github.com/{{ site.github_username }}/seurat).

   ```r
   install_github("satijalab/seurat")
   library(Seurat)
   ```
