# A Penalized Regression Framework for Building Polygenic Risk Models Based on Summary Statistics From Genome-Wide Association Studies and Incorporating External Information

# Author Contributions Checklist Form


## Data


### Abstract

We have used three genomewide association study (GWAS) datasets (lung
cancer, type 2 diabetes and melanoma) in this paper. The genotype data
of the lung cancer GWAS was used for simulation. The T2D and melanoma
data were used for evaluating the performance of the polygenic risk
score prediction models.

### Availability

Lung cancer GWAS data are not publicly available because of the
confidentiality issue. However, the data access can be applied through
DbGap with study ID: phs000093.v2.p2.

The melanoma GWAS summary data and the individual level GWAS data for
validation are not publicly available because of the confidentiality
issue. However, the data access can be applied through DbGap with study
ID: phs001868.v1.p1.

Genetic Epidemiology Research on Aging (GERA) GWAS were used to
generate one part of summary statistics for T2D and for validating the
risk prediction model. This data set is not publicly available because
of the confidentiality issue. The data access can be applied through
DbGap with study ID: phs000674.v2.p2.

The summary GWAS data (for fitting prediction models) for DIAGRAM
consortium can be downloaded at
http://diagram-consortium.org/downloads.html.

### Description

The only data in the public domain is the T2D GWAS summary level data,
which can be access at http://diagram-consortium.org/downloads.html.

## Code

### Abstract

We implemented algorithms for fitting LASSO models and then build
polygenic risk prediction models. The implementation can incorporate
both functional annotation data genetic pleiotropic information. An R
code/package is available at GitHub: <https://github.com/lsncibb/PANPRS>.

### Description

How delivered (R package, Shiny app, etc.): R package

Licensing information (default is MIT License): GNU

Link to code/repository: GitHub

Version information: V1

### Optional Information 

Hardware requirements: currently works for both Unix/Linux/Mac.


## Instructions for Use


### Reproducibility

Because some part of data are from the DbGap website, these data cannot
be released to public domain. Besides the software, we can provide the
R-code and all raw result files generated from the simulation and real
data analysis for reviewing purpose if necessary. 

Notes


<https://github.com/lsncibb/SummaryLasso> describes the R package. In
addition, we provide a testing example as described below. The current
version works on Unix, Linux and Mac System, and requires R
(>=3.4.3). R packages "gtools" and "permutations" and GCC(>=4.4.7)
are required. 

The example datasets are located in the data directory of the package:

1.  **summaryZ:** Z statistics from the univariate analysis of the
    association between 3614 SNPs and three traits of European ancestry,
    respectively. In the data file, the first trait is considered as the
    primary trait while the other two are secondary traits.

2.  **Nvec:** Sample sizes for the 3 GWAS data sets.

3.  **plinkLD:** LD information (pairwise correlation between two SNPs)
    estimated based on the 1000 Genome project data of European
    ancestry. 

4.  **funcIndex:** a 3614 x 3 matrix (binary) for 3614 SNPs and 3
    functional annotations. 

The following code shows how to run the analysis using the testing data
set. 

```
library("SummaryLasso")
data("summaryZ")
data("Nvec")
data("plinkLD")
data("funcIndex")
output = gsfPEN(summaryZ=summaryZ, Nvec=Nvec, plinkLD=plinkLD,
funcIndex=funcIndex, numfunc=ncol(funcIndex), dfMax = 200)
```
