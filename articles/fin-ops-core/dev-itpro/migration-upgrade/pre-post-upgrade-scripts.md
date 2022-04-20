---
# required metadata

title: Pre/post upgrade scripts
description: An overview sentence that describes what this article is all about.
author: ttreen 
ms.date: 04/08/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Pre Sync and Post Sync Upgrade Steps Troubleshooting

[!include[banner](../includes/banner.md)]

This topic provides troubleshooting information for the PreSync and PostSync upgrade sctipts that are run as part of an upgrade frin Microsoft Dynamics AX 2012 to Microsoft Dynamics 365 Finance + Operations 

## Scenario 1: Error - Duplicate key was found for the object name 'dbo.INVENTDIM' and the index name 'I_XXXSHA1HASHIDX'
During the final sync you see an error in the downloaded sync log similar to the following (note table IDs in the index maybe different):
> _The CREATE UNIQUE INDEX statement terminated because a duplicate key was found for the object name 'dbo.INVENTDIM' and the index name 'I_698SHA1HASHIDX'. The duplicate key value is (5637144576, gsmp, B92BAF2504FD67FC15A56F2DFACE09127715B54B). The statement has been terminated. CREATE UNIQUE INDEX I_698SHA1HASHIDX ON DBO.INVENTDIM(PARTITION,DATAAREAID,SHA1HASHHEX) WITH (MAXDOP = 1) ;_

**Cause:**
There can be a few issues for this issue, see below:
1. This error normally comes up when the string size of one of the dimension fields in table **InventDim** has been extended in AX 2012, but the smae fields in D365 were not.  The extension could have been made on the table directly or the extended data types (EDT) that the fields are derived from.

   The fields used to create the HASH are as follows:
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

   The actual data in the table isn't truncated, but it gets truncated in the buffer at runtime when the HASH value was created. 

   For example: INVENTSIZEID has a default size of 10 characters, but in AX 2012 the customer increased this to 12. Then, if you have two values like **1234567890AA** and **1234567890BB**, when these are read into the buffer at runtime both will just be **1234567890**. Therefore, it's a duplicate in the runtime buffer and the upgrade method **ReleaseUpdateDB72_Invent::updateSHA1HashHexInInventDim** which generates the new HASH will not generate all the HASH values as unique. 

2. The data upgrade job didn't run or complete as expected. 
Run the following SQL Query:

```SQL
SELECT PARTITION, DATAAREAID, SHA1HASHHEX, COUNT(*)
FROM INVENTDIM
GROUP BY PARTITION, DATAAREAID, SHA1HASHHEX
HAVING COUNT(*) > 1
```
If you find that the SHA1HASHHEX is blank then the job didn't run. In that case use the following to check the data upgrade jobs:
```SQL
select * from RELEASEUPDATESCRIPTSLOG
where METHODNAME = 'updateSHA1HashHexInInventDim'
```
**Solution:**
1. Get the customer to compare the field sizes in AX2012 on the InventDim table to the field sizes on D365. If there any differences, then the customer will need to fix this by extending the string size for the associated fields through a customization extension.
2. If the job didn't run, try to resume the upgrade from the Upgrade Toolkit, or rerun the runbook step if on a Dev\Tier 1 environment. 

## Scenario 2: Error in ReleaseUpdateDB72_FixedAssets::postSyncUpgradeAssetDepBookJournalTransDimResolve
> Unable to return DimensionAttributeValue record for dimension SystemGeneratedAttributeFixedAsset with value ASSET00001, in legal entity USMF, because a record doesn't exist in table AssetTable through view DimAttributeAssetTable. Batch task failed: Unable to return DimensionAttributeValue record for dimension SystemGeneratedAttributeFixedAsset with value ASSET00001, in legal entity USMF, because a record doesn't exist in table AssetTable through view DimAttributeAssetTable.
 
