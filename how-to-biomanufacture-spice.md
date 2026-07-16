---
layout: default
title: How to biomanufacture spice
---

# How to biomanufacture spice

or 

## Modeling De Novo Biosynthesis of Capsaicin in _Sacchromyces cerevisiase_

Author's Note: This project was written for John Dueber's Synthetic Biology class at UC Berkeley. 

### Background and Rationale

Capsaicin is an alkaloid that is only found in the genus Capsicum and is responsible for
the pungency of chili peppers. It is synthesized by capsaicin synthase (CS) that acts as an
acyltransferase, condensing 8-methyl-6-nonenoyl-CoA with vanillylamine (Figure 1). In addition
to being used as a food additive to add spice, it has clinical and practical uses, such as being the
active ingredient in pepper spray (Reilly et al., 2001). It also has been found to relieve pain and
decrease inflammation in osteoarthritis and rheumatoid arthritis patients (Deal et al., 1991).
Additional research suggests that capsaicin has anti-cancer, anti-obesity, and antimicrobial
activity, although the exact mechanisms of action in these circumstances remains to be
discovered (Swetnisha et al., 2017).

Because of the multiple applications of capsaicin, finding its market size based on sales is
difficult; however, its imports into the U.S. can be tracked. In 2019, a total of 20,267 kg of
capsaicin powder was imported into the U.S. (Import of Capsaicin in USA). Sigma-Aldrich sells
>95% pure capsaicin for $718/g (Capsaicin). Thus, the US market size for pure capsaicin is
around $15 million. Additionally, in 2018, 80,897 kg of capsaicin in varying concentrations
within heat patches, pain relief cream, and food products was imported into the U.S. (Import of
Capsaicin in USA). Therefore, there is clear demand for capsaicin in a variety of markets.

The current method for producing capsaicin is to harvest it from the fruit of chili peppers.
This process has many rate-limiting steps and the need for a biotechnological solution is
imminent. Preliminary research into this has been done by scientists at Conagen Inc., which
holds a patent to produce capsaicin via a biosynthetic pathway in Escheria Coli (Chen et al.,
2016). However, they had to continuously supply 8-methyl-6-nonenoyl-CoA as a substrate, so
there is no one-cell autonomous system to produce capsaicin.

### Technical Details

The metabolic pathway will reside within the fungal yeast Saccharomyces cerevisiae for
multiple reasons, including facilitative native enzymes and the extensive characterization of its
genome. Its main advantage is the fact that it can produce 8-methyl-6-nonenoyl-CoA through the
valine pathway with only one inserted gene. Yeast makes isobutyryl-CoA from valine with its
own branched-chain α-ketoacid dehydrogenase (Dickinson et al., 1998). This is quite an
advantage over other microorganisms that have to rely on engineered metabolic pathways to
make isobutyryl-CoA (Chen et al., 2019). As shown in Figure 2, this can then enter the fatty acid
synthase cycle, along with three molecules of malonyl-CoA, in order to elongate the chain. The
enzyme responsible for catalyzing this reaction will be an inserted KASIII, a β-ketoacyl synthase
III that is native to Capsicum (Thiele et al., 2008; Stewart et al., 2005; Aza-González et al.,
2011). This interaction simply requires the malonyl-CoA and one molecule of Mg2+ per cycle of
fatty acid synthesis (EC 2.3.1.180). A native yeast thioesterase encoded by the gene TES1 will
then take the resulting fatty acid chain along with water and create 8-methyl-6-nonenoic acid
(P41903; EC 3.1.2.23). This will then be processed by a desaturase native to yeast encoded by
OLE1, requiring one molecule of NADH, O2, and a free proton (Martin et al., 2002). Removing
two hydrogens from the short chain fatty acid, it creates a double bond within the chain. Finally,
a native acyl-CoA synthase (Fat1) requiring one unit of ATP will condense the reagent into the
final product of the valine pathway, 8-methyl-6-nonenoyl-CoA (Black et al., 2016).

