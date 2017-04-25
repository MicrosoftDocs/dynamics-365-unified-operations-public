---
# required metadata

title: Import data from an ODBC data source (AX 2012)
description: You can use the Microsoft Dynamics AX 2012 Data Import/Export Framework to import data from an ODBC data source into Microsoft Dynamics AX 2012. 
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18821
ms.assetid: 3eb200bd-666e-424c-8bd0-9528da4ba880
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Import data from an ODBC data source (AX 2012)

[!include[banner](../../includes/banner.md)]


You can use the Microsoft Dynamics AX 2012 Data Import/Export Framework to import data from an ODBC data source into Microsoft Dynamics AX 2012. 

This walkthrough illustrates the following tasks:

-   Create a SQL Server data source
-   Define the format of your source data
-   Define a processing group
-   Process data from source to staging
-   Validate the data in staging
-   Process data from staging to target
-   Validate the data in target

## Prerequisites
To complete this walkthrough you will need:

-   Microsoft Dynamics AX 2012, Microsoft Dynamics AX 2012 R2, or Microsoft Dynamics AX 2012 R3.
-   Data Import/Export Framework

## Create a SQL Server data source
1.  Open Microsoft SQL Server Management Studio.
2.  Run the following query to create a database (DMFLEgacyDB), create a table (VendorEntity), and populate the table.

         USE [master] GO /****** Database [DMFLegacyDB] ******/ CREATE DATABASE [DMFLegacyDB]GOUSE [DMFLegacyDB]
        GO
         /****** Table [dbo].[VendorEntity] ******/
         CREATE TABLE [dbo].[VendorEntity]
        (
         [ACCOUNTNUM][nvarchar](20)default(N'') NOT NULL,
         [FIRSTNAME][nvarchar](25)default(N'') NOT NULL,
         [MIDDLENAME][nvarchar](25)default(N'') NOT NULL,
         [LASTNAME][nvarchar](25)default(N'') NOT NULL,
         [LANGUAGEID][nvarchar](7)NOT NULL,
         [VENDGROUP][nvarchar](20)NULL,
         [CURRENCY][nvarchar](10)NULL,
         [PartyType][nvarchar](10)NULL
         ) 
        ON [PRIMARY]
        GO
        INSERT [dbo].[VendorEntity] ([ACCOUNTNUM], [FIRSTNAME], [MIDDLENAME], [LANGUAGEID], [LASTNAME], [VENDGROUP], [CURRENCY], [PartyType])
         VALUES (N'V001', N'001 first', N'001 middle', N'en-us', N'001 last', N'10', N'USD', N'Person')
        INSERT [dbo].[VendorEntity] ([ACCOUNTNUM], [FIRSTNAME], [MIDDLENAME], [LANGUAGEID], [LASTNAME], [VENDGROUP], [CURRENCY], [PartyType])
         VALUES (N'V002', N'002 first', N'002 middle', N'en-us', N'002 last', N'20', N'USD', N'Person')

## Create an ODBC data source to connect to the SQL Server database
1.  On the computer that is running Microsoft Dynamics AX, open **Administrative Tools** &gt; **Data Source (ODBC)**.
2.  Create a User DSN for SQL Server, name it **DMFLegacyDB-DSN**, and select the instance of SQL Server that you used to create the database.
3.  Click **Next**, and select the appropriate values to connect to the SQL Server instance. In general, we recommend that you connect with the account that you are running the Data Import/Export Framework service as.For more information, see [Managing Data Sources](http://msdn.microsoft.com/en-us/library/windows/desktop/ms712362(v=vs.85).aspx).
4.  Click **Next**, select **DMFLegacyDB** for the default database, and then click **Finish**.

## Define the format of your source data
1.  Open **Data Import/Export Framework** &gt; **Setup** &gt; **Source data formats**.
2.  Click **New**, enter a name and description, and then in the **Type** field, select **ODBC**.
3.  On the **General** tab, for **DSN** type, select **User DSN**, for **DSN location**, select **Client**, and then select **DMFLegacyDB-DSN**. The connection string will populate.
4.  Click **Validate** to verify that the account that you are logged on as has access to the ODBC connection.

## Define a processing group
1.  In **Data Import/Export Framework** &gt; **Common** &gt; **Processing group**, click **New** to create a new processing group.
2.  Set the group name and description.
3.  Click **Entities** to select the entities to include in the processing group.
4.  In the **Select entities for processing group** form, click **New**, and then, for **Entity name**, select **Vendor**.
5.  Click **Entities**. The **Select entities for processing group** dialog box opens.
6.  In the **Query** box, enter the following query:

        select * from VendorEntity

7.  Click **Generate source mapping**. Optional: Modify the mapping as needed.
8.  Click **Validate**.
9.  Click **Preview source file**, and then close the **Select entities for processing group** form.

## Process data from source to staging
1.  In the **Processing group** form, select the vendor group that you created, and click **Get staging data**.The **Create a job ID for the staging data job** dialog box opens.
2.  By default, an ID for the job is generated. You can optionally modify the ID and add a description. Click **OK**.
3.  The **Staging data execution** form opens.
4.  In the **Get data from source to staging** form, click **OK** to run immediately.The source data is copied to the staging tables.

## Validate the data in staging
1.  In **Data Import/Export Framework** &gt; **Common** &gt; **Processing group**, click **Execution history**, and select the job that ran.
2.  Click **View staging data**.
3.  Review the staging data to validate that it matches the ODBC source.
4.  Click **Validate all** to verify that all the related reference data is correct and present in the system.

## Process data from staging to target
1.  In **Data Import/Export Framework** &gt; **Common** &gt; **Processing group**, select the processing group to work with.
2.  Click **Copy data to target**. The **Select a job ID to run** dialog box opens.
3.  Select a job and click **OK**.The **Target data execution** dialog box opens.
4.  Click **Run**, and then click **OK**. The data is copied to the target entities.

## Validate the data in target
Verify that the vendor data from the ODBC source is displayed in either of the following ways:

-   View staging data:
    1.  **Data Import/Export Framework** &gt; **Common** &gt; **Processing group**, click **Execution history**, click **View staging data** and then select the job that ran.
    2.  Review the staging data to validate that it matches the ODBC source.
    3.  Click **Validate all** to verify that all the related reference data is correct and present in the system.
-   Verify that the customer data from the ODBC source is now displayed in **Accounts payable** &gt; **Common** &gt; **Vendor** &gt; **All Vendors** form.




