RM03 Spatial Analysis and New Technologies in Planning
Assignment for Supervision 1
Submission Date: before Supervision 1
The word limit of assignment is 2000 with up to 4 graphs included. Each graph will be count as 250 words. The assignment is divided in two parts, first part is expected to discuss the method you choose and 
Instructions
1.  Please download and install QGIS standalone install version according to your platform: https://qgis.org/en/site/forusers/download.html
2.  Read through the tasks carefully. You may face problems if you overlook any of the steps.
3.  Remember to save the QGIS document regularly. 
4.  Save all the files used or prepared in your assignment (kml, shapefiles, map document, etc.).
5.  Go through the tutorial on converting spreadsheet or csv file to shapefile using QGIS: https://www.qgistutorials.com/en/docs/importing_spreadsheets_csv.html
6.  All figures in the assignment are for illustration purpose only and do not necessarily depict the actual data

Assignment overview
In this exercise, you will extract the wards in the Cambridge city area using the Cambridgeshire data. After that, you will link the population data to the respective wards, and compute population density of each ward. You will also examine other datasets to assess the number of car parks in Cambridge city, as well as in a specific ward. Lastly, you will make a map with essential elements in the Layout View.

By the end of this exercise, you will be able to convert kml data to shapefile using ArcMap, extract data from a larger dataset through selection by attributes, spatially join tabular data to the shapefile, delete field from attribute table of a shapefile, use calculate geometry and field calculator tools, use the dissolve function, and use the select by location tool. 
Data required:
1.  Cambridgeshire district wards (polygon)
2.  Cambridgeshire population (table)
3.  Car Parks (point)

Tasks
1.  Download ‘District Wards’ data (shapefile) of Cambridgeshire from:
https://data.cambridgeshireinsight.org.uk/dataset/wardselectoral-divisions/resource/a5da0436-1142-48a9-8d82-d070fae138aa 
Note: You need to unzip the contents of zip file to a folder before working.

2.  Using ‘Select by Attributes’ in ArcMap, create a new shapefile for the wards of Cambridge City. This shapefile will include these wards: Abbey, Arbury, Castle, Cherry Hinton, Coleridge, East Chesterton, King's Hedges, Market, Newnham, Petersfield, Queen Edith's, Romsey, Trumpington and West Chesterton. Name this file as ‘Cam_City.shp’.
Hint: Use Export Data command to export the data to a new shapefile.
      

3.  Download Cambridge population estimates data 2015 (csv) from:
https://data.cambridgeshireinsight.org.uk/dataset/2015-based-population-and-dwelling-stock-forecasts-cambridgeshire-and-peterborough-0 

4.  Open it in excel and comprise only one sheet, containing five columns, Ward Code, Ward name, Y2011, Y2016 and Y2021.
 

Question A: Which ward has the highest and lowest population in 2011, 2016 and 2021? Tabulate and also write respective population.

5.  Use the ‘Join’ function in ArcMap to join the population data in excel file created in Task 4 to the Cam_City shapefile that was created in Task 2 above. Once this is done, the Attribute Table of Cam_City shapefile should show the Ward name and the population of each ward in 2011, 2016 and 2021.

6.  Use the Export Data command to create a new shapefile, name it as ‘Cam_City_Pop.shp’. The Attribute Table of this shapefile must be showing the ward names as well as the corresponding population in 2011, 2016 and 2021.

7.  Some of the fields in the Cam_City_Pop shapefile are not needed for the assignment. Therefore, delete the following fields:
Wd15cd\Wd15nm\Wd15nmw\Ward_code\Objectid\lad15cd\st_lengths\st_areasha

 

8.  In the Attribute Table of Cam_City_Pop shapefile, add a new field named ‘Sq_Km’. Remember to set the data type of this field to ‘Float’, Precision = 4 and Scale = 2. We will compute the area of each ward in km2 (sq kilometre). Compute the area using ‘Calculate Geometry’ tool (right click after choosing the new field).

Question B: Why did we use ‘Float’ as the data type while adding the field ‘Sq_Km’ in the Attribute Table of Cam_City_Pop shapefile? What is the purpose of setting the ‘Precision’ and ‘Scale’ values?

Question C: Which ward is the largest and smallest in terms of area? Also note their areas in km2.

9.  In the Attribute Table of Cam_City_Pop shapefile, add three new fields. Remember to set the data type as ‘Float’, Precision = 7 and Scale = 2.
a.  Pop_Den11 
b.  Pop_Den16 
c.  Pop_Den21 


10. Compute population density (persons/km2) of 2011, 2016 and 2021 using ‘Field Calculator’ tool (right click after choosing newly created field)  to store in the Pop_Den11, Pop_Den16 and Pop_Den21 fields, respectively.
 

 

Question D: Which ward has the highest and lowest population densities in 2011, 2012 and 2013? Tabulate and also write respective population densities.

11. Use the ‘Dissolve’ function in ArcToolbox to merge the spatial boundaries of all the wards in Cam_City_Pop shapefile to obtain the boundary of Cambridge City. Name this new file as ‘Cam_Boundary.shp’. Change the symbology of Cam_Boundary.shp (without fill, 1 outline width, black color).
Hint: Use help to understand the function of Dissolve tool. You will need one field in the attribute table of Cam_City_Pop.shp. This field should contain same values for all the wards. Then use this attribute in the Dissolve function so that it spatially merges all the wards.
 

12. Download ‘Car Parks’ data (kml) of Cambridgeshire from: 
https://data.cambridgeshireinsight.org.uk/dataset/car-parks/resource/ea299dcb-ff39-4e0c-ae76-99076e7bb071


13. Convert the kml file to shapefile in ArcMap and name it ‘Car_Parks’.
Hint: Use the ‘KML To Layer (conversion tool’) in ArcToolbox for this purpose. Get some help from internet. 
 

14. Using the ‘Select by Location’ tool, select the ‘Car_Parks’ that are within the boundary of Cambridge City (Cam_Boundary.shp). Then, create layer from selected features as ‘Cam_Car_Parks’ and change symbol by searching ‘Parking’ in symbol selector。
 

Question E: How many parks are there in Cambridge city?

15. Using the ‘Select by Location’ tool, select the parks that are within the boundary of ‘Market’ ward.
Hint: You will use the Cam_City_Pop.shp for this purpose.

Question F: How many car parks are there in the ‘Market’ ward? Also note the names of these car  parks.

16. Final task is to present the data in the form of a map. Switch to Layout View (Menu Bar -layout view) and remember to show the basic map elements such as map title, north arrow, scale, legend and map description (Menu Bar-Insert). 
        

Question H: Prepare a map that presents the following information:
   Cambridge ward boundaries with graduated-colour-coded 2016 population density
   Car parks within the boundary of Cambridge
   Add symbols and labelling wherever necessary
   Export the map as TIFF file.
Note: if you want, please goes an extra mile by exploring and justifiably using data and/or tools other than those mentioned in this exercise


 


