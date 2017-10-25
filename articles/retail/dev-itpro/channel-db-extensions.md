---
# required metadata

title: Channel database (DB) extensions
description: This topic explains how to extend the channel database.
author: mugunthanm
manager: AnnBe
ms.date: 09/15/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations, Retail, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 83892
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2017-09-15
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update

---

# Channel database (DB) extensions

The channel database (channel DB) holds transactional and master data from one or more retail channels, such as an online store or a brick-and-mortar store. The master data is pushed down from the Retail Headquarters (Retail HQ) to the channel database using the commerce data exchange (CDX). The transactional data stored in the channel database is pulled back to the headquarters using the CDX.

In this topic we explain how to extend the channel database for different scenarios. The steps here apply only to Dynamics 365 for Retail, Dynamics 365 for Finance and Operations, Enterprise edition.

Before going to the different scenarios for extension, it's important to understand the recent enhancements to channel DB extensions:

## Ext Schema

In Dynamics 365 for Retail and Dynamics 365 Finance and Operations, Enterprise edition we introduced a new schema called the **ext schema** to support extensions. In previous versions, if you wanted to add an extension to channel DB, you would add it to the CRT or AX schema. In Dynamics 365 for Retail and Dynamics 365 for Finance and Operations, Enterprise edition version you cannot change the CRT, AX, or DBO schemas. All changes must be made in the **ext schema**. If you modify anything in the CRT or AX schemas, then deployment in Lifecycle Services will fail. The error reports taht don’t have permission to modify the CRT, AX, and DBO schemas. 

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

