---
# required metadata

title: Channel database extensions
description: This topic explains how to extend the channel database.
author: mugunthanm
manager: AnnBe
ms.date: 06/20/2019
ms.topic: article
ms.prod:
ms.service: dynamics-365-retail
ms.technology:

# optional metadata

# ms.search.form:
# ROBOTS:
audience: Developer
# ms.devlang:
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm:
ms.custom: 83892
ms.search.region: Global
# ms.search.industry:
ms.author: mumani
ms.search.validFrom: 2017-09-15
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update

---

# Channel database extensions

[!include [banner](../../includes/banner.md)]

The channel database (channel DB) holds transactional and master data from one or more retail channels, such as an online store or a brick-and-mortar store. The master data is pushed down from the Retail Headquarters (Retail HQ) to the channel database using the commerce data exchange (CDX). The transactional data stored in the channel database is pulled back to the headquarters using the CDX.

In this topic we explain how to extend the channel database for different scenarios. The steps here apply only to Dynamics 365 for Retail, Dynamics 365 for Finance and Operations.

Before discussing the different scenarios for extension, it's important to understand the recent enhancements to channel DB extensions.

We have made some improvements to how extensions are handled during an upgrade. We recommend using one of the following environment configurations:
- Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (July 2017) with application update 5.
- Microsoft Dynamics 365 for Retail 7.2 with application update 5, which will be available soon.
- Microsoft Dynamics 365 for Retail 7.3, which includes application update 5.
- Microsoft Dynamics 365 for Finance and Operations 7.3, which includes application update 5.

## Ext schema

In Dynamics 365 for Retail and Dynamics 365 Finance and Operations we introduced a new schema called the **ext schema** to support extensions. In previous versions, if you wanted to add an extension to channel DB, you would add it to the CRT or AX schema. In both Retail and Finance and Operations, you cannot change the CRT, AX, or DBO schemas. All changes must be made in the **ext schema**. If you modify anything in the CRT or AX schemas, then deployment in Lifecycle Services (LCS) will fail. An error message states that don’t have permission to modify the CRT, AX, and DBO schemas.

> [!NOTE]
> If you want to increase any channel DB field length, you must create an extensibility request in LCS, increasing the EDT length or decimal precision. Dynamics 365 Finance and Operations will not automatically push the changes to the channel DB, and extensions will not have permissions to change or modify anything in the channel DB - CRT, AX or DBO schema. If you modify anything in the CRT or AX schemas, then deployment in LCS will fail.

## Best practices for channel DB extensions

- Don’t modify anything in the CRT, AX, or DBO schemas. Use the **ext schema** for all extension scenarios.
- Don’t access any CRT, AX, or DBO objects in the **ext schema**. You must use the commerce runtime data service to access any channel DB artifacts.

### Don't do this
The following is an example of what you should not do. Instead, you should use the CRT data service to get the primary key value and then use the primary key to insert into your extension table.

```sql
MERGE INTO [ax].RETAILCUSTPREFERENCE   --DONT access ax schema object
USING (SELECT DISTINCT
tp.PARENTRECID, tp.PROPERTYVALUE as [EMAILOPTIN], ct.ACCOUNTNUM, ct.DATAAREAID
FROM @TVP_EXTENSIONPROPERTIESTABLETYPE tp
JOIN [ax].CUSTTABLE ct on ct.RECID = tp.PARENTRECID  --DONT access ax schema object
WHERE tp.PARENTRECID <> 0 and tp.PROPERTYNAME = 'EMAILOPTIN') AS SOURCE
ON [ax].RETAILCUSTPREFERENCE.RECID = SOURCE.PARENTRECID
and [ax].RETAILCUSTPREFERENCE.DATAAREAID = SOURCE.DATAAREAID --DONT access ax schema object
and [ax].RETAILCUSTPREFERENCE.ACCOUNTNUM = SOURCE.ACCOUNTNUM
WHEN MATCHED THEN
UPDATE SET [EMAILOPTIN] = source.[EMAILOPTIN]
WHEN NOT MATCHED THEN
INSERT
(
    RECID
    ,DATAAREAID
    ,EMAILOPTIN
    ,ACCOUNTNUM
)
VALUES
(
    SOURCE.PARENTRECID
    ,SOURCE.DATAAREAID
    ,SOURCE.EMAILOPTIN
    ,SOURCE.ACCOUNTNUM
);
SELECT @i_Error = @@ERROR;
IF @i_Error <> 0
    BEGIN
    SET @i_ReturnCode = @i_Error;
    GOTO exit_label;
END;
```


### Don't do this
- If you are creating extension table or new table all should be done in ext schema.
- Don’t modify any views, procedures, functions or any of the database artifacts.
- Don’t access or call any of any database artifacts including views, defined types, functions and procedures from your extensions.
- To access the database artifacts, use the CRT data service. For example, suppose you want to extend the product search view to search some custom fields or to show custom columns in journal views. Don’t modify the views or procedures or functions in SQL. Instead, use the CRT data service and do the extension either by overriding or using post triggers and then call your extended procedures.

