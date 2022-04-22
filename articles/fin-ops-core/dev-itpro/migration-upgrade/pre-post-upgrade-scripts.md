---
# required metadata

title: Troubleshoot PreSync and PostSync upgrade scripts during upgrade to Dynamics 365 Finance + Operations
description: This topic provides troubleshooting information for the PreSync and PostSync upgrade scripts that are run as part of the upgrade from Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 Finance + Operations. 
author: ttreen 
ms.date: 04/22/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Troubleshoot PreSync and PostSync upgrade scripts during upgrade to Dynamics 365 Finance + Operations

[!include[banner](../includes/banner.md)]

This topic provides troubleshooting information for the PreSync and PostSync upgrade scripts that are run as part of the upgrade from Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 Finance + Operations. 

## Scenario 1: Error - Duplicate key was found for the object name 'dbo.INVENTDIM' and the index name 'I_XXXSHA1HASHIDX'

During the final sync you may see an error in the downloaded sync log similar to the following (table IDs in the index may be different):

`> _The CREATE UNIQUE INDEX statement terminated because a duplicate key was found for the object name 'dbo.INVENTDIM' and the index name 'I_698SHA1HASHIDX'. The duplicate key value is (5637144576, gsmp, B92BAF2504FD67FC15A56F2DFACE09127715B54B). The statement has been terminated. CREATE UNIQUE INDEX I_698SHA1HASHIDX ON DBO.INVENTDIM(PARTITION,DATAAREAID,SHA1HASHHEX) WITH (MAXDOP = 1) ;_`

**Causes:**

There can be a few causes for this issue:

- This error normally appears when the string size of one of the dimension fields in the **InventDim** table has been extended in Dynamics AX 2012, but the same fields in Dynamics 365 were not extended. The extension could have been made on the table directly or in the extended data types (EDT) that the fields are derived from.

    The following fields are used to create the hash value:
    - ConfigId,InventBatchId
    - InventColorId
    - InventGtdId_RU
    - InventLocationId
    - InventOwnerId_RU
    - InventProfileId_RU
    - InventSerialId
    - InventSiteId
    - InventSizeId
    - InventStatusId
    - InventStyleId
    - LicensePlateId
    - WMSlocationId

    The data in the table isn't truncated, but the data gets truncated in the buffer at runtime when the hash value is created. 

    For example, **InventSizeId** has a default size of 10 characters, but in AX 2012 the customer increased the size to 12. If you then have two values like **1234567890AA** and **1234567890BB**, when these values are read into the buffer at runtime both will be shortened to **1234567890**. Therefore it's a duplicate in the runtime buffer and the upgrade method **ReleaseUpdateDB72_Invent::updateSHA1HashHexInInventDim** that generates the new hash value will not generate all hash values as unique. 

- The data upgrade job didn't run or complete as expected. 

    First, run the following SQL query:

    ```SQL
    SELECT PARTITION, DATAAREAID, SHA1HASHHEX, COUNT(*)
    FROM INVENTDIM
    GROUP BY PARTITION, DATAAREAID, SHA1HASHHEX
    HAVING COUNT(*) > 1
    ```
    If you find that **SHA1HASHHEX** is blank, then the job didn't run. In this case, use the following command to check the data upgrade jobs:

    ```SQL
    select * from RELEASEUPDATESCRIPTSLOG
    where METHODNAME = 'updateSHA1HashHexInInventDim'
    ```
    **Solution:**

    1. Get the customer to compare the field sizes in the Dynamics AX 2012 **InventDim** table to the field sizes in Dynamics 365. If there are any differences, to fix these the customer must extend the string size for the associated fields using a customization extension.
    2. If the job didn't run, try to resume the upgrade from the AX 2012 Database Upgrade Toolkit for Dynamics 365, or rerun the runbook step if on a Tier-1 development environment. 

## Scenario 2: Error running ReleaseUpdateDB72_FixedAssets::postSyncUpgradeAssetDepBookJournalTransDimResolve job

When running the post-sync job **ReleaseUpdateDB72_FixedAssets::postSyncUpgradeAssetDepBookJournalTransDimResolve**, you may get the following error:

`> Unable to return DimensionAttributeValue record for dimension SystemGeneratedAttributeFixedAsset with value ASSET00001, in legal entity USMF, because a record doesn't exist in table AssetTable through view DimAttributeAssetTable. Batch task failed: Unable to return DimensionAttributeValue record for dimension SystemGeneratedAttributeFixedAsset with value ASSET00001, in legal entity USMF, because a record doesn't exist in table AssetTable through view DimAttributeAssetTable.`
 
**Cause:**

This error is due to assets being purged or removed from the Dynamics AX 2012 **AssetTable**, but the associated records in the **ledgerjournaltrans_asset** table remain.

You can check for these orphaned records using the following SQL script:

```SQL
select * from ledgerjournaltrans_asset
where assetid not in (select assetid from assettable)
```
**Solution:**

