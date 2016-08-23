---
layout: data_standards
title: Data Standards | 4DN DCIC
tag: data_standards
permalink: /data standards/
---
## Background

The 4DN Consortium will be generating a lot of Hi-C data, which will be processed and made available to the scientific community via the 4DN Data Coordination and Integration Center. The raw sequencing reads will be made available as FASTQ files (or lossless BAM files), and the mapped reads will be made available as BAM files. But some file format is needed to store and distribute pairwise contacts and contact matrices. The format(s) must be easy to use but should also be efficient in terms of disk space and access time.

The 4DN Omics Working Group has investigated a variety of options for formats for different stages of the processing pipeline. In particular, two general-purpose binary formats exist to describe contact matrices: the Juicer/Juicebox .hic format (<https://github.com/theaidenlab/juicebox>) and the ICE/Cooler .cool format (<https://github.com/mirnylab/cooler>). A small study comparing running times and disk usage for these formats resulted in roughly similar results. The remaining question is whether these two formats differ in terms of usability.

This page provides a basic introduction of these file formats and pointers to files for the usability study. 

##  Juicer/Juicebox .hic  

.hic file 

The .hic format has associated interfaces allowing for data to be accessed via Java and C, and also provides an associated suite of visualization and analysis tools (Juicer). The cooler library provides programmatic access via Python. A small study comparing running times and disk usage for these formats resulted in roughly similar results. The remaining question is whether these two formats differ in terms of usability. This is where you come in.


<http://aidenlab.org/software.html>

## ICE/Cooler .cool 


## Other Reference files


juicer documentation: <http://aidenlab.org/juicer/docs.html>
juicebox documentation: <http://aidenlab.org/commandlinetools/docs.html>

## Contacts

[comment]: # in case the one below does not work on other platforms. [Bill Noble](mailto:wnoble@uw.edu), [Peter Park](mailto:peter_park@HMS.HARVARD.EDU), and [Burak Alver](mailto:burak_alver@hms.harvard.edu).

Please address all questions to [Bill Noble, Peter Park, and Burak Alver](mailto:wnoble@uw.edu,peter_park@HMS.HARVARD.EDU,burak_alver@hms.harvard.edu).