```sql
CREATE VIEW [ext].[CONTOSORETAILSTOREHOURSVIEW] AS
(
    SELECT
    sdht.DAY,
    sdht.OPENTIME,
    sdht.CLOSINGTIME,
    sdht.RECID,
    rst.STORENUMBER
    FROM [ext].[CONTOSORETAILSTOREHOURSTABLE\] sdht
    INNER JOIN [ax].RETAILSTORETABLE rst ON rst.RECID = sdht.RETAILSTORETABLE  --DONT access ax schema object
)
```

## Adding extensions
1. All the extension tables should have grant permission on **UserRole** and **DeployExtensibilityRole**.

    ```sql
    GRANT EXECUTE ON [ext].[EXTTABLENAME] TO [DeployExtensibilityRole];
        GO
        GRANT EXECUTE ON [ext].[EXTTABLENAME] TO [UsersRole];
        GO
    ```

2. Grant **DataSyncUsersRole** permission if your table is going to send receive data from HQ.

    ```sql
    GRANT SELECT, INSERT, UPDATE, DELETE ON OBJECT::[ext].[EXTTABLENAME] TO [DataSyncUsersRole]
    GO
    ```

3. If you are creating extended table and want to sync the data back to HQ, then have the primary column of the parent table in the extended table.
4. Always prefix your table, for example, **ContosoRetailTransactionTable**, so that you can avoid conflicts with other partner/ISV customizations.

## Attributes

We extended the attribute framework in HQ to support attributes for Customers, Customer orders, cash and carry transactions and call center orders.

### Customer attributes
With the new customer attribute framework, you can use configurations to add new fields to the customer add/edit or customer details screens in POS or HQ. After configuring the customer attribute group in retail parameters, POS and HQ will automatically show up the new attribute without any code change or customization. The screen layout designer will also be configured to show the customer attributes in the transaction screen - **Customer** panel.

### Order attributes
The attribute framework was extended to support attributes in cash and carry transactions, customer orders, and call center orders. You can edit and set values directly in HQ or in CRT. All this can be done through configurations, without any database changes. (You can customization the attribute values for core business logic, not required for basic CRUD operations.) Previously, you had to create new tables in HQ and channel DB, and then modify CRT to do this. Now all the attribute creation can be done through configuration.

## Adding a new table

In this scenario we will explain how to create a new table and add it to the channel DB. All extension code has access to the **ext schema**.

1. Create a new table in the channel database in the **ext schema** either using SQL Server Management Studio Designer or using SQL scripts. The following is an example SQL script.

    ```sql
    -- Create the extension table to store the custom fields.
    IF (SELECT OBJECT_ID('[ext].[CONTOSORETAILSTOREHOURSTABLE]')) IS NULL
    BEGIN
    CREATE TABLE [ext].[CONTOSORETAILSTOREHOURSTABLE](
    [RECID] [bigint] NOT NULL,
    [DAY] [int] NOT NULL DEFAULT ((0)),
    [OPENTIME] [int] NOT NULL DEFAULT ((0)),
    [CLOSINGTIME] [int] NOT NULL DEFAULT ((0)),
    [RETAILSTORETABLE] [bigint] NOT NULL DEFAULT ((0)),
    CONSTRAINT [I_CONTOSORETAILSTOREHOURSTABLE_RECID] PRIMARY KEY CLUSTERED
    (
        [RECID] ASC
    ) WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    ALTER TABLE [ext].[CONTOSORETAILSTOREHOURSTABLE] WITH CHECK ADD CHECK (([RECID]<>(0)))
    END
    GO
    GRANT SELECT, INSERT, UPDATE, DELETE ON OBJECT::[ext].[CONTOSORETAILSTOREHOURSTABLE] TO [DataSyncUsersRole]
    GO

## Extending an existing table

If you are extending existing table, then you must either use attributes if supported for that entity or create and extended table (new table) with same primary key as the parent table. The following script extends a table.

```sql
CREATE TABLE [ext].[RETAILTRANSACTIONTABLE](
[TRANSACTIONID] [nvarchar](44) NOT NULL, -- FK to [crt].RETAILTRANSACTIONTABLE
[ISB2BSALES] [int] NOT NULL DEFAULT (0),
[EXTERNALID] [nvarchar](20) NOT NULL DEFAULT (''),
CONSTRAINT [EXT_RETAILTRANSACTIONTABLE_PK] PRIMARY KEY CLUSTERED
(
    [TRANSACTIONID]
) WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
     ) ON [PRIMARY]
