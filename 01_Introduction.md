---
title: Introduction
---

Four-dimensional scanning transmission electron microscopy (4D-STEM) is a powerful technique in material characterisation [@JAS2; @HYB_4metals; @func_mat]. 
It involves scanning an electron beam across a specimen area of interest, while recording two-dimensional electron diffraction patterns at each probe position [@ophus_4dstem]. 
The 4D-STEM technique scanning precession electron diffraction (SPED), uses double conical beam-rocking - also known as beam precession - before and after the specimen [@VINCENT1994271]. 
This is followed by probe 'de-rocking' and integration of diffraction patterns into precession electron diffraction (PED) patterns [@VINCENT1994271; @GJONNES19971; @Own_we5013]. 
The integration of diffraction patterns over a collection of diffraction conditions can make the recorded PED patterns less sensitive to zone-axis mistilts, improve the intensity uniformity in the Bragg disks, and provide patterns that more closely resemble kinematical predictions [@WHITE2010763; @PED_lessSensitive2_structureFactor; @PED_demonstration_structureRefinement]. 
These features can simplify the analysis of the data, and the interpretation of the results [@Own_we5013; @PED_demonstration_structureRefinement; @THRONSEN2024113861]. 
However, as SPED can provide large amounts of data, semi-automatic analysis methods to efficiently manage and extract meaningful insights is crucial. 

SPED has become an important technique for material characterisation [@NORDAHL2025103761; @tb_segmentation; @unsup_on_SPED; @nmf_and_clustering_SR], especially for mapping phases at the nano-scale [@THRONSEN2024113861; @unsup_on_SPED, @SUNDE2018458; @JAS3]. 
Several phase mapping workflows can be readily applied on SPED datasets, each with their own advantages and disadvantages. 
Template matching can for example identify phases and determine their local crystal orientations, by comparing simulated template patterns to the recorded diffraction patterns [@rauch2008automatic; RauchPortilloNicolopoulosBultreysRouvimovMoeck;  @pyxemorientationmapping2022; @Folastre2024]. 
However, to achieve reliable results, data pre-processing, precise fine-tuning of simulation parameters, and pre-defining candidate phases are a prerequisite. 
Consequently, when prior knowledge about the material is limited, phase mapping can become challenging. 

Unsupervised machine learning algorithms are other good SPED data analysis options, as they can be less dependent on detailed prior knowledge about the material system at hand. %Cluster analysis like k-means for example, can look for a user-defined number of groups or clusters within a dataset, and will group data points according to their nearest cluster centre [@kmeans++; nmf_and_clustering_SR; Yoo2024]. %This means that diffraction patterns belonging to the same cluster centre, are likely very similar to each other. An alternative method is to decompose the signal
Signal decomposition techniques like non-negative matrix factorisation (NMF), can for example reduce a dataset's dimensionality into a pre-defined number of components [@nmf]. 
NMF will assume the data matrix $\textbf{X}$ to be non-negative, and will approximate it as the matrix product $\textbf{WH}$, where both factors contain non-negative elements \cite{nmf}. 
Hence, $\textbf{X}$ becomes expressed as a linear combination of non-negative patterns $\textbf{W}$ (known as factors) that resemble diffraction patterns, and positive real-space coefficients $\textbf{H}$ (known as loadings) that describe the patterns' weights and spatial distribution [@nmf_and_clustering_SR; @unsup_on_SPED, @tb_segmentation]. 
NMF can thus be useful on datasets that contain repeating patterns. 
One example is aluminium alloys that contain precipitates with orientation relationships with the host lattice [@THRONSEN2024113861; @Sunde_insitu, @EF]. 
However, since NMF can not directly generate phase maps, the components can be less intuitive and straight-forward to interpret [@THRONSEN2024113861]. 

