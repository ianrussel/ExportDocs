### docs for Exporting from old mssql server(2014) to latest mssql server version# ExportDocs

This project implements a data integration pipeline designed to extract, transform, and load (ETL) data across two separate Microsoft SQL Server databases hosted in Azure. One database is a legacy system running on SQL Server 2014 and requires a Hybrid Connection for secure access. The other database resides on a modern SQL Server instance within Azure SQL Database.

Workflow Overview:
Data Source Access:

Establish a Hybrid Connection to securely access the on-premises (or legacy-hosted) SQL Server 2014 database from Azure.

Connect directly to the latest Azure-hosted SQL Server instance using standard SQL connectivity.

Data Extraction:

Retrieve required records from two source tables:

One from the modern database

One from the legacy SQL 2014 database

Perform joins between these two tables to create a unified dataset based on shared keys or business logic.

Data Filtering:

Use the joined result to filter additional records from a third table located in the legacy database (SQL Server 2014).

Data Insertion:

The filtered and processed records are then inserted as new entries into a target table in the modern SQL database.

Key Technologies and Tools:
Azure App Service (for hosting integration logic or middleware)

Azure Hybrid Connections (for accessing the SQL Server 2014 instance)

Python / .NET / Logic Apps / Data Factory (depending on implementation language or tool)

SQLAlchemy / pyodbc / ADO.NET for database interaction

Stored Procedures or Views (optional for optimization)

Use Case:
This architecture supports gradual cloud migration, allowing seamless integration between legacy systems and modern cloud infrastructure, ensuring data consistency and centralized reporting or analytics on the latest platform.

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
