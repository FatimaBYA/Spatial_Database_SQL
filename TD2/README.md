
# Spatial Database

## TD-2: Creating Tables with Spatial Columns


### 1. Create a Spatial Table (Points)
- With PgAdmin, create a table `points_of_interests` with a geometric column of type `Point`.
    ```sql
    CREATE TABLE points_of_interests (
      id SERIAL PRIMARY KEY,
      nom VARCHAR(255),
      geom GEOMETRY(Point, 4326)
    );
    ```
- Insert data into this table using **QGIS**.
    - For the first connection from QGIS:
        1. Right-click on **Postgresql** in the Explorer panel.
        2. Select **New Connection** and input the required connection details.
        3. Test the connection.
        4. Once the connection is established, double-click the `points_of_interests` table. This will add a layer to QGIS.
        5. Switch to **Edit mode**.
        6. Add some points and save the changes.
- Go to **PgAdmin** and execute the following query:
    ```sql
    select * from points_of_interests;
    ```
    - **Answer:** This query will show all the data from the `points_of_interests` table, including the inserted points.

### 2. Create a Spatial Table (Polygons)
- Create a table `zones_protegees` with a geometric column of type `Polygon`.
    ```sql
    CREATE TABLE zones_protegees (
      id SERIAL PRIMARY KEY,
      nom VARCHAR(255),
      geom GEOMETRY(Polygon, 4326)
    );
    ```
- Insert data into this table using **QGIS**, then save the changes.
- Go to **PgAdmin** and execute the following query:
    ```sql
    select * from zones_protegees;
    ```
    - **Answer:** This query will show all the data from the `zones_protegees` table, including the inserted polygons.

### 3. Create a Spatial Table with a `LINESTRING` Column
- Create a table `routes` with a geometric column of type `LINESTRING`.
    ```sql
    CREATE TABLE routes (
      id SERIAL PRIMARY KEY,
      nom VARCHAR(255),
      geom GEOMETRY(LINESTRING, 4326)
    );
    ```
- Insert data into this table using **QGIS**, then save the changes.
- Go to **PgAdmin** and execute the following query:
    ```sql
    select * from routes;
    ```
    - **Answer:** This query will show all the data from the `routes` table, including the inserted lines.
