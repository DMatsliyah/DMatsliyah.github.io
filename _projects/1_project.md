---
layout: page
title: "Rising sea levels effects on Israeli coasts"
description: Utilizing R & QGIS to inspect the effect of rising sea levels in Israel
img: assets/img/projects/gis_sea/gisCard.jpg
importance: 2
category: Science
giscus_comments: true

---

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/gis_sea/gisPage.jpg" title="Bat Galim beach, Haifa. December 2016. Photo: Amir Ezer." class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Bat Galim beach, Haifa. December 2016. Photo: Amir Ezer.
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/gis_sea/gisPage.jpg" title="Bat Galim beach, Haifa. December 2016. Photo: Amir Ezer." class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Bat Galim beach, Haifa. December 2016. Photo: Amir Ezer.
</div>

This project is a B.Sc GIS project looking into possible damages that could occur with increasing sea levels. Guided by Dr. Yair Suari.

### Introduction

Researchers worldwide are actively engaged in understanding the factors associated with global warming, with the goal of devising solutions to mitigate its impact. Global warming is a phenomenon driven by various interrelated anthropogenic and biogeochemical factors[^1]. A significant contributor to this warming is the emission of greenhouse gases and their accumulation in the atmosphere. This, in turn, affects the flux of solar radiation on Earth, influencing factors such as surface temperature, precipitation, humidity, and sea level.

The primary cause of sea level rise is the expansion of water due to an increase in temperature, causing water molecules to move apart. Additionally, the melting of continental glaciers contributes to this rise[^2][^3]. The Intergovernmental Panel on Climate Change (IPCC), an international body composed of researchers, publishes periodic reports that constitute a consensus on the Earth's climate situation. The 2014 IPCC report presented forecasts suggesting that the sea level will rise between 25-82 cm in the next hundred years[^4].

In Israel, the consequences of rising sea levels extend beyond flooding, encompassing dangers such as seawater intrusion into groundwater, sand erosion, and cliff collapse. These events are expected to become more frequent due to the increased frequency of extreme weather events resulting from global warming[^5]. As the population near the coast continues to grow, the number of potential victims is expected to rise each year. Beyond direct property damage, coastal activities such as water desalination may be harmed, affecting both civilians and industries far from the coast. Studies also indicate potential damage and disruption to various anchorages and ports due to the rise of sea levels[^6][^7].

Hence, this research seeks to answer the question, 'What is the effect of sea level rise on the coasts of Israel?'

### Materials and Methods

To conduct this research, data and models were collected from several official sources. Data regarding global sea water levels, obtained through satellite measurements, were downloaded from the NASA website, the American space agency known for its monitoring and research in various fields[^1]. Advanced satellites enable the measurement of various parameters, such as sea level, recorded by NASA satellites since 1993. Satellite altimetry is recognized as a high-quality technique for measuring Earth's sea level with a high degree of accuracy.

Historical sea level change data and reliable forecasts were extracted from the latest IPCC report in 2014[^4]. As mentioned in the introduction, the IPCC is considered a reliable source of data on this subject. This study presents data from both the strictest and most lenient models from the report to offer a comprehensive picture.

For a comprehensive assessment of the situation on the coasts of Israel, particularly in extreme situations such as storms, sea level data from the Israel Mapping Office (MPI) for the years 1996 to 2020 were downloaded[^8]. The MPI is a government body responsible for sea level measurements, taken automatically every five minutes at various stations along the country's coasts. These measurements use level gauges calibrated to an elevation point in the national balance network, ensuring the reliability of the collected data. To address variations in reporting among stations, a combination of data from Tel Aviv, Jaffa, and Ashdod coastal stations was used due to their proximity and representativeness.

During the data processing phase, which involved approximately 2.4 million lines of map measurements, the RStudio software was employed. The attached code in the appendix outlines the steps taken during this phase. Two steps for sea level rise (0.5 and 1 meter) were determined from this data and will be presented on the map.

To facilitate spatial analysis, raster layers from SRTM, a high-quality source providing data from NASA satellites that have been analyzed and processed to improve quality and fill gaps, were downloaded[^9]. However, challenges arose in distinguishing between individual centimeters due to the resolution of the raster. To address this, an additional raster focused on the fishing trawl area, derived from the map provided by Dr. Suari, was utilized. This raster is expected to provide higher resolution due to point mapping.

Digitization tools and the Raster Calculator tool in QGIS software were employed to extract specific elevation areas from the rasters, later colored for visual illustration. The study is concentrated on the fishing trawler area and Haifa Bay.

### Results

### Discussion & Conclusions
First, an analysis of annual, seasonal, and even daily trends, such as tides, is evident in Graphs 1-3. Graph 2 highlights that while the sea level is higher in the summer, likely due to water expansion, the changes are more moderate. In contrast, winter exhibits faster and more powerful changes. Graph 3, aggregating several winters, emphasizes significant changes in sea level. It is important to note that these values reflect the sea level rather than wave height, justifying the presentation of a rise of up to 0.5 and 1 meter on the maps, respectively. The impact of waves and storms is expected to affect areas higher than these levels[^11].

The primary conclusion drawn from the results is that existing height maps lack the resolution required for an accurate analysis of sea level rise, given the magnitude of changes in tens of centimeters. A comparison between Map 1 and Map 2 illustrates the limitations of SRTM data, considered of high quality, in providing detailed information relative to Mapi mapping. Even in Map 2, displaying improved data quality, there is room for enhancement, as part of the marked area is inaccurately classified as the sea itself.

While damage in Maps 1 and 2 is less tangible, affecting a relatively narrow coastal stretch, Map 3 reveals extensive damage, including significant harm to the port of Haifa, the navy base, and adjacent areas. This poses economic challenges for the Haifa port, a critical entry point for sea goods, and has economic and security implications for the largest navy base in the country. Notably, due to the resolution of the SRTM raster, some buildings in Haifa port and the naval base were manually digitized and classified partially at sea level.

In conclusion, sea level rise appears inevitable in the near term, foreseen to cause considerable damage. Proactive preparation is crucial to minimize the extent of this damage. While satellite altimetry proves effective, the discussion highlights the need for focused mapping, higher resolution tools, or technological advancements to measure risk areas with greater precision and conduct more accurate analyses. The economic and security ramifications of sea level rise underscore the urgency of such preparedness efforts.


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

You can also put regular text between your rows of images.
Say you wanted to write a little bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, *bled* for your project, and then... you reveal its glory in the next row of images.


<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>


The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}
```html
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
```
{% endraw %}
