---
title: Channel database extensions
description: Learn how to extend the channel database for different scenarios in Microsoft Dynamics 365 Finance and Dynamics 365 Commerce.
author: aneesa
ms.date: 10/16/2025
ms.topic: how-to
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: aneesa
ms.search.validFrom: 2017-09-15
ms.custom: 
  - bap-template
---

# Channel database extensions

[!include [banner](../../includes/banner.md)]

This article explains how to extend the channel database for different scenarios in Microsoft Dynamics 365 Finance and Dynamics 365 Commerce. The guidance in this article only applies to Dynamics 365 Finance and Dynamics 365 Commerce.

The channel database (channel DB) holds transactional and master data from one or more commerce channels, such as an online store or a brick-and-mortar store. The master data is pushed down from headquarters to the channel database using the Commerce Data Exchange (CDX). The transactional data stored in the channel database is pulled back to the headquarters using the CDX.

Before discussing the different scenarios for extension, it's important to understand the recent enhancements to channel DB extensions.

Microsoft made some improvements to how extensions are handled during an upgrade, and recommends using one of the following environment configurations:

- Microsoft Dynamics 365 Finance, Enterprise edition (July 2017) with application update 5.
- Microsoft Dynamics 365 Retail 7.2 with application update 5.
- Microsoft Dynamics 365 Retail 7.3, which includes application update 5.
- Microsoft Dynamics 365 Finance 7.3, which includes application update 5.

Learn more in [Pre-extended columns in the channel database](extended-columns.md).

## EXT schema

In Finance and Commerce, there's an external schema called the *EXT schema* that supports extensions. In previous versions, if you wanted to add an extension to channel DB, you would add it to the CRT or AX schema. In both Finance and Commerce, you can't change the CRT, AX, or DBO schemas. All changes must be made in the EXT schema. If you modify anything in the CRT or AX schemas, then deployment in Microsoft Dynamics Lifecycle Services (LCS) fails. An error message states that you don’t have permission to modify the CRT, AX, and DBO schemas. Extensions don't have permission to read the CRT, AX, and DBO schema definition during deployment, don't include any queries in the extension script to read the CRT, AX, and DBO schema definition.

> [!NOTE]
> If you want to increase any channel DB field length, you must create an extensibility request in LCS, increasing the extended data types (EDT) length or decimal precision. Changes aren't automatically pushed to the channel DB, and extensions don't have permissions to change or modify anything in the channel DB - CRT, AX, or DBO schema. If you modify anything in the CRT or AX schemas, then deployment in LCS fails.

## Best practices for channel DB extensions

- Don’t modify anything in the CRT, AX, or DBO schemas. Use the EXT schema for all extension scenarios.
- If available, Microsoft recommends getting data through Commerce Runtime data services, as opposed to accessing channel database artifacts directly from CRT, AX, or DBO objects.
- Avoid accessing tables directly in the EXT schema. You can instead use *views* to read records, and *stored procedures* to insert, update, or delete records.
- Editing the values of any fields of tables in AX or CRT schemas from an extension is unsupported by Microsoft and may eventually break the schemas when stricter enforcement improvements are introduced. Microsoft doesn't support any issues that arise from editing schema values via extensions.

### Generated extension SQL scripts

The Generated extension SQL script feature (available in Commerce versions 10.0.46 and later) simplifies and accelerates the process of adding extensions to the channel database. 

The **Generated extension SQL script** section on the **Scheduler Subjobs** page (**Retail and Commerce** \> **Headquarters setup** \> **Commerce scheduler** \> **Scheduler subjobs**) displays SQL script that you can use as a starting point to add or modify tables in the channel database for the selected subjob.

The generated script follows current guidelines and best practices and automatically includes indexes that optimize performance. It also helps avoid common customization errors such as incorrect column or table names and missing required fields that impact data synchronization.

### Example SQL script of what to avoid

The following SQL script is an example of what you shouldn't do. Instead, you should use the CRT data service to get the primary key value and then use the primary key to insert into your extension table.

