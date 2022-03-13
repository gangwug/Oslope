## Introduction

CYCLOPS (Cyclic Ordering by Periodic Structure) is a tool designed to reconstruct the temporal ordering of high dimensional 
that is generated by a common periodic process. Detail descriptions of the CYCLOPS approach can be found online at 
[PNAS](http://www.pnas.org/content/early/2017/04/19/1619320114.full) (Anafi R.C. et al., CYCLOPS reveals human transcriptional
rhythms in health and disease. Proc Natl Acad Sci U S A. 2017. 114(20):5312-5317). The original and in-development version of
CYCLOPS could be found from the GitHub page of Dr. [Ron C. Anafi](https://github.com/ranafi). 

Oscope is a tool desigend to identify and characterize the transcriptional dynamics of oscillating genes in single-cell RNA-seq data from an unsynchronized cell population. Detail descriptions of the Oscope method can be found online at [Nat Methods](https://www.nature.com/articles/nmeth.3549)(Leng N., Chu LF et al., Oscope identifies oscillatory genes in unsynchronized single cell RNA-seq experiments. Nat Methods. 2015. 12(10):947–950). The Oscope package could be found from [Bioconducor](https://bioconductor.org/packages/release/bioc/html/Oscope.html).

This Oslops repository combines CYCLOPS and Oscope into a new pipleline that was developed to order ~300 human epidermis samples published on 
[PNAS](https://www.pnas.org/content/115/48/12313.long) (Wu G., et al., Population-level rhythms in human skin with implications for circadian medicine. Proc Natl Acad Sci U S A. 2018. 115(48):12313-12318). It was furter improved to order more human epidermis and dermis samples collected from different body sites published on [Genome Medicine](https://link.springer.com/article/10.1186/s13073-020-00768-9) (Wu G., et al., A population-based gene expression signature of molecular clock phase from a single epidermal sample. Genome Med. 2020. 12(1):73. doi: 10.1186/s13073-020-00768-9). 

## Files

CYCLOPSv3: the source julia code file from CYCLOPS (julia version 0.3.12)

runCYCLOPS_Eigen.jl: the code file for getting the Eigen genes

runOscope.R: the code file for selecting Eigen clusters

runCYCLOPS_Order.jl: the code file for ordering

clockList.csv: the input seed gene list for ordering

CYCLOPSout: the output folder for CYCLOPS ordering

example.ToRunCYCLOPS.csv: an example of expression data

skinBenchmarkMatrixARNTLorder.csv: the benchmark correlation matrix used for down-sampling (minor different from the 17 clock and clock-associated genes, which may be helpful for avoiding the bias of using the same 17 seed gene list during ordering)

randomSampling.R: the code file for maximizing the oscillation signal by down-sampling

## Advice about running this pipeline

Step 1: prepare the input data file (e.g., example.ToRunCYCLOPS.csv). Make sure the first column is gene name/id, other columns are samples, and make sure that there are no duplicate gene name/id in the first column. If the input expression data file does not have a functional clock, tested by [nCV](https://github.com/gangwug/nCV) using 'skinBenchmarkMatrixARNTLorder.csv' as the reference matrix, randomSampling.R may be helpful for selecting subset of samples with a functional clock. 

Step 2: run 'runCYCLOPS_Eigen.jl' to generate the eigen genes.

Step 3: run 'runOscope.R' to select clusters of cycling eigen genes with different phase.

Step 4: run 'runCYCLOPS_Order.jl' to order the samples using selected eigen gene clusters.

Step 5: Check and evaluate the output results in 'CYCLOPSout' folder. 

## License
This package is free and open source software, licensed under GPL(>= 2).

