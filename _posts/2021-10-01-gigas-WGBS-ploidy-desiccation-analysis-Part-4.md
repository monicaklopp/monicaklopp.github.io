---
layout: post
title: Thurs. Sept. 30, 2021
subtitle: Bisulfide sequencing analysis - Part 4
gh-repo: mattgeorgephd/mattgeorge.github.io
gh-badge: [star, fork, follow]
tags: oyster temperature triploid diploid methylkit DML
comments: true
---

Project name: [project-gigas_ploidy](https://github.com/mattgeorgephd/project-gigas_ploidy) <br />
Funding source: [unknown]() <br />
Species: *Crassostrea gigas* <br />
variable: ploidy, desiccation, high temperature <br />

### Background
After looking through the MethylKit output generated from Ronit's samples, we are having trouble making sense of our results without the inclusion of diploid and triploid controls. To address this issue, Steven suggested that we include some of the other WGBS data we have for pacific oysters, namely from Yammini's hawaii data, Roberto's samples, and the Manchester gonad samples, as outlined within this [notebook post](https://sr320.github.io/Gigome/).

Steven ran all of these through bismark and the resulting samples are stored on gannet [here](https://gannet.fish.washington.edu/seashell/bu-mox/scrubbed/061021-big/).

Here I will add Yammini's controls to Ronnit's data and run methylkit again.

### Methylkit analysis

The first thing I did was move the files Steven generated out of the scrubbed folder and into [my folder](https://gannet.fish.washington.edu/panopea/061021-big)

Next I ran Methylkit using this [R script]().

First, the files coverage files from Bismark were processed using methRead. With Yammini's controls, we have 22 samples (11 diploid and triploids), 10 Heated and 12 controls. Ploidy information was included in the treatment parameter using 0 = diploid, 1 = triploid.  
```
processedFiles <- methylKit::methRead(analysisFiles,
                                      sample.id = as.list(sampleMetadata$sampleID),
                                      assembly = "Roslin",
                                      treatment = sampleMetadata$ploidyTreatment,
                                      pipeline = "bismarkCoverage",
                                      mincov = 2) #Process files. Treatment specified based on ploidy status. Use mincov = 2 to quickly process reads.
```
Files were then processed and filtered by 10x coverage using filterByCoverage:

```
processedFilteredFilesCov10 <- methylKit::filterByCoverage(processedFiles,
                                                          lo.count = 10, lo.perc = NULL,
                                                          high.count = NULL, high.perc = 99.9) %>% methylKit::normalizeCoverage(.)
```

The methylation information was then generated using unite:

```
methylationInformationFilteredCov10 <- methylKit::unite(processedFilteredFilesCov10,
                                                       destrand = FALSE,
                                                       mc.cores = 8)
```

This resulted in 480,579 identified methylated CpGs. Whether oysters were Heated or not was then added as a co-variate and the number of differentially methylated loci (DML, hyper and hypo) were identified using calculateDiffMeth and getMethylDiff using a 20% difference threshold:

```
covariateHEAT <- data.frame("HEAT" = c(rep("H", times = 10),
                                       rep("C", times = 12))) #Create dataframe with HEAT covariate information

differentialMethylationStatsPloidyCov10 <- methylKit::calculateDiffMeth(methylationInformationFilteredCov10,
                                                                   covariates = covariateHEAT).

diffMethStatsPloidyCov10Diff20 <- methylKit::getMethylDiff(differentialMethylationStatsPloidyCov10, difference = 20, qvalue = 0.01)

diffMethStats20FilteredCov10Hyper <- methylKit::getMethylDiff(differentialMethylationStatsPloidyCov10, difference = 20, qvalue = 0.01, type = "hyper")

diffMethStats20FilteredCov10Hypo <- methylKit::getMethylDiff(differentialMethylationStatsPloidyCov10, difference = 20, qvalue = 0.01, type = "hypo")
```
DMLs = 1038 identified, 442 Hyper, 596 hypo

From here we can generate PCAs that look at the distribution of CpG and DML across ploidy.

Ploidy, Heat-covariate, All 480,579 CpGs
![](/post_images/100421/2021-10-04-All-Data-PCA-ploidy.png)

Ploidy, Heat-covariate, 1038 DML only
![](/post_images/100421/2021-10-04-DML-Only-PCA-ploidy.png)

I then repeated the analysis, using HEAT as the treatment and ploidy as the covariate. The same number of CpGs were identified (480,579).

DMLs = 2351 identified, 1150 Hyper, 1201 hypo

Heated, ploidy-covariate, All 480,579 CpGs
![](/post_images/100421/2021-10-04-All-Data-PCA-heat.png)

Heated, ploidy-covariate, 2351 DML only
![](/post_images/100421/2021-10-04-DML-Only-PCA-heat.png)

From all the DML tables, the following charts were then generated:

DML count comparison
![](/post_images/100421/DML_count_figure.png)
