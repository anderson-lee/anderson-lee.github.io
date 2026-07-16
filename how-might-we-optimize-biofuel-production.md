---
layout: default
title: How might we optimize biofuel production?
---

# How might we optimize biofuel production?

or

## Developing an _in silico_ Oxygen-Sensitive Biological Gene Circuit to Increase Hydrogen Production in _Synechocystis_ PCC 6803 

Author's Note: This was my final project from Adam Arkin's Synthetic Biology course at UC Berkeley. I'm not sure how feasible it is, but it would be cool if this inspired someone.

### Introduction

As fossil fuel reserves deplete and greenhouse gases warm our atmosphere, the world is
looking for a cheap, sustainable alternative energy source. One possible answer is manipulating
biological organisms to create biomass that can then be converted into energy. In this field,
cyanobacteria are of great interest because of their malleable genome and innate autotrophic
cellular machinery. There already exists technology capable of producing energy from hydrogen;
thus, if scientists can engineer organisms to produce mass amounts of biomass, the world will be
supplied with energy.

Previous research has demonstrated how cyanobacteria can produce hydrogen under
specific conditions, such as removing sulfur from algae (Melis et al., 2000). Current research
focuses on how to optimize the innate hydrogen production pathways that cyanobacteria possess,
but none have rendered a commercially viable formula. This paper presents a novel genetic
circuit to increase the hydrogen production of Synechocystis PCC 6803, a well-studied
photosynthetic bacterium. In this organism, an enzyme named hydrogenase catalyzes the reaction $$\ce{2H^+ + 2e^- -> H_2}$. This enzyme functions as a bidirectional hydrogenase, reducing protons to dihydrogen in addition to oxidizing apart H . It has a nickel-iron core, and reduces NAD(P)H in order to gain electrons (Appel et al., 1996). During photosynthesis, cyanobacteria store high energy electrons in a “PQ Pool,” or the plastoquinone pool, located in the thylakoid membrane.
Researchers believe that hydrogenase takes the lower-energy electrons from here—the ones that
do not have enough energy to invoke the next step of photosynthesis—and uses them to create
hydrogen, therefore not wasting any energy (Appel et al., 2000). More recently, they have also
found that when photosynthesis is down-regulated—for example, during nighttime—hydrogen
production by hydrogenase is heavily favored (De Rosa et al., 2015). However, hydrogenase is
greatly inhibited by oxygen. There have been attempts to artificially create a semi-permeable
membrane using nanotechnology that blocks oxygen or to genetically reengineer the hydrogenase to be tolerant to oxygen, but neither of these have produced hydrogen at a
significant level (Santos et. al; Xu et al., 2005).

No previous attempts have been made to create a dynamic genetic circuit that facilitates
hydrogen production by responding to the oxygen level. The following paper details a novel
biological circuit and shows that it prevents oxygen from building up in the cell, thereby aiding
hydrogen production. It also suggests future steps in order to prove this circuit works in vitro.


    ![Alt text](/images/CircuitDiagram.png)

_Figure 1: Genetic Circuit for Optimizing Hydrogen Production. If oxygen is present, then tetR cannot be transcribed, allowing glbN to be produced and bind to O<sub>2</sub>. If oxygen is not present, then fnr is in its active state, and tetR represses the production of glbN._

### Methods

Oxygen can diffuse through the membrane and be present in the cytoplasm of bacteria. In
order to detect oxygen, this circuit will integrate Escherichia coli’s fumarate and nitrate reduction
(FNR) system into my organism. In E. coli, this system is responsible for detecting anaerobic
conditions and regulating gene expression in response. There have already been successful
attempts to create an oxygen-dependent synthetic circuit in Synechocystis PCC 6803 using this
system (Immuthen et al., 2016). The transcription factor will be fnr from E. Coli MG1655 (Gene
ID: 945908). This protein will be constitutively expressed by promoter Bba J23104. The fnr
protein is present in the cytoplasm of the cell, and when it interacts with oxygen, it transforms
from its active state to its inactive state. A [4Fe-4S]<sup>2+</sup> cluster transforms into a [2Fe-2S]<sup>2+</sup> cluster
in the presence of oxygen (Khoroshilova et al., 1997). The [2Fe-2S]<sup>2+</sup> cluster is unable to bind to
DNA, thereby deactivating fnr. This reaction occurs only when O<sub>2</sub> is present, but O<sub>2</sub> is not used
in the reaction (Unden et al., 1997). The activated fnr complex will be referred to as fnr–a in this
paper, and the deactivated complex will be referred to as fnr–d. The deactivated complex, which
can either be the [2Fe-2S]<sup>2+</sup> cluster or the apoFNR form that occurs with prolonged exposure to
O<sub>2</sub>, can transform back into the activated form of the [4Fe-4S]<sup>2+</sup> cluster in the presence of
glutathione (Tran et al., 2000). This paper assumes that there will always be enough glutathione present for this reaction to occur. The corresponding FNR-activated promoter will be used to
control gene expression, hereby referred to as fpromoter (Grainger et al., 2007).

