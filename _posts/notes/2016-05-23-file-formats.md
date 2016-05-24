---
layout: post
title: File Formats
modified:
categories: notes
excerpt: Notes about various file formats useful for this project
tags: []
image:
  feature:
date: 2016-05-23T17:13:07-04:00
---
# File Formats

## PED
Describes individuals and their genetic data.

* Space or tab delimited file
* One line for each individual

Columns:

1. Family ID [string]
2. Individual ID [string] -- unique, containing only alphanumeric characters
3. Father ID [string]
4. Mother ID [string]
5. Sex [integer] -- 1 for female, 2 for male
6. Phenotype [float]
7. SNP1 first allele
8. SNP1 second allele
9. SNP2 first allele
10. SNP2 second allele

[More Information](http://www.shapeit.fr/pages/m02_formats/pedmap.html)

## VCF

* meta-information lines
* header line
* data lines (each for a different position in the genome)

### Meta-information lines
* start with "##"
* must have ''file format' field
* \##fileformat=VCFv4.0

###Header line
* names the 8 fixed, mandatory columns
* tab-delimited

The columns are:

1. \#CHROM
2. POS
3. ID
4. REF
5. ALT
6. QUAL
7. FILTER
8. INFO

### Data lines
* tab-delimited

Fields:

1. \#CHROM: identifier from the reference genome
2. POS: reference position
3. ID: unique identifier like dbSNP rs #
4. REF: A, C, G, T or N, indels include base before event
5. ALT: non-reference alleles called on at least one of the samples; A, C, G, T, N or <ID>
6. QUAL: high scores indicate high confidence
7. FILTER: PASS or codes for filters that fail
8. INFO: additional info

[More Information](http://www.1000genomes.org/wiki/Analysis/Variant%20Call%20Format/vcf-variant-call-format-version-40)

## BAM/CRAM
###BAM
* binary version of a SAM file
* sequence alignment data

###SAM
* Header lines start with ‘@’
* Alignment lines have 11 mandatory fields for essential alignment info
* [More Info](http://samtools.github.io/hts-specs/SAMv1.pdf)

###CRAM
* like BAM
* compressed version of the alignment
* [More Info](http://samtools.github.io/hts-specs/SAMv1.pdf)

## FASTQ
* stores sequences and Phred qualities
* [More Info](http://maq.sourceforge.net/fastq.shtml)

## 23&Me
snp/rs id     chrm #  position    genotype

rs4477212    1         82154      AA
rs3094315    1         752566    AG
rs3131972    1         752721    AG
rs12124819  1         776546    AA
