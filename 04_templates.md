---
title: Defining templates
---

Three approaches of defining template patterns were used for the model dataset, as presented schematically in Figure [](#fig_templates) and explained in the following. 
For the model system, it was observed that some precipitates frequently overlapped in projection. 
To accomodate for this, overlap patterns can be created by simply taking the average of each pair of dissimilar template patterns and rescaling the intensity. 
These overlap templates corresponding to two phases and/or orientations can be included in the template bank in the same manner as for the single crystal template patterns. 
This option is included in the advanced notebook only, to demonstrate the flexibility of the methodology, and overlap patterns are not included when comparing to the ground truth. 

For the test system, only the machine learning-based approach (C) was used to define template patterns since the unique diffraction patterns are not known in advance. 

:::{figure} ./figures/template_selections.png 
:name: fig_templates 
Schematic illustration of the three approaches used to define template patterns: (a) simulate patterns, (b) manually select regions with unqiue patterns, or (c) use NMF to find regions with unqiue patterns. 
:::

## (A) Simulations: 
The five expected unique diffraction patterns were kinematically simulated using the open-source python library diffsims [@diffsims], based on the known crystal structures (Table S-II) and expected orientation relationships [@Thronsen2024]. 
The simulated Bragg spots were expanded to trapezoid disks, using the astropy python library [@astropy], to more closely resemble the Bragg disks in the recorded patterns. 
The simulated patterns were thereafter pre-processed in the same manner as the experimental patterns, as previously described.

## (B) Manual selection: 
The five template patterns were defined by averaging experimental diffraction patterns in the SPED dataset over five manually selected regions in real space. 
These regions were chosen based on manually recognising the known and distinct morphologies of each precipitate type in a virtual dark-field (VDF) image. 
This VDF image was created by applying a mask that blocked out the Al matrix reflections and then summing the intensity in each PED pattern. 

## (C) NMF-guided selection:
NMF was performed on the pre-processed dataset using the scikit-learn implementation in hyperspy [@sklearn; @hyperspy]. 
A signal mask was applied to exclude Al reflections. 
The use of the signal mask, and especially the specific pre-processing done here, significantly reduced the random acess memory required to run the NMF algorithm. 
The result of NMF is known to be highly sensitive to the number of chosen output components [@Martineau2019; @Bergh2020; @Thronsen2024]. 
Therefore, singular value decomposition was computed prior to NMF, and the corresponding scree plot, which shows the fraction of total variance accounted for by each component, was studied to find a ballpark for an adequate number of components. 
Afterwards, NMF was run several times, both with a lower and a higher number of components than the value estimated based on the scree plot, and the results were inspected manually, before a final number of components was selected. 
The resulting components were manually categorised based on the unique precipitate patterns they belonged to. 
The NMF loading maps were thresholded, and for each loading map, the 10\% highest values were taken to define unique regions in real space. 
Within each unique region, patterns were extracted from the pre-processed dataset and summed to give the final template patterns. 
This means that the NMF results were not used as templated directly; NMF was rather used to guide the choice of unique regions, and the template patterns were extracted from the pre-processed SPED dataset itself. 
