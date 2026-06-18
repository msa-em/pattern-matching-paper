---
title: Introduction
---

Four-dimensional scanning transmission electron microscopy (4D-STEM) involves raster scanning an electron beam while recording two-dimensional electron diffraction patterns at each probe position [@Ophus2019]. 
By categorising each diffraction pattern based on which crystal structure or phase it corresponds to, phase maps can be obtained. 
These maps reveal the morphology, spatial distribution, and proportion of various phases with the high spatial resolution offered by scanning transmission electron microscopy (STEM). 
Such information is often crucial to explain the properties of multi-phase materials, for instance metal alloys that contain embedded nanoscale precipitates. 
The 4D-STEM sub-category of scanning precession electron diffraction (SPED) is particularly well suited for phase mapping. 

SPED combines raster scanning with beam precession. 
The incident beam is tilted off the optical axis by the precession angle, $\phi$, and rocked around to trace a circle above the specimen. 
Below the specimen, the beam is tilted back and 'de-rocked' to achieve double conical beam rocking [@Vincent1994]. 
The intensities in a precession electron diffraction (PED) have thus been integrated over a collection of diffraction conditions [@Vincent1994; @Gjonnes1997]. 
This typically leads to excitation of more Bragg spots, makes the recorded PED patterns less sensitive to zone-axis mistilts, improves intensity uniformity inside Bragg disks, and provides intensities that more closely resemble kinematical predictions [@Own2006b; @White2010; @Sinkler2010]. 
These features usually simplify data analysis and interpretation. 
As typical SPED datasets contain thousands to hundreds of thousands diffraction patterns, (semi-)automatic data processing and classification algorithms are crucial.  

Several phase mapping workflows have been developed and applied to SPED data. 
Template matching is a much-used route which relies on comparing each recorded diffraction pattern to a list of simulated template patterns to find the best matching template, typically via cross correlation [@Rauch2010; @Cautaerts2022; @Ophus2022]. 
Reliable results, however, require pre-defined candidate phases and usually also data pre-processing and fine-tuning of simulation parameters. 
If the candidate crystal structures are known, other indexing methods can also be used, such as 'vector matching' that is based on measuring the Bragg spot positions [@Thronsen2024]. 
Supervised machine learning approaches like neural networks can also readily produce phase maps, but rely on correctly labelled training data for accurate classification [@Thronsen2024]. 

Unsupervised machine learning algorithms, on the other hand, do not require prior knowledge and comprise decomposition algroithms like non-negative matrix factorisation (NMF) [@Lee1999]. 
NMF approximates a SPED dataset as a linear combination of reciprocal-space patterns (referred to as factors) that are associated with real-space weighting maps (referred to as loadings) [@Martineau2019; @Bergh2020]. 
NMF offers advatanges for datasets that contain a limited number of unique but reccurring features, since it can reduce the dimensionality and increase the signal-to-noise ratio. 
One such case where NMF-based analysis works well is SPED data from aluminium alloys that contain nanoscale precipitates with specific orientation relationships with the host lattice [@Sunde2018; @Christiansen2019]. 
Further post-processing and classification are, however, required to obtain phase maps based on the output from NMF. 

A recent study compares four of the beforementioned phase mapping approches for the case of an Al-Cu-Li model alloy on the basis of a ground truth phase map [@Thronsen2024]. 
The accuray is higher than 98\% for all the evaluated methods, but each has both advantages and shortcomings. 
All of them can be challenging to use if the studied crystal structures are unknown or unsolved, partly disordered and/or highly similar to each other. 
This is for instance the case for some important and widely used structural aluminium alloys such as Al-Mg-Si-Cu alloys, for which NMF-based SPED phase mapping has been employed previously [@Sunde2018; @Sunde2020]. 
This work therefore sets out to develop an approach that can tackle these challenges and is relatively easy to %understand,
use and further expand. 

A modified phase mapping framework is presented that is referred to as pattern matching (PM). 
PM is similar to template matching as it compares each experimental diffraction pattern to a library of templates, but it offers more flexibility and allows mapping of unknwon crystal sturctures by offering the option of using representative experimental diffraction patterns as templates. 
The approach also implements an efficient pre-processing strategy that highly benefits NMF-based analysis. 
This study demonstrates and benchmarks the PM methodology on the SPED dataset from the model Al-Cu-Li alloy that has previously been released open-source together with a corresponding ground truth phase map [@Thronsen2024]. 
The workflow is further validated by applying it to the more challenging precipitate structures in an Al-Mg-Si-Cu alloy that contains both partly disordered and structurally similar precipitates [@Sunde2020; @sorhaug2026]. 
Overall, this study aims to establish a user-friendly and robust framework for SPED phase mapping that handles both known and unknown crystal structures. 
The workflow is released open-source, and it can be further modified and readily applied to other material systems, for instance it has already been applied to Al-Mg-Si-Cu alloys in a related publication [@sorhaug2026] and to Al-Zn-Mg-Cu alloys [@Ryggetangen2025]. 