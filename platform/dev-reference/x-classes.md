---
# required metadata

title: X Classes
description: System API classes that start with the letter X.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-26 01 - 37 - 51
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 55811
ms.assetid: bc7f3c76-9d89-4a32-a5c3-dfb783c4f4f3
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.intro: 01-02-2016
ms.dyn365.ops.version: AX 7.0.0

---

# X Classes

System API classes that start with the letter X.

Class xApplication
------------------

    class xApplication extends Object

### Remarks

### Examples

### Methods

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

### Method IsTablePerHierarchyMode

Determines whether the system is being run with all table inheritance hierarchies flattened (Table per hierarchy mode).

    public boolean IsTablePerHierarchyMode()

#### Return Value

true if system is being run in Table per hierarchy mode; otherwise, false.

### Method buildNo

    public str buildNo()

#### Return Value

### Method canDeleteCompany

    public boolean canDeleteCompany(SelectableDataArea company)

#### Parameters

company  

#### Return Value

### Method countOfTopLevelFormsOpened

    public int countOfTopLevelFormsOpened()

#### Return Value

### Method company

    public Company company([SelectableDataArea company])

#### Parameters

company  

#### Return Value

### Method curTransactionId

    public Int64 curTransactionId([boolean ForceTakeNumber])

#### Parameters

ForceTakeNumber  

#### Return Value

### Method dbSynchronize

    public boolean dbSynchronize([TableId tableId], [boolean checkAsNeeded], [boolean continueOnError], [boolean showProgress], [container checkSyncTables], [boolean createAllIndexes], [boolean useLockForSingleTable])

#### Parameters

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

#### Return Value

### Method getSameNameDifferentIdFields

    public str getSameNameDifferentIdFields()

#### Return Value

### Method getServiceHostStatus

    public Map getServiceHostStatus()

#### Return Value

### Method isCheckedMode

    public boolean isCheckedMode()

#### Return Value

### Method isConfigMode

    public boolean isConfigMode()

#### Return Value

### Method isDemoMode

    public boolean isDemoMode()

#### Return Value

### Method isSqlConnected

    public boolean isSqlConnected()

#### Return Value

### Method numberOfTreeNodesLoaded

    public int numberOfTreeNodesLoaded()

#### Return Value

### Method releaseVersion

    public str releaseVersion()

#### Return Value

### Method setDefaultCompany

    public boolean setDefaultCompany(SelectableDataArea company)

#### Parameters

company  

#### Return Value

### Method ttsLevel

    public int ttsLevel()

#### Return Value

### Method ttsVersion

    public int ttsVersion()

#### Return Value

### Method CheckUserExistsInAnyPartition

Checks whether the given user is present in any partition.

    public static boolean CheckUserExistsInAnyPartition(str userId)

#### Parameters

userId  

#### Return Value

true if the user exists in any of the partitions; otherwise, false.

### Method getFolderPath

    public static str getFolderPath(int folder)

#### Parameters

folder  

#### Return Value

### Method getVSAssembliesPath

    public static str getVSAssembliesPath()

#### Return Value

### Method ilCacheContains

    public static boolean ilCacheContains(str owner, str key)

#### Parameters

owner  

<!-- -->

key  

#### Return Value

### Method ilCacheDelete

    public static str ilCacheDelete(str owner, str key)

#### Parameters

owner  

<!-- -->

key  

#### Return Value

### Method ilCacheFind

    public static str ilCacheFind(str owner, str key)

#### Parameters

owner  

<!-- -->

key  

#### Return Value

### Method initPartition

Initializes a given partition by creating the DAT company and the Admin user.

    public static boolean initPartition(Partition partition)

#### Parameters

partition  
The record ID of the partition to initialize.

#### Return Value

true if the initialization is successful; otherwise, false.

#### Remarks

This API is meant only for use by the upgrade framework. Using it in other contexts could cause unrecoverable impact to data.

### Method isServiceRegisteredOnClient

    public static boolean isServiceRegisteredOnClient(ClassId classId)

#### Parameters

classId  

#### Return Value

### Method IsSinglePartitionSystem

Evaluates whether the deployment has a single partition or multiple partitions.

    public static boolean IsSinglePartitionSystem()

#### Return Value

true if the deployment has only one partition; false if the deployment has multiple partitions.

### Method XppILAppDomain

    public static CLRObject XppILAppDomain()

#### Return Value

### Method isInTransactionScope

    public boolean isInTransactionScope()

#### Return Value

### Method transactionScopeCommitLevel

    public Int64 transactionScopeCommitLevel()

#### Return Value

### Method Encrypt

    public container Encrypt(str input)

#### Parameters

input  

#### Return Value

### Method Decrypt

    public str Decrypt(container cipher)

#### Parameters

cipher  

#### Return Value

### Method decryptToSecureString

    public System.Security.SecureString decryptToSecureString(container cipher)

#### Parameters

cipher  

#### Return Value

### Method encryptFromSecureString

    public container encryptFromSecureString(System.Security.SecureString input)

#### Parameters

input  

#### Return Value

### Method EncryptForPurpose

    public container EncryptForPurpose(str input, str purpose)

#### Parameters

input  

<!-- -->

purpose  

#### Return Value

### Method DecryptForPurpose

    public str DecryptForPurpose(container cipher, str purpose)

#### Parameters

cipher  

<!-- -->

purpose  

#### Return Value

### Method decryptToSecureStringForPurpose

    public System.Security.SecureString decryptToSecureStringForPurpose(container cipher, str purpose)

#### Parameters

cipher  

<!-- -->

purpose  

#### Return Value

### Method encryptFromSecureStringForPurpose

    public container encryptFromSecureStringForPurpose(System.Security.SecureString input, str purpose)

#### Parameters

input  

<!-- -->

purpose  

#### Return Value

### Method convertToUnsecureString

    public str convertToUnsecureString(System.Security.SecureString secureString)

#### Parameters

secureString  

#### Return Value

### Method convertToSecureString

    public System.Security.SecureString convertToSecureString(str unsecureString)

#### Parameters

unsecureString  

#### Return Value

### Method startBatch

    public static void startBatch()

### Method deleteCompany

    public void deleteCompany(SelectableDataArea company)

#### Parameters

company  

### Method ttsabort

    public void ttsabort()

### Method transactionScopeCommit

    public void transactionScopeCommit()

### Method new

Initializes a new instance of the xApplication class.

    public void new()

### Method stopBatch

    public static void stopBatch()

### Method logRenameKey

    public void logRenameKey(Common recordOrig, Common recordUpdated, container changedFields)

#### Parameters

recordOrig  

<!-- -->

recordUpdated  

<!-- -->

changedFields  

### Method startup

    public void startup(str startupCmd, str buildNumber)

#### Parameters

startupCmd  

<!-- -->

buildNumber  

### Method RedirectToDashboard

    public void RedirectToDashboard()

### Method insertXReferences

Is invoked by the framework when cross-reference information should be inserted into the database.

    public void insertXReferences()

#### Remarks

The Application class provides the overloaded functionality.

### Method logUpdate

    public void logUpdate(Common recordOrig, Common recordUpdated, container changedFields)

#### Parameters

recordOrig  

<!-- -->

recordUpdated  

<!-- -->

changedFields  

### Method setStartPage

    public void setStartPage([SysUserInfoStartPage startpage])

#### Parameters

startpage  

### Method ilCacheInsert

    public static void ilCacheInsert(str owner, str key, str value)

#### Parameters

owner  

<!-- -->

key  

<!-- -->

value  

### Method clearManagedCaches

    public void clearManagedCaches()

### Method eventDelete

Serves as a callback that is called by the kernel when a record in a table is deleted, provided that the kernel has been set up to monitor records in that table.

    public void eventDelete(Common recordDeleted)

#### Parameters

recordDeleted  
The deleted record.

#### Remarks

A developer can set up the kernel to call back on deletes for a given table. This can be accomplished by inserting a record into the DatabaseLog kernel table with all fields set to relevant values, which includes setting the field logType to EventDelete. This is very similar to how the logDelete method is called and set up. The call of this method will be in the transaction in which the record is deleted.

### Method enableCountryContextFilter

Enables system-wide optimization in the data access layer, whereby fields that don't belong in the current company's country/region context are dropped from the SELECT query.

    public void enableCountryContextFilter()

### Method setTheme

    public void setTheme([SysUserInfoTheme theme])

#### Parameters

theme  

### Method sysTrace

    public void sysTrace(SysTraceType traceType, container traceInfo)

#### Parameters

traceType  

<!-- -->

traceInfo  

### Method initGlobal

    public void initGlobal(Info infoObject, VersionControl versionControlObject)

#### Parameters

infoObject  

<!-- -->

versionControlObject  

### Method transactionScopeRollback

    public void transactionScopeRollback(Int64 commitLevel)

#### Parameters

commitLevel  

### Method ttsbegin

    public void ttsbegin()

### Method flushcompanycache

    public void flushcompanycache(SelectableDataArea company)

#### Parameters

company  

### Method logDelete

    public void logDelete(Common recordDeleted)

#### Parameters

recordDeleted  

### Method registerServiceOnClient

    public static void registerServiceOnClient(ClassId classId, str externalName)

#### Parameters

classId  

<!-- -->

externalName  

### Method eventUpdate

Serves as a callback that is called by the kernel when a record in a table is updated, provided that the kernel has been set up to monitor records in that table.

    public void eventUpdate(Common recordOrig, Common recordUpdated, container changedFields)

#### Parameters

recordOrig  
A container of all changed fields.

<!-- -->

recordUpdated  
A container of all changed fields.

<!-- -->

changedFields  
A container of all changed fields.

#### Remarks

A developer can set up the kernel to call back on updates for a given table. This is accomplished by inserting a record into the DatabaseLog kernel table with all fields set to relevant values, which includes setting the field logType to EventUpdate. It is possible to set up the kernel to call back whenever a record is updated or when a specific field is updated. This is very similar to how the logUpdate method is called and set up. The call of this method will be in the transaction in which the record is updated.

### Method transactionScopeBegin

    public void transactionScopeBegin()

### Method checkForNewBatchJobs

    public static void checkForNewBatchJobs()

### Method disableCountryContextFilter

Disables system-wide optimization in the data access layer, whereby fields that don't belong in the current company's country/region context are dropped from the SELECT query.

    public void disableCountryContextFilter()

### Method xref

    public void xref(str path, xRef x)

#### Parameters

path  

<!-- -->

x  

### Method transactionScopeAbort

    public void transactionScopeAbort()

### Method eventRenameKey

Serves as a callback that is called by the kernel when a primary key is renamed, provided that the kernel has been set up to monitor records in that table.

    public void eventRenameKey(Common recordOrig, Common recordUpdated, container changedFields)

#### Parameters

recordOrig  
A container of all changed fields.

<!-- -->

recordUpdated  
A container of all changed fields.

<!-- -->

changedFields  
A container of all changed fields.

#### Remarks

A developer can set up the kernel to call back on primary key renames for a given table. This is accomplished by inserting a record into the DatabaseLog kernel table with all fields set to relevant values, which includes setting the field logType to EventRenameKey. This is very similar to how the logRenameKey method is called and set up. The call of this method will be in the transaction in which the primary key is renamed.

### Method flushClientPerformanceOptions

    public void flushClientPerformanceOptions()

### Method flushClientServices

    public static void flushClientServices()

### Method restartServiceHost

    public void restartServiceHost()

### Method updateXrefTreeNode

Is invoked by the framework when cross-reference information for the various node types is updated.

    public void updateXrefTreeNode(TreeNode treeNode)

#### Parameters

treeNode  

#### Remarks

The Application class provides the overloaded functionality.

### Method ttscommit

    public void ttscommit()

### Method RequestCompanyChange

    public void RequestCompanyChange([DataAreaSysCompany company])

#### Parameters

company  

### Method finalize

    public void finalize()

### Method eventInsert

Serves as a callback that is called by the kernel when a record in a table is inserted, provided that the kernel has been set up to monitor records in that table.

    public void eventInsert(Common recordInserted)

#### Parameters

recordInserted  
The inserted record.

#### Remarks

A developer can set up the kernel to call back on inserts for a given table. This is accomplished by inserting a record into the DatabaseLog kernel table with all fields set to relevant values, which includes setting the field logType to EventInsert. This is very similar to how logInsert method is called and set up. The call of this method will be in the transaction in which the record is inserted.

### Method ttsNotifyBegin

    public void ttsNotifyBegin()

### Method closeAllForms

    public void closeAllForms()

### Method ttsNotifyCommit

    public void ttsNotifyCommit()

### Method ttsNotifyPreCommit

    public void ttsNotifyPreCommit()

### Method ttsNotifyPostBegin

    public void ttsNotifyPostBegin()

### Method ttsNotifyAbort

    public void ttsNotifyAbort()

### Method setDensity

    public void setDensity([SysUserInfoDensity theme])

#### Parameters

theme  

### Method logInsert

    public void logInsert(Common recordInserted)

#### Parameters

recordInserted  

## Class xArgs
    class xArgs extends Object

The xArgs class is used to pass arguments such as a name, a caller, and parameters between application objects.

### Remarks

Forms, reports and queries all use this class as their first argument in the constructor. The preferred way to use this class is to construct an xArgs object, supply a name-string, and then pass the xArgs object to the forms constructor or a ClassFactory method.If you want to refer to the xArgs object passed to one of these classes, it can be reached using args method of that class.There are four methods that can be used to pass extra information to the new class:

-   The parm - to pass strings
-   The parmEnum and parmEnumType methods - to pass enumeration values
-   The parmObject method - to pass an object of any type

The instance of the xArgs class that is sent from the caller can be created automatically by the kernel or explicitly by the caller. When the caller uses a menu item to call an object, an instance of the xArgs class is created by the kernel code. The menu item name will be set to the name of the menu item used. If the menu item has values for the Parameters, EnumParameter, or EnumTypeParameter properties set, the kernel will set the values of the corresponding Parm, ParmEnum, or ParmEnumType properties for this instance of the xArgs class.

### Examples

### Methods

| Method                                                                                                       | Description                                                                                                                           |
|--------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| public boolean allowUseOfPreloadedForm(\[boolean value\])                                                    | Determines if the form launched for this instance may come from the pre-loaded form pool.                                             |
| public int arrIdx(\[int value\])                                                                             |                                                                                                                                       |
| public Object caller(\[Object value\])                                                                       | Gets or sets the instance of the object that created this instance of the xArgs class.                                                |
| public IDispatcherProxy callerDispatcher()                                                                   |                                                                                                                                       |
| public FormControl callerFormControl(\[FormControl value\])                                                  |                                                                                                                                       |
| public str callerName()                                                                                      |                                                                                                                                       |
| public UtilElementType callerType()                                                                          |                                                                                                                                       |
| public Guid callerId()                                                                                       |                                                                                                                                       |
| public str clientId(\[str value\])                                                                           |                                                                                                                                       |
| public CopyCallerQuery copyCallerQuery(\[CopyCallerQuery value\])                                            |                                                                                                                                       |
| public TableId dataset()                                                                                     | Gets the table ID of the table in which the caller object is working.                                                                 |
| public str designName(\[str value\])                                                                         | Gets or sets a string that indicates a design on a report or form.                                                                    |
| public ExtendedTypeId extType(\[ExtendedTypeId edt\], \[int arrayIndex\])                                    |                                                                                                                                       |
| public FormViewOption formViewOption(\[FormViewOption value\])                                               |                                                                                                                                       |
| public InitialQueryParameter initialQuery(\[InitialQueryParameter initialQueryParameter\])                   |                                                                                                                                       |
| public FieldId lookupField(\[FieldId value\])                                                                | Gets or sets the field ID in a table to use to look up a specified record.                                                            |
| public Common lookupRecord(\[Common value\])                                                                 | Finds a record in the specified table.                                                                                                |
| public TableId lookupTable(\[TableId value\])                                                                |                                                                                                                                       |
| public str lookupValue(\[str value\])                                                                        | Gets or sets a string to use with the LookupField method to find a value in a field of a table.                                       |
| public str managedContentItemName(\[str value\])                                                             |                                                                                                                                       |
| public str menuItemName(\[str value\])                                                                       | Gets or sets the name of the menu item to use to start the application object.                                                        |
| public MenuItemType menuItemType(\[MenuItemType value\])                                                     | Gets or sets the type of the menu item to use to start the called application object.                                                 |
| public MultiSelectionContext multiSelectionContext()                                                         |                                                                                                                                       |
| public str name(\[str value\])                                                                               | Gets or sets the name that is used in code to identify a form, report, table, query, or another MSDAX application object.             |
| public Object object(\[Object value\])                                                                       | Gets and sets the application name of the object for which to open a new instance.                                                    |
| public OpenMode openMode(\[OpenMode value\])                                                                 |                                                                                                                                       |
| public Int64 parentWnd(\[Int64 value\])                                                                      |                                                                                                                                       |
| public str parm(\[str value\])                                                                               | Gets or sets a string that specifies miscellaneous information for the called object.                                                 |
| public AnyType parmEnum(\[int value\])                                                                       | Gets or sets the enumeration value of the enumeration type that is specified in the parmEnumType method.                              |
| public int parmEnumType(\[int value\])                                                                       | Gets or sets the ID value of any enumeration type.                                                                                    |
| public Object parmObject(\[Object value\])                                                                   | Gets or sets the instance of any object to pass to the called object.                                                                 |
| public Common record(\[Common value\])                                                                       | Gets or sets the record from the table on which the caller object is working.                                                         |
| public FieldId refField(\[FieldId value\])                                                                   |                                                                                                                                       |
| public str getRequestContextQuery()                                                                          |                                                                                                                                       |
| public str requestContextQuery(str value)                                                                    |                                                                                                                                       |
| public FieldId selectField(\[FieldId value\])                                                                |                                                                                                                                       |
| public str toString()                                                                                        | Retrieves a string representation of an instance of the xArgs.                                                                        |
| public boolean applyRecordAsDynalink(\[boolean applyAsDynalink\])                                            |                                                                                                                                       |
| public void onCallerChanged(\[Object value\])                                                                |                                                                                                                                       |
| public void new(\[AnyType nameOrCaller\], \[Object object\])                                                 | Constructs an instance of this class, which is used to pass information to high-level classes such as the FormRun or ReportRun class. |
| public void finalize()                                                                                       | Removes the current instance of the xArgs class from memory.                                                                          |
| public void setupArgs(str parm, int enumType, AnyType enumValue, \[str menuItemName\], \[int menuItemType\]) |                                                                                                                                       |

### Method allowUseOfPreloadedForm

Determines if the form launched for this instance may come from the pre-loaded form pool.

    public boolean allowUseOfPreloadedForm([boolean value])

#### Parameters

value  
A Boolean value that determines whether the loaded form can come from the pre-loaded form pool.

#### Return Value

true if the form launched for this instance may come from the pre-loaded form pool; otherwise, false.

#### Remarks

Use of a pre-loaded form is permitted by default. Set this to false only if there are undesired side-effects from the use of a pre-loaded form.

### Method arrIdx

    public int arrIdx([int value])

#### Parameters

value  

#### Return Value

### Method caller

Gets or sets the instance of the object that created this instance of the xArgs class.

    public Object caller([Object value])

#### Parameters

value  
The value to set; optional.

#### Return Value

The current instance of the caller object.

### Method callerDispatcher

    public IDispatcherProxy callerDispatcher()

#### Return Value

### Method callerFormControl

    public FormControl callerFormControl([FormControl value])

#### Parameters

value  

#### Return Value

### Method callerName

    public str callerName()

#### Return Value

### Method callerType

    public UtilElementType callerType()

#### Return Value

### Method callerId

    public Guid callerId()

#### Return Value

### Method clientId

    public str clientId([str value])

#### Parameters

value  

#### Return Value

### Method copyCallerQuery

    public CopyCallerQuery copyCallerQuery([CopyCallerQuery value])

#### Parameters

value  

#### Return Value

### Method dataset

Gets the table ID of the table in which the caller object is working.

    public TableId dataset()

#### Return Value

The table ID of the table in which the caller object is working.

#### Remarks

The returned value is often used to identify which type of record is being transferred from the caller in the record method.

### Method designName

Gets or sets a string that indicates a design on a report or form.

    public str designName([str value])

#### Parameters

value  
The value to set; optional.

#### Return Value

### Method extType

    public ExtendedTypeId extType([ExtendedTypeId edt], [int arrayIndex])

#### Parameters

edt  

<!-- -->

arrayIndex  

#### Return Value

### Method formViewOption

    public FormViewOption formViewOption([FormViewOption value])

#### Parameters

value  

#### Return Value

### Method initialQuery

    public InitialQueryParameter initialQuery([InitialQueryParameter initialQueryParameter])

#### Parameters

initialQueryParameter  

#### Return Value

### Method lookupField

Gets or sets the field ID in a table to use to look up a specified record.

    public FieldId lookupField([FieldId value])

#### Parameters

value  
The value to set; optional.

#### Return Value

The field ID of a field in a table to use to look up a specified record.

#### Remarks

The returned value can be used by the called object to look up the specified record in the LookupRecord method or the string specified in the LookupValue method. For example, the field to look up could be set with the following: xArgs.lookupField(fieldnum(TableName, FieldName));

### Method lookupRecord

Finds a record in the specified table.

    public Common lookupRecord([Common value])

#### Parameters

value  
The table in which to find a record.

#### Return Value

A record in the specified table.

#### Remarks

This method can be used by the called object in combination with the field ID that is returned from the lookupField method to find the value of the field in the record that is returned by this method.

### Method lookupTable

    public TableId lookupTable([TableId value])

#### Parameters

value  

#### Return Value

### Method lookupValue

Gets or sets a string to use with the LookupField method to find a value in a field of a table.

    public str lookupValue([str value])

#### Parameters

value  
The value to set; optional.

#### Return Value

A string to use with the LookupField method to find a value.

### Method managedContentItemName

    public str managedContentItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

Gets or sets the name of the menu item to use to start the application object.

    public str menuItemName([str value])

#### Parameters

value  
The value to set; optional.

#### Return Value

The name of the menu item to use to start the application object.

#### Remarks

For example, to set the menu item you could use the following: xArgs.menuItemName(menuitemdisplaystr(CostingVersionPeriodic));

### Method menuItemType

Gets or sets the type of the menu item to use to start the called application object.

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  
The value to set; optional.

#### Return Value

The type of the menu item to use to start the called application object.

#### Remarks

The menu item type will be one of the Display, Output, or Action enumeration values.

### Method multiSelectionContext

    public MultiSelectionContext multiSelectionContext()

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another MSDAX application object.

    public str name([str value])

#### Parameters

value  
The value to set; optional.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Does not exceed 250 characters.
-   May include numbers and underscore characters.
-   May include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

For example, to call a form from an application object you can use: args.name(formstr(FormName));

### Method object

Gets and sets the application name of the object for which to open a new instance.

    public Object object([Object value])

#### Parameters

value  
The value to set; optional.

#### Return Value

The application name of the object for which to open a new instance.

#### Remarks

The value parameter may be one of the following types of objects:

-   Form
-   Report
-   Job
-   Class
-   Query.

### Method openMode

    public OpenMode openMode([OpenMode value])

#### Parameters

value  

#### Return Value

### Method parentWnd

    public Int64 parentWnd([Int64 value])

#### Parameters

value  

#### Return Value

### Method parm

Gets or sets a string that specifies miscellaneous information for the called object.

    public str parm([str value])

#### Parameters

value  
The value to set; optional.

#### Return Value

The value of the string that specifies miscellaneous information for the called object.

### Method parmEnum

Gets or sets the enumeration value of the enumeration type that is specified in the parmEnumType method.

    public AnyType parmEnum([int value])

#### Parameters

value  
The key of an enumeration value to set; optional.

#### Return Value

The enumeration value of the enumeration type that is specified in the parmEnumType method.

#### Remarks

This method is often used with the parmEnumType method: args.parmEnumType(enumnum(AssetBookType));args.parmEnumType(enumnum(AssetBookType));

### Method parmEnumType

Gets or sets the ID value of any enumeration type.

    public int parmEnumType([int value])

#### Parameters

value  
The value to set; optional.

#### Return Value

The ID value of the enumeration type.

#### Remarks

This method is used with the parmEnum method to send a specific value of an enumeration type to the called object. For example: args.parmEnumType(enumnum(AssetBookType));args.parmEnum(AssetBookType::ValueModel);

### Method parmObject

Gets or sets the instance of any object to pass to the called object.

    public Object parmObject([Object value])

#### Parameters

value  
The value to set; optional.

#### Return Value

The instance of an object to pass to the called object.

#### Remarks

The object will often be a class.

### Method record

Gets or sets the record from the table on which the caller object is working.

    public Common record([Common value])

#### Parameters

value  
The value to set; optional.

#### Return Value

The record from the table on which the caller object is working.

#### Remarks

This method is used to access the values in the record that the calling object is currently using.

### Method refField

    public FieldId refField([FieldId value])

#### Parameters

value  

#### Return Value

### Method getRequestContextQuery

    public str getRequestContextQuery()

#### Return Value

### Method requestContextQuery

    public str requestContextQuery(str value)

#### Parameters

value  

#### Return Value

### Method selectField

    public FieldId selectField([FieldId value])

#### Parameters

value  

#### Return Value

### Method toString

Retrieves a string representation of an instance of the xArgs.

    public str toString()

#### Return Value

A string that contains a description of the instance of the xArgs class.

### Method applyRecordAsDynalink

    public boolean applyRecordAsDynalink([boolean applyAsDynalink])

#### Parameters

applyAsDynalink  

#### Return Value

### Method onCallerChanged

    public void onCallerChanged([Object value])

#### Parameters

value  

### Method new

Constructs an instance of this class, which is used to pass information to high-level classes such as the FormRun or ReportRun class.

    public void new([AnyType nameOrCaller], [Object object])

#### Parameters

nameOrCaller  
An object argument; optional. This parameter is used to create the instance of the xArgs class and is used when the nameOrCaller parameter is a caller argument.

<!-- -->

object  
An object argument; optional. This parameter is used to create the instance of the xArgs class and is used when the nameOrCaller parameter is a caller argument.

#### Remarks

To create an xArgs object, either supply a (Caller, Object) pair or a Name argument. Both arguments are optional and all values can be set after it is constructed by calling the appropriate methods.

### Method finalize

Removes the current instance of the xArgs class from memory.

    public void finalize()

### Method setupArgs

    public void setupArgs(str parm, int enumType, AnyType enumValue, [str menuItemName], [int menuItemType])

#### Parameters

parm  

<!-- -->

enumType  

<!-- -->

enumValue  

<!-- -->

menuItemName  

<!-- -->

menuItemType  

## Class xAxaptaUserDetails
    class xAxaptaUserDetails extends Object

### Remarks

### Examples

### Methods

| Method                                           | Description                                                 |
|--------------------------------------------------|-------------------------------------------------------------|
| public UserAccountType getAccountType(int index) |                                                             |
| public int getUserCount()                        |                                                             |
| public str getUserDomain(int index)              |                                                             |
| public str getUserLogin(int index)               |                                                             |
| public str getUserMail(int index)                |                                                             |
| public str getUserName(int index)                |                                                             |
| public str getUserSid(int index)                 |                                                             |
| public boolean isUserEnabled(int index)          |                                                             |
| public boolean isUserExternal(int index)         |                                                             |
| public void finalize()                           |                                                             |
| public void new()                                | Initializes a new instance of the xAxaptaUserDetails class. |

### Method getAccountType

    public UserAccountType getAccountType(int index)

#### Parameters

index  

#### Return Value

### Method getUserCount

    public int getUserCount()

#### Return Value

### Method getUserDomain

    public str getUserDomain(int index)

#### Parameters

index  

#### Return Value

### Method getUserLogin

    public str getUserLogin(int index)

#### Parameters

index  

#### Return Value

### Method getUserMail

    public str getUserMail(int index)

#### Parameters

index  

#### Return Value

### Method getUserName

    public str getUserName(int index)

#### Parameters

index  

#### Return Value

### Method getUserSid

    public str getUserSid(int index)

#### Parameters

index  

#### Return Value

### Method isUserEnabled

    public boolean isUserEnabled(int index)

#### Parameters

index  

#### Return Value

### Method isUserExternal

    public boolean isUserExternal(int index)

#### Parameters

index  

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the xAxaptaUserDetails class.

    public void new()

## Class xAxaptaUserManager
    class xAxaptaUserManager extends Object

### Remarks

### Examples

### Methods

