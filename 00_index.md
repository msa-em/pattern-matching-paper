---
title: 'Analysing scanning precession electron diffraction data using pattern matching: phase mapping of aluminium precipitates'
short_title: Pattern matching
numbering:
  heading_2: false
---

+++ {"part": "abstract"} 

Four-dimensional scanning transmission electron microscopy (4D-STEM) and its sub-category scanning precession electron diffraction (SPED), which includes beam precession, have emerged as promising techniques that enable mapping of the spatial distribution of nano-sized phases in multi-phase materials. 
These techniques typically generate large amounts of data and require (semi-)automatic data analysis workflows. 
This work presents a SPED phase mapping methodology called pattern matching (PM), with the aim of combining benefits of and addressing challenges associated with commonly used data analysis methods such as template matching and machine learning algorithms. 
The pattern matching workflow labels pre-processed diffraction patterns by comparing them to template diffraction patterns through normalised cross-correlation. 
The template diffraction patterns can consist of both simulated diffraction patterns and experimental diffraction patterns originating from the SPED dataset itself. 
Machine-learning algorithms such as non-negative matrix factorisation can be used to select unique diffraction patterns to be used as templates. 

To benchmark PM, a well-studied SPED dataset from an Al-Cu-Li alloy that contains two precipitate phases is analysed and compared to a ground truth phase map. 
The obtained results demonstrate that PM can map the precipitates with high accuracy (${\gt}$98.5\%), using both types of template patterns. 
To further validate the workflow, a more challenging dataset from an Al-Mg-Si-Cu alloy, featuring similar and partly disordered precipitate structures, is also examined. 
The findings confirm that PM can classify these phases in agreement with atomically resolved STEM images. 
The main advantages of the PM method are that recorded patterns can be used as templates, that ill-matching patterns can be easily identified, and that the template bank can be readily expanded during data analysis. 
This enables both known and unfamiliar patterns encoded in SPED datasets to be identified and mapped without necessarily requiring detailed pre-knowledge on the probed crystal structures. 
PM can also be generalised and applied to other material systems. 
The workflow and datasets are available as open-source resources. 

+++


+++{"part": "epigraph"}
:::{warning} Pre-print
This article has not yet been peer-reviewed.  
Updated 2026 June 29
:::

+++

+++ {"part": "acknowledgements"} 

H. L. Korsvold is acknowledged for making the Al-Mg-Si-Cu TEM specimen. This work was supported by the Research Council of Norway (RCN) projects “In-SANE” (project number 301176) and iCSI (237922), and the TEM work was conducted at the NORTEM infrastructure (197405).

+++

+++ {"part": "competing interests"}

The authors declare that they have no known conflicts of interest.

+++

+++ {"part": "data availability"} 

The raw data are available via Zenodo [@Thronsen2022zenodo; @Sorhaug2024zenodo]. The workflow is available open source via GitHub [@PMgithub]. 

+++