This promoter will be upstream of the commonly used TetR repressor. This circuit will
specifically use tetR because it has been shown to work in bacteria before (Vavitsas et al., 2019).
It is assumed that the off-target effects of tetR are minimal and neglectable and that there is an
abundance of RNA polymerase. It is also assumed that all mRNA dynamics are at steady state
because mRNA dynamics are much faster and reach steady state faster than protein dynamics.
tetR has a nucleotide length of 207, and if RNAP operates at 40-80 nt/sec, then it should take
between 2.6-5.2 seconds for one to be transcribed. This is equivalent to 11.5-23 per minute.

Once tetR is transcribed, it will be able to bind to tetO. tetO will be the promoter of a
globin protein. Specifically, it will be transcribing glbN, a protein already present in
Synechocystis PCC 6803 which cooperatively binds to oxygen (Thorsteinsson et al., 1999).
There will be one globin protein transcribed every 1.55-3.1 seconds, which is 19.4-38.7 per
minute. It binds with cooperativity P<sub>50</sub> = 0.013 mmHg at 20°C (Couture et al., 1999).
Furthermore, glbN resides on the peripheral membrane of the cell, so ideally it will bind to
oxygen before oxygen even enters the cell, allowing the cell to increase its hydrogen production
(Hill et al., 1996). There is also the need to consider the oxygen produced by the cell in
photosynthesis. Since this oxygen will already be inside the cell, it is assumed that glbN will
bind to it when it is in the cytoplasm. When oxygen is present, glbN will be expressed because
tetR will not be repressing tetO, but when the conditions are anaerobic, glbN will not be
produced. The reason for this is to limit the load placed on the cell so that the cell is only
producing glbN when it needs to. Otherwise, when oxygen is not present, the cell can focus its
resources on other processes.

The reason for the end product to be a globin protein instead of something else, such as
hydrogenase, is that if oxygen is present it will inhibit hydrogenase, no matter the quantity of
hydrogenase. Thus, the rationale for producing globin is so the cell could still hypothetically
create hydrogen, even when producing oxygen with photosynthesis. In addition, hydrogen
production in Synechocystis only happens in specific conditions, one of which is immediately
when the cell starts to photosynthesize. Thus, designing a circuit that produces hydrogenase
would not be effective because of the time delay involved in the circuit. Hydrogenase needs to be
present and uninhibited in order for maximal hydrogen production. Once O<sub>2</sub> is no longer
inhibiting hydrogenase, the limiting factor of hydrogen production of a cell is the rate at which
NAD(P)H is recycled through the NDH-1 complex (Cournac et al., 2002).

The set of ODEs in Figure 2 will be computationally tested using the Biosystem class of
Matlab. In order to empirically test this model, a bioreactor would be required to control the
inputs of O<sub>2</sub> and measure the output of H2. First, a baseline must be established, so a colony
without any genetic changes in both aerobic/anaerobic environments and dark/light environments
would be analyzed. Synechocystis PCC 6803 produces hydrogen mainly in two precise
environmental states: in the dark, when the cell is forced to assimilate glycogen as an electron acceptor, and at the beginning of photosynthesis when light is exposed (Dickson et al., 2009). In
order to test this model in silico, the genetically modified organisms will be tested under the
same parameters. Ideally, they will behave as expected in stable conditions: the dark, anaerobic
environment will create a natural situation for hydrogen production because no oxygen is present
and the cell is not producing oxygen as a byproduct of photosynthesis. If the cell is without light
but in an aerobic environment, the globin proteins on the membrane will keep the cytoplasm
anaerobic. If the cell is photosynthesizing but in an anaerobic environment, the globin proteins
should bind to the intracellular oxygen, and if the cell is producing oxygen in an oxygenated
environment, then glbN needs to bind to both intracellular O<sub>2</sub> and O<sub>2</sub> diffusing through the
membrane. The two trials with light will prove to be more difficult, as the cell will produce
oxygen, so one would expect them to have a lower hydrogen yield than the cells in the dark.

