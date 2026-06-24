---
title: Alloys
numbering:
  enumerator: 1.%s
---

## The Al-Cu-Li alloy model system

The model SPED dataset was obatined from the Zenodo repository [@Thronsen2022zenodo]. 
Details on the Al-Cu-Li alloy composition, thermo-mechanical treatment, and TEM specimen preparation are provided in a previous study [@Thronsen2024]. 
The alloy contains two distinct and co-existing plate-shaped phases, namely $\theta$'-Al$_{2}$Cu and T$_{1}$-Al$_{2}$CuLi. 
Their space groups and lattice parameters are listed in [](#table1). 
Both have distinct orientation relationships with the host matrix. 
$\theta'$ grows along $\lbrace001\rbrace_{Al}$ planes, while T$_1$ grows along $\lbrace111\rbrace_{Al}$ planes [@Dwyer2011; @Liu2017]. 
Since the precipitates have distinct morphologies, they can readily be distinguished in bright- or dark-field images, and/or by their unique diffraction patterns when viewed along one of the main axes of the Al matrix [@Thronsen2024]. 
Based on the known orientation relationships, there are six unique diffraction patterns that can be found in this alloy when the Al matrix is oriented along $\langle001\rangle$ zone axis. 
These six unique patterns are found in the model SPED dataset and one example of each is displayed in Figure 1(a).

```{list-table} Crystal structure information for selected phases in Al-Cu-Li alloys. 
:name: table1
:header-rows: 1

* - Phase
  - Space group
  - Lattice parameters [Å]
  - Reference
* - Al
  - Fm$\bar{3}$m (225)
  - $a = 4.04$
  - $-$
* - $\theta$'-Al$_{2}$Cu
  - I$\bar{4}$m2 (119)
  - $a = 4.04$, $c = 5.80$
  - [@Silcock1956]
* - T$_{1}$-Al$_{2}$CuLi
  - P6/mmm (191)
  - $a = 4.95$, $b = 14.15$
  - [@Dwyer2011]
```

## The Al-Mg-Si-Cu alloy test system

The test SPED dataset was collected from an Al-Mg-Si-Cu alloy. 
Details on the chemical composition, thermo-mechanical processing, and TEM specimen preparation are provided elsewhere [@sorhaug2026]. 
Previous studies on this specific alloy show that the precipitate types that typically form are $\beta''$, L, C, $\beta'$, $\beta'_{Cu}$, Q', and Q [@Sunde2018; @Sunde2020]. 
They grow as needles, rods or laths along the main axes of the matrix and have specific orientation relationships with the host \hl{lattice} [@Saito2018; @Andersen2018]. 
Their similar shapes and sizes make them difficult to discern based on morphology. 
Some single precipitate particles are even composed of a mixture of multiple phases, referred to as hybrid precipitates. 
[](#table2) lists information on the crystal structures of the precipitate phases. 
The precipitates are built on a common lattice called the Si network, which exhibits a close to hexagonal symmetry along their long axes [@Marioara2007]. 
The L phase is partly disordered and consists of sub-units of the C and Q' phases, meaning that it does not have one specific crystal structure, yet, it is still built on the Si network [@Marioara2007]. 
Thus, there are several challenges to overcome to achieve accurate SPED phase mapping of this alloy, including both similar and unknown structures. 

```{list-table} Crystal structure information for the Si network and selected phases in Al-Mg-Si-Cu alloys. 
:header-rows: 1
:name: table2
* - Phase
  - Space group
  - Lattice parameter(s) [Å]
  - Reference
* - Si network
  - $-$
  - $a = 3.93$, $c = 4.05$
  - [@Cayron1999; @Marioara2007]
* - $\beta''$-Mg$_{5}$Al$_{2}$Si$_{4}$
  - C2/m (12)
  - $a = 15.16$, $c = 6.74$, $\beta = 105.3^\circ$
  - [@Andersen1998]
* - $\beta'$-Mg$_{9}$Si$_{5}$
  - $P6_{3}/m$ (176)
  - $a = 7.15$, $c = 12.15$ 
  - [@Vissers2007]
* - L 
  - $-$
  - $-$
  - [@Marioara2007]
* - C-Mg$_{4}$AlSi$_{3+x}$Cu$_{1-x}$
  - P$2_1$/m (11)
  - $a = 10.32$, $b = 4.05$, $c = 8.10$, $\beta = 100.9^\circ$
  - [@torsaeter2012; @Thronsen2020]
* - Q'-Al$_6$Mg$_6$Si$_7$Cu$_2$
  - P$6_3$ (174)
  - $a = 10.32$, $c = 4.05$
  - [@Torsaeter2008; @Wenner2017]
```