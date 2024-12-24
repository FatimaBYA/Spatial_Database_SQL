# Spatial Database  
 
**TD-1 Installation of PostGIS and Creation of a Spatial Database**

---

### 1. Download and Install PostgreSQL
- Access the [PostgreSQL download page](https://www.postgresql.org/download/) to download the latest version of PostgreSQL suitable for your operating system. PostgreSQL is compatible with Linux, macOS, Windows, BSD, and Solaris.
- Follow the installation guide for your operating system:
  - Windows
  - Linux
  - macOS
- During installation, set a password for the `postgres` user. Ensure it is easy to remember as it will be needed to connect to PostGIS.

---

### 2. Download and Install PostGIS
- During PostgreSQL installation, ensure all components are selected. **Stack Builder** will be used to download PostGIS.
- At the end of the PostgreSQL installation, launch Stack Builder if prompted.
  - Select your installed PostgreSQL version for PostGIS installation.
  - Ensure you are connected to the Internet.
- In Stack Builder:
  - Choose **PostGIS** as the database spatial extension.
  - Optionally, check "Create a spatial database." For this tutorial, we will create it manually using pgAdmin 4.
  - Follow the instructions to specify the installation directory.
  - Complete the setup by clicking **Close** when the configuration is successful.

---

### 3. Create a Database Using PgAdmin 4
1. Launch **pgAdmin 4**, a PostgreSQL database management tool installed with PostgreSQL.
2. Enter the password you defined during PostgreSQL installation.
3. Expand `Servers` > right-click on `PostgreSQL` > **Create** > **Database**.
4. Name the database (e.g., `spatial-db-1`) and click **Save**.

---

### 4. Add the PostGIS Extension
- Expand `Databases` > select your new database (e.g., `spatial-db-1`).
- Right-click on the database > **Query Tool**.
- Execute the following SQL query to add the PostGIS extension:
    ```sql
    CREATE EXTENSION postgis;
    ```
- Click the **Execute** button or press `F5` to run the query.

---

### 5. Verify PostGIS Installation
- After successfully executing the query, confirm that the PostGIS extension has been added:
  1. Expand your database > `Schemas` > `Public` > `Tables`.
  2. Look for a table named `spatial_ref_sys`.  
     This confirms that the PostGIS spatial extension has been successfully installed.
