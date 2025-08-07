# ExportDocs

### docs for Exporting from old mssql server(2014) to latest mssql server version

# Project Summary: Hybrid Azure Data Integration and Synchronization

This project implements a data integration pipeline designed to extract, transform, and load (ETL) data across two separate Microsoft SQL Server databases hosted in Azure. One database is a legacy system running on **SQL Server 2014** and requires a **Hybrid Connection** for secure access. The other database resides on a **modern SQL Server instance** within Azure SQL Database.

## Workflow Overview

1. **Data Source Access**

   - Establish a **Hybrid Connection** to securely access the on-premises (or legacy-hosted) **SQL Server 2014** database from Azure.
   - Connect directly to the latest Azure-hosted SQL Server instance using standard SQL connectivity.

2. **Data Extraction**

   - Retrieve required records from **two source tables**:
     - One from the **modern database**
     - One from the **legacy SQL 2014 database**
   - Perform **joins** between these two tables to create a unified dataset based on shared keys or business logic.

3. **Data Filtering**

   - Use the joined result to **filter additional records** from a **third table** located in the **legacy database** (SQL Server 2014).

4. **Data Insertion**

   - Insert the filtered and processed records as **new entries** into a **target table** in the **modern SQL database**.

## Key Technologies and Tools

- **Azure App Service** – for hosting integration logic or middleware
- **Azure Hybrid Connections** – to securely access SQL Server 2014
- **Python / .NET / Logic Apps / Data Factory** – for building and orchestrating the pipeline
- **SQLAlchemy / pyodbc / ADO.NET** – for database interaction
- **Stored Procedures / Views** – for query optimization (optional)

## Use Case

This architecture supports **gradual cloud migration**, allowing seamless integration between legacy systems and modern cloud infrastructure. It ensures **data consistency** and enables **centralized reporting or analytics** on the latest platform.


### Development

1. Virtual Environment

    - ```python3.11 -m venv .```
2. Activate Virtual Environment

    - ```source bin/activate```

3. Install requirements

    -```pip install -r requirements.txt```

4. Build site

    -```mkdocs build```

5. Deploy to github pages

    - ```mkdocs gh-deploy```
