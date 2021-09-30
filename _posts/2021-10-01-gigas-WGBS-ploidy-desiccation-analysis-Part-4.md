---
layout: post
title: Thurs. Sept. 30, 2021
subtitle: Bisulfide sequencing analysis - Part 3
gh-repo: mattgeorgephd/mattgeorge.github.io
gh-badge: [star, fork, follow]
tags: update monthly goals
comments: true
---

Project name: [project-gigas_ploidy](https://github.com/mattgeorgephd/project-gigas_ploidy) <br />
Funding source: [unknown]() <br />
Species: *Crassostrea gigas* <br />
variable: ploidy, desiccation, high temperature <br />

### Background
After analyzing looking through the MethylKit output generated from Ronit's samples, we are having trouble making sense of our results without the inclusion of diploid and triploid controls. To address this issue, Steven suggested that we include some of the other WGBS data we have for pacific oysters, namely from Yammini's hawaii data, Roberto's samples, and the Manchester gonad samples, as outlined within this [notebook post](https://sr320.github.io/Gigome/).

Steven ran all of these through bismark and the resulting samples are stored on gannet [here](https://gannet.fish.washington.edu/seashell/bu-mox/scrubbed/061021-big/).

My goal is to add these data to Ronnit's and run methylkit again with ploidy controls.

### Methylkit analysis

The first thing I did was move the files Steven generated out of the scrubbed folder and into [my folder](https://gannet.fish.washington.edu/panopea/061021-big)
