# Spatial Database

**TD-3 SQL spatial functions**

### Exercise Objective
How many parcels are located within 1 km of a fire point?  
To explore the `st_xxxx` functions, please refer to the official PostGIS documentation: [PostGIS Documentation](https://postgis.net/docs/reference.html).

### Context
In this exercise, you will use PostGIS to determine how many parcels in Florida are within a 1 km radius of a fire point, which is defined as the centroid of a given parcel. You will use the shapefile of Florida parcels available at this link.

### Exercise Steps

1. **Import the shapefile into PostGIS**
    - Download the shapefile.
    - Open the **PostGIS Shapefile Import/Export Manager** (on Windows, press the Windows key, then type "shap", and Windows should offer the PostGIS Shapefile Import/Export Manager).
    - Select your shapefile for Florida parcels.
    - Import it into a PostgreSQL table.

2. **In pgAdmin, execute the following query**
    ```sql
    select count(*) from parcels;
    ```
    - **Answer:** This query returns the total number of parcels in the table.

3. **Select the fire point (centroid of parcel 462273)**
    ```sql
    SELECT ST_Centroid(geom) AS fire_point
    FROM parcels
    WHERE gid = 462273;
    ```
    - **Answer:** This query returns the centroid (fire point) of parcel 462273, which is used as the reference fire point.

4. **Risk zone within a 1 km radius of the fire point**
    - In **QGIS**, duplicate the `parcel` layer and rename it to `fire-risk`.
    - Right-click on this layer and select "Filter..".
    - Add the following `whereclause` in the "Filter expression" section:
      ```sql
      ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 1000);
      ```
      *Note: The QGIS filter does not expect the first part: "select * from parcel". If you remove it, you will get an error.*

    - Change the symbology of this layer to show the fire risk zones.
    - You have identified another fire point in parcel 460957.
    - Modify the filter to detect both zones now by adjusting the query to:
      ```sql
      ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 1000) 
      OR ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 460957), 1000);
      ```

5. **Develop spatial SQL queries to answer the following questions:**
    - **How many parcels are located within 1 km of both target parcels (gid = 460957 and 462273)?**
      ```sql
      SELECT count(*) 
      FROM parcels 
      WHERE ST_DWithin(geom, 
        (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 462273), 1000) 
      OR ST_DWithin(geom, 
        (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 460957), 1000);
      ```
      - **Answer:** This query will return the number of parcels that are within 1 km of either parcel 462273 or 460957.

    - **What is the total area of parcels near the fire?**
      ```sql
      SELECT SUM(ST_Area(geom)) 
      FROM parcels 
      WHERE ST_DWithin(geom, 
        (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 462273), 1000) 
      OR ST_DWithin(geom, 
        (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 460957), 1000);
      ```
      - **Answer:** This query will return the total area of all parcels within 1 km of the fire points.
