---
layout: post
title: Tues. Mar. 16, 2021
subtitle: Bisulfide sequencing analysis - getting started
gh-repo: mattgeorgephd/mattgeorge.github.io
gh-badge: [star, fork, follow]
tags: oyster temperature triploid diploid bismark mox bowtie2
comments: true
---

1. Project name: RONIT-GIGAS-DESICCATION-3N
2. Funding source:[unknown](https://www.nopp.org/)
3. Species: *Crassostrea gigas*
4. variable: High temperature stress

## Background:
We have bisulfide sequencing data from Ronit's desiccation exposure
experiments using juvenile pacific oysters. Here is the forked [github repo](https://github.com/mattgeorgephd/project-gigas_ploidy).

List of the progress so far:
1. Received [WGBS](https://robertslab.github.io/sams-notebook/2020/11/10/Data-Received-C.gigas-Ploidy-WGBS-from-Ronits-Project-via-ZymoResearch.html) data from ZymoResearch
2. Files were added to the [owl server](https://owl.fish.washington.edu/nightingales/C_gigas/)
3. [Sam ran FastQC](https://robertslab.github.io/sams-notebook/2020/11/10/FastQC-MultiQC-C.gigas-Ploidy-WGBS-Raw-Sequence-Data-from-Ronits-Project-on-Mox.html). Here is the [multiQC report](https://gannet.fish.washington.edu/Atumefaciens/20201110_cgig_fastqc_ronit-ploidy-wgbs/multiqc_report.html)

Here is a list of samples
| SeqID	| Library_Name | 	Tissue | 	Ploidy | 	Desiccation	| Heat_Stress |
| --- | ---| ---| ---| ---| ---|
| zr3534_1 | 	D11-C	| ctenidia	| diploid	| yes| 	no|
| zr3534_2 | 	D12-C	| ctenidia	| diploid	| yes	| no|
| zr3534_3 | 	D13-C	| ctenidia	| diploid	| yes	| no|
| zr3534_4| 	D19-C	| ctenidia	| diploid	| yes	| yes|
| zr3534_5| 	D20-C	| ctenidia	| diploid	| yes	| yes|
| zr3534_6| 	T11-C	| ctenidia	| triploid| 	yes	| no|
| zr3534_7| 	T12-C	| ctenidia	| triploid| 	yes	| no|
| zr3534_8| 	T13-C	| ctenidia	| triploid| 	yes| 	no|
| zr3534_9| 	T19-C	| ctenidia	| triploid| 	yes| 	yes|
| zr3534_10| 	T20-C	| ctenidia	| triploid| 	yes| 	yes|

Desiccation - desiccation for 24 hr at 27C
Heat_stress - 1 hr at 45C  

## Pathway forward:
Now that we have the WGBS files and FastQC did'nt find any large errors, the next steps is to run [Bismark](https://rawgit.com/FelixKrueger/Bismark/master/Docs/Bismark_User_Guide.html#i-bismark-genome-preparation). The files are pretty big, so instead of running it locally, I will use the resources of our [hyak_mox server]((https://github.com/RobertsLab/hyak_mox/wiki/Running-a-Job). Bismark performs alignments of bisulfite-treated reads to a reference genome and cytosine methylation calls at the same time.

The steps I will be following during this analysis are:

1. logging into mox server
2. Generating slurm script (.sh)


## step 1: Logging into mox

  $ ssh mngeorge@mox.hyak.uw.edu
  Password:
  Enter passcode or select one of the following options:

   1. Duo Push to Android (XXX-XXX-5141)
   2. Phone call to Android (XXX-XXX-5141)

  Duo passcode or option [1-2]: 1
           __  __  _____  __  _  ___   ___   _  __
          |  \/  |/ _ \ \/ / | || \ \ / /_\ | |/ /
          | |\/| | (_) >  <  | __ |\ V / _ \| ' <
          |_|  |_|\___/_/\_\ |_||_| |_/_/ \_\_|\_\

      This login node is meant for interacting with the job scheduler and
      transferring data to and from Hyak. Please work by requesting an
      interactive session on (or submitting batch jobs to) compute nodes.

      Visit the Hyak user wiki for more details:
      http://wiki.hyak.uw.edu/Hyak+mox+Overview

      Questions? E-mail help@uw.edu with "hyak" in the subject.

      Run "scontrol show res" to see any reservations in place that will
      prevent your jobs from running with a "(ReqNodeNotAvail,*" error.

## step 2: slurm script and job scheduler

Slurm is an open source, fault-tolerant, and highly scalable cluster management and job scheduling system for large and small Linux clusters. Useful information can be found in the [wiki](https://github.com/RobertsLab/hyak_mox/wiki/Running-a-Job) and in this [example](https://genefish.wordpress.com/2021/03/05/job-nameron-rosm/) that steven provided.

  



mkdir -p zmays-snps/{data/seqs,scripts,analysis}


![](/post_images/121020/tank_upstairs.png)
