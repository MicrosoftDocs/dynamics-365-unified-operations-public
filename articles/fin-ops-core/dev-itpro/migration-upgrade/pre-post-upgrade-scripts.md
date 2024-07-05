---
title: Troubleshoot PreSync and PostSync upgrade scripts during upgrade to Dynamics 365 Finance + Operations
description: Learn about troubleshooting for the PreSync and PostSync upgrade scripts, run as part of the upgrade from Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations.
author: ttreen
ms.author: ttreen
ms.topic: article
ms.date: 04/26/2022
ms.reviewer: johnmichalakffin
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.search.form: 2022-04-08
ms.service: dynamics-365-op
---

# Troubleshoot PreSync and PostSync upgrade scripts during upgrade to Dynamics 365 Finance + Operations

[!include[banner](../includes/banner.md)]

This article provides troubleshooting information for the PreSync and PostSync upgrade scripts that are run as part of the upgrade from Microsoft Dynamics AX 2012 to Dynamics 365 Finance + Operations (on-premises).

## Scenario 1: You receive the following error: "Duplicate key was found for the object name 'dbo.INVENTDIM' and the index name 'I_XXXSHA1HASHIDX'."

During the final synchronization, you might see an error that resembles the following example in the downloaded synchronization log. (The table IDs in the index might differ.)

> The CREATE UNIQUE INDEX statement terminated because a duplicate key was found for the object name 'dbo.INVENTDIM' and the index name 'I\_698SHA1HASHIDX'. The duplicate key value is (5637144576, gsmp, B92BAF2504FD67FC15A56F2DFACE09127715B54B). The statement has been terminated. CREATE UNIQUE INDEX I\_698SHA1HASHIDX ON DBO.INVENTDIM(PARTITION,DATAAREAID,SHA1HASHHEX) WITH (MAXDOP = 1) ;

**Causes**

There can be a few causes for this issue:

- The error typically appears when the string size of one of the dimension fields in the **InventDim** table has been extended in Dynamics AX 2012, but the same field wasn't extended in Dynamics 365. The extension might have been made directly on the table or in the extended data types (EDT) that the fields are derived from.

    The following fields are used to create the hash value:

    - ConfigId,InventBatchId
    - InventColorId
    - InventGtdId\_RU
    - InventLocationId
    - InventOwnerId\_RU
    - InventProfileId\_RU
    - InventSerialId
    - InventSiteId
    - InventSizeId
    - InventStatusId
    - InventStyleId
    - LicensePlateId
    - WMSlocationId

    The data in the table isn't truncated. However, the data is truncated in the buffer at runtime when the hash value is created.

    For example, the **InventSizeId** field has a default size of 10 characters, but the customer increased the size to 12 characters in Dynamics AX 2012. In this case, the field values **1234567890AA** and **1234567890BB** will both be shortened to **1234567890** when they are read into the buffer at runtime. Therefore, there will be a duplicate value in the runtime buffer, and the **ReleaseUpdateDB72\_Invent::updateSHA1HashHexInInventDim** upgrade method that generates the new hash value won't generate all hash values as unique.

- The data upgrade job didn't run as expected, or it wasn't completed as expected.

    First run the following SQL query.

    ```SQL
    SELECT PARTITION, DATAAREAID, SHA1HASHHEX, COUNT(*)
    FROM INVENTDIM
    GROUP BY PARTITION, DATAAREAID, SHA1HASHHEX
    HAVING COUNT(*) > 1
    ```

    If **SHA1HASHHEX** is blank, the job didn't run. In this case, use the following command to check the data upgrade jobs.

    ```SQL
    select * from RELEASEUPDATESCRIPTSLOG
    where METHODNAME = 'updateSHA1HashHexInInventDim'
    ```

    **Solution**

    1. Compare the field sizes in the Dynamics AX 2012 **InventDim** table with the field sizes in Dynamics 365. If there are any differences, you must reconcile them by using a customization extension to extend the string size for the associated fields.
    1. If the job didn't run, try to resume the upgrade from the AX 2012 Database Upgrade Toolkit for Dynamics 365, or rerun the runbook step if you're on a Tier-1 development environment.

## Scenario 2: An error occurs when you run the ReleaseUpdateDB72_FixedAssets::postSyncUpgradeAssetDepBookJournalTransDimResolve job

When you run the **ReleaseUpdateDB72\_FixedAssets::postSyncUpgradeAssetDepBookJournalTransDimResolve** post-synchronization job, you might receive the following error:

> Unable to return DimensionAttributeValue record for dimension SystemGeneratedAttributeFixedAsset with value ASSET00001, in legal entity USMF, because a record doesn't exist in table AssetTable through view DimAttributeAssetTable. Batch task failed: Unable to return DimensionAttributeValue record for dimension SystemGeneratedAttributeFixedAsset with value ASSET00001, in legal entity USMF, because a record doesn't exist in table AssetTable through view DimAttributeAssetTable.

**Cause**

This error occurs because assets were purged or removed from the Dynamics AX 2012 **AssetTable** table, but the associated records in the **ledgerjournaltrans\_asset** table remain.

You can check for these orphaned records by using the following SQL script.

