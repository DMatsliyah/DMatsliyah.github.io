---
layout: page
title: "Rising sea levels effects on Israeli coasts"
description: Utilizing R & QGIS to inspect the possible effects of rising sea levels in Israel
img: assets/img/projects/gis_sea/gisCard.jpg
importance: 2
category: Science
giscus_comments: true
toc:
  sidebar: left

---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/gis_sea/gisPage.jpg" title="Bat Galim beach, Haifa. December 2016. Photo: Amir Ezer." class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Bat Galim beach, Haifa. December 2016. Photo: Amir Ezer.
</div>

This project is a B.Sc level GIS project made during 'GIS Data analysis' class, looking into possible damages that could occur with increasing sea levels. Guided by Dr. Yair Suari.


### Introduction

Researchers globally strive to comprehend factors linked to global warming, aiming to devise solutions to mitigate its impact. Global warming, driven by various anthropogenic and biogeochemical factors[^1], results from greenhouse gas emissions and their atmospheric accumulation, influencing Earth's climate variables such as surface temperature, precipitation, humidity, and sea level.

Sea level rise primarily stems from water expansion due to temperature increase and continental glacier melting[^2],[^3]. The 2014 IPCC report forecasts a sea level rise of 25-82 cm in the next century[^4]. In Israel, rising sea levels pose threats beyond flooding, including seawater intrusion, sand erosion, and cliff collapse, intensified by increased extreme weather events[^5],[^6],[^7]. This research aims to assess the impact of sea level rise on Israel's coasts.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/gis_sea/Tuvalu_high_tide.jpg" title="Tuvaluans watch as the high tide inundates their island home on funafuti due to global warming induced sea level rise. Photo: Ashley Cooper / SCIENCE PHOTO LIBRARY." class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Tuvalu is an example of an area that is in risk due to rising sea levels. Photo: Ashley Cooper / SCIENCE PHOTO LIBRARY.
    
</div>

### Materials and Methods

Data and models were collected from official sources, including global sea water levels from NASA's satellite measurements since 1993[^1], historical sea level change data from the 2014 IPCC report[^4], and sea level data from Israel Mapping Office (MPI) for 1996-2020 [^8]. RStudio processed approximately 2.4 million map measurements, determining two sea level rise steps (0.5 and 1 meter) presented on maps.

SRTM raster layers, providing high-quality data, were used for spatial analysis, with an additional raster focused on the fishing trawl area for higher resolution[^9]. QGIS software facilitated digitization, raster analysis, and visual illustration, focusing on the fishing trawler area and Haifa Bay. A raster map for the Emek Hefer area was provided courtesy of Dr. Yair Suari[^10].

### Results
#### Sea Level Graphs from the Israeli National Mapping Agency Data
Plots 1, 2 and 3 are [available here](/assets/files/projects/gis_sea/SeaLevel.zip) in an interactive version together with the raw data and an R script used for the analysis, just click the .html files to open the plots. 

<div class="row justify-content-center">
    <div class="col-md mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/gis_sea/sealevel1.png" title="Graph 1: Sea level (blue) and its change (red) between the years 1996-2020 in meters" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
Graph 1: Sea level (blue) and its change (red) between the years 1996-2020 in meters. This graph reveals seasonal trends with medium resolution.
</div>

<div class="row justify-content-center">
    <div class="col-md mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/gis_sea/sealevel2.png" title="Graph 2: Sea level (blue) and its change (red) in 2013 in meters" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
Graph 2: Sea level (blue) and its change (red) in 2013 in meters. This graph offers high-resolution details of the sea level variations during the year.
</div>

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

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/gis_sea/searisetable.png" title="Forecasts of the change in the global average sea level in the 21st century" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Table 1: Forecasts of the change in the global average sea level in the 21st century in relation to the values in the years 1986-2005, in units of meters.
</div>

<div class="row justify-content-center">
    <div class="col-sm-7 mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/gis_sea/seariseplot.png" title="Forecasts of the average global sea level in the 21st century" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Graph 5: Forecasts of the average global sea level in the 21st century in relation to data from 1986-2005 based on process-based models. The graph presents expected values in the milder RCP2.6 model in blue, and the stricter RCP8.5 model in red, with the average also marked in blue and red, respectively. Minimum and maximum limits are depicted as a colored band.
</div>

#### QGIS Maps
<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/gis_sea/michmoret_srtm.png" title="Map 1: Areas that may be affected by sea level rise in the west of Emek Hefer" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Map 1: Areas that may be affected by sea level rise in the west of Emek Hefer. Map based on SRTM raster data. Areas colored in orange represent areas that will be damaged by sea level rise of up to 0.5 meters. Areas colored in red represent areas that will be damaged by sea level rise of up to 1 meter. 
</div>