Thronsen et al. [@THRONSEN2024113861] recently evaluated four phase mapping methods on an Al-Cu-Li alloy model SPED dataset. 
Among the investigated methods were template matching and NMF.
The model system contained two different phases with unique morphologies and orientation relationships with the Al lattice. 
When the phases were viewed along one of Al's main axes, the phases produced five distinct diffraction patterns. 
By combining these features, the authors were allowed to establish a ground truth phase map for assessing the accuracy of the investigated phase mapping methods. 
According to their findings, all four methods achieved an accuracy higher than 98\% [@THRONSEN2024113861]. 
This demonstrates that the phase mapping methods are capable of delivering consistent, and reliable phase maps.
However, their performance are anticipated to decline as secondary phases become increasingly disordered, and/or structurally similar to one another. 
This emphasizes a need for more robust SPED data analysis methods. 

To address the challenges outlined above, this work presents a novel phase mapping method called pattern matching (PM). %To the author's knowledge, few attempts have been made on PM TEM diffraction data. Zuo et al. and Kim et al. investigated convergent beam electron diffraction (CBED) patterns, where they did a geometric feature enhancement prior to pattern matching \cite{8157248, pm_CBED2}. Wu and Zaefferer showed that PM is possible on spot electron diffraction patterns. However, their matching procedure encompassed matching spectra from azimuth integration around the center spot \cite{WU20091317}. %Fundenberger also indexed CBED patterns employing the information available from lines in respective patterns \cite{FUNDENBERGER2003127} Regardless, the studies indirectly suggest that geometric enhancements and/or reduction of non-systematic scattering can be important when dictionary indexing precipitate ED patterns. (See also Ref. \cite{ahe}.) In particular, since high symmetry ZAs are more prone to dynamic effects than less symmetric ZAs \cite{humphreys}, providing diffraction spots with little intensity variations can be important for reliable PM schemes. %Trimby et al. performed matching on transmission kikuchi diffraction patterns \cite{TRIMBY2024113940}. 
Similar to template matching, PM can map phases and their orientations by comparing recorded diffraction patterns to a bank/library of template patterns that represent candidate phases at known orientations. %However, there are at least two characteristics that separate the two: (1) the normalised correlation score is often used in template matching to assess the similarity between experimental patterns and template patterns. PM on the other hand, exploits the inherent property of the normalised cross-correlation score\footnote{Also referred to as the Pearson’s correlation coefficient.} (NCC) to identify bad matches \cite{rauch2008automatic, RauchPortilloNicolopoulosBultreysRouvimovMoeck,  pyxemorientationmapping2022, Folastre2024, rafael_book}. %The match index in PM can therefore be more sensitive to differences between the experimental patterns and the templates, like small disorientations and/or the presence (or absence) of reflections in one of the patterns \cite{pyxemorientationmapping2022}. %Indeed, this can be very useful when e.g. similar patterns from dissimilar crystal structures are examined, but it also implies that the match score during PM can be more sensitive to dynamical effects and noise embedded in the data. (2) The experimental and template patterns are mapped with a window-normalised cross-correlation with a binary disk prior to the matching, to effectively dampen noise and intensity variations in Bragg disks. %This trait can benefit PM, as it can enable confident matching while penalizing patterns with extra and/or missing reflections \cite{pyxemorientationmapping2022}. 
However, in contrast to template matching, PM permits simulated and experimental patterns to serve as templates. %This flexibility enables patterns from the dataset to be included in the template library prior to, and during the phase mapping process. 
This unique attribute can facilitate the identification, and the spatial mapping of crystals with previously unknown structures. 

To benchmark the proposed PM methodology against more established phase mapping methods, this study will use PM to map the precipitates in the Al-Cu-Li alloy model SPED dataset analysed by Thronsen et al. [@THRONSEN2024113861]. 
This will be done by separately using kinematically simulated, and experimental patterns extracted from the dataset as templates. %The experimental patterns will be averaged from manually selected regions, and from the highest real-space coefficients from NMF. 
The PM accuracy will then be assessed by comparing the phase maps to the existing ground truth phase map [@THRONSEN2024113861]. 
To further validate the proposed method, PM will also be used to map the more challenging precipitate structures in an Al-Mg-Si-Cu alloy. 
The selected alloy contains both partly disordered precipitates, and structurally similar phases [@SUNDE2020110087; @JAS3]. 
The results from PM will be assessed by comparing the mapped precipitates to atomically resolved STEM images of the same precipitates. 
This study aims to establish a simple and user-friendly approach for mapping known phases and unfamiliar crystal structures encoded in SPED datasets.