| Method                                                                                               | Description                                                            |
|------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| public container enumerateDomains(str server)                                                        |                                                                        |
| public xAxaptaUserDetails enumerateDomainUsers(str domainName)                                       |                                                                        |
| public str generatePassword()                                                                        |                                                                        |
| public xAxaptaUserDetails getDomainUser(str domainName, str userLogin)                               |                                                                        |
| public str getFQDN(str domainName, \[boolean throwError\])                                           |                                                                        |
| public container getGroupsForUser(str userName)                                                      |                                                                        |
| public container getRolesForUser(str userName, str company)                                          | Gets roles for the given user.                                         |
| public xAxaptaUserDetails getSIDFromName(str userLogin, str domainName, UserAccountType accountType) | Gets user details from the given user logon, domain, and account type. |
| public str getUserSid(str username, str domain)                                                      |                                                                        |
| public boolean validateDomain(str domain)                                                            |                                                                        |
| public boolean validateOrgUnit(str ouName)                                                           |                                                                        |
| public boolean validatePassword(str username, str domain, str password)                              |                                                                        |
| public boolean validateSecGroup(str secGroup)                                                        |                                                                        |
| public void new()                                                                                    | Initializes a new instance of the xAxaptaUserManager class.            |
| public void updateUserRoleAssignments(UserId userId, container roles, container removeRoles)         |                                                                        |
| public void finalize()                                                                               |                                                                        |

### Method enumerateDomains

    public container enumerateDomains(str server)

#### Parameters

server  

#### Return Value

### Method enumerateDomainUsers

    public xAxaptaUserDetails enumerateDomainUsers(str domainName)

#### Parameters

domainName  

#### Return Value

### Method generatePassword

    public str generatePassword()

#### Return Value

### Method getDomainUser

    public xAxaptaUserDetails getDomainUser(str domainName, str userLogin)

#### Parameters

domainName  

<!-- -->

userLogin  

#### Return Value

### Method getFQDN

    public str getFQDN(str domainName, [boolean throwError])

#### Parameters

domainName  

<!-- -->

throwError  

#### Return Value

### Method getGroupsForUser

    public container getGroupsForUser(str userName)

#### Parameters

userName  

#### Return Value

### Method getRolesForUser

Gets roles for the given user.

    public container getRolesForUser(str userName, str company)

#### Parameters

userName  

<!-- -->

company  

#### Return Value

A container that holds roles for the given user.

### Method getSIDFromName

Gets user details from the given user logon, domain, and account type.

    public xAxaptaUserDetails getSIDFromName(str userLogin, str domainName, UserAccountType accountType)

#### Parameters

userLogin  

<!-- -->

domainName  

<!-- -->

accountType  

#### Return Value

A xAxaptaUserDetails class instance that contains user details.

### Method getUserSid

    public str getUserSid(str username, str domain)

#### Parameters

username  

<!-- -->

domain  

#### Return Value

### Method validateDomain

    public boolean validateDomain(str domain)

#### Parameters

domain  

#### Return Value

### Method validateOrgUnit

    public boolean validateOrgUnit(str ouName)

#### Parameters

ouName  

#### Return Value

### Method validatePassword

    public boolean validatePassword(str username, str domain, str password)

#### Parameters

username  

<!-- -->

domain  

<!-- -->

password  

#### Return Value

### Method validateSecGroup

    public boolean validateSecGroup(str secGroup)

#### Parameters

secGroup  

#### Return Value

### Method new

Initializes a new instance of the xAxaptaUserManager class.

    public void new()

### Method updateUserRoleAssignments

    public void updateUserRoleAssignments(UserId userId, container roles, container removeRoles)

#### Parameters

userId  

<!-- -->

roles  

<!-- -->

removeRoles  

### Method finalize

    public void finalize()

## Class xBrowser
    class xBrowser extends Object

### Remarks

### Examples

### Methods

| Method                                                                                       | Description |
|----------------------------------------------------------------------------------------------|-------------|
| public void navigate(str downloadUrl, \[boolean openInNewTab\], \[boolean showExitWarning\]) |             |
| public void new()                                                                            |             |

### Method navigate

    public void navigate(str downloadUrl, [boolean openInNewTab], [boolean showExitWarning])

#### Parameters

downloadUrl  

<!-- -->

openInNewTab  

<!-- -->

showExitWarning  

### Method new

    public void new()

## Class xClassFactory
    class xClassFactory extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                                               | Description                                            |
|------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------|
| public xFormRun createAutoReportForm(xArgs args)                                                                                                     |                                                        |
| public xFormRun createLabelForm(xArgs args)                                                                                                          |                                                        |
| public xFormRun createRecInfoForm(xArgs args)                                                                                                        |                                                        |
| public ReportViewer createReportViewer(PrintJobHeader jobsCursor, PrintJobPages pagesCursor, \[ReportRun reportRun\])                                |                                                        |
| public xFormRun createSetupForm(xArgs args)                                                                                                          |                                                        |
| public ReportOutputUser createViewer(PrintJobHeader jobsCursor, PrintJobPages pagesCursor, ReportOutputUserType viewerType, \[ReportRun reportRun\]) |                                                        |
| public Object createWebPageEditor()                                                                                                                  |                                                        |
| public xFormRun formRunClass(xArgs args)                                                                                                             |                                                        |
| public container lastValueGet(SelectableDataArea company, UserId user, UtilElementType utilType, UtilElementName name, \[str design\])               |                                                        |
| public QueryRun queryRunClass(xArgs args)                                                                                                            |                                                        |
| public ReportRun reportRunClass(xArgs args)                                                                                                          |                                                        |
| public Object startAOTWizard(TreeNode parent)                                                                                                        |                                                        |
| public void projectDeleted(str projectName)                                                                                                          |                                                        |
| public void lastValueDelete(SelectableDataArea company, UserId user, UtilElementType utilType, UtilElementName name, \[str design\])                 |                                                        |
| public void lastValuePut(container value, SelectableDataArea company, UserId user, UtilElementType utilType, UtilElementName name, \[str design\])   |                                                        |
| public void drillDown(OutputField outputField, MenuItemType menuItemType, str menuItemName)                                                          |                                                        |
| public void new()                                                                                                                                    | Initializes a new instance of the xClassFactory class. |

### Method createAutoReportForm

    public xFormRun createAutoReportForm(xArgs args)

#### Parameters

args  

#### Return Value

### Method createLabelForm

    public xFormRun createLabelForm(xArgs args)

#### Parameters

args  

#### Return Value

### Method createRecInfoForm

    public xFormRun createRecInfoForm(xArgs args)

#### Parameters

args  

#### Return Value

### Method createReportViewer

    public ReportViewer createReportViewer(PrintJobHeader jobsCursor, PrintJobPages pagesCursor, [ReportRun reportRun])

#### Parameters

jobsCursor  

<!-- -->

pagesCursor  

<!-- -->

reportRun  

#### Return Value

### Method createSetupForm

    public xFormRun createSetupForm(xArgs args)

#### Parameters

args  

#### Return Value

### Method createViewer

    public ReportOutputUser createViewer(PrintJobHeader jobsCursor, PrintJobPages pagesCursor, ReportOutputUserType viewerType, [ReportRun reportRun])

#### Parameters

jobsCursor  

<!-- -->

pagesCursor  

<!-- -->

viewerType  

<!-- -->

reportRun  

#### Return Value

### Method createWebPageEditor

    public Object createWebPageEditor()

#### Return Value

### Method formRunClass

    public xFormRun formRunClass(xArgs args)

#### Parameters

args  

#### Return Value

### Method lastValueGet

    public container lastValueGet(SelectableDataArea company, UserId user, UtilElementType utilType, UtilElementName name, [str design])

#### Parameters

company  

<!-- -->

user  

<!-- -->

utilType  

<!-- -->

name  

<!-- -->

design  

#### Return Value

### Method queryRunClass

    public QueryRun queryRunClass(xArgs args)

#### Parameters

args  

#### Return Value

### Method reportRunClass

    public ReportRun reportRunClass(xArgs args)

#### Parameters

args  

#### Return Value

### Method startAOTWizard

    public Object startAOTWizard(TreeNode parent)

#### Parameters

parent  

#### Return Value

### Method projectDeleted

    public void projectDeleted(str projectName)

#### Parameters

projectName  

### Method lastValueDelete

    public void lastValueDelete(SelectableDataArea company, UserId user, UtilElementType utilType, UtilElementName name, [str design])

#### Parameters

company  

<!-- -->

user  

<!-- -->

utilType  

<!-- -->

name  

<!-- -->

design  

### Method lastValuePut

    public void lastValuePut(container value, SelectableDataArea company, UserId user, UtilElementType utilType, UtilElementName name, [str design])

#### Parameters

value  

<!-- -->

company  

<!-- -->

user  

<!-- -->

utilType  

<!-- -->

name  

<!-- -->

design  

### Method drillDown

    public void drillDown(OutputField outputField, MenuItemType menuItemType, str menuItemName)

#### Parameters

outputField  

<!-- -->

menuItemType  

<!-- -->

menuItemName  

### Method new

Initializes a new instance of the xClassFactory class.

    public void new()

## Class xClassTrace
    class xClassTrace extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                             | Description                                          |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| ::public static boolean isTracingEnabled(\[Int64 keyword\], \[int level\])                                                                                                         |                                                      |
| ::public static boolean isTracingStarted()                                                                                                                                         |                                                      |
| ::public static str kernelCustomerId()                                                                                                                                             |                                                      |
| ::public static Guid kernelRequestId()                                                                                                                                             |                                                      |
| ::public static str kernelSessionId()                                                                                                                                              |                                                      |
| ::public static str kernelUserId()                                                                                                                                                 |                                                      |
| ::public static int start(str logFileName, \[int logBufferSize\], \[int minBuffers\], \[int maxBuffers\], \[Int64 keywords\], \[int maxFileSize\], \[boolean useCircularLogging\]) |                                                      |
| ::public static int stop()                                                                                                                                                         |                                                      |
| ::public static void logMessage(str message)                                                                                                                                       |                                                      |
| public void endMarker(str transactionName)                                                                                                                                         |                                                      |
| public void beginMarker(str transactionName)                                                                                                                                       |                                                      |
| ::public static void logComponentMessage(str component, str message)                                                                                                               |                                                      |
| public void finalize()                                                                                                                                                             |                                                      |
| public void new()                                                                                                                                                                  | Initializes a new instance of the xClassTrace class. |

### Method isTracingEnabled

    public static boolean isTracingEnabled([Int64 keyword], [int level])

#### Parameters

keyword  

<!-- -->

level  

#### Return Value

### Method isTracingStarted

    public static boolean isTracingStarted()

#### Return Value

### Method kernelCustomerId

    public static str kernelCustomerId()

#### Return Value

### Method kernelRequestId

    public static Guid kernelRequestId()

#### Return Value

### Method kernelSessionId

    public static str kernelSessionId()

#### Return Value

### Method kernelUserId

    public static str kernelUserId()

#### Return Value

### Method start

    public static int start(str logFileName, [int logBufferSize], [int minBuffers], [int maxBuffers], [Int64 keywords], [int maxFileSize], [boolean useCircularLogging])

#### Parameters

logFileName  

<!-- -->

logBufferSize  

<!-- -->

minBuffers  

<!-- -->

maxBuffers  

<!-- -->

keywords  

<!-- -->

maxFileSize  

<!-- -->

useCircularLogging  

#### Return Value

### Method stop

    public static int stop()

#### Return Value

### Method logMessage

    public static void logMessage(str message)

#### Parameters

message  

### Method endMarker

    public void endMarker(str transactionName)

#### Parameters

transactionName  

### Method beginMarker

    public void beginMarker(str transactionName)

#### Parameters

transactionName  

### Method logComponentMessage

    public static void logComponentMessage(str component, str message)

#### Parameters

component  

<!-- -->

message  

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the xClassTrace class.

    public void new()

## Class xCompany
    class xCompany extends Object

### Remarks

### Examples

### Methods

| Method                                                                              | Description                                        |
|-------------------------------------------------------------------------------------|----------------------------------------------------|
| public DataAreaId dataArea(TableId tableId)                                         |                                                    |
| public SelectableDataArea ext()                                                     |                                                    |
| public boolean log(DatabaseLogType typeOfLog, TableId tableId, \[FieldId fieldId\]) |                                                    |
| public boolean logAlways(DatabaseLogType typeOfLog, \[boolean log\])                | Enables or disables logging for non-system tables. |
| public boolean reindex(\[TableId tableId\])                                         |                                                    |
| public void reloadLog()                                                             |                                                    |
| public void new(SelectableDataArea company)                                         | Initializes a new instance of the Object class.    |
| public void check()                                                                 |                                                    |
| public void reloadRights()                                                          |                                                    |
| public void flushCache(TableId tableId)                                             |                                                    |
| public void reloadTableCollections()                                                |                                                    |

### Method dataArea

    public DataAreaId dataArea(TableId tableId)

#### Parameters

tableId  

#### Return Value

### Method ext

    public SelectableDataArea ext()

#### Return Value

### Method log

    public boolean log(DatabaseLogType typeOfLog, TableId tableId, [FieldId fieldId])

#### Parameters

typeOfLog  

<!-- -->

tableId  

<!-- -->

fieldId  

#### Return Value

### Method logAlways

Enables or disables logging for non-system tables.

    public boolean logAlways(DatabaseLogType typeOfLog, [boolean log])

#### Parameters

typeOfLog  

<!-- -->

log  

#### Return Value

The status of the database logging for the indicated operation before the call.

#### Remarks

Without the optional typeOfLog parameter, this method will report the status of the database logging for the indicated operation. Note that if the optional parameter is provided, the method is guarded by CAS and the calling code must assert SysDatabaselogPermission.

### Method reindex

    public boolean reindex([TableId tableId])

#### Parameters

tableId  

#### Return Value

### Method reloadLog

    public void reloadLog()

### Method new

Initializes a new instance of the Object class.

    public void new(SelectableDataArea company)

#### Parameters

company  

### Method check

    public void check()

### Method reloadRights

    public void reloadRights()

### Method flushCache

    public void flushCache(TableId tableId)

#### Parameters

tableId  

### Method reloadTableCollections

    public void reloadTableCollections()

## Class xCompilerOutput
    class xCompilerOutput extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                         | Description                                              |
|--------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| public str getErrorMessage(int errorCode, int severity, str errorString)                                                       |                                                          |
| public container getSquiggleInfo(str treeNodePath)                                                                             |                                                          |
| public void compilerStatus(UtilElementType utilElementType, str utilElementName)                                               |                                                          |
| public void setActiveTab(int tab)                                                                                              |                                                          |
| public void startCompilationObject(str path)                                                                                   |                                                          |
| public void endCompilation()                                                                                                   |                                                          |
| public void startExport()                                                                                                      |                                                          |
| public void startCompilation(int flag, str path, int activeWindowHandle)                                                       |                                                          |
| public void importOutput(str buffer)                                                                                           |                                                          |
| public void endExport()                                                                                                        |                                                          |
| public void endCompilationObject(str path)                                                                                     |                                                          |
| public void startImport()                                                                                                      |                                                          |
| public void new()                                                                                                              | Initializes a new instance of the xCompilerOutput class. |
| public void compilerOutputMessage(str path, int errorCode, int line, int col, int severity, str errorString, str propertyName) |                                                          |
| public void exportOutput(str buffer)                                                                                           |                                                          |
| public void endCILGenerationOutput()                                                                                           |                                                          |
| public void cilGenerationOutput(str msg, str path, int severity, int line, int col)                                            |                                                          |
| public void endImport()                                                                                                        |                                                          |
| public void nextError()                                                                                                        |                                                          |
| public void startCILGenerationOutput()                                                                                         |                                                          |

### Method getErrorMessage

    public str getErrorMessage(int errorCode, int severity, str errorString)

#### Parameters

errorCode  

<!-- -->

severity  

<!-- -->

errorString  

#### Return Value

### Method getSquiggleInfo

    public container getSquiggleInfo(str treeNodePath)

#### Parameters

treeNodePath  

#### Return Value

### Method compilerStatus

    public void compilerStatus(UtilElementType utilElementType, str utilElementName)

#### Parameters

utilElementType  

<!-- -->

utilElementName  

### Method setActiveTab

    public void setActiveTab(int tab)

#### Parameters

tab  

### Method startCompilationObject

    public void startCompilationObject(str path)

#### Parameters

path  

### Method endCompilation

    public void endCompilation()

### Method startExport

    public void startExport()

### Method startCompilation

    public void startCompilation(int flag, str path, int activeWindowHandle)

#### Parameters

flag  

<!-- -->

path  

<!-- -->

activeWindowHandle  

### Method importOutput

    public void importOutput(str buffer)

#### Parameters

buffer  

### Method endExport

    public void endExport()

### Method endCompilationObject

    public void endCompilationObject(str path)

#### Parameters

path  

### Method startImport

    public void startImport()

### Method new

Initializes a new instance of the xCompilerOutput class.

    public void new()

### Method compilerOutputMessage

    public void compilerOutputMessage(str path, int errorCode, int line, int col, int severity, str errorString, str propertyName)

#### Parameters

path  

<!-- -->

errorCode  

<!-- -->

line  

<!-- -->

col  

<!-- -->

severity  

<!-- -->

errorString  

<!-- -->

propertyName  

### Method exportOutput

    public void exportOutput(str buffer)

#### Parameters

buffer  

### Method endCILGenerationOutput

    public void endCILGenerationOutput()

### Method cilGenerationOutput

    public void cilGenerationOutput(str msg, str path, int severity, int line, int col)

#### Parameters

msg  

<!-- -->

path  

<!-- -->

severity  

<!-- -->

line  

<!-- -->

col  

### Method endImport

    public void endImport()

### Method nextError

    public void nextError()

### Method startCILGenerationOutput

    public void startCILGenerationOutput()

## Class XDSServices
    class XDSServices extends Object

The XDSServices class provides APIs to manage the extensible data security (XDS) behavior.

### Remarks

### Examples

### Methods

| Method                                                                 | Description                                                                                                                       |
|------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| public int flushXDSMyConstructs(int reserved, str tablename)           | Flushes the MyConstruct table that is used with XDS.                                                                              |
| public str getQuerySQL(str queryname)                                  |                                                                                                                                   |
| public str getTableSQL(str tablename, \[str policyname\])              |                                                                                                                                   |
| public str getXDSBinding(str name)                                     |                                                                                                                                   |
| public str getXDSContext(int reserved)                                 |                                                                                                                                   |
| public int getXDSToFlushPerServiceSession(int reserved)                | Checks whether the MyConstruct tables will be flushed when the service session is returned to the pool.                           |
| public void finalize()                                                 |                                                                                                                                   |
| public void new()                                                      | Initializes a new instance of the XDSServices class.                                                                              |
| public void setXDSContext(int reserved, str contextstring)             |                                                                                                                                   |
| public void setXDSBinding(str name, str value)                         |                                                                                                                                   |
| public void setXDSState(int finalState)                                |                                                                                                                                   |
| public void setXDSToFlushPerServiceSession(int reserved, int newstate) | Sets the setting that determines whether the MyConstruct tables will be flushed when the service session is returned to the pool. |
| public void setXDSTrace(int flag, str value)                           |                                                                                                                                   |

### Method flushXDSMyConstructs

Flushes the MyConstruct table that is used with XDS.

    public int flushXDSMyConstructs(int reserved, str tablename)

#### Parameters

reserved  
The name of the MyConstruct table to flush. It no value is passed in, or if an empty string is passed in, all MyConstruct tables are flushed.

<!-- -->

tablename  
The name of the MyConstruct table to flush. It no value is passed in, or if an empty string is passed in, all MyConstruct tables are flushed.

#### Return Value

### Method getQuerySQL

    public str getQuerySQL(str queryname)

#### Parameters

queryname  

#### Return Value

### Method getTableSQL

    public str getTableSQL(str tablename, [str policyname])

#### Parameters

tablename  

<!-- -->

policyname  

#### Return Value

### Method getXDSBinding

    public str getXDSBinding(str name)

#### Parameters

name  

#### Return Value

### Method getXDSContext

    public str getXDSContext(int reserved)

#### Parameters

reserved  

#### Return Value

### Method getXDSToFlushPerServiceSession

Checks whether the MyConstruct tables will be flushed when the service session is returned to the pool.

    public int getXDSToFlushPerServiceSession(int reserved)

#### Parameters

reserved  
A reserved flag; not currently used.

#### Return Value

1 if the MyConstruct tables will be flushed when the service session is returned to the pool; otherwise, 0.

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the XDSServices class.

    public void new()

### Method setXDSContext

    public void setXDSContext(int reserved, str contextstring)

#### Parameters

reserved  

<!-- -->

contextstring  

### Method setXDSBinding

    public void setXDSBinding(str name, str value)

#### Parameters

name  

<!-- -->

value  

### Method setXDSState

    public void setXDSState(int finalState)

#### Parameters

finalState  

### Method setXDSToFlushPerServiceSession

Sets the setting that determines whether the MyConstruct tables will be flushed when the service session is returned to the pool.

    public void setXDSToFlushPerServiceSession(int reserved, int newstate)

#### Parameters

reserved  
A value that indicates whether to flush the MyConstruct tables when the service session is returned to the pool. Pass 1 to flush the tables and 0 not to flush them.

<!-- -->

newstate  
A value that indicates whether to flush the MyConstruct tables when the service session is returned to the pool. Pass 1 to flush the tables and 0 not to flush them.

### Method setXDSTrace

    public void setXDSTrace(int flag, str value)

#### Parameters

flag  

<!-- -->

value  

## Class xDynamicVarSet
    class xDynamicVarSet extends Object

### Remarks

### Examples

### Methods

| Method            | Description |
|-------------------|-------------|
| public void new() |             |

### Method new

    public void new()

## Class xExportToExcelController
    class xExportToExcelController extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                             | Description |
|------------------------------------------------------------------------------------------------------------------------------------|-------------|
| public boolean export()                                                                                                            |             |
| public boolean exportGrid(FormGridControl gridControl, boolean onlyMarkedRows)                                                     |             |
| public boolean performStaticExport(xFormRun formRun, FormGridControl gridControl, System.IO.Stream stream, boolean onlyMarkedRows) |             |
| public void new()                                                                                                                  |             |

### Method export

    public boolean export()

#### Return Value

### Method exportGrid

    public boolean exportGrid(FormGridControl gridControl, boolean onlyMarkedRows)

#### Parameters

gridControl  

<!-- -->

onlyMarkedRows  

#### Return Value

### Method performStaticExport

    public boolean performStaticExport(xFormRun formRun, FormGridControl gridControl, System.IO.Stream stream, boolean onlyMarkedRows)

#### Parameters

formRun  

<!-- -->

gridControl  

<!-- -->

stream  

<!-- -->

onlyMarkedRows  

#### Return Value

### Method new

    public void new()