```sql
MERGE INTO [ax].RETAILCUSTPREFERENCE   --Don't access AX schema object
USING (SELECT DISTINCT
    tp.PARENTRECID, tp.PROPERTYVALUE AS [EMAILOPTIN], ct.ACCOUNTNUM, ct.DATAAREAID
  FROM @TVP_EXTENSIONPROPERTIESTABLETYPE tp
  JOIN [ax].CUSTTABLE ct ON ct.RECID = tp.PARENTRECID  --Don't access AX schema object
  WHERE tp.PARENTRECID <> 0 AND tp.PROPERTYNAME = 'EMAILOPTIN') AS SOURCE
  ON [ax].RETAILCUSTPREFERENCE.RECID = SOURCE.PARENTRECID
    AND [ax].RETAILCUSTPREFERENCE.DATAAREAID = SOURCE.DATAAREAID --Don't access AX schema object
    AND [ax].RETAILCUSTPREFERENCE.ACCOUNTNUM = SOURCE.ACCOUNTNUM
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

### Scenarios to avoid

- Don't create any new extension tables, views, or stored procedures in CRT, AX, or DBO schemas. All extension artifacts must be done in the EXT schema.
- Don't use any of the CRT, AX, or DBO schema data types in the EXT schema. You must create custom data types in the EXT schema and use those data types instead.
- Don't modify any views, procedures, functions, or database artifacts.
- If possible, avoid accessing or calling database artifacts from your extensions. Instead, use the CRT data service to get data. The benefit of using the data service is that it's supported until the end of the Service Level Agreement (SLA), even if breaking changes are later made to the database schema. However, there are instances in which the CRT data service doesn't expose the data that you need. In these cases, it's still possible to access this data by creating a view that joins on a channel DB artifact. Creating views can be a powerful tool to structure the data in a format you need at a database level, as opposed to doing it in memory through CRT extensions.
- Don't access any dbo.objects from extension scripts because DBO schema objects aren't available in Commerce Scale Unit deployments.

```sql
CREATE VIEW [ext].[CONTOSORETAILSTOREHOURSVIEW] AS
(
    SELECT
    sdht.DAY,
    sdht.OPENTIME,
    sdht.CLOSINGTIME,
    sdht.RECID,
    rst.STORENUMBER
    FROM [ext].[CONTOSORETAILSTOREHOURSTABLE] sdht
    INNER JOIN [ax].RETAILSTORETABLE rst --Don't access AX schema object
       ON rst.RECID = sdht.RETAILSTORETABLE
)
```

## Adding extensions

- If you create an extended upload table and want to sync the data back to headquarters, the table must have the same primary key and clustered index as the headquarters table in the extended table. If not, the CDX sync fails. 
- If you need to pull the data from the extension table to headquarters, then the **REPLICATIONCOUNTERFROMORIGIN** identity column (`[REPLICATIONCOUNTERFROMORIGIN] [int] IDENTITY(1,1) NOT NULL,`) is required in the extension table.
- The **REPLICATIONCOUNTERFROMORIGIN** field can't be the only unique field.
- For better performance, create an index on the **REPLICATIONCOUNTERFROMORIGIN** field.
- All extension table columns must have the NOT NULL constraint enforced. During upgrade, blank column values are updated with NULL values that may cause a runtime exception in CRT if the null value isn't handled properly.
- All the extension tables should have grant permission on **UserRole** and **DeployExtensibilityRole**.

    ```sql
    --Tables:

    GRANT SELECT, INSERT, UPDATE, DELETE ON OBJECT::[ext].[RETAILCUSTPREFERENCE] TO [UsersRole]
    GO

    GRANT SELECT, INSERT, UPDATE, DELETE ON OBJECT::[ext].[RETAILCUSTPREFERENCE] TO [DeployExtensibilityRole]
    GO

    --Stored procedures:

    GRANT EXECUTE ON [ext].[EXTSTOREDPROCEDURE] TO [UsersRole];
    GO

    GRANT EXECUTE ON [ext].[EXTSTOREDPROCEDURE] TO [PublishersRole];
    GO

    GRANT EXECUTE ON [ext].[EXTSTOREDPROCEDURE] TO [DeployExtensibilityRole];
    GO
    ```

- Grant **DataSyncUsersRole** permission if your table is going to send or receive data from headquarters.

    ```sql
    GRANT SELECT, INSERT, UPDATE, DELETE, ALTER ON OBJECT::[ext].[EXTTABLENAME] TO [DataSyncUsersRole]
    GO
    ```

- Always prefix your table, for example **ContosoRetailTransactionTable**, so that you can avoid conflicts with other customizations.

## Attributes

The attribute framework in headquarters is extended to support attributes for customers, customer orders, cash and carry transactions, and call center orders.

### Customer attributes

With the new customer attribute framework, you can use configurations to add new fields to the customer add/edit or customer details screens in POS or headquarters. After you configure the customer attribute group in Commerce parameters, POS and headquarters automatically show the new attribute without any code change or customization. The screen layout designer is also configured to show the customer attributes in the transaction screen **Customer** panel.

### Order attributes

The attribute framework iss extended to support attributes in cash and carry transactions, customer orders, and call center orders. You can edit and set values directly in headquarters or in CRT without any database changes by using configurations. You can customize the attribute values for core business logic, but customization isn't required for basic create, read, update, and delete (CRUD) operations. Previously, to create attributes you had to create new tables in headquarters and the channel DB, and then modify CRT. Now all the attribute creation can be done through configuration.

## Adding a new table

This scenario explains how to create a new table and add it to the channel DB. All extension code has access to the EXT schema.

- Create a new table in the channel database in the EXT schema either using SQL Server Management Studio Designer or SQL scripts. The following script is an example of a SQL script.

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
    [REPLICATIONCOUNTERFROMORIGIN] [int] IDENTITY(1,1) NOT NULL,
    [ROWVERSION] [timestamp] NOT NULL,
    [DATAAREAID] [nvarchar](4) NOT NULL,
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

> [!NOTE]
> If the new extension table data needs to be pulled into Retail headquarters using Commerce Data Exchange (CDX), then the extension table must include the REPLICATIONCOUNTERFROMORIGIN identity column (`[REPLICATIONCOUNTERFROMORIGIN] [int] IDENTITY(1,1) NOT NULL,), [ROWVERSION] [timestamp] NOT NULL` and `[DATAAREAID] [nvarchar](4) NOT NULL`) if nonshared. The **REPLICATIONCOUNTERFROMORIGIN** field can't be the only unique field and is required if the table data is per company. This configuration also required for a CDX pull job. **REPLICATIONCOUNTERFROMORIGIN** isn't required if the data is pushed from Retail headquarters to the channel database, and is only needed if the data is pulled from channel database to Retail headquarters.

## Extending an existing table

If you're extending existing table, then you must either use attributes if supported for that entity or create and extended table (new table) with same primary key as the parent table. The following script extends a table.

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
GRANT UPDATE ON [ext].[RETAILTRANSACTIONTABLE] TO [DataSyncUsersRole];
GO
GRANT SELECT ON [ext].[RETAILTRANSACTIONTABLE] TO [DataSyncUsersRole];
GO
```

