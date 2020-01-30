# Supervision 1

## Instructions
1. Read through the instruction carefully. You may face problems if you overlook any of the steps.
2. Remember to save the QGIS document regularly. 

Note: functions and filename are `highlighted` in this document.

## Supervision overview
In this exercise, you will familialise youself with basic features of QGIS software and geoprocessing exercises with vector data and raster data.

### Setup work enviornment (10 mins)
1. Please download and install `QGIS standalone install version` according to your platform: [QGIS Download Page](https://qgis.org/en/site/forusers/download.html). 
2. It is suggested to create a folder and name it as `rm03_YourCRSid_sup1`, at your prefered directory on your disk. This folder will be the working directory for all datasets and QGIS project file in this supervision.
3. Launch QGIS: Start QGIS Desktop and check interface (menu bar, toolbar, brower panel, layer panerl and map window)

Note: if some panels or toolbars are not showing, nevigate to menu bar  `View` > `Panels` or `Toolbars` to switch on.

![](statics/QGIS_start.png)

### QGIS project setup (5 mins)
1. Create new project: In the QGIS – Map view window, click `New`.
2. Save your project: Click `Project` button in `Project Toolbar` and save as `supervision1.QGZ` to the working directory. 
3. Go to `Project` >  `Properties` in menu bar and open the `Project Properties` window. Check following tabs and edit: 
    - `General` tab: in the general settings, set your working directory as `Project Home`, change the unit for distance measurement you prefer and also display coordinates units.
    - `Metadata` tab: It is suggested to input title, author, creation date and a short abstract in the identification tab.
    - `CRS` tab: this tab provide coordinate reference system (CRS) setting for the project file. Be aware that CRS setting in the `Project Properties` is just for the project (called as `Data Frame setting` in ArcGIS). CRS setting for layers will be introduced later.

Note: after adding project home, you can find `Project Home` directory is showing in the `Browser panel`. It is much easier to locate your data files through this panel.
![](statics/QGIS_general.png)![](statics/QGIS_project.png)![](statics/QGIS_crs.png)

### Vector data (30 mins)
1. Download `Cambridge District Wards` data of Cambridgeshire from:[Cambridgeshire Insight Open Data](https://data.cambridgeshireinsight.org.uk/dataset/wardselectoral-divisions/resource/a5da0436-1142-48a9-8d82-d070fae138aa) and save into your working directory.
2. Import shapefile into your project:  Locate this file at your working directory through `browser panel` and hold the left mouse and drag the `Wards_December_2015_Generalised_Clipped_Boundaries_in_Great_Britain.shp` into the map window. Or, you can add vector file through data source manager.
Note: You will beprompted a window to conduct CRS transformation. 
![](statics/QGIS_import.png)
3: Layer ticked then can be found in layer panel. You can turn on and off layer by tick it or not. If you intend to process one layer, please make sure the target layer are ticked and selected with hightlight.

#### Attributes table
- How to open attribute table?
- How to select ploygons only in cambridge from attribute tbale?
1. Select layer in layers penel, click the `open attribute table` in the `Attribut Toolbar`. You will see the attribute table with different fields including `wd15nm` (name for Ward District) and `lad12nm` (name for Local Authority District). 
![](statics/QGIS_table.png)
2. In the attribute table of Cambridgeshire layer and double-click `lad12nm` to sort by value/content. Select all rows whose `lad12nm` value equals `cambridge` (select first one and then press SHIFT on your keyboard while selecting the last one).
![](#statics/QGIS_select1.png)![](#statics/QGIS_select2.png)
3.  Here is an alternative method to select elements precisely: Open attribute table of Cambridgeshire layer and Select features using an expression in QGIS. In the window of expression, input `"lad15nm" = 'Cambridge'` and click select features. 
Note: You don't need to type expression manually, expand `Field and Values` option in the right panel and  double click `lad15nm`. The field name will show in the expression window. Once you select the field `lad15nm`, click `All Unique` button on the right, it will show a list of unique values from the field of `lad15nm`. Double click it to finish the expression.
![](statics/QGIS_select3.png)
4. Once select elements you need, right-click this layer and nevigative to `Export` > `Save Selected Features As`. Name this file as `Cam_City.shp`. This shapefile will include these wards: Abbey, Arbury, Castle, Cherry Hinton, Coleridge, East Chesterton, King’s Hedges, Market, Newnham, Petersfield, Queen Edith’s, Romsey, Trumpington and West Chesterton. 


5. Check other functions in attribute table: `select all`, `invert selection`, `deselect all`

#### Importing Spreadsheets or CSV files
1. Download `Cambridge local services` data of Cambridgeshire from: [Cambridgeshire Insight Open Data](https://data.cambridgeshireinsight.org.uk/dataset/cambridge-local-services/resource/af2c41d1-c8a0-46cf-ab77-ca407732e060) and save into your working directory.
2. Nevigate to menu bar click `Layer` > `Add Layer` > `Add Delimited Text Layer`. Browse the `cambridge-services-geolocated-csv-2-standardized.csv` just dowloaded and change the layer name to `Cam_Services`. In the section of File Format, choose CSV. In the Geometry Definition section, choose `Point coordinates` and select `Longitude` and `Latitude` fields as X Y fields respectively. Normally the Geometry definition secction will be auto-populated if it finds a suitable X and Y coordinate fields. Then choose the right CRS (EPSG: 4277 - OSGB 1936) for this file. Finally, click add and you will find a point layer 
![](statics/QGIS_csv.png)


#### Join layer
- How can we link cambridge local services with district information?
1. Nevigate to `Processing` > `Toolbox` and search `Join  attributes by location`. In the prompted window, choose `Cam_services` as input layer and `Cam_City` as join layer. In the geometric predicate stection, choose `intersects`. In the join type section, choose `create seperate feature for each located feature (one-to-many)`.
![](statics/QGIS_join.png)
2. Check attribute table of `Joined layer` and you will find district information for each service item.

### Digitizing Map Data (10 mins)
#### Basemap and plugins in QGIS
1. Extent the function of your QGIS function with plugins: open `Plugins` > `Manage and Install Plugins` on menu bar. Search `QuickMapServices` and click `Install plugin`. 
Note: if some plugins are not showing, please allow the `experiment` option.
2. After isntalling plugin, you can find `QuickMapServices` function in the `web` section on menu bar. Choose `OSM`-`OSM Standard` and you will add basemap in QGIS.

#### Create features/shapefiles in QGIS

1.  Once you add basemap for your qgis project, you will see a scalable map in the map window.
2.  Zoom in to the Cambridge area to find the location of your college/office.
Note: You computer must be connected to the internet to add basemap as the imagery is fetched from web servers

3.  Create the following three shapefiles using `layer` - `Create Layer` > `New Shapefile Layer`. Remember to assign the `EPSG:27700 - OSGB 1936 / British National Grid` coordinate system (select CRS > filter > Search `OSGB 1936`). Add new fields into `Fields list` with setting data type, length and precision. For instance, add `name` as new field and set length at 15.

4. Select the `my_college/office` layer in layer penel, then open `Toggle editing` and select `Add Point Feature`. After pin a point feature on map winodw, a `Feature Attribute` window will pop up. Input value you want to assign to attributes of this new feature. 
![](statics/QGIS_feature.png)
5. After creating features in map window, click `Toggle Editing` to save the edit.


6.  The following things will be digitized in these three shapefiles:
a.  `My_Route.shp` (Polyline)
b.  `My_PoI.shp` (Point)
c.  `My_Locations.shp` (Polygon)

- `My_Route` – You will digitize a ‘line’ showing your daily route from your house to college/office. You will also add a Field to its Attribute Table to store the ‘distance’ of this path.
- `My_PoI` – You will digitize your ‘points’ of interests (PoI) alongside this route. These may include locations of your favourite restaurants, coffee shops, cash machines, etc. You will add two Fields to its Attribute Table to store the ‘name’ and ‘category’ (restaurant, coffee shop, etc.) of each PoI.
- `My_Locations` – You will digitize the spatial extent of your living place (house, flat, etc.) and your college/office in the form of ‘polygon’. You will add two Fields to its Attribute Table to store the ‘name’ and ‘area’ of each polygon.

4.  After digitizing the features, open the Attribute Table of each shapefile one by one and add new fields to store data as mentioned in Task 3. Compute the distance and area using ‘Calculate Geometry’ tool.

### Raster data (5 mins)
1. Download `Cambridge District Wards` data of Cambridgeshire from:[link](https://data.cambridgeshireinsight.org.uk/dataset/wardselectoral-divisions/resource/a5da0436-1142-48a9-8d82-d070fae138aa) and save into your working directory.
2. Import shapefile into your project:  Navigate to the your working directory in browser panel and drag the `Wards_December_2015_Generalised_Clipped_Boundaries_in_Great_Britain.shp` into the map view window. Or, you can add vector file through data source manager.
You can check your raster map with [Camrbidge Terrain Map](https://en-gb.topographic-map.com/maps/dgf/Cambridge/)
Note: Click ok if there is a CRS transformation window pop-up
![](statics/QGIS_import.png)