## Class xFormRun
    class xFormRun extends ObjectRun

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                                                                                                                                                                                                         | Description |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| public boolean allowPrimaryKeyPreview(\[boolean display\])                                                                                                                                                                                                                                                                                                     |             |
| public boolean canClose()                                                                                                                                                                                                                                                                                                                                      |             |
| public boolean canSubmitToWorkflow()                                                                                                                                                                                                                                                                                                                           |             |
| public boolean checkViewOption(int viewOption)                                                                                                                                                                                                                                                                                                                 |             |
| public boolean closed()                                                                                                                                                                                                                                                                                                                                        |             |
| public boolean closedCancel()                                                                                                                                                                                                                                                                                                                                  |             |
| public boolean closedOk()                                                                                                                                                                                                                                                                                                                                      |             |
| public boolean contains(FormControl control)                                                                                                                                                                                                                                                                                                                   |             |
| public FormControl control(int controlId)                                                                                                                                                                                                                                                                                                                      |             |
| public FormControl controlCallingMethod()                                                                                                                                                                                                                                                                                                                      |             |
| public int controlId(str controlName)                                                                                                                                                                                                                                                                                                                          |             |
| public boolean controlMethodOverload(\[boolean value\])                                                                                                                                                                                                                                                                                                        |             |
| public Object controlMethodOverloadObject(\[Object value\])                                                                                                                                                                                                                                                                                                    |             |
| public boolean copy()                                                                                                                                                                                                                                                                                                                                          |             |
| public boolean cut()                                                                                                                                                                                                                                                                                                                                           |             |
| public FormObjectSet dataSource(\[AnyType objectSet\])                                                                                                                                                                                                                                                                                                         |             |
| public int dataSourceCount()                                                                                                                                                                                                                                                                                                                                   |             |
| public FormObjectSet defaultDataSource(\[FormObjectSet value\])                                                                                                                                                                                                                                                                                                |             |
| public boolean defaultInitialQueryValuesOnCreate(\[boolean value\])                                                                                                                                                                                                                                                                                            |             |
| public FormDesign design(\[int reserved\])                                                                                                                                                                                                                                                                                                                     |             |
| public Common docCursor()                                                                                                                                                                                                                                                                                                                                      |             |
| public boolean enableCountryRegion(\[boolean flag\])                                                                                                                                                                                                                                                                                                           |             |
| public Form form()                                                                                                                                                                                                                                                                                                                                             |             |
| public Common getActiveWorkflowConfiguration()                                                                                                                                                                                                                                                                                                                 |             |
| public Common getActiveWorkflowTrackingStatus()                                                                                                                                                                                                                                                                                                                |             |
| public Common getActiveWorkflowWorkItem()                                                                                                                                                                                                                                                                                                                      |             |
| public container getAutoCompleteString(int startIdx, \[FormControl control\], \[str searchString\])                                                                                                                                                                                                                                                            |             |
| public str getFormHelpTopic()                                                                                                                                                                                                                                                                                                                                  |             |
| public FormControl getNextField(FormControl control, \[int flags\])                                                                                                                                                                                                                                                                                            |             |
| public FormControl getPrevField(FormControl control, \[int flags\])                                                                                                                                                                                                                                                                                            |             |
| public boolean hasExecutedInit()                                                                                                                                                                                                                                                                                                                               |             |
| public int hWnd()                                                                                                                                                                                                                                                                                                                                              |             |
| public int installMessageProc(int message, int handle, str method)                                                                                                                                                                                                                                                                                             |             |
| public boolean inViewMode()                                                                                                                                                                                                                                                                                                                                    |             |
| public boolean isDataInteractionSupported()                                                                                                                                                                                                                                                                                                                    |             |
| public boolean isPreloadedInstance()                                                                                                                                                                                                                                                                                                                           |             |
| public boolean isFormPart()                                                                                                                                                                                                                                                                                                                                    |             |
| public boolean isFactBox()                                                                                                                                                                                                                                                                                                                                     |             |
| public boolean isLookupForm()                                                                                                                                                                                                                                                                                                                                  |             |
| public boolean isPartRemote()                                                                                                                                                                                                                                                                                                                                  |             |
| public boolean isPartLocal()                                                                                                                                                                                                                                                                                                                                   |             |
| public boolean isWorkflowEnabled()                                                                                                                                                                                                                                                                                                                             |             |
| public Common loadWorkflowConfiguration()                                                                                                                                                                                                                                                                                                                      |             |
| public boolean lockWindowUpdate(boolean lock)                                                                                                                                                                                                                                                                                                                  |             |
| public str name()                                                                                                                                                                                                                                                                                                                                              |             |
| public FormObjectSet objectSet(\[AnyType objectSet\])                                                                                                                                                                                                                                                                                                          |             |
| public boolean resetAsyncOperationsPendingState()                                                                                                                                                                                                                                                                                                              |             |
| public PageInteraction pageInteraction()                                                                                                                                                                                                                                                                                                                       |             |
| public boolean paste()                                                                                                                                                                                                                                                                                                                                         |             |
| public str recordingScopeId()                                                                                                                                                                                                                                                                                                                                  |             |
| public boolean removeMessageProc(int message, int handle)                                                                                                                                                                                                                                                                                                      |             |
| public List rootFormDataSources()                                                                                                                                                                                                                                                                                                                              |             |
| public boolean selectControl(FormControl control)                                                                                                                                                                                                                                                                                                              |             |
| public FormControl selectedControl()                                                                                                                                                                                                                                                                                                                           |             |
| public Common selectRecordModeSelectedRecord(\[Common selectedRecord\])                                                                                                                                                                                                                                                                                        |             |
| public FormControl selectTarget(\[FormControl target\])                                                                                                                                                                                                                                                                                                        |             |
| public Array tabOrder(\[Array newValue\])                                                                                                                                                                                                                                                                                                                      |             |
| public int task(int taskId)                                                                                                                                                                                                                                                                                                                                    |             |
| public str toString()                                                                                                                                                                                                                                                                                                                                          |             |
| public FormObjectSet workflowDataSource()                                                                                                                                                                                                                                                                                                                      |             |
| public str workflowType()                                                                                                                                                                                                                                                                                                                                      |             |
| public System.Threading.Tasks.Task runAsync(int runAsClassId, str runAsStaticMethodName, container parms, \[System.Threading.CancellationToken cancellationToken\], \[str callbackFormMethodName\], \[container asyncState\], \[str userId\], \[str company\], \[str language\], \[str partitionKey\], \[System.Threading.Tasks.TaskCreationOptions options\]) |             |
| public System.Threading.Tasks.Task setTimeoutEx(\[str formMethodName\], \[container parms\], \[int delay\], \[System.Threading.CancellationToken cancellationToken\])                                                                                                                                                                                          |             |
| public void setParentHandle(int hwnd)                                                                                                                                                                                                                                                                                                                          |             |
| public void setFormHelpTopic(str formHelpTopic)                                                                                                                                                                                                                                                                                                                |             |
| public void setFactBoxEditable()                                                                                                                                                                                                                                                                                                                               |             |
| public void setAutoCompleteString(str string, AnyType control)                                                                                                                                                                                                                                                                                                 |             |
| public void RaiseOnClosing(\[FormEventArgs e\])                                                                                                                                                                                                                                                                                                                |             |
| public void inlineLoadingKey(FormControl parentControl)                                                                                                                                                                                                                                                                                                        |             |
| public void closeSelect(str selectString)                                                                                                                                                                                                                                                                                                                      |             |
| public void RaiseOnActivated(\[FormEventArgs e\])                                                                                                                                                                                                                                                                                                              |             |
| public void prevField(\[int flags\])                                                                                                                                                                                                                                                                                                                           |             |
| public void send()                                                                                                                                                                                                                                                                                                                                             |             |
| public void RaiseOnInitializing(\[FormEventArgs e\])                                                                                                                                                                                                                                                                                                           |             |
| public void updateWorkflowControls()                                                                                                                                                                                                                                                                                                                           |             |
| public void closeCancel()                                                                                                                                                                                                                                                                                                                                      |             |
| public void lastField(\[int flags\])                                                                                                                                                                                                                                                                                                                           |             |
| public void wait(\[boolean modal\])                                                                                                                                                                                                                                                                                                                            |             |
| public void unLock(\[boolean arrangeNow\])                                                                                                                                                                                                                                                                                                                     |             |
| private void OnInitialized(\[xFormRun sender\], \[FormEventArgs e\])                                                                                                                                                                                                                                                                                           |             |
| public void detach()                                                                                                                                                                                                                                                                                                                                           |             |
| public void resetStatusBarBackgroundColor()                                                                                                                                                                                                                                                                                                                    |             |
| private void OnClosing(\[xFormRun sender\], \[FormEventArgs e\])                                                                                                                                                                                                                                                                                               |             |
| public void addDisplayMethod(str name, int displayKind, int displayType, int displayXType, int displayRecord, \[str dataSourceName\], \[boolean isTableDisplayMethod\])                                                                                                                                                                                        |             |
| public void print()                                                                                                                                                                                                                                                                                                                                            |             |
| public void activate(boolean active)                                                                                                                                                                                                                                                                                                                           |             |
| public void resize(int width, int height)                                                                                                                                                                                                                                                                                                                      |             |
| public void reload(\[xArgs args\])                                                                                                                                                                                                                                                                                                                             |             |
| public void finalize()                                                                                                                                                                                                                                                                                                                                         |             |
| public void RaiseOnInitialized(\[FormEventArgs e\])                                                                                                                                                                                                                                                                                                            |             |
| public void resetSize()                                                                                                                                                                                                                                                                                                                                        |             |
| public void clientId(str clientId)                                                                                                                                                                                                                                                                                                                             |             |
| public void createRecord(str formDataSourceName, \[boolean append\])                                                                                                                                                                                                                                                                                           |             |
| public void firstField(\[int flags\])                                                                                                                                                                                                                                                                                                                          |             |
| public void savePersonalization(str controlName, str propertyKey, str propertyValue)                                                                                                                                                                                                                                                                           |             |
| public void expandFactBoxPaneAtStart()                                                                                                                                                                                                                                                                                                                         |             |
| public void redraw()                                                                                                                                                                                                                                                                                                                                           |             |
| public void arrange()                                                                                                                                                                                                                                                                                                                                          |             |
| public void blockPersonalization(boolean blockPersonalization)                                                                                                                                                                                                                                                                                                 |             |
| public void nextField(\[int flags\])                                                                                                                                                                                                                                                                                                                           |             |
| public void nextGroup()                                                                                                                                                                                                                                                                                                                                        |             |
| public void prevGroup()                                                                                                                                                                                                                                                                                                                                        |             |
| public void setFormPartStyle(boolean isFactBox)                                                                                                                                                                                                                                                                                                                |             |
| public void run()                                                                                                                                                                                                                                                                                                                                              |             |
| public void setActive()                                                                                                                                                                                                                                                                                                                                        |             |
| public void closeSelectRecord(Common selectedRecord)                                                                                                                                                                                                                                                                                                           |             |
| public void registerFormSpecializedCustomControl(str customControlName)                                                                                                                                                                                                                                                                                        |             |
| public void setApply(Object object, \[Object parm\])                                                                                                                                                                                                                                                                                                           |             |
| public void new(xArgs args)                                                                                                                                                                                                                                                                                                                                    |             |
| public void RegisterXppILImplementation(str className)                                                                                                                                                                                                                                                                                                         |             |
| public void sysColorChanged()                                                                                                                                                                                                                                                                                                                                  |             |
| public void selectRecordMode(\[FormControl control\])                                                                                                                                                                                                                                                                                                          |             |
| private void OnPostRun(\[xFormRun sender\], \[FormEventArgs e\])                                                                                                                                                                                                                                                                                               |             |
| public void skipSaveUserSetting(boolean skip)                                                                                                                                                                                                                                                                                                                  |             |
| public void selectMode(\[FormControl control\])                                                                                                                                                                                                                                                                                                                |             |
| public void printPreview()                                                                                                                                                                                                                                                                                                                                     |             |
| private void OnActivated(\[xFormRun sender\], \[FormEventArgs e\])                                                                                                                                                                                                                                                                                             |             |
| public void collapseFactBoxPaneAtStart()                                                                                                                                                                                                                                                                                                                       |             |
| public void lock()                                                                                                                                                                                                                                                                                                                                             |             |
| public void init()                                                                                                                                                                                                                                                                                                                                             |             |
| public void formOnTop()                                                                                                                                                                                                                                                                                                                                        |             |
| public void close()                                                                                                                                                                                                                                                                                                                                            |             |
| public void delAutoCompleteString(\[AnyType control\])                                                                                                                                                                                                                                                                                                         |             |
| public void closeOk()                                                                                                                                                                                                                                                                                                                                          |             |
| public void modeledQueryName(str queryName)                                                                                                                                                                                                                                                                                                                    |             |
| public void initWorkflowControls()                                                                                                                                                                                                                                                                                                                             |             |
| public void setOrder(FormControl control, FormControl control1, \[boolean before\])                                                                                                                                                                                                                                                                            |             |
| public void allowCrossFormLinks(boolean allowCrossFormLinks)                                                                                                                                                                                                                                                                                                   |             |
| public void RaiseOnPostRun(\[FormEventArgs e\])                                                                                                                                                                                                                                                                                                                |             |
| public void setStatusBarBackgroundColor(int a, int r, int g, int b)                                                                                                                                                                                                                                                                                            |             |
| public void loadPersonalization()                                                                                                                                                                                                                                                                                                                              |             |
| public void doApply()                                                                                                                                                                                                                                                                                                                                          |             |
| private void OnInitializing(\[xFormRun sender\], \[FormEventArgs e\])                                                                                                                                                                                                                                                                                          |             |
| public void flushCountryRegionCodeCache()                                                                                                                                                                                                                                                                                                                      |             |
| public void localRefresh()                                                                                                                                                                                                                                                                                                                                     |             |

### Method allowPrimaryKeyPreview

    public boolean allowPrimaryKeyPreview([boolean display])

#### Parameters

display  

#### Return Value

### Method canClose

    public boolean canClose()

#### Return Value

### Method canSubmitToWorkflow

    public boolean canSubmitToWorkflow()

#### Return Value

### Method checkViewOption

    public boolean checkViewOption(int viewOption)

#### Parameters

viewOption  

#### Return Value

### Method closed

    public boolean closed()

#### Return Value

### Method closedCancel

    public boolean closedCancel()

#### Return Value

### Method closedOk

    public boolean closedOk()

#### Return Value

### Method contains

    public boolean contains(FormControl control)

#### Parameters

control  

#### Return Value

### Method control

    public FormControl control(int controlId)

#### Parameters

controlId  

#### Return Value

### Method controlCallingMethod

    public FormControl controlCallingMethod()

#### Return Value

### Method controlId

    public int controlId(str controlName)

#### Parameters

controlName  

#### Return Value

### Method controlMethodOverload

    public boolean controlMethodOverload([boolean value])

#### Parameters

value  

#### Return Value

### Method controlMethodOverloadObject

    public Object controlMethodOverloadObject([Object value])

#### Parameters

value  

#### Return Value

### Method copy

    public boolean copy()

#### Return Value

### Method cut

    public boolean cut()

#### Return Value

### Method dataSource

    public FormObjectSet dataSource([AnyType objectSet])

#### Parameters

objectSet  

#### Return Value

### Method dataSourceCount

    public int dataSourceCount()

#### Return Value

### Method defaultDataSource

    public FormObjectSet defaultDataSource([FormObjectSet value])

#### Parameters

value  

#### Return Value

### Method defaultInitialQueryValuesOnCreate

    public boolean defaultInitialQueryValuesOnCreate([boolean value])

#### Parameters

value  

#### Return Value

### Method design

    public FormDesign design([int reserved])

#### Parameters

reserved  

#### Return Value

### Method docCursor

    public Common docCursor()

#### Return Value

### Method enableCountryRegion

    public boolean enableCountryRegion([boolean flag])

#### Parameters

flag  

#### Return Value

### Method form

    public Form form()

#### Return Value

### Method getActiveWorkflowConfiguration

    public Common getActiveWorkflowConfiguration()

#### Return Value

### Method getActiveWorkflowTrackingStatus

    public Common getActiveWorkflowTrackingStatus()

#### Return Value

### Method getActiveWorkflowWorkItem

    public Common getActiveWorkflowWorkItem()

#### Return Value

### Method getAutoCompleteString

    public container getAutoCompleteString(int startIdx, [FormControl control], [str searchString])

#### Parameters

startIdx  

<!-- -->

control  

<!-- -->

searchString  

#### Return Value

### Method getFormHelpTopic

    public str getFormHelpTopic()

#### Return Value

### Method getNextField

    public FormControl getNextField(FormControl control, [int flags])

#### Parameters

control  

<!-- -->

flags  

#### Return Value

### Method getPrevField

    public FormControl getPrevField(FormControl control, [int flags])

#### Parameters

control  

<!-- -->

flags  

#### Return Value

### Method hasExecutedInit

    public boolean hasExecutedInit()

#### Return Value

### Method hWnd

    public int hWnd()

#### Return Value

### Method installMessageProc

    public int installMessageProc(int message, int handle, str method)

#### Parameters

message  

<!-- -->

handle  

<!-- -->

method  

#### Return Value

### Method inViewMode

    public boolean inViewMode()

#### Return Value

### Method isDataInteractionSupported

    public boolean isDataInteractionSupported()

#### Return Value

### Method isPreloadedInstance

    public boolean isPreloadedInstance()

#### Return Value

### Method isFormPart

    public boolean isFormPart()

#### Return Value

### Method isFactBox

    public boolean isFactBox()

#### Return Value

### Method isLookupForm

    public boolean isLookupForm()

#### Return Value

### Method isPartRemote

    public boolean isPartRemote()

#### Return Value

### Method isPartLocal

    public boolean isPartLocal()

#### Return Value

### Method isWorkflowEnabled

    public boolean isWorkflowEnabled()

#### Return Value

### Method loadWorkflowConfiguration

    public Common loadWorkflowConfiguration()

#### Return Value

### Method lockWindowUpdate

    public boolean lockWindowUpdate(boolean lock)

#### Parameters

lock  

#### Return Value

### Method name

    public str name()

#### Return Value

### Method objectSet

    public FormObjectSet objectSet([AnyType objectSet])

#### Parameters

objectSet  

#### Return Value

### Method resetAsyncOperationsPendingState

    public boolean resetAsyncOperationsPendingState()

#### Return Value

### Method pageInteraction

    public PageInteraction pageInteraction()

#### Return Value

### Method paste

    public boolean paste()

#### Return Value

### Method recordingScopeId

    public str recordingScopeId()

#### Return Value

### Method removeMessageProc

    public boolean removeMessageProc(int message, int handle)

#### Parameters

message  

<!-- -->

handle  

#### Return Value

### Method rootFormDataSources

    public List rootFormDataSources()

#### Return Value

### Method selectControl

    public boolean selectControl(FormControl control)

#### Parameters

control  

#### Return Value

### Method selectedControl

    public FormControl selectedControl()

#### Return Value

### Method selectRecordModeSelectedRecord

    public Common selectRecordModeSelectedRecord([Common selectedRecord])

#### Parameters

selectedRecord  

#### Return Value

### Method selectTarget

    public FormControl selectTarget([FormControl target])

#### Parameters

target  

#### Return Value

### Method tabOrder

    public Array tabOrder([Array newValue])

#### Parameters

newValue  

#### Return Value

### Method task

    public int task(int taskId)

#### Parameters

taskId  

#### Return Value

### Method toString

    public str toString()

#### Return Value

### Method workflowDataSource

    public FormObjectSet workflowDataSource()

#### Return Value

### Method workflowType

    public str workflowType()

#### Return Value

### Method runAsync

    public System.Threading.Tasks.Task runAsync(int runAsClassId, str runAsStaticMethodName, container parms, [System.Threading.CancellationToken cancellationToken], [str callbackFormMethodName], [container asyncState], [str userId], [str company], [str language], [str partitionKey], [System.Threading.Tasks.TaskCreationOptions options])

#### Parameters

runAsClassId  

<!-- -->

runAsStaticMethodName  

<!-- -->

parms  

<!-- -->

cancellationToken  

<!-- -->

callbackFormMethodName  

<!-- -->

asyncState  

<!-- -->

userId  

<!-- -->

company  

<!-- -->

language  

<!-- -->

partitionKey  

<!-- -->

options  

#### Return Value

### Method setTimeoutEx

    public System.Threading.Tasks.Task setTimeoutEx([str formMethodName], [container parms], [int delay], [System.Threading.CancellationToken cancellationToken])

#### Parameters

formMethodName  

<!-- -->

parms  

<!-- -->

delay  

<!-- -->

cancellationToken  

#### Return Value

### Method setParentHandle

    public void setParentHandle(int hwnd)

#### Parameters

hwnd  

### Method setFormHelpTopic

    public void setFormHelpTopic(str formHelpTopic)

#### Parameters

formHelpTopic  

### Method setFactBoxEditable

    public void setFactBoxEditable()

### Method setAutoCompleteString

    public void setAutoCompleteString(str string, AnyType control)

#### Parameters

string  

<!-- -->

control  

### Method RaiseOnClosing

    public void RaiseOnClosing([FormEventArgs e])

#### Parameters

e  

### Method inlineLoadingKey

    public void inlineLoadingKey(FormControl parentControl)

#### Parameters

parentControl  

### Method closeSelect

    public void closeSelect(str selectString)

#### Parameters

selectString  

### Method RaiseOnActivated

    public void RaiseOnActivated([FormEventArgs e])

#### Parameters

e  

### Method prevField

    public void prevField([int flags])

#### Parameters

flags  

### Method send

    public void send()

### Method RaiseOnInitializing

    public void RaiseOnInitializing([FormEventArgs e])

#### Parameters

e  

### Method updateWorkflowControls

    public void updateWorkflowControls()

### Method closeCancel

    public void closeCancel()

### Method lastField

    public void lastField([int flags])

#### Parameters

flags  

### Method wait

    public void wait([boolean modal])

#### Parameters

modal  

### Method unLock

    public void unLock([boolean arrangeNow])

#### Parameters

arrangeNow  

