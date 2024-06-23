---
title: R Environment on HiPerGator
summary: Setup and management of the R environment on HiPerGator, including package installation and using RStudio.
weight: 4
---

## Managing R Environment

### Install R Packages
R packages can be installed to the user space using several methods depending on the source of the package:

  - **From CRAN-R**:
```
module load R/X.X
R
> install.packages("PACKAGE")
```
  - **From GitHub repository**:
```
module load R/X.X
R
> devtools::install_github("author/software")
# or
> remotes::install_github("author/software")
```
  - **From tarball (tar.gz) files**:
```
module load R/X.X
R CMD INSTALL /path/package.tar.gz
```

### Environment Modules
- Run `module spider R` to find available R environment modules.
- The available environments are listed in the Installed Libraries table. For more details, visit [HiPerGator R Documentation](https://help.rc.ufl.edu/doc/R).

### Create new R Environment
To request the installation of additional libraries, file a support ticket at HiPerGator Support.

## RStudio
RStudio is an integrated development environment (IDE) for R, featuring tools for plotting, history, debugging, and workspace management, among others. The recommended way to run RStudio is through Open OnDemand on HiPerGator.

### Accessing Blue and Orange Drives in RStudio
By default, the RStudio file browser accesses your home directory. To access other directories such as `/blue` or `/orange`, you can:
1. Create a symlink to your target directory in home:
```
$ cd
$ ln -s /blue/group_name/user_name/ blue
```
Replace `group_name` and `user_name` with your actual group and user names.
2. Change your working directory using R console: In RStudio, click on the `[Gear] More` menu in the RStudio file browser and choose `Synchronize Working Directory`. Next, run
```
setwd('/blue/group_name/user_name/')
```
This will update the file browser to reflect the new working directory.


### Clearing R Markdown Outputs

Before sharing your R Markdown files on GitHub or other platforms, it's important to clear the output to keep the repository clean and to prevent the accidental sharing of sensitive data displayed in outputs. You can clear outputs both from the RStudio interface and via the command line.

- **Using the RStudio Interface**:
To clear outputs using the RStudio interface:
    1. Open your R Markdown file in RStudio.
    2. Navigate to the top menu and select `Edit`.
    3. Click on `Clear All Output`.

This will remove all outputs from the R Markdown file, ensuring that only the code and markdown cells remain. This approach is useful for keeping the workspace tidy and preventing the inclusion of unwanted results.

- **Using the Command Line**:  For a command-line approach, particularly useful for automating the process or clearing multiple R Markdown files at once, you can use a script to render the R Markdown without output:
```
Rscript -e "rmarkdown::render('/Users/qixu/Desktop/aa.Rmd', clean = TRUE)"
```
This command will render the R Markdown file and remove intermediate files, effectively clearing the outputs and ensuring that the document is ready for sharing without revealing sensitive information.
