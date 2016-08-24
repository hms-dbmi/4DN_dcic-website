---
layout: data_standards
title: Data Standards | 4DN DCIC
tag: data_standards
permalink: /data standards/
---

# Background

The 4DN Consortium will be generating a lot of Hi-C data, which will be processed and made available to the scientific community via the 4DN Data Portal. The raw sequencing reads will be made available as FASTQ files (or lossless BAM files), and the mapped reads will be made available as BAM files. But file format(s) are needed to store and distribute pairwise contacts and contact matrices. The format(s) must be easy to use but should also be efficient in terms of disk space and access time 

The 4DN Omics Working Group has investigated a variety of options for formats for different stages of the processing pipeline. (See [this document ](https://docs.google.com/document/d/1Ts9Hcvo-33UK3_pdRLLkMGiU04S7AA-26FM2MdkQw-g/edit?usp=sharing) for details on desired features and considerations.) In particular, two general-purpose binary formats exist to describe contact matrices: the Juicer/Juicebox .hic format (<https://github.com/theaidenlab/juicebox>) and the ICE/Cooler .cool format (<https://github.com/mirnylab/cooler>). A small study comparing running times and disk usage for these formats resulted in roughly similar results. The remaining question is whether these two formats differ in terms of usability.

We are currently performing a study to evaluate the usability of the different formats. It should be noted that the two formats contain very similar information; what is being evaluated are the tools around each format and how easy it will be to develop more tools around them (think bam/sam, samtools, Rsamtools etc.). The focus of the study is on the end user who would like to use these files in some bioinformatics analysis. But, in certain cases, users may also need to generate the files, and evaluation on this task is also welcome. This page provides a basic introduction of these file formats and pointers to files for the usability study. 

#  Juicer/Juicebox .hic

### Introduction and Documentation

The Juicer/Juicebox suite of tools and the .hic file format are described in [Aiden Lab website](http://aidenlab.org/software.html). [The Juicer pipeline](http://aidenlab.org/juicer/docs.html) takes fastq files as input and creates .hic files, containing normalized contact matrices at multiple resolutions. [The Juicebox tools](http://aidenlab.org/commandlinetools/docs.html) read in .hic files and provide visualization and downstream analysis. To create .hic files, users can start with fastq files and run the whole Juicer pipeline or start with the intermeditate text file for valid read pairs, the merged_nodups "pre" format. For advanced users, the .hic file schema is available [here](https://github.com/theaidenlab/juicebox/blob/master/HiC_format_v8.docx).

### Features

The .hic format features:

- Contact matrices in multiple resolutions and summary statistics stored in one file.
- Java and C bindings
- Command line tools
- Extant suite of analysis tools
- Extant visualization tool

### Files

.hic files for a number of papers can be downloaded from [this link](http://aidenlab.org/data.html). The reviewers can use any sample of their choice, from this set or elsewhere. From this set, we can recommend that reviewers use one, two, or three of the following samples to test out different sequencing depths.

- [GM12878 sample I from Rao and Huntley et al. Cell 2014](https://hicfiles.s3.amazonaws.com/hiseq/gm12878/in-situ/primary.hic) with 2.6B contacts.
- [K562 sample from Rao and Huntley et al. Cell 2014](https://hicfiles.s3.amazonaws.com/hiseq/k562/in-situ/combined.hic) with 930M contacts.
- [HUVEC sample from Rao and Huntley et al. Cell 2014](https://hicfiles.s3.amazonaws.com/hiseq/huvec/in-situ/combined.hic) with 460M contacts.



# Cooler .cool

### Introduction and Documentation

The cooler library and .cool file format are described in [the Mirny Lab github repo](https://github.com/mirnylab/cooler/). The cooler python library and command line tools
 take in a text file for read pairs or contact matrices; store the information in the sparse, compressed, binary .cool format; include utilities for performing out-of-core contact matrix balancing; and perform fast range queries on a contact matrix. The .cool format is a sparse, compressed, binary persistent storage format for Hi-C contact matrices based on HDF5. HDF5 is a general purpose binary container format for large scientific datasets, with bindings in multiple languages. Therefore .cool files can be read in as HDF5 files natively in different languages.

### Features
The .cool format features:
- Flexibility to store one or multiple matrices with varying bin sizes.
- python library
- Command line tools
- HDF5, which has native bindings in practically all languages
- out of memory iterative matrix balancing, that can work on very large matrices.

### Files

.cool files for a number of papers can be downloaded from [this link](ftp://cooler.csail.mit.edu/coolers). The reviewers can use any sample of their choice, from this set or elsewhere. From this set, we can recommend that reviewers  one, two, or three of the following samples to test out different sequencing depths.

- Rao2014-GM12878-MboI-allreps-*
- Rao2014-K562-MboI-allreps-*
- Rao2014-HUVEC-MboI-allreps-filtered-*


# Other reference files

Here are pointers to reference maps that can be of interest while studying the Hi-C contact matrices:

- [GM12878 histone marks from ENCODE](https://www.encodeproject.org/search/?type=Experiment&assay_title=ChIP-seq&assembly=hg19&biosample_term_name=GM12878&assay_title=ChIP-seq&files.file_type=bigWig&target.investigated_as=histone+modification) (bigWig tracks)
- [GM12878 CTCF peak calls from ENCODE](https://www.encodeproject.org/search/?searchTerm=gm12878+ctcf&type=Experiment&assay_title=ChIP-seq&biosample_term_name=GM12878&files.file_type=bed+narrowPeak)  (narrowPeak files from 4 different labs processed separately)
- [GM12878 CTCF peak calls with motif orientation (Aiden Lab)](https://hicfiles.s3.amazonaws.com/external/GM12878_CTCF_orientation.bed) from <http://aidenlab.org/data.html>.
- [GM12878 loop calls from Rao and Huntley et al. Cell 2014 (Aiden Lab)](https://hicfiles.s3.amazonaws.com/hiseq/gm12878/in-situ/combined_peaks_with_motifs.txt) from <http://aidenlab.org/data.html>.
- [GM12878 Candidate Enhancer and Promoter maps from ENCODE](https://www.encodeproject.org/search/?type=Annotation&encyclopedia_version=3&biosample_term_name=GM12878&annotation_type=enhancer-like+regions&annotation_type=promoter-like+regions)

- [K562 histone marks from ENCODE](https://www.encodeproject.org/search/?type=Experiment&assay_title=ChIP-seq&assembly=hg19&biosample_term_name=K562&assay_title=ChIP-seq&files.file_type=bigWig&target.investigated_as=histone+modification) (bigWig tracks)
- [K562 CTCF peak calls from ENCODE](https://www.encodeproject.org/search/?searchTerm=k562+ctcf&type=Experiment&assay_title=ChIP-seq&month_released=August%2C+2012&month_released=February%2C+2011&month_released=February%2C+2012&month_released=March%2C+2011&month_released=May%2C+2012&files.file_type=bed+narrowPeak)  (narrowPeak files from 5 different labs processed separately)
- [K562 loop calls from Rao and Huntley et al. Cell 2014 (Aiden Lab)](https://hicfiles.s3.amazonaws.com/hiseq/k562/in-situ/combined_peaks_with_motifs.txt) from <http://aidenlab.org/data.html>.
- [K562 Candidate Enhancer and Promoter maps from ENCODE](https://www.encodeproject.org/search/?type=Annotation&encyclopedia_version=3&biosample_term_name=K562&annotation_type=enhancer-like+regions&annotation_type=promoter-like+regions)

- [HUVEC reference epigone series from ENCODE](https://www.encodeproject.org/reference-epigenomes/ENCSR194DQD/)
- [HUVEC CTCF peak calls from ENCODE](https://www.encodeproject.org/experiments/ENCSR000ALA/)
- [HUVEC loop calls from Rao and Huntley et al. Cell 2014 (Aiden Lab)](https://hicfiles.s3.amazonaws.com/hiseq/huvec/in-situ/combined_peaks_with_motifs.txt) from <http://aidenlab.org/data.html>.

# Contacts

[comment]: # in case the one below does not work on other platforms. [Bill Noble](mailto:wnoble@uw.edu), [Peter Park](mailto:peter_park@HMS.HARVARD.EDU), and [Burak Alver](mailto:burak_alver@hms.harvard.edu).

Please address all questions to [Bill Noble, Peter Park, and Burak Alver](mailto:wnoble@uw.edu,peter_park@HMS.HARVARD.EDU,burak_alver@hms.harvard.edu).


