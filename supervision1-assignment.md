---
layout: default
title: Assignment 1
nav_order: 3
---

# Assignment for Supervision 1
**Submission Date**: Before Supervision 2

## Instructions
1.  Please download and install QGIS standalone install version according to your platform:[link](https://qgis.org/en/site/forusers/download.html)
2.  Read through the tasks carefully. You may face problems if you overlook any of the steps.
3.  Remember to save the QGIS document regularly. 
4.  Save all the files used or prepared in your assignment (kml, shapefiles, map document, etc.).
5.  Go through the tutorial on converting spreadsheet or csv file to shapefile using QGIS:[link](https://www.qgistutorials.com/en/docs/importing_spreadsheets_csv.html)
6.  All figures in the assignment are for illustration purpose only and do not necessarily depict the actual data

Note: functions and filename are `highlighted` in this document.


## Assignment overview
In this exercise, you will familialise youself with basic features of QGIS software and geospatial data processing.
Extract the wards in the Cambridge city area using the Cambridgeshire data. After that, you will link the population data to the respective wards, and compute population density of each ward. You will also examine other datasets to assess the number of car parks in Cambridge city, as well as in a specific ward. Lastly, you will make a map with essential elements in the Layout View.

By the end of this exercise, you will be able to import shapefile data using QGIS, extract data from a larger dataset through selection by expression, spatially join tabular data to the shapefile, delete field from attribute table of a shapefile, use calculate geometry and field calculator tools, use the dissolve function, and use the select by location tool. 
Data required:
1.  Cambridgeshire district wards (polygon)
2.  Cambridgeshire population (table)

Tasks
1.  Download ‘District Wards’ data (shapefile) of Cambridgeshire from:
http://www.cambridgeshire.gov.uk/info/20082/open_data/150/open_data/2
Note: You need to unzip the contents of zip file to a folder before working.
2.  Open attribute table of `Cambridgeshire layer` and `Select features using an expression` in QGIS, create a new shapefile for the wards of Cambridge City. This shapefile will include these wards: Abbey, Arbury, Castle, Cherry Hinton, Coleridge, East Chesterton, King's Hedges, Market, Newnham, Petersfield, Queen Edith's, Romsey, Trumpington and West Chesterton. Name this file as `Cam_City.shp’.
Hint: Use Export Data command to export the data to a new shapefile. 
![](#statics/Assignment1_select.png)

3.  Download Cambridge population estimates data 2015 (csv) from:[Cambridge shire Insights Data](https://data.cambridgeshireinsight.org.uk/dataset/2015-based-population-and-dwelling-stock-forecasts-cambridgeshire-and-peterborough-0)

4.  Open it in excel and comprise only one sheet, containing five columns, Ward Code, Ward name, Y2011, Y2016 and Y2021.

![](statics/Assignment1_pop.png)

5. import comprised csv file into QGIS.

**Question A: Which ward has the highest and lowest population in 2011, 2016 and 2021? Tabulate and also write respective population.**

5.  Right-click the layer and click properties option. Use the `Join` function on the side to join the population data in excel file created in Task 2 to the Cam_City shapefile that was created in Task 1 above. Once this is done, the Attribute Table of Cam_City shapefile should show the Ward name and the population of each ward in 2011, 2016 and 2021.
Note: join function is a extremly useful function in GIS software. It can link your tabular data and spatial data together. Make sure both spatial layer and tabular data have at least one same column can be used as identical id.
6.  Use the Export Data command to create a new shapefile, name it as `Cam_City_Pop.shp’. The Attribute Table of this shapefile must be showing the ward names as well as the corresponding population in 2011, 2016 and 2021.
7.  Some of the fields in the Cam_City_Pop shapefile are not needed for the assignment. Therefore, delete the following fields:
```
Wd15cd\Wd15nm\Wd15nmw\Ward_code\Objectid\lad15cd\st_lengths\st_areasha
```
![](statics/Assignment1_join.png)
8.  In the Attribute Table of Cam_City_Pop shapefile, add a new field named ‘Sq_Km’. Remember to set the data type of this field to ‘Float’, Precision = 4 and Scale = 2. We will compute the area of each ward in km2 (sq kilometre). Compute the area using ‘Calculate Geometry’ tool (right click after choosing the new field).
**Question B: Why did we use ‘Float’ as the data type while adding the field ‘Sq_Km’ in the Attribute Table of Cam_City_Pop shapefile? What is the purpose of setting the ‘Precision’ and ‘Scale’ values?**

**Question C: Which ward is the largest and smallest in terms of area? Also note their areas in km2.**

9.  In the Attribute Table of Cam_City_Pop shapefile, add three new fields. Remember to set the data type as ‘Float’, Precision = 7 and Scale = 2.
a.  Pop_Den11 
b.  Pop_Den16 
c.  Pop_Den21 


10. Compute population density (persons/km2) of 2011, 2016 and 2021 using ‘Field Calculator’ tool (right click after choosing newly created field)  to store in the Pop_Den11, Pop_Den16 and Pop_Den21 fields, respectively.
![](statics/Assignment1_field.png)
![](statics/Assignment1_field_output.png)

**Question D: Which ward has the highest and lowest population densities in 2011, 2012 and 2013? Tabulate and also write respective population densities.**
