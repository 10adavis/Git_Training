---
output: github_document
---



# Reproducible code using git and GitHub

This tutorial covers version control with git. The tutorial is meant to be hands-on, so the target audience should have access to a PC (preferably Windows) with an internet connection. One must also install Git for Windows v2.31.1, and an active R/R Studio environment.

We will begin with a brief introduction to the concepts of git and then move on to some hands-on learning (no prior experience needed). At the end of the meeting, you will know how to create a repository, commit changes, and push/pull changes from a remote repository. 

To support the reproducibility of these analyses, this tutorial employs literate programming using [Rmarkdown(Rmd)](https://rmarkdown.rstudio.com/) and full R package dependency management using the [renv](https://rstudio.github.io/renv/articles/renv.html) package.

## Prerequisites:

### Hardware:
* A computer with an internet connection

### Software:
* Register a GitHub Account: [https://github.com](https://github.com)    
* Install [Git for Windows v2.31.1 64-bit](https://git-scm.com/download/win) also known as msysgit or “Git Bash”, to get Git in addition to some other useful tools, such as the Bash shell. Yes, all those names are totally confusing, but you might encounter them elsewhere and I want you to be well-informed.
  * NOTE: When asked about “Adjusting your PATH environment”, make sure to select “Git from the command line and also from 3rd-party software”. Otherwise, we believe it is good to accept the defaults.
  * Note that RStudio for Windows prefers for Git to be installed below C:/Program Files and this appears to be the default. This implies, for example, that the Git executable on my Windows system is found at C:/Program Files/Git/bin/git.exe. Unless you have specific reasons to otherwise, follow this convention.
 
#### Configure git user info:
* Introduce yourself to Git using Git Bash (included with Git for Windows). 
In the shell, configure your global user name and user email (associated with your github account):

```bash
git config --global user.name 'Jane Doe'
git config --global user.email 'jane@gmail.com'
git config --global --list
```
  * For additional instructions, see: [https://happygitwithr.com/hello-git.html](https://happygitwithr.com/hello-git.html)


* (Optional) Install a Git client. Learning version control (e.g. git) is much easier with the use of a GUI, which is frequently called a git client. My favorite client for windows is [Sourcetree](https://www.sourcetreeapp.com/). 
    * For additional info, see: [https://happygitwithr.com/git-client.html](https://happygitwithr.com/git-client.html).

During our meeting I will (likely) give a brief demo using Sourcetree and RStudio, which is nicely integrated with git, and is the primary interface I personally use.

## Hands On Demo:
### To run R/RStudio locally: 
* Install [R version 4.0.0 or above](https://www.r-project.org/)
* Install [RStudio Desktop 1.2 or above](https://rstudio.com/products/rstudio/)

### Running the test analysis:
This tutorial includes a very simple analysis, executed in 2 .Rmd scripts. In [1.02_Hello-World.Rmd](Scripts/1.02_Hello-World.Rmd)  which reads in an excel spreadsheet and outputs the contents of that spreadsheet to a .txt file. In [2.02_PCA-example.Rmd](Scripts/2.02_PCA-example.Rmd), we run a simple PCA analysis of the mtcars dataset. 

After cloning this repo, the first required step is to install the R dependencies required to run the analysis (written in the .Rmd files in R_scripts). To do so, execute the following command in your R environment.


```r
renv::restore()
```

This will automatically install the packages required to run this analysis. By doing this, one will be able to execute the analysis using the same R packages (and the same versions) each time. Note that this will only need to be run once. 

#### Mechanics:
To run this analysis, first create/clean the results output folder by running the codes in [95_Make_Clean.Rmd](). Subsequently, run the code chunks in [99_Run_All.Rmd](R_scripts/99_Run_All.Rmd). This will run the Rmarkdown (.Rmd) files containing the actual code for this analysis in numerical order. 

Running [99_Run_All.Rmd](R_scripts/99_Run_All.Rmd) will also render html files of each .Rmd file, which will be saved to the results folder, making useful reports of this analysis. Finally, this README.Rmd files will also be "knit" to an html file, as well as a markdown (.md) file, in the working directory of this repository. This markdown file makes for easy viewing on GitHub, and acts as the "home page" for this repo.

#### Output:
The resulting output files were saved to the [Results](Results) folder in this repository. 


```
#> [1] "1.02_Hello-World.html"  "1.02_Hello-World.md"   
#> [3] "2.02_PCA-example.html"  "2.02_PCA-example.md"   
#> [5] "2.02_PCA-example_files" "Hello_World.txt"       
#> [7] "PCA_Eigenvectors.pdf"
```

## Background slides:  
* [Slides for Git Training Session](Presentations/An_Intro_to_Git.pptx) (includes presentation on git concepts)

## Session information


```r
sessionInfo()
#> R version 4.0.4 (2021-02-15)
#> Platform: x86_64-w64-mingw32/x64 (64-bit)
#> Running under: Windows 10 x64 (build 19041)
#> 
#> Matrix products: default
#> 
#> locale:
#> [1] LC_COLLATE=English_United States.1252 
#> [2] LC_CTYPE=English_United States.1252   
#> [3] LC_MONETARY=English_United States.1252
#> [4] LC_NUMERIC=C                          
#> [5] LC_TIME=English_United States.1252    
#> 
#> attached base packages:
#> [1] stats     graphics  grDevices datasets  utils     methods  
#> [7] base     
#> 
#> other attached packages:
#> [1] rmarkdown_2.7    here_1.0.1       ggfortify_0.4.11
#> [4] ggplot2_3.3.3    readxl_1.3.1    
#> 
#> loaded via a namespace (and not attached):
#>  [1] Rcpp_1.0.6        highr_0.9         cellranger_1.1.0 
#>  [4] pillar_1.6.0      compiler_4.0.4    tools_4.0.4      
#>  [7] digest_0.6.27     evaluate_0.14     lifecycle_1.0.0  
#> [10] tibble_3.1.1      gtable_0.3.0      pkgconfig_2.0.3  
#> [13] rlang_0.4.10      cli_2.5.0         yaml_2.2.1       
#> [16] xfun_0.22         gridExtra_2.3     withr_2.4.2      
#> [19] dplyr_1.0.5       stringr_1.4.0     knitr_1.33       
#> [22] generics_0.1.0    vctrs_0.3.8       rprojroot_2.0.2  
#> [25] grid_4.0.4        tidyselect_1.1.0  glue_1.4.2       
#> [28] R6_2.5.0          fansi_0.4.2       farver_2.1.0     
#> [31] tidyr_1.1.3       purrr_0.3.4       magrittr_2.0.1   
#> [34] scales_1.1.1      ellipsis_0.3.2    htmltools_0.5.1.1
#> [37] colorspace_2.0-0  renv_0.13.2       labeling_0.4.2   
#> [40] utf8_1.2.1        stringi_1.5.3     munsell_0.5.0    
#> [43] crayon_1.4.1
```

This document was processed on: 2021-05-04.