## Adding new views, stored procedure, functions, and defined types

All new stored procedures, views, or functions must be created in the EXT schema. Don't access or call our database artifacts from your procedures, views, or functions.

## Deployment checks

The deployment process determines if there are any modification to the database artifacts. If you attempt to modify the CRT, AX, or DBO schema objects, or access them for any scenario directly in SQL, then deployment fails.

## Deployment timeout

SQL Server times out if the deployment script runs for more than 30 minutes. To avoid timeout and deployment failure, split the long running script into multiple smaller scripts that run in less than 30 minutes.

## Extension scripts and deployment

Channel database extensions are provided by authoring one or more T-SQL script files and including them in a [deployable package](./retail-sdk/retail-sdk-packaging.md). This process is described in the [Retail SDK](./retail-sdk/retail-sdk-overview.md) documentation.

Extension script files must be written using [T-SQL](/sql/t-sql/language-reference) and compatible with [Azure SQL Database](/azure/sql-database/sql-database-features).

The script files must end with the *.sql* file extension. Any other files are ignored or may induce a packaging or deployment failure. If you intend to deploy your channel DB extensions as part of Commerce Scale Unit or Store Commerce app offline, the scripts must also be compatible with the version of SQL Express and/or SQL Server that is used for those components.

During deployment and installation, the extension scripts are executed in alphabetical order based on the script file name. Each script is run to completion and then a metadata record is added to the channel database's CRT.RETAILUPGRADEHISTORY table to track the completion of that extension script.

