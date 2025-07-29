# Development

### Whats the goal,

1. To update BI_Table hosted in mssql server latest version (>= 2022 )
2. The rows comes from B&F Papers$Shipment LInes Tables hosted in mssql older version (2014) which hosted in hybrid connection

#### REQUIREMENTS(Ubuntu)

1. MSSQL VERSION 2014 <= 2017
2. MSSQL VERSION >= 2022


### steps

1. Create a view table vv_BiTable
2. Populate it with initial data from joined tables
    - B&F Papers$Sales Shipment Line
    - B&F Papers$Customer
    - B&F Papers$Item
    - B&F Papers$ Shipment Headers


    Note: This is a one time job only. This tables come from NavDatabase(MSSQL 2014 VERSION)

3. If not exists, Create table BI_table in database with MSSQL 2022 
4. Run the scheduled job(aka cron job). [See illustration](diagram.md)