GO
GRANT INSERT ON [ext].[RETAILTRANSACTIONTABLE] TO [DataSyncUsersRole];
GO
GRANT DELETE ON [ext].[RETAILTRANSACTIONTABLE] TO [DataSyncUsersRole];
GO
GRANT UPDATE ON [ext\].[RETAILTRANSACTIONTABLE] TO [DataSyncUsersRole];
GO
GRANT SELECT ON [ext].[RETAILTRANSACTIONTABLE] TO [DataSyncUsersRole];
GO
```

## Adding new views, stored procedure, functions, and defined types

All new stored procedures, views or functions must be created in the **ext schema**. Don't access or call our database artifacts from your procedures, views, or functions.

## Deployment checks

The deployment process determines if there are any modification to the database artifacts. If you have attempted to modify the CRT, AX, or DBO schema objects, or access them for any scenario directly in SQL, then deployment will fail.

## Extension scripts and deployment

Channel Database extensions are provided by authoring one or more T-SQL script files and including them in a [deployable package](./retail-sdk/retail-sdk-packaging.md). This process is described in the [Retail SDK](./retail-sdk/retail-sdk-overview.md) documentation.

Extension script files must be written using [T-SQL](https://docs.microsoft.com/sql/t-sql/language-reference) and compatible with [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-features).
The script files must end with the *.sql* file extension, any other files will be ignored or may induce a packaging or deployment failure. If you intend to deploy your Channel Database extensions as part of Retail Store Scale Unit or Modern POS offline,
the scripts must also be compatible with the version of SQL Express and/or SQL Server that will be used for those components.

During deployment and installation, the extension scripts are executed in alphabetical order based on the script file name.
Each script is run to completion and then a metadata record is added to the Channel Database's CRT.RETAILUPGRADEHISTORY table to track the completion of that extension script.
The script will not be executed again for the same Channel Database in subsequent deployments if that metadata record is present.
If a script fails during execution and does not complete successfully, its metadata will not be stored and the script will be rerun on subsequent deployments.

If the deployment or installation is combined with an update of the product, the extension scripts are run after the product update.

To author a successful Channel Database extension, you must adhere to the following guidelines.

### Use a naming convention that ensures stable order when sorted alphabetically

Because extension scripts are executed in alphabetical order based on the file name, you should establish a naming convention that ensures that the correct execution order is used when sorted.

One example would be naming files with the following pattern: "<ISO 8601 date>_<descriptio>.sql", where **<ISO 8601 date>** is a ISO 8601 formatted date and **<description>** is descriptive text to identify the purpose of the script.
For instance, *"20180501_CustomerDetails.sql"* and *"20181102_CustomerDetailsIndex.sql"*.
The former would represent an extension script authored on May 1, 2018 that is related to "Customer Details" feature and the latter an extension script associated to indexes related to the previous feature authored on November 2, 2018.

Another simpler alternative is to use an incremental numeric prefix, such as "0001_CustomerDetails.sql" and "0002_CustomerDetailsIndex.sql".

If one script depends on another having executed successfully, you must name then in a way that ensures that the file name in alphabetical order matches the required execution order.

### Do not alter extension scripts that have been published

If you have released a deployable package or installer extension that contains Channel Database extension scripts, do not alter those scripts. Extension scripts are run only once per Channel Database instance.
If you alter published scripts and those scripts may have already been run against a Channel Database, the modifications to an already executed script will not be applied to the database.

Instead, provide the modifications in a new script file. Consider the naming convention noted above to ensure that it runs after its dependencies.

### Do not remove old extension scripts that have been published

Your deployable package or installer extension must represent a cumulative update for your database extensions. There should be no dependencies on previous versions of an extension package or installer. A customer should be able to apply your extension package or installer without depending on a previous version of your package or extension.

If your extension scripts have been published as part of a deployable package or installer extension, do not remove them from subsequent updates in your package or installer. To account for disaster recovery, upgrade and scale out scenarios, extension packages may be
used to bring a new instance of the Channel Database to the same version of the last deployed extension package.

### Extension scripts must be idempotent and reentrant

Although extension scripts are run only once per Channel Database, scripts may fail due to authoring errors or transient SQL errors, like time outs or transaction deadlocks. The extension scripts must be idempotent and reentrant to account for those failure scenarios.
If the extension script fails due to any error, it may be rerun. Rerunning the script should not adversely affect the database.

### Do not assume that the Channel Database data is perennial

The Channel Database is a transactional database that provides storage support for operations performed by Retail Server. All data that is stored in the Channel Database that must be kept for long periods of time must be uploaded to the headquarters
through the [Commerce Data Exchange](./cdx-extensibility.md). Data uploaded to the headquarters can be accessed by the [Commerce Data Exchange Real-time Service](./extend-commerce-data-exchange.md).

### Do write backward compatible channel database extensions

The Channel Database is expected to be backward compatible. This means that updating only the Channel Database without updating Retail Server or POS must not prevent existing Retail Server or POS operations from functioning correctly. During deployment flows, the different components of your Retail Cloud Scale Unit, Retail Store Scale Unit and Modern POS are updated in the inverse orther of dependency. This means that the Channel Database is the first component to be updated, and Retail Server or POS are updated next. In case that Retail Server or POS fails to update successfully, those components are rolledback to restore them to their previous working state. However, in such situations, the Channel Database is not rolledback to prevent data loss. If your extensions are not backward compatible, they may fail to work properly until a successfull deployment is performed.