Separately, the phenylpropanoid pathway that results in the production of vanillylamine
requires more metabolic engineering, but it has already been created and substantiated by a
Hansen et al. As described in Figure 3, 3-dehydroshikimate dehydratase (3DSD) is extracted
from the filamentous fungi Podospora pauciseta, and this catalyzes the conversion of
3-dehydroshikimic acid and Mn2+ to protocatechuic acid (EC 4.2.1.118). In order to prevent
buildup of an undesired product, a highly substrate-specific Homo sapien O-methyl transferase
(COMT) is utilized to create vanillic acid, requiring one molecule of Mn2+ (P21964). Next, an
aromatic carboxylic acid reductase (ACAR) optimized for yeast codon usage reduces the
compound with the help of ATP (He et al., 2004). To increase ACAR’s functionality in S.
cerevisiase, a phosphopantetheine transferase from C. glutamicum, PPTcg-1, is added. This is
necessary because ACAR requires phosphopantetheinylation for functionality
(Venkitasubramanian et al., 2006). PPTcg-1 necessitates Mg2+ as a cofactor (Copp et al., 2006). Finally, to add on to the Hansen et al. metabolic pathway that produces vanillin, a vanillin
aminotransferase (VAMT) can be implemented into yeast to make vanillylamine with pyruvate
as an amine acceptor (EC 2.6.1.119; Weber et al., 2014). In addition to this final reaction
producing the desired product, it also keeps the concentration of vanillin, a toxic chemical to
cells, relatively low (Hansen et al., 2009).

Capsaicin synthase will be introduced into the cell in order to condense vanillylamine and
8-methyl-6-nonenoyl-CoA into capsaicin. Transduction of CS into S. cerevisiase necessitates
codon optimization for yeast. Its maximum activity occurs at pH 8 and 37°C, and the Km value of
vanillylamine and 8-methyl-6-nonenoyl-CoA is 6.6 ± 0.5 μM and 8.2 ± 0.6 μM, respectively
(Prasad et al., 2006).

The previously researched phenylpropanoid pathway allowed for production of 486
grams of vanillin per gram of glucose, or 45 mg/L (Hansen et al., 2009). The conversion rate of
VAMT was almost 100% when using pyruvate as a substrate (Weber et al., 2014). It is difficult to
estimate the expected production of 8-methyl-6-nonenoyl-CoA because the only scientists to
metabolically engineer it into microorganisms proved its presence, not its amount (Chen et al.,
2019). However, similar short branched fatty acids have been produced at a level of 12.4 mg/L
(Yu et al., 2015). Additionally, preliminary data suggests the CS enzyme has a conversion rate of
20% (Ogawa et al., 2015). Thus, a conservative estimate for the titer amount would be within the
range of 1E+0 to 1E+1 mg/L. This would then necessitate a 1E+3 size reactor in order to
produce a significant amount of capsaicin. With that being said, capsaicin will also most likely
be toxic to yeast cells at high concentrations, so the final reactor size will have to balance
toxicity and profitable titer.

### Potential Pitfalls

The KAS and VMAT genes are the only cassettes used in this pathway that have not been
tested in yeast before, and the KASIII enzyme is only found in Capsicum, so there might be
problem with integration into S. cerevisiae. Furthermore, the rate-limiting step of the valine
pathway will be the concentration of isobutyryl-CoA and malonyl-CoA, since their production is
through native cellular processes. Researchers have developed metabolic pathways within yeast
to increase the production of malonyl-CoA, but adding additional systems might cause too much
stress on the cell (Hu et al., 2019). This is of further concern because it has been proven that the valine pathway is more crucial to capsaicin biosynthesis than the phenylpropanoid pathway
(Prasad et al., 2006). An additional problem of this system is its sheer complexity. Inserting six
genes into any cell will cause stress, and even though the cofactors and ATP requirement of these
enzymes is minimal, cellular growth will likely decrease. Finally, capsaicin can be toxic at high
concentrations, so its effect on S. cerevisiase will have to be measured and accounted for.

### Figures

Note: All figures were created using PubChemSketcher.


![Alt text](/images/CapsaicinFig1)

_Figure 1: Synthesis of capsaicin via capsaicin synthase condensation of 8-methyl 6-nonenoyl-CoA and vanillylamine._

![Alt text](/images/CapsaicinFig2)

_Figure 2: Proposed biosynthetic pathway for the production of 8-methyl-6-nonenoyl-CoA in S. cerevisiae from the valine pathway. As labeled in the figure, 1: Isobutyryl CoA; 2: 8-methyl-6-nonenoic acid; 3: 8-methylnonanoic acid; 4: 8-methyl-6-nonenoyl-CoA. Adapted from Stewart et al._

![Alt text](/images/CapsaicinFig3)

_Fig 3. Proposed model for biosynthetic pathway of vanillylamine production in S. cerevisiase. As labeled in the figure, 1: Dehydroshikimic acid; 2: Protocatechuic acid; 3: Vanillic acid; 4: Vanillin; 5: Vanillylamine. Adapted from Hansen et al._

