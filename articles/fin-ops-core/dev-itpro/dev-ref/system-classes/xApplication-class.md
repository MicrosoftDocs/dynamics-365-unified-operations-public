---
title: xApplication class
description: This topic describes the xApplication class.
author: robinarh
manager: tonyafehr
ms.date: 06/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

audience: Developer
ms.reviewer: rhaertle
ms.search.scope: Operations
ms.search.region: Global
ms.author: rhaertle
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Class xApplication

[!include [banner](../../includes/banner.md)]


```xpp
class xApplication extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                                                                                                              | Description                                                                                                                                                                     |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean IsTablePerHierarchyMode()                                                                                                                                                                                            | Determines whether the system is being run with all table inheritance hierarchies flattened (Table per hierarchy mode).                                                         |
| public str buildNo()                                                                                                                                                                                                                |                                                                                                                                                                                 |
| public boolean canDeleteCompany(SelectableDataArea company)                                                                                                                                                                         |                                                                                                                                                                                 |
| public int countOfTopLevelFormsOpened()                                                                                                                                                                                             |                                                                                                                                                                                 |
| public Company company(\[SelectableDataArea company\])                                                                                                                                                                              |                                                                                                                                                                                 |
| public Int64 curTransactionId(\[boolean ForceTakeNumber\])                                                                                                                                                                          |                                                                                                                                                                                 |
| public boolean dbSynchronize(\[TableId tableId\], \[boolean checkAsNeeded\], \[boolean continueOnError\], \[boolean showProgress\], \[container checkSyncTables\], \[boolean createAllIndexes\], \[boolean useLockForSingleTable\]) |                                                                                                                                                                                 |
| public str getSameNameDifferentIdFields()                                                                                                                                                                                           |                                                                                                                                                                                 |
| public Map getServiceHostStatus()                                                                                                                                                                                                   |                                                                                                                                                                                 |
| public boolean isCheckedMode()                                                                                                                                                                                                      |                                                                                                                                                                                 |
| public boolean isConfigMode()                                                                                                                                                                                                       |                                                                                                                                                                                 |
| public boolean isDemoMode()                                                                                                                                                                                                         |                                                                                                                                                                                 |
| public boolean isSqlConnected()                                                                                                                                                                                                     |                                                                                                                                                                                 |
| public int numberOfTreeNodesLoaded()                                                                                                                                                                                                |                                                                                                                                                                                 |
| public str releaseVersion()                                                                                                                                                                                                         |                                                                                                                                                                                 |
| public boolean setDefaultCompany(SelectableDataArea company)                                                                                                                                                                        |                                                                                                                                                                                 |
| public int ttsLevel()                                                                                                                                                                                                               |                                                                                                                                                                                 |
| public int ttsVersion()                                                                                                                                                                                                             |                                                                                                                                                                                 |
| ::public static boolean CheckUserExistsInAnyPartition(str userId)                                                                                                                                                                   | Checks whether the given user is present in any partition.                                                                                                                      |
| ::public static str getFolderPath(int folder)                                                                                                                                                                                       |                                                                                                                                                                                 |
| ::public static str getVSAssembliesPath()                                                                                                                                                                                           |                                                                                                                                                                                 |
| ::public static boolean ilCacheContains(str owner, str key)                                                                                                                                                                         |                                                                                                                                                                                 |
| ::public static str ilCacheDelete(str owner, str key)                                                                                                                                                                               |                                                                                                                                                                                 |
| ::public static str ilCacheFind(str owner, str key)                                                                                                                                                                                 |                                                                                                                                                                                 |
| ::public static boolean initPartition(Partition partition)                                                                                                                                                                          | Initializes a given partition by creating the DAT company and the Admin user.                                                                                                   |
| ::public static boolean isServiceRegisteredOnClient(ClassId classId)                                                                                                                                                                |                                                                                                                                                                                 |
| ::public static boolean IsSinglePartitionSystem()                                                                                                                                                                                   | Evaluates whether the deployment has a single partition or multiple partitions.                                                                                                 |
| ::public static CLRObject XppILAppDomain()                                                                                                                                                                                          |                                                                                                                                                                                 |
| public boolean isInTransactionScope()                                                                                                                                                                                               |                                                                                                                                                                                 |
| public Int64 transactionScopeCommitLevel()                                                                                                                                                                                          |                                                                                                                                                                                 |
| public container Encrypt(str input)                                                                                                                                                                                                 |                                                                                                                                                                                 |
| public str Decrypt(container cipher)                                                                                                                                                                                                |                                                                                                                                                                                 |
| public System.Security.SecureString decryptToSecureString(container cipher)                                                                                                                                                         |                                                                                                                                                                                 |
| public container encryptFromSecureString(System.Security.SecureString input)                                                                                                                                                        |                                                                                                                                                                                 |
| public container EncryptForPurpose(str input, str purpose)                                                                                                                                                                          |                                                                                                                                                                                 |
| public str DecryptForPurpose(container cipher, str purpose)                                                                                                                                                                         |                                                                                                                                                                                 |
| public System.Security.SecureString decryptToSecureStringForPurpose(container cipher, str purpose)                                                                                                                                  |                                                                                                                                                                                 |
| public container encryptFromSecureStringForPurpose(System.Security.SecureString input, str purpose)                                                                                                                                 |                                                                                                                                                                                 |
| public str convertToUnsecureString(System.Security.SecureString secureString)                                                                                                                                                       |                                                                                                                                                                                 |
| public System.Security.SecureString convertToSecureString(str unsecureString)                                                                                                                                                       |                                                                                                                                                                                 |
| ::public static void startBatch()                                                                                                                                                                                                   |                                                                                                                                                                                 |
| public void deleteCompany(SelectableDataArea company)                                                                                                                                                                               |                                                                                                                                                                                 |
| public void ttsabort()                                                                                                                                                                                                              |                                                                                                                                                                                 |
| public void transactionScopeCommit()                                                                                                                                                                                                |                                                                                                                                                                                 |
| public void new()                                                                                                                                                                                                                   | Initializes a new instance of the xApplication class.                                                                                                                           |
| ::public static void stopBatch()                                                                                                                                                                                                    |                                                                                                                                                                                 |
| public void logRenameKey(Common recordOrig, Common recordUpdated, container changedFields)                                                                                                                                          |                                                                                                                                                                                 |
| public void startup(str startupCmd, str buildNumber)                                                                                                                                                                                |                                                                                                                                                                                 |
| public void RedirectToDashboard()                                                                                                                                                                                                   |                                                                                                                                                                                 |
| public void insertXReferences()                                                                                                                                                                                                     | Is invoked by the framework when cross-reference information should be inserted into the database.                                                                              |
| public void logUpdate(Common recordOrig, Common recordUpdated, container changedFields)                                                                                                                                             |                                                                                                                                                                                 |
| public void setStartPage(\[SysUserInfoStartPage startpage\])                                                                                                                                                                        |                                                                                                                                                                                 |
| ::public static void ilCacheInsert(str owner, str key, str value)                                                                                                                                                                   |                                                                                                                                                                                 |
| public void clearManagedCaches()                                                                                                                                                                                                    |                                                                                                                                                                                 |
| public void eventDelete(Common recordDeleted)                                                                                                                                                                                       | Serves as a callback that is called by the kernel when a record in a table is deleted, provided that the kernel has been set up to monitor records in that table.               |
| public void enableCountryContextFilter()                                                                                                                                                                                            | Enables system-wide optimization in the data access layer, whereby fields that don't belong in the current company's country/region context are dropped from the SELECT query.  |
| public void setTheme(\[SysUserInfoTheme theme\])                                                                                                                                                                                    |                                                                                                                                                                                 |
| public void sysTrace(SysTraceType traceType, container traceInfo)                                                                                                                                                                   |                                                                                                                                                                                 |
| public void initGlobal(Info infoObject, VersionControl versionControlObject)                                                                                                                                                        |                                                                                                                                                                                 |
| public void transactionScopeRollback(Int64 commitLevel)                                                                                                                                                                             |                                                                                                                                                                                 |
| public void ttsbegin()                                                                                                                                                                                                              |                                                                                                                                                                                 |
| public void flushcompanycache(SelectableDataArea company)                                                                                                                                                                           |                                                                                                                                                                                 |
| public void logDelete(Common recordDeleted)                                                                                                                                                                                         |                                                                                                                                                                                 |
| ::public static void registerServiceOnClient(ClassId classId, str externalName)                                                                                                                                                     |                                                                                                                                                                                 |
| public void eventUpdate(Common recordOrig, Common recordUpdated, container changedFields)                                                                                                                                           | Serves as a callback that is called by the kernel when a record in a table is updated, provided that the kernel has been set up to monitor records in that table.               |
| public void transactionScopeBegin()                                                                                                                                                                                                 |                                                                                                                                                                                 |
| ::public static void checkForNewBatchJobs()                                                                                                                                                                                         |                                                                                                                                                                                 |
| public void disableCountryContextFilter()                                                                                                                                                                                           | Disables system-wide optimization in the data access layer, whereby fields that don't belong in the current company's country/region context are dropped from the SELECT query. |
| public void xref(str path, xRef x)                                                                                                                                                                                                  |                                                                                                                                                                                 |
| public void transactionScopeAbort()                                                                                                                                                                                                 |                                                                                                                                                                                 |
| public void eventRenameKey(Common recordOrig, Common recordUpdated, container changedFields)                                                                                                                                        | Serves as a callback that is called by the kernel when a primary key is renamed, provided that the kernel has been set up to monitor records in that table.                     |
| public void flushClientPerformanceOptions()                                                                                                                                                                                         |                                                                                                                                                                                 |
| ::public static void flushClientServices()                                                                                                                                                                                          |                                                                                                                                                                                 |
| public void restartServiceHost()                                                                                                                                                                                                    |                                                                                                                                                                                 |
| public void updateXrefTreeNode(TreeNode treeNode)                                                                                                                                                                                   | Is invoked by the framework when cross-reference information for the various node types is updated.                                                                             |
| public void ttscommit()                                                                                                                                                                                                             |                                                                                                                                                                                 |
| public void RequestCompanyChange(\[DataAreaSysCompany company\])                                                                                                                                                                    |                                                                                                                                                                                 |
| public void finalize()                                                                                                                                                                                                              |                                                                                                                                                                                 |
| public void eventInsert(Common recordInserted)                                                                                                                                                                                      | Serves as a callback that is called by the kernel when a record in a table is inserted, provided that the kernel has been set up to monitor records in that table.              |
| public void ttsNotifyBegin()                                                                                                                                                                                                        |                                                                                                                                                                                 |
| public void closeAllForms()                                                                                                                                                                                                         |                                                                                                                                                                                 |
| public void ttsNotifyCommit()                                                                                                                                                                                                       |                                                                                                                                                                                 |
| public void ttsNotifyPreCommit()                                                                                                                                                                                                    |                                                                                                                                                                                 |
| public void ttsNotifyPostBegin()                                                                                                                                                                                                    |                                                                                                                                                                                 |
| public void ttsNotifyAbort()                                                                                                                                                                                                        |                                                                                                                                                                                 |
| public void setDensity(\[SysUserInfoDensity theme\])                                                                                                                                                                                |                                                                                                                                                                                 |
| public void logInsert(Common recordInserted)                                                                                                                                                                                        |                                                                                                                                                                                 |

## Method IsTablePerHierarchyMode

Determines whether the system is being run with all table inheritance hierarchies flattened (Table per hierarchy mode).

```xpp
public boolean IsTablePerHierarchyMode()
```

### Return Value - IsTablePerHierarchyMode

true if system is being run in Table per hierarchy mode; otherwise, false.

## Method buildNo

```xpp
public str buildNo()
```

### Return Value - buildNo

## Method canDeleteCompany

```xpp
public boolean canDeleteCompany(SelectableDataArea company)
```

### Parameters - canDeleteCompany

company  

### Return Value - canDeleteCompany

## Method countOfTopLevelFormsOpened

```xpp
public int countOfTopLevelFormsOpened()
```

### Return Value - countOfTopLevelFormsOpened

## Method company

```xpp
public Company company([SelectableDataArea company])
```

### Parameters - company

company  

### Return Value - company

## Method curTransactionId

```xpp
public Int64 curTransactionId([boolean ForceTakeNumber])
```

### Parameters - curTransactionId

ForceTakeNumber  

### Return Value - curTransactionId

## Method dbSynchronize

```xpp
public boolean dbSynchronize([TableId tableId], [boolean checkAsNeeded], [boolean continueOnError], [boolean showProgress], [container checkSyncTables], [boolean createAllIndexes], [boolean useLockForSingleTable])
```

### Parameters - dbSynchronize

tableId  

<!-- -->

checkAsNeeded  

<!-- -->

continueOnError  

<!-- -->

showProgress  

<!-- -->

checkSyncTables  

<!-- -->

createAllIndexes  

<!-- -->

useLockForSingleTable  

### Return Value - dbSynchronize

## Method getSameNameDifferentIdFields

```xpp
public str getSameNameDifferentIdFields()
```

### Return Value - getSameNameDifferentIdFields

## Method getServiceHostStatus

```xpp
public Map getServiceHostStatus()
```

### Return Value - getServiceHostStatus

## Method isCheckedMode

```xpp
public boolean isCheckedMode()
```

### Return Value - isCheckedMode

## Method isConfigMode

```xpp
public boolean isConfigMode()
```

### Return Value - isConfigMode

## Method isDemoMode

```xpp
public boolean isDemoMode()
```

### Return Value - isDemoMode

## Method isSqlConnected

```xpp
public boolean isSqlConnected()
```

### Return Value - isSqlConnected

## Method numberOfTreeNodesLoaded

```xpp
public int numberOfTreeNodesLoaded()
```

### Return Value - numberOfTreeNodesLoaded

## Method releaseVersion

```xpp
public str releaseVersion()
```

### Return Value - releaseVersion

## Method setDefaultCompany

```xpp
public boolean setDefaultCompany(SelectableDataArea company)
```

### Parameters - setDefaultCompany

company  

### Return Value - setDefaultCompany

## Method ttsLevel

```xpp
public int ttsLevel()
```

### Return Value - ttsLevel

## Method ttsVersion

```xpp
public int ttsVersion()
```

### Return Value - ttsVersion

## Method CheckUserExistsInAnyPartition

Checks whether the given user is present in any partition.

```xpp
public static boolean CheckUserExistsInAnyPartition(str userId)
```

### Parameters - CheckUserExistsInAnyPartition

userId  

### Return Value - CheckUserExistsInAnyPartition

true if the user exists in any of the partitions; otherwise, false.

## Method getFolderPath

```xpp
public static str getFolderPath(int folder)
```

### Parameters - getFolderPath

folder  

### Return Value - getFolderPath

## Method getVSAssembliesPath

```xpp
public static str getVSAssembliesPath()
```

### Return Value - getVSAssembliesPath

## Method ilCacheContains

```xpp
public static boolean ilCacheContains(str owner, str key)
```

### Parameters - ilCacheContains

owner  

<!-- -->

key  

### Return Value - ilCacheContains

## Method ilCacheDelete

```xpp
public static str ilCacheDelete(str owner, str key)
```

### Parameters - ilCacheDelete

owner  

<!-- -->

key  

### Return Value - ilCacheDelete

## Method ilCacheFind

```xpp
public static str ilCacheFind(str owner, str key)
```

### Parameters - ilCacheFind

owner  

<!-- -->

key  

### Return Value - ilCacheFind

## Method initPartition

Initializes a given partition by creating the DAT company and the Admin user.

```xpp
public static boolean initPartition(Partition partition)
```

### Parameters - initPartition

partition  
The record ID of the partition to initialize.

### Return Value - initPartition

true if the initialization is successful; otherwise, false.

### Remarks - initPartition

This API is meant only for use by the upgrade framework. Using it in other contexts could cause unrecoverable impact to data.

## Method isServiceRegisteredOnClient

```xpp
public static boolean isServiceRegisteredOnClient(ClassId classId)
```

### Parameters - isServiceRegisteredOnClient

classId  

### Return Value - isServiceRegisteredOnClient

## Method IsSinglePartitionSystem

Evaluates whether the deployment has a single partition or multiple partitions.

```xpp
public static boolean IsSinglePartitionSystem()
```

### Return Value - IsSinglePartitionSystem

true if the deployment has only one partition; false if the deployment has multiple partitions.

## Method XppILAppDomain

```xpp
public static CLRObject XppILAppDomain()
```

### Return Value - XppILAppDomain

## Method isInTransactionScope

```xpp
public boolean isInTransactionScope()
```

### Return Value - isInTransactionScope

## Method transactionScopeCommitLevel

```xpp
public Int64 transactionScopeCommitLevel()
```

### Return Value - transactionScopeCommitLevel

## Method Encrypt

```xpp
public container Encrypt(str input)
```

### Parameters - Encrypt

input  

### Return Value - Encrypt

## Method Decrypt

```xpp
public str Decrypt(container cipher)
```

### Parameters - Decrypt

cipher  

### Return Value - Decrypt

## Method decryptToSecureString

```xpp
public System.Security.SecureString decryptToSecureString(container cipher)
```

### Parameters - decryptToSecureString

cipher  

### Return Value - decryptToSecureString

## Method encryptFromSecureString

```xpp
public container encryptFromSecureString(System.Security.SecureString input)
```

### Parameters - encryptFromSecureString

input  

### Return Value - encryptFromSecureString

## Method EncryptForPurpose

```xpp
public container EncryptForPurpose(str input, str purpose)
```

### Parameters - EncryptForPurpose

input  

<!-- -->

purpose  

### Return Value - EncryptForPurpose

## Method DecryptForPurpose

```xpp
public str DecryptForPurpose(container cipher, str purpose)
```

### Parameters - DecryptForPurpose

cipher  

<!-- -->

purpose  

### Return Value - DecryptForPurpose

## Method decryptToSecureStringForPurpose

```xpp
public System.Security.SecureString decryptToSecureStringForPurpose(container cipher, str purpose)
```

### Parameters - decryptToSecureStringForPurpose

cipher  

<!-- -->

purpose  

### Return Value - decryptToSecureStringForPurpose

## Method encryptFromSecureStringForPurpose

```xpp
public container encryptFromSecureStringForPurpose(System.Security.SecureString input, str purpose)
```

### Parameters - encryptFromSecureStringForPurpose

input  

<!-- -->

purpose  

### Return Value - encryptFromSecureStringForPurpose

## Method convertToUnsecureString

```xpp
public str convertToUnsecureString(System.Security.SecureString secureString)
```

### Parameters - convertToUnsecureString

secureString  

### Return Value - convertToUnsecureString

## Method convertToSecureString

```xpp
public System.Security.SecureString convertToSecureString(str unsecureString)
```

### Parameters - convertToSecureString

unsecureString  

### Return Value - convertToSecureString

## Method startBatch

```xpp
public static void startBatch()
```

## Method deleteCompany

```xpp
public void deleteCompany(SelectableDataArea company)
```

### Parameters - deleteCompany

company  

## Method ttsabort

```xpp
public void ttsabort()
```

## Method transactionScopeCommit

```xpp
public void transactionScopeCommit()
```

## Method new

Initializes a new instance of the xApplication class.

```xpp
public void new()
```

## Method stopBatch

```xpp
public static void stopBatch()
```

## Method logRenameKey

```xpp
public void logRenameKey(Common recordOrig, Common recordUpdated, container changedFields)
```

### Parameters - logRenameKey

recordOrig  

<!-- -->

recordUpdated  

<!-- -->

changedFields  

## Method startup

```xpp
public void startup(str startupCmd, str buildNumber)
```

### Parameters - startup

startupCmd  

<!-- -->

buildNumber  

## Method RedirectToDashboard

```xpp
public void RedirectToDashboard()
```

## Method insertXReferences

Is invoked by the framework when cross-reference information should be inserted into the database.

```xpp
public void insertXReferences()
```

### Remarks - insertXReferences

The Application class provides the overloaded functionality.

## Method logUpdate

```xpp
public void logUpdate(Common recordOrig, Common recordUpdated, container changedFields)
```

### Parameters - logUpdate

recordOrig  

<!-- -->

recordUpdated  

<!-- -->

changedFields  

## Method setStartPage

```xpp
public void setStartPage([SysUserInfoStartPage startpage])
```

### Parameters - setStartPage

startpage  

## Method ilCacheInsert

```xpp
public static void ilCacheInsert(str owner, str key, str value)
```

### Parameters - ilCacheInsert

owner  

<!-- -->

key  

<!-- -->

value  

## Method clearManagedCaches

```xpp
public void clearManagedCaches()
```

## Method eventDelete

Serves as a callback that is called by the kernel when a record in a table is deleted, provided that the kernel has been set up to monitor records in that table.

```xpp
public void eventDelete(Common recordDeleted)
```

### Parameters - eventDelete

recordDeleted  
The deleted record.

### Remarks - eventDelete

A developer can set up the kernel to call back on deletes for a given table. This can be accomplished by inserting a record into the DatabaseLog kernel table with all fields set to relevant values, which includes setting the field logType to EventDelete. This is very similar to how the logDelete method is called and set up. The call of this method will be in the transaction in which the record is deleted.

## Method enableCountryContextFilter

Enables system-wide optimization in the data access layer, whereby fields that don't belong in the current company's country/region context are dropped from the SELECT query.

```xpp
public void enableCountryContextFilter()
```

## Method setTheme

```xpp
public void setTheme([SysUserInfoTheme theme])
```

### Parameters - setTheme

theme  

## Method sysTrace

```xpp
public void sysTrace(SysTraceType traceType, container traceInfo)
```

### Parameters - sysTrace

traceType  

<!-- -->

traceInfo  

## Method initGlobal

```xpp
public void initGlobal(Info infoObject, VersionControl versionControlObject)
```

### Parameters - initGlobal

infoObject  

<!-- -->

versionControlObject  

## Method transactionScopeRollback

```xpp
public void transactionScopeRollback(Int64 commitLevel)
```

### Parameters - transactionScopeRollback

commitLevel  

## Method ttsbegin

```xpp
public void ttsbegin()
```

## Method flushcompanycache

```xpp
public void flushcompanycache(SelectableDataArea company)
```

### Parameters - flushcompanycache

company  

## Method logDelete

```xpp
public void logDelete(Common recordDeleted)
```

### Parameters - logDelete

recordDeleted  

## Method registerServiceOnClient

```xpp
public static void registerServiceOnClient(ClassId classId, str externalName)
```

### Parameters - registerServiceOnClient

classId  

<!-- -->

externalName  

## Method eventUpdate

Serves as a callback that is called by the kernel when a record in a table is updated, provided that the kernel has been set up to monitor records in that table.

```xpp
public void eventUpdate(Common recordOrig, Common recordUpdated, container changedFields)
```

### Parameters - eventUpdate

recordOrig  
A container of all changed fields.

<!-- -->

recordUpdated  
A container of all changed fields.

<!-- -->

changedFields  
A container of all changed fields.

### Remarks - eventUpdate

A developer can set up the kernel to call back on updates for a given table. This is accomplished by inserting a record into the DatabaseLog kernel table with all fields set to relevant values, which includes setting the field logType to EventUpdate. It is possible to set up the kernel to call back whenever a record is updated or when a specific field is updated. This is very similar to how the logUpdate method is called and set up. The call of this method will be in the transaction in which the record is updated.

## Method transactionScopeBegin

```xpp
public void transactionScopeBegin()
```

## Method checkForNewBatchJobs

```xpp
public static void checkForNewBatchJobs()
```

## Method disableCountryContextFilter

Disables system-wide optimization in the data access layer, whereby fields that don't belong in the current company's country/region context are dropped from the SELECT query.

```xpp
public void disableCountryContextFilter()
```

## Method xref

```xpp
public void xref(str path, xRef x)
```

### Parameters - xref

path  

<!-- -->

x  

## Method transactionScopeAbort

```xpp
public void transactionScopeAbort()
```

## Method eventRenameKey

Serves as a callback that is called by the kernel when a primary key is renamed, provided that the kernel has been set up to monitor records in that table.

```xpp
public void eventRenameKey(Common recordOrig, Common recordUpdated, container changedFields)
```

### Parameters - eventRenameKey

recordOrig  
A container of all changed fields.

<!-- -->

recordUpdated  
A container of all changed fields.

<!-- -->

changedFields  
A container of all changed fields.

### Remarks - eventRenameKey

A developer can set up the kernel to call back on primary key renames for a given table. This is accomplished by inserting a record into the DatabaseLog kernel table with all fields set to relevant values, which includes setting the field logType to EventRenameKey. This is very similar to how the logRenameKey method is called and set up. The call of this method will be in the transaction in which the primary key is renamed.

## Method flushClientPerformanceOptions

```xpp
public void flushClientPerformanceOptions()
```

## Method flushClientServices

```xpp
public static void flushClientServices()
```

## Method restartServiceHost

```xpp
public void restartServiceHost()
```

## Method updateXrefTreeNode

Is invoked by the framework when cross-reference information for the various node types is updated.

```xpp
public void updateXrefTreeNode(TreeNode treeNode)
```

### Parameters - updateXrefTreeNode

treeNode  

### Remarks - updateXrefTreeNode

The Application class provides the overloaded functionality.

## Method ttscommit

```xpp
public void ttscommit()
```

## Method RequestCompanyChange

```xpp
public void RequestCompanyChange([DataAreaSysCompany company])
```

### Parameters - RequestCompanyChange

company  

## Method finalize

```xpp
public void finalize()
```

## Method eventInsert

Serves as a callback that is called by the kernel when a record in a table is inserted, provided that the kernel has been set up to monitor records in that table.

```xpp
public void eventInsert(Common recordInserted)
```

### Parameters - eventInsert

recordInserted  
The inserted record.

### Remarks - eventInsert

A developer can set up the kernel to call back on inserts for a given table. This is accomplished by inserting a record into the DatabaseLog kernel table with all fields set to relevant values, which includes setting the field logType to EventInsert. This is very similar to how logInsert method is called and set up. The call of this method will be in the transaction in which the record is inserted.

## Method ttsNotifyBegin

```xpp
public void ttsNotifyBegin()
```

## Method closeAllForms

```xpp
public void closeAllForms()
```

## Method ttsNotifyCommit

```xpp
public void ttsNotifyCommit()
```

## Method ttsNotifyPreCommit

```xpp
public void ttsNotifyPreCommit()
```

## Method ttsNotifyPostBegin

```xpp
public void ttsNotifyPostBegin()
```

## Method ttsNotifyAbort

```xpp
public void ttsNotifyAbort()
```

## Method setDensity

```xpp
public void setDensity([SysUserInfoDensity theme])
```

### Parameters - setDensity

theme  

## Method logInsert

```xpp
public void logInsert(Common recordInserted)
```

### Parameters - logInsert

recordInserted  

