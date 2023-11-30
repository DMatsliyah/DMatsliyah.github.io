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
    <div class="col-sm mt-md-0">
        {% include figure.html path="assets/img/projects/t4ss/function_profile_cleaning.png" title="Function profile data" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-md-0">
        {% include figure.html path="assets/img/projects/t4ss/metadata_cleaning.png" title="Genomic metadata" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
  Lots of raw data to handle!
</div>

#### Tools and methods used for analysis
Beyond analyses done using R and 
Include R, Python, Linux and linux based tools (PHYLIP, sequence alignment and such). mention online domain analyses services very briefly in non-biological manner.

### Results
#### Copy from thesis
#### Yes that includes the heatmap. I don't know how it will fit though
#### and such and such

### Discussion & Conclusions

### References