```SQL
select * from ledgerjournaltrans_asset
where assetid not in (select assetid from assettable)
```

**Solution**

> [!IMPORTANT]
> Before you delete any data, make sure that you have database backups.

You can delete the records by running the following SQL statement.

```SQL
--
-- This source code or script is freeware and is provided on an "as is" basis without warranties of any kind, 
-- whether express or implied, including without limitation warranties that the code is free of defect, 
-- fit for a particular purpose or non-infringing. The entire risk as to the quality and performance of 
-- the code is with the end user.
--
delete from ledgerjournaltrans_asset
where assetid not in (select assetid from assettable)
```

## Scenario 3: An error occurs when you run the ReleaseUpdateDB10_CaseManagement::updateCaseCategoryTypeMajor job

When you run the **ReleaseUpdateDB10\_CaseManagement::updateCaseCategoryTypeMajor**  post-synchronization job, you might receive the following error from the **ReleaseUpdateScriptsErrorLog** table:

> === start of x++ data upgrade scripts that failed during the 'PostSync' step. ===  
{ ClassName: "ReleaseUpdateDB10\_CaseManagement", MethodName: "updateCaseCategoryTypeMajor", Company: "DAT", DataParition: "initial", ErrorCount: "1", ErrorMessage: " Cannot edit a record in Case category Security by Role (CaseCategoryRole). Category type: None.  
The record already exists. Batch task failed: Cannot edit a record in Case category Security by Role (CaseCategoryRole). Category type: None.  
The record already exists." }  
{ ClassName: "ReleaseUpdateDB72  
=== start of x++ data upgrade scripts that failed during the 'PostSync' step. ===  
{ ClassName: "ReleaseUpdateDB10\_CaseManagement", MethodName: "updateCaseCategoryTypeMajor", Company: "DAT", DataParition: "initial", ErrorCount: "1", ErrorMessage: " Cannot edit a record in Case category Security by Role (CaseCategoryRole). Category type: None.  
The record already exists. Batch task failed: Cannot edit a record in Case category Security by Role (CaseCategoryRole). Category type: None.  
The record already exists." }  
_Stopped DBSync monitoring. Microsot.Dynamics.Ax.Xpp.ErrorException: Failed to create a session; confirm that the user has the proper privileges to log on to Microsoft Dynamics 365 Finance._

**Cause**

This error occurs because, in Dynamics AX 2012, the **CaseCategoryType** enumeration (enum) of the **Web** type uses the value "9" in most cases. However, in Dynamics 365, the **Web** value is deprecated, and the same value can be used by the enum value **CaseCategoryType::FMLA**. Because the enum is extensible, it can be assigned the same value.

To check the enum values, run the following SQL statement.

```SQL
select t1.name as enumvaluename, t1.enumvalue
from enumvaluetable  t1
join enumidtable t2 on t2.id = t1.enumid
where t2.name = 'CaseCategoryType'
```

**Solution**

1. In the **CaseCategoryRole** table, remove the record for the **Web** type.
1. Check the value of the enum in Dynamics AX 2012. As was previously mentioned, this value will be "9" in most cases.
1. Delete the record in the **CaseCategoryRole** table by using the following SQL statement. (Edit the value as required.)

```SQL
--
-- This source code or script is freeware and is provided on an "as is" basis without warranties of any kind, 
-- whether express or implied, including without limitation warranties that the code is free of defect, 
-- fit for a particular purpose or non-infringing. The entire risk as to the quality and performance of 
-- the code is with the end user.
--
delete from CaseCategoryRole
where CaseCategoryType = 9 --Edit to be the enum value of CaseCategoryType::Web in AX2012
```

## Scenario 4: You receive the following error: "Cannot edit a record in Table Name (TableName) - Invalid column name 'COLUMNNAME'."

When you run the PreSync or PostSync upgrade jobs, you might receive an error that resembles the following example. If you find that the referenced field is no longer in Dynamics 365, the error might be related to legacy table triggers.

> Cannot edit a record in Table Name (TableName).  
The SQL database has issued an error. Object Server DataUpgrade\_Batch: \[Microsoft\]\[ODBC Driver 17 for SQL Server\]\[SQL Server\]Invalid column name 'DEPRACATEDCOLUMNNAME'. UPDATE T1 SET VALUE=?,RECVERSION=? FROM TABLENAME session 10 (Admin) Batch task failed: Cannot edit a record in Bank accounts (TableName).  
The SQL database has issued an error."

**Solution**

1. Connect to the database by using SQL Management Studio (SSMS).
1. In Object Explorer, expand the database and tables, and find the table that is referenced in the error message.
1. Review the triggers on that table to check for custom triggers. Most standard triggers that are created in Dynamics 365 will be prefixed with, for example, **SysDbLog**, **SysEvenCud**, or **AIF**.
1. To script the custom triggers that you think might be causing the issue, select and hold (or right-click) each trigger, and then select **Script Trigger as \> Create To \> New Query Editor Window**.
1. After the script is completed, go to **Edit \> Find** to determine whether the field that is referenced in the error message exists in the script. If you find a match in the trigger, you must disable or drop the trigger.