<div class="row justify-content-center text-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/gis_sea/michmoret_hires.png" title="Map 2: Areas that may be affected by sea level rise in the west of Emek Hefer" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Map 2: Areas that may be affected by sea level rise in the west of Emek Hefer. Map based on raster data from MAPI. Areas colored in orange represent areas that will be damaged by sea level rise of up to 0.5 meters. Areas colored in red represent areas that will be damaged by sea level rise of up to 1 meter. 
</div>

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/gis_sea/haifa_srtm.png" title="Map 3: Areas that may be affected by sea level rise in Haifa Bay" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
Map 3: Areas that may be affected by sea level rise in Haifa Bay. Map based on SRTM raster data. Purple-colored areas represent areas at sea level and were mapped separately as they indicate regions at sea level, necessitating distinction from the sea itself.  Areas colored in orange represent areas that will be damaged by sea level rise of up to 0.5 meters. Areas colored in red represent areas that will be damaged by sea level rise of up to 1 meter. 
</div>

### Discussion & Conclusions
Graphs 1-3 reveal annual, seasonal, and daily trends. Graph 2 shows moderate sea level elevation during the summer, this increase may be attributed to water expansion. In contrast, data for winter sea level displays faster and more powerful changes. Graph 3, covering multiple winters, emphasizes significant sea level variations during winters. The data reflect sea level and don't account for waves, therefore I chose to model sea level increase with a 0.5 and 1 meter rise on the maps. Wave and storm impact is expected beyond these levels[^11].

The key finding is that existing height maps lack the needed resolution for accurate sea level rise analysis due to centimeter-scale changes. Map 1 vs. Map 2 compares SRTM limitations, even with improved data quality in Map 2. Higher resolution maps are needed in order to perform a reliable analysis, as part of the marked area is misclassified as the sea.

Maps 1 and 2 show less tangible damage along a narrow coast, while Map 3 reveals extensive harm to Haifa's port and navy base. This presents economic and security challenges for Haifa, a vital sea goods entry point, and the largest navy base in the country[^6]. Due to SRTM raster resolution, buildings in Haifa port and the naval base were manually classified partly at sea level.

In conclusion, inevitable sea level rise foresees considerable damage. Proactive preparation is crucial. While satellite altimetry is effective, the discussion emphasizes the need for focused mapping, higher resolution tools, or technological advancements for precise risk assessment. Economic and security implications underscore the urgency of preparedness efforts.

### My thoughts, three years later
I've been re-reading and editing this project now (November 2023) to upload as part of my portfolio and I made some interesting new discoveries.

At the time of writing the project, high resolution maps of Israel were unavailable due to the [Kyl-Bingaman Amendment](https://en.wikipedia.org/wiki/Kyl%E2%80%93Bingaman_Amendment), limiting resolution to over 2 meters per pixel. something I was not aware of. However, while going back to this project I found out that this law was changed, with the new restriction set at 40 centimeters. Today, higher resolution maps of Israel are already available. I wonder what the data would say now :thinking:

<div class="row justify-content-center">
    <div class="col-sm mt-3 mt-md-0 text-center">
        {% include figure.html path="assets/img/projects/gis_sea/sealevelEndpic.jpg" title="A Prediction of Rising Sea Levels, Photo by go_greener_oz" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A Prediction of Rising Sea Levels, Photo by go_greener_oz
</div>

### References
  [^1]: [NASA: Climate Change and Global Warming](https://climate.nasa.gov/). cited February 2nd, 2021 
  [^2]: N. N. Greenwood and A. Earnshaw (1997), Chemistry of the Elements, 2nd ed. p.625, Elsevier.
  [^3]: [Sea Level - AR4 WGI Chapter 10: Global Climate Projections](https://archive.ipcc.ch/publications_and_data/ar4/wg1/en/ch10s10-es-8-sea-level.html). cited February 2nd, 2021
  [^4]: [AR5 Climate Change 2014: Impacts, Adaptation, and Vulnerability - IPCC](https://www.ipcc.ch/report/ar5/wg2/). cited February 2nd, 2021
  [^5]: [Rosen S.D (2004), Assessment of the impact due to sea level rise and wave climate change on the state of the Israeli beaches, in view of the monitoring activities performed by Israel Oceanographic & Limnological Research in Israel and abroad, Beaches 2004, Yrly. J. Isr. Soc. Prot. Nat., pp. 21-28.](http://seashorerosen.com/wp-content/uploads/2014/10/hofim_2004_lr.pdf) cited January 27th, 2021
  [^6]: A. Christodoulou, P. Christidis, and H. Demirel, (2019). Sea-level rise in ports: a wider focus on impacts, Marit. Econ. Logist., vol. 21, no. 4, pp. 482-496, doi: 10.1057/s41278-018-0114-z.
  [^7]: P. D. Bromirski, A. J. Miller, and R. E. Flick, (2012). Understanding North Pacific sea level trends, Eos (Washington. DC)., vol. 93, no. 27, pp. 249-251, doi: 10.1029/2012EO270001.
  [^8]: [Israeli national mapping agency (MAPI) sea level data](https://www.mapi.gov.il/Research/sea_level/info/Pages/seaLvlInfo.aspx). cited January 5th, 2021
  [^9]: [CGIAR-CSI SRTM - SRTM 90m DEM Digital Elevation Database](https://srtm.csi.cgiar.org/). cited January 5th, 2021
  [^10]: MAPI mapping of Michmoret and surrounding area, courtesy of Dr. Yair Suari.
  [^11]: [NOAA - Intro to Storm Surge](https://www.nhc.noaa.gov/surge/surge_intro.pdf). cited January 11th, 2021