### Results and Discussion

Synechocystis PCC 6803 produces 0.025μM O<sub>2</sub> due to photosynthesis (Kihara et al.,
2014). Thus, the first trial assumed that no environmental oxygen diffused through the cellular
membrane, and it assumed the intracellular O<sub>2</sub> could be bound by glbN.

    ![Alt text](/images/Fig3.png)

    _Figure 3: Simulation of the genetic circuit in an anaerobic (a) and aerobic (b) environment.

As one can observe from Figure 3a, the intracellular oxygen was immediately bound by
globin. This is because tetO is constitutively expressed, and as soon as glbN is made, it binds to
the available oxygen. This is favorable because O<sub>2</sub> inhibits hydrogen production whereas glbN
simply places slightly more load on the cell, so it is beneficial to automatically produce globin
immediately rather than wait to detect if O<sub>2</sub> is present or not. Once all of the oxygen has been bound by glbN to create glbN::O<sub>2</sub>, glbN is still produced. However, once the upstream parts of the genetic circuit detect that there is no oxygen left, tetR is produced and tetO is no longer able to create glbN, so the concentration of glbN decreases as it binds to O<sub>2</sub> that dissociated from glbN::O<sub>2</sub> and the protein degrades. In water that comes into contact with air, the oxygen concentration is $2.25 \times 10^−4$_M_.

Thus, to simplify the system the extracellular concentration of oxygen will be combined with the
intracellular concentration of oxygen to exemplify a cyanobacterial cell in light in an aerobic
environment. This results in an oxygen concentration of $2. 75 \times 10^-4$_M_. As expected, Figure 3b shows that this trial yields a similar result to the first one, except for the fact that it takes slightly
longer for the cell to produce enough glbN to bind to O<sub>2</sub>.

For the cells placed in the dark, there will be no light energy to undergo photosynthesis,
so the cell will not be producing oxygen. Thus, the only oxygen that could interfere with
hydrogenase activity will be environmental O<sub>2</sub>. This yields essentially the same result as the second trial, as depicted by Figure 4a.

Finally, when Synechocystis is placed in a dark, anaerobic environment, it already
produces H2, so this circuit should not interfere with the cell. Figure 4b displays the fact that when
no oxygen is present, glbN is repressed by the production of tetR. The glbN initially produced
slowly decays away, and the cell is in its natural state.

    ![Alt text](/images/Fig4.png)

    _Figure 4: Simulation of the genetic circuit of a non-photoautotrophic cell in an anaerobic (a) and aerobic (b) environment.

Looking at the results as a whole, this genetic circuit functions well under the
assumptions made. Future steps in this field include addressing some of the assumptions. For
instance, it should be investigated whether the glbN protein can prevent oxygen from entering
the cell by residing on the membrane. If a complete anaerobic environment is created inside the
cell, then there would exist a large chemical gradient for oxygen to diffuse into the cell.
Furthermore, it was assumed that the oxygen inside the cell, produced as a byproduct of photosynthesis, would be bound by glbN. However, that is not guaranteed. Since hydrogen production in Synechocystis occurs in the PQ pool, there might be no possible way to separate the O<sub>2</sub> produced in photosynthesis from the hydrogenase needed to produce H2 because they
operate in the same physical space. It would be of interest to make the space inside the thylakoid
anaerobic so that hydrogenase could function while the cell was undergoing photosynthesis. This
could be achieved with a chemical gradient in conjunction with the oxygen content of the
cytoplasm. Another future paper would be to examine the off-target effects of the tetR protein.
Synechocystis does have a homolog to tetR, and since tetR is being produced constantly in
anaerobic environments, it could effect expression of other genes. That being said, the genetic
circuit presented in this paper might be most applicable to instances without light. This is still
advantageous because a mutant cell would ideally be able to operate in an oxygenated
environment, whereas a normal cell could not.

### Conclusion

