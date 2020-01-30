# Supervision 2

## Instructions
1. Read through the instruction carefully. You may face problems if you overlook any of the steps.
2. Remember to save the QGIS document regularly. 

Note: functions and filename are `highlighted` in this document.

## Supervision overview
In this exercise, you will familiarise yourself with geoprocessing raster data on QGIS software as well as basic features of NetLogo software and how to use the GIS extension to input raster maps. 

### Setup work enviornment (10 mins)
1. Please download and install `NetLogo (6.1.1)` according to your platform. We recommend downloading `Windows (64-bit)`, `Mac OS X`, or `Linux (64-bit)`: [NetLogo Download Page](https://ccl.northwestern.edu/netlogo/6.1.1/
). 
2. It is suggested to create a folder and name it as `rm03_YourCRSid_sup2`, at your prefered directory on your disk. This folder will be the working directory for all datasets and QGIS project file in this supervision.
3. Launch QGIS and NetLogo.

## What are raster data?
•	While vector data use points, lines, and polygons, raster data store information in cells – coded image on a grid/matrix of X columns by Y rows
•	Examples: aerial photography, satellite image, digital elevation model (DEM)…
•	Has fixed pixel dimensions (spatial resolution) which is cell size
•	Formats: generic image formats (bmp, tif, jpeg…), satellite formats (BIL, BIP, BSQ…), geocoded formats (Geotiff, GeoJPG…)…
•	Can hold categorical (codified) or continuous values




Source: Silva (2020)
Preparing raster files for SLEUTH model in NetLogo
1. SLEUTH urban growth model
•	SLEUTH is an urban growth model developed by Keith C. Clarke. SLEUTH stands for slope, land use, exclusion, urban, transportation, and hillshade layer which form the model input (Silva & Clarke, 2002). It originally uses C++ language but it is being translated to NetLogo (Kwon, Silva, Scherer & Clarke, forthcoming).
•	SLEUTH requires one slope, two land-use (if land use change is to be simulated), one exclusion, four urban, three transport, and one hillshade layers with control years as well as calibration (brute force, monte carlo).
•	For the sake of simple exercise, we will prepare four raster maps on QGIS as input layers for SLEUTH model in NetLogo without calibration.
 Source: Clarke (2019)
