---
# required metadata

title: Channel DB extensions
description: 
author: mugunthanm
manager: AnnBe
ms.date: 09/15/207
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

# Channel DB extensions

Channel database hold transitional and master data from one or more retail channels, such as Online store or brick-and-mortar stores. The master data is pushed down from the Retail Headquarters to the channel database using the commerce data exchange (CDX) and all the transactional data stored in the channel database is pulled back to the headquarters using the CDX.

In this topic we will explain how we can extend the channel database for different scenarios, the steps mentioned here applies only to Dynamics 365 for Retail, Dynamics 365 for Finance and Operations, Enterprise edition.

Before going to the different scenarios for extension, lets understand some of the new enhancement we did in channel DB extensions:

**Ext Schema:**

In Dynamics 365 for Retail, Dynamics 365 for Finance and Operations, Enterprise edition we introduced new schema called ext schema to support extensions. In previous versions if you want to add any extension in channel DB you will do in crt or ax schema but in Dynamics 365 for Retail, Dynamics 365 for Finance and Operations, Enterprise edition versions you should not to do any changes in Microsoft schema, all changes should be done in **ext schema**, if you modify anything in our schema then during deployment in Lifecycle service it will fail saying you don’t have permission to modify the crt, ax or dbo schema. The rule is any change to channel DB should be done in ext schema.

**Best practice and Don’ts for channel DB extensions:**

1.  Don’t modify anything in crt, ax or dbo. Use the **ext schema** for all extension scenarios.

2.  Don’t access any crt, ax or dbo object in ext schema. You must use the commerce runtime data service to access any channel DB artifacts.

    Example: Don’t access any of ax or crt schema in your extension like below, you should use the CRT data service to get the primary key value and using that you should insert into your extension table not by accessing our objects.

# DON'T DO THIS

```sql
    MERGE INTO [ax].RETAILCUSTPREFERENCE   --DONT access ax schema object

     USING (SELECT DISTINCT

     tp.PARENTRECID, tp.PROPERTYVALUE as [EMAILOPTIN], ct.ACCOUNTNUM, ct.DATAAREAID

     FROM @TVP_EXTENSIONPROPERTIESTABLETYPE tp

     JOIN [ax].CUSTTABLE ct on ct.RECID = tp.PARENTRECID  --DONT access ax schema object

     WHERE tp.PARENTRECID &lt;&gt; 0 and tp.PROPERTYNAME = 'EMAILOPTIN') AS SOURCE

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

     IF @i_Error &lt;&gt; 0

    BEGIN

    SET @i_ReturnCode = @i_Error;

    GOTO exit_label;

    END;
```

1.  If you are creating extension table or new table all should be done in ext schema.

2.  Don’t modify our views, procedures, functions or any of our DB artifacts and don’t access/call any of our DB artifacts including views, defined types, functions and procedures from your extensions.

3.  To access our DB artifacts, use CRT data service. Ex: if you want to extend our product search view to search some custom fields or to show custom columns in show journal views the don’t modify our views or procedures or functions in SQL use the respective CRT data service and do the extension either by overriding or using post triggers and then call your extended procedures.

    **Example:**

# DON'T DO THIS

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

1.  All the extension table should have grant permission on UersRole and DeployExtensibilityRole

```sql
    GRANT EXECUTE ON [ext].[EXTTABLENAME] TO [DeployExtensibilityRole];

    GO

     
    GRANT EXECUTE ON [ext].[EXTTABLENAME] TO [UsersRole];

    GO
```

2.  Grant DataSyncUsersRole permission if you table is going to send receive data from HQ.

```sql
 GRANT SELECT, INSERT, UPDATE, DELETE ON OBJECT::[ext].[EXTTABLENAME] TO [DataSyncUsersRole]

 GO
```

1.  If your creating extended table and want to sync the data back to HQ then have the primary column of the parent table in the extended table.

2.  Always prefix your table. Ex:ContosoRetailTransactionTable, so that you can avoid conflicts with other partner/ISV customization.

**Attributes:**

We extended the attribute framework in HQ to support attributes for Customers, Customer orders, cash and carry transactions and call center orders.

**Customer attributes** - With the new customer attribute framework, you can use configurations to add new fields to the customer add/edit or customer details screens in POS or HQ. After configuring the customer attribute group in retail parameters, POS and HQ will automatically show up the new attribute without any code change or customization. The screen layout designer will also be configured to show the customer attributes in the transaction screen - customer panel.

**Order attributes** - The attribute framework will be extended to support attributes in cash and carry transactions, customer orders, and call center orders. You will be able to edit and set values directly in HQ or in CRT. All this can be done through configurations, without any database changes. (You can customization the attribute values for core business logic, not required for basic CRUD operations.)

Previously you have to create new table in HQ, channel DB and modify CRT to do this. Now all the attribute creation can be done through configuration. Before creating the extension table for customer master or for order/transaction scenarios, read the attribute article on customer and order attributes.

**New table:**

In this scenario we will talk about to create a new table and add it to the channel DB. We did changes in CRT to make all extension code have access to the ext schema.

**Steps to create a new table:**

1.  Create a new table in the channel database in the **ext schema** either using SQL server management studio designer or using SQL scripts.

 **Sample script:**

```sql
     /**

     * SAMPLE CODE NOTICE

     * THIS SAMPLE CODE IS MADE AVAILABLE AS IS. MICROSOFT MAKES NO WARRANTIES,

     * WHETHER EXPRESS OR IMPLIED, OF FITNESS FOR A PARTICULAR PURPOSE, OF ACCURACY OR COMPLETENESS OF RESPONSES, OF RESULTS, OR CONDITIONS OF MERCHANTABILITY.

     * THE ENTIRE RISK OF THE USE OR THE RESULTS FROM THE USE OF THIS SAMPLE CODE REMAINS WITH THE USER.

     * NO TECHNICAL SUPPORT IS PROVIDED. YOU MAY NOT DISTRIBUTE THIS CODE UNLESS YOU HAVE A LICENSE AGREEMENT WITH MICROSOFT THAT ALLOWS YOU TO DO SO.

     */

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

     )WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]

     ) ON [PRIMARY]

     ALTER TABLE [ext].[CONTOSORETAILSTOREHOURSTABLE] WITH CHECK ADD CHECK (([RECID]&lt;&gt;(0)))

     END

     GO

     GRANT SELECT, INSERT, UPDATE, DELETE ON OBJECT::[ext].[CONTOSORETAILSTOREHOURSTABLE] TO [DataSyncUsersRole]

     GO

    **Extending existing table:**

    Even if you are extending existing table, Ex: if you want to store some custom fields in transaction table, sales line or payment trans etc. you should not modify our tables. Either use attributes if supported for that entity or create extended table (new table) with same primary key as the parent table.

    **Sample:**

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
**New Views, Stored procedure, functions or defined types:**

All new stored procedures, views or functions should be created in the ext schema like the tables and don’t access/call our DB artifacts from your procedures, views or functions.

**Deployment check:**

During deployment we will check if there is any modification to our DB artifacts, If you modified any of our crt, ax or dbo schema objects or accessed it for any scenario directly in SQL then deployment will be failed, you should follow the best practices mentioned above.

