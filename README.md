# Spatial_Database_SQL
### A comprehensive guide for practical sessions on spatial databases, including PostgreSQL and PostGIS
### TD1
**Practical Work:** Installation of PostGIS and Creation of a Spatial Database  

## Objective  
This guide is designed to help students install PostgreSQL and PostGIS, and create a spatial database using pgAdmin.

## Step 1: Installing PostgreSQL  
1. Visit the [PostgreSQL download page](https://www.postgresql.org/download/) and download the latest version for your operating system.  
2. Follow the installation guide specific to your OS:  
   - For **Windows**: Run the installer and follow the setup wizard.  
   - For **Linux**: Use your package manager to install PostgreSQL.  
   - For **macOS**: Use `brew` or download the installer.  
3. During the installation, set a password for the `postgres` user. Ensure it is easy to remember.  

## Step 2: Installing PostGIS  
1. During the PostgreSQL installation, ensure all components are selected.  
2. Launch **Stack Builder** after the installation is complete.  
3. Select the PostgreSQL version installed on your machine.  
4. Download and install PostGIS by following the wizard steps.  
5. Complete the setup by clicking **Finish**.  

## Step 3: Creating a Database with pgAdmin  
1. Open **pgAdmin 4**, a database management tool included with PostgreSQL.  
2. Log in using the password you set during the PostgreSQL installation.  
3. Expand the **Servers** node and right-click on **PostgreSQL** > **Create** > **Database**.  
4. Enter a name for your new database (e.g., `spatial-db-1`) and click **Save**.  

## Verifying PostGIS Installation  
1. Expand your newly created database in **pgAdmin**.  
2. Open the **Query Tool** by right-clicking on the database.  
3. Execute the following SQL command:  
   ```sql
   CREATE EXTENSION postgis;
