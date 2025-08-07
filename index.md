---
title: 'Analysing scanning precession electron diffraction data using pattern matching: phase mapping of aluminium precipitates'
short_title: Pattern matching
numbering:
  heading_2: false
---

+++ {"part": "abstract"} 

Four-dimensional scanning transmission electron microscopy (4D-STEM) involves scanning an electron beam across a specimen area of interest, while recording diffraction patterns at each probe position. 
The 4D-STEM technique scanning precession electron diffraction (SPED), includes beam precession, and integration of diffraction patterns over a collection of diffraction conditions to mitigate dynamical effects. %This provides an eminent approach to map the spatial distribution of nano-sized phases. 
This can effectively simplify the following data analysis, and interpretations of the results.
However, as SPED can provide large amounts of data during each session, semi-automatic SPED data analysis approaches become crucial. 
Common analysis workflows include for example template matching where recorded diffraction patterns are compared with simulated template patterns, or machine learning algorithms that can reduce the data dimensionality. 
However, simulation of template patterns is limited to pre-defined crystal structures, and machine learning algorithms can be prone to artefacts and lack sensitivity. 
To address these challenges, this work presents an improved template matching methodology called pattern matching, that allows simulated diffraction patterns and/or patterns extracted from the SPED dataset, to be used as template patterns.

To benchmark pattern matching, a well-studied SPED dataset from an Al-Cu-Li alloy that contains two precipitate phases is analysed and compared to a ground truth phase map. 
The obtained results demonstrate that pattern matching can map the precipitates with high accuracy ($\sim$99\%), regardless of the used template type. 
To further validate the workflow, a more challenging dataset from an Al-Mg-Si-Cu alloy, featuring similar and partly disordered precipitate structures, is also examined. 
The findings confirm that pattern matching can map these precipitates in agreement with atomically resolved STEM images. 
The key advantage of the proposed method is that the template library allows experimental diffraction patterns to be used as template patterns. 
This enables known and previously unfamiliar crystal structures encoded in SPED datasets to be identified and mapped.
Pattern matching can also be generalised, and applied to other material systems. 
The workflow and datasets are made available as open-source resources. 


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