### Method OnInitialized

    private void OnInitialized([xFormRun sender], [FormEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method detach

    public void detach()

### Method resetStatusBarBackgroundColor

    public void resetStatusBarBackgroundColor()

### Method OnClosing

    private void OnClosing([xFormRun sender], [FormEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method addDisplayMethod

    public void addDisplayMethod(str name, int displayKind, int displayType, int displayXType, int displayRecord, [str dataSourceName], [boolean isTableDisplayMethod])

#### Parameters

name  

<!-- -->

displayKind  

<!-- -->

displayType  

<!-- -->

displayXType  

<!-- -->

displayRecord  

<!-- -->

dataSourceName  

<!-- -->

isTableDisplayMethod  

### Method print

    public void print()

### Method activate

    public void activate(boolean active)

#### Parameters

active  

### Method resize

    public void resize(int width, int height)

#### Parameters

width  

<!-- -->

height  

### Method reload

    public void reload([xArgs args])

#### Parameters

args  

### Method finalize

    public void finalize()

### Method RaiseOnInitialized

    public void RaiseOnInitialized([FormEventArgs e])

#### Parameters

e  

### Method resetSize

    public void resetSize()

### Method clientId

    public void clientId(str clientId)

#### Parameters

clientId  

### Method createRecord

    public void createRecord(str formDataSourceName, [boolean append])

#### Parameters

formDataSourceName  

<!-- -->

append  

### Method firstField

    public void firstField([int flags])

#### Parameters

flags  

### Method savePersonalization

    public void savePersonalization(str controlName, str propertyKey, str propertyValue)

#### Parameters

controlName  

<!-- -->

propertyKey  

<!-- -->

propertyValue  

### Method expandFactBoxPaneAtStart

    public void expandFactBoxPaneAtStart()

### Method redraw

    public void redraw()

### Method arrange

    public void arrange()

### Method blockPersonalization

    public void blockPersonalization(boolean blockPersonalization)

#### Parameters

blockPersonalization  

### Method nextField

    public void nextField([int flags])

#### Parameters

flags  

### Method nextGroup

    public void nextGroup()

### Method prevGroup

    public void prevGroup()

### Method setFormPartStyle

    public void setFormPartStyle(boolean isFactBox)

#### Parameters

isFactBox  

### Method run

    public void run()

### Method setActive

    public void setActive()

### Method closeSelectRecord

    public void closeSelectRecord(Common selectedRecord)

#### Parameters

selectedRecord  

### Method registerFormSpecializedCustomControl

    public void registerFormSpecializedCustomControl(str customControlName)

#### Parameters

customControlName  

### Method setApply

    public void setApply(Object object, [Object parm])

#### Parameters

object  

<!-- -->

parm  

### Method new

    public void new(xArgs args)

#### Parameters

args  

### Method RegisterXppILImplementation

    public void RegisterXppILImplementation(str className)

#### Parameters

className  

### Method sysColorChanged

    public void sysColorChanged()

### Method selectRecordMode

    public void selectRecordMode([FormControl control])

#### Parameters

control  

### Method OnPostRun

    private void OnPostRun([xFormRun sender], [FormEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method skipSaveUserSetting

    public void skipSaveUserSetting(boolean skip)

#### Parameters

skip  

### Method selectMode

    public void selectMode([FormControl control])

#### Parameters

control  

### Method printPreview

    public void printPreview()

### Method OnActivated

    private void OnActivated([xFormRun sender], [FormEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method collapseFactBoxPaneAtStart

    public void collapseFactBoxPaneAtStart()

### Method lock

    public void lock()

### Method init

    public void init()

### Method formOnTop

    public void formOnTop()

### Method close

    public void close()

### Method delAutoCompleteString

    public void delAutoCompleteString([AnyType control])

#### Parameters

control  

### Method closeOk

    public void closeOk()

### Method modeledQueryName

    public void modeledQueryName(str queryName)

#### Parameters

queryName  

### Method initWorkflowControls

    public void initWorkflowControls()

### Method setOrder

    public void setOrder(FormControl control, FormControl control1, [boolean before])

#### Parameters

control  

<!-- -->

control1  

<!-- -->

before  

### Method allowCrossFormLinks

    public void allowCrossFormLinks(boolean allowCrossFormLinks)

#### Parameters

allowCrossFormLinks  

### Method RaiseOnPostRun

    public void RaiseOnPostRun([FormEventArgs e])

#### Parameters

e  

### Method setStatusBarBackgroundColor

    public void setStatusBarBackgroundColor(int a, int r, int g, int b)

#### Parameters

a  

<!-- -->

r  

<!-- -->

g  

<!-- -->

b  

### Method loadPersonalization

    public void loadPersonalization()

### Method doApply

    public void doApply()

### Method OnInitializing

    private void OnInitializing([xFormRun sender], [FormEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method flushCountryRegionCodeCache

    public void flushCountryRegionCodeCache()

### Method localRefresh

    public void localRefresh()

## Class xGlobal
    class xGlobal extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                                                                                                                                                                                                                                             | Description                                        |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------|
| ::public static ClientType clientKind()                                                                                                                                                                                                                                                                                                                                                            |                                                    |
| ::public static SelectableDataArea company(TableId tableid, \[SelectableDataArea company\])                                                                                                                                                                                                                                                                                                        |                                                    |
| ::public static str computerName()                                                                                                                                                                                                                                                                                                                                                                 |                                                    |
| ::public static boolean hasClient()                                                                                                                                                                                                                                                                                                                                                                |                                                    |
| ::public static int infologLine()                                                                                                                                                                                                                                                                                                                                                                  | Returns the number of lines in the Infolog buffer. |
| ::public static boolean isAOS()                                                                                                                                                                                                                                                                                                                                                                    |                                                    |
| ::public static boolean isGuest()                                                                                                                                                                                                                                                                                                                                                                  |                                                    |
| ::public static boolean isUserLanguageRTL()                                                                                                                                                                                                                                                                                                                                                        |                                                    |
| ::public static container languageList()                                                                                                                                                                                                                                                                                                                                                           |                                                    |
| ::public static str machineTzDisplayName()                                                                                                                                                                                                                                                                                                                                                         |                                                    |
| ::public static boolean isObjectOnServer(AnyType object)                                                                                                                                                                                                                                                                                                                                           |                                                    |
| ::public static int randomPositiveInt32()                                                                                                                                                                                                                                                                                                                                                          |                                                    |
| ::public static boolean terminalServer()                                                                                                                                                                                                                                                                                                                                                           |                                                    |
| ::public static WorkerSessionType workerSessionType()                                                                                                                                                                                                                                                                                                                                              |                                                    |
| ::public static System.Threading.Tasks.Task runAsync(int runAsClassId, str runAsStaticMethodName, container parms, \[System.Threading.CancellationToken cancellationToken\], \[int callbackClassId\], \[str callbackStaticMethodName\], \[container asyncState\], \[str userId\], \[str company\], \[str language\], \[str partitionKey\], \[System.Threading.Tasks.TaskCreationOptions options\]) |                                                    |
| ::public static System.Threading.Tasks.Task runAsyncWithObjectCallback(int runAsClassId, str runAsStaticMethodName, container parms, Object callbackObject, str callbackStaticMethodName)                                                                                                                                                                                                          |                                                    |
| ::public static void forceFormPreload()                                                                                                                                                                                                                                                                                                                                                            | Forces form preloading to occur immediately.       |
| private void new()                                                                                                                                                                                                                                                                                                                                                                                 | Initializes a new instance of the xGlobal class.   |

### Method clientKind

    public static ClientType clientKind()

#### Return Value

### Method company

    public static SelectableDataArea company(TableId tableid, [SelectableDataArea company])

#### Parameters

tableid  

<!-- -->

company  

#### Return Value

### Method computerName

    public static str computerName()

#### Return Value

### Method hasClient

    public static boolean hasClient()

#### Return Value

### Method infologLine

Returns the number of lines in the Infolog buffer.

    public static int infologLine()

#### Return Value

#### Remarks

This method has similar functionality to the xInfo.line method, but it improves performance and lowers network load when you are executing server-side code. When xInfo.line is run on the server, it makes a call to the client to retrieve the number of lines in the Infolog buffer. The xGlobal::infologLine method retrieves the line count of the server-side Infolog buffer, so that you do not have to call to the client. When the xGlobal::infologLine method is called on the client, it returns the count directly from the Infolog buffer on the client. This method is especially useful when you are writing server-side code that processes exceptions. The number of lines in the Infolog is typically stored before a try/catch block is entered. If an exception occurs, the number of lines that were previously stored is used to determine which messages were logged during the code in the try block. If no exceptions occur, the stored Infolog buffer line count is often unused. By using the xGlobal::infologLine method instead of the xInfo.line method to retrieve the Infolog lines, you avoid a round trip to the client.

### Method isAOS

    public static boolean isAOS()

#### Return Value

### Method isGuest

    public static boolean isGuest()

#### Return Value

### Method isUserLanguageRTL

    public static boolean isUserLanguageRTL()

#### Return Value

### Method languageList

    public static container languageList()

#### Return Value

### Method machineTzDisplayName

    public static str machineTzDisplayName()

#### Return Value

### Method isObjectOnServer

    public static boolean isObjectOnServer(AnyType object)

#### Parameters

object  

#### Return Value

### Method randomPositiveInt32

    public static int randomPositiveInt32()

#### Return Value

### Method terminalServer

    public static boolean terminalServer()

#### Return Value

### Method workerSessionType

    public static WorkerSessionType workerSessionType()

#### Return Value

### Method runAsync

    public static System.Threading.Tasks.Task runAsync(int runAsClassId, str runAsStaticMethodName, container parms, [System.Threading.CancellationToken cancellationToken], [int callbackClassId], [str callbackStaticMethodName], [container asyncState], [str userId], [str company], [str language], [str partitionKey], [System.Threading.Tasks.TaskCreationOptions options])

#### Parameters

runAsClassId  

<!-- -->

runAsStaticMethodName  

<!-- -->

parms  

<!-- -->

cancellationToken  

<!-- -->

callbackClassId  

<!-- -->

callbackStaticMethodName  

<!-- -->

asyncState  

<!-- -->

userId  

<!-- -->

company  

<!-- -->

language  

<!-- -->

partitionKey  

<!-- -->

options  

#### Return Value

### Method runAsyncWithObjectCallback

    public static System.Threading.Tasks.Task runAsyncWithObjectCallback(int runAsClassId, str runAsStaticMethodName, container parms, Object callbackObject, str callbackStaticMethodName)

#### Parameters

runAsClassId  

<!-- -->

runAsStaticMethodName  

<!-- -->

parms  

<!-- -->

callbackObject  

<!-- -->

callbackStaticMethodName  

#### Return Value

### Method forceFormPreload

Forces form preloading to occur immediately.

    public static void forceFormPreload()

#### Remarks

Normally, preloading occurs only when the client has gone idle. In scenarios where long-running X++ execution is occurring, this method can be used to force form preloading.

### Method new

Initializes a new instance of the xGlobal class.

    private void new()

## Class xInfo
    class xInfo extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                                                       | Description                                                                                                                                                                             |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public int removeMessage(Int64 messageId)                                                                                                                                                                    |                                                                                                                                                                                         |
| public Int64 insertMessage(MessageSeverity type, str message)                                                                                                                                                |                                                                                                                                                                                         |
| public Exception add(Exception exceptionType, str string, \[str helpURL\], \[Object obj\], \[boolean buildprefix\])                                                                                          | Adds a string to the Infolog buffer.                                                                                                                                                    |
| public Exception addException(str string, str stackTrace)                                                                                                                                                    |                                                                                                                                                                                         |
| public container breakpoint(\[container breakpoint\])                                                                                                                                                        | Gets or sets information about breakpoints.                                                                                                                                             |
| public boolean canShowCreateRuleMenuItem(xFormRun caller)                                                                                                                                                    | Determines whether the menu item for the Create alert rule form should be displayed for a form.                                                                                         |
| public boolean canShutdown(boolean silent)                                                                                                                                                                   | Tests whether the system can be shut down. Do not use this method. Use the version that is overridden on the Info class instead.                                                        |
| public boolean canViewAlertInbox()                                                                                                                                                                           | Determines whether the current user has permission to view the View alerts form.                                                                                                        |
| public xCompilerOutput compilerOutput(\[Object compilerOut\])                                                                                                                                                | Gets or sets the compiler output object. The compiler output object is the Compiler output window by default.                                                                           |
| public container copy(int from, int to)                                                                                                                                                                      | Copies lines from the Infolog buffer.                                                                                                                                                   |
| public int createDevelopmentWorkspaceWindow()                                                                                                                                                                |                                                                                                                                                                                         |
| public int createWorkspaceWindow()                                                                                                                                                                           | Opens a new workspace window. For example, this enables you to open different sets of application objects in different windows, or to work with two different sets of company accounts. |
| public UtilEntryLevel currentAOLayer()                                                                                                                                                                       | Retrieves the current layer you are running in such as SYS, or USR.                                                                                                                     |
| public container cut(int from, int to)                                                                                                                                                                       | Cuts lines from the Infolog buffer.                                                                                                                                                     |
| public str documentationLanguage(\[str languageCode\])                                                                                                                                                       | Gets or sets the language that is used for the Microsoft Dynamics AX documentation.                                                                                                     |
| public container export()                                                                                                                                                                                    |                                                                                                                                                                                         |
| public TreeNode findNode(str nodePath)                                                                                                                                                                       | Retrieves the specified a tree node.                                                                                                                                                    |
| public TreeNode getDocNode(UtilFileType helpType, int UtilType, str Name, \[UtilElementId ParentId\], \[int Type\], \[UtilEntryLevel UtilLevel\], \[boolean ForceLevel\], \[int Mode\], \[boolean OldUtil\]) | Retrieves the specified documentation nodes from the AOT.                                                                                                                               |
| public TreeNode getImportedNode(int id, int utilfiletype, UtilElementType utiltype, str name, int fileposition, int Flag)                                                                                    | Creates an instance of a tree node from an XPO file but does not import it into the AOT. For example, this allows you to compare it with another version of the same tree node.         |
| public TreeNode getNode(UtilElementType UtilType, str Name, \[UtilElementId ParentId\], \[int Type\], \[UtilEntryLevel Utillevel\], \[boolean Forcelevel\], \[int Mode\], \[boolean OldUtil\])               | Retrieves a tree node that corresponds to a node in the AOT.                                                                                                                            |
| public int getNodeResid(UtilElementType nodeType)                                                                                                                                                            | Retrieves the resource ID for the icon that is used to display nodes of the specified type.                                                                                             |
| public Struct getTaskInfo(int taskNumber)                                                                                                                                                                    |                                                                                                                                                                                         |
| public UserSetup getUserSetup()                                                                                                                                                                              | Retrieves a UserSetup object that is used to set user parameters.                                                                                                                       |
| public container getWorkspaceList()                                                                                                                                                                          |                                                                                                                                                                                         |
| public int hWnd(\[int workspaceNum\])                                                                                                                                                                        | Retrieves a handle to the Microsoft Dynamics AXNavigation Pane window.                                                                                                                  |
| public boolean import(container infologContainer, \[boolean clearExistingInfolog\])                                                                                                                          |                                                                                                                                                                                         |
| public int importElement(int id, int utilfiletype, UtilElementType utiltype, str name, int fileposition, int Flag)                                                                                           | Specifies the object to be imported.                                                                                                                                                    |
| public int importString(str source, UtilElementType kind, str name)                                                                                                                                          | Imports an object from a file.                                                                                                                                                          |
| public int instance()                                                                                                                                                                                        | Retrieves a handle to the current instance of the application.                                                                                                                          |
| public str isoCurrencyCode(\[str code\])                                                                                                                                                                     | Gets or sets the currency code.                                                                                                                                                         |
| public boolean IsVisible()                                                                                                                                                                                   | Determines whether the client window is not minimized.                                                                                                                                  |
| public str language(\[str languageCode\])                                                                                                                                                                    | Gets or sets the language for the GUI.                                                                                                                                                  |
| public Exception level(int line)                                                                                                                                                                             | Retrieves the exception level of a line in the Infolog buffer.                                                                                                                          |
| public int line()                                                                                                                                                                                            | Retrieves the number of lines in the Infolog buffer.                                                                                                                                    |
| public MessageWin messageWin()                                                                                                                                                                               | Enables you to send output from the Infolog to the Message window.                                                                                                                      |
| public Real nationalCurrencyFactor(\[Real factor\])                                                                                                                                                          |                                                                                                                                                                                         |
| public str nationalCurrencyPostfix(\[str string\])                                                                                                                                                           |                                                                                                                                                                                         |
| public str nationalCurrencyPrefix(\[str string\])                                                                                                                                                            |                                                                                                                                                                                         |
| public xNavPane navPane()                                                                                                                                                                                    | Retrieves an xNavPane object, the primary navigation control class.                                                                                                                     |
| public int num(\[Exception exceptionType\])                                                                                                                                                                  | Retrieves the number of exceptions of the specified type in the Infolog buffer.                                                                                                         |
| public int prevInstance()                                                                                                                                                                                    | Retrieves a handle to the previous instance of the application.                                                                                                                         |
| public int processId()                                                                                                                                                                                       | Retrieves the ID for the Microsoft Dynamics AX process.                                                                                                                                 |
| public TreeNode projectRootNode()                                                                                                                                                                            | Returns the X++ Projects node.                                                                                                                                                          |
| public TreeNode rootNode()                                                                                                                                                                                   | Retrieves the root of the application object tree.                                                                                                                                      |
| public int startImport(str file, int flag, \[str labelSubstitutes\])                                                                                                                                         | Creates an import context.                                                                                                                                                              |
| public str text(\[int line\])                                                                                                                                                                                | Retrieves a line of text from the Infolog.                                                                                                                                              |
| public TreeNode userNode()                                                                                                                                                                                   |                                                                                                                                                                                         |
| public AnyType webSession(\[AnyType value\])                                                                                                                                                                 |                                                                                                                                                                                         |
| ::public static container activeXControls()                                                                                                                                                                  | Retrieves a list of the ActiveX controls that are in Microsoft Dynamics AX.                                                                                                             |
| ::public static str AOTLogDirectory()                                                                                                                                                                        | Gets the path to the log directory for the current installation.                                                                                                                        |
| ::public static container automationObjects()                                                                                                                                                                | Retrieves the list of COM objects that are available in Microsoft Dynamics AX.                                                                                                          |
| ::public static str buildNo()                                                                                                                                                                                | Retrieves the kernel build number of the current Microsoft Dynamics AX executable.                                                                                                      |
| ::public static str compilationDate()                                                                                                                                                                        | Retrieves the date on which the current version of Microsoft Dynamics AX was last compiled.                                                                                             |
| ::public static str compilationTime()                                                                                                                                                                        | Retrieves the time at which the current version of Microsoft Dynamics AX was last compiled.                                                                                             |
| ::public static str componentName()                                                                                                                                                                          | Retrieves the path to the component.                                                                                                                                                    |
| ::public static str configuration()                                                                                                                                                                          | Retrieves the current client configuration.                                                                                                                                             |
| ::public static int currentWorkspaceNum()                                                                                                                                                                    | Retrieves the application window ID of the current workspace.                                                                                                                           |
| ::public static str directory(DirectoryType type)                                                                                                                                                            | Retrieves the path to the directory where the Microsoft Dynamics AX client has been installed.                                                                                          |
| ::public static Date expireDate()                                                                                                                                                                            | Retrieves the date on which the license for the current installation expires.                                                                                                           |
| ::public static ApplicationObjectTreeWindow getApplicationObjectTreeWindow()                                                                                                                                 |                                                                                                                                                                                         |
| ::public static int getCurrentModelId()                                                                                                                                                                      |                                                                                                                                                                                         |
| ::public static int getNumberOfDecimals(Real number)                                                                                                                                                         | Retrieves the number of decimal places in the specified number.                                                                                                                         |
| ::public static PropertiesWindow getPropertiesWindow()                                                                                                                                                       |                                                                                                                                                                                         |
| ::public static int getSystemGeneratedModelId(UtilEntryLevel layer)                                                                                                                                          |                                                                                                                                                                                         |
| ::public static str licenseName()                                                                                                                                                                            | Retrieves the name of the current Microsoft Dynamics AX license.                                                                                                                        |
| ::public static str productName()                                                                                                                                                                            | Retrieves the name of the product.                                                                                                                                                      |
| ::public static str productRegisteredName()                                                                                                                                                                  |                                                                                                                                                                                         |
| ::public static str releaseVersion()                                                                                                                                                                         | Retrieves the version number of the current Microsoft Dynamics AX executable; for example: 3.0, or 4.0.                                                                                 |
| ::public static str releaseYear()                                                                                                                                                                            |                                                                                                                                                                                         |
| ::public static str serialNo()                                                                                                                                                                               | Retrieves the serial number of the current Microsoft Dynamics AX license.                                                                                                               |
| public void new()                                                                                                                                                                                            | Initializes a new xInfo object.                                                                                                                                                         |
| public void workspaceWindowDestroyed(int hWnd)                                                                                                                                                               | Executes when a workspace is closed.                                                                                                                                                    |
| public void writeCustomStatlineItem(str text)                                                                                                                                                                | Writes a line of text to the status bar.                                                                                                                                                |
| public void reloadRunningMode()                                                                                                                                                                              |                                                                                                                                                                                         |
| public void setWindowOrder(int window, \[int afterWindow\])                                                                                                                                                  | Sets the order in which windows should be displayed.                                                                                                                                    |
| public void shutDown(boolean force)                                                                                                                                                                          | Shuts down the client.                                                                                                                                                                  |
| public void xref(str path, xRef x)                                                                                                                                                                           | Executes when the cross-reference system is used.                                                                                                                                       |
| public void updateCurrentCompany()                                                                                                                                                                           |                                                                                                                                                                                         |
| public void redrawAllWindows()                                                                                                                                                                               | Redraws all windows.                                                                                                                                                                    |
| public void formNotify(xFormRun form, FormNotify notification, \[FormNotifyEventArgs formNotifyEventArgs\])                                                                                                  | Executes based on a particular type of change to a specific form, allowing custom code to run.                                                                                          |
| public void mayReloadMenu(boolean value)                                                                                                                                                                     | Prevents the UI from refreshing.                                                                                                                                                        |
| public void startLengthyOperation()                                                                                                                                                                          | Sets the mouse cursor to idle.                                                                                                                                                          |
| public void breakpointNotify(BreakpointNotify notification)                                                                                                                                                  | Implements a notification system when a breakpoint is changed.                                                                                                                          |
| public void initializeInfolog(int window)                                                                                                                                                                    |                                                                                                                                                                                         |
| public void startup(str startupCmd)                                                                                                                                                                          | Executes when the client starts.                                                                                                                                                        |
| public void endImport(int id, int elements)                                                                                                                                                                  | Completes an import process.                                                                                                                                                            |
| public void yield()                                                                                                                                                                                          |                                                                                                                                                                                         |
| public void viewAlertInbox(\[int selectedTab\])                                                                                                                                                              | Launches the View alerts form.                                                                                                                                                          |
| public void reportSendMailServer(PrintJobSettings settings)                                                                                                                                                  |                                                                                                                                                                                         |
| public void endLengthyOperation(\[boolean endAll\])                                                                                                                                                          | Sets the mouse cursor back to normal after a call to startLengthyOperation.                                                                                                             |
| public void setNumUnreadAlerts(\[int n\])                                                                                                                                                                    | Refreshes the status bar text when the number of unread Alert e-mails changes.                                                                                                          |
| public void truncate(str prefix)                                                                                                                                                                             | Removes the items with the specified prefix from the Infolog.                                                                                                                           |
| public void formNoteButton(boolean enable, boolean value)                                                                                                                                                    | Controls the Document handling button on the toolbar.                                                                                                                                   |
| public void viewCreateRuleDialog(xFormRun caller)                                                                                                                                                            | Launches the Create alert rule form.                                                                                                                                                    |
| public void view(\[container container\])                                                                                                                                                                    |                                                                                                                                                                                         |
| public void clear(\[int linesLeft\])                                                                                                                                                                         | Deletes lines from the Infolog buffer.                                                                                                                                                  |
| public void workspaceWindowCreated(int hWnd)                                                                                                                                                                 | Executes when a new workspace is created.                                                                                                                                               |
| ::public static void setCurrentModelId(int currentModelId)                                                                                                                                                   |                                                                                                                                                                                         |
| public void activateMenubarTask(int command)                                                                                                                                                                 |                                                                                                                                                                                         |
| public void finalize()                                                                                                                                                                                       |                                                                                                                                                                                         |
| public void insertXReferences()                                                                                                                                                                              |                                                                                                                                                                                         |
| public void activateButton(int command)                                                                                                                                                                      |                                                                                                                                                                                         |
| public void activateWindow(int window)                                                                                                                                                                       | Sets the focus on a form or Window.                                                                                                                                                     |
| public void reportSendMail(PrintJobSettings settings)                                                                                                                                                        | Generates the settings for sending a report by email.                                                                                                                                   |

### Method removeMessage

    public int removeMessage(Int64 messageId)

#### Parameters

messageId  

#### Return Value

### Method insertMessage

    public Int64 insertMessage(MessageSeverity type, str message)

#### Parameters

type  

<!-- -->

message  

#### Return Value

### Method add

Adds a string to the Infolog buffer.

    public Exception add(Exception exceptionType, str string, [str helpURL], [Object obj], [boolean buildprefix])

#### Parameters

exceptionType  
Optional parameter, that enables you to turn off the generation of prefix information that is used to provide context to Infolog messages.

<!-- -->

string  
Optional parameter, that enables you to turn off the generation of prefix information that is used to provide context to Infolog messages.

<!-- -->

helpURL  
Optional parameter, that enables you to turn off the generation of prefix information that is used to provide context to Infolog messages.

<!-- -->

obj  
Optional parameter, that enables you to turn off the generation of prefix information that is used to provide context to Infolog messages.

<!-- -->

buildprefix  
Optional parameter, that enables you to turn off the generation of prefix information that is used to provide context to Infolog messages.

#### Return Value

An Exception system enumeration value. For more information, see Exception Handling with try and catch Keywords.

#### Remarks

An example value for the helpURL parameter is 'KernDoc:\\\\\\\\Functions\\\\substr'. This method should not be used directly. Instead, use the infolog.info, infolog.warning, infolog.error, or infolog.checkFailed method instead. For more information about the exceptionType parameter, see Exception Handling with try and catch Keywords.

### Method addException

    public Exception addException(str string, str stackTrace)

#### Parameters

string  

<!-- -->

stackTrace  

#### Return Value

### Method breakpoint

Gets or sets information about breakpoints.

    public container breakpoint([container breakpoint])

#### Parameters

breakpoint  
A container that holds information about the current breakpoints.

#### Return Value

A container holding information about the current breakpoints.

#### Remarks

The container that holds information about breakpoints is of the format:

-   Item 1: Version number
-   Items 2 - 4, 5-7, … n - n+2: Information about each breakpoint, consisting of:
    -   the AOT path
    -   the line number on which the breakpoint is set
    -   whether the breakpoint is enabled or disabled

In the application, this method is used by the Breakpoints form. When the form is opened it calls the getBreakpoints method on the form. This calls the xInfo.breakpoint method, and uses a container with the breakpoint information as a parameter. When a breakpoint is disabled, enabled, or deleted from the form, the setBreakpoints method is called. This updates the information about the breakpoints and returns this as a container using the xInfo.breakpoint method without using the breakpoint parameter. The container is used to update the breakpoint information in the Code Editor window.

### Method canShowCreateRuleMenuItem

Determines whether the menu item for the Create alert rule form should be displayed for a form.

    public boolean canShowCreateRuleMenuItem(xFormRun caller)

#### Parameters

caller  
The current form: the form from which the Create alert rule menu item can be displayed.

#### Return Value

true if the current form supports the creation of alerts; otherwise false.

### Method canShutdown

Tests whether the system can be shut down. Do not use this method. Use the version that is overridden on the Info class instead.

    public boolean canShutdown(boolean silent)

#### Parameters

silent  
A Boolean that determines whether users are asked if they want to exit the system.

#### Return Value

true of the system can be shut down; otherwise false.

### Method canViewAlertInbox

Determines whether the current user has permission to view the View alerts form.

    public boolean canViewAlertInbox()

#### Return Value

true if the user has permission to view the form; otherwise, false.

#### Remarks

Call this method before calling xInfo.viewAlertInbox.

### Method compilerOutput

Gets or sets the compiler output object. The compiler output object is the Compiler output window by default.

    public xCompilerOutput compilerOutput([Object compilerOut])

#### Parameters

compilerOut  
A compiler output object; optional. Optional parameter.

#### Return Value

An xCompilerOutput object.

#### Remarks

The default value of the compilerOut parameter is the Compiler output window, but it can also be the Message window.

### Method copy

Copies lines from the Infolog buffer.

    public container copy(int from, int to)

#### Parameters

from  
The last line to copy.

<!-- -->

to  
The last line to copy.

#### Return Value

Container that contains the Infolog lines between from and to.

#### Examples

The following example uses the copy method to copy the content of the Infolog into a log.

    boolean validateRecord() 
    { 
        boolean     ok = true; 
        ok = intrastat.validateRecord(); 
        if (ok) 
            intrastat.log = ''; 
        else 
        { 
            intrastat.log = Info::infoCon2Str( 
                infolog.copy(infoLogCounter+1,infolog.num())); 
            infoLogCounter = infolog.num(); 
            errorFound = true; 
        } 
        intrastat.update(); 
        return ok; 
    }

### Method createDevelopmentWorkspaceWindow

    public int createDevelopmentWorkspaceWindow()

#### Return Value

### Method createWorkspaceWindow

Opens a new workspace window. For example, this enables you to open different sets of application objects in different windows, or to work with two different sets of company accounts.

    public int createWorkspaceWindow()

#### Return Value

Returns a handle to the new window.

### Method currentAOLayer

Retrieves the current layer you are running in such as SYS, or USR.

    public UtilEntryLevel currentAOLayer()

#### Return Value

A UtilEntryLevel system enumeration value that indicates the current layer you are working in.

#### Remarks

For more information, see Layers.

### Method cut

Cuts lines from the Infolog buffer.

    public container cut(int from, int to)

#### Parameters

from  
The last line to cut.

<!-- -->

to  
The last line to cut.

#### Return Value

A container that contains the Infolog lines between the lines specified by the from and to parameters.

#### Examples

The following example cuts the lines in the Infolog from the line specified by the fromLine value, up to the last line.

    private void cutInfolog(int fromLine) 
    { 
        infolog.cut(fromLine+1, Global::infologLine()); 
    }

### Method documentationLanguage

Gets or sets the language that is used for the Microsoft Dynamics AX documentation.

    public str documentationLanguage([str languageCode])

#### Parameters

languageCode  
The ID of the language you want to set; optional.

#### Return Value

The ID of the language that is currently used for the documentation.

#### Remarks

Use the xInfo.language Method to set the language for the GUI. To set the documentation language for a particular session, use the xSession.documentationLanguage Method. An example value for the languageCode parameter is "en-us", which will set the language to US English.

### Method export

    public container export()

#### Return Value

### Method findNode

Retrieves the specified a tree node.

    public TreeNode findNode(str nodePath)

#### Parameters

nodePath  
A string that contains the path to the node.

#### Return Value

Returns the tree node that is specified by the nodePath parameter.

#### Remarks

This method is obsolete. Use the TreeNode::findNode Method instead.

### Method getDocNode

Retrieves the specified documentation nodes from the AOT.

    public TreeNode getDocNode(UtilFileType helpType, int UtilType, str Name, [UtilElementId ParentId], [int Type], [UtilEntryLevel UtilLevel], [boolean ForceLevel], [int Mode], [boolean OldUtil])

#### Parameters

helpType  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

UtilType  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

Name  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

ParentId  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

Type  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

UtilLevel  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

ForceLevel  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

Mode  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

<!-- -->

OldUtil  
A Boolean value that indicates whether to retrieve the node from the old AOT in the oldAOT folder.

#### Return Value

A documentation node from the AOT.

#### Remarks

The possible values for the helpType parameter are values of the UtilFileType system enumeration:

-   KernelHelp: the System Documentation node
-   ApplicationHelp: the Application Documentation node
-   ApplicationCodeDocumentation: the Application Developer Documentation node.

An example value of the utilType parameter is the Functions node within the System Documentation node. The default value of the ForceLevel parameter is false. If it is set to false, and there is no content in the layer specified, the node will be taken from the next layer below this that does have content. If it is set to true, and there is no content in the layer, the method will return nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Method getImportedNode

Creates an instance of a tree node from an XPO file but does not import it into the AOT. For example, this allows you to compare it with another version of the same tree node.

    public TreeNode getImportedNode(int id, int utilfiletype, UtilElementType utiltype, str name, int fileposition, int Flag)

#### Parameters

id  

<!-- -->

utilfiletype  

<!-- -->

utiltype  

<!-- -->

name  

<!-- -->

fileposition  

<!-- -->

Flag  

#### Return Value

A tree node.

#### Remarks

The possible values for the utilfiletype parameter are those that are available in the UtilFileType Enumeration. The possible values for the utiltype parameter are those that are available in the UtilElementType Enumeration. For a list of the possible values for the Flag parameter, see the AOTExport macro. The values are listed under the System import flags comment.

#### Examples

The following example uses the getImportedNode method to create a virtual tree node.

    public TreeNode getVirtualTreenode( 
        Filename _filename = this.fileName()) 
    { 
        #AOT 
        #AotExport 
        TmpAotImport      tmpImportAot; 
        SysImportElements sysImportElements = new SysImportElements(); 
        TreeNode treeNodeImport  = null; 
        int      exportId; 
        int      flag = (#impGetCompareNode + #impKeepIds); 
        str      name; 
        ; 
        // Set the filename. 
        sysImportElements.newFile(_filename); 
        // Get info from the file 
        tmpImportAot = sysImportElements.getTmpImportAot(); 
        // Create an import context 
        exportId     = infolog.startImport(_filename, flag); 
        // Get the right name 
        // for doc nodes it is the path excl. the first part 
        switch (tmpImportAot.UtilFileType) 
        { 
            case UtilFileType::Application: 
                name = tmpImportAot.TreeNodeName; 
                break; 
            case UtilFileType::ApplicationCodeDocumentation: 
                name = strdel(tmpImportAot.TreeNodePath, 1, strlen(#ApplicationDeveloperDocPath)); 
                break; 
            case UtilFileType::ApplicationHelp: 
                name = strdel(tmpImportAot.TreeNodePath, 1, strlen(#ApplicationDocPath)); 
                break; 
            case UtilFileType::KernelHelp: 
                name = strdel(tmpImportAot.TreeNodePath, 1, strlen(#SystemDocPath)); 
                break; 
            default: 
                name = tmpImportAot.TreeNodeName; 
                break; 
        } 
        // Import the node in memory 
        treeNodeImport  = infolog.getImportedNode( 
            exportId, 
            tmpImportAot.UtilFileType, 
            tmpImportAot.UtilElementType, 
            name, 
            tmpImportAot.FilePos, 
            flag); 
        // Close the import context 
        infolog.endImport(exportId, 1); 
        return treeNodeImport; 
    }

### Method getNode

Retrieves a tree node that corresponds to a node in the AOT.

    public TreeNode getNode(UtilElementType UtilType, str Name, [UtilElementId ParentId], [int Type], [UtilEntryLevel Utillevel], [boolean Forcelevel], [int Mode], [boolean OldUtil])

#### Parameters

UtilType  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

<!-- -->

Name  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

<!-- -->

ParentId  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

<!-- -->

Type  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

<!-- -->

Utillevel  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

<!-- -->

Forcelevel  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

<!-- -->

Mode  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

<!-- -->

OldUtil  
A Boolean value that indicates whether to take the node from the old AOT in the old AOT folder.

#### Return Value

The tree node that is specified by the UtilType and Name parameters.

#### Remarks

The node returned is not linked into the AOT, so you cannot perform operations on the node. To perform operations on a node, use the findNode or rootNode method instead. The default value for the UtilLevel parameter is the current layer. The possible values for the Mode parameter are:

-   0x001: Load for run
-   0x002: Load for edit

The default value of the ForceLevel parameter is false. If it is set to false, and there is no content in the layer specified, the node will be taken from the next layer below this that does have content. If it is set to true, and there is no content in the layer, the method will return nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Method getNodeResid

Retrieves the resource ID for the icon that is used to display nodes of the specified type.

    public int getNodeResid(UtilElementType nodeType)

#### Parameters

nodeType  
A UtilElementType system enumeration value that indicates the type of node to retrieve.

#### Return Value

An integer that represents the Resource ID for the node.

### Method getTaskInfo

    public Struct getTaskInfo(int taskNumber)

#### Parameters

taskNumber  

#### Return Value

### Method getUserSetup

Retrieves a UserSetup object that is used to set user parameters.

    public UserSetup getUserSetup()

#### Return Value

A UserSetup object.

#### Remarks

The UserSetup system class provides an interface for setting user parameters.

### Method getWorkspaceList

    public container getWorkspaceList()

#### Return Value

### Method hWnd

Retrieves a handle to the Microsoft Dynamics AXNavigation Pane window.

    public int hWnd([int workspaceNum])

#### Parameters

workspaceNum  
The handle to the workspace from which to get the Navigation Pane handle.

#### Return Value

An integer that represents the handle to the Microsoft Dynamics AXNavigation Pane window.

### Method import

    public boolean import(container infologContainer, [boolean clearExistingInfolog])

#### Parameters

infologContainer  

<!-- -->

clearExistingInfolog  

#### Return Value

### Method importElement

Specifies the object to be imported.

    public int importElement(int id, int utilfiletype, UtilElementType utiltype, str name, int fileposition, int Flag)

#### Parameters

id  

<!-- -->

utilfiletype  

<!-- -->

utiltype  

<!-- -->

name  

<!-- -->

fileposition  

<!-- -->

Flag  

#### Return Value

This method is obsolete. Use the SysImportElements class instead.

### Method importString

Imports an object from a file.

    public int importString(str source, UtilElementType kind, str name)

#### Parameters

source  
The name of the object.

<!-- -->

kind  
The name of the object.

<!-- -->

name  
The name of the object.

#### Return Value

### Method instance

Retrieves a handle to the current instance of the application.

    public int instance()

#### Return Value

The handle of the current instance of the application.

### Method isoCurrencyCode

Gets or sets the currency code.

    public str isoCurrencyCode([str code])

#### Parameters

code  
A string that contains the ISO currency code to set.

#### Return Value

A string that contains the currency code for the current application.

### Method IsVisible

Determines whether the client window is not minimized.

    public boolean IsVisible()

#### Return Value

false if the client window is minimized; otherwise, true.

### Method language

Gets or sets the language for the GUI.

    public str language([str languageCode])

#### Parameters

languageCode  
A string that contains the language code to set.

#### Return Value

A string that contains the current language code.

#### Remarks

To set the language for the documentation, use the xInfo.documentationLanguage Method. To set the GUI language for a particular session, use the xSession.interfaceLanguage Method.

#### Examples

The following example prints the code for the language that is currently set. For example, if the interface was in US English, it would print "en-us".

    { 
        print infolog.language(); 
        pause; 
    }

### Method level

Retrieves the exception level of a line in the Infolog buffer.

    public Exception level(int line)

#### Parameters

line  
The line in the Infolog for which to retrieve the exception level.

#### Return Value

A Exception system enumeration value.

#### Remarks

For more information, see Exception Handling with try and catch Keywords.

### Method line

Retrieves the number of lines in the Infolog buffer.

    public int line()

#### Return Value

An integer that represents the number of lines in the Infolog buffer.

#### Remarks

If you are running code on the server, use the xGlobal::infologLine method instead. It eliminates calls between the server and client. To get the number of exceptions of a specific type in the Infolog, use the xInfo.num Method.

### Method messageWin

Enables you to send output from the Infolog to the Message window.

    public MessageWin messageWin()

#### Return Value

A MessageWin object.

#### Remarks

You may want to send output to the Message window if you have a lengthy process. If you send output to the Infolog, nothing will be displayed until the process is completed. If you send output to the Message window, content is displayed as the operation proceeds.

### Method nationalCurrencyFactor

    public Real nationalCurrencyFactor([Real factor])

#### Parameters

factor  

#### Return Value

### Method nationalCurrencyPostfix

    public str nationalCurrencyPostfix([str string])

#### Parameters

string  

#### Return Value

### Method nationalCurrencyPrefix

    public str nationalCurrencyPrefix([str string])

#### Parameters

string  

#### Return Value

### Method navPane

Retrieves an xNavPane object, the primary navigation control class.

    public xNavPane navPane()

#### Return Value

An instance of the xNavPane class.

#### Remarks

You can only have one instance of this class per workspace.

### Method num

Retrieves the number of exceptions of the specified type in the Infolog buffer.

    public int num([Exception exceptionType])

#### Parameters

exceptionType  
A Exception system enumeration value that indicates the exception type to count; optional.

#### Return Value

An integer that represents the number of exceptions of the type specified by the exceptionType parameter, or the total number of lines in the Infolog if no parameter is specified.

#### Remarks

For more information, see Exception Handling with try and catch Keywords.

#### Examples

The following example returns the number of warnings in the Infolog.

    { 
        print infolog.num(Exception::Warning); 
        pause; 
    }

### Method prevInstance

Retrieves a handle to the previous instance of the application.

    public int prevInstance()

#### Return Value

The handle of the previous instance of the application.

#### Remarks

This method should not be used.

### Method processId

Retrieves the ID for the Microsoft Dynamics AX process.

    public int processId()

#### Return Value

The ID for the Microsoft Dynamics AX process.

### Method projectRootNode

Returns the X++ Projects node.

    public TreeNode projectRootNode()

#### Return Value

The tree node that contains the X++ projects.

#### Examples

The following example prints out the names of all the projects in the Shared projects folder.

    void ProjectNames() 
    { 
        Treenode treenode; 
        TreenodeIterator it; 
        treenode = infolog.projectRootNode(); 
        treenode = treenode.AOTfindChild("Shared"); 
        it = treenode.AOTiterator(); 
        while (treenode) 
        { 
           print treenode.treeNodeName(); 
           treenode = it.next(); 
        } 
        pause; 
    }

### Method rootNode

Retrieves the root of the application object tree.

    public TreeNode rootNode()

#### Return Value

The root of the application object tree.

#### Examples

The following example prints out all the names of the methods in the AddressSelectForm class. The rootnode method is used to set the treenode object to the AOT root before selecting a child node.

    { 
        Treenode treenode; 
        TreenodeIterator it; 
        treenode = infolog.rootNode(); 
        treenode = treenode.AOTfindChild("Classes"); 
        treenode = treenode.AOTfindChild("AddressSelectForm"); 
        it = treenode.AOTiterator(); 
        while (treenode) 
        { 
           print treenode.treeNodeName(); 
           treenode = it.next(); 
        } 
        pause; 
    }

### Method startImport

Creates an import context.

    public int startImport(str file, int flag, [str labelSubstitutes])

#### Parameters

file  

<!-- -->

flag  

<!-- -->

labelSubstitutes  

#### Return Value

#### Remarks

This method is obsolete. Use the SysImportElements class instead.

### Method text

Retrieves a line of text from the Infolog.

    public str text([int line])

#### Parameters

line  
The line in the Infolog with the text to retrieve.

#### Return Value

A string that contains the text from the Infolog.

### Method userNode

    public TreeNode userNode()

#### Return Value

### Method webSession

    public AnyType webSession([AnyType value])

#### Parameters

value  

#### Return Value

### Method activeXControls

Retrieves a list of the ActiveX controls that are in Microsoft Dynamics AX.

    public static container activeXControls()

#### Return Value

A nested container that holds information about each of the ActiveX controls.

#### Remarks

The returned container contains four containers. The first inner container contains the names of all the controls. The second inner container contains the ID for each control, which is a GUID. The third inner container contains the security setting for each control. The fourth inner container contains a description of each control.

#### Examples

The following example prints a description of each of the ActiveX controls in Microsoft Dynamics AX.

    static void activeXcontents(Args _args) 
    { 
        int       i; 
        str       strClsName, strTypeLibHelp, strClsId, strSafeForBits; 
        container c; 
        container clsName, clsId, safeForBits, typeLibHelp; 
        c = xinfo::activeXControls(); 
        clsName = conpeek(c, 1); 
        clsId = conpeek(c, 2); 
        safeForBits = conpeek(c, 3); 
        typeLibHelp = conpeek(c, 4); 
        for (i=1; i<conlen(clsName); i++) 
        { 
            strClsName = conpeek(clsName, i); 
            strClsId = conpeek(clsId, i); 
            strSafeForBits = conpeek(safeForBits, i); 
            strTypeLibHelp = conpeek(typeLibHelp, i); 
            print strClsName, " ", strClsId, " ", strSafeForBits, 
                " ", strTypeLibHelp; 
        } 
        pause; 
    }

### Method AOTLogDirectory

Gets the path to the log directory for the current installation.

    public static str AOTLogDirectory()

#### Return Value

A string that contains the path to the log directory for the current installation.

#### Remarks

If you turn on the AOT Log option, information will be stored in the log directory each time you compile. To turn on this option:

1.  Open a developer workspace.
2.  Select Tools &gt; Options &gt; Development &gt; Compiler.
3.  Select the AOT log check box.

### Method automationObjects

Retrieves the list of COM objects that are available in Microsoft Dynamics AX.

    public static container automationObjects()

#### Return Value

A nested container that holds a description of each COM object.

#### Examples

The following example unpacks the nested container that is returned from automationObjects to get a list of COM objects.

    void getAutomationObjects() 
    { 
        int idx; 
        FormListItem listItem; 
        int itemPos; 
        container clsGUID,clsDesc,clsVersion,clsPath; 
        [clsGUID,clsDesc,clsVersion,clsPath] = xInfo::automationObjects(); 
        for (idx = 1; idx < conlen(clsGUID); idx++) 
        { 
            itemPos = formListControl.add(conpeek(clsDesc,idx)); 
            listItem = formListControl.getItem(itemPos); 
            listItem.data(conpeek(clsPath,idx)); 
            formListControl.setItem(listItem); 
        } 
    }

### Method buildNo

Retrieves the kernel build number of the current Microsoft Dynamics AX executable.

    public static str buildNo()

#### Return Value

A string that contains the kernel build number.

#### Examples

The following example uses this method to return the kernel build number as part of a string that contains Microsoft Dynamics AX version information.

    static client str axaptaReleaseID() 
    { 
        #define.versionPrefix('v') 
        #define.versionNumber('#') 
        #define.versionPartition('/') 
        return    #versionprefix+xInfo::releaseVersion()+ 
                  #versionNumber+xInfo::buildNo()+ 
                  #versionPartition+ApplicationVersion::buildNo(); 
    }

### Method compilationDate

Retrieves the date on which the current version of Microsoft Dynamics AX was last compiled.

    public static str compilationDate()

#### Return Value

A string that contains the date on which Microsoft Dynamics AX was last compiled.

#### Examples

The following example returns system information, including the date on which the application was last compiled:

    str environment() 
    { 
        return xInfo::buildNo() + ' - '  
            + xInfo::compilationDate() + ' - '  
            + xInfo::dbName() + ' - '  
            + xInfo::osName() + ' - '  
            + xInfo::productName() + ' - '  
            + xInfo::releaseVersion(); 
    }

### Method compilationTime

Retrieves the time at which the current version of Microsoft Dynamics AX was last compiled.

    public static str compilationTime()

#### Return Value

A string that contains the time at which Microsoft Dynamics AX was last compiled.

### Method componentName

Retrieves the path to the component.

    public static str componentName()

#### Return Value

A string that contains the path to the executable.

#### Remarks

If this method is run on the client, it returns the path to the .exe file for the Microsoft Dynamics AX client. If it is run on the server, it returns the path to the .exe file for the AOS.

### Method configuration

Retrieves the current client configuration.

    public static str configuration()

#### Return Value

A string that represents the current client configuration.

#### Remarks

This is the configuration that is selected in the Configuration box in the Client Configuration Utility program. An example string that could be returned is "Original (installed configuration)".

### Method currentWorkspaceNum

Retrieves the application window ID of the current workspace.

    public static int currentWorkspaceNum()

#### Return Value

The application window ID of the current workspace.

#### Remarks

The createWorkspaceWindow method allows you to open additional workspaces in the application.

### Method directory

Retrieves the path to the directory where the Microsoft Dynamics AX client has been installed.

    public static str directory(DirectoryType type)

#### Parameters

type  
A DirectoryType enumeration value that indicates one of the subfolders of the client installation.

#### Return Value

A string that contains the path to the directory that is specified by the DirectoryType parameter.

#### Examples

The following example prints the path to the Bin directory for the current client installation.

    { 
        print xInfo::directory(DirectoryType::Bin); 
        pause; 
    }

### Method expireDate

Retrieves the date on which the license for the current installation expires.

    public static Date expireDate()

#### Return Value

A date that represents the date on which the license expires.

### Method getApplicationObjectTreeWindow

    public static ApplicationObjectTreeWindow getApplicationObjectTreeWindow()

#### Return Value

### Method getCurrentModelId

    public static int getCurrentModelId()

#### Return Value

### Method getNumberOfDecimals

Retrieves the number of decimal places in the specified number.

    public static int getNumberOfDecimals(Real number)

#### Parameters

number  
A real number.

#### Return Value

The number of decimal places in the number parameter.

### Method getPropertiesWindow

    public static PropertiesWindow getPropertiesWindow()

#### Return Value

### Method getSystemGeneratedModelId

    public static int getSystemGeneratedModelId(UtilEntryLevel layer)

#### Parameters

layer  

#### Return Value

### Method licenseName

Retrieves the name of the current Microsoft Dynamics AX license.

    public static str licenseName()

#### Return Value

A string that contains the name of the license.

#### Remarks

The xInfo::expireDate Method returns the date on which the license expires. The xInfo::serialNo Method returns the serial number of the license.

### Method productName

Retrieves the name of the product.

    public static str productName()

#### Return Value

A string that contains the name of the product.

#### Examples

The following example returns system information, including the name of the product.

    str environment() 
    { 
        return xInfo::buildNo() + ' - '  
            + xInfo::compilationDate() + ' - '  
            + xInfo::dbName() + ' - '  
            + xInfo::osName() + ' - '  
            + xInfo::productName() + ' - '  
            + xInfo::releaseVersion(); 
    }

### Method productRegisteredName

    public static str productRegisteredName()

#### Return Value

### Method releaseVersion

Retrieves the version number of the current Microsoft Dynamics AX executable; for example: 3.0, or 4.0.

    public static str releaseVersion()

#### Return Value

A string containing the Microsoft Dynamics AX version number.

#### Remarks

Possible version numbers include 3.0 and 4.0.

#### Examples

The following example uses this return the version number as part of a string that contains Microsoft Dynamics AX version information.

    static client str axaptaReleaseID() 
    { 
        #define.versionPrefix('v') 
        #define.versionNumber('#') 
        #define.versionPartition('/') 
        return    #versionprefix+xInfo::releaseVersion()+ 
                  #versionNumber+xInfo::buildNo()+ 
                  #versionPartition+ApplicationVersion::buildNo(); 
    }

### Method releaseYear

    public static str releaseYear()

#### Return Value

### Method serialNo

Retrieves the serial number of the current Microsoft Dynamics AX license.

    public static str serialNo()

#### Return Value

A string that contains the serial number of the Microsoft Dynamics AX license.

### Method new

Initializes a new xInfo object.

    public void new()

#### Remarks

Note: Do not use this method. You should use the global instance of the xInfo class, infolog, instead. For more information, see the xInfo class.

### Method workspaceWindowDestroyed

Executes when a workspace is closed.

    public void workspaceWindowDestroyed(int hWnd)

#### Parameters

hWnd  
The handle of the workspace.

#### Remarks

This method is called when a new workspace is closed. It allows you to perform an action when this occurs.

### Method writeCustomStatlineItem

Writes a line of text to the status bar.

    public void writeCustomStatlineItem(str text)

#### Parameters

text  
The line of text to put on the status bar.

### Method reloadRunningMode

    public void reloadRunningMode()

### Method setWindowOrder

Sets the order in which windows should be displayed.

    public void setWindowOrder(int window, [int afterWindow])

#### Parameters

window  
The handle to the window to place after the window specified by the window parameter; optional.

<!-- -->

afterWindow  
The handle to the window to place after the window specified by the window parameter; optional.

#### Examples

The following example sets focus on a window and brings it to the front.

    void setFocus() 
    { 
        infolog.activateWindow(element.hWnd()); 
        infolog.setWindowOrder(element.hWnd()); 
    }

### Method shutDown

Shuts down the client.

    public void shutDown(boolean force)

#### Parameters

force  
A Boolean value that indicates whether the user is given the option to prevent the shutdown.

### Method xref

Executes when the cross-reference system is used.

    public void xref(str path, xRef x)

#### Parameters

path  

<!-- -->

x  

#### Remarks

Do not use this method.

### Method updateCurrentCompany

    public void updateCurrentCompany()

### Method redrawAllWindows

Redraws all windows.

    public void redrawAllWindows()

#### Remarks

This method can be used to update the display during a long process.

### Method formNotify

Executes based on a particular type of change to a specific form, allowing custom code to run.

    public void formNotify(xFormRun form, FormNotify notification, [FormNotifyEventArgs formNotifyEventArgs])

#### Parameters

form  

<!-- -->

notification  

<!-- -->

formNotifyEventArgs  

#### Remarks

Possible values for the notification parameter are:

-   Activate
-   DeActivate
-   Open
-   Close
-   RecordChange
-   NoteClicked

For an example of the usage of this method, see the formNotify method of the Info class, where this method has been overridden.

### Method mayReloadMenu

Prevents the UI from refreshing.

    public void mayReloadMenu(boolean value)

#### Parameters

value  
A Boolean value that indicates whether to prevent the UI from refreshing.

#### Remarks

Set the value to false to prevent the UI from refreshing when a process is executing, and then set it to true after the process has finished. The mayReloadMenu method can be useful to prevent the UI from flickering, for example when many nodes in the AOT are being read.

### Method startLengthyOperation

Sets the mouse cursor to idle.

    public void startLengthyOperation()

#### Remarks

Use at the start of a lengthy operation to indicate that a process is in progress. When the operation has finished, the system automatically calls the endLengthyOperation method.

### Method breakpointNotify

Implements a notification system when a breakpoint is changed.

    public void breakpointNotify(BreakpointNotify notification)

#### Parameters

notification  
A BreakpointNotify system enumeration value that specifies the type of change that has occurred to the breakpoints.

#### Remarks

In the application, this method is used to update the Breakpoints form when a change is made to a breakpoint in the Code Editor window. The following values of the BreakpointNotify enumeration type are valid for the notification parameter:

-   BreakpointForm: Notifies the client that the breakpoint list should be reloaded.
-   BreakpointChange: Notifies the client and server that the status of a breakpoint has changed (enabled, disabled, or deleted).

### Method initializeInfolog

    public void initializeInfolog(int window)

#### Parameters

window  

### Method startup

Executes when the client starts.

    public void startup(str startupCmd)

#### Parameters

startupCmd  

#### Remarks

Do not use this method. Use one following methods instead. Use the Info.startupPost Method to pass startup commands to the client. Use the Application.startupPost Method to pass startup commands to the server. Do not use the Application.startup or Info.startup methods. This might affect code in a new version of Microsoft Dynamics AX, which could prevent the client or server from starting.

### Method endImport

Completes an import process.

    public void endImport(int id, int elements)

#### Parameters

id  

<!-- -->

elements  

#### Remarks

This method is obsolete. Use the SysImportElements class instead.

### Method yield

    public void yield()

### Method viewAlertInbox

Launches the View alerts form.

    public void viewAlertInbox([int selectedTab])

#### Parameters

selectedTab  
Determines which tab the View alerts form opens on; optional.

#### Remarks

The default value for the selectedTab parameter is Overview, the first tab. Call the xInfo.canViewAlertInbox Method to check whether the user has permission to view this form.

### Method reportSendMailServer

    public void reportSendMailServer(PrintJobSettings settings)

#### Parameters

settings  

### Method endLengthyOperation

Sets the mouse cursor back to normal after a call to startLengthyOperation.

    public void endLengthyOperation([boolean endAll])

#### Parameters

endAll  
Reserved.

#### Remarks

It is best practice not to call this method. It will be called automatically by the system when the operation has ended. If you call this method explicitly and there are other processes, or looping code, that use the method, it could lead to the mouse pointer flickering.

### Method setNumUnreadAlerts

Refreshes the status bar text when the number of unread Alert e-mails changes.

    public void setNumUnreadAlerts([int n])

#### Parameters

n  
Allows you to set the number of unread e-mails to a specific number.

### Method truncate

Removes the items with the specified prefix from the Infolog.

    public void truncate(str prefix)

#### Parameters

prefix  
The prefix for the items that you want to remove from the Infolog.

### Method formNoteButton

Controls the Document handling button on the toolbar.

    public void formNoteButton(boolean enable, boolean value)

#### Parameters

enable  
A Boolean data type that indicates the appearance of the icon.

<!-- -->

value  
A Boolean data type that indicates the appearance of the icon.

#### Examples

The following example shows how to disable the Document handling button.

    void disableNoteButton() 
        { 
            infolog.formNoteButton(false, false); 
        }

### Method viewCreateRuleDialog

Launches the Create alert rule form.

    public void viewCreateRuleDialog(xFormRun caller)

#### Parameters

caller  
The current form.

#### Remarks

The Create alert rule form will be launched from the current form, as specified by the caller parameter.

### Method view

    public void view([container container])

#### Parameters

container  

### Method clear

Deletes lines from the Infolog buffer.

    public void clear([int linesLeft])

#### Parameters

linesLeft  
Number of lines to leave in the buffer; optional.

#### Remarks

Do not call this with method with the default value of zero unless another process has not put information into the Infolog.

#### Examples

Use this pattern to clear the Infolog cache:

    int line = Global::infologLine();
    try 
    { 
        // 
    } 
    catch 
    { 
        infolog.clear(line); 
    }

### Method workspaceWindowCreated

Executes when a new workspace is created.

    public void workspaceWindowCreated(int hWnd)

#### Parameters

hWnd  
The handle of the new workspace.

#### Remarks

This method is called when a new workspace is created. It allows you to perform an action when this occurs.

### Method setCurrentModelId

    public static void setCurrentModelId(int currentModelId)

#### Parameters

currentModelId  

### Method activateMenubarTask

    public void activateMenubarTask(int command)

#### Parameters

command  

### Method finalize

    public void finalize()

### Method insertXReferences

    public void insertXReferences()

### Method activateButton

    public void activateButton(int command)

#### Parameters

command  

### Method activateWindow

Sets the focus on a form or Window.

    public void activateWindow(int window)

#### Parameters

window  
The handle to the form or window that you want to bring into focus.

### Method reportSendMail

Generates the settings for sending a report by email.

    public void reportSendMail(PrintJobSettings settings)

#### Parameters

settings  
The email settings for the user.

## Class xLanguage
    class xLanguage extends Object

The xLanguage class provides access to a list of language IDs and information about existing label files.

### Remarks

ISO 639 defines the names of languages, such as "en" for English. Microsoft has listed a set of language codes, such "en-us" for English (United States). These language codes are referred to in Microsoft Dynamics AX as Language IDs. Microsoft Dynamics AX uses "ko-jo" for Korean (Johab). In the Microsoft list, "ko" is both Korean and Korean (Johab). Microsoft Dynamics AX uses "no-ny" for Norwegian (Nynorsk). In the Microsoft list, "no" is both Norwegian (Bokmal) and Norwegian (Nynorsk). Microsoft Dynamics AX uses "es-tr" to represent Spanish (Spain - Traditional Sort). In the Microsoft list, "es" is both Spanish (Spain - Modern Sort) and Spanish (Spain - Traditional Sort). A language name in the following format, such as "English (United States)", is referred to as the description in Microsoft Dynamics AX.

### Examples

The following example prints all the language IDs from the Microsoft list and a list of existing label files.

    static void aaaTestLanguage(args a) 
    { 
        int i; 
        int cnt; 
        str languageID; 
        str description; 
        str shortName; 
        cnt = xlanguage::languageCount(); 
        for (i = 0; i<=cnt; i++) 
        { 
            languageID =xLanguage::index2languageID(i); 
            print "Language ", i, ":", languageID, ":"; 
        } 
        cnt = xLanguage::labelFileCount(); 
        for (i = 0; i<=cnt; i++) 
        { 
            shortName =xLanguage::labelFileNumber2LanguageID(i); 
            languageID =xLanguage::index2languageID(i); 
            description = xLanguage::languageID2Description(languageID); 
            print i, ":", shortName, ":", description; 
        } 
        pause; 
    }

### Methods

| Method                                                     | Description                                                                                                 |
|------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| ::public static str index2languageID(int number)           | Retrieves the language ID (for example, "en-us") of the specified language.                                 |
| ::public static int labelFileCount()                       | Returns the number of label files.                                                                          |
| ::public static str labelFileNumber2LanguageID(int number) |                                                                                                             |
| ::public static int languageCount()                        |                                                                                                             |
| ::public static str languageID2Description(str languageID) | Returns the name of the specified language (for example, "English (United States)"), given the language ID. |
| ::public static int languageID2LCID(str languageID)        |                                                                                                             |
| ::public static str lcid2languageID(int lcid)              |                                                                                                             |

### Method index2languageID

Retrieves the language ID (for example, "en-us") of the specified language.

    public static str index2languageID(int number)

#### Parameters

number  
A number between 1 and the return value of the languageCount method.

#### Return Value

The language ID.

### Method labelFileCount

Returns the number of label files.

    public static int labelFileCount()

#### Return Value

The number of label files (that is, the number of files that have names in the form ax???\*.ald).

### Method labelFileNumber2LanguageID

    public static str labelFileNumber2LanguageID(int number)

#### Parameters

number  

#### Return Value

### Method languageCount

    public static int languageCount()

#### Return Value

### Method languageID2Description

Returns the name of the specified language (for example, "English (United States)"), given the language ID.

    public static str languageID2Description(str languageID)

#### Parameters

languageID  
The ID of the language (for example, "en-us").

#### Return Value

A string that contains the description of a language.

### Method languageID2LCID

    public static int languageID2LCID(str languageID)

#### Parameters

languageID  

#### Return Value

### Method lcid2languageID

    public static str lcid2languageID(int lcid)

#### Parameters

lcid  

#### Return Value

## Class xMenuFunction
    class xMenuFunction extends SecureNode

The xMenuFunction class represents an interface to other Microsoft Dynamics AX Application objects, providing an easy way to access and run any Form, Report, Job, Class, and Query.

### Remarks

You refer to an Application object using a xMenuFunction object and its methods and properties. For example, you can:

-   Use the Run Method to run the object referenced in the property
-   Create a xMenuFunction object and make a reference to the object it runs (or references to). This enables you to manipulate the arguments passed to the object before running it

Note: This system class represents MenuItem nodes in the AOT. This class enables you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before calling this API.

### Examples

### Methods

| Method                                                                                                  | Description                                                                                                                               |
|---------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])                                                                     | Gets or sets the name of the user who last changed the application object.                                                                |
| public Date changedDate(\[Date value\])                                                                 | Gets or sets the date when an application object was last changed.                                                                        |
| public str changedTime(\[str value\])                                                                   | Gets or sets the time when an application object was last changed.                                                                        |
| public boolean checkAccessRights()                                                                      |                                                                                                                                           |
| public int copyCallerQuery(\[int value\])                                                               |                                                                                                                                           |
| public int correctPermissions(\[int value\])                                                            |                                                                                                                                           |
| public str countryRegionCodes(\[str value\])                                                            |                                                                                                                                           |
| public ObjectRun create(\[xArgs args\])                                                                 | Creates and returns a reference to an Microsoft Dynamics AX application object.                                                           |
| public str createdBy(\[str value\])                                                                     | Gets or sets the name of the user who created the application object.                                                                     |
| public int createPermissions(\[int value\])                                                             |                                                                                                                                           |
| public Date creationDate(\[Date value\])                                                                | Gets or sets the date an application object was created.                                                                                  |
| public str creationTime(\[str value\])                                                                  |                                                                                                                                           |
| public int deletePermissions(\[int value\])                                                             |                                                                                                                                           |
| public str disabledImage(\[str value\])                                                                 | Gets or sets the disabled image of the button.                                                                                            |
| public int disabledImageLocation(\[int value\])                                                         |                                                                                                                                           |
| public int disabledResource(\[int value\])                                                              | Gets or sets the resource ID of the image to use as the disabled button image.                                                            |
| public int enumParameter(\[int value\])                                                                 | Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class.                               |
| public EnumId enumTypeParameter(\[EnumId value\])                                                       | Gets or sets the enumTypeParameter property for the MenuFunction class.                                                                   |
| public int formViewOption(\[int value\])                                                                |                                                                                                                                           |
| public Query getRootQuery()                                                                             |                                                                                                                                           |
| public boolean hasRunPermissions(\[xArgs args\])                                                        | Checks if the xMenuFunction object has execute permissions and run() may be called successfully.                                          |
| public str helpText(\[str value\])                                                                      | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                  |
| public int imageLocation(\[int value\])                                                                 |                                                                                                                                           |
| public str label(\[str value\])                                                                         | Gets or sets the label for a control.                                                                                                     |
| public str linkedPermissionObject(\[str value\])                                                        |                                                                                                                                           |
| public str linkedPermissionObjectChild(\[str value\])                                                   |                                                                                                                                           |
| public int linkedPermissionType(\[int value\])                                                          |                                                                                                                                           |
| public int maintainUserLicense(\[int value\])                                                           |                                                                                                                                           |
| public boolean multiSelect(\[boolean value\])                                                           |                                                                                                                                           |
| public str name(\[str value\])                                                                          | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public int needsRecord(\[int value\])                                                                   |                                                                                                                                           |
| public str normalImage(\[str value\])                                                                   |                                                                                                                                           |
| public int normalResource(\[int value\])                                                                |                                                                                                                                           |
| public str object(\[str value\])                                                                        | Gets or sets the object that is run by the MenuFunction class.                                                                            |
| public int objectType(\[int value\])                                                                    |                                                                                                                                           |
| public int openMode(\[int value\])                                                                      |                                                                                                                                           |
| public Guid origin(\[Guid value\])                                                                      |                                                                                                                                           |
| public str parameters(\[str value\])                                                                    | Gets or sets the list of parameters that are passed to objects taht are run by the MenuFunction class.                                    |
| public str query(\[str value\])                                                                         |                                                                                                                                           |
| public int readPermissions(\[int value\])                                                               |                                                                                                                                           |
| public str reportDesign(\[str value\])                                                                  |                                                                                                                                           |
| public int runOn(\[int value\])                                                                         |                                                                                                                                           |
| public MenuItemType type()                                                                              |                                                                                                                                           |
| public int updatePermissions(\[int value\])                                                             |                                                                                                                                           |
| public int viewUserLicense(\[int value\])                                                               |                                                                                                                                           |
| public str web(\[str value\])                                                                           |                                                                                                                                           |
| public int webAccess(\[int value\])                                                                     |                                                                                                                                           |
| public str webMenuItemName(\[str value\])                                                               |                                                                                                                                           |
| public str webPage(\[str value\])                                                                       |                                                                                                                                           |
| public boolean webSecureTransaction(\[boolean value\])                                                  |                                                                                                                                           |
| public void run(\[xArgs args\])                                                                         | Runs the xMenuFunction object.                                                                                                            |
| ::public static void runCalled(str Name, MenuItemType type, \[boolean setContextMenu\], \[xArgs args\]) |                                                                                                                                           |
| ::public static void runClient(str Name, MenuItemType type, \[boolean setContextMenu\], \[xArgs args\]) |                                                                                                                                           |
| ::public static void runServer(str Name, MenuItemType type, \[boolean setContextMenu\], \[xArgs args\]) |                                                                                                                                           |
| public void new(str Name, MenuItemType type)                                                            | Creates a new xMenuFunction object by passing xMenuFunction's name and MenuItemType to the xMenuFunction constructor.                     |
| public void AOTrun(\[xArgs args\])                                                                      | Compiles this node and its subtree in the Application Object Tree (AOT).                                                                  |

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  
The value to set; optional.

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date when an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  
The value to set; optional.

#### Return Value

The date when an application object was last changed.

### Method changedTime

Gets or sets the time when an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  
The value to set; optional.

#### Return Value

The time when an application object was last changed.

### Method checkAccessRights

    public boolean checkAccessRights()

#### Return Value

### Method copyCallerQuery

    public int copyCallerQuery([int value])

#### Parameters

value  

#### Return Value

### Method correctPermissions

    public int correctPermissions([int value])

#### Parameters

value  

#### Return Value

### Method countryRegionCodes

    public str countryRegionCodes([str value])

#### Parameters

value  

#### Return Value

### Method create

Creates and returns a reference to an Microsoft Dynamics AX application object.

    public ObjectRun create([xArgs args])

#### Parameters

args  
An xArgs class object; optional.

#### Return Value

A reference to an Microsoft Dynamics AX application object.

#### Remarks

This method is used to create an application object. The object that is returned is assigned to an object variable. Note that the init function is invoked by the create function. Therefore you should not invoke it.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method createPermissions

    public int createPermissions([int value])

#### Parameters

value  

#### Return Value

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method deletePermissions

    public int deletePermissions([int value])

#### Parameters

value  

#### Return Value

### Method disabledImage

Gets or sets the disabled image of the button.

    public str disabledImage([str value])

#### Parameters

value  

#### Return Value

The full name of an image file; the system supports all of the GDI-supported image formats.

#### Remarks

This property has precedence over the disabledResource property value. It is used if both of these properties are set.

### Method disabledImageLocation

    public int disabledImageLocation([int value])

#### Parameters

value  

#### Return Value

### Method disabledResource

Gets or sets the resource ID of the image to use as the disabled button image.

    public int disabledResource([int value])

#### Parameters

value  

#### Return Value

The resource ID of the image to use as the disabled button image. Both icon and bitmap images are supported.

### Method enumParameter

Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class.

    public int enumParameter([int value])

#### Parameters

value  

#### Return Value

The enumParameter property that is passed to the object that is run by the MenuFunction class.

### Method enumTypeParameter

Gets or sets the enumTypeParameter property for the MenuFunction class.

    public EnumId enumTypeParameter([EnumId value])

#### Parameters

value  

#### Return Value

The enumTypeParameter property for the MenuFunction class.

### Method formViewOption

    public int formViewOption([int value])

#### Parameters

value  

#### Return Value

### Method getRootQuery

    public Query getRootQuery()

#### Return Value

### Method hasRunPermissions

Checks if the xMenuFunction object has execute permissions and run() may be called successfully.

    public boolean hasRunPermissions([xArgs args])

#### Parameters

args  
An xArgs class object as would be passed to the run() method; optional.

#### Return Value

true if neccessary permissions exist to successfully call run().

#### Remarks

This function may throw in case of permissions failure.

### Method helpText

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialog box.The help text must not exceed 250 characters.

### Method imageLocation

    public int imageLocation([int value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method linkedPermissionObject

    public str linkedPermissionObject([str value])

#### Parameters

value  

#### Return Value

### Method linkedPermissionObjectChild

    public str linkedPermissionObjectChild([str value])

#### Parameters

value  

#### Return Value

### Method linkedPermissionType

    public int linkedPermissionType([int value])

#### Parameters

value  

#### Return Value

### Method maintainUserLicense

    public int maintainUserLicense([int value])

#### Parameters

value  

#### Return Value

### Method multiSelect

    public boolean multiSelect([boolean value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method needsRecord

    public int needsRecord([int value])

#### Parameters

value  

#### Return Value

### Method normalImage

    public str normalImage([str value])

#### Parameters

value  

#### Return Value

### Method normalResource

    public int normalResource([int value])

#### Parameters

value  

#### Return Value

### Method object

Gets or sets the object that is run by the MenuFunction class.

    public str object([str value])

#### Parameters

value  

#### Return Value

The object that is run by the MenuFunction class.

#### Remarks

The property value may be one of the following objects:

-   Form.
-   Report.
-   Job.
-   Class.
-   Query.

### Method objectType

    public int objectType([int value])

#### Parameters

value  

#### Return Value

### Method openMode

    public int openMode([int value])

#### Parameters

value  

#### Return Value

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method parameters

Gets or sets the list of parameters that are passed to objects taht are run by the MenuFunction class.

    public str parameters([str value])

#### Parameters

value  

#### Return Value

The list of parameters that are passed to the object.

#### Remarks

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on.cts ignore passed, unrecognized parameters.

### Method query

    public str query([str value])

#### Parameters

value  

#### Return Value

### Method readPermissions

    public int readPermissions([int value])

#### Parameters

value  

#### Return Value

### Method reportDesign

    public str reportDesign([str value])

#### Parameters

value  

#### Return Value

### Method runOn

    public int runOn([int value])

#### Parameters

value  

#### Return Value

### Method type

    public MenuItemType type()

#### Return Value

### Method updatePermissions

    public int updatePermissions([int value])

#### Parameters

value  

#### Return Value

### Method viewUserLicense

    public int viewUserLicense([int value])

#### Parameters

value  

#### Return Value

### Method web

    public str web([str value])

#### Parameters

value  

#### Return Value

### Method webAccess

    public int webAccess([int value])

#### Parameters

value  

#### Return Value

### Method webMenuItemName

    public str webMenuItemName([str value])

#### Parameters

value  

#### Return Value

### Method webPage

    public str webPage([str value])

#### Parameters

value  

#### Return Value

### Method webSecureTransaction

    public boolean webSecureTransaction([boolean value])

#### Parameters

value  

#### Return Value

### Method run

Runs the xMenuFunction object.

    public void run([xArgs args])

#### Parameters

args  
An xArgs class object; optional.

#### Remarks

This function is used to run a xMenuFunction object from code.

### Method runCalled

    public static void runCalled(str Name, MenuItemType type, [boolean setContextMenu], [xArgs args])

#### Parameters

Name  

<!-- -->

type  

<!-- -->

setContextMenu  

<!-- -->

args  

### Method runClient

    public static void runClient(str Name, MenuItemType type, [boolean setContextMenu], [xArgs args])

#### Parameters

Name  

<!-- -->

type  

<!-- -->

setContextMenu  

<!-- -->

args  

### Method runServer

    public static void runServer(str Name, MenuItemType type, [boolean setContextMenu], [xArgs args])

#### Parameters

Name  

<!-- -->

type  

<!-- -->

setContextMenu  

<!-- -->

args  

### Method new

Creates a new xMenuFunction object by passing xMenuFunction's name and MenuItemType to the xMenuFunction constructor.

    public void new(str Name, MenuItemType type)

#### Parameters

Name  
A constant in the MenuItemType system enumeration: MenuItemType::Display, MenuItemType::Output, or MenuItemType::Action.

<!-- -->

type  
A constant in the MenuItemType system enumeration: MenuItemType::Display, MenuItemType::Output, or MenuItemType::Action.

#### Remarks

When creating a xMenuFunction object, the parameters must uniquely identify an existing xMenuFunction. If not, Exception::Internal is thrown.

### Method AOTrun

Compiles this node and its subtree in the Application Object Tree (AOT).

    public void AOTrun([xArgs args])

#### Parameters

args  

## Class xNavPane
    class xNavPane extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                | Description                                       |
|-------------------------------------------------------------------------------------------------------|---------------------------------------------------|
| public boolean collapseFavoriteNode(str path)                                                         |                                                   |
| public boolean collapseNode(str path)                                                                 |                                                   |
| public boolean expandFavoriteNode(str path)                                                           |                                                   |
| public boolean expandNode(str path)                                                                   |                                                   |
| public boolean favPaneVisible(\[boolean value\])                                                      |                                                   |
| public container getButtons()                                                                         |                                                   |
| public str getCurrMenuName()                                                                          |                                                   |
| public TreeNode getSelectedFavoriteNode()                                                             |                                                   |
| public TreeNode getSelectedNode()                                                                     |                                                   |
| public boolean navPaneVisible(\[boolean value\])                                                      |                                                   |
| public boolean runFavoriteNode(str path)                                                              |                                                   |
| public boolean runNode(str path)                                                                      |                                                   |
| public str selectedFavoriteGroup(\[str groupName\])                                                   |                                                   |
| public str selectedGroup(\[str groupName\])                                                           |                                                   |
| public boolean setSelectedFavoriteNode(str path)                                                      |                                                   |
| public boolean setSelectedNode(str path)                                                              |                                                   |
| public void refreshFavorites(\[str selectFavoriteGroup\], \[int workspaceNum\], \[boolean saveToDB\]) |                                                   |
| public void setCurrMenuButtons(container buttons)                                                     |                                                   |
| public void loadStartupButtons()                                                                      |                                                   |
| public void new()                                                                                     | Initializes a new instance of the xNavPane class. |

### Method collapseFavoriteNode

    public boolean collapseFavoriteNode(str path)

#### Parameters

path  

#### Return Value

### Method collapseNode

    public boolean collapseNode(str path)

#### Parameters

path  

#### Return Value

### Method expandFavoriteNode

    public boolean expandFavoriteNode(str path)

#### Parameters

path  

#### Return Value

### Method expandNode

    public boolean expandNode(str path)

#### Parameters

path  

#### Return Value

### Method favPaneVisible

    public boolean favPaneVisible([boolean value])

#### Parameters

value  

#### Return Value

### Method getButtons

    public container getButtons()

#### Return Value

### Method getCurrMenuName

    public str getCurrMenuName()

#### Return Value

### Method getSelectedFavoriteNode

    public TreeNode getSelectedFavoriteNode()

#### Return Value

### Method getSelectedNode

    public TreeNode getSelectedNode()

#### Return Value

### Method navPaneVisible

    public boolean navPaneVisible([boolean value])

#### Parameters

value  

#### Return Value

### Method runFavoriteNode

    public boolean runFavoriteNode(str path)

#### Parameters

path  

#### Return Value

### Method runNode

    public boolean runNode(str path)

#### Parameters

path  

#### Return Value

### Method selectedFavoriteGroup

    public str selectedFavoriteGroup([str groupName])

#### Parameters

groupName  

#### Return Value

### Method selectedGroup

    public str selectedGroup([str groupName])

#### Parameters

groupName  

#### Return Value

### Method setSelectedFavoriteNode

    public boolean setSelectedFavoriteNode(str path)

#### Parameters

path  

#### Return Value

### Method setSelectedNode

    public boolean setSelectedNode(str path)

#### Parameters

path  

#### Return Value

### Method refreshFavorites

    public void refreshFavorites([str selectFavoriteGroup], [int workspaceNum], [boolean saveToDB])

#### Parameters

selectFavoriteGroup  

<!-- -->

workspaceNum  

<!-- -->

saveToDB  

### Method setCurrMenuButtons

    public void setCurrMenuButtons(container buttons)

#### Parameters

buttons  

### Method loadStartupButtons

    public void loadStartupButtons()

### Method new

Initializes a new instance of the xNavPane class.

    public void new()

## Class XppCompiler
    class XppCompiler extends Object

### Remarks

### Examples

### Methods

| Method                                 | Description                                                                                                       |
|----------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| public boolean compile(str source)     |                                                                                                                   |
| public boolean compileExpr(str source) |                                                                                                                   |
| public str dumpClass(str className)    | Creates an XML string that contains the X++ compiler information for a class.                                     |
| public str dumpEnums()                 | Creates an XML string that contains the X++ compiler information for all enumerations in the current application. |
| public str dumpTable(str tableName)    | Creates an XML string that contains the X++ compiler information for a table.                                     |
| public str errorText()                 |                                                                                                                   |
| public AnyType execute(VarArg )        |                                                                                                                   |
| public AnyType executeEx()             |                                                                                                                   |
| public void setGuidArg(Guid arg)       |                                                                                                                   |
| public void setInt64Arg(Int64 arg)     |                                                                                                                   |
| public void setDateArg(Date arg)       |                                                                                                                   |
| public void new()                      | Initializes a new instance of the XppCompiler class.                                                              |
| public void endArgs()                  |                                                                                                                   |
| public void startArgs()                |                                                                                                                   |
| public void setRealArg(Real arg)       |                                                                                                                   |
| public void setIntArg(int arg)         |                                                                                                                   |
| public void setStrArg(str arg)         |                                                                                                                   |

### Method compile

    public boolean compile(str source)

#### Parameters

source  

#### Return Value

### Method compileExpr

    public boolean compileExpr(str source)

#### Parameters

source  

#### Return Value

### Method dumpClass

Creates an XML string that contains the X++ compiler information for a class.

    public str dumpClass(str className)

#### Parameters

className  

#### Return Value

The X++ compiler information for the specified class

#### Remarks

General use of this method is discouraged, because the output format might change without warning from version to version.

### Method dumpEnums

Creates an XML string that contains the X++ compiler information for all enumerations in the current application.

    public str dumpEnums()

#### Return Value

The X++ compiler information for all enumerations in the current application

#### Remarks

General use of this method is discouraged, because the output format might change without warning from version to version.

### Method dumpTable

Creates an XML string that contains the X++ compiler information for a table.

    public str dumpTable(str tableName)

#### Parameters

tableName  

#### Return Value

The X++ compiler information for the specified table

#### Remarks

General use of this method is discouraged, because the output format might change without warning from version to version.

### Method errorText

    public str errorText()

#### Return Value

### Method execute

    public AnyType execute(VarArg )

#### Parameters

  

#### Return Value

#### Remarks

XppCompiler objects can compile code at run time. This presents a security risk. Therefore, execute method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

#### Examples

The following example calls the execute method to compile and execute the supplied buffer.

    void XppCompilerExecuteExample(Common _buf) 
    { 
        XppCompiler       xpp; 
        ExecutePermission perm; 
        perm = new ExecutePermission(); 
        if (perm == null) 
        { 
            return; 
        } 
        perm.assert(); 
        xpp = new XppCompiler(); 
        if (xpp != null) 
        { 
            xpp.execute(_buf); 
        } 
        CodeAccessPermission::revertAssert(); 
    }

### Method executeEx

    public AnyType executeEx()

#### Return Value

#### Remarks

XppCompiler objects can compile code at run time. This presents a security risk. Therefore, the executeEx method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

#### Examples

    void XppCompilerExecuteExExample() 
    { 
        XppCompiler       xpp; 
        ExecutePermission perm; 
        perm = new ExecutePermission(); 
        if (perm == null) 
        { 
            return; 
        } 
        perm.assert(); 
        xpp = new XppCompiler(); 
        if (xpp != null) 
        { 
            xpp.executeEx(); 
        } 
        CodeAccessPermission::revertAssert(); 
    }

### Method setGuidArg

    public void setGuidArg(Guid arg)

#### Parameters

arg  

### Method setInt64Arg

    public void setInt64Arg(Int64 arg)

#### Parameters

arg  

### Method setDateArg

    public void setDateArg(Date arg)

#### Parameters

arg  

### Method new

Initializes a new instance of the XppCompiler class.

    public void new()

#### Remarks

Instances of the XppCompiler class can compile code at run time. Because this presents a security risk, the new method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission Class.

### Method endArgs

    public void endArgs()

### Method startArgs

    public void startArgs()

### Method setRealArg

    public void setRealArg(Real arg)

#### Parameters

arg  

### Method setIntArg

    public void setIntArg(int arg)

#### Parameters

arg  

### Method setStrArg

    public void setStrArg(str arg)

#### Parameters

arg  

## Class XppPrePostArgs
    class XppPrePostArgs extends XppEventArgs

The XppPrePostArgs class provides information about a publisher's arguments and return values for pre-handlers and post-handlers.

### Remarks

A publisher is a method that exposes pre-events and post-events.

### Examples

### Methods

| Method                                                                                       | Description                                                                                                 |
|----------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| public boolean wrapper(str fieldName, AnyType value)                                         |                                                                                                             |
| public struct args()                                                                         |                                                                                                             |
| public boolean existsArg(str fieldName)                                                      | Checks the existence of the publisher's argument by name.                                                   |
| public AnyType getArgNum(int argIndex)                                                       | Retrieves the ;publisher's argument by index.                                                               |
| public int setArgNum(int argIndex, AnyType value)                                            | Sets the publisher's argument by index.                                                                     |
| public AnyType value(str fieldName)                                                          |                                                                                                             |
| public XppEventHandlerCalledWhen getCalledWhen()                                             | Retrieves a value that indicates whether the instance is currently serving a pre-handler or a post-handler. |
| public AnyType getReturnValue()                                                              | Gets the publisher's return value.                                                                          |
| public AnyType getThis()                                                                     | Gets the publisher's "this" reference.                                                                      |
| public boolean removeArg(str fieldName)                                                      |                                                                                                             |
| public int wrapper(str fieldName, AnyType value)                                             |                                                                                                             |
| public int setReturnValue(AnyType retval)                                                    | Sets the publisher's return value.                                                                          |
| public str isFirst()                                                                         |                                                                                                             |
| public void setCalledWhen(XppEventHandlerCalledWhen calledWhen)                              | Sets whether the instance is currently serving a pre-handler or a post-handler.                             |
| ::public static void setReturnValueEx(AnyType retval, XppPrePostArgs args)                   |                                                                                                             |
| public void new(\[AnyType thisPtr\], \[str args\], \[XppEventHandlerCalledWhen calledWhen\]) | Initializes a new instance of the Object class.                                                             |

### Method wrapper

    public boolean wrapper(str fieldName, AnyType value)

#### Parameters

fieldName  

<!-- -->

value  

#### Return Value

### Method args

    public struct args()

#### Return Value

### Method existsArg

Checks the existence of the publisher's argument by name.

    public boolean existsArg(str fieldName)

#### Parameters

fieldName  

#### Return Value

A Boolean data type value that indicates whether the specified argument exists.

#### Remarks

Argument names are case insensitive.

### Method getArgNum

Retrieves the ;publisher's argument by index.

    public AnyType getArgNum(int argIndex)

#### Parameters

argIndex  
An int index of the target argument.

#### Return Value

An anytype value of the specified argument.

#### Remarks

The index range is 0-based for static publishers but 1-based for instance publishers.

### Method setArgNum

Sets the publisher's argument by index.

    public int setArgNum(int argIndex, AnyType value)

#### Parameters

argIndex  
An anytype value to assign to the specified argument.

<!-- -->

value  
An anytype value to assign to the specified argument.

#### Return Value

An int data type value of 1.

#### Remarks

The index range is 0-based for static publishers but 1-based for instance publishers.

### Method value

    public AnyType value(str fieldName)

#### Parameters

fieldName  

#### Return Value

### Method getCalledWhen

Retrieves a value that indicates whether the instance is currently serving a pre-handler or a post-handler.

    public XppEventHandlerCalledWhen getCalledWhen()

#### Return Value

An XppEventHandlerCalledWhen data type value that indicates whether the XppPrePostArgs instance is serving the pre-handlers or the post-handlers.

### Method getReturnValue

Gets the publisher's return value.

    public AnyType getReturnValue()

#### Return Value

An anytype data type value that represents the publisher's return value.

#### Remarks

This method is not intended for pre-handlers.

### Method getThis

Gets the publisher's "this" reference.

    public AnyType getThis()

#### Return Value

An anytype data type value that represents the publisher's "this" reference.

#### Remarks

Returns a nullNothingnullptrunita null reference (Nothing in Visual Basic) reference if the publisher is static.

### Method removeArg

    public boolean removeArg(str fieldName)

#### Parameters

fieldName  

#### Return Value

### Method wrapper

    public int wrapper(str fieldName, AnyType value)

#### Parameters

fieldName  

<!-- -->

value  

#### Return Value

### Method setReturnValue

Sets the publisher's return value.

    public int setReturnValue(AnyType retval)

#### Parameters

retval  

#### Return Value

An int data type value of 1.

#### Remarks

This method is not intended for pre-handlers or for publishers that return void.

### Method isFirst

    public str isFirst()

#### Return Value

### Method setCalledWhen

Sets whether the instance is currently serving a pre-handler or a post-handler.

    public void setCalledWhen(XppEventHandlerCalledWhen calledWhen)

#### Parameters

calledWhen  

#### Remarks

This method must never be called explicitly from the pre-handler or post-handler code. This method is reserved for unit testing and auto-generated code only.

### Method setReturnValueEx

    public static void setReturnValueEx(AnyType retval, XppPrePostArgs args)

#### Parameters

retval  

<!-- -->

args  

### Method new

Initializes a new instance of the Object class.

    public void new([AnyType thisPtr], [str args], [XppEventHandlerCalledWhen calledWhen])

#### Parameters

thisPtr  

<!-- -->

args  

<!-- -->

calledWhen  

## Class xRecord
    class xRecord extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                     | Description                                                                                                                    |
|----------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| public boolean aosValidateDelete()                                                                                         | Validates on the server that the specified record can be deleted from a table.                                                 |
| public boolean aosValidateInsert()                                                                                         | Validates on the server that the specified record can be inserted.                                                             |
| public boolean aosValidateRead()                                                                                           | Validates on the server that the specified record can be read.                                                                 |
| public boolean aosValidateUpdate()                                                                                         | Validates on the server that the specified record can be updated.                                                              |
| public container buf2con(\[boolean packOrigBuffer\])                                                                       | Packs the table buffers of an xRecord instance into an X++ container.                                                          |
| public boolean canSubmitToWorkflow(\[str workflowType\])                                                                   | Indicates whether submission to workflow is possible.                                                                          |
| public str caption()                                                                                                       | Gets and sets the caption property of a table.                                                                                 |
| public boolean checkInvalidFieldAccess(\[boolean checkInvalidFieldAccess\])                                                | Gets and sets invalid field access.                                                                                            |
| public boolean checkRecord(\[boolean checkMandatoryFields\])                                                               | Gets and sets the property that indicates whether to check mandatory fields.                                                   |
| public boolean checkRestrictedDeleteActions(\[boolean checkRestrictedDeleteActions\])                                      | Gets and sets the property that indicates whether a record can be deleted.                                                     |
| public SelectableDataArea company(\[SelectableDataArea company\])                                                          | Gets and sets the property that indicates a legal entity for the record.                                                       |
| public Common con2buf(container container)                                                                                 | Unpacks a container into the table buffers.                                                                                    |
| public ConcurrencyModel concurrencyModel(\[ConcurrencyModel concurrencyModel\])                                            | Gets and sets the default concurrency model to use to update records.                                                          |
| public int context(\[int newValue\])                                                                                       | Gets and sets the context property.                                                                                            |
| public Common data(\[Common cursor\])                                                                                      | Retrieves a row from the table.                                                                                                |
| public FormObjectSet dataSource()                                                                                          | Retrieves the data source of the table.                                                                                        |
| public boolean disableCache(\[boolean newValue\])                                                                          | Gets and sets the property that indicates whether caching is disabled.                                                         |
| public boolean doValidateDelete()                                                                                          | Performs the action to validate that a record can be deleted.                                                                  |
| public boolean equal(Common cursor)                                                                                        | Determines whether the specified object is equal to the current one.                                                           |
| public AccessRight fieldAccessRight(FieldName fieldName)                                                                   | Returns the field access right.                                                                                                |
| public AccessRight fieldBufferAccessRight(FieldName fieldName)                                                             | Returns the field access right for the current record.                                                                         |
| public FieldState fieldState(FieldId fieldId, \[FieldState state\])                                                        | Sets or returns the state of a field in the table buffer.                                                                      |
| public container getAllowRedefault()                                                                                       | Returns the list of fields that are allowed to re-default.                                                                     |
| public container getDefaultingDependencies()                                                                               | Returns the container that holds defaulting dependencies.                                                                      |
| public TableExtension getExtension()                                                                                       | Returns the table extension.                                                                                                   |
| public AnyType getFieldValue(str fieldName, \[int arrayIndex\])                                                            | Gets the value of the specified field from a table buffer.                                                                     |
| public str getInstanceRelationType()                                                                                       | Returns the table name that corresponds to the InstanceRelationType ID.                                                        |
| public str getPhysicalTableName()                                                                                          | Return the physical table name, which, in the case of the SQL Temp DB table, is the table instance name.                       |
| public PresenceInfo getPresenceFieldData(FieldId fieldId, AnyType fieldValue)                                              | Retrieves the PresenceInfo value from the specified field.                                                                     |
| public str getSQLStatement()                                                                                               | Gets the SQL statement that is used to return records from the database.                                                       |
| public Common getTableInInstanceHierarchy(TableId tableId)                                                                 |                                                                                                                                |
| public TableType getTableType()                                                                                            | Indicates the type of the table.                                                                                               |
| public boolean hasRelatedTable(str relatedRoleName)                                                                        | Indicates whether a foreign key constraint buffer is linked with the table.                                                    |
| public str helpField(FieldId fieldId)                                                                                      | Retrieves a string that contains the Help text for the specified field.                                                        |
| public FieldState inputStatus(\[FieldState inputStatus\])                                                                  | Sets or returns the current input status of the table buffer.                                                                  |
| public boolean interactiveContext(\[boolean context\])                                                                     | Sets or returns the current interactive context of the table buffer.                                                           |
| public boolean isFieldDataRetrieved(str fieldName, \[int arrayIndex\])                                                     | Checks whether the data of the given field has been retrieved.                                                                 |
| public boolean isFieldSet(FieldId fieldId)                                                                                 | Checks whether a field has a Set or Defaulted state.                                                                           |
| public boolean isFormDataSource()                                                                                          | Indicates whether the data source is a form.                                                                                   |
| public boolean isNewRecord()                                                                                               | Returns true if the record is a new record that hasn't been persisted yet.                                                     |
| public boolean isPartOfUOWSaveChanges()                                                                                    |                                                                                                                                |
| public boolean isTempDb()                                                                                                  | Indicates whether the type of the table is SQL TempDB.                                                                         |
| public boolean isTmp()                                                                                                     | Indicates whether this is a temporary table.                                                                                   |
| public Common joinChild()                                                                                                  | Finds the join child of the current record.                                                                                    |
| public Common joinParent()                                                                                                 | Finds the join parent of the current record.                                                                                   |
| public boolean linkPhysicalTableInstance(\[Common record\])                                                                | Checks whether there is a link for the physical table instance for the record.                                                 |
| public Common orig()                                                                                                       | Retrieves the original values of the current record.                                                                           |
| public boolean overwriteSystemfields(\[boolean allowOverwrite\])                                                           | Gets and sets the property that indicates whether system fields can be overwritten.                                            |
| public boolean queryTimedOut()                                                                                             | Indicates whether the query exceeded the time limit for execution.                                                             |
| public int queryTimeout(\[int seconds\], \[boolean raiseException\])                                                       | Gets and sets the property that indicates the time limit for the execution of a query.                                         |
| public boolean readCommittedLock(\[boolean readCommittedLock\])                                                            |                                                                                                                                |
| public boolean readPast(\[boolean skipLockedRows\])                                                                        | Gets and sets the property that indicates whether to skip rows that are locked by other processes when a record is read.       |
| public boolean recordLevelSecurity(\[boolean newValue\])                                                                   | Gets and sets the property that indicates whether to apply security on a record level.                                         |
| public Common relatedTable(str name, \[Common buffer\])                                                                    | Sets or returns the related buffer of a link of a table buffer.                                                                |
| public Int64 RowCount()                                                                                                    | Retrieves the number of rows in the table.                                                                                     |
| public boolean selectForUpdate(\[boolean lockRecordsExclusive\])                                                           | Gets and sets the property that indicates whether to select records for update when they are read.                             |
| public boolean selectLocked(\[boolean lockRecordsShared\])                                                                 | Indicates whether to select locked records.                                                                                    |
| public Common selectRefRecord(FieldId referenceFieldId)                                                                    | Selects the record by referenced field ID.                                                                                     |
| public boolean selectWithRepeatableRead(\[boolean useRepeatableRead\])                                                     | Gets and sets the property that indicates whether repeatable read is enabled.                                                  |
| public boolean setTempDB()                                                                                                 |                                                                                                                                |
| public boolean setTmp()                                                                                                    | Sets the table so that it is not persisted to the database.                                                                    |
| public boolean skipAosValidation(\[boolean newValue\])                                                                     | Gets and sets the property that indicates whether to skip validation of Microsoft Dynamics AX Application Object Server (AOS). |
| public boolean skipDatabaseLog(\[boolean newValue\])                                                                       | Gets and sets the property that indicates whether to skip database log requests.                                               |
| public boolean skipDataMethods(\[boolean newValue\])                                                                       | Gets and sets the property that indicates whether to discard overloaded methods.                                               |
| public boolean skipDeleteActions(\[boolean newValue\])                                                                     | Gets and sets the property that indicates whether to skip delete actions on the table.                                         |
| public boolean skipDeleteMethod(\[boolean newValue\])                                                                      | Gets and sets the property that indicates whether to discard overloaded methods.                                               |
| public boolean skipEvents(\[boolean newValue\])                                                                            | Provides an option to turn off calling the Application.event\* methods for the lifetime of an xRecord object.                  |
| public boolean skipPostLoad(\[boolean newValue\])                                                                          | Gets and sets the property that indicates whether to skip executing the xRecord.postLoad method on the table.                  |
| public boolean skipTTSCheck(\[boolean newValue\])                                                                          | Gets and sets the property that indicates whether to skip the check to determine whether the record is selected for update.    |
| public boolean suppressWarnings(\[boolean newValue\])                                                                      | Gets and sets the property that indicates whether to suppress warnings for this pointer.                                       |
| public AccessRight tableAccessRight()                                                                                      | Returns the table access right.                                                                                                |
| public AccessRight tableBufferAccessRight()                                                                                | Returns the table access right for the current record.                                                                         |
| public boolean takeOwnershipOfTempDBTable(boolean newValue)                                                                |                                                                                                                                |
| public str toolTipField(FieldId fieldId)                                                                                   | Retrieves the HelpText value for the specified field.                                                                          |
| public str toolTipRecord()                                                                                                 | Retrieves the ToolTip value for the current record.                                                                            |
| public int usageCount()                                                                                                    | Retrieves the current number of references (the value of the reference counter) that the object has.                           |
| public boolean useExistingTempDBTable(str physicalTempTableName)                                                           |                                                                                                                                |
| public boolean validateDelete()                                                                                            | Determines whether the current record is valid and ready to be deleted from the database.                                      |
| public boolean validateField(FieldId fieldIdToCheck)                                                                       | Determines whether the specified field is valid.                                                                               |
| public boolean validateFieldValue(FieldName fieldName, \[int arrayIndex\])                                                 |                                                                                                                                |
| private container validateRelations(\[boolean onlyValidateCompositeRelations\], \[boolean onlyValidateModifiedRelations\]) |                                                                                                                                |
| public boolean validateWrite()                                                                                             | Determines whether the current record is valid and ready to be written.                                                        |
| public ValidTimeStateUpdate validTimeStateUpdateMode(ValidTimeStateUpdate validTimeStateUpdateMode)                        | Sets a valid time state update mode on the cursor.                                                                             |
| public CachedHow wasCached()                                                                                               | Specifies the location from which the data was retrieved.                                                                      |
| public str xml(\[int indent\])                                                                                             | Retrieves an XML string that represents the current object.                                                                    |
| public void doDelete()                                                                                                     | Deletes the current record from the table and bypasses any additional logic in the delete method of the table.                 |
| public void update()                                                                                                       | Updates the current record.                                                                                                    |
| public void merge(Common mergeInto)                                                                                        | Merges the current table with the specified table.                                                                             |
| public void clear()                                                                                                        | Removes all rows from the table buffer.                                                                                        |
| public void setXDSContext(\[str contextString\])                                                                           | Sets new XDS context.                                                                                                          |
| public void renamePrimaryKey()                                                                                             | Renames the foreign keys in other tables according to the change of the corresponding primary key value in this table.         |
| public void dispose()                                                                                                      | Releases resources that are used by the xRecord object.                                                                        |
| public void setConnection(Connection connection)                                                                           | Sets the user connection for this table.                                                                                       |
| public void delete()                                                                                                       | Deletes the current record from the table.                                                                                     |
| public void defaultField(FieldId fieldId)                                                                                  | Populates default values in a field in the table.                                                                              |
| private void dbOpInTransaction(\[boolean isWriteOperation\])                                                               | Makes sure that database operations are correctly closed if they fail.                                                         |
| public void write()                                                                                                        | Updates a record if it exists; otherwise, inserts a record.                                                                    |
| public void preRemoting()                                                                                                  | Is executed before a cross-tier call is about to be executed for the table that would pack its state to the other tier.        |
| public void modifiedFieldValue(FieldName fieldName, \[int arrayIndex\])                                                    | Modifies the specified field to the original value.                                                                            |
| public void defaultRow()                                                                                                   | Populates default values in fields in the table in the non-interactive case.                                                   |
| public void reread()                                                                                                       | Rereads the record from the table.                                                                                             |
| public void modifiedField(FieldId fieldId)                                                                                 | Modifies the specified field to the original.                                                                                  |
| public void ttsabort()                                                                                                     | Aborts a transaction that was started by a call to the ttsbegin method.                                                        |
| public void insert()                                                                                                       | Inserts the record into the table.                                                                                             |
| public void doClear()                                                                                                      | Removes all rows from the table buffer and bypasses any additional logic in the clear method of the table.                     |
| public void initValue()                                                                                                    | Initializes a field to the default value.                                                                                      |
| public void doUpdate()                                                                                                     | Updates the current record and bypasses any additional logic in the update method of the table.                                |
| public void ttsbegin()                                                                                                     | Starts a transaction that can be either committed by the ttscommit method or aborted by the ttsabort method.                   |
| public void setCrossPartition(boolean newValue)                                                                            | Sets or resets cross-partitioning for the table.                                                                               |
| public void setTmpData(Common cursor)                                                                                      | Sets the contents of the temporary table to the specified data.                                                                |
| public void ttscommit()                                                                                                    | Commits a transaction that was started by a call to the ttsbegin method.                                                       |
| public void setFieldValue(str fieldName, AnyType value, \[int arrayIndex\])                                                | Sets the field value in the record buffer.                                                                                     |
| public void doInsert()                                                                                                     | Inserts the record into the table and bypasses any additional logic in the insert method of the table.                         |
| public void setSQLTracing(\[boolean tracingmode\])                                                                         | Enables or disables SQL tracing mode.                                                                                          |
| public void postLoad()                                                                                                     | Is executed after a record is read.                                                                                            |

### Method aosValidateDelete

Validates on the server that the specified record can be deleted from a table.

    public boolean aosValidateDelete()

#### Return Value

true if the record can be deleted; otherwise, false.

### Method aosValidateInsert

Validates on the server that the specified record can be inserted.

    public boolean aosValidateInsert()

#### Return Value

true if the record can be inserted; otherwise, false.

### Method aosValidateRead

Validates on the server that the specified record can be read.

    public boolean aosValidateRead()

#### Return Value

true if the record can be read; otherwise, false.

### Method aosValidateUpdate

Validates on the server that the specified record can be updated.

    public boolean aosValidateUpdate()

#### Return Value

true if the record can be updated; otherwise, false.

### Method buf2con

Packs the table buffers of an xRecord instance into an X++ container.

    public container buf2con([boolean packOrigBuffer])

#### Parameters

packOrigBuffer  

#### Return Value

A container that holds packed buffers.

### Method canSubmitToWorkflow

Indicates whether submission to workflow is possible.

    public boolean canSubmitToWorkflow([str workflowType])

#### Parameters

workflowType  

#### Return Value

true if submission is possible; otherwise, false.

### Method caption

Gets and sets the caption property of a table.

    public str caption()

#### Return Value

The caption of the table.

### Method checkInvalidFieldAccess

Gets and sets invalid field access.

    public boolean checkInvalidFieldAccess([boolean checkInvalidFieldAccess])

#### Parameters

checkInvalidFieldAccess  
The value to set; optional.

#### Return Value

true if invalid field access is set; otherwise, false.

### Method checkRecord

Gets and sets the property that indicates whether to check mandatory fields.

    public boolean checkRecord([boolean checkMandatoryFields])

#### Parameters

checkMandatoryFields  
A Boolean value that indicates whether to check mandatory fields; optional.

#### Return Value

true if mandatory fields are checked; otherwise, false.

### Method checkRestrictedDeleteActions

Gets and sets the property that indicates whether a record can be deleted.

    public boolean checkRestrictedDeleteActions([boolean checkRestrictedDeleteActions])

#### Parameters

checkRestrictedDeleteActions  
A Boolean value that indicates whether a record can be deleted; optional.

#### Return Value

true if the record can be deleted; otherwise, false.

#### Remarks

The property is based on delete actions for a table, and whether the table allows for delete actions when corresponding records are in corresponding tables.

### Method company

Gets and sets the property that indicates a legal entity for the record.

    public SelectableDataArea company([SelectableDataArea company])

#### Parameters

company  
A new legal entity for the record; optional.

#### Return Value

The legal entity ID.

### Method con2buf

Unpacks a container into the table buffers.

    public Common con2buf(container container)

#### Parameters

container  

#### Return Value

### Method concurrencyModel

Gets and sets the default concurrency model to use to update records.

    public ConcurrencyModel concurrencyModel([ConcurrencyModel concurrencyModel])

#### Parameters

concurrencyModel  
The new concurrency model, by default; optional.

#### Return Value

The current value of the concurrency model property, by default.

### Method context

Gets and sets the context property.

    public int context([int newValue])

#### Parameters

newValue  
The new value of the context property; optional.

#### Return Value

The current value of the context property.

### Method data

Retrieves a row from the table.

    public Common data([Common cursor])

#### Parameters

cursor  
The row to retrieve; optional.

#### Return Value

The record buffer.

#### Remarks

Partly because scenarios that involve table inheritance, we recommend that you instead use the following methods on the Global class: con2buf, buf2con, and buf2buf.

### Method dataSource

Retrieves the data source of the table.

    public FormObjectSet dataSource()

#### Return Value

The data source of the table.

### Method disableCache

Gets and sets the property that indicates whether caching is disabled.

    public boolean disableCache([boolean newValue])

#### Parameters

newValue  
A Boolean value that indicates whether caching is disabled.

#### Return Value

The new value of the disable cache property.

### Method doValidateDelete

Performs the action to validate that a record can be deleted.

    public boolean doValidateDelete()

#### Return Value

### Method equal

Determines whether the specified object is equal to the current one.

    public boolean equal(Common cursor)

#### Parameters

cursor  
The object to check for equality.

#### Return Value

true if the objects are equal; otherwise, false.

#### Remarks

This method is overridden. The default implementation of the Object::equal method supports only reference equality. Derived classes can override the Object::equal method to support value equality.

### Method fieldAccessRight

Returns the field access right.

    public AccessRight fieldAccessRight(FieldName fieldName)

#### Parameters

fieldName  
The name of the field for which to obtain the field access right.

#### Return Value

The field access right for the field.

### Method fieldBufferAccessRight

Returns the field access right for the current record.

    public AccessRight fieldBufferAccessRight(FieldName fieldName)

#### Parameters

fieldName  
The name of the field for which to obtain the field access right.

#### Return Value

The field access right.

### Method fieldState

Sets or returns the state of a field in the table buffer.

    public FieldState fieldState(FieldId fieldId, [FieldState state])

#### Parameters

fieldId  

<!-- -->

state  

#### Return Value

The old state of the field.

### Method getAllowRedefault

Returns the list of fields that are allowed to re-default.

    public container getAllowRedefault()

#### Return Value

The container that holds the fields.

### Method getDefaultingDependencies

Returns the container that holds defaulting dependencies.

    public container getDefaultingDependencies()

#### Return Value

The container that holds defaulting dependencies.

### Method getExtension

Returns the table extension.

    public TableExtension getExtension()

#### Return Value

The table extension.

### Method getFieldValue

Gets the value of the specified field from a table buffer.

    public AnyType getFieldValue(str fieldName, [int arrayIndex])

#### Parameters

fieldName  
The array index of the field; optional.

<!-- -->

arrayIndex  
The array index of the field; optional.

#### Return Value

The value of a field.

#### Remarks

The arrayIndex parameter only applies to array fields. Either omit this parameter or specify 0 (zero) for fields that are not arrays.This method throws an ArgumentOutOfRange exception if the specified field is unknown.

### Method getInstanceRelationType

Returns the table name that corresponds to the InstanceRelationType ID.

    public str getInstanceRelationType()

#### Return Value

The table name that corresponds to the InstanceRelationType ID.

### Method getPhysicalTableName

Return the physical table name, which, in the case of the SQL Temp DB table, is the table instance name.

    public str getPhysicalTableName()

#### Return Value

The physical table name or the table instance name.

### Method getPresenceFieldData

Retrieves the PresenceInfo value from the specified field.

    public PresenceInfo getPresenceFieldData(FieldId fieldId, AnyType fieldValue)

#### Parameters

fieldId  

<!-- -->

fieldValue  

#### Return Value

### Method getSQLStatement

Gets the SQL statement that is used to return records from the database.

    public str getSQLStatement()

#### Return Value

The string that contains the SQL statement.

### Method getTableInInstanceHierarchy

    public Common getTableInInstanceHierarchy(TableId tableId)

#### Parameters

tableId  

#### Return Value

### Method getTableType

Indicates the type of the table.

    public TableType getTableType()

#### Return Value

The type of the table (Regular, InMemory, or TempDB).

### Method hasRelatedTable

Indicates whether a foreign key constraint buffer is linked with the table.

    public boolean hasRelatedTable(str relatedRoleName)

#### Parameters

relatedRoleName  

#### Return Value

true if a foreign key constraint buffer is linked with the table; otherwise, false.

### Method helpField

Retrieves a string that contains the Help text for the specified field.

    public str helpField(FieldId fieldId)

#### Parameters

fieldId  
The field for which to retrieve the Help text.

#### Return Value

The Help text for the specified field.

### Method inputStatus

Sets or returns the current input status of the table buffer.

    public FieldState inputStatus([FieldState inputStatus])

#### Parameters

inputStatus  

#### Return Value

The old input status.

### Method interactiveContext

Sets or returns the current interactive context of the table buffer.

    public boolean interactiveContext([boolean context])

#### Parameters

context  

#### Return Value

The current interactive context of the table buffer.

### Method isFieldDataRetrieved

Checks whether the data of the given field has been retrieved.

    public boolean isFieldDataRetrieved(str fieldName, [int arrayIndex])

#### Parameters

fieldName  

<!-- -->

arrayIndex  

#### Return Value

true if the data has been retrieved; otherwise, false.

### Method isFieldSet

Checks whether a field has a Set or Defaulted state.

    public boolean isFieldSet(FieldId fieldId)

#### Parameters

fieldId  

#### Return Value

true if field is has a Set or Defaulted state; otherwise, false.

### Method isFormDataSource

Indicates whether the data source is a form.

    public boolean isFormDataSource()

#### Return Value

true if the data source is a form; otherwise, false.

### Method isNewRecord

Returns true if the record is a new record that hasn't been persisted yet.

    public boolean isNewRecord()

#### Return Value

true if the record is a new record that hasn't been persisted yet; otherwise, false.

### Method isPartOfUOWSaveChanges

    public boolean isPartOfUOWSaveChanges()

#### Return Value

### Method isTempDb

Indicates whether the type of the table is SQL TempDB.

    public boolean isTempDb()

#### Return Value

true if the type of the table is SQL TempDB; otherwise, false.

### Method isTmp

Indicates whether this is a temporary table.

    public boolean isTmp()

#### Return Value

true if this is a temporary table; otherwise, false.

### Method joinChild

Finds the join child of the current record.

    public Common joinChild()

#### Return Value

The join child of the current record.

### Method joinParent

Finds the join parent of the current record.

    public Common joinParent()

#### Return Value

The join parent of the current record.

### Method linkPhysicalTableInstance

Checks whether there is a link for the physical table instance for the record.

    public boolean linkPhysicalTableInstance([Common record])

#### Parameters

record  

#### Return Value

A Boolean value that indicates whether a link is available.

### Method orig

Retrieves the original values of the current record.

    public Common orig()

#### Return Value

#### Remarks

Partly because of scenarios that involve table inheritance, we recommend that you instead use the following methods on the Global class: con2buf, buf2con, and buf2buf.

### Method overwriteSystemfields

Gets and sets the property that indicates whether system fields can be overwritten.

    public boolean overwriteSystemfields([boolean allowOverwrite])

#### Parameters

allowOverwrite  
A Boolean value that indicates whether system fields can be overwritten; optional.

#### Return Value

true if system fields can be overwritten; otherwise, false.

### Method queryTimedOut

Indicates whether the query exceeded the time limit for execution.

    public boolean queryTimedOut()

#### Return Value

true if the query exceeded the time limit for execution; otherwise, false.

### Method queryTimeout

Gets and sets the property that indicates the time limit for the execution of a query.

    public int queryTimeout([int seconds], [boolean raiseException])

#### Parameters

seconds  

<!-- -->

raiseException  

#### Return Value

The current value of the query time-out property.

### Method readCommittedLock

    public boolean readCommittedLock([boolean readCommittedLock])

#### Parameters

readCommittedLock  

#### Return Value

### Method readPast

Gets and sets the property that indicates whether to skip rows that are locked by other processes when a record is read.

    public boolean readPast([boolean skipLockedRows])

#### Parameters

skipLockedRows  
A Boolean value that indicates whether to skip rows that are locked; optional.

#### Return Value

true if locked rows should be skipped; otherwise, false.

### Method recordLevelSecurity

Gets and sets the property that indicates whether to apply security on a record level.

    public boolean recordLevelSecurity([boolean newValue])

#### Parameters

newValue  
A Boolean value that indicates whether to apply security on a record level; optional.

#### Return Value

true if security should be applied on a record level; otherwise, false.

### Method relatedTable

Sets or returns the related buffer of a link of a table buffer.

    public Common relatedTable(str name, [Common buffer])

#### Parameters

name  

<!-- -->

buffer  

#### Return Value

The related buffer of a link of a table buffer.

### Method RowCount

Retrieves the number of rows in the table.

    public Int64 RowCount()

#### Return Value

The number of rows in the table.

### Method selectForUpdate

Gets and sets the property that indicates whether to select records for update when they are read.

    public boolean selectForUpdate([boolean lockRecordsExclusive])

#### Parameters

lockRecordsExclusive  
A Boolean value that indicates whether to read records for update; optional.

#### Return Value

true if records should be read for update; otherwise, false.

### Method selectLocked

Indicates whether to select locked records.

    public boolean selectLocked([boolean lockRecordsShared])

#### Parameters

lockRecordsShared  
A Boolean value that indicates whether to select locked records.

#### Return Value

true if locked records should be selected; otherwise, false.

### Method selectRefRecord

Selects the record by referenced field ID.

    public Common selectRefRecord(FieldId referenceFieldId)

#### Parameters

referenceFieldId  
The referenced field ID.

#### Return Value

The record buffer.

### Method selectWithRepeatableRead

Gets and sets the property that indicates whether repeatable read is enabled.

    public boolean selectWithRepeatableRead([boolean useRepeatableRead])

#### Parameters

useRepeatableRead  
A Boolean value that indicates whether repeatable read is enabled; optional.

#### Return Value

true if repeatable read is enabled; otherwise, false.

### Method setTempDB

    public boolean setTempDB()

#### Return Value

### Method setTmp

Sets the table so that it is not persisted to the database.

    public boolean setTmp()

#### Return Value

true if the operation was successful; otherwise, false.

### Method skipAosValidation

Gets and sets the property that indicates whether to skip validation of Microsoft Dynamics AX Application Object Server (AOS).

    public boolean skipAosValidation([boolean newValue])

#### Parameters

newValue  
A Boolean value that indicates whether to skip AOS validation.

#### Return Value

true if AOS validation should be skipped; otherwise, false.

#### Remarks

If an attacker can control input to the skipAosValidation method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the SkipAOSValidationPermission class. Make sure that the user has development user rights by setting the security key to SysDevelopment on the control that calls this method.

### Method skipDatabaseLog

Gets and sets the property that indicates whether to skip database log requests.

    public boolean skipDatabaseLog([boolean newValue])

#### Parameters

newValue  
A Boolean value that indicates whether to skip database log requests; optional.

#### Return Value

true if database log requests should be skipped; otherwise, false.

### Method skipDataMethods

Gets and sets the property that indicates whether to discard overloaded methods.

    public boolean skipDataMethods([boolean newValue])

#### Parameters

newValue  
A Boolean value that indicates whether to discard overloaded methods; optional.

#### Return Value

true if overloaded methods should be discarded; otherwise, false.

### Method skipDeleteActions

Gets and sets the property that indicates whether to skip delete actions on the table.

    public boolean skipDeleteActions([boolean newValue])

#### Parameters

newValue  
A Boolean value that indicates whether to ignore requests to delete records; optional.

#### Return Value

true if requests to delete records should be ignored; otherwise, false.

#### Remarks

This method works only when you are using a set-based operation, such as the delete\_from statement. If you use it on a row-based operation, such as the xRecord.delete method, the property will not be respected, and the delete action will still be called.

### Method skipDeleteMethod

Gets and sets the property that indicates whether to discard overloaded methods.

    public boolean skipDeleteMethod([boolean newValue])

#### Parameters

newValue  
A Boolean value that indicates whether to discard overloaded methods; optional.

#### Return Value

true if overloaded methods should be discarded; otherwise, false.

### Method skipEvents

Provides an option to turn off calling the Application.event\* methods for the lifetime of an xRecord object.

    public boolean skipEvents([boolean newValue])

#### Parameters

newValue  
A Boolean value that indicates whether to skip events; optional.

#### Return Value

true if events are skipped; otherwise, false.

#### Remarks

This method resembles the xRecord.skipDatabaseLog method. The skipEvents method is also used internally in the kernel to skip events that make no sense to generate; this is consistent with the current behavior of the xRecord.skipDatabaseLog method:

-   The Application.deleteCompany method: Event generation is turned off for the duration of a company delete operation. This is an admin operation, and it could cause performance issues to support events in this case.
-   The SqlDataDictionary.tableDelete method: Event generation is turned off for the duration of a table delete. This is an admin operation, and it could cause performance issues to support events in this case.
-   The RecordInsertList class, which implements array insert capabilities in the kernel, takes an optional argument, \_skipEvents = false, in the new method that will conditionally skip events as specified by a developer. Even if events are not skipped, this will not make the kernel rewrite the SQL.
-   When a primary key is renamed, event generation is turned off for the duration of the rename operation. This includes a primary key in one record and can include a foreign key in many records. After the rename operation, the eventRenameKey method is called.

### Method skipPostLoad

Gets and sets the property that indicates whether to skip executing the xRecord.postLoad method on the table.

    public boolean skipPostLoad([boolean newValue])

#### Parameters

newValue  
A Boolean value that indicates whether to skip executing the postLoad method on the table; optional.

#### Return Value

true to skip executing the postLoad method; otherwise, false.

### Method skipTTSCheck

Gets and sets the property that indicates whether to skip the check to determine whether the record is selected for update.

    public boolean skipTTSCheck([boolean newValue])

#### Parameters

newValue  
A Boolean value that indicates whether to skip the check; optional.

#### Return Value

true if the TTS check should be skipped; otherwise, false.

### Method suppressWarnings

Gets and sets the property that indicates whether to suppress warnings for this pointer.

    public boolean suppressWarnings([boolean newValue])

#### Parameters

newValue  
A Boolean value that indicates whether to suppress warnings for this pointer; optional.

#### Return Value

true if warnings for this pointer should be suppressed; otherwise, false.

### Method tableAccessRight

Returns the table access right.

    public AccessRight tableAccessRight()

#### Return Value

The table access right value.

### Method tableBufferAccessRight

Returns the table access right for the current record.

    public AccessRight tableBufferAccessRight()

#### Return Value

The table access right for the current record.

### Method takeOwnershipOfTempDBTable

    public boolean takeOwnershipOfTempDBTable(boolean newValue)

#### Parameters

newValue  

#### Return Value

### Method toolTipField

Retrieves the HelpText value for the specified field.

    public str toolTipField(FieldId fieldId)

#### Parameters

fieldId  
The field for which to retrieve the HelpText value.

#### Return Value

The HelpText value of the specified field.

### Method toolTipRecord

Retrieves the ToolTip value for the current record.

    public str toolTipRecord()

#### Return Value

The ToolTip value for the current record.

### Method usageCount

Retrieves the current number of references (the value of the reference counter) that the object has.

    public int usageCount()

#### Return Value

The current number of references that the object has.

#### Remarks

This method is overridden. When an object is created, its reference counter equals 1. When a new reference is created, its value increases. As a reference goes out of scope, its value decreases.

### Method useExistingTempDBTable

    public boolean useExistingTempDBTable(str physicalTempTableName)

#### Parameters

physicalTempTableName  

#### Return Value

### Method validateDelete

Determines whether the current record is valid and ready to be deleted from the database.

    public boolean validateDelete()

#### Return Value

true if the current record can be deleted; otherwise, false.

### Method validateField

Determines whether the specified field is valid.

    public boolean validateField(FieldId fieldIdToCheck)

#### Parameters

fieldIdToCheck  
The field ID of the field to validate.

#### Return Value

true if the specified field is valid; otherwise, false.

### Method validateFieldValue

    public boolean validateFieldValue(FieldName fieldName, [int arrayIndex])

#### Parameters

fieldName  

<!-- -->

arrayIndex  

#### Return Value

### Method validateRelations

    private container validateRelations([boolean onlyValidateCompositeRelations], [boolean onlyValidateModifiedRelations])

#### Parameters

onlyValidateCompositeRelations  

<!-- -->

onlyValidateModifiedRelations  

#### Return Value

### Method validateWrite

Determines whether the current record is valid and ready to be written.

    public boolean validateWrite()

#### Return Value

true if the current record can be written; otherwise, false.

### Method validTimeStateUpdateMode

Sets a valid time state update mode on the cursor.

    public ValidTimeStateUpdate validTimeStateUpdateMode(ValidTimeStateUpdate validTimeStateUpdateMode)

#### Parameters

validTimeStateUpdateMode  

#### Return Value

The old value of the valid time state update mode.

### Method wasCached

Specifies the location from which the data was retrieved.

    public CachedHow wasCached()

#### Return Value

A CachedHow enumeration value that indicates the location from which the data was retrieved.

### Method xml

Retrieves an XML string that represents the current object.

    public str xml([int indent])

#### Parameters

indent  
An integer that indicates the number of spaces to use for indentation in the XML string.

#### Return Value

An XML string that represents the current object.

#### Remarks

This method can be overridden to return values that are meaningful for that type.

### Method doDelete

Deletes the current record from the table and bypasses any additional logic in the delete method of the table.

    public void doDelete()

### Method update

Updates the current record.

    public void update()

### Method merge

Merges the current table with the specified table.

    public void merge(Common mergeInto)

#### Parameters

mergeInto  
The table to merge with.

### Method clear

Removes all rows from the table buffer.

    public void clear()

### Method setXDSContext

Sets new XDS context.

    public void setXDSContext([str contextString])

#### Parameters

contextString  

### Method renamePrimaryKey

Renames the foreign keys in other tables according to the change of the corresponding primary key value in this table.

    public void renamePrimaryKey()

### Method dispose

Releases resources that are used by the xRecord object.

    public void dispose()

### Method setConnection

Sets the user connection for this table.

    public void setConnection(Connection connection)

#### Parameters

connection  

### Method delete

Deletes the current record from the table.

    public void delete()

### Method defaultField

Populates default values in a field in the table.

    public void defaultField(FieldId fieldId)

#### Parameters

fieldId  

### Method dbOpInTransaction

Makes sure that database operations are correctly closed if they fail.

    private void dbOpInTransaction([boolean isWriteOperation])

#### Parameters

isWriteOperation  
A Boolean value that indicates whether the operation is a write operation; optional.

### Method write

Updates a record if it exists; otherwise, inserts a record.

    public void write()

### Method preRemoting

Is executed before a cross-tier call is about to be executed for the table that would pack its state to the other tier.

    public void preRemoting()

### Method modifiedFieldValue

Modifies the specified field to the original value.

    public void modifiedFieldValue(FieldName fieldName, [int arrayIndex])

#### Parameters

fieldName  
The array index of the field; optional.

<!-- -->

arrayIndex  
The array index of the field; optional.

### Method defaultRow

Populates default values in fields in the table in the non-interactive case.

    public void defaultRow()

### Method reread

Rereads the record from the table.

    public void reread()

### Method modifiedField

Modifies the specified field to the original.

    public void modifiedField(FieldId fieldId)

#### Parameters

fieldId  
The field ID to modify.

### Method ttsabort

Aborts a transaction that was started by a call to the ttsbegin method.

    public void ttsabort()

### Method insert

Inserts the record into the table.

    public void insert()

### Method doClear

Removes all rows from the table buffer and bypasses any additional logic in the clear method of the table.

    public void doClear()

### Method initValue

Initializes a field to the default value.

    public void initValue()

### Method doUpdate

Updates the current record and bypasses any additional logic in the update method of the table.

    public void doUpdate()

### Method ttsbegin

Starts a transaction that can be either committed by the ttscommit method or aborted by the ttsabort method.

    public void ttsbegin()

### Method setCrossPartition

Sets or resets cross-partitioning for the table.

    public void setCrossPartition(boolean newValue)

#### Parameters

newValue  
A new Boolean value to set or reset cross-partitioning.

### Method setTmpData

Sets the contents of the temporary table to the specified data.

    public void setTmpData(Common cursor)

#### Parameters

cursor  
The new data for the temporary table.

### Method ttscommit

Commits a transaction that was started by a call to the ttsbegin method.

    public void ttscommit()

### Method setFieldValue

Sets the field value in the record buffer.

    public void setFieldValue(str fieldName, AnyType value, [int arrayIndex])

#### Parameters

fieldName  
The array index of the field; optional.

<!-- -->

value  
The array index of the field; optional.

<!-- -->

arrayIndex  
The array index of the field; optional.

#### Remarks

The arrayIndex parameter applies only to array fields. Either omit this parameter or specify0 (zero) for fields that are not arrays.This method throws an ArgumentOutOfRange exception if the specified field is unknown or a TypeMismatch exception if the value parameter is incompatible with the specified field..

### Method doInsert

Inserts the record into the table and bypasses any additional logic in the insert method of the table.

    public void doInsert()

### Method setSQLTracing

Enables or disables SQL tracing mode.

    public void setSQLTracing([boolean tracingmode])

#### Parameters

tracingmode  

### Method postLoad

Is executed after a record is read.

    public void postLoad()

## Class xRef
    class xRef extends Object

### Remarks

### Examples

### Methods

| Method                                         | Description                                     |
|------------------------------------------------|-------------------------------------------------|
| public AccessLevel accessLevel()               |                                                 |
| public int column()                            |                                                 |
| public container contents()                    |                                                 |
| public xRefKind kind()                         |                                                 |
| public int line()                              |                                                 |
| public XRefMode mode()                         |                                                 |
| public str name()                              |                                                 |
| public str path()                              |                                                 |
| public XRefReference reference()               |                                                 |
| public int typeHandle()                        |                                                 |
| public str typeName(xRefKind kind, int handle) |                                                 |
| public void new(container data)                | Initializes a new instance of the Object class. |
| public void init()                             |                                                 |
| public void finalize()                         |                                                 |
| public void next()                             |                                                 |

### Method accessLevel

    public AccessLevel accessLevel()

#### Return Value

### Method column

    public int column()

#### Return Value

### Method contents

    public container contents()

#### Return Value

### Method kind

    public xRefKind kind()

#### Return Value

### Method line

    public int line()

#### Return Value

### Method mode

    public XRefMode mode()

#### Return Value

### Method name

    public str name()

#### Return Value

### Method path

    public str path()

#### Return Value

### Method reference

    public XRefReference reference()

#### Return Value

### Method typeHandle

    public int typeHandle()

#### Return Value

### Method typeName

    public str typeName(xRefKind kind, int handle)

#### Parameters

kind  

<!-- -->

handle  

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(container data)

#### Parameters

data  

### Method init

    public void init()

### Method finalize

    public void finalize()

### Method next

    public void next()

## Class xResourceNode
    class xResourceNode extends TreeNode

### Remarks

### Examples

### Methods

| Method                                                                   | Description |
|--------------------------------------------------------------------------|-------------|
| public BinData AOTGetData()                                              |             |
| public Image AOTGetImage()                                               |             |
| public str changedBy(\[str value\])                                      |             |
| public Date changedDate(\[Date value\])                                  |             |
| public str changedTime(\[str value\])                                    |             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) |             |
| public str createdBy(\[str value\])                                      |             |
| public Date creationDate(\[Date value\])                                 |             |
| public str creationTime(\[str value\])                                   |             |
| public str filename(\[str value\])                                       |             |
| public str helpText(\[str value\])                                       |             |
| public str label(\[str value\])                                          |             |
| public str name(\[str value\])                                           |             |
| public Guid origin(\[Guid value\])                                       |             |
| ::public static Image AOTCreateImage(str imageName)                      |             |
| public void AOTSetData(BinData data)                                     |             |
| public void AOTSetImage(Image image)                                     |             |

### Method AOTGetData

    public BinData AOTGetData()

#### Return Value

### Method AOTGetImage

    public Image AOTGetImage()

#### Return Value

### Method changedBy

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

### Method changedDate

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

### Method changedTime

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

### Method configurationKey

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

### Method createdBy

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

### Method creationDate

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method filename

    public str filename([str value])

#### Parameters

value  

#### Return Value

### Method helpText

    public str helpText([str value])

#### Parameters

value  

#### Return Value

### Method label

    public str label([str value])

#### Parameters

value  

#### Return Value

### Method name

    public str name([str value])

#### Parameters

value  

#### Return Value

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method AOTCreateImage

    public static Image AOTCreateImage(str imageName)

#### Parameters

imageName  

#### Return Value

### Method AOTSetData

    public void AOTSetData(BinData data)

#### Parameters

data  

### Method AOTSetImage

    public void AOTSetImage(Image image)

#### Parameters

image  

## Class xSession
    class xSession extends Object

Gets information about Microsoft Dynamics AX sessions.

### Remarks

To get information about the current session, create a new xSession session without parameters. The only way to get information about all active sessions (AOS only) is to traverse from session ID 1 to xSession.maxSessionId. The IDs are not an unbroken list, but will never exceed the maximum number of sessions as specified in the maxSessionId method.

### Examples

The following example creates a new xSession object, and then uses it to find the name of the server for the current session.

    xSession xSession; 
    xSession = new xSession();   
    // Prints the name of server for the current session. 
    print xSession.AOSName();

### Methods

| Method                                                                            | Description                                                                                                                    |
|-----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| public str AOSName()                                                              | Retrieves the name of the Application Object Server (AOS) that is responsible for servicing the session.                       |
| public str clientComputerName()                                                   | Retrieves the network name of the client computer that is responsible for servicing the session.                               |
| public ClientType clientKind()                                                    | Retrieves the type of the client that is responsible for servicing the session.                                                |
| public str databaseSpid()                                                         | Retrieves a comma-separated list of active connection IDs.                                                                     |
| public str documentationLanguage()                                                | Retrieves the language ID of the documentation that is shown for the session.                                                  |
| public str interfaceLanguage()                                                    | Retrieves the ID for the language that is used on menus and dialogs for the session.                                           |
| public boolean isWorkerThread()                                                   | Determines whether the session is a worker thread.                                                                             |
| public Date loginDate()                                                           | Retrieves the date on which the user of the session logged on.                                                                 |
| public DateTime loginDateTime()                                                   |                                                                                                                                |
| public TimeOfDay loginTime()                                                      | Retrieves the time at which the user of the session logged on.                                                                 |
| public int masterSessionId()                                                      | Retrieves the master session ID for the session that the xSession object covers.                                               |
| public int serverId()                                                             |                                                                                                                                |
| public int sessionId()                                                            | Retrieves the session ID of the session that the xSession object covers.                                                       |
| public boolean terminate(\[Date loginDate\], \[TimeOfDay loginTime\])             | Terminates the session ID that the object was instantiated with.                                                               |
| public UserId userId()                                                            | Retrieves the user ID that this session is logged on with.                                                                     |
| ::public static int currentRetryCount()                                           | Counts the number of times a try block has been retried after a deadlock, an update conflict, or another exception.            |
| ::public static Uncheck currentUnCheck()                                          |                                                                                                                                |
| ::public static str getDbSchema()                                                 | Retrieves the schema part of the database object name for the session.                                                         |
| ::public static COM getIISObject(IISObject object)                                | Instantiates and returns a COM object for an IIS object.                                                                       |
| ::public static boolean getSysTraceActive()                                       | Enables you to determine whether system tracing is turned on for the session.                                                  |
| ::public static str getXRefAssembyTempFolder()                                    |                                                                                                                                |
| ::public static boolean isCLRSession()                                            |                                                                                                                                |
| ::public static boolean isUserPreferredTzSameAsLocalMachine()                     |                                                                                                                                |
| ::public static int lastDuplicateKeyViolatingTable()                              |                                                                                                                                |
| ::public static int lastUpdateConflictingTable()                                  | Retrieves an instance of the table that most recently had an update conflict.                                                  |
| ::public static int maxSessionId()                                                | Retrieves the maximum number of sessions that are permitted by the current license codes.                                      |
| ::public static int numSession()                                                  | Retrieves the current number of registered sessions.                                                                           |
| public PreferredLocale preferredLocale()                                          |                                                                                                                                |
| ::public static int pseudoBandwidth(\[int bandwidth\])                            | Determines whether bandwidth simulation is turned on for the session, and enables bandwidth simulation to be turned on or off. |
| ::public static int pseudoLatency(\[int latency\])                                | Determines whether latency simulation is turned on for the session, and enables latency simulation to be turned on or off.     |
| ::public static int pseudoSimMode(\[int simMode\])                                | Determines whether delay simulation is turned on for the session, and enables delay simulation to be turned on or off.         |
| ::public static int systemSessionId()                                             | Retrieves the system session ID for the session that the xSession object covers.                                               |
| ::public static container xppCallStack()                                          | Retrieves the current call stack.                                                                                              |
| ::public static void removeAOC()                                                  | Removes the Application Object Server client-side cache (AOC) for the current session.                                         |
| ::public static void updateAOC()                                                  | Updates the Application Object Server client-side cache (AOC) for the current session.                                         |
| ::public static void setAutoUpdateRecVersion(boolean autoUpdateRecVersion)        |                                                                                                                                |
| ::public static void setSysTraceActive(boolean nValue)                            | Switches system tracing on or off.                                                                                             |
| ::private static void clientSetAutoUpdateRecVersion(boolean autoUpdateRecVersion) |                                                                                                                                |
| ::private static void serverSetAutoUpdateRecVersion(boolean autoUpdateRecVersion) |                                                                                                                                |
| public void new(\[int sessionId\], \[boolean checkSession\])                      | Instantiates the xSession object, either for current session or for the session ID passed in as a parameter.                   |
| ::public static void reloadTableCollectionOnClient()                              |                                                                                                                                |

### Method AOSName

Retrieves the name of the Application Object Server (AOS) that is responsible for servicing the session.

    public str AOSName()

#### Return Value

A string that indicates the name of the AOS.

#### Remarks

For non–AOS connected clients, this method returns an empty string.

#### Examples

The following example prints the name of the AOS that is running the current session.

    xSession xSession; 
    xSession = new xSession(); 
    // Prints the name of server for the current session. 
    print xSession.AOSName();

### Method clientComputerName

Retrieves the network name of the client computer that is responsible for servicing the session.

    public str clientComputerName()

#### Return Value

A string that indicates the name of the client computer.

#### Examples

The following example prints the name of the client that is running the current session.

    { 
        xSession xSession; 
        xSession = new xSession(); 
        print xSession.clientComputerName(); 
        pause; 
    }

### Method clientKind

Retrieves the type of the client that is responsible for servicing the session.

    public ClientType clientKind()

#### Return Value

The type of the client.

#### Remarks

The possible values are those in the ClientType system enumeration:

-   COMObject
-   Client
-   Server
-   WorkerThread

#### Examples

The following example prints the type of the client that is running the current session.

    { 
        xSession xSession; 
        xSession = new xSession(); 
        print xSession.clientKind(); 
        pause; 
    }

### Method databaseSpid

Retrieves a comma-separated list of active connection IDs.

    public str databaseSpid()

#### Return Value

A comma-separated list of active connection IDs.

#### Remarks

This method is used to populate the Online users form (SysUsersOnline). To retrieve the number of active connections, use xSession::numSession.

### Method documentationLanguage

Retrieves the language ID of the documentation that is shown for the session.

    public str documentationLanguage()

#### Return Value

A string that contains the ID of the language that is used for the documentation in the session.

#### Remarks

For example, this method returns "en-us" if the language is set to US English. The documentation language can be selected separately and is not necessarily identical to the language used in menus and dialogs. To retrieve the language ID for menus and dialogs, use xSession.interfaceLanguage. xInfo.documentationLanguage enables you to set the documentation language.

### Method interfaceLanguage

Retrieves the ID for the language that is used on menus and dialogs for the session.

    public str interfaceLanguage()

#### Return Value

A string that contains the ID of the language used on menus and dialogs in the session.

#### Remarks

For example, this method returns "en-us" if the language is set to US English. The documentation language can be selected separately and is not necessarily identical to the language used in menus and dialogs. To retrieve the language ID for documentation, use .

### Method isWorkerThread

Determines whether the session is a worker thread.

    public boolean isWorkerThread()

#### Return Value

true if the session is a worker thread; otherwise, false.

#### Remarks

A worker thread is an instance of the Thread class, which creates a new instance of Microsoft Dynamics AX without UI. If this method is called inside such a session, it will return true.

### Method loginDate

Retrieves the date on which the user of the session logged on.

    public Date loginDate()

#### Return Value

The date that the user of the session logged on.

### Method loginDateTime

    public DateTime loginDateTime()

#### Return Value

### Method loginTime

Retrieves the time at which the user of the session logged on.

    public TimeOfDay loginTime()

#### Return Value

The time that the user of the session logged on.

### Method masterSessionId

Retrieves the master session ID for the session that the xSession object covers.

    public int masterSessionId()

#### Return Value

An integer that represents the session ID.

#### Remarks

Some sessions have a master session ID, such as a COM session or a worker thread session.

#### Examples

The following example creates an xSession object by using the normal session ID (or the master session ID, if there is one).

    static xSession getThisSession() 
    { 
        xSession xSession = new xSession(sessionid()); 
        if (xSession.masterSessionId()) 
        { 
            xSession = new xSession(xSession.masterSessionId()); 
        } 
        return xSession; 
    }

### Method serverId

    public int serverId()

#### Return Value

### Method sessionId

Retrieves the session ID of the session that the xSession object covers.

    public int sessionId()

#### Return Value

An integer that represents the session ID.

### Method terminate

Terminates the session ID that the object was instantiated with.

    public boolean terminate([Date loginDate], [TimeOfDay loginTime])

#### Parameters

loginDate  
The time that the user of the session logged on; optional.

<!-- -->

loginTime  
The time that the user of the session logged on; optional.

#### Return Value

false if the user is not authorized to perform this function; otherwise, true.

#### Remarks

This API has a built-in authorization check that is invoked at run time. An exception is thrown if calls to the terminate method are made by users who do not have access to the development security key (SysDevelopment). The optional parameters allow you to put a timestamp on the session to ensure that it is the session you intend to terminate. The same session ID could be used at two different times. The terminate method is used in the Online users form to allow administrators to terminate sessions. An administrator might decide to terminate a session because it has stopped responding, is consuming a lot of resources, or its license needs to be freed for another user.

#### Examples

The following example confirms whether the user has permission to terminate the session. If so, the session is terminated.

    server static public void Main(Args _args) 
    { 
        Session session; 
        session = new Session(); 
        if (session) 
        { 
            session.terminate(); 
        } 
    }

### Method userId

Retrieves the user ID that this session is logged on with.

    public UserId userId()

#### Return Value

The ID for the user of the session.

#### Examples

The following example determines whether a particular user is online.

    server static boolean isUserOnline(userId userId) 
    { 
        xSession    session; 
        int counter; 
        int maxSessions = Info::licensedUsersTotal(); 
        if (!userId) 
        { 
            return false; 
        } 
        for(counter = 1; counter < maxSessions;counter++) 
        { 
            session = new xSession(counter, true); 
            if(session && session.userId() == userId) 
            { 
                return true; 
            } 
        } 
        return false; 
    }

### Method currentRetryCount

Counts the number of times a try block has been retried after a deadlock, an update conflict, or another exception.

    public static int currentRetryCount()

#### Return Value

The number of times that the try block has been retried.

#### Examples

The following example uses the currentRetryCount method to test how many times that a transaction has been retried to determine the exception handling for a CUD transaction.

    catch (Exception::UpdateConflict) 
        { 
            if (appl.ttsLevel() == 0) 
            { 
                if (xSession::currentRetryCount() >= #RetryNum) 
                { 
                    throw Exception::UpdateConflictNotRecovered; 
                } 
                else 
                { 
                    retry; 
                } 
            } 
            else 
            { 
                throw Exception::UpdateConflict; 
            } 
        }

### Method currentUnCheck

    public static Uncheck currentUnCheck()

#### Return Value

### Method getDbSchema

Retrieves the schema part of the database object name for the session.

    public static str getDbSchema()

#### Return Value

Returns the schema part of the database object name.

### Method getIISObject

Instantiates and returns a COM object for an IIS object.

    public static COM getIISObject(IISObject object)

#### Parameters

object  
The IIS object that you want to create a COM object for.

#### Return Value

A COM object.

#### Remarks

The IIS object can be one of the possible values supplied by the IISObject system enumeration:

-   ApplicationObject
-   Request
-   Response
-   Server
-   SessionObject

### Method getSysTraceActive

Enables you to determine whether system tracing is turned on for the session.

    public static boolean getSysTraceActive()

#### Return Value

true if system tracing is active; otherwise, false.

#### Remarks

To turn on system tracing, use xSession::setSysTraceActive.

#### Examples

The following example uses the getSysTraceActive method to determine the original setting for system tracing and to reset the setting after tracing is temporarily set to false.

    server static void main(Args a) 
    { 
        SysDataImport sysDataImport; 
        boolean       sysTraceActive = xSession::getSysTraceActive(); 
        sysDataImport = SysDataImport::newTmpFilename(''); 
        sysDataImport.addTmpExpImpTable( 
            tablenum(SysTraceTableSQL), 
            false); 
        sysDataImport.addTmpExpImpTable( 
            tablenum(SysTraceTableSQLExecPlan), 
            false); 
        sysDataImport.addTmpExpImpTable( 
            tablenum(SysTraceTableSQLTabRef), 
            false); 
        xSession::setSysTraceActive(FALSE); 
        if (sysDataImport.prompt()) 
            sysDataImport.run(); 
        xSession::setSysTraceActive(sysTraceActive); 
    }

### Method getXRefAssembyTempFolder

    public static str getXRefAssembyTempFolder()

#### Return Value

### Method isCLRSession

    public static boolean isCLRSession()

#### Return Value

### Method isUserPreferredTzSameAsLocalMachine

    public static boolean isUserPreferredTzSameAsLocalMachine()

#### Return Value

### Method lastDuplicateKeyViolatingTable

    public static int lastDuplicateKeyViolatingTable()

#### Return Value

### Method lastUpdateConflictingTable

Retrieves an instance of the table that most recently had an update conflict.

    public static int lastUpdateConflictingTable()

#### Return Value

An instance of the table that most recently had an update conflict.

#### Examples

The following example demonstrates the general use of the lastUpdateConflictingTable method—it enables you to abort or retry transactions according to which table has an update conflict.

    try 
    { 
        // ... 
        table1.update(); 
        // ... 
        table2.update(); 
    } 
    catch(Exception::UpdateConflict) 
    { 
        if(xSession::lastUpdateConflictingTable() == table1) 
        { 
            ttsabort; 
        } 
        else if(xSession::lastUpdateConflictingTable() == table2) 
        { 
            // Compensate here. 
            // ... 
            retry; 
        } 
    }

### Method maxSessionId

Retrieves the maximum number of sessions that are permitted by the current license codes.

    public static int maxSessionId()

#### Return Value

An integer that indicates the maximum number of sessions that are permitted by the current license code.

### Method numSession

Retrieves the current number of registered sessions.

    public static int numSession()

#### Return Value

An integer that indicates the number of currently registered sessions.

### Method preferredLocale

    public PreferredLocale preferredLocale()

#### Return Value

### Method pseudoBandwidth

Determines whether bandwidth simulation is turned on for the session, and enables bandwidth simulation to be turned on or off.

    public static int pseudoBandwidth([int bandwidth])

#### Parameters

bandwidth  
Turns bandwidth simulation on or off. Set to zero to turn simulation off. Other values turn simulation on.

#### Return Value

An integer that indicates whether bandwidth simulation is turned on. If the return value is zero, there is no bandwidth simulation.

#### Remarks

You can run pseudo simulations of remote connections from the System monitoring tool:

-   On the toolbar, select Tools, point to Development tools, point to System monitoring, and then click the Remote connection tab.

### Method pseudoLatency

Determines whether latency simulation is turned on for the session, and enables latency simulation to be turned on or off.

    public static int pseudoLatency([int latency])

#### Parameters

latency  
Turns latency simulation on or off. Set to zero to turn simulation off. Other values turn simulation on.

#### Return Value

An integer that indicates whether latency simulation is turned on. If the return value is zero, there is no latency simulation.

#### Remarks

You can run pseudo simulations of remote connections from the System monitoring tool:

-   On the toolbar, select Tools, point to Development tools, point to System monitoring, and then click the Remote connection tab

### Method pseudoSimMode

Determines whether delay simulation is turned on for the session, and enables delay simulation to be turned on or off.

    public static int pseudoSimMode([int simMode])

#### Parameters

simMode  
Turns delay simulation on or off. Set to zero to turn simulation off. Set to 1 to simulate delays for application calls. Set to 2 to simulate delays for all calls.

#### Return Value

An integer that indicates whether delay simulation is turned on. If the return value is zero, there is no delay simulation. If the return value is 1, delays are simulated only for application-controlled calls. If the return value is 2, delays are simulated for all calls.

#### Remarks

You can run pseudo simulations of remote connections from the System monitoring tool:

-   On the toolbar, select Tools, point to Development tools, point to System monitoring, and then click the Remote connection tab

### Method systemSessionId

Retrieves the system session ID for the session that the xSession object covers.

    public static int systemSessionId()

#### Return Value

An integer that represents the session ID.

#### Remarks

Some sessions, such as a COM session or a worker thread session, have a parent system session.

### Method xppCallStack

Retrieves the current call stack.

    public static container xppCallStack()

#### Return Value

A container that holds the contents of the current call stack.

### Method removeAOC

Removes the Application Object Server client-side cache (AOC) for the current session.

    public static void removeAOC()

### Method updateAOC

Updates the Application Object Server client-side cache (AOC) for the current session.

    public static void updateAOC()

#### Remarks

AOC is a client-side cache that consists of metadata that is loaded by the client, and then saved to disk when the client is closed. It is saved under the user’s local settings folder. The file has an .auc filename extension and is saved in a user's Local Settings folder. When the client is started, it reads from the cache, and then deletes the cache from the disk.

### Method setAutoUpdateRecVersion

    public static void setAutoUpdateRecVersion(boolean autoUpdateRecVersion)

#### Parameters

autoUpdateRecVersion  

### Method setSysTraceActive

Switches system tracing on or off.

    public static void setSysTraceActive(boolean nValue)

#### Parameters

nValue  
A Boolean value that determines whether tracing should be switched on or off. Set to true to switch tracing on.

#### Examples

The following example uses the setSysTraceActive method to turn system tracing off when data is imported.

    server static void main(Args a) 
    { 
        SysDataImport sysDataImport; 
        boolean       sysTraceActive = xSession::getSysTraceActive(); 
        sysDataImport = SysDataImport::newTmpFilename(''); 
        sysDataImport.addTmpExpImpTable( 
            tablenum(SysTraceTableSQL), 
            false); 
        sysDataImport.addTmpExpImpTable( 
            tablenum(SysTraceTableSQLExecPlan), 
            false); 
        sysDataImport.addTmpExpImpTable( 
            tablenum(SysTraceTableSQLTabRef), 
            false); 
        xSession::setSysTraceActive(FALSE); 
        if (sysDataImport.prompt()) 
            sysDataImport.run(); 
        xSession::setSysTraceActive(sysTraceActive); 
    }

### Method clientSetAutoUpdateRecVersion

    private static void clientSetAutoUpdateRecVersion(boolean autoUpdateRecVersion)

#### Parameters

autoUpdateRecVersion  

### Method serverSetAutoUpdateRecVersion

    private static void serverSetAutoUpdateRecVersion(boolean autoUpdateRecVersion)

#### Parameters

autoUpdateRecVersion  

### Method new

Instantiates the xSession object, either for current session or for the session ID passed in as a parameter.

    public void new([int sessionId], [boolean checkSession])

#### Parameters

sessionId  
A boolean flag that, if set to true, checks to determine whether the session specified by the \_SessionId parameter exists. The operation that checks whether a session exists might use a lot of system resources. This parameter is therefore set to false by default.

<!-- -->

checkSession  
A boolean flag that, if set to true, checks to determine whether the session specified by the \_SessionId parameter exists. The operation that checks whether a session exists might use a lot of system resources. This parameter is therefore set to false by default.

#### Examples

The following example returns a count of all the active sessions.

    server static Integer getAllOnlineUserCount() 
    { 
        int      counter; 
        int      num = 0; 
        int      maxSessions = Info::licensedUsersTotal(); 
        xSession session; 
        UserInfo userInfo; 
        for(counter = 1; counter < maxSessions;counter++) 
        { 
            session = new xSession(counter, true); 
            if(session && session.userId()) 
            { 
                select firstonly userInfo 
                    where userInfo.Id == session.userId(); 
                if (userInfo) 
                    num++; 
            } 
        } 
        return num; 
    }

### Method reloadTableCollectionOnClient

    public static void reloadTableCollectionOnClient()

## Class xSqlEnumerator
    class xSqlEnumerator extends Object

### Remarks

### Examples

### Methods

| Method                                               | Description                                             |
|------------------------------------------------------|---------------------------------------------------------|
| public str getConnStr(str database)                  |                                                         |
| public List getDatabases(str server, \[str driver\]) |                                                         |
| public List getServers(str driver)                   |                                                         |
| public void new()                                    | Initializes a new instance of the xSqlEnumerator class. |

### Method getConnStr

    public str getConnStr(str database)

#### Parameters

database  

#### Return Value

### Method getDatabases

    public List getDatabases(str server, [str driver])

#### Parameters

server  

<!-- -->

driver  

#### Return Value

### Method getServers

    public List getServers(str driver)

#### Parameters

driver  

#### Return Value

### Method new

Initializes a new instance of the xSqlEnumerator class.

    public void new()

## Class xToastNotification
    class xToastNotification extends Object

### Remarks

### Examples

### Methods

| Method                                      | Description                                                 |
|---------------------------------------------|-------------------------------------------------------------|
| public int duration(\[int duration\])       |                                                             |
| public int imageResId(\[int imageResId\])   |                                                             |
| public str messageText(\[str messageText\]) |                                                             |
| public str subject(\[str subject\])         |                                                             |
| public void new()                           | Initializes a new instance of the xToastNotification class. |
| public void onClosed()                      |                                                             |
| public void show()                          |                                                             |
| public void finalize()                      |                                                             |
| public void onClicked()                     |                                                             |

### Method duration

    public int duration([int duration])

#### Parameters

duration  

#### Return Value

### Method imageResId

    public int imageResId([int imageResId])

#### Parameters

imageResId  

#### Return Value

### Method messageText

    public str messageText([str messageText])

#### Parameters

messageText  

#### Return Value

### Method subject

    public str subject([str subject])

#### Parameters

subject  

#### Return Value

### Method new

Initializes a new instance of the xToastNotification class.

    public void new()

### Method onClosed

    public void onClosed()

### Method show

    public void show()

### Method finalize

    public void finalize()

### Method onClicked

    public void onClicked()

## Class xVersionControl
    class xVersionControl extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                                                            | Description                                              |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| public boolean allowCreate(TreeNode node)                                                                                                                         |                                                          |
| public boolean allowDelete(TreeNode node)                                                                                                                         |                                                          |
| public boolean allowEdit(TreeNode node)                                                                                                                           |                                                          |
| public boolean allowRename(TreeNode node)                                                                                                                         |                                                          |
| public boolean checkOut(TreeNode node)                                                                                                                            |                                                          |
| public boolean create(TreeNode node)                                                                                                                              |                                                          |
| public boolean delete(TreeNode node)                                                                                                                              |                                                          |
| public int getAvailableId(UtilElementType objectType, UtilEntryLevel layer, \[int parentId\], \[IdAllocationSchema idAllocationSchema\], \[boolean inheritance\]) |                                                          |
| public int getAvailableLabelId(str labelFile, str language, \[IdAllocationSchema idAllocationSchema\])                                                            |                                                          |
| public boolean ideIntegration()                                                                                                                                   |                                                          |
| public boolean moveToModel(TreeNode node, int modelId)                                                                                                            |                                                          |
| public boolean rename(TreeNode node, str newname)                                                                                                                 |                                                          |
| public boolean undoCheckOut(TreeNode node, \[boolean showDialog\])                                                                                                |                                                          |
| public Set unwantedObjectTypes()                                                                                                                                  |                                                          |
| public void colorAOT()                                                                                                                                            |                                                          |
| public void save(TreeNode node)                                                                                                                                   |                                                          |
| public void showHistory(TreeNode node)                                                                                                                            |                                                          |
| public void updateCheckedOutList(Set checkedOutObjects)                                                                                                           |                                                          |
| public void getLatestVersion(\[TreeNode node\], \[boolean delLocalFiles\])                                                                                        |                                                          |
| public void checkIn(TreeNode node)                                                                                                                                |                                                          |
| public void new()                                                                                                                                                 | Initializes a new instance of the xVersionControl class. |
| public void reload()                                                                                                                                              |                                                          |
| public void getLabelVersion(\[TreeNode node\], \[str label\])                                                                                                     |                                                          |

### Method allowCreate

    public boolean allowCreate(TreeNode node)

#### Parameters

node  

#### Return Value

### Method allowDelete

    public boolean allowDelete(TreeNode node)

#### Parameters

node  

#### Return Value

### Method allowEdit

    public boolean allowEdit(TreeNode node)

#### Parameters

node  

#### Return Value

### Method allowRename

    public boolean allowRename(TreeNode node)

#### Parameters

node  

#### Return Value

### Method checkOut

    public boolean checkOut(TreeNode node)

#### Parameters

node  

#### Return Value

### Method create

    public boolean create(TreeNode node)

#### Parameters

node  

#### Return Value

### Method delete

    public boolean delete(TreeNode node)

#### Parameters

node  

#### Return Value

### Method getAvailableId

    public int getAvailableId(UtilElementType objectType, UtilEntryLevel layer, [int parentId], [IdAllocationSchema idAllocationSchema], [boolean inheritance])

#### Parameters

objectType  

<!-- -->

layer  

<!-- -->

parentId  

<!-- -->

idAllocationSchema  

<!-- -->

inheritance  

#### Return Value

### Method getAvailableLabelId

    public int getAvailableLabelId(str labelFile, str language, [IdAllocationSchema idAllocationSchema])

#### Parameters

labelFile  

<!-- -->

language  

<!-- -->

idAllocationSchema  

#### Return Value

### Method ideIntegration

    public boolean ideIntegration()

#### Return Value

### Method moveToModel

    public boolean moveToModel(TreeNode node, int modelId)

#### Parameters

node  

<!-- -->

modelId  

#### Return Value

### Method rename

    public boolean rename(TreeNode node, str newname)

#### Parameters

node  

<!-- -->

newname  

#### Return Value

### Method undoCheckOut

    public boolean undoCheckOut(TreeNode node, [boolean showDialog])

#### Parameters

node  

<!-- -->

showDialog  

#### Return Value

### Method unwantedObjectTypes

    public Set unwantedObjectTypes()

#### Return Value

### Method colorAOT

    public void colorAOT()

### Method save

    public void save(TreeNode node)

#### Parameters

node  

### Method showHistory

    public void showHistory(TreeNode node)

#### Parameters

node  

### Method updateCheckedOutList

    public void updateCheckedOutList(Set checkedOutObjects)

#### Parameters

checkedOutObjects  

### Method getLatestVersion

    public void getLatestVersion([TreeNode node], [boolean delLocalFiles])

#### Parameters

node  

<!-- -->

delLocalFiles  

### Method checkIn

    public void checkIn(TreeNode node)

#### Parameters

node  

### Method new

Initializes a new instance of the xVersionControl class.

    public void new()

### Method reload

    public void reload()

### Method getLabelVersion

    public void getLabelVersion([TreeNode node], [str label])

#### Parameters

node  

<!-- -->

label  