**Cause:**
This is due to assets being purged or removed in AX 2012 from the AssetTable, but the associated records in the ledgerjournaltrans_asset remain.
You can check for these orphaned records using the following SQL:
```SQL
select * from ledgerjournaltrans_asset
where assetid not in (select assetid from assettable)
```
**Solution:**
The records can be deleted using the following SQL:
**Note:** Please ensure you have database backups before deleting any data
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

## Scenario 3: Error on ReleaseUpdateDB10_CaseManagement::updateCaseCategoryTypeMajor
During the post-sync job ReleaseUpdateDB10_CaseManagement::updateCaseCategoryTypeMajor you get the following error from the ReleaseUpdateScriptsErrorLog table:
> === start of x++ data upgrade scripts that failed during the 'PostSync' step. ===
{ ClassName: "ReleaseUpdateDB10_CaseManagement", MethodName: "updateCaseCategoryTypeMajor", Company: "DAT", DataParition: "initial", ErrorCount: "1", ErrorMessage: " Cannot edit a record in Case category Security by Role (CaseCategoryRole). Category type: None.
The record already exists. Batch task failed: Cannot edit a record in Case category Security by Role (CaseCategoryRole). Category type: None.
The record already exists." }
{ ClassName: "ReleaseUpdateDB72
=== start of x++ data upgrade scripts that failed during the 'PostSync' step. ===
{ ClassName: "ReleaseUpdateDB10_CaseManagement", MethodName: "updateCaseCategoryTypeMajor", Company: "DAT", DataParition: "initial", ErrorCount: "1", ErrorMessage: " Cannot edit a record in Case category Security by Role (CaseCategoryRole). Category type: None.
The record already exists. Batch task failed: Cannot edit a record in Case category Security by Role (CaseCategoryRole). Category type: None.
The record already exists." }
_Stopped DBSync monitoring. Microsot.Dynamics.Ax.Xpp.ErrorException: Failed to create a session; confirm that the user has the proper privileges to log on to Microsoft Dynamics 365 for Finance and Operations._

**Cause:**
The reason for this is that in AX 2012 the enum **CaseCategoryType**, value **Web** in most cases used value 9:
In D365 this **web** value is deprecated, and the same value in D365 can be used by enum value CaseCategoryType::FMLA
The reason for this is that the enum is extensible, so it can be assigned the same value. 
To check the enum values run the following SQL:
```SQL
select t1.name as enumvaluename, t1.enumvalue
from enumvaluetable  t1
join enumidtable t2 on t2.id = t1.enumid
where t2.name = 'CaseCategoryType'
```
**Solution:**
1. The record in CaseCategoryRole for type **Web** needs to be removed.
2. Check the value of the enum in AX 2012, as per the screenshot above. As mentioned in most cases this will be 9.
3. Delete the record in table CaseCategoryRole using the following SQL statement (edit value as needed):
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
If you get errors when running the pre-sync or post-syn upgrade jobs similar to the one below, and find the field being referenced is no longer in D365; it could be related to legacy table triggers.
>Cannot edit a record in Table Name (TableName).
The SQL database has issued an error. Object Server DataUpgrade_Batch: [Microsoft][ODBC Driver 17 for SQL Server][SQL Server]Invalid column name 'DEPRACATEDCOLUMNNAME'. UPDATE T1 SET VALUE=?,RECVERSION=? FROM TABLENAME session 10 (Admin) Batch task failed: Cannot edit a record in Bank accounts (TableName).
The SQL database has issued an error." 

**Solution:**
1. Connect to the database via SQL Management Studio
2. In the Obejct Explorer, expand out the database and tables and locate the table in question.
3. Review the triggers on that table to check for custom triggers.
   - Standard triggers created in D365 will be be prefixed with SysDbLog, SysEvenCud, AIF (list not inclusive of all D365 ones)
4. Script the custom triggers you think maybe causing the issue, you can right click on the trigger and select **Script Trigger as** > **CREATE To** > **New Query Editor Window**
5. Once the script is completed, go to menu **Edit > Find** to check for the field in the error exists in the script. If you find a match in the trigger, then you will need to disable or drop the trigger. 

