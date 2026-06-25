---
title: The test system
numbering:
  enumerator: 7.%s
---

For the Al-Mg-Si-Cu alloy test dataset, template patterns were found by NMF-based selection (C). 
Distinct template patterns were identified for the known phases $\beta''$, L and C. 
Other template patterns could not be assigned to one specific phase and were labelled according to three broader categories. 
The label 'in-plane' is used for precipitates oriented with their needle axis in the specimen plane, which makes them highly challenging to distinguish. 
'Si network' (short: 'Si nw.') refers to precipitates whose patterns display a near-hexagonal symmetry without displaying clear characteristics from one specific phase. 
Lastly, the category 'short-range order' corresponds to precipitate patterns that neither showed any clear Si-network or single-phase characteristics. 
[](#fig_6xxx_templates) presents one selected example template pattern per category. 
Patterns from the phases $\beta'$, $\beta$'$_\mathrm{Cu}$, Q' and Q were not observed in this dataset and are therefore not included here. 

:::{figure} ./figures/6xxx_selected_templates.png 
:name: fig_6xxx_templates
:width: 60%
Selected template patterns for the Al-Mg-Si-Cu alloy test dataset. The top row shows example template patterns corresponding to the distinct phases: $\beta''$, L, and C, while the bottom row shows example template patterns from the broader categories: 'Si network', 'short-range order' and 'in-plane'. 
:::

[](#fig_6xxx_A)(a) presents the phase map for the 6xxx dataset. It includes a magnified view of one region in the phase map where selected precipitates are assigned letter names, A-I. 
For these named precipitates, the SPED phase labelling is compared to manual labelling based on atomically resolved HAADF-STEM images, as shown in [](#fig_6xxx_A)(b). 
The left side of (b) displays a crop-out of the phase map alongside corresponding PED patterns and their respective best matching templates. 
The right side displays a manually labelled HAADF-STEM image next to its corresponding FFT magnitude images. 
Some unit cells and sub-units of known precipitate phases have been outlined on the HAADF-STEM images. 
The colour scheme refers to the sketches of known precipitate crystal structures shown in the rightmost panel. 
Overall, the classification based on PM and HAADF-STEM corresponds well, however, specific hybrid precipitates, namely Precipitate A-C, demonstrate particular challenges that are discussed separately in the following. 

- Precipitate A is labelled as a hybrid composed of the C and L phases.
These two phases are challenging to distinguish since their PED patterns appear highly similar due to their related atomic structures.
In fact, the L phase is composed of sub-units of both the C and Q' phases and is considered to be the disordered counterpart of the C phase [@Marioara2007; @Torsaeter2011], also referred to as 'disordered QP2' [@Ding2018]. 
By comparing the phase map to the HAADF-STEM image in [](#fig_6xxx_A)(b), it can be seen that individual L and C segments have been discriminated.
The left end of the precipitate is, however, classified as L in the SPED phase map and C in the HAADF-STEM image, likely since the end appears more disordered in diffraction than the internal part of the precipitate.

- Precipitate B is classified as a hybrid composed of the categories L, in-plane and Si network.
Both the L and the in-plane segments show strong correspondence between PM- and HAADF-STEM-based labelling.
The top part labelled Si network is, on the other hand, more complex. 
All the precipitates are built on an underlying common Si network, alternatively referred to as the QP lattice, which also holds for partly disordered precipitate regions [@Cayron1999; @Marioara2007; @Andersen2017]. 
The HAADF-STEM image reveals that the top region is partly disordered and contains one or two unit cells of both $\beta'$ and Q', in addition to Q'/C sub-units.
These Q' fragments, together with its growth direction along $\langle510\rangle_{\textrm{Al}}$, indicate that this region can be labelled as the precursor Q' phase (short: pre-Q'), which has also been referred to as 'S' [@Marioara2007] or 'disordered QP1' [@Ding2018] in previous work. 
The PED pattern from this region is dominated by spots originating from the Si network, and no single-phase characteristics can be picked out, hence the classification as Si network based on PM. 
This highlights that although the PM method can correctly label segments of different phases within hybrid precipitates, it cannot necessarily label sub-regions within partly disordered precipitate segments. 
In any case, the pre-Q' phase is indeed partly disordered, meaning that this segment is also manually classified as partly disordered based on the HAADF-STEM image, which underscores the correspondence between the methods. 

- Precipitate C is according to the phase map a hybrid between $\beta''$ and the Si network. 
The HAADF-STEM image shows connected $\beta''$ sub-units, known as $\beta''$-eyes, together with a slightly disordered part to the right. 
No perfect $\beta''$ unit cell can be found, but the characteristics of the connected $\beta''$-eyes are still picked up in the PED patterns. 
The lower right part is more disordered and has a less clear PED pattern, which results in this region instead being labelled Si network. 


:::::{tab-set} 

::::{tab-item} Precipitate A
:sync: tab1

:::{figure} ./figures/6xxx_1.png
:name: fig_6xxx_A
:width: 100%
Comparison of phase mapping based on SPED PM and HAADF-STEM for **Precipitate A** in the Al-Mg-Si-Cu alloy test dataset. (a) SPED PM-based phase map with a zoom-in where the selected precipitate is outlined. (b) Comparison of SPED PM-based phase labelling and HAADF-STEM-based manual labelling, which includes from left to right: a phase map crop-out, PED patterns from single-phase precipitate regions next to their corresponding best-matching templates, FFT magnitude images (corresponding to the regions marked by dashed rectangles in the HAADF-STEM image) and a manually labelled HAADF-STEM image. The rightmost illustration shows sketches of the relevant precipitate crystal structures, with unit cells and/or sub-units marked by coloured rectangles. The colours correspond to the phase label colours and marks on the HAADF-STEM image.
:::

::::

::::{tab-item} Precipitate B
:sync: tab2

:::{figure} ./figures/6xxx_2.png
:name: fig_6xxx_B
:width: 100%
Comparison of phase mapping based on SPED PM and HAADF-STEM for **Precipitate B** in the Al-Mg-Si-Cu alloy test dataset. (a) SPED PM-based phase map with a zoom-in where the selected precipitate is outlined. (b) Comparison of SPED PM-based phase labelling and HAADF-STEM-based manual labelling, which includes from left to right: a phase map crop-out, PED patterns from single-phase precipitate regions next to their corresponding best-matching templates, FFT magnitude images (corresponding to the regions marked by dashed rectangles in the HAADF-STEM image) and a manually labelled HAADF-STEM image. The rightmost illustration shows sketches of the relevant precipitate crystal structures, with unit cells and/or sub-units marked by coloured rectangles. The colours correspond to the phase label colours and marks on the HAADF-STEM image.
:::

::::

::::{tab-item} Precipitate C
:sync: tab3

:::{figure} ./figures/6xxx_3.png
:name: fig_6xxx_C
:width: 100%
Comparison of phase mapping based on SPED PM and HAADF-STEM for **Precipitate C** in the Al-Mg-Si-Cu alloy test dataset. (a) SPED PM-based phase map with a zoom-in where the selected precipitate is outlined. (b) Comparison of SPED PM-based phase labelling and HAADF-STEM-based manual labelling, which includes from left to right: a phase map crop-out, PED patterns from single-phase precipitate regions next to their corresponding best-matching templates, FFT magnitude images (corresponding to the regions marked by dashed rectangles in the HAADF-STEM image) and a manually labelled HAADF-STEM image. The rightmost illustration shows sketches of the relevant precipitate crystal structures, with unit cells and/or sub-units marked by coloured rectangles. The colours correspond to the phase label colours and marks on the HAADF-STEM image.
:::

::::

::::{tab-item} Precipitate D
:sync: tab4

:::{figure} ./figures/6xxx_4.png
:name: fig_6xxx_D
:width: 100%
Comparison of phase mapping based on SPED PM and HAADF-STEM for **Precipitate D** in the Al-Mg-Si-Cu alloy test dataset. (a) SPED PM-based phase map with a zoom-in where the selected precipitate is outlined. (b) Comparison of SPED PM-based phase labelling and HAADF-STEM-based manual labelling, which includes from left to right: a phase map crop-out, PED patterns from single-phase precipitate regions next to their corresponding best-matching templates, FFT magnitude images (corresponding to the regions marked by dashed rectangles in the HAADF-STEM image) and a manually labelled HAADF-STEM image. The rightmost illustration shows sketches of the relevant precipitate crystal structures, with unit cells and/or sub-units marked by coloured rectangles. The colours correspond to the phase label colours and marks on the HAADF-STEM image.
:::

::::

::::{tab-item} Precipitate E
:sync: tab5

:::{figure} ./figures/6xxx_5.png
:name: fig_6xxx_E
:width: 100%
Comparison of phase mapping based on SPED PM and HAADF-STEM for **Precipitate E** in the Al-Mg-Si-Cu alloy test dataset. (a) SPED PM-based phase map with a zoom-in where the selected precipitate is outlined. (b) Comparison of SPED PM-based phase labelling and HAADF-STEM-based manual labelling, which includes from left to right: a phase map crop-out, PED patterns from single-phase precipitate regions next to their corresponding best-matching templates, FFT magnitude images (corresponding to the regions marked by dashed rectangles in the HAADF-STEM image) and a manually labelled HAADF-STEM image. The rightmost illustration shows sketches of the relevant precipitate crystal structures, with unit cells and/or sub-units marked by coloured rectangles. The colours correspond to the phase label colours and marks on the HAADF-STEM image.
:::

::::

::::{tab-item} Precipitate F
:sync: tab6

:::{figure} ./figures/6xxx_6.png
:name: fig_6xxx_F
:width: 100%
Comparison of phase mapping based on SPED PM and HAADF-STEM for **Precipitate F** in the Al-Mg-Si-Cu alloy test dataset. (a) SPED PM-based phase map with a zoom-in where the selected precipitate is outlined. (b) Comparison of SPED PM-based phase labelling and HAADF-STEM-based manual labelling, which includes from left to right: a phase map crop-out, PED patterns from single-phase precipitate regions next to their corresponding best-matching templates, FFT magnitude images (corresponding to the regions marked by dashed rectangles in the HAADF-STEM image) and a manually labelled HAADF-STEM image. The rightmost illustration shows sketches of the relevant precipitate crystal structures, with unit cells and/or sub-units marked by coloured rectangles. The colours correspond to the phase label colours and marks on the HAADF-STEM image.
:::

::::

::::{tab-item} Precipitate G
:sync: tab7

:::{figure} ./figures/6xxx_7.png
:name: fig_6xxx_G
:width: 100%
Comparison of phase mapping based on SPED PM and HAADF-STEM for **Precipitate G** in the Al-Mg-Si-Cu alloy test dataset. (a) SPED PM-based phase map with a zoom-in where the selected precipitate is outlined. (b) Comparison of SPED PM-based phase labelling and HAADF-STEM-based manual labelling, which includes from left to right: a phase map crop-out, PED patterns from single-phase precipitate regions next to their corresponding best-matching templates, FFT magnitude images (corresponding to the regions marked by dashed rectangles in the HAADF-STEM image) and a manually labelled HAADF-STEM image. The rightmost illustration shows sketches of the relevant precipitate crystal structures, with unit cells and/or sub-units marked by coloured rectangles. The colours correspond to the phase label colours and marks on the HAADF-STEM image.
:::

::::

::::{tab-item} Precipitate H
:sync: tab8

:::{figure} ./figures/6xxx_8.png
:name: fig_6xxx_H
:width: 100%
Comparison of phase mapping based on SPED PM and HAADF-STEM for **Precipitate H** in the Al-Mg-Si-Cu alloy test dataset. (a) SPED PM-based phase map with a zoom-in where the selected precipitate is outlined. (b) Comparison of SPED PM-based phase labelling and HAADF-STEM-based manual labelling, which includes from left to right: a phase map crop-out, PED patterns from single-phase precipitate regions next to their corresponding best-matching templates, FFT magnitude images (corresponding to the regions marked by dashed rectangles in the HAADF-STEM image) and a manually labelled HAADF-STEM image. The rightmost illustration shows sketches of the relevant precipitate crystal structures, with unit cells and/or sub-units marked by coloured rectangles. The colours correspond to the phase label colours and marks on the HAADF-STEM image.
:::

::::

::::{tab-item} Precipitate I
:sync: tab9

:::{figure} ./figures/6xxx_9.png
:name: fig_6xxx_I
:width: 100%
Comparison of phase mapping based on SPED PM and HAADF-STEM for **Precipitate I** in the Al-Mg-Si-Cu alloy test dataset. (a) SPED PM-based phase map with a zoom-in where the selected precipitate is outlined. (b) Comparison of SPED PM-based phase labelling and HAADF-STEM-based manual labelling, which includes from left to right: a phase map crop-out, PED patterns from single-phase precipitate regions next to their corresponding best-matching templates, FFT magnitude images (corresponding to the regions marked by dashed rectangles in the HAADF-STEM image) and a manually labelled HAADF-STEM image. The rightmost illustration shows sketches of the relevant precipitate crystal structures, with unit cells and/or sub-units marked by coloured rectangles. The colours correspond to the phase label colours and marks on the HAADF-STEM image.
:::

::::

:::::

Overall, the phase labelling from PM corresponds well to that achieved by manual labelling of HAADF-STEM images. 
This substantiates that the PM workflow can be used for reliable phase mapping, even for hybrid precipitates that are composed of different single-phase segments. 
The method is capable of capturing small, yet significant, differences in the PED patterns of structurally similar phases, as exemplified by the differentiation between the L and C phases. 
Applying the PM method to the test system nonetheless highlights some limitations. 

Firstly, correct labelling and inclusion of template patterns is naturally a pre-requisite for correct phase mapping. 
For the Al-Mg-Si-Cu system this can be highly challenging since several similar templates need to be included to distinguish between the similar categories L, C and in-plane, and their potential overlap patterns. 
For the specific test dataset, a total of 36 templates were included in the template bank.  

Secondly, although the method can correctly label single-phase segments within hybrid precipitates, the PM method cannot label sub-regions within mixed-phase or partly disordered regions. 
For such regions, the underlying Si network dominates, and classification is done accordingly. 
The same can, however, be said for labelling based on HAADF-STEM images, where partly disordered regions should also be categorised as such. 
The border between hybrid and partly disordered precipitate regions can be difficult to define. 
In this regard, a unified precipitate phase classification scheme, which considers hybrid and partly disordered precipitate regions, would be invaluable and facilitate comparison across research groups. 
This goes far beyond the validation of the PM approach which is the goal of the current work. 