### Works Cited
1. Aza-González, C., Núñez-Palenius, H. G., & Ochoa-Alejo, N. (2010). Molecular biology of
capsaicinoid biosynthesis in chili pepper (Capsicum spp.). Plant Cell Reports, 30(5),
695-706. https://doi.org/10.1007/s00299-010-0968-8
2. Black, P. N., & DiRusso, C. C. (2007). Yeast acyl-CoA synthetases at the crossroads of fatty acid
metabolism and regulation. Biochimica Et Biophysica Acta (BBA) - Molecular and Cell
Biology of Lipids, 1771(3), 286-298. https://doi.org/10.1016/j.bbalip.2006.05.003
3. Capsaicin. (n.d.). Sigma-Aldrich. Retrieved November 11, 2020, from
https://www.sigmaaldrich.com/catalog/product/sigma/m2028?lang=en&region=US&cm_
sp=Insite-_-caSrpResults_srpRecs_srpModel_capsaicin-_-srpRecs3-1
4. Chen, H., & Lu, X. (2019). Method for the Microbial Production of 8-Methyl Nonanioc Acid
(U.S. Patent No. US20190390231A1). U.S. Patent and Trademark Office.
5. Chen, H., Wang, H., & Yu, O. (2016). Methods for the use of Capsaicin Synthase for the
Microbial Production of Capsaicinoids (U.S. Patent No. US20160340701A1). U.S.
Patent and Trademark Office.
6. Copp, J. N., & Neilan, B. A. (2006). The Phosphopantetheinyl Transferase Superfamily:
Phylogenetic Analysis and Functional Implications in Cyanobacteria. Applied and
Environmental Microbiology, 72(4), 2298-2305.
https://doi.org/10.1128/AEM.72.4.2298-2305.2006
7. Deal CL, Schnitzer TJ, Lipstein E, Seibold JR, Stevens RM, Levy MD, Albert D, Renold F.
Treatment of arthritis with topical capsaicin: a double-blind trial. Clin Ther. 1991
May-Jun;13(3):383-95. PMID: 1954640.
8. Dickinson, J. R., Harrison, S. J., & Hewlins, M. J. E. (1998). An Investigation of the Metabolism
of Valine to Isobutyl Alcohol in Saccharomyces cerevisiae. Journal of Biological
Chemistry, 273(40), 25751-25756. https://doi.org/10.1074/jbc.273.40.25751
9. EC 4.2.1.118. (n.d.). Expasy. Retrieved November 11, 2020, from
https://enzyme.expasy.org/EC/4.2.1.118
10. EC 3.1.2.23. (n.d.). BRENDA. Retrieved November 11, 2020, from
https://www.brenda-enzymes.org/enzyme.php?ecno=3.1.2.23#REF.
11. EC 2.6.1.119 -- vanillin aminotransferase. (n.d.). MetaCyc. Retrieved November 11, 2020, from
https://biocyc.org/META/NEW-IMAGE?type=EC-NUMBER&object=EC-2.6.1.119
12. EC 2.3.1.180. (n.d.). BRENDA. Retrieved November 11, 2020, from
https://www.brenda-enzymes.org/enzyme.php?ecno=2.3.1.180#METALS%20and%20IO
NS
13. Gallage, N., & Møller, B. (2015). Vanillin–Bioconversion and Bioengineering of the Most
Popular Plant Flavor and Its De Novo Biosynthesis in the Vanilla Orchid. Molecular
Plant, 8(1), 40-57. http://dx.doi.org/10.1016/j.molp.2014.11.008
14. Hansen, E. H., Møller, B. L., Kock, G. R., Bünner, C. M., Kristensen, C., Jensen, O. R., Okkels,
F. T., Olsen, C. E., Motawia, M. S., & Hansen, J. (2009). De Novo Biosynthesis of
Vanillin in Fission Yeast (Schizosaccharomyces pombe) and Baker's Yeast
(Saccharomyces cerevisiae). Applied and Environmental Microbiology, 75(9),
2765-2774. https://doi.org/10.1128/AEM.02681-08
15. He, A., Li, T., Daniels, L., Fotheringham, I., & Rosazza, J. P. N. (2004). Nocardia sp. Carboxylic
Acid Reductase: Cloning, Expression, and Characterization of a New Aldehyde
Oxidoreductase Family. Applied and Environmental Microbiology, 70(3), 1874-1881.
https://doi.org/10.1128/AEM.70.3.1874-1881.2004
16. Hu, Y., Zhu, Z., Nielsen, J., & Siewers, V. (2019). Engineering Saccharomyces cerevisiae cells
for production of fatty acid-derived biofuels and chemicals. Open Biology, 9(5), 190049.
https://doi.org/10.1098/rsob.190049
17. Import of Capsaicin in USA. (n.d.). Zauba. Retrieved November 11, 2020, from
https://www.zauba.com/USA-import-capsaicin-data.html
18. Martin, C. E., Oh, C.-S., Kandasamy, P., Chellapa, R., & Vemula, M. (2002). Yeast desaturases.
Biochemical Society Transactions, 30(6), 1080-1082. https://doi.org/10.1042/bst0301080
Ogawa, K., Murota, K., Shimura, H., Furuya, M., Togawa, Y., Matsumura, T., & Masuta, C.
(2015). Evidence of capsaicin synthase activity of the Pun1-encoded protein and its role
as a determinant of capsaicinoid accumulation in pepper. BMC Plant Biology, 15(1).
https://doi.org/10.1186/s12870-015-0476-7
19. P21964 (COMT_HUMAN). (n.d.). UniProt. Retrieved November 11, 2020, from
https://www.uniprot.org/uniprot/P21964
20. P41903 (PTE1_YEAST). (n.d.). UniProt. Retrieved November 11, 2020, from
https://www.uniprot.org/uniprot/P41903
21. Prasad, B. C. N., Gururaj, H. B., Kumar, V., Giridhar, P., & Ravishankar, G. A. (2006). Valine
Pathway Is More Crucial than Phenyl Propanoid Pathway in Regulating Capsaicin
Biosynthesis inCapsicum frutescensMill. Journal of Agricultural and Food Chemistry,
54(18), 6660-6666. https://doi.org/10.1021/jf061040a
22. Prasad, B. C. N., Kumar, V., Gururaj, H. B., Parimalan, R., Giridhar, P., & Ravishankar, G. A.
(2006). Characterization of capsaicin synthase and identification of its gene (csy1) for
pungency factor capsaicin in pepper (Capsicum sp.). Proceedings of the National
Academy of Sciences, 103(36), 13315-13320. https://doi.org/10.1073/pnas.0605805103
23. Reilly, C. A., Crouch, D. J., Yost, G. S., & Fatah, A. A. (2001). Determination of capsaicin,
dihydrocapsaicin, and nonivamide in self-defense weapons by liquid
chromatography–mass spectrometry and liquid chromatography–tandem mass
spectrometry. Journal of Chromatography a, 912(2), 259-267.
https://doi.org/10.1016/s0021-9673(01)00574-x
24. Stewart, C., Kang, B.-C., Liu, K., Mazourek, M., Moore, S. L., Yoo, E. Y., Kim, B.-D., Paran, I.,
& Jahn, M. M. (2005). The Pun1 gene for pungency in pepper encodes a putative
acyltransferase. The Plant Journal, 42(5), 675-688.
https://doi.org/10.1111/j.1365-313X.2005.02410.x
25. Swetnisha, A. B., Gogoi, H. K., & Raju, P. S. (2017). In vitro production of capsaicin through
plant tissue culture. Journal of Phytology, 24-33.
https://doi.org/10.25081/jp.2017.v9.3389
26. Thiele, R., Mueller-Seitz, E., & Petz, M. (2008). Chili Pepper Fruits: Presumed Precursors of
Fatty Acids Characteristic for Capsaicinoids. Journal of Agricultural and Food
Chemistry, 56(11), 4219-4224. https://doi.org/10.1021/jf073420h
27. Venkitasubramanian, P., Daniels, L., & Rosazza, J. P. N. (2006). Reduction of Carboxylic Acids
by Nocardia Aldehyde Oxidoreductase Requires a Phosphopantetheinylated Enzyme.
Journal of Biological Chemistry, 282(1), 478-485.
https://doi.org/10.1074/jbc.M607980200
28. Weber, N., Ismail, A., Gorwa-Grauslund, M., & Carlquist, M. (2014). Biocatalytic potential of
vanillin aminotransferase from Capsicum chinense. BMC Biotechnology, 14(1), 25.
https://doi.org/10.1186/1472-6750-14-25
29. Yu, A.-Q., Pratomo Juwono, N. K., Foo, J. L., Leong, S. S. J., & Chang, M. W. (2016). Metabolic
engineering of Saccharomyces cerevisiae for the overproduction of short branched-chain
fatty acids. Metabolic Engineering, 34, 36-43.
http://dx.doi.org/10.1016/j.ymben.2015.12.005