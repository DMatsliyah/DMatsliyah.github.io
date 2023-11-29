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

This project is an M.Sc research project that was part of my masters' thesis, I was under the supervision of Dr. Einat Segev and have also been mentored by PhD student Yemima Duchin Rapp, in the Plant & Environmental Sciences department of the Weizmann Institute of Science. Parts of my work were featured in [this recent paper which was submitted not long ago](https://www.biorxiv.org/content/10.1101/2023.11.14.567099v2) so I won't be expanding too much on that here, but I will be giving some context and introduction before diving into the data analysis driven portion of the project. Also feel free to skip ahead to the '' section to get right into the data.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/t4ss/barentsbloom.jpg" title="Phytoplankton bloom, Barents Sea." class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Phytoplankton bloom, Barents Sea. August 3rd, 2023. The image above was acquired by the Moderate Resolution Imaging Spectroradiometer (MODIS) on NASA's Terra satellite.
</div> 


### Introduction


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/gis_sea/Tuvalu_high_tide.jpg" title="Tuvaluans watch as the high tide inundates their island home on funafuti due to global warming induced sea level rise. Photo: Ashley Cooper / SCIENCE PHOTO LIBRARY." class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Tuvalu is an example of an area that is in risk due to rising sea levels. Photo: Ashley Cooper / SCIENCE PHOTO LIBRARY.
    
</div>

### Materials and Methods


### Results
#### Sea Level Graphs from the Israeli National Mapping Agency Data

<div class="row justify-content-center">
    <div class="col-md mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/gis_sea/sealevel3.png" title="Graph 3: A panel of graphs showing the sea level (blue) and its change (red) in meters" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
Graph 3: A panel of graphs showing the sea level (blue) and its change (red) in meters. Each graph displays data from the winter of each year between 2009 and 2015. The data shown is from October to March every year, except for the winter of 2010/2011 where there was no data between January and March. Unusual changes in the panel indicate storms and extreme events.
</div>

#### Relevant Tables and Graphs from the 2014 IPCC Report
<div class="row justify-content-center">
    <div class="col-sm-7 mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/gis_sea/ipcc2014.png" title="Graph 4: Historical global change in sea level in relation to the average sea level in the years 1905-2000" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Graph 4: Historical global change in sea level in relation to the average sea level in the years 1905-2000.
</div>


#### QGIS Maps
<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/gis_sea/michmoret_srtm.png" title="Map 1: Areas that may be affected by sea level rise in the west of Emek Hefer" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Map 1: Areas that may be affected by sea level rise in the west of Emek Hefer. Map based on SRTM raster data[9]. Areas colored in orange represent areas that will be damaged by sea level rise of up to 0.5 meters. Areas colored in red represent areas that will be damaged by sea level rise of up to 1 meter. 
</div>

### Discussion & Conclusions

### My thoughts, two years later

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/gis_sea/sealevelEndpic.jpg" title="A Prediction of Rising Sea Levels, Photo by go_greener_oz" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A Prediction of Rising Sea Levels, Photo by go_greener_oz
</div>

### References:
  1. [NASA: Climate Change and Global Warming](https://climate.nasa.gov/). cited February 2nd, 2021 
  2. N. N. Greenwood and A. Earnshaw (1997), Chemistry of the Elements, 2nd ed. p.625, Elsevier.
  3. [Sea Level - AR4 WGI Chapter 10: Global Climate Projections](https://archive.ipcc.ch/publications_and_data/ar4/wg1/en/ch10s10-es-8-sea-level.html). cited February 2nd, 2021
  4. [AR5 Climate Change 2014: Impacts, Adaptation, and Vulnerability - IPCC](https://www.ipcc.ch/report/ar5/wg2/). cited February 2nd, 2021
  5. [Rosen S.D (2004), Assessment of the impact due to sea level rise and wave climate change on the state of the Israeli beaches, in view of the monitoring activities performed by Israel Oceanographic & Limnological Research in Israel and abroad, Beaches 2004, Yrly. J. Isr. Soc. Prot. Nat., pp. 21-28.](http://seashorerosen.com/wp-content/uploads/2014/10/hofim_2004_lr.pdf) cited January 27th, 2021
  6. A. Christodoulou, P. Christidis, and H. Demirel, (2019). Sea-level rise in ports: a wider focus on impacts, Marit. Econ. Logist., vol. 21, no. 4, pp. 482-496, doi: 10.1057/s41278-018-0114-z.
  7. P. D. Bromirski, A. J. Miller, and R. E. Flick, (2012). Understanding North Pacific sea level trends, Eos (Washington. DC)., vol. 93, no. 27, pp. 249-251, doi: 10.1029/2012EO270001.
  8. [Israeli national mapping agency (MAPI) sea level data](https://www.mapi.gov.il/Research/sea_level/info/Pages/seaLvlInfo.aspx). cited January 5th, 2021
  9. [CGIAR-CSI SRTM - SRTM 90m DEM Digital Elevation Database](https://srtm.csi.cgiar.org/). cited January 5th, 2021
  10. MAPI mapping of Michmoret and surrounding area, courtesy of Dr. Yair Suari.
  11. [NOAA - Intro to Storm Surge](https://www.nhc.noaa.gov/surge/surge_intro.pdf). cited January 11th, 2021
