---
layout: post
title: Thu. Apr. 1, 2021
subtitle: Bisulfide sequencing analysis - Part 2
gh-repo: mattgeorgephd/mattgeorge.github.io
gh-badge: [star, fork, follow]
tags: oyster temperature triploid diploid bismark methylkit DML
comments: true
---

Project name: RONIT-GIGAS-DESICCATION-3N <br />
Funding source: [unknown]() <br />
Species: *Crassostrea gigas* <br />
variable: ploidy, desiccation, high temperature <br />

### Background:
This is continuation of the WGBS analysis I've been running on Ronit's data. The previous post can be found [here](). I'll be following Yaamini's [walkthrough](https://yaaminiv.github.io/Hawaii-Gigas-Methylation-Analysis-Part5/) in this post to look at the results of bismark.

### List of the progress so far:
1. Completed bismark on mox. The output was then transferred to gannet by running the rsync command as outlined in the previous post. The output is available [here](https://gannet.fish.washington.edu/cgigas-ploidy/globalmeth/030521-ronrosM/030521-ronrosM/).
2. The MultiQC report can be found [here](https://gannet.fish.washington.edu/cgigas-ploidy/globalmeth/030521-ronrosM/030521-ronrosM/multiqc_report.html).

### Pathway forward:
1. Look at MultiQC report.
2. Determine effect of ploidy of %mCpG
3. Continue analysis with [MethylKit](https://bioconductor.org/packages/release/bioc/vignettes/methylKit/inst/doc/methylKit.html).

### Step 1: Look at MultiQC report

Looking over the MultiQC report, alignment was amazingly consistent across samples (~61%).

![](/post_images/040121/summary_statistics.png)

As the samples are from diploid and triploid oysters, a possible issue could differences in genome size across samples. However, the number of reads across all the samples look fairly consistent (68-80 million), with the exception of maybe sample 8 which had almost 90 million.

![](/post_images/040121/bismark_alignment_scores.png)

The deduplication percentages were pretty consistent across samples, with the highest being in sample 8 at 20.6%. At first glance there doesn't seem to be a treatment level effect.

### Step 2: Determine effect of ploidy of %mCpG



![](/post_images/040121/mCpG_figure.png)
