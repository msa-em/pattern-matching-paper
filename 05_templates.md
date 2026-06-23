---
title: Template patterns
numbering:
  enumerator: 4.%s
---

Three approaches of defining template patterns were used for the model dataset, as explained in the following. 
For the model system, it was observed that some precipitates frequently overlapped in projection. 
To accomodate for this, overlap patterns can be created by simply taking the average of each pair of dissimilar template patterns and rescaling the intensity. 
These overlap templates corresponding to two phases and/or orientations can be included in the template bank in the same manner as for the single crystal template patterns. 
This option is included in the advanced notebook only, to demonstrate the flexibility of the methodology, and overlap patterns are not included when comparing to the ground truth. 

For the test system, only the machine learning-based approach (C) was used to define template patterns since the unique diffraction patterns are not known in advance. 

## (A) Simulations
The five expected unique diffraction patterns were kinematically simulated using the open-source python library diffsims [@diffsims], based on the known crystal structures (Table S-II) and expected orientation relationships [@Thronsen2024]. 
The simulated Bragg spots were expanded to trapezoid disks, using the astropy python library [@astropy], to more closely resemble the Bragg disks in the recorded patterns. 
The simulated patterns were thereafter pre-processed in the same manner as the experimental patterns, as previously described. 
[](#fig_templates_A) illustrates the two main steps of simulation and pre-processing. 

:::{figure} ./figures/template_selections_A.png 
:name: fig_templates_A
Illustration of defining template patterns by approach (A) simulations, which includes kinematic simulations and pre-processing of the simulated patterns. The final template patterns are shown to the right. 
:::

## (B) Manual selection
The five template patterns were defined by averaging experimental diffraction patterns in the SPED dataset over five manually selected regions in real space. 
These regions were chosen based on manually recognising the known and distinct morphologies of each precipitate type in a virtual dark-field (VDF) image. 
This VDF image was created by applying a mask that blocked out the Al matrix reflections and then summing the intensity in each PED pattern. 
[](#fig_templates_B) presents the VADF image and the selected regions, together with the final templates.

:::{figure} ./figures/template_selections_B.png 
:name: fig_templates_B
Illustration of defining template patterns by approach (B) manual selection, which involves manually selecting five regions with unqiue patterns based on the morphologies in the VADF image. Each region was averaged to yield the final template patterns, which are shown to the right. 
:::

## (C) NMF-guided selection
NMF was performed on the pre-processed dataset using the scikit-learn implementation in hyperspy [@sklearn; @hyperspy]. 
A signal mask was applied to exclude Al reflections. 
In addition, a navigation mask was used to exclude regions with patterns that did not show any other reflections than those from Al, as determiend based on peak finding. 
The use of the masks, and especially the specific pre-processing done here, significantly reduced the random acess memory required to run the NMF algorithm. 

The result of NMF is known to be highly sensitive to the number of chosen output components [@Martineau2019; @Bergh2020; @Thronsen2024]. 
Therefore, singular value decomposition was computed prior to NMF, and the corresponding scree plot, which shows the fraction of total variance accounted for by each component, was studied to find a ballpark for an adequate number of components. 
Afterwards, NMF was run several times, both with a lower and a higher number of components than the value estimated based on the scree plot, and the results were inspected manually, before a final number of components was selected. 
[](#fig_nmf) presents an interactive plot where the NMF output for the model dataset is displayed for a user-selected number of components in the range of 1 to 20. 
In this work, 5 components were chosen for the model dataset since these adequately described the five main unique patterns. 
A lower number failed to include all unique patterns, while a higher number lead to signals belonging to the same unique pattern being split across various components. 
Although the number of components is important, searching for an optimal number of components is unnecessary within this workflow, as long as the number of components is high enough so that all the unique patterns are represented in separate components. 

:::{figure} #app:nmf_components
:name: fig_nmf
:placeholder: ./figures/nmf_placeholder.png
Interactive plot showing NMF results for the model dataset. Loadings and factors are shown for a user-selected number of components in the range of 1 to 20.
:::

The process of NMF-based template selection is illustated in [](#fig_templates_C). 
The components from NMF were manually categorised based on pre-knowledge of the unique precipitate patterns they belonged to. 
The categorised loading maps were thresholded, and for each thresholded loading, the 10\% most intense pixels were taken to define unique regions in real space. 
If signals from one category were split into several components, the respective loading maps could be summed prior to defining unique regions, or alternatively, unique regions could be summed to yield one unique region per unique pattern category. 
Within each unique region, patterns were extracted from the pre-processed dataset and averaged to yield the final template patterns. 
This means that the NMF results were not used as templated directly; NMF was rather used to guide the choice of unique regions, and the template patterns were extracted from the pre-processed SPED dataset itself. 
For this reason, neither the number of components chosen for NMF, nor the thresholding of loadings, need to be optimised within this workflow. 

:::{figure} ./figures/template_selections_C.png 
:name: fig_templates_C
Illustration of defining template patterns by approach (C) NMF-guided selection. The dataset is masked to reduce the data size, before NMF expresses the dataset as a combination of factors and loadings. The number of components for NMF is selected manually, and the resulting factors and loadings are categorised manually based on pre-knowledge. The loadings that correspond to unique categories are then each thresholded. The final template patterns is then obtained by averaging the pre-processed dataset over each thresholded loading map. 
:::