> [!NOTE]
> Ensure you have database backups before deleting any data.

The records can be deleted by running the following SQL statement:

```SQL
--
-- This source code or script is freeware and is provided on an "as is" basis without warranties of any kind, 
-- whether express or implied, including without limitation warranties that the code is free of defect, 
-- fit for a particular purpose or non-infringing.  The entire risk as to the quality and performance of 
-- the code is with the end user.
--
delete from ledgerjournaltrans_asset
where assetid not in (select assetid from assettable)
```

## Scenario 3: Error running ReleaseUpdateDB10_CaseManagement::updateCaseCategoryTypeMajor job

When running the post-sync job **ReleaseUpdateDB10_CaseManagement::updateCaseCategoryTypeMajor**, you get the following error from the **ReleaseUpdateScriptsErrorLog** table:

`> === start of x++ data upgrade scripts that failed during the 'PostSync' step. ===
{ ClassName: "ReleaseUpdateDB10_CaseManagement", MethodName: "updateCaseCategoryTypeMajor", Company: "DAT", DataParition: "initial", ErrorCount: "1", ErrorMessage: " Cannot edit a record in Case category Security by Role (CaseCategoryRole). Category type: None.
The record already exists. Batch task failed: Cannot edit a record in Case category Security by Role (CaseCategoryRole). Category type: None.
The record already exists." }
{ ClassName: "ReleaseUpdateDB72
=== start of x++ data upgrade scripts that failed during the 'PostSync' step. ===
{ ClassName: "ReleaseUpdateDB10_CaseManagement", MethodName: "updateCaseCategoryTypeMajor", Company: "DAT", DataParition: "initial", ErrorCount: "1", ErrorMessage: " Cannot edit a record in Case category Security by Role (CaseCategoryRole). Category type: None.
The record already exists. Batch task failed: Cannot edit a record in Case category Security by Role (CaseCategoryRole). Category type: None.
The record already exists." }
_Stopped DBSync monitoring. Microsot.Dynamics.Ax.Xpp.ErrorException: Failed to create a session; confirm that the user has the proper privileges to log on to Microsoft Dynamics 365 for Finance and Operations._`

**Cause:**

The cause for this error is that in Dynamics AX 2012, the enum **CaseCategoryType** type **Web** in most cases uses the value "9". In Dynamics 365, the **Web** value is deprecated, and the same value in Dynamics 365 can be used by enum value **CaseCategoryType::FMLA**. The reason for this is that the enum is extensible, so it can be assigned the same value. 

To check the enum values, run the following SQL statement:

```SQL
select t1.name as enumvaluename, t1.enumvalue
from enumvaluetable  t1
join enumidtable t2 on t2.id = t1.enumid
where t2.name = 'CaseCategoryType'
```
**Solution:**

1. Remove the record in the **CaseCategoryRole** table for type **Web**.
1. Check the value of the enum in Dynamics AX 2012. As mentioned previously, in most cases this will be "9".
1. Delete the record in the **CaseCategoryRole** table using the following SQL statement (edit value as needed):

```SQL
--
-- This source code or script is freeware and is provided on an "as is" basis without warranties of any kind, 
-- whether express or implied, including without limitation warranties that the code is free of defect, 
-- fit for a particular purpose or non-infringing.  The entire risk as to the quality and performance of 
-- the code is with the end user.
--
delete from CaseCategoryRole
where CaseCategoryType = 9 --Edit to be the enum value of CaseCategoryType::Web in AX2012
```

## Scenario 4: Error: Cannot edit a record in Table Name (TableName) - Invalid column name 'COLUMNNAME'

If you get errors similar to the one shown below when running the PreSync or PostSync upgrade jobs, and also find that the field being referenced is no longer in Dynamics 365, it could be related to legacy table triggers.

`> Cannot edit a record in Table Name (TableName).
The SQL database has issued an error. Object Server DataUpgrade_Batch: [Microsoft][ODBC Driver 17 for SQL Server][SQL Server]Invalid column name 'DEPRACATEDCOLUMNNAME'. UPDATE T1 SET VALUE=?,RECVERSION=? FROM TABLENAME session 10 (Admin) Batch task failed: Cannot edit a record in Bank accounts (TableName).
The SQL database has issued an error." `

**Solution:**

1. Connect to the database using SQL Management Studio.
1. In the Object Explorer, expand the database and tables and locate the table referenced in the error.
1. Review the triggers on that table to check for custom triggers. Most standard triggers created in Dynamics 365 will be be prefixed with **SysDbLog**, **SysEvenCud**, and **AIF** (list not inclusive).
1. To script the custom triggers you think maybe causing the issue, right-click on each trigger and select **Script Trigger as \> CREATE To \> New Query Editor Window**.
1. Once the script is completed, go to **Edit \> Find** to check if the field referenced in the error exists in the script. If you find a match in the trigger, then you will need to disable or drop the trigger. 

