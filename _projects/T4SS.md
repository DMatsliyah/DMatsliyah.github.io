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

This project is an M.Sc research project that was part of my masters' thesis, I was under the supervision of Dr. Einat Segev and have also been mentored by PhD student Yemima Duchin Rapp, in the Plant & Environmental Sciences department of the Weizmann Institute of Science. 

Parts of my work were featured [in a very recent paper which was submitted not long ago](https://www.biorxiv.org/content/10.1101/2023.11.14.567099v2). Therefore I'll only give very brief and partial introduction before diving into the data analysis driven portion of the project. Please read the paper if you want to read about the biology! :man_scientist: :microbe:

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

Horizontal gene transfer (HGT), vital in bacterial evolution, involves the transfer of genetic material between unrelated bacteria. Despite small genomes, bacteria display remarkable genetic variations, enabling adaptability and flexibility. HGT, through mechanisms like Transformation, Transduction, Gene Transfer Agents, and Conjugation, empowers bacteria to acquire new capabilities for symbiosis, antibiotic resistance, metabolic activity, and pathogenicity.

A central mechanism for HGT is the type IV secretion system (T4SS), facilitating cell-to-cell contact and genetic material transfer. Many bacteria possess T4SS on plasmids or chromosomes, impacting their functionality. In the environmentally crucial Roseobacter group, T4SS genes vary in genomic locations, raising questions about their functional impact.

Conjugation, a form of HGT, is suggested to contribute significantly to the ecological success of Roseobacters, known for diverse metabolic capabilities and symbiotic interactions, especially with algal hosts. Algal exudates, influencing bacterial physiology, may act as signals promoting bacterial HGT.

Many Roseobacters interact with algal hosts, benefiting from algae's nutrient-rich exudates in the nutrient-poor ocean. This proximity supports nutrient flux for planktonic bacteria. Algal exudates impact bacterial physiology and interactions, promoting horizontal gene transfer (HGT) through bacterial proximity and attachment. Our study explores Roseobacter conjugation in the ecological context of the algal host *Emiliania huxleyi*. We utilized Roseobacter species identified in algal samples, testing their ability to conduct conjugation and examining the influence of T4SS genomic location. Additionally, we investigated the impact of algal exudates on bacterial conjugation, focusing on T4SS-encoding gene expression and DNA transfer.

This study explored Roseobacter conjugation in the context of an algal host, using *Emiliania huxleyi*. While a chromosome-encoded T4SS did not lead to successful conjugation, a plasmid-encoded T4SS functioned. Surprisingly, expression of plasmid-encoded T4SS genes did not increase in response to algal exudates, yet conjugation efficiency and plasmid transfer improved. This suggests a connection between bacterial response to an algal host and an increased likelihood of successful conjugation. The difference in functionality of a plasmid-encoded, or a chromosomally encoded T4SS sparked my interest and led to the project I'm going to show you now!'

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

Imagine bacteria as tiny living beings with small instruction manuals inside them, guiding how they grow and function. Sometimes, these bacteria share parts of their instruction manuals with each other. This sharing, called Horizontal Gene Transfer (HGT), helps them adapt to different challenges.

Now, one way bacteria share information is through something called the type IV secretion system (T4SS). It's like a tiny delivery system that allows bacteria to pass on their instruction manuals to other bacteria nearby. Some bacteria have this system on small circular structures called plasmids, while others have it in their main instruction manual (chromosome).

In a specific group of bacteria called Roseobacters, we found that the T4SS genes are in different places in their instruction manuals. One interesting thing about Roseobacters is their interactions with algae, like tiny plant-like organisms in the ocean. These bacteria benefit from the nutrients that algae release, helping them grow. The study looked at how these bacteria interact with algae, focusing on the T4SS.

We tested different Roseobacter species to see how they share information, and found that the T4SS on plasmids works well, while the one on the chromosome (main instruction manual) doesn't work as effectively.

Surprisingly, the bacteria's response to algae didn't make the T4SS on plasmids work better, but the bacteria still shared information more efficiently. This suggests that the way bacteria react to algae somehow helps them share their instruction manuals better.

So, this study explored how bacteria, specifically Roseobacters, share information in the context of their interaction with algae. The differences in how the plasmid and main instruction manual versions of T4SS work caught the our attention and inspired the project I'm showing next.

### Defining a research question and approach
Seeing as there's a functional difference between these systems depending on their encoding location, we defined our research question as 'What is the difference between chromosomally or plasmid encoded T4SS and can it explain conjugation ability?'

We began approaching this question experimentally and planned designs of several mutant strains, however, technical difficulties and time limits of my studies made us recalculate. 

I've decided to move on with a bioinformatic approach, focusing on data analysis in order to address the question on a larger scale by collecting data from numerous bacterial strains. The first step would be to create a dataset.

### Data Retreival and Handeling
#### Data Retreival
The first step was to gather all relevant data. We started by mapping out all the relevant genes associated with our system on [KEGG](https://www.genome.jp/kegg/). Next, we produced function profiles listing the number of copies of each gene per bacterial scaffold using [JGI's IMG/MER database](https://img.jgi.doe.gov/cgi-bin/mer/main.cgi) and matching with the unique IDs we previously gathered. Additionally, we downloaded all protein sequences files.

Retrieval of protein sequences had to be automated using the Selenium library in Python due to the large quantity of sequences (over 6,000). The script interacts with [JGI's IMG/MER interfaces](https://img.jgi.doe.gov/cgi-bin/mer/main.cgi) for genomic data.

In total, we gathered several thousands of lines of data, and several thousands of protein sequences to analyze.

#### Data Cleaning and Transformation
Tables containing function profiles had to be merged with metadata tables using R and the dplyr package in R. Cleaning the data included renaming mislabeled columns, treating missing data with NA and overall reorganization of the dataset.

Protein sequences files also required attention throughout the pipeline, mainly requiring text manipulation on file names. This was done using linux and python.

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
Beyond analyses done using R, designated tools for sequence analyses were used in this work. Web-based apps like [InterProScan](https://www.ebi.ac.uk/interpro/), for classification of protein families. [BLAST](https://blast.ncbi.nlm.nih.gov/Blast.cgi), a sequence alignment tool. And other offline, linux based applications as [MAFFT sequence alignment program](https://mafft.cbrc.jp/alignment/server/) and [PHYLIP program suite, for phylogenetic analyses](https://phylipweb.github.io/phylip/).

### Results
#### Target genes' distribution in Roseobacters reveals missing pieces
Even before we deal with our question directly, exploring the data and getting to know it reveals lots of interesting observations and generate more questions.

Due to the large amount of data, and since we're now looking into the distribution of genes I thought the best way to visualize it would be to show the gene distribution on a heatmap. 

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/t4ss/big_heatmap.png" title="Type IV secretion system gene distribution in Roseobacters" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
  Gene distribution heatmap in Roseobacters. The columns present genes, rows correspond to operons of specific strains. The rightmost column shows the predicted encoding location (plasmid or chromosome). Colors in the body of the table the indicate gene copy numbers. Rows are clustered by encoding loci.
</div>

The first noticeable anomaly is the absence of VirB1 genes. What's not shown here is how VirB7 is missing completely, and therfore is not plotted. The literature isn't conclusive on these genes' importance for conjugation. Some suggest they're essential, while others argue they're dispensable. However the functions their said to perform may be critical for conjugation. Given these extreme findings, I questioned the validity of the data. To perform a sanity check, I conducted a thorough analysis of our model strains.

##### Thorough (t4sslayout)

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/t4ss/T4SSlayout.png" title="Schematic T4SS operon layout for P. inhibens strains P72 and DSM 17395" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
  Schematic T4SS operon layout for P. inhibens strains P72 and DSM 17395. A.  Layout of P. inhibens P72 pP72b operon. B. Layout of P. inhibens P72 pP72e operon. C. Layout of P. inhibens DSM 17395 operon.
</div>


#### unique pOTUs 

<div class="row justify-content-center">
    <div class="col-sm-7 mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/t4ss/uniquePOTUplot.png" title="Unique pOTUs abundance in Roseobacters" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
  Unique pOTUs abundance in Roseobacters. X axis shows how many times a unique pOTU is found across all Roseobacter genomes. Y axis shows the number of unique pOTUs (also indicated above each bar).
</div>

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/t4ss/pOTU_heatmap.png" title="VirB/D operon genes distribution in Roseobacters" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
  VirB/D operon genes distribution in Roseobacters. A subset data for pOTUs appearing in more than 6 Roseobacter genomes was used to generate a heatmap. Columns present genes, rows correspond to strains. Colors of the heatmap indicate the copy number for each gene (0-2, see legend on the right). Rightmost column (pOTU) shows the classification of plasmid OTUs.
</div>
#### Sequences encoded on chromosomes are distinct from sequences encoded on plasmids

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/t4ss/virB8tree.jpg" title="virB8 protein maximum likelihood tree" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
  virB8 protein maximum likelihood tree. X axis presents branch length in arbitrary units, Y axis shows different taxa. Yellow markers represent T4SS operons encoded on chromosome, blue markers stands for T4SS operons encoded on plasmid. Black arrows mark instances of chromosomal sequences clustered in plasmid-encoded-dominant clusters. Trees were generated using sequence alignment analyzed by PHYLIP proML and colored manually. 
</div>

### Discussion & Conclusions

### References

