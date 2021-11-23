---
layout: post
title: Mon. Nov. 15, 2021
subtitle: Bisulfide sequencing analysis - Part 6
gh-repo: mattgeorgephd/mattgeorge.github.io
gh-badge: [star, fork, follow]
tags: oyster temperature triploid diploid methylkit DML
comments: true
---

Project name: [project-gigas_ploidy](https://github.com/mattgeorgephd/project-gigas_ploidy) <br />
Funding source: [unknown]() <br />
Species: *Crassostrea gigas* <br />
variable: ploidy, desiccation, high temperature <br />

[previous notebook entry](https://mattgeorgephd.github.io/gigas-WGBS-ploidy-desiccation-analysis-Part-5/)

### Background
After comparing analyses and looking at genome feature locations, we decided to continue using the Ronit dataset with Yaamini controls to see what the processes look like.

### GOterm annotation
GOterm annotation was carried out using this [jupyter-notebook]()

The order of operations included: </br>
1. Creating a master annotation table using DIAMOND blastx
2. Joining with GO terms
3. Joining with GO slim terms
4. Matching CpG background and DML lists with GOterms

Matching the DML looked a little something like this:

```
!intersectBed \
-wb \
-a DML/DML-getMethylDiff-ploidy-Cov10-20.bed \
-b GFF/cgigas_uk_roslin_v1_gene.gff \
> DML/DML-ploidy-Cov10-20-Gene-wb.bed
```

Output:
DML-Cov10-20-BOTH-COMBO.GeneIDs.geneOverlap.transcriptIDs.GOAnnot
BOTH datasets = RONIT + YAAMINI Controls

BOTH datasets - Overlapping DML - 833 unique GOIDs, 517 associated with BP
BOTH datasets - PLOIDY DML - 3264 unique GOIDs, 29 unique genes


##########################################################################
```
Here is the prior table for reference:

Table 1. DML counts from each analysis
![](/post_images/100421/DML_count_table.png)

Here are the plots:

Figure 1. Each dataset separately
![](/post_images/100621/genome_location_INDIVIDUAL.png)

Figure 2. Both datasets together
![](/post_images/100621/genome_location_BOTH.png)