2. Preparing layers
Downloading dataset: sample data of Sejong, South Korea
•	[Urban_2018.shp](https://googledoc.com)
•	`Exclusion_2014.shp`
•	`Road_2018.shp`
•	`Boundary.shp`
•	`Slope_2014.txt`
Loading vector files on QGIS
•	Open QGIS
•	Layer → Add Vector Layer  → add four shp files (or just drag and drop the files to the blank window)
![](statics/QGIS_start.png) 

Saving QGIS file (qgz)
•	Project → Save → Sup1.qgz. There is no auto-save so save frequently.
 
Sorting layers
•	Drag Boundary layer to the bottom
•	Uncheck all layers except Boundary
 
Changing colour
•	Right-click on Boundary layer → Properties → Symbology (or double-click the color box)
•	Click Simple fill → Change Fill color to black → Change Stroke style to No Pen → OK 
•	Check Urban_2018 layer → double-click the color box
•	Click Simple fill → Change Fill color to white → Change Stroke style to No Pen → OK 
  
•	Uncheck Urban_2018 layer
•	Check Exclusion_2014 layer → double-click the color box
•	Click Single symbol → Categorized
•	Click Column → EXCLUSION
•	Click Classify → Change Legend to 0=non-excluded, 100=excluded
•	Double-click color box of Non-excluded → Simple fill → Change Fill color to black → Change Stroke style to No Pen → OK
•	Double-click color box of Excluded → Simple fill → Change Fill color to white → Change Stroke style to No Pen → OK
•	Delete the third row by pressing the negative sign in the bottom
•	Uncheck Exclusion_2014 layer
•	Check Road_2018 layer → double-click the color box
•	Click Single symbol → Categorized
•	Click Column → road_class
•	Click Classify → Change Legend and color to 0=non-road (black), 25=small road (#404040), 50=medium road (#808080), 75=large road (#3a3a3a), 100=expressway (white) with No Pen
 
Q1. Urban_2018 layer is a combination of land-use data by parcel and building data. Right-click on this layer and Open Attribute Table. How many attributes are there? What is the total number of features?
A1: Four attributes, 94477 features.
Q2. Exclusion_2014 is a combination of river, urban parks and development restriction zone. Right-click on this layer and Open Attribute Table. The attribute “EXCLUSION” is coded into 0 and 100. Click on the number 1 to see this feature highlighted in yellow. What do you think 0 and 100 refer to?
 
A2: 0 = non-excluded, 100 = excluded.
Q3. Right-click on Road_2018 layer and Open Attribute Table. Click the attribute tab of road_class to sort and select all ‘25’s to highlight them in yellow. What do you think 25, 50, 75, 100 refer to?
A3: 25 = small road, 50 = medium road, 75 = large road, 100 = expressway

3. Converting vector to raster (rasterize)
Urban_2018
•	Click and check Urban_2018 layer → Raster → Conversion → Rasterize
•	Field to use for a burn-in value: URBAN → A field value to burn: Not set → Output raster size units: Georeferenced units → Resolution: 30 and 30, Output extent: 211290.7980001302785240, 236760.7980001302785240, 322863.2411839000415057, 359223.2411839000415057 → Nodata value: Not set → Run
Note: The output extent is that of the largest layer. This extent will be given to all raster layers so that they all have the same output extent
•	Right-click on the newly created Rasterized layer → Export → Save As (if you don’t save, these temporary files will disappear next time you open the QGIS file)
•	Output mode: Raw data → Format: GeoTIFF → Filename: Urban_2018 → OK
   
   
Q4. Zoom into the Urban_2018 layer.  You will see that the pixels are in grid. Check the size of the grid by right-clicking on Urban_2018 → Properties. In the information tab, what are the dimensions, origin, and pixel size (set in meters)? In real life, what would be the dimension of this city in kilometers? Double-check on google map to see whether your calculation is correct.
 
A4: Dimensions: X = 849, Y: 1212. Origin: 211291, 359223. Pixel Size: 30, -30. Dimension of this city: (849*30) x (1212*30) = 25,470m x 36,360m =  25.47km x 36.36km

Exclusion_2014
•	Uncheck Urban_2018 layer → click and check Exclusion_2014 layer → Raster → Conversion → Rasterize
•	Field to use for a burn-in value: EXCLUSION → A field value to burn: Not set → Output raster size units: Georeferenced units → Resolution: 30 and 30, Output extent: 211290.7980001302785240, 236760.7980001302785240, 322863.2411839000415057, 359223.2411839000415057 → Nodata value: Not set → Run

Q4. Use the Identify Features button to click on white and black cells of Exclusion_2014 layer.
A4:

4. Generating slope map in percent in raster
Importing DEM data (txt) as delimited text layer 
•	Layer → Add Delimited Text Layer
•	File name: Sejong_DEM, File Format: CSV, Geometry CRS: WGS 84 → Add
•	Note: In general, leave the default setting if unsure.
   
Saving layer as shapefile
•	Right-click on the Sejong_DEM layer → Export → Save Feature As… (if you don’t save as, these temporary files will disappear next time you open the QGIS file)
•	Format: ESRI Shapefile, name: Slope, CRS: WGS 84, Encoding: System → OK
   

Interpolating the xyz 
•	Raster → Analysis → Grid (Inverse Distance to a Power)
•	Point layer: Slope, Weighting power: 2, Z value: z → Run
  
  

Generating slope from interpolated raster
•	Raster → Analysis → Slope
•	Input layer: Interpolated (IDW)
•	Check “Slope expressed as percent”
  

Saving raster with specific extent and resolution
•	Right-click on the raster Slope layer → Save As → Format: GeoTIFF, File name: Slope
•	Extent
- West: 211290.7980001302785240
- South: 322863.2411839000415057
- East: 236760.7980001302785240
- North: 359223.2411839000415057
   

Generating slope from interpolated raster
•	Raster → Analysis → Slope
•	Input layer: Interpolated (IDW)
•	Check “Slope expressed as percent”
 
