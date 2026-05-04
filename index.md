---
title: 'Analysing scanning precession electron diffraction data using pattern matching: phase mapping of aluminium precipitates'
short_title: Pattern matching
numbering:
  heading_2: false
---

+++ {"part": "abstract"} 

Four-dimensional scanning transmission electron microscopy (4D-STEM) and its sub-categroy scanning precession electron diffraction (SPED), which includes beam precession, have emerged as promising techniques that enable mapping of the spatial distribution of nano-sized phases in multi-phase materials. 
These technqiues typically generate large amounts of data and require (semi-)automatic data analysis workflows. 
This work presents a SPED phase mapping methodology called pattern matching, with the aim of combining benefits of and addressing challenges associated with commonly used data analysis methods such as template matching and machine learning algorithms. 
The pattern matching workflow labels pre-processed diffraction patterns by comparing them to template diffraction patterns through normalised cross-correlation. 
The template diffraction patterns can consist of both simulated diffraction patterns or experimental diffraction patterns originating from the SPED dataset itself. 
The latter can be aided by machine-learning algorithms such as non-negative matrix factorisation. 

To benchmark pattern matching, a well-studied SPED dataset from an Al-Cu-Li alloy that contains two precipitate phases is analysed and compared to a ground truth phase map. 
The obtained results demonstrate that pattern matching can map the precipitates with high accuracy ($\sim$99\%), using both types of template patterns. 
To further validate the workflow, a more challenging dataset from an Al-Mg-Si-Cu alloy, featuring similar and partly disordered precipitate structures, is also examined. 
The findings confirm that pattern matching can classify these phases in agreement with atomically-resolved STEM images. 
The main advantages of the PM method are that recorded patterns can be used as templates, that ill-matching patterns can be easily identified, and that the template bank can be easily expanded during data analysis. 
This enables both known and unfamiliar patterns encoded in SPED datasets to be identified and mapped without necessarily requiring detailed pre-knowlege on the probed crystal structures. 
Pattern matching can also be generalised and applied to other material systems. 
The workflow and datasets are available as open-source resources. 

+++


+++{"part":"epigraph"}
:::{warning} Pre-print
This article has not yet been peer-reviewed.  
_Updated 2024 August 27_
:::

+++

+++ {"part": "acknowledgements"} 

Add your acknowledgments, if any, here.

+++

+++ {"part": "competing interests"} 
## Competing Interests

Add your competing interests, if any, here.
+++