The novel biological gene circuit presented here prevents O<sub>2</sub> from interfering with
hydrogenase activity in silico. In environments where the cell is producing O<sub>2</sub> or O<sub>2</sub> is present in
the environment, the circuit produces a globin protein that binds with high affinity to oxygen.
When no oxygen is present, the circuit does not place a significantly larger load on the cell.
The future of cyanobacterial hydrogen production is promising; however, it is not close to
becoming commercially viable yet. In addition to investigating the subtleties of this approach,
hydrogen production in general needs to be optimized, including strategies surrounding the
recycling of NAD(P)H through the NDH-1 complex and rapid biomass accumulation. Internal
processes of Synechocystis PCC 6803 need to be more fully understood, and researchers need to
document other, possibly more helpful species of cyanobacteria that possess the ability to
produce hydrogen.

### References

References
1. Allahverdiyeva, Y., Mustila, H., Ermakova, M., Bersanini, L., Richaud, P., Ajlani, G., ... Aro, E.
M. (2013). Flavodiiron proteins Flv1 and Flv3 enable cyanobacterial growth and
photosynthesis under fluctuating light. Proceedings of the National Academy of Sciences of
the United States of America, 110(10), 4111–4116.
https://doi.org/10.1073/pnas.1221194110
2. Appel, J., Phunpruch, S., Steinmüller, K., & Schulz, R. (2000). The bidirectional hydrogenase of
Synechocystis sp. PCC 6803 works as an electron valve during photosynthesis. Archives of
Microbiology, 173(5–6), 333–338. https://doi.org/10.1007/s002030000139
3. Appel, J., & Schulz, R. (1996). Sequence analysis of an operon of a NAD(P)-reducing nickel
hydrogenase from the cyanobacterium Synechocystis sp. PCC 6803 gives additional
evidence for direct coupling of the enzyme to NAD(P)H-dehydrogenase (complex I).
Biochimica et Biophysica Acta - Protein Structure and Molecular Enzymology, 1298(2),
141–147. https://doi.org/10.1016/S0167-4838(96)00176-8
4. Cournac, L., Mus, F., Bernard, L., Guedeney, G., Vignais, P., & Peltier, G. (2002). Limiting steps
of hydrogen production in Chlamydomonas reinhardtii and Synechocystis PCC 6803 as
analysed by light-induced gas exchange transients. International Journal of Hydrogen
Energy, 27(11–12), 1229–1237. https://doi.org/10.1016/S0360-3199(02)00105-2
5. Couture, M., Yeh, S. R., Wittenberg, B. A., Wittenberg, J. B., Ouellet, Y., Rousseau, D. L., &
Guertin, M. (1999). A cooperative oxygen-binding hemoglobin from Mycobacterium
tuberculosis. Proceedings of the National Academy of Sciences of the United States of
America, 96(20), 11223–11228. https://doi.org/10.1073/pnas.96.20.11223
6. Crack, J., Green, J., & Thomson, A. J. (2004). Mechanism of Oxygen Sensing by the Bacterial
Transcription Factor Fumarate-Nitrate Reduction (FNR). Journal of Biological Chemistry,
279(10), 9278–9286. https://doi.org/10.1074/jbc.M309878200
7. De Rosa, E., Checchetto, V., Franchin, C., Bergantino, E., Berto, P., Szabò, I., ... Costantini, P.
(2015). [NiFe]-hydrogenase is essential for cyanobacterium Synechocystis sp. PCC 6803
aerobic growth in the dark. Scientific Reports, 5. https://doi.org/10.1038/srep12424
Dennis, P. P., & Bremer, H. (2008). Modulation of Chemical Composition and Other Parameters
of the Cell at Different Exponential Growth Rates. In EcoSal Plus (Vol. 3).
https://doi.org/10.1128/ecosal.5.2.3
8. Dickson, D. J., Page, C. J., & Ely, R. L. (2009). Photobiological hydrogen production from
Synechocystis sp. PCC 6803 encapsulated in silica sol-gel. International Journal of
Hydrogen Energy, 34(1), 204–215. https://doi.org/10.1016/j.ijhydene.2008.10.021
9. Ducat, D. C., Sachdeva, G., & Silver, P. A. (2011). Rewiring hydrogenase-dependent redox
circuits in cyanobacteria. Proceedings of the National Academy of Sciences of the United
States of America, 108(10), 3941–3946. https://doi.org/10.1073/pnas.1016026108
10. Dutta, D., De, D., Chaudhuri, S., & Bhattacharya, S. K. (2005). Microbial Cell Factories
Hydrogen production by Cyanobacteria. 11, 1–11. https://doi.org/10.1186/1475-2859-4-36
11. Eckert, C., Boehm, M., Carrieri, D., Yu, J., Dubini, A., Nixon, P. J., & Maness, P. C. (2012).
Genetic analysis of the Hox hydrogenase in the cyanobacterium Synechocystis sp. PCC
6803 reveals subunit roles in association, assembly, maturation, and function. Journal of
Biological Chemistry, 287(52), 43502–43515. https://doi.org/10.1074/jbc.M112.392407
12. Freed, E., Fenster, J., Smolinski, S. L., Walker, J., Henard, C. A., Gill, R., & Eckert, C. A.
(2018). Building a genome engineering toolbox in nonmodel prokaryotic microbes.
Biotechnology and Bioengineering, 115(9), 2120–2138. https://doi.org/10.1002/bit.26727
13. Grainger, D. C., Aiba, H., Hurd, D., Browning, D. F., & Busby, S. J. W. (2007). Transcription
factor distribution in Escherichia coli: Studies with FNR protein. Nucleic Acids Research,
35(1), 269–278. https://doi.org/10.1093/nar/gkl1023
14. Gutthann, F., Egert, M., Marques, A., & Appel, J. (2007). Inhibition of respiration and nitrate
assimilation enhances photohydrogen evolution under low oxygen concentrations in
Synechocystis sp. PCC 6803. Biochimica et Biophysica Acta - Bioenergetics, 1767(2),
161–169. https://doi.org/10.1016/j.bbabio.2006.12.003
15. Hill, D. R., Belbin, T. J., Thorsteinsson, M. V., Bassam, D., Brass, S., Ernst, A., ... Potts, M.
(1996). GlbN (cyanoglobin) is a peripheral membrane protein that is restricted to certain
Nostoc spp. Journal of Bacteriology, 178(22), 6587–6598.
https://doi.org/10.1128/jb.178.22.6587-6598.1996
16. Immethun, C. M., Ng, K. M., Delorenzo, D. M., Waldron-Feinstein, B., Lee, Y. C., & Moon, T.
S. (2016). Oxygen-responsive genetic circuits constructed in Synechocystis sp. PCC 6803.
Biotechnology and Bioengineering, 113(2), 433–442. https://doi.org/10.1002/bit.25722
17. Jordan, P. A., Thomson, A. J., Ralph, E. T., Guest, J. R., & Green, J. (1997). FNR is a direct
oxygen sensor having a biphasic response curve. FEBS Letters, 416(3), 349–352.
https://doi.org/10.1016/S0014-5793(97)01219-2
18. Kamionka, A., Bogdanska-Urbaniak, J., Scholz, O., & Hillen, W. (2004). Two mutations in the
tetracycline repressor change the inducer anhydrotetracycline to a corepressor. Nucleic
Acids Research, 32(2), 842–847. https://doi.org/10.1093/nar/gkh200
19. Khoroshilova, N., Popescu, C., Münck, E., Beinert, H., & Kiley, P. J. (1997). Iron-sulfur cluster
disassembly in the FNR protein of Escherichia coli by O2: [4Fe-4S] to [2Fe-2S] conversion
with loss of biological activity. Proceedings of the National Academy of Sciences of the
United States of America, 94(12), 6087–6092. https://doi.org/10.1073/pnas.94.12.6087
20. Kihara, S., Hartzler, D. A., & Savikhin, S. (2014). Oxygen Concentration Inside a Functioning
Photosynthetic Cell. Biophysj, 106, 1882–1889. https://doi.org/10.1016/j.bpj.2014.03.031
21. Kihara, S., Hartzler, D. A., & Savikhin, S. (2014). Oxygen concentration inside a functioning
photosynthetic cell. Biophysical Journal, 106(9), 1882–1889.
https://doi.org/10.1016/j.bpj.2014.03.031
22. Melis, A., Zhang, L., Forestier, M., Ghirardi, M. L., & Seibert, M. (2000). Sustained
photobiological hydrogen gas production upon reversible inactivation of oxygen evolution in the green alga Chlamydomonas reinhardtii. Plant Physiology, 122(1), 127–135.
https://doi.org/10.1104/pp.122.1.127
23. Sarsekeyeva, F., Zayadan, B. K., Usserbaeva, A., Bedbenov, V. S., Sinetova, M. A., & Los, D. A.
(2015, August 17). Cyanofuels: Biofuels from cyanobacteria. Reality and perspectives.
Photosynthesis Research, Vol. 125, pp. 329–340.
https://doi.org/10.1007/s11120-015-0103-3
24. Scott, N. L., & Lecomte, J. T. J. (2008). Cloning, expression, purification, and preliminary
characterization of a putative hemoglobin from the cyanobacterium synechocystis sp. PCC
6803. Protein Science, 9(3), 587–597. https://doi.org/10.1110/ps.9.3.587
25. Thorsteinsson, M. V, Bevan, D. R., Potts, M., Dou, Y., Eich, R. F., Hargrove, M. S., ... Olson, J.
S. (1999). A Cyanobacterial Hemoglobin with Unusual Ligand Binding Kinetics and
Stability Properties †. https://doi.org/10.1021/bi9819172
26. Tolla, D. A., & Savageau, M. A. (2010). Regulation of aerobic-to-anaerobic transitions by the
FNR cycle in Escherichia coli. Journal of Molecular Biology, 397(4), 893–905.
https://doi.org/10.1016/j.jmb.2010.02.015
27. Tran, Q. H., Arras, T., Becker, S., Holighaus, G., Ohlberger, G., & Unden, G. (2000). Role of
glutathione in the formation of the active form of the oxygen sensor FNR ([4Fe-4S]·FNR)
and in the control of FNR function. European Journal of Biochemistry, 267(15),
4817–4824. https://doi.org/10.1046/j.1432-1327.2000.01539.x
28. Tran, Q. H., Arras, T., Becker, S., Holighaus, G., Ohlberger, G., & Unden, G. (2000). Role of
glutathione in the formation of the active form of the oxygen sensor FNR ([4Fe-4S]·FNR)
and in the control of FNR function. European Journal of Biochemistry, 267(15),
4817–4824. https://doi.org/10.1046/j.1432-1327.2000.01539.x
29. Unden, G., Achebach, S., Holighaus, G., Tran, H.-Q., & Zeuner, Y. (n.d.). Control of FNR
Function of Escherichia coli by O 2 and Reducing Conditions. Retrieved from
www.caister.com/bacteria-plant
30. Unden, G., Achebach, S., Holighaus, G., Tran, H.-Q., & Zeuner, Y. (n.d.). Control of FNR
Function of Escherichia coli by O 2 and Reducing Conditions. Retrieved from
www.caister.com/bacteria-plant
31. Unden, G., Becker, S., Bongaerts, J., Holighaus, G., Schirawski, J., & Six, S. (1995). O 2
-Sensing and O 2 -dependent gene regulation in facultatively anaerobic bacteria. Archives
of Microbiology, 164(2), 81–90. https://doi.org/10.1007/s002030050238
32. Unden, G., & Schirawski, J. (1997). The oxygen-responsive transcriptional regulator FNR of
Escherichia coli : the search for signals and reactions. Molecular Microbiology, 25(02),
205–210. https://doi.org/10.1046/j.1365-2958.1997.4731841.x
33. Ungerer, J., & Pakrasi, H. B. (2016). Cpf1 Is A Versatile Tool for CRISPR Genome Editing
Across Diverse Species of Cyanobacteria. Scientific Reports, 6.
https://doi.org/10.1038/srep39681
34. Vavitsas, K., Crozet, P., Vinde, M. H., Davies, F., Lemaire, S. D., & Vickers, C. E. (2019). The
Synthetic Biology Toolkit for Photosynthetic Microorganisms. Plant Physiology, 181(1),
14–27. https://doi.org/10.1104/pp.19.00345
35. Wang, B., Wang, J., & Meldrum, D. R. (2012). Application of synthetic biology in cyanobacteria
and algae. Frontiers in Microbiology, 3(SEP), 1–15.
https://doi.org/10.3389/fmicb.2012.00344
36. Xu Q, Yooseph S, Smith HO, Venter CJ: Development of a Novel Recombinant Cyanobacterial
System for Hydrogen Production from Water [abstract]. In Genomics: GTL Program
Projects J. Craig Venter Inatitute, Rockville, MD; 2005:64.