The script isn't executed again for the same channel database in subsequent deployments if that metadata record is present. If a script fails during execution and doesn't complete successfully, its metadata isn't stored and the script is rerun on subsequent deployments.

If the deployment or installation is combined with an update of the product, the extension scripts are run after the product update.

To author a successful channel database extension, you must adhere to the following guidelines.

### Use a naming convention that ensures stable order when sorted alphabetically

Because extension scripts are executed in alphabetical order based on the file name, you should establish a naming convention that ensures that the correct execution order is used when sorted.

One example would be naming files with the following pattern: `<ISO 8601 date>_<descriptio>.sql`, where `<ISO 8601 date>` is an ISO 8601 formatted date, and `<description>` is descriptive text to identify the purpose of the script. Using *"20180501_CustomerDetails.sql"* and *"20181102_CustomerDetailsIndex.sql"* as  examples, the former represents an extension script authored on May 1, 2018 that is related to the "Customer Details" feature, and the latter represents an extension script associated to indexes related to the previous feature authored on November 2, 2018.

Another simpler alternative is to use an incremental numeric prefix, such as "0001_CustomerDetails.sql" and "0002_CustomerDetailsIndex.sql".

If one script depends on another script executing successfully, you must name the scripts to ensure that the file name in alphabetical order matches the required execution order.

### Don't alter published extension scripts

If you release a deployable package or installer extension that contains channel database extension scripts, don't alter those scripts. Extension scripts are run only once per channel database instance.

If you alter a published script that was already run against a channel database, the modifications to the already executed script aren't applied to the database.

Instead, provide the modifications in a new script file. Consider using a naming convention that determines the correct script execution order to ensure that the script runs after its dependencies.

### Don't remove old published extension scripts

Your deployable package or installer extension must represent a cumulative update for your database extensions. There should be no dependencies on previous versions of an extension package or installer. A customer should be able to apply your extension package or installer without depending on a previous version of your package or extension.

If your extension scripts were published as part of a deployable package or installer extension, don't remove them from subsequent updates in your package or installer. To account for disaster recovery, upgrade, and scale out scenarios, you can use extension packages to upgrade a new instance of the channel database to use the same version of the last deployed extension package.

### Extension scripts must be idempotent and reentrant

Although extension scripts are run only once per channel database, scripts may fail due to authoring errors or transient SQL errors, like timeouts or transaction deadlocks. The extension scripts must be idempotent and reentrant to account for those failure scenarios.
If the extension script fails due to any error, it may be rerun. Rerunning the script shouldn't adversely affect the database.

### Don't assume that the channel database data is perennial

The channel database is a transactional database that provides storage support for operations performed by Commerce Scale Unit. All data stored in the channel database that must be kept for long periods of time must be uploaded to headquarters through the [Commerce Data Exchange](./cdx-extensibility.md). Data uploaded to headquarters can be accessed by the [Commerce Data Exchange Real-time Service](./extend-commerce-data-exchange.md).

### Do write backward compatible channel database extensions

The channel database is expected to be backward compatible, which means that updating only the channel database without updating Commerce Scale Unit or POS must not prevent existing Commerce Scale Unit or POS operations from functioning correctly. During deployment flows, the different components of your Commerce Scale Unit and Store Commerce app are updated in the inverse order of dependency, which means that the channel database is the first component updated, and Commerce Scale Unit or POS are updated next. If Commerce Scale Unit or POS fails to update successfully, those components are rolled back to restore them to their previous working state. However, in such situations, the channel database isn't rolled back to prevent data loss. If your extensions aren't backward compatible, they may fail to work properly until a successful deployment is performed.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
