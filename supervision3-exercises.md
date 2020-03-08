---
title: "Supervision 3"
nav_order: 8
nav_exclude: false
search_exclude: true
---

# Supervision 3 (12-13 March, 2020)

### Instructions
1. Read through the instruction carefully. You may face problems if you overlook any of the steps.
2. The instruction for data collection via APIs is written in [Google Colab](https://colab.research.google.com/notebooks/intro.ipynb#recent=true), a free jupyter environment that requires no setup to use and runs python entirely in the cloud. You need log in with your **Google Account** to use this free platform. If you do not have Google Account previously, please apply a new account via this [link](https://accounts.google.com/signup/v2/webcreateaccount?hl=en&continue=https%3A%2F%2Fmyaccount.google.com%2Fintro&flowName=GlifWebSignIn&flowEntry=SignUp) before the supervision. Know more about Google Colab, please check this [link](https://research.google.com/colaboratory/faq.html).
3. If you do not have **Twitter account**, please apply one via this [Twitter Signup](https://twitter.com/i/flow/signup)

Note: functions and filename are `highlighted` in this document.

### Supervision overview
In this exercise, you will familiarise yourself with collect data via Application programming interface(APIs), spatial visualization with collected data and creating a formal map on QGIS. The first two exercises will be practiced on Google Colab and the last exercise will be finished in QGIS.


# 1. Collect Tweets via API
> Please click this button below to move to Google Colab to start the first two exercises. Once open the colab, please save a copy to your own Google Drive.    
> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hn303/CamLandEc-RM03/blob/master/supervision3-v3.ipynb)

# 2. Sentiment analysis with content of tweets
> Please click this button below to move to Google Colab to start the first two exercises. Once open the colab, please save a copy to your own Google Drive.    
> [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/hn303/CamLandEc-RM03/blob/master/supervision3-v3.ipynb)

# 3. Visualizaton of geo-tagged tweets
Geo-location is another important feature of social media. Location of social media can be used in mobility pattern identification, sentiment detection, emergency management and so on. In emergency management, social media data can be used as crowdsourcing tool to collect real-time information in different effected areas. In this section, we will use tweets with geotagged location to identified the effected areas may suffer flood or storms in the early spring 2020. 
Because of the limted time of supervision, we will use pre-collected data (data collected in a week) to demonstrate how to process and visualize geo-location of tweets. 

### QGIS Project Setup (5 mins)

1. It is suggested to create a folder and name it as `rm03_YourCRSid_sup2`, at your prefered directory on your disk. This folder will be the working directory for the assignment and supervision.

2. In the menu bar, Click `Project` > `New` to create a new QGIS project.
3. Go to `Project` > `Save As` and save as `supervision3.QGZ` to the working directory. 
4. Go to `Project` >  `Properties` and open the `Project Properties` window. 
    - `General` tab: in the general settings, set your working directory as `Project Home`, change the unit for distance measurement you prefer and also display coordinates units.
    - `Metadata` tab: It is suggested to input title, author, creation date and a short abstract in the identification tab.
    - `CRS` tab: this tab provides Coordinate Reference System (CRS) setting for the project file. Here, we choose the projected coordinate system, `OSGB 1936/British National Grid EPSG:27700`. Be aware that CRS setting in the `Project Properties` is just for the project (called `Data Frame setting` in ArcGIS). CRS setting for layers will be introduced later.<br>
Note: after adding `Project home`, you can find `Project Home` directory is showing in the `Browser panel`. It is much easier to locate your data files through this panel.<br>
![](statics/Sup3_crs.png) 
![](statics/Sup3_general.png)
![](statics/Sup3_metadata.png)


### Making heatmap based on their location (5Mins)

- How to import data from spreadsheets and CSV with coordinates?
- How to display coordinates from spreadsheets and CSV in QGIS?
In the raw data of geotagged tweets, there is obvious cluster around London. The reason is that there are more twitter users in London because of large population base. It is inappropriate to directly summarise flood-related tweets within local athorities to identify possible affected areas. We need we use normalization to minimize differences in geotagged tweets based on the population of each local authority. 
- import local authority boundary with population value.
- import geotagged tweets
- join by location while summarising


**Importing tweets file and local authorities boundaries**

1. Download `Census_Merged_Local_Authority_Districts_December_2011_in_Great_Britain` data from: [(link)](https://github.com/hn303/CamLandEc-RM03/blob/master/data/Census_Merged_Local_Authority_Districts_December_2011_in_Great_Britain.zip) {:target="_blank"} and `flood_tweets.csv` data from[(link)](https://github.com/hn303/CamLandEc-RM03/blob/master/data/flood_tweets.csv) into your working directory. Both files should be saved into your working directory. 
2. Import shapefile into your project: Locate this file at your working directory in the Browser Panel and hold the left mouse and drag the Census_Merged_Local_Authority_Districts_December_2011_in_Great_Britain.shp into the map window. Alternatively, you can add vector file through data source manager. Click Open data source manager button on Data source manager toolbar and switch to Vector tab. Choose file as the source type and choose your shapefile in the source path.
3. Navigate to menu bar click `Layer` > `Add Layer` > `Add Delimited Text Layer`. Browse the `flood_tweets.csv` just downloaded and change the layer name to `flood_tweets`. In the section of File Format, choose CSV. In the Geometry Definition section, choose `Point coordinates` and select `Longitude` and `Latitude` fields as X Y fields respectively. Normally the Geometry definition section will be auto-populated if it finds a suitable X and Y coordinate fields. Then choose the right CRS (EPSG:4326 - WGS84) for this file. Finally, click add and you will find a point layer.<br>
![csv](statics/Sup3_csv.png)

**Calculate density of geo-tagged tweets (normalised by population in local authorities)**

- How can we link `Census_Merged_Local_Authority_Districts_December_2011_in_Great_BritainCambridge local services` with `flood_tweets`?

1. Navigate to `Processing` > `Toolbox` and search `Join attributes by location(summary)`. In the prompted window, choose `Cam_Services` as input layer and `Cam_City` as join layer. In the geometric predicate section, choose `intersects`. In the join type section, choose `create separate feature for each located feature (one-to-many)`.<br>
![](statics/Sup3_join.png)
![](statics/Sup3_sum.png)

2. In the Attribute Table of `Joined` layer, click `Open field calculator`. Create another new field named as `tweet_normalised` and set the output field type to ‘Decimal number (real)’, Precision = 10 and Scale = 3. In the expression window, input `text_count * 1000/Pop_2016` and we will compute tweet density, number of flood-related tweets per 1000 people in each local athority. 
![](statics/Sup3_nor.png)

3. Symbolised cambridge map in `Graduated color` by `tweet_normalised`(per 1000 people) column . After choosing color ramp, set `Classes` at 10 in ``Natural Breaks (Jenks)` mode. Click `Classify` button and add all classes.
![](statics/Sup3_symbol.png)


### Using print layout 

**The Layout Manager**

QGIS allows you to create multiple maps using the same map file. For this reason, it has a tool called the Layout Manager.
![](statics/Sup3_layout.png)

1. Click on the `Project` -> `Layout Manager` menu entry to open this tool. You’ll see a blank Layout manager dialog appear.
2. Click the Add button and give the new layout the name of `flood_tweets`.
3. Click OK.
4. Click the Show button.


**Basic Map Composition**

In this example, the composition was already the way we wanted it. Ensure that yours is as well.

1. In the Print Layout window, check that the values under Composition ‣ Paper and Quality are set to the following:
![](statics/Sup3_symbol.png)

2. Now you’ve got the page layout the way you wanted it, but this page is still blank. To add the map, click on the `Add New Map` button: . With this tool activated, you’ll be able to place a map on the page.

3. Click and drag a box on the blank page. The map will appear on the page.

![add_map](statics/Sup3_add_map.png)

4. Move the map by clicking and dragging it around: ![layout](statics/Sup_layout.png)

Note:
- Zoom in and out on the page (but not the map!) by using these buttons ![layout_zoom](statics/Sup3_layout_zoom.png).
- Zoom and pan the map in the main QGIS window. You can also pan the map using the Move item content tool: `move Item Content` ![layout_zoom](statics/Sup3_layout_zoom.png).

Because a Layout in QGIS is part of the main map file, you’ll need to save your main project. Go to the main QGIS window (the one with the Layers panel and all the other familiar elements you were working with before), and save your project from there as usual.

### Adding Map Elements

Now your map is looking good on the page, but your readers/users are not being told what’s going on yet. They need some context, which is what you’ll provide for them by adding map elements. First, let’s add elements.


**Add Scale**
1. Click on this button: label
2. Click on the page, above the map, and a label will appear at the top of the map.
Resize it and place it in the top center of the page. It can be resized and moved in the same way that you resized and moved the map.
3. As you move the title, you’ll notice that guidelines appear to help you position the title in the center of the page.
![scale](statics/Sup3_scale.png)

**Add Legend**
1. Click on this button: `add Legend`
2. Click on the page to place the legend, and move it to where you want it:
![legend1](statics/Sup3_legend.png)

3. Input title (`Legend`) for legend.
4. You can also rename items. Double click legend item to rename.
5. Rename the layers to `Local Authority Boundary` and `Floods Tweets Density (per 1000 people)`. You can also reorder the items.
![legend2](statics/Sup3_legend1.png)

Not everything on the legend is necessary, so let’s remove some unwanted items.

6. In the `Item Properties` tab, you’ll find the `Legend items` panel. Uncheck `Auto update` to enable editing function.
6. Select the `flood_tweets`.
7. Delete it from the legend by clicking the minus button.


**Add North Arrow**
1. Click on this button: ``add picture``
2. Click on the page to place the legend, and move it to where you want it.
3. In the `Item Properties` tab, you’ll find the `Search Directories` panel. Choose the north arrow you prefer.
![arrow](statics/Sup3_north.png)


Adding elements is the basic step for a map. To make a **good** map, you need to do more! Check the [experts' guidence from ESRI](https://www.esri.com/news/arcuser/0911/making-a-map-meaningful.html) illustrating how to make a meaning map by answeing 10 questions. 
![good_map](statics/Sup3_goodmap.png).


**Exporting Your Map**

Finally the map is ready for export! 
1. Find export buttons near the top left corner of the Layout window:
2. Choose `Export as Image`
![map](statics/Sup3_map.png)
