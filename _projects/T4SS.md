---
layout: page
title: "Algae, bacteria, and the genetics in between"
description: Bioinformatic research on bacterial genome architecture with regards to microbial interactions
img: assets/img/projects/t4ss/ehuxPinhibens.jpg
importance: 1
category: Science
giscus_comments: true
toc:
  sidebar: left

---

This project is an M\.Sc research project that was part of my masters' thesis, I was under the supervision of Dr. Einat Segev and have also been mentored by PhD student Yemima Duchin Rapp, in the Plant & Environmental Sciences department of the Weizmann Institute of Science. 

Parts of my work were featured [in a very recent paper which was submitted not long ago](https://www.biorxiv.org/content/10.1101/2023.11.14.567099v2). Therefore I'll only give very brief and partial introduction before diving into the data analysis driven portion of the project, therefore I'm not going to meticulously state every single reference, only a few major ones. Please read the paper if you want to read about the study in depth! :man_scientist: :microbe:

Not a biologist? No worries! You can [skip the biology and go through a much simpler explanation of what's going on](#introduction-for-non-biologists) or you can [go straight into my data analysis project!](#defining-a-research-question-and-approach).

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/t4ss/barentsbloom.jpg" title="Phytoplankton bloom, Barents Sea." class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Phytoplankton bloom, Barents Sea. August 3rd, 2023. These seasonal blooms are where many different organisms interact, as well as the bacteria and micro-algae we study. The image above was acquired by the Moderate Resolution Imaging Spectroradiometer (MODIS) on NASA's Terra satellite.
</div> 

### Biological Introduction

**Horizontal gene transfer (HGT)**, vital in bacterial evolution, involves the transfer of genetic material between unrelated bacteria.[^HGT] Despite small genomes, bacteria display remarkable genetic variations, enabling adaptability and flexibility. HGT, through mechanisms like Transformation, Transduction, Gene Transfer Agents, and Conjugation, empowers bacteria to acquire new capabilities for symbiosis, antibiotic resistance, metabolic activity, and pathogenicity.[^trans]

A central mechanism for HGT is the **type IV secretion system (T4SS)**, facilitating **cell-to-cell contact and genetic material transfer**. Many bacteria possess T4SS on plasmids or chromosomes, impacting their functionality. In the environmentally crucial Roseobacter group, T4SS genes vary in genomic locations, raising questions about their functional impact.[^t4ss]

Conjugation, a form of HGT, is suggested to contribute significantly to the ecological success of Roseobacters, known for diverse metabolic capabilities and symbiotic interactions, especially with algal hosts. Algal exudates, influencing bacterial physiology, may act as signals promoting bacterial HGT.[^roseoConjugation]

Many Roseobacters interact with algal hosts, benefiting from algae's nutrient-rich exudates in the nutrient-poor ocean. This proximity supports nutrient flux for planktonic bacteria. **Algal exudates impact bacterial physiology and interactions**, promoting horizontal gene transfer (HGT) through bacterial proximity and attachment. Our study explores Roseobacter conjugation in the ecological context of the algal host *Emiliania huxleyi*. We utilized Roseobacter species identified in algal samples, testing their ability to conduct conjugation and examining the influence of T4SS genomic location. Additionally, we investigated the impact of algal exudates on bacterial conjugation, focusing on T4SS-encoding gene expression and DNA transfer.[^exudates]

This study explored Roseobacter conjugation in the context of an algal host, using *Emiliania huxleyi*. While a **chromosome-encoded T4SS did not lead to successful conjugation, a plasmid-encoded T4SS functioned**. Surprisingly, expression of plasmid-encoded T4SS genes did not increase in response to algal exudates, yet conjugation efficiency and plasmid transfer improved. This suggests a connection between bacterial response to an algal host and an increased likelihood of successful conjugation. ***The difference in functionality of a plasmid-encoded, or a chromosomally encoded T4SS sparked my interest and led to the project I'm going to show you now!***

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/t4ss/ehux.jpg" title="Emiliania huxleyi" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/t4ss/PIrosette.png" title="Phaeobacter inhibens bacteria form beautiful rosettes" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/t4ss/ehuxPinhibens.jpg" title="Phaeobacter inhibens attached to an Emiliania huxleyi cell" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    On the left, Emiliania huxleyi, an abundant coccolithophore in modern oceans. Middle, multiple cells of Phaeobacter inhibens bacteria, forming what we call a 'rosette'. Right, Phaeobacter inhibens attached to an Emiliania huxleyi cell.
</div>

### Introduction for non-biologists
*You can [skip ahead](#defining-a-research-question-and-approach) if you've read the previous introduction segment.*

Imagine bacteria as tiny living beings with small instruction manuals inside them, guiding how they grow and function, that's their DNA. **Sometimes, these bacteria share parts of their instruction manuals with each other**. This sharing, called Horizontal Gene Transfer (HGT), helps them adapt to different challenges.

Now, **one way bacteria share information is through something called the type IV secretion system (T4SS)**. It's like a tiny delivery system that allows bacteria to pass on their instruction manuals to other bacteria nearby. Some bacteria have this system on **small circular structures called plasmids**, while others have it in their **main instruction manual (chromosome)**.

In a specific group of bacteria called *Roseobacters*, we found that the T4SS genes are in different places in their instruction manuals. One interesting thing about Roseobacters is their interactions with algae, like tiny plant-like organisms in the ocean. **These bacteria benefit from the nutrients that algae release, helping them grow**. The study looked at how these bacteria interact with algae, focusing on the T4SS.

We tested different Roseobacter species to see how they share information, and found that the T4SS on plasmids works well, while the one on the chromosome (main instruction manual) doesn't work as effectively.

Surprisingly, the bacteria's response to algae didn't make the T4SS on plasmids work better, but the **bacteria still shared information more efficiently**. This suggests that the way bacteria react to algae somehow helps them share their instruction manuals better.

So, this study explored how bacteria, specifically Roseobacters, share information in the context of their interaction with algae. ***The differences in how the plasmid and main instruction manual versions of T4SS work caught the our attention and inspired the project I'm showing next.***

### Defining a research question and approach
Seeing as there's a functional difference between these systems depending on their encoding location, we defined our research question as ***"What is the difference between chromosomally or plasmid encoded T4SS and can it explain conjugation ability"***'

We began approaching this question experimentally and planned designs of several mutant strains, however, technical difficulties and time limits of my studies made us recalculate and I've decided to move on with a **bioinformatic approach**, focusing on **data analysis** in order to address the question on a **larger scale** by collecting data from numerous bacterial strains. The first step would be to **create a dataset**.

### Data Retreival and Handeling
#### Data Retreival
The first step was to **gather all relevant data**. We started by mapping out all the relevant genes associated with our system on [KEGG](https://www.genome.jp/kegg/). Next, we produced function profiles listing the number of copies of each gene per bacterial scaffold using [JGI's IMG/MER database](https://img.jgi.doe.gov/cgi-bin/mer/main.cgi) and matching with the unique IDs we previously gathered. Additionally, we downloaded all protein sequences files. **Retrieval of protein sequences had to be automated using the Selenium library in Python** due to the large quantity of sequences (over 6,000). The script interacts with [JGI's IMG/MER interfaces](https://img.jgi.doe.gov/cgi-bin/mer/main.cgi) for genomic data.:globe_with_meridians::snake:

***In total, we gathered several thousands of lines of data, and several thousands of protein sequences to analyze.***

#### Data Cleaning and Transformation
Tables containing function profiles had to be merged with metadata tables **using R and the dplyr package in R**. Cleaning the data included renaming mislabeled columns, treating missing data with NA and overall reorganization of the dataset.

Protein sequences files also required attention throughout the pipeline, mainly requiring text manipulation on file names. **This was done using linux and python.** :man_technologist:

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/t4ss/function_profile_cleaning.png" title="Function profile data" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/t4ss/metadata_cleaning.png" title="Genomic metadata" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
  Lots of raw data to handle!
</div>

#### Tools and methods used for analysis
Beyond analyses done using **R**, designated tools for sequence analyses were used in this work. Web-based apps like [InterProScan](https://www.ebi.ac.uk/interpro/), for classification of protein families. [BLAST](https://blast.ncbi.nlm.nih.gov/Blast.cgi), a sequence alignment tool. And other offline, **linux based applications** as [MAFFT sequence alignment program](https://mafft.cbrc.jp/alignment/server/) and [PHYLIP program suite, for phylogenetic analyses](https://phylipweb.github.io/phylip/).

### Results
#### Target genes' distribution in Roseobacters reveals missing pieces
Even before we deal with our question directly, exploring the data and getting to know it revealed lots of interesting observations and generated more questions.

Due to the large amount of data, and since we're now looking into the distribution of genes I thought the best way to visualize it would be to show the gene distribution on a heatmap. 

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/t4ss/big_heatmap.png" title="Type IV secretion system gene distribution in Roseobacters" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
  Gene distribution heatmap in Roseobacters. The columns present genes, rows correspond to operons of specific strains. The rightmost column shows the predicted encoding location (plasmid or chromosome). Colors in the body of the table the indicate gene copy numbers. Rows are clustered by encoding loci.
</div>

The heatmap shows so much! You can tell there's lots of variance in the gene distribution, clearly **most systems are encoded on plasmids**. Also there seem to be a **variety of unique plasmids**, but we'll touch more on that later.

The first noticeable anomaly is the **absence of VirB1 genes. What's not shown here is how VirB7 is missing completely, and therfore is not plotted**. The literature isn't conclusive on these genes' importance for conjugation. Some suggest they're essential, while others argue they're dispensable. However the functions they're said to perform **may be critical for conjugation**. Given these extreme findings, I questioned the validity of the data. To perform a sanity check, I conducted a thorough analysis of the genes comprising the system in our model strains.


#### Thorough gene context analysis reveals challenges in study of T4SS genes
JGI's platform proved useful for comparing gene context between the T4SS of two model strains we used for this research: *Phaeobacter inhibens* strains P72 and DSM-17395. Two copies of the system are encoded on **two different plasmids** of strain **P72** (A & B in the figure below), while only one copy exists on the **chromosome of DSM-17395** (C in the figure below). 

The first thing I noticed when I looked at the gene layout of P72 was there were so many **hypothetical proteins!** is one of them our missing ***VirB1 or VirB7?***

To those of you that are not biologists, a hypothetical protein means these are proteins that are **predicted** to be expressed in an organism, but so far there's no evidence of their existence. Meaning that the gene exists, but it's not clear if it is being transcribed and translated into a **functioning protein**.

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/t4ss/T4SSlayout.png" title="Schematic T4SS operon layout for P. inhibens strains P72 and DSM 17395" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
  Schematic T4SS operon layout for P. inhibens strains P72 and DSM 17395. A.  Layout of P. inhibens P72 pP72b operon. B. Layout of P. inhibens P72 pP72e operon. C. Layout of P. inhibens DSM 17395 operon.
</div>

It's no big surprise as you can see below, but after some analyses we found that some of these proteins resembled VirB1! **A specific domain affiliated with VirB1 was found and allowed us to classify it as VirB1-like protein**. Even though the databases link this domain and hypothetical protein, they don't link it to the original VirB1 protein. In analyses on the other hypothetical proteins we couldn't find any resemblence to other proteins. However we can say that the hypothetical proteins (#1,2,3,4) we're talking about differ from each other but are highly similar between the strains. 

This highlighted the challenge in studying this system, where **some proteins lack distinct patterns or domains that would allow us to identify them**. We decided to neglect these proteins' influence, excluding them from other analysis, in order to move forward and see what else the data shows :nerd_face:.

#### A missing protein may explain in-ability to perform conjugation in chromosomal T4SS
But hey, that's not all, there's a noticeable difference between the gene layout of the plasmid-encoded T4SS (A & B in the previous picture) and the chromosomally encoded T4SS (C in the previous picture), And that is **the absence of hypothetical protein #4**. 

While we couldn't associate it with any function computationaly, it is currently the first candidate to blame for a functional difference between the systems. The next logical step is to experimentally test this hypothesis using genetic editing tools. *Unfortunately, experimental work was no longer possible at that stage of my studies* :man_shrugging:.

#### Relatively few Roseobacters contain "intact" systems
Genes in some genetic systems, like the T4SS we're studying, are **grouped togheter** in the DNA. Therefore we assume that the entire group has to be intact, complete and all of the genes of the system must be present in the DNA for the system to be 'enabled'. Any missing protein could effect the functionality of the system, think about it like a machine with missing cogs!

After filtering the data to count how many bacteria contain a complete system we found that **only 329 out of 1172 strains have at least one system encoded in their DNA**! (that's just 28%! :hushed: ) 

Can the system function with missing proteins? Are there alternative proteins filling in for the missing ones? Are there entirely alternative systems in use? So many questions! :thinking:

#### Unique plasmid Operational Taxonomic Units 
Researchers at the JGI came up with a tool to identify mobile genetic elements[^camarago]. The idea is that **plasmids that are have very close evolutionary relations, can be clustered and be named with the same "plasmid Operational Taxonomic Unit" (pOTU)**. We can use this type of analysis to determine plasmids of unique ancestry.

From this data we can see that distribution of unique pOTUs in Roseobacters varies significantly. **The majority (372) of plasmids are unique to a single strain**, indicating diverse plasmid arrays. Meaning that **each of these 372 plasmids are completely unique**! Conversely, **up to 18 genomes share a single pOTU**, in other words, there are groups of bacteria, with the largest group having 18 bacteria, that have the same plasmid OTU! This may not be *exactly* the same plasmid, but **evolutionarily speaking they're as close as it gets!** this suggests enhanced HGT potential within this plasmids.

<div class="row justify-content-center">
    <div class="col-sm-7 mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/t4ss/uniquePOTUplot.png" title="Unique pOTUs abundance in Roseobacters" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
  Unique pOTUs abundance in Roseobacters. X axis shows how many times a unique pOTU is found across all Roseobacter genomes. Y axis shows the number of unique pOTUs (also indicated above each bar).
</div>

In the table below we see how distinct gene distributions look like in pOTUs that are common to more than 6 genomes in the Roseobacter group. **Most operons within the same pOTU share similar function profiles**. For example, PTU_00024961 and PTU_00009131 exhibit a conservative pattern, indicating a relatively recent transfer. In contrast, pOTUs like PTU_000002018, PTU_000000120, and PTU_000000141 show lower conservation and significant variance among plasmids carrying the same pOTU.

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/t4ss/pOTU_heatmap.png" title="VirB/D operon genes distribution in Roseobacters" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
  VirB/D operon genes distribution in Roseobacters. A subset data for pOTUs appearing in more than 6 Roseobacter genomes was used to generate a heatmap. Columns present genes, rows correspond to strains. Colors of the heatmap indicate the copy number for each gene (0-2, see legend on the right). Rightmost column (pOTU) shows the classification of plasmid OTUs.
</div>


#### Sequences encoded on chromosomes are distinct from sequences encoded on plasmids
One of the more resource-intensive analyses I've done was focused on sequence comparison. **Protein sequences of each studied Vir protein family found in Roseobacters were aligned and then processed in a phylogenetic pipeline for clustering and tree-drawing**. The pipeline is briefly described in the flowchart below.

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/t4ss/diagram.png" title="virB8 protein maximum likelihood tree" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

In one example, for T4SS gene virB8, out of 569 virB8 sequences that were analyzed, 28 are encoded on chromosomes and 541 on plasmids. It's easily seen on the tree shown below, that **most chromosomally encoded virB8 sequences cluster together** (marked in yellow), with only 4 outlier sequences which cluster within PE-virB8 clusters (pointed at with black arrows). the clear distinction between the two groups suggests recent incorporation of these plasmid virB8 genes (and the whole operons) into the chromosomes of their hosts. 

The consensus sequences of each alignment, plasmid and chromosomally encoded T4SS genes, were taken and aligned to the other. Sequence alignment between consensus sequences shows that the proteins are **mostly conserved**, yet some differences are visible. By definitions formerly suggested in the literature, most changes seem conservative or moderately conservative, suggesting such changes would preserve protein structure and properties[^grantham],[^li]. However, **eight of the variable positions present changes that are classified as moderately radical and may affect protein structure and properties.**

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/t4ss/virB8tree.jpg" title="virB8 protein maximum likelihood tree" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
  virB8 protein maximum likelihood tree. X axis presents branch length in arbitrary units, Y axis shows different taxa. Yellow markers represent T4SS operons encoded on chromosome, blue markers stands for T4SS operons encoded on plasmid. Black arrows mark instances of chromosomal sequences clustered in plasmid-encoded-dominant clusters. Trees were generated using sequence alignment analyzed by PHYLIP proML and colored manually. 
</div>

### Discussion & Conclusions
In conclusion, exploration into the T4SS presented several interesting observations, as well as challenges. The mis-annotation of certain genes, such as virB1 and virB7, highlighted the challenges in studying these systems, emphasizing the need for precise genetic data. Furthermore, our comparative analysis of chromosomal and plasmid encoded T4SS sequences shed light on distinctive patterns, further underscoring the uniqueness of these systems. And suggesting that plasmid encoded T4SS in Roseobacters is active in context of conjugation, while chromosomally encoded T4SS is not, although it requires further confirmation. 

Although certain questions remain, particularly regarding the evolutionary scenarios and the precise roles of specific proteins, this study lays a foundation for future investigations in understanding the complex interplay between algae and bacterial conjugation within the Roseobacter group.

<div class="row justify-content-center">
    <div class="col-sm-7 mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/t4ss/comics.jfif" title="Bacteria performing conjugation. Picture by Noémie Matthey" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
Conjugation is a HGT process that occurs between bacterial cells (involving cell contact). The genetic materiel is transferred via a #pilus from the donor to the recipient bacterium. Picture by Noémie Matthey
</div>

### References
  [^camarago]: Camargo, A. P. et al. Identification of mobile genetic elements with geNomad. Nat Biotechnol 1-10 (2023) doi:10.1038/s41587-023-01953-y.
  [^HGT]: Ochman, H., Lawrence, J.G., and Groisman, E.A. (2000). Lateral gene transfer and the nature of bacterial innovation. Nature 405, 299–304. doi:10.1038/35012500.
  [^trans]:Thomas, C.M., and Nielsen, K.M. (2005). Mechanisms of, and barriers to, horizontal gene transfer between bacteria. Nat Rev Microbiol 3, 711–721. doi:10.1038/nrmicro1234.
  [^t4ss]:Wong, J.J., Lu, J., and Glover, J.N. (2012). Relaxosome function and conjugation regulation in F-like plasmids - a structural biology perspective. Mol Microbiol 85, 602–617. doi:10.1111/j.1365-2958.2012.08131.x.
  [^roseoConjugation]:Birmes, L., Freese, H.M., and Petersen, J. (2021). RepC_soli: a novel promiscuous plasmid type of Rhodobacteraceae mediates horizontal transfer of antibiotic resistances in the ocean. Environ Microbiol 23, 5395–5411. doi:10.1111/1462-2920.15380.
  [^exudates]:Segev, E., Wyche, T.P., Kim, K.H., Petersen, J., Ellebrandt, C., Vlamakis, H., Barteneva, N., Paulson, J.N., Chai, L., Clardy, J., and Kolter, R. (2016). Dynamic metabolic exchange governs a marine algal-bacterial interaction. Elife 5. doi:10.7554/eLife.17473.
  [^grantham]:Grantham, R. Amino acid difference formula to help explain protein evolution. Science 185, 862–864 (1974).
  [^li]:Li, W.-H., Wu, C.-I. & Luo, C.-C. Nonrandomness of point mutation as reflected in nucleotide substitutions in pseudogenes and its evolutionary implications. J Mol Evol 21, 58–71 (1984).
  