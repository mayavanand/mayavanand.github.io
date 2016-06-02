---
layout: post
title: Filtering VCFs by Position Using Bcftools
modified:
categories: 
excerpt:
tags: []
image:
  feature:
date: 2016-06-02T15:49:03-04:00
---
`bcftools view` is a useful tool for subsetting VCFs. There are several different options that can be used alone or in combination to filter only variants appearing at specific coordinates.

For the purposes of this post, I will be specifying the desired coordintes using a .txt file and exploring the nuances between the `-R` and `-T` options.
The `-r` option works similarly to the `-R` option and `-t` works similary to `-T`, however `-t` and `-r` must be followed by a comma separated list of regions instead of a .txt file.

## -R (regions-file)
The regions-file option requires the VCF files to be compressed with bgzip and indexed by tabix. Since the index is used to jump to positions in the original vcf to be subsetted.
For variations spanning a region like indels, regions-file includes the variation in the resulting subset vcf if a coordinate in the file overlaps the region.

## -T (targets-file)
The targets-file option does not require indexed VCF files and streams the whole vcf to access the next position.
For variations spanning a region like indels, targets-file only includes the variation in the subset if the coordinate in the file matches that start coordinate of the variation.

## -R and -T in combination
When regions-file and targets-file are used in combination, the same file containing coordinates should be specified for both options.
Indexed VCF file must be used.
The index is used to jump to the next position, however variations are only included in the subset if the coordinate in the file matches the start coordinate.


## -R with -v snps 
If only one is only interested in simple snps, `-v snps` can be used to filter the output only to simple snps in combination with -R.
This should acheive the same result as using -R and -T if all coordinates in the position file refer to simple snps. 
