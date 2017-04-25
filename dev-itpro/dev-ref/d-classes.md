---
# required metadata

title: D Classes
description: System API classes that start with the letter D.
author: RobinARH
manager: AnnBe
ms.date: 04/04/2017
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
ms.custom: 52531
ms.assetid: 97f18d4d-1704-40fd-a0a2-2624a5798d66
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# D Classes

[!include[banner](../includes/banner.md)]


System API classes that start with the letter D.

Class DataEntityDataSourceRuntimeContext
----------------------------------------

    class DataEntityDataSourceRuntimeContext extends Object

### Remarks

### Examples

### Methods

| Method                                                                         | Description |
|--------------------------------------------------------------------------------|-------------|
| public str name()                                                              |             |
| public int id()                                                                |             |
| public Common getBuffer()                                                      |             |
| public DataEntityDatabaseOperation getDatabaseOperation()                      |             |
| public str getCompany()                                                        |             |
| public boolean getDataSaved()                                                  |             |
| public boolean skipDataMethods(\[boolean skip\])                               |             |
| public boolean skipDeleteMethod(\[boolean b\])                                 |             |
| public boolean skipValidateWrite(\[boolean skip\])                             |             |
| public boolean skipValidateDelete(\[boolean skip\])                            |             |
| public boolean skipInitValue(\[boolean skip\])                                 |             |
| public boolean skipDefaultRow(\[boolean skip\])                                |             |
| public boolean readOnly()                                                      |             |
| public boolean oneToMany()                                                     |             |
| public boolean optional()                                                      |             |
| public boolean dateEffective()                                                 |             |
| public boolean conflictDetectionInvoked(\[boolean found\])                     |             |
| public void new(Common dataSourceBuffer, str dataSourceName, int dataSourceId) |             |
| public void setCompany(str company)                                            |             |
| public void setBuffer(Common buffer)                                           |             |
| public void setDatabaseOperation(DataEntityDatabaseOperation dbOperation)      |             |
| public void setDataSaved(boolean saved)                                        |             |

### Method name

    public str name()

#### Return Value

### Method id

    public int id()

#### Return Value

### Method getBuffer

    public Common getBuffer()

#### Return Value

### Method getDatabaseOperation

    public DataEntityDatabaseOperation getDatabaseOperation()

#### Return Value

### Method getCompany

    public str getCompany()

#### Return Value

### Method getDataSaved

    public boolean getDataSaved()

#### Return Value

### Method skipDataMethods

    public boolean skipDataMethods([boolean skip])

#### Parameters

skip  

#### Return Value

### Method skipDeleteMethod

    public boolean skipDeleteMethod([boolean b])

#### Parameters

b  

#### Return Value

### Method skipValidateWrite

    public boolean skipValidateWrite([boolean skip])

#### Parameters

skip  

#### Return Value

### Method skipValidateDelete

    public boolean skipValidateDelete([boolean skip])

#### Parameters

skip  

#### Return Value

### Method skipInitValue

    public boolean skipInitValue([boolean skip])

#### Parameters

skip  

#### Return Value

### Method skipDefaultRow

    public boolean skipDefaultRow([boolean skip])

#### Parameters

skip  

#### Return Value

### Method readOnly

    public boolean readOnly()

#### Return Value

### Method oneToMany

    public boolean oneToMany()

#### Return Value

### Method optional

    public boolean optional()

#### Return Value

### Method dateEffective

    public boolean dateEffective()

#### Return Value

### Method conflictDetectionInvoked

    public boolean conflictDetectionInvoked([boolean found])

#### Parameters

found  

#### Return Value

### Method new

    public void new(Common dataSourceBuffer, str dataSourceName, int dataSourceId)

#### Parameters

dataSourceBuffer  

<!-- -->

dataSourceName  

<!-- -->

dataSourceId  

### Method setCompany

    public void setCompany(str company)

#### Parameters

company  

### Method setBuffer

    public void setBuffer(Common buffer)

#### Parameters

buffer  

### Method setDatabaseOperation

    public void setDatabaseOperation(DataEntityDatabaseOperation dbOperation)

#### Parameters

dbOperation  

### Method setDataSaved

    public void setDataSaved(boolean saved)

#### Parameters

saved  

## Class DataEntityPersister
    class DataEntityPersister extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                                                            | Description |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| public boolean doSaveDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                             |             |
| public Common doFindDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                              |             |
| public boolean hasDataSourceRecordChanged(int dataSourceId, Common originalRecord, Common updatedRecord)                                                                                                          |             |
| public str getCompanyForDataSource(DataEntityRuntimeContext entityCtx, int dataSourceId)                                                                                                                          |             |
| public int getValidTimeStateUpdateModeForDataSource(DataEntityRuntimeContext entityCtx, int dataSourceId)                                                                                                         |             |
| public Common findDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                                |             |
| public boolean saveDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                               |             |
| public void doMapEntityToDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                         |             |
| public void mapEntityToDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                           |             |
| public void doMapDataSourceToEntity(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                         |             |
| public void selectDataSourceBufferByRecId(Common dataSourceBuffer, Int64 dataSourceRecId, Boolean explicitlyForUpdate, Boolean fetchActiveRecordOnly)                                                             |             |
| public void doPersistEntity(DataEntityRuntimeContext entityCtx)                                                                                                                                                   |             |
| public void doInitializeDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                          |             |
| public void initializeDataSource(DataEntityRuntimeContext entityCtx, str dataSourceName, Common dataSourceBuffer, int dataSourceId, Boolean optional, Boolean readonly, Boolean oneToMany, Boolean dateEffective) |             |

### Method doSaveDataSource

    public boolean doSaveDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)

#### Parameters

entityCtx  

<!-- -->

dataSourceCtx  

#### Return Value

### Method doFindDataSource

    public Common doFindDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)

#### Parameters

entityCtx  

<!-- -->

dataSourceCtx  

#### Return Value

### Method hasDataSourceRecordChanged

    public boolean hasDataSourceRecordChanged(int dataSourceId, Common originalRecord, Common updatedRecord)

#### Parameters

dataSourceId  

<!-- -->

originalRecord  

<!-- -->

updatedRecord  

#### Return Value

### Method getCompanyForDataSource

    public str getCompanyForDataSource(DataEntityRuntimeContext entityCtx, int dataSourceId)

#### Parameters

entityCtx  

<!-- -->

dataSourceId  

#### Return Value

### Method getValidTimeStateUpdateModeForDataSource

    public int getValidTimeStateUpdateModeForDataSource(DataEntityRuntimeContext entityCtx, int dataSourceId)

#### Parameters

entityCtx  

<!-- -->

dataSourceId  

#### Return Value

### Method findDataSource

    public Common findDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)

#### Parameters

entityCtx  

<!-- -->

dataSourceCtx  

#### Return Value

### Method saveDataSource

    public boolean saveDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)

#### Parameters

entityCtx  

<!-- -->

dataSourceCtx  

#### Return Value

### Method doMapEntityToDataSource

    public void doMapEntityToDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)

#### Parameters

entityCtx  

<!-- -->

dataSourceCtx  

### Method mapEntityToDataSource

    public void mapEntityToDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)

#### Parameters

entityCtx  

<!-- -->

dataSourceCtx  

### Method doMapDataSourceToEntity

    public void doMapDataSourceToEntity(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)

#### Parameters

entityCtx  

<!-- -->

dataSourceCtx  

### Method selectDataSourceBufferByRecId

    public void selectDataSourceBufferByRecId(Common dataSourceBuffer, Int64 dataSourceRecId, Boolean explicitlyForUpdate, Boolean fetchActiveRecordOnly)

#### Parameters

dataSourceBuffer  

<!-- -->

dataSourceRecId  

<!-- -->

explicitlyForUpdate  

<!-- -->

fetchActiveRecordOnly  

### Method doPersistEntity

    public void doPersistEntity(DataEntityRuntimeContext entityCtx)

#### Parameters

entityCtx  

### Method doInitializeDataSource

    public void doInitializeDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)

#### Parameters

entityCtx  

<!-- -->

dataSourceCtx  

### Method initializeDataSource

    public void initializeDataSource(DataEntityRuntimeContext entityCtx, str dataSourceName, Common dataSourceBuffer, int dataSourceId, Boolean optional, Boolean readonly, Boolean oneToMany, Boolean dateEffective)

#### Parameters

entityCtx  

<!-- -->

dataSourceName  

<!-- -->

dataSourceBuffer  

<!-- -->

dataSourceId  

<!-- -->

optional  

<!-- -->

readonly  

<!-- -->

oneToMany  

<!-- -->

dateEffective  

## Class DataEntityRuntimeContext
    class DataEntityRuntimeContext extends Object

### Remarks

### Examples

### Methods

| Method                                                                                               | Description |
|------------------------------------------------------------------------------------------------------|-------------|
| public DataEntityDatabaseOperation getDatabaseOperation()                                            |             |
| public AnyType getCustomProperty(str name)                                                           |             |
| public Common getEntityRecord()                                                                      |             |
| public DataEntityDataSourceRuntimeContext getRuntimeContextByName(str datasourceName)                |             |
| public void new(DataEntityDatabaseOperation operation, Common record, DataEntityPersister persister) |             |
| public void setCustomProperty(str name, AnyType obj)                                                 |             |

### Method getDatabaseOperation

    public DataEntityDatabaseOperation getDatabaseOperation()

#### Return Value

### Method getCustomProperty

    public AnyType getCustomProperty(str name)

#### Parameters

name  

#### Return Value

### Method getEntityRecord

    public Common getEntityRecord()

#### Return Value

### Method getRuntimeContextByName

    public DataEntityDataSourceRuntimeContext getRuntimeContextByName(str datasourceName)

#### Parameters

datasourceName  

#### Return Value

### Method new

    public void new(DataEntityDatabaseOperation operation, Common record, DataEntityPersister persister)

#### Parameters

operation  

<!-- -->

record  

<!-- -->

persister  

### Method setCustomProperty

    public void setCustomProperty(str name, AnyType obj)

#### Parameters

name  

<!-- -->

obj  

## Class DataEventArgs
    class DataEventArgs

### Remarks

### Examples

### Methods

| Method | Description |
|--------|-------------|

## Class DataImportExportManager
    class DataImportExportManager extends Object

### Remarks

### Examples

### Methods

| Method                               | Description |
|--------------------------------------|-------------|
| public void finalize()               |             |
| public void new()                    |             |
| public void importDataFile(str name) |             |

### Method finalize

    public void finalize()

### Method new

    public void new()

### Method importDataFile

    public void importDataFile(str name)

#### Parameters

name  

## Class DataImportManager
    class DataImportManager extends Object

### Remarks

### Examples

### Methods

| Method                                                                                        | Description                                                |
|-----------------------------------------------------------------------------------------------|------------------------------------------------------------|
| ::public static int commitImportSessionInfo(DataImportSessionInfo impInfo)                    |                                                            |
| ::public static int endTableDataCopy(ImportTableDataInfo dataInfo)                            |                                                            |
| ::public static int endTableSchemaCopy(ImportTableSchemaInfo schInfo)                         |                                                            |
| ::public static int finishMergeTableData()                                                    |                                                            |
| ::public static int getImportSessionProgress(DataImportSessionInfo impInfo)                   |                                                            |
| ::public static int mergeAllData()                                                            |                                                            |
| ::public static int mergeTableData(int mergeStep, TableId tableId, boolean updateHeartbeat)   |                                                            |
| ::public static int recoverImportSession(DataImportSessionInfo impInfo, boolean fTryToResume) |                                                            |
| public void new()                                                                             | Initializes a new instance of the DataImportManager class. |

### Method commitImportSessionInfo

    public static int commitImportSessionInfo(DataImportSessionInfo impInfo)

#### Parameters

impInfo  

#### Return Value

### Method endTableDataCopy

    public static int endTableDataCopy(ImportTableDataInfo dataInfo)

#### Parameters

dataInfo  

#### Return Value

### Method endTableSchemaCopy

    public static int endTableSchemaCopy(ImportTableSchemaInfo schInfo)

#### Parameters

schInfo  

#### Return Value

### Method finishMergeTableData

    public static int finishMergeTableData()

#### Return Value

### Method getImportSessionProgress

    public static int getImportSessionProgress(DataImportSessionInfo impInfo)

#### Parameters

impInfo  

#### Return Value

### Method mergeAllData

    public static int mergeAllData()

#### Return Value

### Method mergeTableData

    public static int mergeTableData(int mergeStep, TableId tableId, boolean updateHeartbeat)

#### Parameters

mergeStep  

<!-- -->

tableId  

<!-- -->

updateHeartbeat  

#### Return Value

### Method recoverImportSession

    public static int recoverImportSession(DataImportSessionInfo impInfo, boolean fTryToResume)

#### Parameters

impInfo  

<!-- -->

fTryToResume  

#### Return Value

### Method new

Initializes a new instance of the DataImportManager class.

    public void new()

## Class DataImportSessionInfo
    class DataImportSessionInfo extends Object

### Remarks

### Examples

### Methods

| Method                                                                         | Description                                     |
|--------------------------------------------------------------------------------|-------------------------------------------------|
| public int addImportTable(str szTabName, int ulTableId, boolean fAlwaysUpdate) |                                                 |
| public int getCurrentProgress()                                                |                                                 |
| public str getCurrentTable()                                                   |                                                 |
| public int setSourceGUID(Guid szSourceGUID)                                    |                                                 |
| public int setSysDataImpLogId(int sysDataImpLogId)                             |                                                 |
| public void new(str szInpFileName, boolean fUpdateExistingData)                | Initializes a new instance of the Object class. |

### Method addImportTable

    public int addImportTable(str szTabName, int ulTableId, boolean fAlwaysUpdate)

#### Parameters

szTabName  

<!-- -->

ulTableId  

<!-- -->

fAlwaysUpdate  

#### Return Value

### Method getCurrentProgress

    public int getCurrentProgress()

#### Return Value

### Method getCurrentTable

    public str getCurrentTable()

#### Return Value

### Method setSourceGUID

    public int setSourceGUID(Guid szSourceGUID)

#### Parameters

szSourceGUID  

#### Return Value

### Method setSysDataImpLogId

    public int setSysDataImpLogId(int sysDataImpLogId)

#### Parameters

sysDataImpLogId  

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(str szInpFileName, boolean fUpdateExistingData)

#### Parameters

szInpFileName  

<!-- -->

fUpdateExistingData  

## Class DataSet
    class DataSet extends TreeNode

### Remarks

### Examples

### Methods

| Method                                                  | Description                                                                                                                       |
|---------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| public FormBuildDataSource addDataSource(str name)      |                                                                                                                                   |
| public str changedBy(\[str value\])                     | Gets or sets the name of the user who last changed the application object.                                                        |
| public Date changedDate(\[Date value\])                 | Gets or sets the date an application object was last changed.                                                                     |
| public str changedTime(\[str value\])                   | Gets or sets the time an application object was last changed.                                                                     |
| public str createdBy(\[str value\])                     | Gets or sets the name of the user who created the application object.                                                             |
| public Date creationDate(\[Date value\])                | Gets or sets the date an application object was created.                                                                          |
| public str creationTime(\[str value\])                  |                                                                                                                                   |
| public FormBuildDataSource dataSource(int dataSourceNo) |                                                                                                                                   |
| public int dataSourceCount()                            |                                                                                                                                   |
| public str name(\[str value\])                          | Gets or sets the name used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object. |
| public Guid origin(\[Guid value\])                      |                                                                                                                                   |
| public void load(str name, \[boolean buildMode\])       |                                                                                                                                   |
| public void finalize()                                  |                                                                                                                                   |
| public void new(\[str name\], \[boolean buildMode\])    | Initializes a new instance of the TreeNode class.                                                                                 |
| public void save()                                      |                                                                                                                                   |

### Method addDataSource

    public FormBuildDataSource addDataSource(str name)

#### Parameters

name  

#### Return Value

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

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

### Method dataSource

    public FormBuildDataSource dataSource(int dataSourceNo)

#### Parameters

dataSourceNo  

#### Return Value

### Method dataSourceCount

    public int dataSourceCount()

#### Return Value

### Method name

Gets or sets the name used in code to identify a form, report, table, query, or another Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumeration types, classes, and so on.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method load

    public void load(str name, [boolean buildMode])

#### Parameters

name  

<!-- -->

buildMode  

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the TreeNode class.

    public void new([str name], [boolean buildMode])

#### Parameters

name  

<!-- -->

buildMode  

### Method save

    public void save()

## Class DataSetRun
    class DataSetRun extends ObjectRun

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                              | Description                                                                   |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| public FormDataSource addDataSource(TableId tableId, \[str joinDataSourceName\], \[DataSourceLinkTypePropertyValues linkType\], \[FieldId joinFieldId\], \[str newDataSourceName\]) | Adds a new data source to the dataSetRun class.                               |
| public DataSet dataSet()                                                                                                                                                            |                                                                               |
| public FormObjectSet dataSource(\[AnyType objectSet\])                                                                                                                              |                                                                               |
| public FormObjectSet dataSourceById(int id)                                                                                                                                         |                                                                               |
| public int dataSourceCount()                                                                                                                                                        |                                                                               |
| public Array getActiveFields(int dataSourceId)                                                                                                                                      |                                                                               |
| public container getChildrenById(str dataSourceName, \[AnyType parentId\])                                                                                                          | Gets the children of a data source by using the parent ID.                    |
| public container getChildrenByIndex(str dataSourceName, \[int parentIndex\])                                                                                                        | Gets the children of a data source by using the parent index.                 |
| public DataSetError getLastError()                                                                                                                                                  |                                                                               |
| public AnyType getParentById(str dataSourceName, AnyType childId)                                                                                                                   | Gets the parent of a data source by using the child ID.                       |
| public int getParentByIndex(str dataSourceName, int childIndex)                                                                                                                     | Gets the parent of a data source by using the child index.                    |
| public int getRowIndexFromRowHierarchyId(str dataSourceName, AnyType id)                                                                                                            | Gets the row index on a data source by using a row hierarchy ID.              |
| public boolean initComplete()                                                                                                                                                       |                                                                               |
| public str name()                                                                                                                                                                   |                                                                               |
| public FormObjectSet objectSet(\[AnyType objectSet\])                                                                                                                               |                                                                               |
| public container pack()                                                                                                                                                             | Serializes the current instance of the DataSetRun class.                      |
| public boolean runCalled()                                                                                                                                                          |                                                                               |
| public boolean unpack(container pack)                                                                                                                                               | Deserializes the pack parameter value to an instance of the DataSetRun class. |
| ::public static DataSetRun create(str name, container pack)                                                                                                                         |                                                                               |
| ::public static DataSetRun createRunTime(container pack)                                                                                                                            |                                                                               |
| public void setLastError(DataSetError error)                                                                                                                                        |                                                                               |
| public void run()                                                                                                                                                                   |                                                                               |
| public void setLookupMode()                                                                                                                                                         | Puts the dataset into lookup mode.                                            |
| public void new(xArgs args)                                                                                                                                                         | Initializes a new instance of the Object class.                               |
| public void finalize()                                                                                                                                                              |                                                                               |
| public void createRecord(str formDataSourceName, \[boolean append\])                                                                                                                | Creates a new record.                                                         |
| public void setActiveFields(int dataSourceId, Array fieldIds)                                                                                                                       |                                                                               |
| public void setExternalContext(\[Common externalContext\])                                                                                                                          | Sets the external context on the dataSetRun object.                           |
| public void init()                                                                                                                                                                  |                                                                               |
| public void enableHierarchicalDataBrowsing(str hierarchyPKDataSourceName, FieldId hierarchyPKfieldId, str hierarchyFKDataSourceName, FieldId hierarchyFKfieldId)                    | Enables hierarchical data browsing.                                           |
| public void disableHierarchicalDataBrowsing(str dataSourceName)                                                                                                                     | Disables hierarchical data browsing.                                          |

### Method addDataSource

Adds a new data source to the dataSetRun class.

    public FormDataSource addDataSource(TableId tableId, [str joinDataSourceName], [DataSourceLinkTypePropertyValues linkType], [FieldId joinFieldId], [str newDataSourceName])

#### Parameters

tableId  
The name of the new data source.

<!-- -->

joinDataSourceName  
The name of the new data source.

<!-- -->

linkType  
The name of the new data source.

<!-- -->

joinFieldId  
The name of the new data source.

<!-- -->

newDataSourceName  
The name of the new data source.

#### Return Value

The new data source.

### Method dataSet

    public DataSet dataSet()

#### Return Value

### Method dataSource

    public FormObjectSet dataSource([AnyType objectSet])

#### Parameters

objectSet  

#### Return Value

### Method dataSourceById

    public FormObjectSet dataSourceById(int id)

#### Parameters

id  

#### Return Value

### Method dataSourceCount

    public int dataSourceCount()

#### Return Value

### Method getActiveFields

    public Array getActiveFields(int dataSourceId)

#### Parameters

dataSourceId  

#### Return Value

### Method getChildrenById

Gets the children of a data source by using the parent ID.

    public container getChildrenById(str dataSourceName, [AnyType parentId])

#### Parameters

dataSourceName  
The parent ID.

<!-- -->

parentId  
The parent ID.

#### Return Value

A container for the children.

### Method getChildrenByIndex

Gets the children of a data source by using the parent index.

    public container getChildrenByIndex(str dataSourceName, [int parentIndex])

#### Parameters

dataSourceName  
The parent index.

<!-- -->

parentIndex  
The parent index.

#### Return Value

A container for the children.

### Method getLastError

    public DataSetError getLastError()

#### Return Value

### Method getParentById

Gets the parent of a data source by using the child ID.

    public AnyType getParentById(str dataSourceName, AnyType childId)

#### Parameters

dataSourceName  
The child ID.

<!-- -->

childId  
The child ID.

#### Return Value

The parent ID.

### Method getParentByIndex

Gets the parent of a data source by using the child index.

    public int getParentByIndex(str dataSourceName, int childIndex)

#### Parameters

dataSourceName  
The child index.

<!-- -->

childIndex  
The child index.

#### Return Value

The parent ID.

### Method getRowIndexFromRowHierarchyId

Gets the row index on a data source by using a row hierarchy ID.

    public int getRowIndexFromRowHierarchyId(str dataSourceName, AnyType id)

#### Parameters

dataSourceName  
The row hierarchy ID.

<!-- -->

id  
The row hierarchy ID.

#### Return Value

The row index.

### Method initComplete

    public boolean initComplete()

#### Return Value

### Method name

    public str name()

#### Return Value

### Method objectSet

    public FormObjectSet objectSet([AnyType objectSet])

#### Parameters

objectSet  

#### Return Value

### Method pack

Serializes the current instance of the DataSetRun class.

    public container pack()

#### Return Value

A container that contains the current instance of the DataSetRun class.

### Method runCalled

    public boolean runCalled()

#### Return Value

### Method unpack

Deserializes the pack parameter value to an instance of the DataSetRun class.

    public boolean unpack(container pack)

#### Parameters

pack  
The container from which to deserialize the instance.

#### Return Value

true if deserialization was successful; otherwise, false.

### Method create

    public static DataSetRun create(str name, container pack)

#### Parameters

name  

<!-- -->

pack  

#### Return Value

### Method createRunTime

    public static DataSetRun createRunTime(container pack)

#### Parameters

pack  

#### Return Value

### Method setLastError

    public void setLastError(DataSetError error)

#### Parameters

error  

### Method run

    public void run()

### Method setLookupMode

Puts the dataset into lookup mode.

    public void setLookupMode()

### Method new

Initializes a new instance of the Object class.

    public void new(xArgs args)

#### Parameters

args  

### Method finalize

    public void finalize()

### Method createRecord

Creates a new record.

    public void createRecord(str formDataSourceName, [boolean append])

#### Parameters

formDataSourceName  
The record to append.

<!-- -->

append  
The record to append.

### Method setActiveFields

    public void setActiveFields(int dataSourceId, Array fieldIds)

#### Parameters

dataSourceId  

<!-- -->

fieldIds  

### Method setExternalContext

Sets the external context on the dataSetRun object.

    public void setExternalContext([Common externalContext])

#### Parameters

externalContext  
The external context.

### Method init

    public void init()

### Method enableHierarchicalDataBrowsing

Enables hierarchical data browsing.

    public void enableHierarchicalDataBrowsing(str hierarchyPKDataSourceName, FieldId hierarchyPKfieldId, str hierarchyFKDataSourceName, FieldId hierarchyFKfieldId)

#### Parameters

hierarchyPKDataSourceName  
The ID of the foreign key field in the hierarchy.

<!-- -->

hierarchyPKfieldId  
The ID of the foreign key field in the hierarchy.

<!-- -->

hierarchyFKDataSourceName  
The ID of the foreign key field in the hierarchy.

<!-- -->

hierarchyFKfieldId  
The ID of the foreign key field in the hierarchy.

### Method disableHierarchicalDataBrowsing

Disables hierarchical data browsing.

    public void disableHierarchicalDataBrowsing(str dataSourceName)

#### Parameters

dataSourceName  
The name of the data source to disable hierarchical data browsing on.

## Class DataSourceMethodInfo
    class DataSourceMethodInfo extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                           | Description                                     |
|------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| public DisplayFunctionType displayType()                                                                         |                                                 |
| public boolean isStatic()                                                                                        |                                                 |
| public str name()                                                                                                |                                                 |
| public Types returnType()                                                                                        |                                                 |
| public int returnTypeId()                                                                                        |                                                 |
| public void new(str name, DisplayFunctionType displayType, Types returnType, int returnTypeId, boolean isStatic) | Initializes a new instance of the Object class. |
| public void finalize()                                                                                           |                                                 |

### Method displayType

    public DisplayFunctionType displayType()

#### Return Value

### Method isStatic

    public boolean isStatic()

#### Return Value

### Method name

    public str name()

#### Return Value

### Method returnType

    public Types returnType()

#### Return Value

### Method returnTypeId

    public int returnTypeId()

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(str name, DisplayFunctionType displayType, Types returnType, int returnTypeId, boolean isStatic)

#### Parameters

name  

<!-- -->

displayType  

<!-- -->

returnType  

<!-- -->

returnTypeId  

<!-- -->

isStatic  

### Method finalize

    public void finalize()

## Class DataSourceMethodInfoList
    class DataSourceMethodInfoList extends Object

### Remarks

### Examples

### Methods

| Method                                                  | Description                                                       |
|---------------------------------------------------------|-------------------------------------------------------------------|
| public int count()                                      |                                                                   |
| public DataSourceMethodInfo getMethod(int methodNumber) |                                                                   |
| public void addMethod(DataSourceMethodInfo method)      |                                                                   |
| public void new()                                       | Initializes a new instance of the DataSourceMethodInfoList class. |
| public void finalize()                                  |                                                                   |

### Method count

    public int count()

#### Return Value

### Method getMethod

    public DataSourceMethodInfo getMethod(int methodNumber)

#### Parameters

methodNumber  

#### Return Value

### Method addMethod

    public void addMethod(DataSourceMethodInfo method)

#### Parameters

method  

### Method new

Initializes a new instance of the DataSourceMethodInfoList class.

    public void new()

### Method finalize

    public void finalize()

## Class DataSourceNode
    class DataSourceNode extends TreeNode

### Remarks

### Examples

### Methods

| Method                                            | Description                                             |
|---------------------------------------------------|---------------------------------------------------------|
| public DataSourceMethodInfoList memberFunctions() |                                                         |
| public void finalize()                            |                                                         |
| private void new()                                | Initializes a new instance of the DataSourceNode class. |

### Method memberFunctions

    public DataSourceMethodInfoList memberFunctions()

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the DataSourceNode class.

    private void new()

## Class DataSourceRuntimeMetadataChangedEvtArgs
    class DataSourceRuntimeMetadataChangedEvtArgs extends ManagedEventArgs

### Remarks

### Examples

### Methods

| Method                                                                                                                                    | Description                                               |
|-------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| public str changedDataSourceName()                                                                                                        |                                                           |
| public FieldId changedFieldId()                                                                                                           |                                                           |
| public DataSourceMetadataChangeType changeType()                                                                                          |                                                           |
| public str referencedDataSourceName()                                                                                                     |                                                           |
| public void new(str changedDatasourceName, str referencedDatasourceName, FieldId changedFieldId, DataSourceMetadataChangeType changeType) | Initializes a new instance of the ManagedEventArgs class. |
| public void finalize()                                                                                                                    |                                                           |

### Method changedDataSourceName

    public str changedDataSourceName()

#### Return Value

### Method changedFieldId

    public FieldId changedFieldId()

#### Return Value

### Method changeType

    public DataSourceMetadataChangeType changeType()

#### Return Value

### Method referencedDataSourceName

    public str referencedDataSourceName()

#### Return Value

### Method new

Initializes a new instance of the ManagedEventArgs class.

    public void new(str changedDatasourceName, str referencedDatasourceName, FieldId changedFieldId, DataSourceMetadataChangeType changeType)

#### Parameters

changedDatasourceName  

<!-- -->

referencedDatasourceName  

<!-- -->

changedFieldId  

<!-- -->

changeType  

### Method finalize

    public void finalize()

## Class DateTimeUtil
    class DateTimeUtil extends Object

The DateTimeUtil class can be used to convert or modify utcdatetime and Timezone values.

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                            | Description                                                                                                                                                    |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ::public static DateTime addDays(DateTime t, int value)                                                                                                                           | Adds the specified number of days to a utcdatetime value.                                                                                                      |
| ::public static DateTime addHours(DateTime t, int value)                                                                                                                          | Adds the specified number of hours to a utcdatetime value.                                                                                                     |
| ::public static DateTime addMinutes(DateTime t, int value)                                                                                                                        | Adds the specified number of minutes to a utcdatetime value.                                                                                                   |
| ::public static DateTime addMonths(DateTime t, int value)                                                                                                                         | Adds the specified number of months to a utcdatetime value.                                                                                                    |
| ::public static DateTime addSeconds(DateTime t, Int64 value)                                                                                                                      | Adds the specified number of seconds to a utcdatetime value.                                                                                                   |
| ::public static DateTime addYears(DateTime t, int value)                                                                                                                          | Adds the specified number of years to a utcdatetime value.                                                                                                     |
| ::public static DateTime anyToDateTime(AnyType value)                                                                                                                             | Converts an anytype object to a utcdatetime value.                                                                                                             |
| ::public static DateTime applyTimeZoneOffset(DateTime t, Timezone tz)                                                                                                             | Retrieves a utcdatetime value that is offset from the specified utcdatetime value by the amount that is indicated by the specified Timezone enumeration value. |
| ::public static str applyTimeZoneOffsetFilter(QueryFilter filter)                                                                                                                 | Applies the time zone offset to the filter.                                                                                                                    |
| ::public static str applyTimeZoneOffsetRange(QueryBuildRange range)                                                                                                               | Applies the time zone offset to the range.                                                                                                                     |
| ::public static Date date(DateTime t)                                                                                                                                             | Converts the specified utcdatetime value to a date type.                                                                                                       |
| ::public static int day(DateTime t)                                                                                                                                               | Retrieves the day of the month that is specified by a utcdatetime value.                                                                                       |
| ::public static Timezone getClientMachineTimeZone()                                                                                                                               | Gets the Timezone enumeration value on the client computer.                                                                                                    |
| ::public static Timezone getCompanyTimeZone()                                                                                                                                     | Gets the Timezone value that is set for the current legal entity.                                                                                              |
| ::public static Int64 getDifference(DateTime t1, DateTime t2)                                                                                                                     | Gets the number of seconds between two specified utcdatetime values.                                                                                           |
| ::public static Timezone getOriginatingTimeZone(DateTime t)                                                                                                                       | Gets the originating Timezone enumeration value of the specified utcdatetime value.                                                                            |
| ::public static Date getSystemDate(Timezone tz)                                                                                                                                   |                                                                                                                                                                |
| ::public static DateTime getSystemDateTime()                                                                                                                                      | Gets the current system time as a utcdatetime value.                                                                                                           |
| ::public static TimeOfDay getTimeNow(Timezone tz)                                                                                                                                 |                                                                                                                                                                |
| ::public static TimeZoneId getTimeZoneId(Timezone tz)                                                                                                                             |                                                                                                                                                                |
| ::public static int getTimeZoneOffset(DateTime t, Timezone tz)                                                                                                                    | Gets the offset of the specified utcdatetime value to UTC by using the information in a Timezone enumeration value.                                            |
| ::public static int getTimeZoneRule(DateTime t)                                                                                                                                   | Returns the time zone rule that takes effect on the given date.                                                                                                |
| ::public static Date getToday(Timezone tz)                                                                                                                                        |                                                                                                                                                                |
| ::public static PreferredCalendar getUserPreferredCalendar()                                                                                                                      | Gets the PreferredCalendar enumeration value for the current user.                                                                                             |
| ::public static Timezone getUserPreferredTimeZone()                                                                                                                               | Gets the PreferredTimezone enumeration value for the current user.                                                                                             |
| ::public static int hour(DateTime t)                                                                                                                                              | Retrieves the hour of the day that is specified by a utcdatetime value.                                                                                        |
| ::public static DateTime maxValue()                                                                                                                                               | Retrieves the maximum value that is allowed for a variable of the utcdatetime type.                                                                            |
| ::public static int minute(DateTime t)                                                                                                                                            | Retrieves the minute in the hour that is specified by a utcdatetime value.                                                                                     |
| ::public static DateTime minValue()                                                                                                                                               | Retrieves the minimum value that is allowed for a variable of the utcdatetime type.                                                                            |
| ::public static int month(DateTime t)                                                                                                                                             | Retrieves the month in the year that is specified by a utcdatetime value.                                                                                      |
| ::public static DateTime newDateTime(Date date, TimeOfDay time, \[Timezone tzOffsetToRemove\])                                                                                    | Creates a new utcdatetime value by using the specified date and timeOfDay values.                                                                              |
| ::public static DateTime parse(str s)                                                                                                                                             | Creates a new utcdatetime value from the specified string.                                                                                                     |
| ::public static container populateTimeZoneInfo(int year, Timezone tz)                                                                                                             | Retrieves start and end dates and time bias.                                                                                                                   |
| ::public static DateTime removeTimeZoneOffset(DateTime t, Timezone tz)                                                                                                            | Removes the offset that is indicated by a Timezone enumeration value from the specified utcdatetime value.                                                     |
| ::public static str removeTimeZoneOffsetFilter(QueryFilter filter)                                                                                                                | Removes the time zone offset from the filter.                                                                                                                  |
| ::public static str removeTimeZoneOffsetRange(QueryBuildRange range)                                                                                                              | Removes the time zone offset from the range.                                                                                                                   |
| ::public static int second(DateTime t)                                                                                                                                            | Retrieves the seconds in a minute that is specified by a utcdatetime value.                                                                                    |
| ::public static TimeOfDay time(DateTime t)                                                                                                                                        | Retrieves the number of seconds that have elapsed since midnight as a timeOfDay value from the specified utcdatetime value.                                    |
| ::public static str toFormattedStr(DateTime t, int sequence, int day, int separator1, int month, int separator2, int year, int timeSeparator1, int timeSeparator2, \[int flags\]) |                                                                                                                                                                |
| ::public static str toStr(DateTime t)                                                                                                                                             | Converts a utcdatetime value to a string in the following format: YYYY-MM-DDThh:mm:ss, where T is a character literal.                                         |
| ::public static DateTime utcNow()                                                                                                                                                 | Retrieves a utcdatetime value that indicates the current system time.                                                                                          |
| ::public static int year(DateTime t)                                                                                                                                              | Retrieves the year that is specified by a utcdatetime value.                                                                                                   |
| ::public static void setSystemDateTime(DateTime t)                                                                                                                                | Sets the date and time of the system to the specified utcdatetime value.                                                                                       |
| ::public static void setCompanyTimeZone(Timezone tz, \[boolean persist\])                                                                                                         | Sets the Timezone enumeration value that is used by the current company.                                                                                       |
| ::public static void setUserPreferredCalendar(PreferredCalendar calendar)                                                                                                         | Sets the value of the PreferredCalendar enumeration type of the current user for the current session.                                                          |
| ::public static void setUserPreferredTimeZone(Timezone tz, \[boolean persist\])                                                                                                   | Sets the preferred time zone of the user to the specified Timezone enumeration value.                                                                          |
| private void new()                                                                                                                                                                | Initializes a new instance of the DateTimeUtil class.                                                                                                          |

### Method addDays

Adds the specified number of days to a utcdatetime value.

    public static DateTime addDays(DateTime t, int value)

#### Parameters

t  
The number of days to add.

<!-- -->

value  
The number of days to add.

#### Return Value

A new utcdatetime value.

#### Remarks

If the value of the value parameter is negative, days will be subtracted.

### Method addHours

Adds the specified number of hours to a utcdatetime value.

    public static DateTime addHours(DateTime t, int value)

#### Parameters

t  
The number of hours to add.

<!-- -->

value  
The number of hours to add.

#### Return Value

A new utcdatetime value.

#### Remarks

If the value of the value parameter is negative, hours will be subtracted.

### Method addMinutes

Adds the specified number of minutes to a utcdatetime value.

    public static DateTime addMinutes(DateTime t, int value)

#### Parameters

t  
The number of minutes to add.

<!-- -->

value  
The number of minutes to add.

#### Return Value

A new utcdatetime value.

#### Remarks

If the value of the value parameter is negative, minutes will be subtracted.

### Method addMonths

Adds the specified number of months to a utcdatetime value.

    public static DateTime addMonths(DateTime t, int value)

#### Parameters

t  
The number of months to add.

<!-- -->

value  
The number of months to add.

#### Return Value

A new utcdatetime value.

#### Remarks

If the value of the value parameter is negative, months will be subtracted.

### Method addSeconds

Adds the specified number of seconds to a utcdatetime value.

    public static DateTime addSeconds(DateTime t, Int64 value)

#### Parameters

t  
The number of seconds to add.

<!-- -->

value  
The number of seconds to add.

#### Return Value

A new utcdatetime value.

#### Remarks

If the value of the value parameter is negative, seconds will be subtracted.

### Method addYears

Adds the specified number of years to a utcdatetime value.

    public static DateTime addYears(DateTime t, int value)

#### Parameters

t  
The number of years to add.

<!-- -->

value  
The number of years to add.

#### Return Value

A new utcdatetime value.

#### Remarks

If the value of the value parameter is negative, years will be subtracted.

### Method anyToDateTime

Converts an anytype object to a utcdatetime value.

    public static DateTime anyToDateTime(AnyType value)

#### Parameters

value  
The object to convert.

#### Return Value

A new utcdatetime value.

#### Remarks

The following example string shows the format of a date-time string that this anyToDateTime method can correctly convert: "2009-01-28T13:44:55". The output of the DateTimeUtil::utcNow method is valid input into the anyToDateTime method.

### Method applyTimeZoneOffset

Retrieves a utcdatetime value that is offset from the specified utcdatetime value by the amount that is indicated by the specified Timezone enumeration value.

    public static DateTime applyTimeZoneOffset(DateTime t, Timezone tz)

#### Parameters

t  
A Timezone enumeration value that indicates the new offset to use.

<!-- -->

tz  
A Timezone enumeration value that indicates the new offset to use.

#### Return Value

A new utcdatetime value.

### Method applyTimeZoneOffsetFilter

Applies the time zone offset to the filter.

    public static str applyTimeZoneOffsetFilter(QueryFilter filter)

#### Parameters

filter  

#### Return Value

The new date/time range value.

### Method applyTimeZoneOffsetRange

Applies the time zone offset to the range.

    public static str applyTimeZoneOffsetRange(QueryBuildRange range)

#### Parameters

range  

#### Return Value

The new date/time range value.

### Method date

Converts the specified utcdatetime value to a date type.

    public static Date date(DateTime t)

#### Parameters

t  
The utcdatetime value to convert.

#### Return Value

A date value.

### Method day

Retrieves the day of the month that is specified by a utcdatetime value.

    public static int day(DateTime t)

#### Parameters

t  
A utcdatetime value for which to retrieve the value of the day component.

#### Return Value

The day of the month of the specified utcdatetime value.

### Method getClientMachineTimeZone

Gets the Timezone enumeration value on the client computer.

    public static Timezone getClientMachineTimeZone()

#### Return Value

The Timezone enumeration value on the client computer.

### Method getCompanyTimeZone

Gets the Timezone value that is set for the current legal entity.

    public static Timezone getCompanyTimeZone()

#### Return Value

The Timezone value that is set for the current legal entity.

### Method getDifference

Gets the number of seconds between two specified utcdatetime values.

    public static Int64 getDifference(DateTime t1, DateTime t2)

#### Parameters

t1  
The second utcdatetime value.

<!-- -->

t2  
The second utcdatetime value.

#### Return Value

The number of seconds between the two specified utcdatetime values.

### Method getOriginatingTimeZone

Gets the originating Timezone enumeration value of the specified utcdatetime value.

    public static Timezone getOriginatingTimeZone(DateTime t)

#### Parameters

t  
The utcdatetime value for which to retrieve the time zone.

#### Return Value

The Timezone enumeration value of the specified utcdatetime value.

### Method getSystemDate

    public static Date getSystemDate(Timezone tz)

#### Parameters

tz  

#### Return Value

### Method getSystemDateTime

Gets the current system time as a utcdatetime value.

    public static DateTime getSystemDateTime()

#### Return Value

The current system time as a utcdatetime value.

#### Remarks

If the system time has a fixed value, it will be returned. Otherwise, the current date and time from the local computer will be returned.

### Method getTimeNow

    public static TimeOfDay getTimeNow(Timezone tz)

#### Parameters

tz  

#### Return Value

### Method getTimeZoneId

    public static TimeZoneId getTimeZoneId(Timezone tz)

#### Parameters

tz  

#### Return Value

### Method getTimeZoneOffset

Gets the offset of the specified utcdatetime value to UTC by using the information in a Timezone enumeration value.

    public static int getTimeZoneOffset(DateTime t, Timezone tz)

#### Parameters

t  
A Timezone enumeration value that indicates the time zone of the t parameter.

<!-- -->

tz  
A Timezone enumeration value that indicates the time zone of the t parameter.

#### Return Value

An integer that indicates the offset of the specified utcdatetime value to UTC.

### Method getTimeZoneRule

Returns the time zone rule that takes effect on the given date.

    public static int getTimeZoneRule(DateTime t)

#### Parameters

t  

#### Return Value

The time zone rule for the given date.

### Method getToday

    public static Date getToday(Timezone tz)

#### Parameters

tz  

#### Return Value

### Method getUserPreferredCalendar

Gets the PreferredCalendar enumeration value for the current user.

    public static PreferredCalendar getUserPreferredCalendar()

#### Return Value

The PreferredCalendar enumeration value for the current user.

### Method getUserPreferredTimeZone

Gets the PreferredTimezone enumeration value for the current user.

    public static Timezone getUserPreferredTimeZone()

#### Return Value

The PreferredTimezone enumeration value for the current user.

### Method hour

Retrieves the hour of the day that is specified by a utcdatetime value.

    public static int hour(DateTime t)

#### Parameters

t  
A utcdatetime value for which to retrieve the value of the hour component.

#### Return Value

The hour in the day of the specified utcdatetime value.

### Method maxValue

Retrieves the maximum value that is allowed for a variable of the utcdatetime type.

    public static DateTime maxValue()

#### Return Value

The maximum value that is allowed for a variable of the utcdatetime type.

### Method minute

Retrieves the minute in the hour that is specified by a utcdatetime value.

    public static int minute(DateTime t)

#### Parameters

t  
A utcdatetime value for which to retrieve the value of the minute component.

#### Return Value

The minute in the hour of the specified utcdatetime value.

### Method minValue

Retrieves the minimum value that is allowed for a variable of the utcdatetime type.

    public static DateTime minValue()

#### Return Value

The minimum value that is allowed for a variable of the utcdatetime type.

### Method month

Retrieves the month in the year that is specified by a utcdatetime value.

    public static int month(DateTime t)

#### Parameters

t  
A utcdatetime value for which to retrieve the value of the month component.

#### Return Value

The month in the year of the specified utcdatetime value.

### Method newDateTime

Creates a new utcdatetime value by using the specified date and timeOfDay values.

    public static DateTime newDateTime(Date date, TimeOfDay time, [Timezone tzOffsetToRemove])

#### Parameters

date  
The time zone in which to create the new utcdatetime value; optional.

<!-- -->

time  
The time zone in which to create the new utcdatetime value; optional.

<!-- -->

tzOffsetToRemove  
The time zone in which to create the new utcdatetime value; optional.

#### Return Value

A new utcdatetime value.

#### Remarks

If no value is specified for the tzOffsetToRemove parameter, the utcdatetime value will be created in the UTC time zone.

### Method parse

Creates a new utcdatetime value from the specified string.

    public static DateTime parse(str s)

#### Parameters

s  
A string in the following format: yyyy-mm-ddThh:mm:ss.

#### Return Value

A new utcdatetime value from the specified string.

### Method populateTimeZoneInfo

Retrieves start and end dates and time bias.

    public static container populateTimeZoneInfo(int year, Timezone tz)

#### Parameters

year  
The time zone.

<!-- -->

tz  
The time zone.

#### Return Value

The start and end dates and time bias.

### Method removeTimeZoneOffset

Removes the offset that is indicated by a Timezone enumeration value from the specified utcdatetime value.

    public static DateTime removeTimeZoneOffset(DateTime t, Timezone tz)

#### Parameters

t  
The Timezone enumeration value to remove.

<!-- -->

tz  
The Timezone enumeration value to remove.

#### Return Value

A utcdatetime value without a time zone offset.

### Method removeTimeZoneOffsetFilter

Removes the time zone offset from the filter.

    public static str removeTimeZoneOffsetFilter(QueryFilter filter)

#### Parameters

filter  

#### Return Value

The new date/time range value.

### Method removeTimeZoneOffsetRange

Removes the time zone offset from the range.

    public static str removeTimeZoneOffsetRange(QueryBuildRange range)

#### Parameters

range  

#### Return Value

The new date/time range value.

### Method second

Retrieves the seconds in a minute that is specified by a utcdatetime value.

    public static int second(DateTime t)

#### Parameters

t  
A utcdatetime value for which to retrieve the value of the second component.

#### Return Value

The second in the minute of the specified utcdatetime value.

### Method time

Retrieves the number of seconds that have elapsed since midnight as a timeOfDay value from the specified utcdatetime value.

    public static TimeOfDay time(DateTime t)

#### Parameters

t  
A utcdatetime value for which to retrieve the time.

#### Return Value

A timeOfDay value that indicates the number of seconds that have elapsed since midnight.

### Method toFormattedStr

    public static str toFormattedStr(DateTime t, int sequence, int day, int separator1, int month, int separator2, int year, int timeSeparator1, int timeSeparator2, [int flags])

#### Parameters

t  

<!-- -->

sequence  

<!-- -->

day  

<!-- -->

separator1  

<!-- -->

month  

<!-- -->

separator2  

<!-- -->

year  

<!-- -->

timeSeparator1  

<!-- -->

timeSeparator2  

<!-- -->

flags  

#### Return Value

### Method toStr

Converts a utcdatetime value to a string in the following format: YYYY-MM-DDThh:mm:ss, where T is a character literal.

    public static str toStr(DateTime t)

#### Parameters

t  
The utcdatetime value to convert.

#### Return Value

The string representation of the specified utcdatetime value.

### Method utcNow

Retrieves a utcdatetime value that indicates the current system time.

    public static DateTime utcNow()

#### Return Value

The current system time as a utcdatetime value.

#### Remarks

This method is run on the server, so that the time that is returned is the system time of the server.

### Method year

Retrieves the year that is specified by a utcdatetime value.

    public static int year(DateTime t)

#### Parameters

t  
A utcdatetime value for which to retrieve the value of the year component.

#### Return Value

The year of the specified utcdatetime value.

### Method setSystemDateTime

Sets the date and time of the system to the specified utcdatetime value.

    public static void setSystemDateTime(DateTime t)

#### Parameters

t  
A utcdatetime value to which to set the system date and time.

### Method setCompanyTimeZone

Sets the Timezone enumeration value that is used by the current company.

    public static void setCompanyTimeZone(Timezone tz, [boolean persist])

#### Parameters

tz  
A Boolean value that indicates whether the new value should be persisted.

<!-- -->

persist  
A Boolean value that indicates whether the new value should be persisted.

### Method setUserPreferredCalendar

Sets the value of the PreferredCalendar enumeration type of the current user for the current session.

    public static void setUserPreferredCalendar(PreferredCalendar calendar)

#### Parameters

calendar  
The PreferredCalendar enumeration value to set.

### Method setUserPreferredTimeZone

Sets the preferred time zone of the user to the specified Timezone enumeration value.

    public static void setUserPreferredTimeZone(Timezone tz, [boolean persist])

#### Parameters

tz  
A Boolean value that indicates whether the new value should be persisted.

<!-- -->

persist  
A Boolean value that indicates whether the new value should be persisted.

### Method new

Initializes a new instance of the DateTimeUtil class.

    private void new()

## Class DialogBox
    class DialogBox extends Object

### Remarks

### Examples

### Methods

| Method                                                                                               | Description                                     |
|------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| public DialogButton retval()                                                                         |                                                 |
| public void new(DialogBoxType type, str text, str title, str bottomtext, DialogButton defaultButton) | Initializes a new instance of the Object class. |
| public void finalize()                                                                               |                                                 |

### Method retval

    public DialogButton retval()

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(DialogBoxType type, str text, str title, str bottomtext, DialogButton defaultButton)

#### Parameters

type  

<!-- -->

text  

<!-- -->

title  

<!-- -->

bottomtext  

<!-- -->

defaultButton  

### Method finalize

    public void finalize()

## Class DictClass
    class DictClass extends Object

The DictClass class provides information about a class.

### Remarks

### Examples

### Methods

| Method                                                            | Description                                                                                                                                   |
|-------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public AnyType callObject(str methodName, Object Called, VarArg ) | Calls a method on an object.                                                                                                                  |
| public AnyType callStatic(str methodName, VarArg )                | Calls a static method.                                                                                                                        |
| public ClassId extend()                                           | Provides the ID for the class that a specified class extends.                                                                                 |
| public List extendedBy(\[boolean allLevels\])                     | Provides a List object for the classes that extend a specified class.                                                                         |
| public Array getAllAttributes()                                   | Retrieves the full set of attributes for the class.                                                                                           |
| public Object getAttribute(str attribute)                         | Gets the first matching attribute from the class header metadata, creates an instance of the Object class that represents it, and returns it. |
| public Array getAttributes(str attribute)                         |                                                                                                                                               |
| public ClassId id()                                               | Provides the ID for a specified class.                                                                                                        |
| public ClassId implements(int no)                                 | Provides the ID for a specified interface that a class implements.                                                                            |
| public int implementsCnt()                                        | Indicates the number of interfaces that a class implements.                                                                                   |
| public boolean isAbstract()                                       | Indicates whether a class is abstract.                                                                                                        |
| public boolean isFinal()                                          | Indicates whether a class is final.                                                                                                           |
| public boolean isInterface()                                      | Indicates whether an object is an interface.                                                                                                  |
| public boolean isKernel()                                         | Indicates whether a class is a kernel class.                                                                                                  |
| public boolean isRunable()                                        | Indicates whether a class can be run.                                                                                                         |
| public Object makeObject(VarArg )                                 | Creates an object.                                                                                                                            |
| public str name()                                                 | Provides the name of a class.                                                                                                                 |
| public str objectMethod(int methodNumber)                         | Provides the name of a specified instance method in a class.                                                                                  |
| public int objectMethodCnt()                                      | Indicates the number of instance methods in a class.                                                                                          |
| public DictMethod objectMethodObject(int methodNumber)            | Provides information about a specified instance method in a class by returning a DictMethod object.                                           |
| public ClassRunMode RunMode()                                     | Specifies where a class is executed.                                                                                                          |
| public str staticMethod(int methodNumber)                         | Provides the name of a specified static method in a class.                                                                                    |
| public int staticMethodCnt()                                      | Indicates the number of static methods in a class.                                                                                            |
| public DictMethod staticMethodObject(int methodNumber)            | Provides information about a specified static method in a class by returning a DictMethod object.                                             |
| ::public static Array getAttributedClasses(str attribute)         |                                                                                                                                               |
| ::public static Object createObject(str className, VarArg )       |                                                                                                                                               |
| public void new(ClassId classId)                                  | Initializes a new instance of the Object class.                                                                                               |

### Method callObject

Calls a method on an object.

    public AnyType callObject(str methodName, Object Called, VarArg )

#### Parameters

methodName  

<!-- -->

Called  

<!-- -->

  

#### Return Value

An anytype data type value that is returned by the specified method.

#### Remarks

You must create an instance of the DictClass object by using a class that contains the method that you pass to the callObject method. If an attacker can control the input to the callObject method, a security risk exists. Therefore, this method runs under code access security. Calls to this method on the server require permission from the InteropPermission class. Make sure that the user has development rights by setting the security key to SysDevelopment on the control that calls this method.

#### Examples

This example calls the toString instance method in the Info class, for which the global instance of this class is named infolog, and then prints the value that is returned from the call.

    static void Job_Example_DictClass_CallObject(Args _args) 
    { 
        DictClass dictClass; 
        anytype   retVal; 
        str      resultOutput; 
        ExecutePermission perm; 
        perm = new ExecutePermission(); 
        // Grants permission to execute the DictClass.callObject method. 
        // DictClass.callObject runs under code access security. 
        perm.assert(); 
        dictClass = new DictClass(classidget(infolog)); 
        if (dictClass != null) 
        { 
            retVal       = dictClass.callObject("toString", infolog); 
            resultOutput = strfmt("Return value is %1", retVal); 
            print resultOutput; 
            pause; 
        } 
        // Closes the code access permission scope. 
        CodeAccessPermission::revertAssert(); 
    }

### Method callStatic

Calls a static method.

    public AnyType callStatic(str methodName, VarArg )

#### Parameters

methodName  

<!-- -->

  

#### Return Value

An anytype data type value that is returned by the specified method.

#### Remarks

You must create an instance of an object of the DictClass class by using a class that contains the method passed to the callStatic method. If an attacker can control the input to the callStatic method, a security risk exists. Therefore, this method runs under the code access security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development rights by setting the security key to the SysDevelopment on the control that calls this method.

#### Examples

This example calls the AOSClientMode method in the Session class and then prints the value returned from the call.

    static void Job_Example_DictClass_CallStatic(Args _args) 
    { 
        DictClass dictClass; 
        anytype   retVal; 
        str       resultOutput; 
        ExecutePermission perm; 
        perm = new ExecutePermission(); 
        // Grants permission to execute the DictClass.callStatic method. 
        // DictClass.callStatic runs under code access security. 
        perm.assert(); 
        dictClass = new DictClass(classnum(Session)); 
        if (dictClass != null) 
        { 
            retVal       = dictClass.callStatic("AOSClientMode"); 
            resultOutput = strfmt( 
                "Return value of AOSClientMode is %1",  
                retVal); 
            print resultOutput; 
            pause; 
        } 
        // Closes the code access permission scope. 
        CodeAccessPermission::revertAssert(); 
    }

### Method extend

Provides the ID for the class that a specified class extends.

    public ClassId extend()

#### Return Value

A value of the classID system data type that indicates the class ID; 0 if a class does not extend another class.

### Method extendedBy

Provides a List object for the classes that extend a specified class.

    public List extendedBy([boolean allLevels])

#### Parameters

allLevels  

#### Return Value

A List object for the classes that extend the class.

### Method getAllAttributes

Retrieves the full set of attributes for the class.

    public Array getAllAttributes()

#### Return Value

The array of SysAttribute objects for the class.

### Method getAttribute

Gets the first matching attribute from the class header metadata, creates an instance of the Object class that represents it, and returns it.

    public Object getAttribute(str attribute)

#### Parameters

attribute  
The attribute for which to search.

#### Return Value

The attribute as an instance of the Object class.

### Method getAttributes

    public Array getAttributes(str attribute)

#### Parameters

attribute  

#### Return Value

### Method id

Provides the ID for a specified class.

    public ClassId id()

#### Return Value

A value of the classId system data type that indicates the class ID.

### Method implements

Provides the ID for a specified interface that a class implements.

    public ClassId implements(int no)

#### Parameters

no  
An integer data type that specifies the interface, based on the order of the interfaces in the class declaration.

#### Return Value

A value of the classID system data type that indicates the class ID.

### Method implementsCnt

Indicates the number of interfaces that a class implements.

    public int implementsCnt()

#### Return Value

An integer data type value for the number of interfaces that a class implements.

### Method isAbstract

Indicates whether a class is abstract.

    public boolean isAbstract()

#### Return Value

true if the class is abstract; otherwise, false.

### Method isFinal

Indicates whether a class is final.

    public boolean isFinal()

#### Return Value

true if the class is final; otherwise, false.

### Method isInterface

Indicates whether an object is an interface.

    public boolean isInterface()

#### Return Value

true if the object is an interface; otherwise, false.

### Method isKernel

Indicates whether a class is a kernel class.

    public boolean isKernel()

#### Return Value

true if the class is a kernel class; otherwise, false.

### Method isRunable

Indicates whether a class can be run.

    public boolean isRunable()

#### Return Value

true if the class can be run; otherwise, false.

### Method makeObject

Creates an object.

    public Object makeObject(VarArg )

#### Parameters

  

#### Return Value

An instance of the Object class.

#### Remarks

You can pass an instance of the Object class to the DictClass::callObject method.

### Method name

Provides the name of a class.

    public str name()

#### Return Value

A string data type value for the class name.

### Method objectMethod

Provides the name of a specified instance method in a class.

    public str objectMethod(int methodNumber)

#### Parameters

methodNumber  
An integer data type that specifies a method in a class, based on the order of the methods.

#### Return Value

A string data type value for the method name.

#### Remarks

The \_methodNumber parameter starts counting at 1.

### Method objectMethodCnt

Indicates the number of instance methods in a class.

    public int objectMethodCnt()

#### Return Value

An integer value that indicates the number of instance methods in a class.

### Method objectMethodObject

Provides information about a specified instance method in a class by returning a DictMethod object.

    public DictMethod objectMethodObject(int methodNumber)

#### Parameters

methodNumber  
An integer data type that specifies a method in a class, based on the order of the methods. Numbering starts at 1.

#### Return Value

A DictMethod object that contains information about a specified method in a class.

#### Remarks

The \_methodNumber parameter starts counting at 1.

### Method RunMode

Specifies where a class is executed.

    public ClassRunMode RunMode()

#### Return Value

A ClassRunMode system enumeration value that indicates where a class is executed.

#### Remarks

The following are the possible return values:

-   The Called value.
-   The Client value.
-   The ClientorServer value.
-   The Server value.

### Method staticMethod

Provides the name of a specified static method in a class.

    public str staticMethod(int methodNumber)

#### Parameters

methodNumber  
An integer data type that specifies a method in a class, based on the order of the methods.

#### Return Value

A string data type value for the method name.

#### Remarks

The \_methodNumber parameter starts counting at 1.

### Method staticMethodCnt

Indicates the number of static methods in a class.

    public int staticMethodCnt()

#### Return Value

An integer that indicates the number of static methods in a class.

### Method staticMethodObject

Provides information about a specified static method in a class by returning a DictMethod object.

    public DictMethod staticMethodObject(int methodNumber)

#### Parameters

methodNumber  
An integer data type that specifies a method in a class, based on the order of the methods.

#### Return Value

A DictMethod object that contains information about a specified method in a class.

#### Remarks

The \_methodNumber parameter starts counting at 1.

### Method getAttributedClasses

    public static Array getAttributedClasses(str attribute)

#### Parameters

attribute  

#### Return Value

### Method createObject

    public static Object createObject(str className, VarArg )

#### Parameters

className  

<!-- -->

  

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(ClassId classId)

#### Parameters

classId  
A value of the classId system data type that indicates the system ID of a class.

#### Remarks

Class IDs are unsigned integers and are therefore always in the range 0 to 65535. The method does not fail if an invalid class ID is passed.You can pass a class name to the method instead of a class ID by using the classNum intrinsic function. For more information, see “Intrinsic Functions.”

## Class DictCompositeChildDataEntity
    class DictCompositeChildDataEntity extends Object

### Remarks

### Examples

### Methods

| Method                                                           | Description |
|------------------------------------------------------------------|-------------|
| public int level()                                               |             |
| public str name()                                                |             |
| public str dataEntity()                                          |             |
| public str relation()                                            |             |
| public str tags()                                                |             |
| public DictCompositeChildDataEntity parent()                     |             |
| public void new(str compositeDataEntityName, str dataEntityName) |             |

### Method level

    public int level()

#### Return Value

### Method name

    public str name()

#### Return Value

### Method dataEntity

    public str dataEntity()

#### Return Value

### Method relation

    public str relation()

#### Return Value

### Method tags

    public str tags()

#### Return Value

### Method parent

    public DictCompositeChildDataEntity parent()

#### Return Value

### Method new

    public void new(str compositeDataEntityName, str dataEntityName)

#### Parameters

compositeDataEntityName  

<!-- -->

dataEntityName  

## Class DictCompositeDataEntity
    class DictCompositeDataEntity extends Object

### Remarks

### Examples

### Methods

| Method                                                       | Description |
|--------------------------------------------------------------|-------------|
| ::public static List listOfCompositeDataEntities()           |             |
| public str label()                                           |             |
| public boolean isReadOnly()                                  |             |
| public str modules()                                         |             |
| public str configurationKey()                                |             |
| public str countryRegionCodes()                              |             |
| public str countryRegionContextField()                       |             |
| public str developerDocumentation()                          |             |
| public EntityCategory entityCategory()                       |             |
| public str formRef()                                         |             |
| public str singularLabel()                                   |             |
| public str tags()                                            |             |
| public str publicCollectionName()                            |             |
| public str publicEntityName()                                |             |
| public int dataEntityCount()                                 |             |
| public DictCompositeChildDataEntity childDataEntityNo(int n) |             |
| public void new(str compositeDataEntityName)                 |             |

### Method listOfCompositeDataEntities

    public static List listOfCompositeDataEntities()

#### Return Value

### Method label

    public str label()

#### Return Value

### Method isReadOnly

    public boolean isReadOnly()

#### Return Value

### Method modules

    public str modules()

#### Return Value

### Method configurationKey

    public str configurationKey()

#### Return Value

### Method countryRegionCodes

    public str countryRegionCodes()

#### Return Value

### Method countryRegionContextField

    public str countryRegionContextField()

#### Return Value

### Method developerDocumentation

    public str developerDocumentation()

#### Return Value

### Method entityCategory

    public EntityCategory entityCategory()

#### Return Value

### Method formRef

    public str formRef()

#### Return Value

### Method singularLabel

    public str singularLabel()

#### Return Value

### Method tags

    public str tags()

#### Return Value

### Method publicCollectionName

    public str publicCollectionName()

#### Return Value

### Method publicEntityName

    public str publicEntityName()

#### Return Value

### Method dataEntityCount

    public int dataEntityCount()

#### Return Value

### Method childDataEntityNo

    public DictCompositeChildDataEntity childDataEntityNo(int n)

#### Parameters

n  

#### Return Value

### Method new

    public void new(str compositeDataEntityName)

#### Parameters

compositeDataEntityName  

## Class DictConfigurationKey
    class DictConfigurationKey extends Object

The DictConfigurationKey class provides information about a configuration key.

### Remarks

For an example that uses the DictConfigurationKey class, see the new method.

### Examples

### Methods

| Method                                                                     | Description                                                               |
|----------------------------------------------------------------------------|---------------------------------------------------------------------------|
| public boolean enabled()                                                   | Returns a value that indicates whether the configuration key is enabled.  |
| public ConfigurationKeyId id()                                             | Returns the ID of the configuration key.                                  |
| public str label()                                                         | Returns the label for a configuration key.                                |
| public str labelId()                                                       |                                                                           |
| public LicenseCodeId licenseCode()                                         | Returns the license code ID for the configuration key.                    |
| public str name()                                                          | Returns the name of the configuration key.                                |
| public ConfigurationKeyId parentConfigurationKeyId()                       | Returns the ID of the parent configuration key for the configuration key. |
| ::public static boolean enabledById(ConfigurationKeyId configurationKeyId) |                                                                           |
| public boolean permanentlyDisabled()                                       |                                                                           |
| public void new(ConfigurationKeyId configurationKeyId)                     | Initializes a new instance of the Object class.                           |

### Method enabled

Returns a value that indicates whether the configuration key is enabled.

    public boolean enabled()

#### Return Value

true if the configuration key is enabled; otherwise, false.

#### Remarks

For an example that uses this method, see the new method.

### Method id

Returns the ID of the configuration key.

    public ConfigurationKeyId id()

#### Return Value

The ID of the configuration key.

### Method label

Returns the label for a configuration key.

    public str label()

#### Return Value

The label for the configuration key; an empty string if the configuration key does not have a label value.

### Method labelId

    public str labelId()

#### Return Value

### Method licenseCode

Returns the license code ID for the configuration key.

    public LicenseCodeId licenseCode()

#### Return Value

The license code ID for the configuration key; 0 (zero) if the configuration key has no license code.

### Method name

Returns the name of the configuration key.

    public str name()

#### Return Value

The name of the configuration key.

#### Remarks

For an example that uses this method, see the new method.

### Method parentConfigurationKeyId

Returns the ID of the parent configuration key for the configuration key.

    public ConfigurationKeyId parentConfigurationKeyId()

#### Return Value

The ID of the parent configuration key; 0 (zero) if the configuration key has no parent configuration key.

### Method enabledById

    public static boolean enabledById(ConfigurationKeyId configurationKeyId)

#### Parameters

configurationKeyId  

#### Return Value

### Method permanentlyDisabled

    public boolean permanentlyDisabled()

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(ConfigurationKeyId configurationKeyId)

#### Parameters

configurationKeyId  
The ID of the configuration key that is used to create the instance of the DictConfigurationKey class.

#### Examples

The following example shows how to create a new instance of the DictConfigurationKey class during an enumeration of configuration keys.

    ConfigurationKeySet configKeySet; 
    DictConfigurationKey dictConfigKey; 
    str strOutput; 
    int i; 
    configKeySet = new ConfigurationKeySet(); 
    configKeySet.loadSystemSetup(); 
    // Output the configuration key names and their enable state. 
    for (i=1; i <= configKeySet.cnt(); i++) 
    { 
        dictConfigKey = new DictConfigurationKey(configKeySet.cnt2Id(i)); 
        strOutput = dictConfigKey.enabled() ? "enabled" : "disabled"; 
        strOutput += " " + dictConfigKey.name(); 
        print strOutput; 
    }

## Class DictDataEntity
    class DictDataEntity extends DictView

### Remarks

### Examples

### Methods

| Method                                                  | Description |
|---------------------------------------------------------|-------------|
| public boolean isAggregateDataEntity()                  |             |
| public boolean isReadOnly()                             |             |
| public str primaryCompanyContext()                      |             |
| public str primaryKey()                                 |             |
| public boolean supportsSetBasedSqlOperations()          |             |
| public AutoNo enableSetBasedSqlOperations()             |             |
| public str modules()                                    |             |
| public EntityCategory entityCategory()                  |             |
| public boolean dataManagementEnabled()                  |             |
| public str dataManagementStagingTable()                 |             |
| public str publicCollectionName()                       |             |
| public str publicEntityName()                           |             |
| public boolean dataSourceIsReadOnly(str dataSourceName) |             |
| public str dataSourceID2Name(int dataSourceId)          |             |
| public boolean hasExtensionFields()                     |             |
| public List getExtensionFieldNames()                    |             |
| ::public static List listOfDataEntities()               |             |
| public void new(TableId tableId)                        |             |

### Method isAggregateDataEntity

    public boolean isAggregateDataEntity()

#### Return Value

### Method isReadOnly

    public boolean isReadOnly()

#### Return Value

### Method primaryCompanyContext

    public str primaryCompanyContext()

#### Return Value

### Method primaryKey

    public str primaryKey()

#### Return Value

### Method supportsSetBasedSqlOperations

    public boolean supportsSetBasedSqlOperations()

#### Return Value

### Method enableSetBasedSqlOperations

    public AutoNo enableSetBasedSqlOperations()

#### Return Value

### Method modules

    public str modules()

#### Return Value

### Method entityCategory

    public EntityCategory entityCategory()

#### Return Value

### Method dataManagementEnabled

    public boolean dataManagementEnabled()

#### Return Value

### Method dataManagementStagingTable

    public str dataManagementStagingTable()

#### Return Value

### Method publicCollectionName

    public str publicCollectionName()

#### Return Value

### Method publicEntityName

    public str publicEntityName()

#### Return Value

### Method dataSourceIsReadOnly

    public boolean dataSourceIsReadOnly(str dataSourceName)

#### Parameters

dataSourceName  

#### Return Value

### Method dataSourceID2Name

    public str dataSourceID2Name(int dataSourceId)

#### Parameters

dataSourceId  

#### Return Value

### Method hasExtensionFields

    public boolean hasExtensionFields()

#### Return Value

### Method getExtensionFieldNames

    public List getExtensionFieldNames()

#### Return Value

### Method listOfDataEntities

    public static List listOfDataEntities()

#### Return Value

### Method new

    public void new(TableId tableId)

#### Parameters

tableId  

## Class DictDataEntityField
    class DictDataEntityField extends DictField

### Remarks

### Examples

### Methods

| Method                                                                | Description |
|-----------------------------------------------------------------------|-------------|
| public FieldAccessModifier accessModifier()                           |             |
| public str dataEntityViewMethod()                                     |             |
| public str dataField()                                                |             |
| public str dataSource()                                               |             |
| public str dimensionLegalEntityContextField()                         |             |
| public str dynamicDimensionEnumerationField()                         |             |
| public boolean IsComputedField()                                      |             |
| public void new(TableId tableId, FieldId fieldId, \[int arrayIndex\]) |             |

### Method accessModifier

    public FieldAccessModifier accessModifier()

#### Return Value

### Method dataEntityViewMethod

    public str dataEntityViewMethod()

#### Return Value

### Method dataField

    public str dataField()

#### Return Value

### Method dataSource

    public str dataSource()

#### Return Value

### Method dimensionLegalEntityContextField

    public str dimensionLegalEntityContextField()

#### Return Value

### Method dynamicDimensionEnumerationField

    public str dynamicDimensionEnumerationField()

#### Return Value

### Method IsComputedField

    public boolean IsComputedField()

#### Return Value

### Method new

    public void new(TableId tableId, FieldId fieldId, [int arrayIndex])

#### Parameters

tableId  

<!-- -->

fieldId  

<!-- -->

arrayIndex  

## Class DictEnum
    class DictEnum extends Object

The DictEnum class obtains meta-information about the base enum enumerations in the Microsoft Dynamics 365 for Operations Application Object Tree (AOT).

### Remarks

For backward compatibility, a special naming convention for methods that convert to or from properties is used.

|                 |                                |                          |
|-----------------|--------------------------------|--------------------------|
| Name            | ReqDate                        | Symbol (typed as string) |
| Label           | @SYS18075 ("Requirement date") | Name or Label            |
| FeatureKey      | ReqSchedAction                 | FeatureKey               |
| EnumValue       | 0                              | Value                    |
| Position in AOT | First (Index = 0)              | Index                    |

This example is from the ActionBasicDateType base enum. For general information about enumerations, see the Developer's Guide.

### Examples

### Methods

| Method                                                            | Description                                                                                                               |
|-------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public ConfigurationKeyId configurationKeyId()                    | Returns the configuration key ID for the enumeration.                                                                     |
| public int displayLength(\[boolean useLongestLabel\])             |                                                                                                                           |
| public container getCountryRegionCodes()                          |                                                                                                                           |
| public str help(\[boolean useInterfaceLanguage\])                 | Retrieves the Help text for this enumeration.                                                                             |
| public str helpDefined()                                          | Returns the value of the help property for this enumeration.                                                              |
| public EnumId id()                                                | Returns the enumeration ID of the enumeration.                                                                            |
| public ConfigurationKeyId index2ConfigurationKey(int index)       |                                                                                                                           |
| public container index2CountryRegionCodes(int index)              |                                                                                                                           |
| public str index2Label(int index)                                 | Returns the label of the enumeration item that is specified by an index.                                                  |
| public str index2LabelId(int index)                               |                                                                                                                           |
| public str index2Name(int index)                                  | Returns the label of the enumeration item that is specified by an index.                                                  |
| public str index2Symbol(int index)                                | Returns the symbol or name of the enumeration item that is specified by an index.                                         |
| public int index2Value(int index)                                 | Returns the value of the enumeration item that is specified by an index.                                                  |
| public str label()                                                | Returns the label text of the enumeration.                                                                                |
| public str labelDefined()                                         | Returns the value of the label property for this enumeration.                                                             |
| public str name()                                                 | Returns the name of the enumeration.                                                                                      |
| public int name2Value(str name)                                   | Returns the enumeration value of the item that is referenced by its label.                                                |
| public boolean showAsRadio()                                      | Returns a value that indicates whether the enumeration should be displayed by using radio buttons instead of a combo box. |
| public int symbol2Value(str name)                                 | Returns the enumeration value of the item, referenced by its symbol or name.                                              |
| public ConfigurationKeyId value2ConfigurationKey(int value)       | Returns the configuration key ID of a specified enumeration value.                                                        |
| public container value2CountryRegionCodes(int value)              |                                                                                                                           |
| public str value2Label(int value)                                 | Returns the label of a specified enumeration value.                                                                       |
| public str value2Name(int value)                                  | Returns the name of a specified enumeration value.                                                                        |
| public str value2Symbol(int value)                                | Returns the symbol, or the value of the Name property, of a specified enumeration value.                                  |
| public int values()                                               | Returns the number of items in the enumeration.                                                                           |
| ::public static str queryFilterNames2Values(QueryFilter filter)   |                                                                                                                           |
| ::public static str queryFilterValues2Names(QueryFilter filter)   |                                                                                                                           |
| ::public static str queryRangeNames2Values(QueryBuildRange range) |                                                                                                                           |
| ::public static str queryRangeValues2Names(QueryBuildRange range) |                                                                                                                           |
| ::public static int value2id(AnyType value)                       | Returns the enumeration ID of a specified value.                                                                          |
| public void new(EnumId typeId)                                    | Initializes a new instance of the Object class.                                                                           |

### Method configurationKeyId

Returns the configuration key ID for the enumeration.

    public ConfigurationKeyId configurationKeyId()

#### Return Value

The configuration key ID for the enumeration; 0 (zero) if there is no configuration key ID for the enumeration.

#### Examples

The following example shows the retrieval of the configuration key ID for an enumeration.

    DictEnum de; 
    int      i; 
    de = new DictEnum(enumName2Id("ActionType")); 
    print int2str(de.configurationKeyId());

### Method displayLength

    public int displayLength([boolean useLongestLabel])

#### Parameters

useLongestLabel  

#### Return Value

### Method getCountryRegionCodes

    public container getCountryRegionCodes()

#### Return Value

### Method help

Retrieves the Help text for this enumeration.

    public str help([boolean useInterfaceLanguage])

#### Parameters

useInterfaceLanguage  

#### Return Value

A string that contains the Help text; an empty string if no Help text is defined.

#### Remarks

The Help text is defined on the Help property of the base enumeration.

### Method helpDefined

Returns the value of the help property for this enumeration.

    public str helpDefined()

#### Return Value

The value of the help property for this enumeration.

### Method id

Returns the enumeration ID of the enumeration.

    public EnumId id()

#### Return Value

The enumeration ID of the enumeration.

### Method index2ConfigurationKey

    public ConfigurationKeyId index2ConfigurationKey(int index)

#### Parameters

index  

#### Return Value

### Method index2CountryRegionCodes

    public container index2CountryRegionCodes(int index)

#### Parameters

index  

#### Return Value

### Method index2Label

Returns the label of the enumeration item that is specified by an index.

    public str index2Label(int index)

#### Parameters

index  
The zero-based index of the enumeration in the AOT.

#### Return Value

The label of the enumeration item that specified by index; an empty string if index does not reference a valid enumeration item.

#### Examples

The following example shows the retrieval of the label for items in an enumeration.

    DictEnum de; 
    int      i; 
    de = new DictEnum(enumName2Id("ActionType")); 
    for (i=0; i < de.values(); i++) 
    { 
        print int2str(i) + ", " + de.index2Label(i); 
    }

### Method index2LabelId

    public str index2LabelId(int index)

#### Parameters

index  

#### Return Value

### Method index2Name

Returns the label of the enumeration item that is specified by an index.

    public str index2Name(int index)

#### Parameters

index  
The zero-based index of the enumeration in the AOT.

#### Return Value

The label of the enumeration item that is specified by index; an empty string if index does not reference a valid enumeration item.

#### Remarks

For backward compatibility with earlier versions of Microsoft Dynamics 365 for Operations, "Name" in DictEnum::value2Name refers to the enumeration item's label property. To make your code more readable, use the DictEnum::value2Label method instead of the DictEnum::value2Name method. To retrieve the value of the name property of the enumeration item as shown in the AOT, use the DictEnum::value2Symbol method.

#### Examples

The following example shows the retrieval of the label for items in an enumeration.

    DictEnum de; 
    int      i; 
    de = new DictEnum(enumName2Id("ActionType")); 
    for (i=0; i < de.values(); i++) 
    { 
        print int2str(i) + ", " + de.index2Name(i); 
    }

### Method index2Symbol

Returns the symbol or name of the enumeration item that is specified by an index.

    public str index2Symbol(int index)

#### Parameters

index  
The zero-based index of the enumeration in the AOT.

#### Return Value

The symbol of the enumeration item that is specified by index; an empty string if index does not reference a valid enumeration item.

#### Remarks

The symbol corresponds to the Name property of the enumeration item in the AOT.

#### Examples

The following example shows the retrieval of the symbol for items in an enumeration.

    DictEnum de; 
    int      i; 
    de = new DictEnum(enumName2Id("ActionType")); 
    for (i=0; i < de.values(); i++) 
    { 
        print int2str(i) + ", " + de.index2Symbol(i); 
    }

### Method index2Value

Returns the value of the enumeration item that is specified by an index.

    public int index2Value(int index)

#### Parameters

index  
The zero-based index of the enumeration in the AOT.

#### Return Value

The value of the enumeration item that is specified by index.

#### Examples

The following example shows the retrieval of the value for items in an enumeration.

    DictEnum de; 
    int      i; 
    de = new DictEnum(enumName2Id("ActionType")); 
    for (i=0; i < de.values(); i++) 
    { 
        print int2str(i) + ", " + int2str(de.index2Value(i)); 
    }

### Method label

Returns the label text of the enumeration.

    public str label()

#### Return Value

The name of the enumeration; an empty string if there is no label for the enumeration.

### Method labelDefined

Returns the value of the label property for this enumeration.

    public str labelDefined()

#### Return Value

The value of the label property for this enumeration.

### Method name

Returns the name of the enumeration.

    public str name()

#### Return Value

The name of the enumeration.

### Method name2Value

Returns the enumeration value of the item that is referenced by its label.

    public int name2Value(str name)

#### Parameters

name  
The label for the enumeration for which the enumeration value is being retrieved.

#### Return Value

The enumeration value for name; 255 if name is not a valid label of an enumeration.

#### Remarks

For backward compatibility with earlier versions of Microsoft Dynamics 365 for Operations, name refers to the label. Enumeration items that do not have labels cannot be found by using the DictEnum::name2Value method.

### Method showAsRadio

Returns a value that indicates whether the enumeration should be displayed by using radio buttons instead of a combo box.

    public boolean showAsRadio()

#### Return Value

true if the enumeration style is radio button; otherwise, false.

### Method symbol2Value

Returns the enumeration value of the item, referenced by its symbol or name.

    public int symbol2Value(str name)

#### Parameters

name  
The symbol or name for the enumeration for which the enumeration value is being retrieved.

#### Return Value

The enumeration value for name; 255 if name is not a valid enumeration.

### Method value2ConfigurationKey

Returns the configuration key ID of a specified enumeration value.

    public ConfigurationKeyId value2ConfigurationKey(int value)

#### Parameters

value  
The integer value for the enumeration for which the configuration key is being retrieved.

#### Return Value

The configuration key ID for value; 0 (zero) if there is no configuration key for value or value is not a valid enumeration.

### Method value2CountryRegionCodes

    public container value2CountryRegionCodes(int value)

#### Parameters

value  

#### Return Value

### Method value2Label

Returns the label of a specified enumeration value.

    public str value2Label(int value)

#### Parameters

value  
The integer value for the enumeration for which the label is being retrieved.

#### Return Value

The label for value; an empty string if there is no label for value or value is not a valid enumeration.

#### Remarks

Enumeration items are not required to have a label. This method cannot be used to determine whether a value exists in the enumeration. To determine whether a value exists in the enumeration, use the DictEnum::value2Symbol method.

### Method value2Name

Returns the name of a specified enumeration value.

    public str value2Name(int value)

#### Parameters

value  
The integer value for the enumeration for which the label is being retrieved.

#### Return Value

The name for value; an empty string if there is no name for value or value is not a valid enumeration.

#### Remarks

To determine whether a value is in the enumeration, use the value2Symbol method instead. The value2Name method cannot be used to determine whether a value is in the enumeration, because enumeration items are not required to have a label.

### Method value2Symbol

Returns the symbol, or the value of the Name property, of a specified enumeration value.

    public str value2Symbol(int value)

#### Parameters

value  
The integer value for the enumeration for which the symbol is being retrieved.

#### Return Value

The symbol or name for value; an empty string if value is not a valid enumeration.

#### Remarks

Enumeration values are required to have a symbol. This method can be used to determine whether an enumeration value exists by checking whether the return value is an empty string.

### Method values

Returns the number of items in the enumeration.

    public int values()

#### Return Value

The number of items in the enumeration.

#### Remarks

Because values must be unique, the number of values is the same as the number of items.

#### Examples

The following example shows how to retrieve the number of items in an enumeration and use that value in a loop.

    DictEnum de; 
    int      i; 
    de = new DictEnum(enumName2Id("ActionType")); 
    for (i=0; i < de.values(); i++) 
    { 
        print int2str(i) + ", " + de.index2Name(i); 
    }

### Method queryFilterNames2Values

    public static str queryFilterNames2Values(QueryFilter filter)

#### Parameters

filter  

#### Return Value

### Method queryFilterValues2Names

    public static str queryFilterValues2Names(QueryFilter filter)

#### Parameters

filter  

#### Return Value

### Method queryRangeNames2Values

    public static str queryRangeNames2Values(QueryBuildRange range)

#### Parameters

range  

#### Return Value

### Method queryRangeValues2Names

    public static str queryRangeValues2Names(QueryBuildRange range)

#### Parameters

range  

#### Return Value

### Method value2id

Returns the enumeration ID of a specified value.

    public static int value2id(AnyType value)

#### Parameters

value  
The value for which the enumeration ID is being queried. The value parameter can be of any type.

#### Return Value

The enumeration ID of value if value is an enumeration; otherwise, 0 (zero).

#### Remarks

The value parameter can be of any type.

### Method new

Initializes a new instance of the Object class.

    public void new(EnumId typeId)

#### Parameters

typeId  
The ID of the enumeration.

#### Remarks

The constructor does not fail if an invalid enum ID is supplied. However, when the DictEnum instance is used, a run-time error occurs. Note that EnumID values are unsigned integers and are therefore always in the range 0–65535.

#### Examples

The following example creates an instance of the DictEnum class.

    DictEnum de; 
    de = new DictEnum(enumName2Id("ActionType"));

## Class DictField
    class DictField extends Object

The DictField class provides information about a specified field in a specified table.

### Remarks

### Examples

The following example shows how to create an instance of the DictField class to determine whether a field is mandatory.

    #macrolib.dictfield 
    DictField df; 
    int       nFlags; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    if (df) 
    { 
        nFlags = df.flags(); 
        if (bitTest(nFlags,#DBF_MANDATORY)) 
        { 
            print ("The field is mandatory."); 
        } 
        else 
        { 
            print ("The field is not mandatory."); 
        } 
    }

### Methods

| Method                                                                                                                | Description                                                                                                                               |
|-----------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public FieldId aliasFor()                                                                                             | Returns the ID of the alias field, if the field is an alias for another field.                                                            |
| public Alignment alignment()                                                                                          |                                                                                                                                           |
| public boolean allowEdit()                                                                                            |                                                                                                                                           |
| public boolean allowEditOnCreate()                                                                                    |                                                                                                                                           |
| public boolean aosAuthorization()                                                                                     |                                                                                                                                           |
| public int arrayIndex()                                                                                               |                                                                                                                                           |
| public int arraySize()                                                                                                | Returns the array size for the field (in other words, the array size of the underlying extended data type).                               |
| public Types baseType()                                                                                               | Returns the base type of the field, such as string, real, integer, date, time, enum, or container.                                        |
| public ConfigurationKeyId configurationKeyId()                                                                        | Returns the ID of the configuration key for the field.                                                                                    |
| public str dateTimeTimeZoneRuleFieldName(\[int arrayindex\])                                                          |                                                                                                                                           |
| public int displayHeight(\[boolean useDefaults\])                                                                     |                                                                                                                                           |
| public int displayLength(\[boolean useDefaults\])                                                                     |                                                                                                                                           |
| public EnumId enumId()                                                                                                | Returns the ID of the enumeration if the field is based on an enumeration.                                                                |
| public int flags(\[str ext\], \[Common record\])                                                                      | Returns an integer that defines the properties of the field. The flag values, such as DBF\_MANDATORY, are defined in the DictField macro. |
| public container getCountryRegionCodes()                                                                              |                                                                                                                                           |
| public FieldId getCountryRegionContextField()                                                                         |                                                                                                                                           |
| public str getPrimaryTableForSurrogateField()                                                                         |                                                                                                                                           |
| public str groupPrompt()                                                                                              | Returns the groupPrompt value for the field.                                                                                              |
| public str groupPromptDefined()                                                                                       | Returns the value of the groupPrompt property for the field.                                                                              |
| public str help(\[int arrayIndex\], \[boolean useInterfaceLanguage\])                                                 | Returns the Help text that is displayed for the field.                                                                                    |
| public str helpDefined()                                                                                              | Returns the value of the help property for the field.                                                                                     |
| public FieldId id()                                                                                                   | Returns the ID of the field.                                                                                                              |
| public boolean isIgnoreEDTRelation()                                                                                  |                                                                                                                                           |
| public boolean isMonocased()                                                                                          | Returns a value that indicates whether the database requires that the field be monocase.                                                  |
| public boolean isSql()                                                                                                | Returns a value that indicates whether the field is in the SQL database.                                                                  |
| public boolean isSurrogateForeignKey()                                                                                |                                                                                                                                           |
| public boolean isSystem()                                                                                             | Returns a value that indicates whether the field is a system field.                                                                       |
| public str label(\[int arrayIndex\])                                                                                  | Returns the label for the field.                                                                                                          |
| public str labelDefined()                                                                                             | Returns the value of the label property for the field.                                                                                    |
| public boolean mandatory()                                                                                            |                                                                                                                                           |
| public str name(\[DbBackend db\], \[int arrayindex\], \[FieldNameGenerationMode generationMode\], \[str tableAlias\]) | Returns the name of the field.                                                                                                            |
| public Guid origin()                                                                                                  |                                                                                                                                           |
| public str qualifiedLabel(\[int arrayIndex\])                                                                         |                                                                                                                                           |
| public str relatedTableName()                                                                                         |                                                                                                                                           |
| public str relationContext()                                                                                          |                                                                                                                                           |
| public DictRelation relationObject(\[int arrayIndex\])                                                                | Returns a DictRelation object for the field if the field is based on an extended data type that has a relation.                           |
| public AccessType rights(\[boolean ignoreContext\])                                                                   | Returns the access rights for the current user that are specified for the field.                                                          |
| public int stringLen()                                                                                                | Returns the string size of the field if the base type of the field is a string.                                                           |
| public TableId tableid()                                                                                              | Returns the ID of the table that contains the field.                                                                                      |
| public Types type()                                                                                                   | Returns the data type of the field.                                                                                                       |
| public ExtendedTypeId typeId()                                                                                        | Returns the ID of the extended data type if the field is based on an extended data type.                                                  |
| public boolean visible()                                                                                              |                                                                                                                                           |
| public void setLookupMode(boolean lookupMode)                                                                         |                                                                                                                                           |
| public void setSFKAutoAuthorizationMode(boolean sfkMode)                                                              |                                                                                                                                           |
| public void new(TableId tableId, FieldId fieldId, \[int arrayIndex\])                                                 | Initializes a new instance of the Object class.                                                                                           |

### Method aliasFor

Returns the ID of the alias field, if the field is an alias for another field.

    public FieldId aliasFor()

#### Return Value

The ID of the alias field for the field; 0 (zero) if the field is not an alias for another field.

#### Remarks

When the user enters data in a field, the validateField method of the table is called. If the validateField method cannot perform a lookup on the value, it checks whether an alias exists. If an alias field exists, the validateField method performs a lookup on the alias field.

#### Examples

The following example shows the retrieval of the alias field for a field.

    DictField df; 
    fieldId   fId; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum));
    if (df) 
    { 
        fId = df.aliasFor(); 
        if (0 != fId) 
        { 
            print (strfmt("Field alias: %1", fieldid2name(tablenum(CustTable), fId))); 
        } 
    }

### Method alignment

    public Alignment alignment()

#### Return Value

### Method allowEdit

    public boolean allowEdit()

#### Return Value

### Method allowEditOnCreate

    public boolean allowEditOnCreate()

#### Return Value

### Method aosAuthorization

    public boolean aosAuthorization()

#### Return Value

### Method arrayIndex

    public int arrayIndex()

#### Return Value

### Method arraySize

Returns the array size for the field (in other words, the array size of the underlying extended data type).

    public int arraySize()

#### Return Value

The array size for the field; 1 if the field is not an array.

#### Examples

The following example shows the retrieval of the array size for a field.

    DictField df; 
    Types     t; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum));  
    if (df) 
    { 
        print strfmt("The arraySize is %1.", df.arraySize()); 
    }

### Method baseType

Returns the base type of the field, such as string, real, integer, date, time, enum, or container.

    public Types baseType()

#### Return Value

A Types value that specifies the type of the field.

#### Examples

The following example shows the retrieval of the base type of a field.

    DictField df;
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    if (df)
    {
        print strfmt("The field type is %1.", df.baseType());
    }

### Method configurationKeyId

Returns the ID of the configuration key for the field.

    public ConfigurationKeyId configurationKeyId()

#### Return Value

The ID of the configuration key for the field; 0 (zero) if there is no configuration key for the field.

#### Examples

The following example shows the retrieval of the configuration key ID and the configuration key name for a field.

    DictField df; 
    configurationKeyId cki; 
    DictConfigurationKey dck; 
    df = new DictField(tablenum(BankAccountTable), fieldnum(BankAccountTable, CustPaymFeePost)); 
    if (df) 
    { 
        cki = df.configurationKeyId(); 
        //    print df.helpDefined(); 
        if (0 != cki) 
        { 
            dck = new DictConfigurationKey(cki); 
            if (dck) 
            print strfmt("The configuration key is %1.", dck.name()); 
        } 
        else 
        { 
            print "No configuration key"; 
        } 
    }

### Method dateTimeTimeZoneRuleFieldName

    public str dateTimeTimeZoneRuleFieldName([int arrayindex])

#### Parameters

arrayindex  

#### Return Value

### Method displayHeight

    public int displayHeight([boolean useDefaults])

#### Parameters

useDefaults  

#### Return Value

### Method displayLength

    public int displayLength([boolean useDefaults])

#### Parameters

useDefaults  

#### Return Value

### Method enumId

Returns the ID of the enumeration if the field is based on an enumeration.

    public EnumId enumId()

#### Return Value

The enumeration ID if the field is based on an enumeration; otherwise, 0 (zero).

#### Examples

The following example shows the retrieval of the enumeration ID and the enumeration name of a field that is based on an enumeration.

    DictField df; 
    DictEnum  de; 
    enumId    id; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    if (df) 
    { 
        id = df.enumId(); 
        if (0 != id) 
        { 
            de = new DictEnum(id); 
            if (de) 
            { 
                print de.name(); 
            } 
        } 
    }

### Method flags

Returns an integer that defines the properties of the field. The flag values, such as DBF\_MANDATORY, are defined in the DictField macro.

    public int flags([str ext], [Common record])

#### Parameters

ext  

<!-- -->

record  

#### Return Value

An integer value, where each bit corresponds to a field flag.

#### Remarks

Use the Global::bitTest Method method or the & operator to check individual flag values.

#### Examples

The following example shows the retrieval of the flags of a field to determine whether the field is mandatory.

    #macrolib.dictfield 
    DictField df; 
    int       nFlags; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    if (df) 
    { 
        nFlags = df.flags(); 
        if (bitTest(nFlags,#DBF_MANDATORY)) 
        { 
            print ("The field is mandatory."); 
        } 
        else 
        { 
            print ("The field is not mandatory."); 
        } 
    }

### Method getCountryRegionCodes

    public container getCountryRegionCodes()

#### Return Value

### Method getCountryRegionContextField

    public FieldId getCountryRegionContextField()

#### Return Value

### Method getPrimaryTableForSurrogateField

    public str getPrimaryTableForSurrogateField()

#### Return Value

### Method groupPrompt

Returns the groupPrompt value for the field.

    public str groupPrompt()

#### Return Value

The groupPrompt value for the field.

### Method groupPromptDefined

Returns the value of the groupPrompt property for the field.

    public str groupPromptDefined()

#### Return Value

The value of the groupPrompt property for the table.

### Method help

Returns the Help text that is displayed for the field.

    public str help([int arrayIndex], [boolean useInterfaceLanguage])

#### Parameters

arrayIndex  
A Boolean value that indicates whether to use the user interface language for the Help text; optional.

<!-- -->

useInterfaceLanguage  
A Boolean value that indicates whether to use the user interface language for the Help text; optional.

#### Return Value

The Help text or inherited Help text for the field.

#### Remarks

If no Help text is defined for the field, this method returns the Help text for the extended data type that is used for the field, if applicable. If an array entry is specified, this method returns the Help text for the array element.

#### Examples

The following example shows retrieval of the Help text for the field.

    DictField df; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    if (df) 
    { 
        print df.help(); 
    }

### Method helpDefined

Returns the value of the help property for the field.

    public str helpDefined()

#### Return Value

The value of the help property for the field.

#### Remarks

Unlike the help method, the helpDefined method does not return the Help text of the extended data type if the field is based on an extended data type and has no Help text defined for it.

#### Examples

The following example shows retrieval of the defined Help text for the field.

    DictField df; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    if (df) 
    { 
        print df.helpDefined(); 
    }

### Method id

Returns the ID of the field.

    public FieldId id()

#### Return Value

The ID of the field.

#### Examples

The following example retrieves the ID of a field.

    DictField df; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    if (df) 
    { 
        print df.id(); 
    }

### Method isIgnoreEDTRelation

    public boolean isIgnoreEDTRelation()

#### Return Value

### Method isMonocased

Returns a value that indicates whether the database requires that the field be monocase.

    public boolean isMonocased()

#### Return Value

true if the field is monocase; otherwise, false.

### Method isSql

Returns a value that indicates whether the field is in the SQL database.

    public boolean isSql()

#### Return Value

true if the field is in the SQL database; otherwise, false.

#### Examples

The following example determines whether the field is in the SQL database.

        DictField df; 
        df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
        if (df) 
        { 
        if (df.isSql()) 
        { 
            print ("Field is in SQL database"); 
        } 
        else 
        { 
            print ("Field is not in SQL database"); 
        } 
        }

### Method isSurrogateForeignKey

    public boolean isSurrogateForeignKey()

#### Return Value

### Method isSystem

Returns a value that indicates whether the field is a system field.

    public boolean isSystem()

#### Return Value

true if the field is a system field; otherwise, false.

### Method label

Returns the label for the field.

    public str label([int arrayIndex])

#### Parameters

arrayIndex  

#### Return Value

The label or inherited label value for the field.

#### Remarks

If no label is provided for the field, this method returns the label for the extended data type for the field, if applicable. If an array entry is specified, this method returns the label for the array element.

### Method labelDefined

Returns the value of the label property for the field.

    public str labelDefined()

#### Return Value

The value of the label property for the table; an empty string if there is no label text for the table.

#### Remarks

Unlike the label method, the labelDefined method does not return the extended data type label if the field is based on an extended data type and has no label defined for it.

#### Examples

The following example shows the retrieval of the defined label for a field.

    DictField df; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    if (df) 
    { 
        print df.labelDefined(); 
    }

### Method mandatory

    public boolean mandatory()

#### Return Value

### Method name

Returns the name of the field.

    public str name([DbBackend db], [int arrayindex], [FieldNameGenerationMode generationMode], [str tableAlias])

#### Parameters

db  
The alias for the table; optional.

<!-- -->

arrayindex  
The alias for the table; optional.

<!-- -->

generationMode  
The alias for the table; optional.

<!-- -->

tableAlias  
The alias for the table; optional.

#### Return Value

The name of the field.

#### Examples

The following example shows the retrieval of the name of the field.

    DictField df; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    if (df) 
    { 
        print df.name(); 
    }

### Method origin

    public Guid origin()

#### Return Value

### Method qualifiedLabel

    public str qualifiedLabel([int arrayIndex])

#### Parameters

arrayIndex  

#### Return Value

### Method relatedTableName

    public str relatedTableName()

#### Return Value

### Method relationContext

    public str relationContext()

#### Return Value

### Method relationObject

Returns a DictRelation object for the field if the field is based on an extended data type that has a relation.

    public DictRelation relationObject([int arrayIndex])

#### Parameters

arrayIndex  

#### Return Value

A DictRelation object that represents the relations for the field; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if there no relations are defined for the field, or if the field is not based on an extended data type.

### Method rights

Returns the access rights for the current user that are specified for the field.

    public AccessType rights([boolean ignoreContext])

#### Parameters

ignoreContext  

#### Return Value

The access rights for the current user that are specified for the field.

#### Remarks

This can be one of the values in the AccessType enumeration.

### Method stringLen

Returns the string size of the field if the base type of the field is a string.

    public int stringLen()

#### Return Value

The string size of the field if the base type of the field is a string; otherwise, 0 (zero).

#### Examples

The following example shows retrieving the string length of a field.

    DictField df; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    if (df) 
    { 
        print strfmt("The string length is %1.", df.stringLen()); 
    }

### Method tableid

Returns the ID of the table that contains the field.

    public TableId tableid()

#### Return Value

The ID of the table that contains the field.

#### Examples

The following example shows the retrieval of the table ID of a field.

    DictField df; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    if (df) 
    { 
        print df.tableid(); 
    }

### Method type

Returns the data type of the field.

    public Types type()

#### Return Value

A Types value that specifies the type of the field.

#### Remarks

If the field is based on an extended data type, Types::UserType is returned as the return value of this method.

#### Examples

The following example shows the retrieval of the type of a field.

    DictField df; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    if (df) 
    { 
        print df.type(); 
    }

### Method typeId

Returns the ID of the extended data type if the field is based on an extended data type.

    public ExtendedTypeId typeId()

#### Return Value

The ID of the extended data type if the field is based on an extended data type; otherwise, 0 (zero).

#### Examples

The following example shows the retrieval of the extended data type ID for a field.

    DictField df; 
    extendedTypeId eti; 
    DictType  dt; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    if (df) 
    { 
       eti = df.typeId(); 
       if (0 != eti) 
       { 
            dt = new DictType(eti); 
            if (dt) 
            { 
                print strfmt("The field is based on %1.", dt.name()); 
            } 
       } 
       else 
       { 
            print "The field is not based on an extended data type."; 
       } 
    }

### Method visible

    public boolean visible()

#### Return Value

### Method setLookupMode

    public void setLookupMode(boolean lookupMode)

#### Parameters

lookupMode  

### Method setSFKAutoAuthorizationMode

    public void setSFKAutoAuthorizationMode(boolean sfkMode)

#### Parameters

sfkMode  

### Method new

Initializes a new instance of the Object class.

    public void new(TableId tableId, FieldId fieldId, [int arrayIndex])

#### Parameters

tableId  

<!-- -->

fieldId  

<!-- -->

arrayIndex  

#### Examples

The following example shows how to create an instance of the DictField class.

    DictField df; 
    df = new DictField(tablenum(CustTable), fieldnum(CustTable, AccountNum)); 
    // Check df for successful creation before proceeding. 
    if (!df) 
    { 
    // Take error action. 
    }

## Class DictFieldGroup
    class DictFieldGroup extends Object

The DictFieldGroup class provides information about a specific field group in a table.

### Remarks

For a code example that uses this class, see the DictFieldGroup.numberOfFields Method method.

### Examples

### Methods

| Method                                                                             | Description                                                                         |
|------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| public FieldId field(int fieldNumber)                                              | Returns the specified field from the field group.                                   |
| public str label()                                                                 | Returns the label text of the field group.                                          |
| public str labelId()                                                               | Returns the label ID of the field group.                                            |
| public str methodName(FieldId fieldId)                                             | Returns the name of the specified method from the field group.                      |
| public str name()                                                                  | Returns the name of the field group.                                                |
| public int numberOfFields()                                                        | Returns the number of table fields and edit and display methods in the field group. |
| public TableId tableid()                                                           | Returns the ID of the table that is associated with the field group.                |
| public void new(TableId tableId, str FieldGroupName, \[TableId includeBaseTable\]) | Initializes a new instance of the Object class.                                     |

### Method field

Returns the specified field from the field group.

    public FieldId field(int fieldNumber)

#### Parameters

fieldNumber  
The one-based index to the list of fields in the field group. The index is in the same order as the Microsoft Dynamics 365 for Operations Application Object Tree (AOT).

#### Return Value

The field ID of the field. If the item is a display method, the ID is in the form 65280 + 0-based method index.

#### Remarks

For a code example that uses the Field method, see the DictFieldGroup.numberOfFields Method method.

### Method label

Returns the label text of the field group.

    public str label()

#### Return Value

The label text of the field group.

### Method labelId

Returns the label ID of the field group.

    public str labelId()

#### Return Value

The label ID of the field group.

### Method methodName

Returns the name of the specified method from the field group.

    public str methodName(FieldId fieldId)

#### Parameters

fieldId  
The field ID that is returned from a call to the field method for the method name to return. It is the responsibility of the developer to make sure that a valid field ID is used.

#### Return Value

The name of the specified method from the field group; an empty string if the fieldId value is less than 65280.

#### Remarks

Methods are specified by method index + 65280. For a code example that uses this method, see the DictFieldGroup.numberOfFields Method method.

### Method name

Returns the name of the field group.

    public str name()

#### Return Value

The name of the field group.

### Method numberOfFields

Returns the number of table fields and edit and display methods in the field group.

    public int numberOfFields()

#### Return Value

The number of table fields and edit and display methods in the field group.

#### Examples

The following example shows the retrieval of the number of table fields and edit and display methods in a field group.

        DictFieldGroup  fldGrp; 
        DictField       fld; 
        fieldId         fldId; 
        tableId         tblId; 
        int             i; 
        tblId = tablenum("CustTable"); 
        fldGrp = new DictFieldGroup(tblId,"AutoReport"); 
        if (fldGrp) 
        {     for (i=1; i <= fldGrp.numberOfFields(); i++) 
             { 
                 fldId = fldGrp.field(i); 
                 fld  = new DictField(tblId, fldId); 
                 if (fld) 
                 { 
                    print 'Field: ' + fld.name() 
           + ' (' + int2str(fldId) + ')'; 
                 } 
                 else 
                 { 
                    print 'MethodName: ' + fldGrp.methodName(fldId)  
                    + ' (' + int2str(fldId) + ')'; 
                 } 
             } 
        }

### Method tableid

Returns the ID of the table that is associated with the field group.

    public TableId tableid()

#### Return Value

The ID of the table that is associated with the field group.

### Method new

Initializes a new instance of the Object class.

    public void new(TableId tableId, str FieldGroupName, [TableId includeBaseTable])

#### Parameters

tableId  

<!-- -->

FieldGroupName  

<!-- -->

includeBaseTable  

#### Remarks

For a code example that uses this method, see the DictFieldGroup.numberOfFields Method method.

## Class DictFullTextIndex
    class DictFullTextIndex extends Object

The DictFullTextIndex class returns metadata about a full text index.

### Remarks

### Examples

### Methods

| Method                                                  | Description                                            |
|---------------------------------------------------------|--------------------------------------------------------|
| public FullTextIndexChangeTracking changeTrackingMode() | Gets the change tracking mode of the full text index.  |
| public ConfigurationKeyId configurationKeyId()          | Returns the ID of the configuration key for the index. |
| public IndexId id()                                     | Gets the ID of the full text index.                    |
| public str name()                                       | Gets the name of the full text index.                  |
| public TableId tableid()                                | Returns the ID of the table that contains the index.   |
| public void new(TableId tableId, IndexId indexId)       | Initializes a new instance of the Object class.        |

### Method changeTrackingMode

Gets the change tracking mode of the full text index.

    public FullTextIndexChangeTracking changeTrackingMode()

#### Return Value

### Method configurationKeyId

Returns the ID of the configuration key for the index.

    public ConfigurationKeyId configurationKeyId()

#### Return Value

The ID of the configuration key for the index; 0 (zero) if the index does not have a configuration key.

### Method id

Gets the ID of the full text index.

    public IndexId id()

#### Return Value

The ID of the index.

### Method name

Gets the name of the full text index.

    public str name()

#### Return Value

The name of the index.

### Method tableid

Returns the ID of the table that contains the index.

    public TableId tableid()

#### Return Value

The ID of the table that contains the index.

### Method new

Initializes a new instance of the Object class.

    public void new(TableId tableId, IndexId indexId)

#### Parameters

tableId  

<!-- -->

indexId  

## Class DictIndex
    class DictIndex extends Object

The DictIndex class returns metadata about a table index.

### Remarks

### Examples

The following example creates an instance of the DictIndex class.

    Dictionary dict; 
    DictTable  table; 
    DictIndex  idx; 
    dict = new Dictionary(); 
    table = new DictTable(dict.tableName2Id("Address")); 
    idx = new DictIndex(table.id(), table.indexName2Id("AddrIdx"));

### Methods

| Method                                                                                                                          | Description                                                           |
|---------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------|
| public boolean allowDuplicates()                                                                                                | Returns the value of the allowDuplicates property for the index.      |
| public ConfigurationKeyId configurationKeyId()                                                                                  | Returns the ID of the configuration key for the index.                |
| public boolean enabled()                                                                                                        | Returns a value that indicates whether the index is enabled.          |
| public FieldId field(int fieldNumber)                                                                                           | Returns the ID of the specified field in the index.                   |
| public ValidTimeStateMode getValidTimeStateMode()                                                                               |                                                                       |
| public IndexId id()                                                                                                             | Returns the ID of the index.                                          |
| public FieldId includedColumn(int fieldNumber)                                                                                  |                                                                       |
| public boolean isAlternateKey()                                                                                                 |                                                                       |
| public boolean isSql()                                                                                                          | Gets a value that indicates whether the index is in the SQL database. |
| public boolean isValidTimeStateKey()                                                                                            |                                                                       |
| public boolean modify(boolean enabled, boolean allowDuplicates, boolean saveInLoadedLayer)                                      | Modifies the index.                                                   |
| public str name(\[DbBackend db\])                                                                                               | Returns the name of the index.                                        |
| public int numberOfFields()                                                                                                     | Returns the number of fields in the index definition.                 |
| public int numberOfIncludedColumns()                                                                                            |                                                                       |
| public boolean setAlternateKey(boolean alternateKey, boolean saveInLoadedLayer)                                                 |                                                                       |
| public boolean setValidTimeStateKey(boolean setValidTimeStateKey, ValidTimeStateMode validTimeState, boolean saveInLoadedLayer) |                                                                       |
| public TableId tableid()                                                                                                        | Returns the ID of the table that contains the index.                  |
| public void new(TableId tableId, IndexId indexId)                                                                               | Initializes a new instance of the Object class.                       |

### Method allowDuplicates

Returns the value of the allowDuplicates property for the index.

    public boolean allowDuplicates()

#### Return Value

true if the index allows duplicates; otherwise, false.

### Method configurationKeyId

Returns the ID of the configuration key for the index.

    public ConfigurationKeyId configurationKeyId()

#### Return Value

The ID of the configuration key for the index; 0 (zero) if the index does not have a configuration key.

### Method enabled

Returns a value that indicates whether the index is enabled.

    public boolean enabled()

#### Return Value

true if the index is enabled; otherwise, false.

### Method field

Returns the ID of the specified field in the index.

    public FieldId field(int fieldNumber)

#### Parameters

fieldNumber  
The one-based index of the field in the index.

#### Return Value

The ID of the field that is specified by fieldNumber; 0 (zero) if fieldNumber does not represent a valid field.

#### Examples

The following example shows the retrieval of each field in an index. The name of each field is displayed by using a loop.

    Dictionary dict; 
    DictTable  table; 
    DictIndex  idx; 
    DictField  field; 
    int i; 
    dict = new Dictionary(); 
    table = new DictTable(dict.tableName2Id("Address")); 
    idx = new DictIndex(table.id(), table.indexName2Id("AddrIdx")); 
    for (i=1; i <= idx.numberOfFields(); i++) 
    { 
        field = new DictField(table.id(), idx.field(i)); 
        print field.name(); 
    }

### Method getValidTimeStateMode

    public ValidTimeStateMode getValidTimeStateMode()

#### Return Value

### Method id

Returns the ID of the index.

    public IndexId id()

#### Return Value

The ID of the index.

### Method includedColumn

    public FieldId includedColumn(int fieldNumber)

#### Parameters

fieldNumber  

#### Return Value

### Method isAlternateKey

    public boolean isAlternateKey()

#### Return Value

### Method isSql

Gets a value that indicates whether the index is in the SQL database.

    public boolean isSql()

#### Return Value

true if the index is in the SQL database; otherwise, false.

### Method isValidTimeStateKey

    public boolean isValidTimeStateKey()

#### Return Value

### Method modify

Modifies the index.

    public boolean modify(boolean enabled, boolean allowDuplicates, boolean saveInLoadedLayer)

#### Parameters

enabled  
A Boolean value that indicates whether the modification is saved in the layer that is loaded.

<!-- -->

allowDuplicates  
A Boolean value that indicates whether the modification is saved in the layer that is loaded.

<!-- -->

saveInLoadedLayer  
A Boolean value that indicates whether the modification is saved in the layer that is loaded.

#### Return Value

true if the index was successfully modified; otherwise, false.

#### Remarks

This method lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Method name

Returns the name of the index.

    public str name([DbBackend db])

#### Parameters

db  
A DbBackend value that specifies the type of name to return. This can be DbBackend::Native for the native name of the index or DbBackend::Sql for the SQL name of the index. If db is not specified, DbBackend::Native is used.

#### Return Value

The name of the index in the format that is specified by db.

### Method numberOfFields

Returns the number of fields in the index definition.

    public int numberOfFields()

#### Return Value

The number of fields in the index.

#### Examples

The following example shows the retrieval of the number of fields in the index and lists the names of the fields in the index.

    Dictionary dict; 
    DictTable  table; 
    DictIndex  idx; 
    DictField  field; 
    int i; 
    dict = new Dictionary(); 
    table = new DictTable(dict.tableName2Id("Address")); 
    idx = new DictIndex(table.id(), table.indexName2Id("AddrIdx")); 
    for (i=1; i <= idx.numberOfFields(); i++) 
    { 
        field = new DictField(table.id(), idx.field(i)); 
        print field.name(); 
    }

### Method numberOfIncludedColumns

    public int numberOfIncludedColumns()

#### Return Value

### Method setAlternateKey

    public boolean setAlternateKey(boolean alternateKey, boolean saveInLoadedLayer)

#### Parameters

alternateKey  

<!-- -->

saveInLoadedLayer  

#### Return Value

### Method setValidTimeStateKey

    public boolean setValidTimeStateKey(boolean setValidTimeStateKey, ValidTimeStateMode validTimeState, boolean saveInLoadedLayer)

#### Parameters

setValidTimeStateKey  

<!-- -->

validTimeState  

<!-- -->

saveInLoadedLayer  

#### Return Value

### Method tableid

Returns the ID of the table that contains the index.

    public TableId tableid()

#### Return Value

The ID of the table that contains the index.

### Method new

Initializes a new instance of the Object class.

    public void new(TableId tableId, IndexId indexId)

#### Parameters

tableId  
The ID of the index that is used to create this instance of the DictIndex class.

<!-- -->

indexId  
The ID of the index that is used to create this instance of the DictIndex class.

## Class Dictionary
    class Dictionary extends Object

The Dictionary class provides information about tables, extended data types, classes, and other items in the Microsoft Dynamics 365 for Operations Application Object Tree (AOT).

### Remarks

### Examples

### Methods

| Method                                                                                                                                       | Description                                                                                                      |
|----------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| public int classCnt()                                                                                                                        | Indicates the number of classes in Microsoft Dynamics 365 for Operations.                                                        |
| public ClassId classCnt2Id(int cnt)                                                                                                          | Provides the ID of a specified class.                                                                            |
| public str className(ClassId classId)                                                                                                        | Provides the name of a specified class.                                                                          |
| public ClassId className2Id(str name)                                                                                                        | Provides the ID for a specified class, based on the class name.                                                  |
| public ClassId classNext(ClassId classId)                                                                                                    | Indicates the class that succeeds a specified class, based on the class IDs.                                     |
| public DictClass classObject(ClassId classId)                                                                                                | Provides information about a specified class by returning a DictClass object.                                    |
| public int configurationKeyCnt()                                                                                                             | Indicates the number of configuration keys in Microsoft Dynamics 365 for Operations.                                             |
| public ConfigurationKeyId configurationKeyCnt2Id(int cnt)                                                                                    | Provides the ID of a specified configuration key.                                                                |
| public str configurationKeyName(ConfigurationKeyId configurationKey)                                                                         | Provides the name of a specified configuration key.                                                              |
| public ConfigurationKeyId configurationKeyName2Id(str name)                                                                                  | Provides the ID for a specified configuration key, based on the configuration key name.                          |
| public ConfigurationKeyId configurationKeyNext(ConfigurationKeyId configurationKey)                                                          | Indicates the configuration key that succeeds a specified configuration key, based on the configuration key IDs. |
| public DictConfigurationKey configurationKeyObject(ConfigurationKeyId configurationKey)                                                      | Provides information about a specified configuration key by returning a DictConfigurationKey object.             |
| public SelectableDataArea currentCompany()                                                                                                   | Indicates the current company for which data is available in the database.                                       |
| public int enumCnt()                                                                                                                         | Indicates the number of enumeration types in Microsoft Dynamics 365 for Operations.                                              |
| public EnumId enumCnt2Id(int cnt)                                                                                                            | Provides the ID of a specified enumeration type.                                                                 |
| public str enumName(EnumId typeId)                                                                                                           | Provides the name for a specified enumeration.                                                                   |
| public EnumId enumName2Id(str name)                                                                                                          | Provides the ID of a specified enumeration, based on the name.                                                   |
| public EnumId enumNext(EnumId typeId)                                                                                                        | Indicates the enumeration type that succeeds a specified enumeration type, based on the enumeration type IDs.    |
| public DictEnum enumObject(EnumId typeId)                                                                                                    | Provides information about a specified enumeration by returning a DictEnum object.                               |
| public int licenseCodeCnt()                                                                                                                  | Indicates the number of license codes in Microsoft Dynamics 365 for Operations.                                                  |
| public LicenseCodeId licenseCodeCnt2Id(int cnt)                                                                                              | Provides the ID of a specified license code.                                                                     |
| public str licenseCodeName(LicenseCodeId licenseCode)                                                                                        | Provides the name of a specified license code.                                                                   |
| public LicenseCodeId licenseCodeName2Id(str name)                                                                                            | Provides the ID for a specified license code, based on the license code name.                                    |
| public LicenseCodeId licenseCodeNext(LicenseCodeId licenseCode)                                                                              | Indicates the license code that succeeds a specified license code, based on the license code IDs.                |
| public DictLicenseCode licenseCodeObject(LicenseCodeId licenseCode)                                                                          | Provides information about a specified license code by returning a DictLicenseCode object.                       |
| public int tableCnt()                                                                                                                        | Indicates the number of tables in Microsoft Dynamics 365 for Operations.                                                         |
| public TableId tableCnt2Id(int cnt)                                                                                                          | Provides the ID of a specified table.                                                                            |
| public str tableName(TableId tableId)                                                                                                        | Provides the name of a specified table.                                                                          |
| public TableId tableName2Id(str name)                                                                                                        | Provides the ID for a specified table, based on the table name.                                                  |
| public TableId tableNext(TableId tableId)                                                                                                    | Indicates the table that succeeds a specified table, based on the table IDs.                                     |
| public DictTable tableObject(TableId tableId)                                                                                                | Provides information about a specified table by returning a DictTable object.                                    |
| public boolean tableSql(TableId tableId)                                                                                                     | Indicates whether a table is a SQL table.                                                                        |
| public boolean tableSystem(TableId tableId)                                                                                                  | Indicates whether a table is a system table.                                                                     |
| public int testCode(int id, str value, str name, str serialno, str expiryDate, \[int userCount\], \[boolean verifyCert\], \[str timestamp\]) |                                                                                                                  |
| public int typeCnt()                                                                                                                         | Indicates the number of extended data types in Microsoft Dynamics 365 for Operations.                                            |
| public ExtendedTypeId typeCnt2Id(int cnt)                                                                                                    | Provides the ID of a specified extended data type.                                                               |
| public str typeName(ExtendedTypeId typeId)                                                                                                   | Provides the name of a specified extended data type.                                                             |
| public ExtendedTypeId typeName2Id(str name)                                                                                                  | Provides the ID for a specified extended data type, based on the extended data type name.                        |
| public ExtendedTypeId typeNext(ExtendedTypeId typeId)                                                                                        | Indicates the extended data type that succeeds a specified extended data type, based on the IDs.                 |
| public DictType typeObject(ExtendedTypeId typeId)                                                                                            | Provides information about a specified extended data type by returning a DictType object.                        |
| ::public static boolean safeMode()                                                                                                           |                                                                                                                  |
| ::public static void loginSettingsFlush()                                                                                                    | Refreshes the logon settings for Microsoft Dynamics 365 for Operations.                                                          |
| ::public static void dataFlush(\[TableId tableId\])                                                                                          | Refreshes the table data in Microsoft Dynamics 365 for Operations.                                                               |
| public void tableFlush()                                                                                                                     | Refreshes the tables in Microsoft Dynamics 365 for Operations.                                                                   |
| public void enumFlush()                                                                                                                      | Refreshes the enumeration types in Microsoft Dynamics 365 for Operations.                                                        |
| public void new()                                                                                                                            | Initializes a new instance of the Dictionary class.                                                              |
| public void classFlush()                                                                                                                     | Refreshes the classes in Microsoft Dynamics 365 for Operations.                                                                  |
| public void reloadSecurity(\[boolean reloadCodes\], \[boolean setSynchronizeRequired\], \[boolean flushTable\])                              | Reloads the feature key system.                                                                                  |
| public void typeFlush()                                                                                                                      | Refreshes the extended data types in Microsoft Dynamics 365 for Operations.                                                      |
| public void configurationKeyFlush()                                                                                                          | Refreshes the configuration keys in Microsoft Dynamics 365 for Operations.                                                       |
| public void licenseCodeFlush()                                                                                                               | Refreshes the license codes in Microsoft Dynamics 365 for Operations.                                                            |
| ::public static void aodFlush()                                                                                                              | Refreshes the .aod file.                                                                                         |

### Method classCnt

Indicates the number of classes in Microsoft Dynamics 365 for Operations.

    public int classCnt()

#### Return Value

An integer value that indicates the number of classes.

### Method classCnt2Id

Provides the ID of a specified class.

    public ClassId classCnt2Id(int cnt)

#### Parameters

cnt  
An integer value that specifies a class, based on the order of classes in Microsoft Dynamics 365 for Operations.

#### Return Value

A classId system data type value that indicates the class ID; 0 (zero) if you pass a cnt value that is larger than the number of classes that is returned by the Dictionary::classCnt method.

### Method className

Provides the name of a specified class.

    public str className(ClassId classId)

#### Parameters

classId  
A classId system data type that indicates the class ID.

#### Return Value

A string that indicates the class name.

#### Remarks

Class IDs are unsigned integers.

### Method className2Id

Provides the ID for a specified class, based on the class name.

    public ClassId className2Id(str name)

#### Parameters

name  
A string that indicates the class name.

#### Return Value

A classId system data type value that indicates the class ID; 0 (zero) if you pass a name value for a nonexistent class.

### Method classNext

Indicates the class that succeeds a specified class, based on the class IDs.

    public ClassId classNext(ClassId classId)

#### Parameters

classId  
A classId system data type that indicates a class ID.

#### Return Value

A classId system data type value that indicates the class that succeeds the specified class.

### Method classObject

Provides information about a specified class by returning a DictClass object.

    public DictClass classObject(ClassId classId)

#### Parameters

classId  
A classId system data type that indicates a class ID.

#### Return Value

A DictClass object that contains information about the specified class.

### Method configurationKeyCnt

Indicates the number of configuration keys in Microsoft Dynamics 365 for Operations.

    public int configurationKeyCnt()

#### Return Value

An integer value that indicates the number of configuration keys.

### Method configurationKeyCnt2Id

Provides the ID of a specified configuration key.

    public ConfigurationKeyId configurationKeyCnt2Id(int cnt)

#### Parameters

cnt  
An integer that specifies a configuration key, based on the order of configuration keys in Microsoft Dynamics 365 for Operations.

#### Return Value

A configurationKeyId system data type value that indicates a configuration key ID; 0 (zero) if you pass a cnt value that is larger than the number of configuration keys that is returned by the Dictionary::configurationKeyCnt method.

### Method configurationKeyName

Provides the name of a specified configuration key.

    public str configurationKeyName(ConfigurationKeyId configurationKey)

#### Parameters

configurationKey  
A configurationKeyId system data type that indicates a configuration key ID.

#### Return Value

A string that indicates the name of the configuration key.

### Method configurationKeyName2Id

Provides the ID for a specified configuration key, based on the configuration key name.

    public ConfigurationKeyId configurationKeyName2Id(str name)

#### Parameters

name  
A string that indicates a configuration key name.

#### Return Value

A configurationKeyId system data type value that indicates the configuration key ID; 0 (zero) if you pass a name value for a nonexistent configuration key.

### Method configurationKeyNext

Indicates the configuration key that succeeds a specified configuration key, based on the configuration key IDs.

    public ConfigurationKeyId configurationKeyNext(ConfigurationKeyId configurationKey)

#### Parameters

configurationKey  
A configurationKeyId system data type that indicates a configuration key ID.

#### Return Value

A configurationKeyId system data type value for the configuration key that succeeds the specified configuration key.

### Method configurationKeyObject

Provides information about a specified configuration key by returning a DictConfigurationKey object.

    public DictConfigurationKey configurationKeyObject(ConfigurationKeyId configurationKey)

#### Parameters

configurationKey  
A configurationKeyId system data type that indicates a configuration key ID.

#### Return Value

A DictConfigurationKey object that contains information about the specified configuration key.

### Method currentCompany

Indicates the current company for which data is available in the database.

    public SelectableDataArea currentCompany()

#### Return Value

A selectableDataArea system data type value that indicates the current company.

### Method enumCnt

Indicates the number of enumeration types in Microsoft Dynamics 365 for Operations.

    public int enumCnt()

#### Return Value

An integer that indicates the number of enumeration types.

### Method enumCnt2Id

Provides the ID of a specified enumeration type.

    public EnumId enumCnt2Id(int cnt)

#### Parameters

cnt  
An integer that specifies an enumeration type, based on the order of enumeration types in Microsoft Dynamics 365 for Operations.

#### Return Value

An enumId system data type value that indicates the enumeration type ID; 0 (zero) if you pass a cnt value that is larger than the number of classes that is returned by the Dictionary::enumCnt method.

### Method enumName

Provides the name for a specified enumeration.

    public str enumName(EnumId typeId)

#### Parameters

typeId  
An enumId system data type for an enumeration.

#### Return Value

A string that indicates the name of the enumeration.

### Method enumName2Id

Provides the ID of a specified enumeration, based on the name.

    public EnumId enumName2Id(str name)

#### Parameters

name  
A string that indicates the name of an enumeration.

#### Return Value

An enumId system data type value that indicates the ID of the enumeration.

### Method enumNext

Indicates the enumeration type that succeeds a specified enumeration type, based on the enumeration type IDs.

    public EnumId enumNext(EnumId typeId)

#### Parameters

typeId  
An enumId system data type that indicates an enumeration ID.

#### Return Value

An enumId system data type value for the enumeration that succeeds the specified enumeration.

### Method enumObject

Provides information about a specified enumeration by returning a DictEnum object.

    public DictEnum enumObject(EnumId typeId)

#### Parameters

typeId  
An enumId system data type that indicates an enumeration ID.

#### Return Value

A DictEnum object that contains information about the specified enumeration.

### Method licenseCodeCnt

Indicates the number of license codes in Microsoft Dynamics 365 for Operations.

    public int licenseCodeCnt()

#### Return Value

An integer that indicates the number of license codes.

### Method licenseCodeCnt2Id

Provides the ID of a specified license code.

    public LicenseCodeId licenseCodeCnt2Id(int cnt)

#### Parameters

cnt  
An integer that specifies a license code, based on the order of license codes in Microsoft Dynamics 365 for Operations.

#### Return Value

A licenseCodeId system data type value that indicates the license code ID; 0 (zero) if you pass a cnt value that is larger than the number of license codes that is returned by the Dictionary::licenseCodeCnt method.

### Method licenseCodeName

Provides the name of a specified license code.

    public str licenseCodeName(LicenseCodeId licenseCode)

#### Parameters

licenseCode  
A licenseCodeId system data type that indicates the license code ID.

#### Return Value

A string that indicates the license code name.

### Method licenseCodeName2Id

Provides the ID for a specified license code, based on the license code name.

    public LicenseCodeId licenseCodeName2Id(str name)

#### Parameters

name  
A string that indicates the license code name.

#### Return Value

A licenseCodeId system data type value that indicates the license code ID; 0 (zero) if you pass a name value for a nonexistent license code.

### Method licenseCodeNext

Indicates the license code that succeeds a specified license code, based on the license code IDs.

    public LicenseCodeId licenseCodeNext(LicenseCodeId licenseCode)

#### Parameters

licenseCode  
A licenseCodeId system data type that indicates a license code ID.

#### Return Value

A licenseCodeId system data type value for the license code that succeeds the specified license code.

### Method licenseCodeObject

Provides information about a specified license code by returning a DictLicenseCode object.

    public DictLicenseCode licenseCodeObject(LicenseCodeId licenseCode)

#### Parameters

licenseCode  
A licenseCodeId system data that indicates a license code ID.

#### Return Value

A DictLicenseCode object that contains information about the specified license code.

### Method tableCnt

Indicates the number of tables in Microsoft Dynamics 365 for Operations.

    public int tableCnt()

#### Return Value

An integer that indicates the number of tables.

### Method tableCnt2Id

Provides the ID of a specified table.

    public TableId tableCnt2Id(int cnt)

#### Parameters

cnt  
An integer that specifies a table, based on the order of tables.

#### Return Value

A tableId system data type value that indicates the table ID; 0 (zero) if you pass a cnt value that is larger than the number of tables that is returned by the Dictionary::tableCnt method.

### Method tableName

Provides the name of a specified table.

    public str tableName(TableId tableId)

#### Parameters

tableId  
A tableId system data type that indicates the table ID.

#### Return Value

A string that indicates the table name; UNKNOWN if you pass a tableId value that does not exist.

#### Remarks

The method returns UNKNOWN if you pass a tableId value that does not exist.

### Method tableName2Id

Provides the ID for a specified table, based on the table name.

    public TableId tableName2Id(str name)

#### Parameters

name  
A string that indicates the table name.

#### Return Value

A tableId system data type value that indicates the table ID; 0 (zero) if you pass a name value for a nonexistent table.

### Method tableNext

Indicates the table that succeeds a specified table, based on the table IDs.

    public TableId tableNext(TableId tableId)

#### Parameters

tableId  
A tableId system data type that indicates a table ID.

#### Return Value

A tableId system data type value for the table that succeeds the specified table.

### Method tableObject

Provides information about a specified table by returning a DictTable object.

    public DictTable tableObject(TableId tableId)

#### Parameters

tableId  
A tableId system data type that indicates a table ID.

#### Return Value

A DictTable object that contains information about the specified table.

### Method tableSql

Indicates whether a table is a SQL table.

    public boolean tableSql(TableId tableId)

#### Parameters

tableId  
A tableId system data type that indicates the table ID.

#### Return Value

true if the table is a SQL table; otherwise, false.

### Method tableSystem

Indicates whether a table is a system table.

    public boolean tableSystem(TableId tableId)

#### Parameters

tableId  
A tableId system data type that indicates a table ID.

#### Return Value

true if the table is a system table; otherwise, false.

#### Remarks

You can pass a table name to this method instead of a table ID by using the tableNum intrinsic function. For more information, see Intrinsic Functions.

### Method testCode

    public int testCode(int id, str value, str name, str serialno, str expiryDate, [int userCount], [boolean verifyCert], [str timestamp])

#### Parameters

id  

<!-- -->

value  

<!-- -->

name  

<!-- -->

serialno  

<!-- -->

expiryDate  

<!-- -->

userCount  

<!-- -->

verifyCert  

<!-- -->

timestamp  

#### Return Value

### Method typeCnt

Indicates the number of extended data types in Microsoft Dynamics 365 for Operations.

    public int typeCnt()

#### Return Value

An integer that indicates the number of extended data types.

### Method typeCnt2Id

Provides the ID of a specified extended data type.

    public ExtendedTypeId typeCnt2Id(int cnt)

#### Parameters

cnt  
An integer that specifies an extended data type, based on the order of extended data types in Microsoft Dynamics 365 for Operations.

#### Return Value

An extendedTypeId system data type value that indicates the ID of the extended data type; 0 (zero) if you pass a cnt value that is larger than the number of extended data types that is returned by the Dictionary::typeCnt method.

### Method typeName

Provides the name of a specified extended data type.

    public str typeName(ExtendedTypeId typeId)

#### Parameters

typeId  
An extendedTypeId system data type that indicates the ID of an extended data type.

#### Return Value

A string that indicates the name of the extended data type.

### Method typeName2Id

Provides the ID for a specified extended data type, based on the extended data type name.

    public ExtendedTypeId typeName2Id(str name)

#### Parameters

name  
A string that indicates the name of the extended data type.

#### Return Value

An extendedTypeId system data type value that indicates the ID of the extended data type; 0 (zero) if you pass a name value for a nonexistent extended data type.

### Method typeNext

Indicates the extended data type that succeeds a specified extended data type, based on the IDs.

    public ExtendedTypeId typeNext(ExtendedTypeId typeId)

#### Parameters

typeId  
An extendedTypeId system data type that indicates the ID for an extended data type.

#### Return Value

An extendedTypeId system data type value for the extended data type that succeeds the specified extended data type.

### Method typeObject

Provides information about a specified extended data type by returning a DictType object.

    public DictType typeObject(ExtendedTypeId typeId)

#### Parameters

typeId  
An extendedTypeId system data type that indicates the ID for an extended data type.

#### Return Value

A DictType object that contains information about the specified extended data type.

### Method safeMode

    public static boolean safeMode()

#### Return Value

### Method loginSettingsFlush

Refreshes the logon settings for Microsoft Dynamics 365 for Operations.

    public static void loginSettingsFlush()

### Method dataFlush

Refreshes the table data in Microsoft Dynamics 365 for Operations.

    public static void dataFlush([TableId tableId])

#### Parameters

tableId  
A tableId system data type that indicates a single table or all tables. The default value is ALL.

#### Remarks

By default, this method refreshes data in all tables.

### Method tableFlush

Refreshes the tables in Microsoft Dynamics 365 for Operations.

    public void tableFlush()

### Method enumFlush

Refreshes the enumeration types in Microsoft Dynamics 365 for Operations.

    public void enumFlush()

### Method new

Initializes a new instance of the Dictionary class.

    public void new()

### Method classFlush

Refreshes the classes in Microsoft Dynamics 365 for Operations.

    public void classFlush()

### Method reloadSecurity

Reloads the feature key system.

    public void reloadSecurity([boolean reloadCodes], [boolean setSynchronizeRequired], [boolean flushTable])

#### Parameters

reloadCodes  

<!-- -->

setSynchronizeRequired  

<!-- -->

flushTable  

#### Remarks

The default value for the \_reloadCodes parameter is false. The default value for the \_setSynchronizeRequired parameter is true.

### Method typeFlush

Refreshes the extended data types in Microsoft Dynamics 365 for Operations.

    public void typeFlush()

### Method configurationKeyFlush

Refreshes the configuration keys in Microsoft Dynamics 365 for Operations.

    public void configurationKeyFlush()

### Method licenseCodeFlush

Refreshes the license codes in Microsoft Dynamics 365 for Operations.

    public void licenseCodeFlush()

### Method aodFlush

Refreshes the .aod file.

    public static void aodFlush()

## Class DictLicenseCode
    class DictLicenseCode extends Object

### Remarks

### Examples

### Methods

| Method                                       | Description                                     |
|----------------------------------------------|-------------------------------------------------|
| public LicenseCodeGroup group()              |                                                 |
| public LicenseCodeId id()                    |                                                 |
| public str label()                           |                                                 |
| public str name()                            |                                                 |
| public SysLicensePackageType package()       |                                                 |
| public int publicKey()                       |                                                 |
| public LicenseCodeType type()                |                                                 |
| public void new(LicenseCodeId licenseCodeId) | Initializes a new instance of the Object class. |

### Method group

    public LicenseCodeGroup group()

#### Return Value

### Method id

    public LicenseCodeId id()

#### Return Value

### Method label

    public str label()

#### Return Value

### Method name

    public str name()

#### Return Value

### Method package

    public SysLicensePackageType package()

#### Return Value

### Method publicKey

    public int publicKey()

#### Return Value

### Method type

    public LicenseCodeType type()

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(LicenseCodeId licenseCodeId)

#### Parameters

licenseCodeId  

## Class DictMethod
    class DictMethod extends MethodInfo

### Remarks

### Examples

### Methods

| Method                                                      | Description                                                                                                                                                  |
|-------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public AccessSpecifier accessSpecifier()                    | Specifies whether the method is public, protected, or private.                                                                                               |
| public str clrParameterType(int variableNumber)             |                                                                                                                                                              |
| public str clrReturnType()                                  |                                                                                                                                                              |
| public str clrVarType(int variableNumber)                   |                                                                                                                                                              |
| public boolean compiledOk()                                 | Indicates whether the method compiled successfully.                                                                                                          |
| public TableId displayId()                                  |                                                                                                                                                              |
| public DisplayFunctionType displayType()                    | Indicates the type of display function of a method.                                                                                                          |
| public boolean hasImplementation()                          | Determines whether the actual method implementation is on the class or derived from the base class.                                                          |
| public boolean isAbstract()                                 | Indicates whether the method is abstract.                                                                                                                    |
| public boolean isDelegate()                                 | Indicates whether the method is a delegate.                                                                                                                  |
| public boolean isStatic()                                   | Indicates whether the method is static.                                                                                                                      |
| public str name()                                           | Gets the name of the method.                                                                                                                                 |
| public int parameterCnt()                                   | Gets the number of parameters for the method.                                                                                                                |
| public int parameterId(int variableNumber)                  | Gets the ID of the specified parameter.                                                                                                                      |
| public str parameterName(int variableNumber)                | Gets the name of the specified parameter.                                                                                                                    |
| public boolean parameterOptional(int variableNumber)        | Indicates whether the specified parameter of the method is optional.                                                                                         |
| public Types parameterType(int variableNumber)              |                                                                                                                                                              |
| public int parentId()                                       | Gets the ID of the parent that owns the method.                                                                                                              |
| public str propertyHelp()                                   | Gets the Help string for the property that is associated with the method.                                                                                    |
| public NoYes propertyMethod()                               | Indicates whether the method is a property method.                                                                                                           |
| public int returnId()                                       | Specifies the ID for certain return data types, such as extended data types and classes, for a method that returns a value.                                  |
| public Types returnType()                                   | Specifies a method return type.                                                                                                                              |
| public ClassRunMode runMode()                               | Specifies where a method is run.                                                                                                                             |
| public int varCnt()                                         | Gets the number of variables for the method.                                                                                                                 |
| public str varName(int variableNumber)                      | Gets the name of the specified variable.                                                                                                                     |
| public void setMethod(MemberFunction method)                | Specifies the application object type of a node in the Microsoft Dynamics 365 for Operations Application Object Tree (AOT) by using an instance of the MemberFunction class. |
| public void new(UtilElementType utilType, int id, str name) | Initializes a new instance of the Object class.                                                                                                              |

### Method accessSpecifier

Specifies whether the method is public, protected, or private.

    public AccessSpecifier accessSpecifier()

#### Return Value

An AccessSpecifier enumeration value that specifies whether the method is public, protected, or private.

### Method clrParameterType

    public str clrParameterType(int variableNumber)

#### Parameters

variableNumber  

#### Return Value

### Method clrReturnType

    public str clrReturnType()

#### Return Value

### Method clrVarType

    public str clrVarType(int variableNumber)

#### Parameters

variableNumber  

#### Return Value

### Method compiledOk

Indicates whether the method compiled successfully.

    public boolean compiledOk()

#### Return Value

true if the method compiled successfully; otherwise, false.

### Method displayId

    public TableId displayId()

#### Return Value

### Method displayType

Indicates the type of display function of a method.

    public DisplayFunctionType displayType()

#### Return Value

A DisplayFunctionType enumeration value that indicates the display function type of a method.

#### Remarks

The following table lists the possible values that are returned by the displayType method.

|           |                                             |
|-----------|---------------------------------------------|
| Get       | The method is a display method.             |
| None      | The method is not a display or edit method. |
| RecordGet | The method retrieves a record.              |
| RecordSet | The method sets a record.                   |
| Set       | The method is an edit method.               |

### Method hasImplementation

Determines whether the actual method implementation is on the class or derived from the base class.

    public boolean hasImplementation()

#### Return Value

true if the method is implemented on the class; otherwise, false.

### Method isAbstract

Indicates whether the method is abstract.

    public boolean isAbstract()

#### Return Value

true if the method is abstract; otherwise, false.

### Method isDelegate

Indicates whether the method is a delegate.

    public boolean isDelegate()

#### Return Value

true if the method is a delegate; otherwise, false.

### Method isStatic

Indicates whether the method is static.

    public boolean isStatic()

#### Return Value

true if the method is a static; otherwise, false.

### Method name

Gets the name of the method.

    public str name()

#### Return Value

The name of the method.

### Method parameterCnt

Gets the number of parameters for the method.

    public int parameterCnt()

#### Return Value

The number of parameters for the method.

### Method parameterId

Gets the ID of the specified parameter.

    public int parameterId(int variableNumber)

#### Parameters

variableNumber  
The one-based index to the parameter list for the method.

#### Return Value

The ID of the specified parameter.

### Method parameterName

Gets the name of the specified parameter.

    public str parameterName(int variableNumber)

#### Parameters

variableNumber  
The one-based index to the parameter list for the method.

#### Return Value

The name of the specified parameter.

### Method parameterOptional

Indicates whether the specified parameter of the method is optional.

    public boolean parameterOptional(int variableNumber)

#### Parameters

variableNumber  
The one-based index to the parameter list for the method.

#### Return Value

true if the parameter is optional; otherwise, false.

### Method parameterType

    public Types parameterType(int variableNumber)

#### Parameters

variableNumber  

#### Return Value

### Method parentId

Gets the ID of the parent that owns the method.

    public int parentId()

#### Return Value

The ID of the parent that owns the method.

### Method propertyHelp

Gets the Help string for the property that is associated with the method.

    public str propertyHelp()

#### Return Value

The Help string for the property that is associated with the method; an empty string if there is no Help string.

#### Remarks

This method calls the DictMethod::propertyMethod method to determine whether the method is a property method.

### Method propertyMethod

Indicates whether the method is a property method.

    public NoYes propertyMethod()

#### Return Value

A NoYes::No enumeration value if the method is a property method; otherwise, a NoYes::Yes enumeration value.

### Method returnId

Specifies the ID for certain return data types, such as extended data types and classes, for a method that returns a value.

    public int returnId()

#### Return Value

The ID for the return data type; 0 (zero) if the data type does not have an ID or a method does not return a value..

### Method returnType

Specifies a method return type.

    public Types returnType()

#### Return Value

A Types enumeration value that indicates the method return type.

#### Remarks

The following list shows the possible values:

-   AnyType
-   BLOB
-   Class
-   Container
-   Date
-   DateTime
-   Enum
-   Grid
-   Int64
-   Integer
-   Real
-   Record
-   RString
-   String
-   UserType
-   VarString
-   void

### Method runMode

Specifies where a method is run.

    public ClassRunMode runMode()

#### Return Value

A ClassRunMode enumeration value that indicates where a method is run.

#### Remarks

The following list shows the possible values:

-   Called
-   Client
-   ClientorServer
-   Server

### Method varCnt

Gets the number of variables for the method.

    public int varCnt()

#### Return Value

The number of local and inherited variables for the method.

### Method varName

Gets the name of the specified variable.

    public str varName(int variableNumber)

#### Parameters

variableNumber  
The one-based index to the variable list for the method.

#### Return Value

The name of the specified variable.

### Method setMethod

Specifies the application object type of a node in the Microsoft Dynamics 365 for Operations Application Object Tree (AOT) by using an instance of the MemberFunction class.

    public void setMethod(MemberFunction method)

#### Parameters

method  
An instance of the MemberFunction class that represents a node in the AOT.

### Method new

Initializes a new instance of the Object class.

    public void new(UtilElementType utilType, int id, str name)

#### Parameters

utilType  

<!-- -->

id  

<!-- -->

name  

## Class DictRelation
    class DictRelation extends Object

The DictRelation class can be used to manage dictionary relations for the tables.

### Remarks

### Examples

### Methods

| Method                                                                                                                | Description                                                          |
|-----------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| public Cardinality Cardinality()                                                                                      | Retrieves the cardinality value.                                     |
| public boolean createNavigationPropertyMethods()                                                                      |                                                                      |
| public boolean EDTRelation()                                                                                          | Retrieves the extended data type (EDT) relation state.               |
| public str entityRelationshipRole()                                                                                   | Retrieves the name of the entity relationship role.                  |
| public str entityRelationshipRoleLabelId()                                                                            | Retrieves the label ID for the name of the entity relationship role. |
| public TableId externTable()                                                                                          | Returns the ID of the external table that is used for the relation.  |
| public boolean isSelfLink()                                                                                           | Verifies whether the relation is self-linked.                        |
| public int lineExternTableValue(int lineNumber)                                                                       | Retrieves the external table value for the given line.               |
| public int lines()                                                                                                    | Retrieves the number of the lines in the relation.                   |
| public int lineSourceEDT(int lineNumber)                                                                              | Retrieves the source EDT value for the given table line.             |
| public RelationshipSubType lineSubType(int lineNumber)                                                                | Retrieves the sub-type for the given table line.                     |
| public int lineTableValue(int lineNumber)                                                                             | Retrieves the value for the given table line.                        |
| public TableRelation lineType(int lineNumber)                                                                         | Retrieves the relation type for the given table line.                |
| public TableId loadFieldRelation(FieldId fieldId, \[TableScope tableScope\], \[Common record\], \[boolean isLookup\]) | Loads a relation that is specified by a field ID.                    |
| public TableId loadNameRelation(str name)                                                                             | Loads the relation for the given name.                               |
| public TableId loadTableRelation(TableId tableId, \[TableScope tableScope\], \[Common record\])                       | Loads a table relation.                                              |
| public str navigationPropertyNameOverride()                                                                           |                                                                      |
| public RelatedTableCardinality RelatedTableCardinality()                                                              | Retrieves the cardinality for the related table.                     |
| public str RelatedTableRole()                                                                                         | Retrieves the role name for the related table.                       |
| public RelationshipType relationshipType()                                                                            | Retrieves the relationship type.                                     |
| public str Role()                                                                                                     | Retrieves the role name.                                             |
| public TableId table()                                                                                                | Returns the table ID of the relation.                                |
| public boolean useDefaultRoleNames()                                                                                  |                                                                      |
| public boolean validate()                                                                                             | Validates a relation.                                                |
| ::public static boolean isSurrogateForeignKeyRelation(TableId tableId, str relationName)                              | Verifies whether there is surrogate foreign key relation.            |
| public void new(int id, \[UtilElementType Util\_Element\_Type\], \[int index\])                                       | Initializes a new instance of the Object class.                      |

### Method Cardinality

Retrieves the cardinality value.

    public Cardinality Cardinality()

#### Return Value

The cardinality value.

### Method createNavigationPropertyMethods

    public boolean createNavigationPropertyMethods()

#### Return Value

### Method EDTRelation

Retrieves the extended data type (EDT) relation state.

    public boolean EDTRelation()

#### Return Value

A Boolean value that indicates whether the EDT relation is available.

### Method entityRelationshipRole

Retrieves the name of the entity relationship role.

    public str entityRelationshipRole()

#### Return Value

The name of the entity relationship role.

### Method entityRelationshipRoleLabelId

Retrieves the label ID for the name of the entity relationship role.

    public str entityRelationshipRoleLabelId()

#### Return Value

The label ID for the entity relationship role.

### Method externTable

Returns the ID of the external table that is used for the relation.

    public TableId externTable()

#### Return Value

The ID of the external table that is used for the relation; 0 (zero) if the relation has not yet been loaded.

#### Examples

The following example shows the retrieval of the external table ID.

    Dictionary dict; 
    DictRelation dr; 
    int i;  
    dict = new Dictionary(); 
    dr = new DictRelation(dict.tableName2Id("CustTable")); 
    // Load a relation by name 
    dr.loadNameRelation("CompanyData");  // Also returns the external table ID. 
    print "The external table ID is: " + int2str(dr.externTable());

### Method isSelfLink

Verifies whether the relation is self-linked.

    public boolean isSelfLink()

#### Return Value

true if the relation is self-linked; otherwise, false.

### Method lineExternTableValue

Retrieves the external table value for the given line.

    public int lineExternTableValue(int lineNumber)

#### Parameters

lineNumber  

#### Return Value

The external table value.

### Method lines

Retrieves the number of the lines in the relation.

    public int lines()

#### Return Value

The number of the lines.

### Method lineSourceEDT

Retrieves the source EDT value for the given table line.

    public int lineSourceEDT(int lineNumber)

#### Parameters

lineNumber  

#### Return Value

The source EDT value.

### Method lineSubType

Retrieves the sub-type for the given table line.

    public RelationshipSubType lineSubType(int lineNumber)

#### Parameters

lineNumber  

#### Return Value

The sub-type for the given table line.

### Method lineTableValue

Retrieves the value for the given table line.

    public int lineTableValue(int lineNumber)

#### Parameters

lineNumber  

#### Return Value

The value for the table line.

### Method lineType

Retrieves the relation type for the given table line.

    public TableRelation lineType(int lineNumber)

#### Parameters

lineNumber  

#### Return Value

The table relation type for the given line.

### Method loadFieldRelation

Loads a relation that is specified by a field ID.

    public TableId loadFieldRelation(FieldId fieldId, [TableScope tableScope], [Common record], [boolean isLookup])

#### Parameters

fieldId  

<!-- -->

tableScope  

<!-- -->

record  

<!-- -->

isLookup  

#### Return Value

The ID of the table for the relation; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the method failed.

### Method loadNameRelation

Loads the relation for the given name.

    public TableId loadNameRelation(str name)

#### Parameters

name  

#### Return Value

The table ID for the table relation.

### Method loadTableRelation

Loads a table relation.

    public TableId loadTableRelation(TableId tableId, [TableScope tableScope], [Common record])

#### Parameters

tableId  

<!-- -->

tableScope  

<!-- -->

record  

#### Return Value

The table ID for the table relation.

### Method navigationPropertyNameOverride

    public str navigationPropertyNameOverride()

#### Return Value

### Method RelatedTableCardinality

Retrieves the cardinality for the related table.

    public RelatedTableCardinality RelatedTableCardinality()

#### Return Value

The cardinality for the related table.

### Method RelatedTableRole

Retrieves the role name for the related table.

    public str RelatedTableRole()

#### Return Value

The role name for the related table.

### Method relationshipType

Retrieves the relationship type.

    public RelationshipType relationshipType()

#### Return Value

The relationship type.

### Method Role

Retrieves the role name.

    public str Role()

#### Return Value

The role name.

### Method table

Returns the table ID of the relation.

    public TableId table()

#### Return Value

The table ID of the relation.

#### Examples

The following example shows the retrieval of the table ID for a relation.

    Dictionary dict; 
    DictRelation dr; 
    dict = new Dictionary(); 
    dr = new DictRelation(dict.tableName2Id("CustTable")); 
    print dr.table();

### Method useDefaultRoleNames

    public boolean useDefaultRoleNames()

#### Return Value

### Method validate

Validates a relation.

    public boolean validate()

#### Return Value

true if the relation is valid; otherwise, false.

### Method isSurrogateForeignKeyRelation

Verifies whether there is surrogate foreign key relation.

    public static boolean isSurrogateForeignKeyRelation(TableId tableId, str relationName)

#### Parameters

tableId  

<!-- -->

relationName  

#### Return Value

true if there is a surrogate foreign key relation; otherwise, false.

### Method new

Initializes a new instance of the Object class.

    public void new(int id, [UtilElementType Util_Element_Type], [int index])

#### Parameters

id  
The relation index; optional. The default value is 1.

<!-- -->

Util\_Element\_Type  
The relation index; optional. The default value is 1.

<!-- -->

index  
The relation index; optional. The default value is 1.

## Class DictTable
    class DictTable extends Object

The DictTable class provides information about a table.

### Remarks

### Examples

The following example shows how to create an instance of the DictTable class to determine whether the data in the table is stored on a per-company basis.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print (strfmt("The table is saved on a %1 basis.", dt.dataPrCompany() ? 
                          "per company" : "global")); 
    }

### Methods

| Method                                                                                                                                      | Description                                                                                                                                                               |
|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean doesMethodExist(str name)                                                                                                    | Checks whether a given method exists on the table.                                                                                                                        |
| public AOSAuthorization AOSAuthSetting()                                                                                                    | Retrieves an AOSAuthorization system enumeration value that specifies the type of operation that a user can perform on a table, depending on the permissions of the user. |
| public RecordCacheLevel cacheLookup()                                                                                                       | Returns the record cache level for the table.                                                                                                                             |
| public int cacheSize()                                                                                                                      | Returns the cache size for the table, in the number of records.                                                                                                           |
| public AnyType callObject(str methodName, Common Called, VarArg )                                                                           | Calls the specified object method for a table.                                                                                                                            |
| public AnyType callStatic(str methodName, VarArg )                                                                                          | Calls the specified static method for a table.                                                                                                                            |
| public IndexId clusterIndex(\[boolean asDefinedInAOT\])                                                                                     | Returns the ID of the clustered index for the table.                                                                                                                      |
| public ConfigurationKeyId configurationKeyId()                                                                                              | Returns the ID of the configuration key for the table.                                                                                                                    |
| public boolean dataPerPartition()                                                                                                           | Returns a value that indicates whether the data of the table is saved on a per-partition basis, and corresponds to the SaveDataPerPartition property of the table.        |
| public boolean dataPrCompany()                                                                                                              | Returns a value that indicates whether the data of the table is saved on a per-company basis, and corresponds to the SaveDataPerCompany property of the table.            |
| public int deleteActionCnt()                                                                                                                | Retrieves the number of delete actions for the table.                                                                                                                     |
| public str deleteActionRelation(int cnt)                                                                                                    |                                                                                                                                                                           |
| public TableId deleteActionTableId(int cnt)                                                                                                 | Returns the table ID of a table's delete action that is specified by an index.                                                                                            |
| public int deleteActionType(int cnt)                                                                                                        | Retrieves the type of a delete action for a table.                                                                                                                        |
| public str developerDocumentation()                                                                                                         |                                                                                                                                                                           |
| public str developerDocumentationLabelId()                                                                                                  |                                                                                                                                                                           |
| public boolean enabled()                                                                                                                    | Returns a value that indicates whether the table is enabled.                                                                                                              |
| public boolean enforceRelationRules()                                                                                                       |                                                                                                                                                                           |
| public EntityRelationshipType entityRelationshipType()                                                                                      |                                                                                                                                                                           |
| public List extendedBy(\[boolean allLevels\])                                                                                               |                                                                                                                                                                           |
| public TableId extends()                                                                                                                    | Returns the table ID of a base table.                                                                                                                                     |
| public int fieldCnt(\[TableScope tableScope\])                                                                                              | Returns the number of fields for a table.                                                                                                                                 |
| public FieldId fieldCnt2Id(int cnt, \[TableScope tableScope\])                                                                              | Returns the field ID of the field that is specified by an index.                                                                                                          |
| public str fieldGroup(int FieldGroupNumber, \[TableScope tableScope\])                                                                      | Returns the name of a field group that is specified by index.                                                                                                             |
| public int fieldGroupCnt(\[TableScope tableScope\])                                                                                         | Returns the number of field groups for the table.                                                                                                                         |
| public str fieldName(FieldId fieldId, \[DbBackend db\], \[int arrayindex\], \[FieldNameGenerationMode generationMode\], \[str tableAlias\]) | Returns the name of the field that is specified by field ID.                                                                                                              |
| public FieldId fieldName2Id(str name)                                                                                                       | Returns the field ID of a field that is specified by name.                                                                                                                |
| public FieldId fieldNext(FieldId fieldId, \[TableScope tableScope\])                                                                        | Returns the value of the next field ID during a field iteration of the table.                                                                                             |
| public DictField fieldObject(FieldId fieldId)                                                                                               | Creates an instance of the DictField class for the field that is specified by field ID.                                                                                   |
| public IndexId fieldOrigin2Id(Guid fieldOrigin, \[TableScope tableScope\])                                                                  |                                                                                                                                                                           |
| public str fieldSqlDefault(FieldId fieldId)                                                                                                 | Returns the SQL default value for the field that is specified by field ID.                                                                                                |
| public str formRef(\[boolean searchBaseTables\])                                                                                            | Returns the name of the default form for the table.                                                                                                                       |
| public container getCountryRegionCodes()                                                                                                    |                                                                                                                                                                           |
| public FieldId getCountryRegionContextField()                                                                                               |                                                                                                                                                                           |
| public FieldId getValidTimeStateValidFromFieldId()                                                                                          |                                                                                                                                                                           |
| public FieldId getValidTimeStateValidToFieldId()                                                                                            |                                                                                                                                                                           |
| public boolean hasRecidIdx()                                                                                                                | Returns a value that indicates whether a record ID index for the table is in effect.                                                                                      |
| public boolean hasSurrogateKey()                                                                                                            |                                                                                                                                                                           |
| public TableId id()                                                                                                                         | Returns the ID of the table.                                                                                                                                              |
| public int indexCnt()                                                                                                                       | Returns the number of indexes for the table.                                                                                                                              |
| public IndexId indexCnt2Id(int cnt)                                                                                                         |                                                                                                                                                                           |
| public str indexName(IndexId indexId, \[DbBackend db\])                                                                                     | Returns the name of an index that is specified by the indexId parameter.                                                                                                  |
| public IndexId indexName2Id(str name)                                                                                                       | Returns the ID of an index that is specified by name.                                                                                                                     |
| public IndexId indexNext(IndexId id)                                                                                                        | Returns the value of the next index ID during an index iteration of the table.                                                                                            |
| public DictIndex indexObject(IndexId indexId)                                                                                               | Creates an instance of the DictTable class for the index that is specified by ID.                                                                                         |
| public IndexId indexUnique()                                                                                                                | Returns the ID of the unique index for the table.                                                                                                                         |
| public FieldId instanceRelationType()                                                                                                       |                                                                                                                                                                           |
| public boolean isAbstract()                                                                                                                 | Indicates whether this table is abstract.                                                                                                                                 |
| public boolean isBaseData()                                                                                                                 | Indicates whether the table content is base data.                                                                                                                         |
| public boolean isDefaultData()                                                                                                              | Indicates whether the table contains default data.                                                                                                                        |
| public boolean isDerivedFrom(TableName baseTableName)                                                                                       | Indicates whether one table type derives from another.                                                                                                                    |
| public boolean isMap()                                                                                                                      | Indicates whether the table is a map.                                                                                                                                     |
| public boolean isSql()                                                                                                                      | Indicates whether the table is an SQL table.                                                                                                                              |
| public boolean isSystemTable()                                                                                                              | Indicates whether the table is a system table.                                                                                                                            |
| public boolean isTempDb()                                                                                                                   |                                                                                                                                                                           |
| public boolean isTmp()                                                                                                                      | Indicates whether the table is a temporary table.                                                                                                                         |
| public boolean isUnionAllView()                                                                                                             |                                                                                                                                                                           |
| public boolean isValidTimeStateTable()                                                                                                      |                                                                                                                                                                           |
| public boolean isView()                                                                                                                     | Indicates whether the table is a view.                                                                                                                                    |
| public str label()                                                                                                                          | Returns the label text for the table.                                                                                                                                     |
| public str labelDefined()                                                                                                                   | Returns the value of the label property for the table.                                                                                                                    |
| public str listPageRef(\[boolean searchBaseTables\])                                                                                        |                                                                                                                                                                           |
| public Common makeRecord()                                                                                                                  | Creates a blank record for the table.                                                                                                                                     |
| public AccessType maxAccessMode()                                                                                                           | Returns the value of the MaxAccessMode property for a table, as set in the AOT.                                                                                           |
| public str name(\[DbBackend db\], \[boolean pseudoname\])                                                                                   | Retrieves the name of the table.                                                                                                                                          |
| public str objectMethod(int methodNumber, \[TableScope tableScope\])                                                                        | Returns the name of an instance method that is specified by index.                                                                                                        |
| public int objectMethodCnt(\[TableScope tableScope\])                                                                                       | Returns the number of instance methods for the table.                                                                                                                     |
| public DictMethod objectMethodObject(int methodNumber, \[TableScope tableScope\])                                                           | Returns an instance of the MethodInfo class for an object method that is specified by index.                                                                              |
| public DictTableMap mapObject(int methodNumber)                                                                                             | Creates an instance of the \[T: DictTableMap\] class for a mapping that is specified by index.                                                                            |
| public int mapCnt()                                                                                                                         | Returns the count of available table mappings for the map that is specified by this DictTable instance.                                                                   |
| public boolean occEnabled()                                                                                                                 | Indicates whether the optimistic concurrency mode has been enabled for a table.                                                                                           |
| public IndexId primaryIndex(\[boolean asDefinedInAOT\])                                                                                     | Returns the ID of the primary index for the table.                                                                                                                        |
| public FieldId primaryKeyField()                                                                                                            | Returns the ID of the field that is used for the primary key of the table.                                                                                                |
| public str relation(int RelationNumber, \[TableScope tableScope\])                                                                          | Returns the name of a relation that is specified by index.                                                                                                                |
| public int relationCnt(\[TableScope tableScope\])                                                                                           | Returns the number of relations for the table.                                                                                                                            |
| public IndexId replacementKey()                                                                                                             |                                                                                                                                                                           |
| public str reportRef()                                                                                                                      | Returns the name of the default report for the table.                                                                                                                     |
| public AccessType rights(\[boolean ignoreContext\])                                                                                         | Returns the access rights of the current user that is specified for the table.                                                                                            |
| public SecurityKeyId securityKeyId()                                                                                                        | Returns the ID of the security key for the table.                                                                                                                         |
| public str singularLabel(\[boolean labelTranslation\])                                                                                      |                                                                                                                                                                           |
| public str staticMethod(int methodNumber)                                                                                                   | Returns the name of a static method that is specified by index.                                                                                                           |
| public int staticMethodCnt()                                                                                                                | Returns the number of static methods for the table.                                                                                                                       |
| public DictMethod staticMethodObject(int methodNumber)                                                                                      | Returns an instance of the MethodInfo class for a static method that is specified by index.                                                                               |
| public boolean supportInheritance()                                                                                                         |                                                                                                                                                                           |
| public TableGroup tableGroup()                                                                                                              | Returns the table group for a table.                                                                                                                                      |
| public TableType tableType()                                                                                                                | Indicates the type of the table.                                                                                                                                          |
| public FieldId titleField1(\[boolean includeBaseTables\], \[boolean extendedFieldId\])                                                      | Returns the ID of the field that represents the titleField1 property of the table.                                                                                        |
| public FieldId titleField2(\[boolean includeBaseTables\], \[boolean extendedFieldId\])                                                      | Returns the ID of the field that represents the titleField2 property of the table.                                                                                        |
| public boolean validRelationship()                                                                                                          |                                                                                                                                                                           |
| public boolean visible()                                                                                                                    | Determines whether the table is visible.                                                                                                                                  |
| ::public static DictTable construct(str tableName)                                                                                          |                                                                                                                                                                           |
| ::public static RecId getRelationTypeFromTableName(TableName tableName)                                                                     |                                                                                                                                                                           |
| ::public static TableName getTableNameFromRelationType(RecId relationType)                                                                  |                                                                                                                                                                           |
| ::public static Common createRecord(str tableName)                                                                                          |                                                                                                                                                                           |
| public void reloadSecurity()                                                                                                                | Reloads the feature key system for the table.                                                                                                                             |
| public void new(TableId tableId)                                                                                                            | Initializes a new instance of the Object class.                                                                                                                           |
| public void reindex()                                                                                                                       | Performs a reindex of the table.                                                                                                                                          |

### Method doesMethodExist

Checks whether a given method exists on the table.

    public boolean doesMethodExist(str name)

#### Parameters

name  

#### Return Value

true if the given method exists on the table; otherwise, false.

#### Remarks

This API is the preferred way to check whether a method exists on the table without checking whether the method compiled successfully.

### Method AOSAuthSetting

Retrieves an AOSAuthorization system enumeration value that specifies the type of operation that a user can perform on a table, depending on the permissions of the user.

    public AOSAuthorization AOSAuthSetting()

#### Return Value

An AOSAuthorization system enumeration value.

#### Remarks

The AOSAuthorization::None value indicates that an authorization check is not performed. Use table properties to set the AOSAuthorization property for a table. In the Microsoft Dynamics 365 for Operations Application Object Tree (AOT), right-click the table, and then click Properties to access the table properties.

#### Examples

This following example shows a call to the AOSAuthSetting method.

    static public void Main(Args _args) 
    { 
        DictTable dt; 
        AOSAuthorization a; 
        dt = new DictTable(tablenum(CustTable)); 
        a = dt.AOSAuthSetting(); 
    }

### Method cacheLookup

Returns the record cache level for the table.

    public RecordCacheLevel cacheLookup()

#### Return Value

A RecordCacheLevel value that indicates the record cache level for the table.

#### Examples

The following example shows the retrieval of the cache level for a table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print dt.cacheLookup(); 
    }

### Method cacheSize

Returns the cache size for the table, in the number of records.

    public int cacheSize()

#### Return Value

The cache size for the table.

#### Examples

The following example retrieves the cache size for a table.

    DictTable dt; 
    dt = new DictTable(tablenum(SysUserInfo)); 
    if (dt) 
    { 
         print strfmt("Cache size: %1", dt.cacheSize()); 
    }

### Method callObject

Calls the specified object method for a table.

    public AnyType callObject(str methodName, Common Called, VarArg )

#### Parameters

methodName  

<!-- -->

Called  

<!-- -->

  

#### Return Value

The results of the call to the methodName parameter.

#### Remarks

If an attacker can control input to the callObject method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

#### Examples

This example calls the SysUserLog.onlineTime static method in the SysUserLog table and then prints the value that is returned from the call.

    { 
        Dicttable         dictTable; 
        int               onlineTime; 
        Common            common; 
        str               resultOutput; 
        ExecutePermission perm; 
        perm = new ExecutePermission(); 
        dictTable= new DictTable(tablenum(SysUserLog)); 
        if (dictTable != null) 
        { 
            common = dictTable.makeRecord(); 
            // Grants permission to execute the 
            // DictTable.callObject method. DictTable.callObject runs 
            // under code access security. 
            perm.assert(); 
            onlineTime   = dictTable.callObject("onlineTime", common); 
            resultOutput = strfmt("User online time is %1", onlineTime); 
            print resultOutput; 
            pause; 
        } 
        // Close the code access permission scope. 
        CodeAccessPermission::revertAssert(); 
    }

### Method callStatic

Calls the specified static method for a table.

    public AnyType callStatic(str methodName, VarArg )

#### Parameters

methodName  

<!-- -->

  

#### Return Value

The results of the call to the methodName parameter.

#### Remarks

If an attacker can control input to this function, a security risk exists. Therefore, the callStatic method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

#### Examples

This example calls the SysUserInfo:find static method in the SysUserInfo table and then prints the value that is returned from the call to the callStatic method.

     { 
        Dicttable   dictTable; 
        SysUserInfo userInfo; 
        str         resultOutput; 
        ExecutePermission perm; 
        perm = new ExecutePermission(); 
        // Grants permission to execute the DictTable.callStatic method. 
        // DictTable.callStatic runs under code access security. 
        perm.assert(); 
        dictTable= new DictTable(tablenum(SysUserInfo)); 
        if (dictTable != null) 
        { 
            userInfo     = dictTable.callStatic("find"); 
            resultOutput = strfmt("Current user ID is %1", userInfo.Id); 
            print resultOutput; 
            pause; 
        } 
        // Close the code access permission scope. 
        CodeAccessPermission::revertAssert(); 
    }

### Method clusterIndex

Returns the ID of the clustered index for the table.

    public IndexId clusterIndex([boolean asDefinedInAOT])

#### Parameters

asDefinedInAOT  
A value that indicates whether the clustered index to retrieve is defined in the AOT. A value of true returns the clustered index as defined in the AOT. A value of false returns the clustered index as defined in the SQL table; optional.

#### Return Value

The ID of the clustered index for the table; 0 (zero) if there is no clustered index for the table.

#### Examples

The following example shows the retrieval of the clustered index for a table.

    DictTable dt; 
    DictIndex di; 
    int       i; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        i = dt.clusterIndex(); 
        if (0 != i) 
        { 
            di = new DictIndex(tablenum(CustTable), i); 
            print di.name(); 
        } 
    }

### Method configurationKeyId

Returns the ID of the configuration key for the table.

    public ConfigurationKeyId configurationKeyId()

#### Return Value

The ID of the configuration key for the table; 0 (zero) if there is no configuration key for the table.

#### Examples

The following example shows the retrieval of the configuration key ID for a table.

    DictTable dt; 
    DictConfigurationKey dck; 
    dt = new DictTable(tablenum(AddressCountryRegionBLWI)); 
    if (dt) 
    { 
        if (0 != dt.configurationKeyId()) 
        dck = new DictConfigurationKey(dt.configurationKeyId()); 
        if (dck) 
        { 
            print (strfmt("The table's configuration key is %1.", dck.name())); 
        } 
    }

### Method dataPerPartition

Returns a value that indicates whether the data of the table is saved on a per-partition basis, and corresponds to the SaveDataPerPartition property of the table.

    public boolean dataPerPartition()

#### Return Value

true if the data is saved on a per-partition basis; otherwise, false, and the data is saved globally for all partitions.

### Method dataPrCompany

Returns a value that indicates whether the data of the table is saved on a per-company basis, and corresponds to the SaveDataPerCompany property of the table.

    public boolean dataPrCompany()

#### Return Value

true if the data is saved on a per-company basis; otherwise, false, and the data is saved globally for all companies.

#### Examples

The following example shows the retrieval of the value that indicates whether the data is saved on a per-company basis.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print (strfmt("The table is saved on a %1 basis.", dt.dataPrCompany() ? "per company" : "global")); 
    }

### Method deleteActionCnt

Retrieves the number of delete actions for the table.

    public int deleteActionCnt()

#### Return Value

The number of delete actions for the table.

#### Examples

The following example shows the retrieval of the number of delete actions for the table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print (strfmt("The table has %1 delete actions.", dt.deleteActionCnt())); 
    }

### Method deleteActionRelation

    public str deleteActionRelation(int cnt)

#### Parameters

cnt  

#### Return Value

### Method deleteActionTableId

Returns the table ID of a table's delete action that is specified by an index.

    public TableId deleteActionTableId(int cnt)

#### Parameters

cnt  
A one-based index to the list of the delete actions for the table. The list is in AOT order.

#### Return Value

The table ID of the table's delete action that is specified by cnt; 0 (zero) if the cnt value does not represent a valid delete action index.

#### Examples

The following example shows the use of the deleteActionTableId method to retrieve the names of tables that have delete actions for the CustTable table.

    DictTable dt, dt2; 
    int       i; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        for (i=1; i <= dt.deleteActionCnt(); i++) 
        { 
            dt2 = new DictTable(dt.deleteActionTableId(i)); 
            if (dt2) 
            { 
                print dt2.name(); 
            } 
        } 
    }

### Method deleteActionType

Retrieves the type of a delete action for a table.

    public int deleteActionType(int cnt)

#### Parameters

cnt  
The one-based index to the list of the delete actions for the table. The list is in AOT order.

#### Return Value

An integer that represents the type of the delete action of the table that is specified by the cnt parameter. It can be one of the values in the following table.

|     |                      |
|-----|----------------------|
| 0   | None                 |
| 1   | Cascade              |
| 2   | Restricted           |
| 3   | Cascade + Restricted |

#### Examples

The following example shows the retrieval of the type of delete actions for a table.

    DictTable dt, dt2; 
    str       strDelActType; 
    int       i, nDelActType; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        for (i=1; i <= dt.deleteActionCnt(); i++) 
        { 
            dt2 = new DictTable(dt.deleteActionTableId(i)); 
            if (dt2) 
            { 
                nDelActType = dt.deleteActionType(i); 
                switch (nDelActType) 
                { 
                   case 0: 
                    strDelActType = "None"; 
                    break; 
                   case 1: 
                    strDelActType = "Cascade"; 
                    break; 
                   case 2: 
                    strDelActType = "Restricted"; 
                    break; 
                   case 3: 
                    strDelActType = "Cascade + Restricted"; 
                    break; 
                } 
                print strfmt("Delete action table: %1 Type: %2", 
                             dt2.name(), 
                             strDelActType); 
            } 
        } 
    }

### Method developerDocumentation

    public str developerDocumentation()

#### Return Value

### Method developerDocumentationLabelId

    public str developerDocumentationLabelId()

#### Return Value

### Method enabled

Returns a value that indicates whether the table is enabled.

    public boolean enabled()

#### Return Value

true if the table is enabled; otherwise, false.

#### Examples

The following example shows the retrieval of the value that indicates whether the table is enabled.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print (strfmt("The table is %1.", dt.enabled() ? "enabled" : "not enabled")); 
    }

### Method enforceRelationRules

    public boolean enforceRelationRules()

#### Return Value

### Method entityRelationshipType

    public EntityRelationshipType entityRelationshipType()

#### Return Value

### Method extendedBy

    public List extendedBy([boolean allLevels])

#### Parameters

allLevels  

#### Return Value

### Method extends

Returns the table ID of a base table.

    public TableId extends()

#### Return Value

The table ID of the base table.

### Method fieldCnt

Returns the number of fields for a table.

    public int fieldCnt([TableScope tableScope])

#### Parameters

tableScope  

#### Return Value

The number of fields for the table.

#### Examples

The following example shows the retrieval of the number of fields for a table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print (strfmt("The table has %1 fields.", dt.fieldCnt())); 
    }

### Method fieldCnt2Id

Returns the field ID of the field that is specified by an index.

    public FieldId fieldCnt2Id(int cnt, [TableScope tableScope])

#### Parameters

cnt  

<!-- -->

tableScope  

#### Return Value

The field ID of the field that is specified by an index.

#### Examples

The following example shows the retrieval of the fields of a table by index.

    DictTable dt; 
    int       i, fId, tId; 
    DictField df; 
    str       strFieldName; 
    tId = tablenum(CustTable); 
    dt = new DictTable(tId); 
    if (dt) 
    { 
        for (i=1; i <= dt.fieldCnt(); i++) 
        { 
            fId = dt.fieldCnt2Id(i); 
            df = new DictField(tId, fId); 
            strFieldName = (df ? df.name() : ""); 
            print(strfmt("%1) %2 %3", i, fId, strFieldName)); 
        } 
    }

### Method fieldGroup

Returns the name of a field group that is specified by index.

    public str fieldGroup(int FieldGroupNumber, [TableScope tableScope])

#### Parameters

FieldGroupNumber  

<!-- -->

tableScope  

#### Return Value

The name of the field group that is specified by the FieldGroupNumber parameter.

#### Examples

The following example shows the retrieval of the names of the field groups for a table.

    DictTable dt; 
    int       i; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        for (i =1; i <= dt.fieldGroupCnt(); i++) 
        { 
            print (dt.fieldGroup(i)); 
        } 
    }

### Method fieldGroupCnt

Returns the number of field groups for the table.

    public int fieldGroupCnt([TableScope tableScope])

#### Parameters

tableScope  

#### Return Value

The number of field groups for the table.

#### Examples

The following example shows the retrieval of the number of field groups for a table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print (strfmt("The table has %1 field groups.", dt.fieldGroupCnt())); 
    }

### Method fieldName

Returns the name of the field that is specified by field ID.

    public str fieldName(FieldId fieldId, [DbBackend db], [int arrayindex], [FieldNameGenerationMode generationMode], [str tableAlias])

#### Parameters

fieldId  
The alias name for the table; optional.

<!-- -->

db  
The alias name for the table; optional.

<!-- -->

arrayindex  
The alias name for the table; optional.

<!-- -->

generationMode  
The alias name for the table; optional.

<!-- -->

tableAlias  
The alias name for the table; optional.

#### Return Value

The name of the field that is specified by its field ID.

#### Remarks

If db is not specified, the DbBackend::Native object is used.

#### Examples

The following example shows the retrieval of field names of a table as specified by the field IDs.

    DictTable dt; 
    int       i, tId, fId; 
    tId = tablenum(CustTable); 
    dt = new DictTable(tId); 
    if (dt) 
    { 
        for (i=1; i <= dt.fieldCnt(); i++) 
        { 
            fId = dt.fieldCnt2Id(i); 
            print(strfmt("%1) %2 %3", i, fId, dt.fieldName(fId))); 
        } 
    }

### Method fieldName2Id

Returns the field ID of a field that is specified by name.

    public FieldId fieldName2Id(str name)

#### Parameters

name  
The name of the field for which the field ID is being retrieved.

#### Return Value

The field ID of the field that is specified by the name parameter; 0 (zero) if name does not represent a valid field name for the table.

#### Examples

The following example shows the retrieval of a field ID by its field name.

    DictTable dt; 
    fieldId   fId; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        fId = dt.fieldName2Id("Pager"); 
        // Use the field ID as needed. 
        // This example merely prints out the field ID. 
        print (strfmt("fId: %1", fId)); 
    }

### Method fieldNext

Returns the value of the next field ID during a field iteration of the table.

    public FieldId fieldNext(FieldId fieldId, [TableScope tableScope])

#### Parameters

fieldId  

<!-- -->

tableScope  

#### Return Value

The ID of the next field in the field iteration for the table; 0 (zero) if there are no more fields to iterate.

#### Remarks

The value of the fieldId parameter should evaluate to 0 (zero) to start the field iteration, and the return value should be used for subsequent calls to the iteration.

#### Examples

The following example iterates through the fields of a table.

    DictTable   dt; 
    DictField   df; 
    int         counter; 
    counter = 0; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        counter = dt.fieldNext(counter); 
        while (counter) 
        { 
            df = dt.fieldObject(counter); 
            if (df) 
            { 
                print strfmt("ID: %1 Name: %2", 
                             df.id(), 
                             df.name() ); 
            } 
            counter = dt.fieldNext(counter); 
        } 
    }

### Method fieldObject

Creates an instance of the DictField class for the field that is specified by field ID.

    public DictField fieldObject(FieldId fieldId)

#### Parameters

fieldId  
The ID of the field to create.

#### Return Value

A DictField object for the field that is specified by the fieldId parameter; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the object could not be created.

#### Examples

The following example shows how to create a DictField object for the fields in a table.

    DictTable dt; 
    DictField df; 
    int       i; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        for (i=1; i <= dt.fieldCnt(); i++) 
        { 
          df = dt.fieldObject(dt.fieldCnt2Id(i)); 
          if (df) 
          { 
              print df.name(); 
          } 
        } 
    }

### Method fieldOrigin2Id

    public IndexId fieldOrigin2Id(Guid fieldOrigin, [TableScope tableScope])

#### Parameters

fieldOrigin  

<!-- -->

tableScope  

#### Return Value

### Method fieldSqlDefault

Returns the SQL default value for the field that is specified by field ID.

    public str fieldSqlDefault(FieldId fieldId)

#### Parameters

fieldId  
The ID of the field for which the SQL default data is being retrieved.

#### Return Value

A string that represents the SQL default value for the field that is specified by the fieldId parameter; an empty string if the field has no SQL default value or the table is not an SQL table.

### Method formRef

Returns the name of the default form for the table.

    public str formRef([boolean searchBaseTables])

#### Parameters

searchBaseTables  

#### Return Value

The name of the default form for the table.

#### Remarks

If the AOT shows no value for the FormRef property of a table, the name of the default form for the table is considered to be the same as the name of the table. In this case, this method does not return an empty string.

#### Examples

The following example shows the retrieval of the default form for a table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print strfmt("Default form: %1", dt.formRef()); 
    }

### Method getCountryRegionCodes

    public container getCountryRegionCodes()

#### Return Value

### Method getCountryRegionContextField

    public FieldId getCountryRegionContextField()

#### Return Value

### Method getValidTimeStateValidFromFieldId

    public FieldId getValidTimeStateValidFromFieldId()

#### Return Value

### Method getValidTimeStateValidToFieldId

    public FieldId getValidTimeStateValidToFieldId()

#### Return Value

### Method hasRecidIdx

Returns a value that indicates whether a record ID index for the table is in effect.

    public boolean hasRecidIdx()

#### Return Value

true if a record ID index is in effect for the table; otherwise, false.

#### Remarks

The return value corresponds to whether the CreateRecIdIndex property of the table is set to Yes.

#### Examples

The following example shows the retrieval of a value that indicates whether the record ID index of the table is in effect.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print (strfmt("A record ID index for the table %1 in effect.", 
               dt.hasRecidIdx() ? "is" : "is not") ); 
    }

### Method hasSurrogateKey

    public boolean hasSurrogateKey()

#### Return Value

### Method id

Returns the ID of the table.

    public TableId id()

#### Return Value

The ID of the table.

#### Examples

The following example shows the retrieval of the ID of a table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print (strfmt("The table ID is: %1", dt.id())); 
    }

### Method indexCnt

Returns the number of indexes for the table.

    public int indexCnt()

#### Return Value

The number of indexes for the table.

#### Examples

The following example shows the retrieval of the number of indexes for a table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print (strfmt("The table has %1 indexes.", dt.indexCnt())); 
    }

### Method indexCnt2Id

    public IndexId indexCnt2Id(int cnt)

#### Parameters

cnt  

#### Return Value

### Method indexName

Returns the name of an index that is specified by the indexId parameter.

    public str indexName(IndexId indexId, [DbBackend db])

#### Parameters

indexId  
A DbBackend value that specifies the type of database back end; optional.

<!-- -->

db  
A DbBackend value that specifies the type of database back end; optional.

#### Return Value

The name of the index that is specified by the indexId parameter.

#### Examples

The following example shows the retrieval of the names of the indexes for a table.

    DictTable dt; 
    int       i; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        for (i=1; i <= dt.indexCnt(); i++) 
        { 
            print (dt.indexName(i)); 
        } 
    }

### Method indexName2Id

Returns the ID of an index that is specified by name.

    public IndexId indexName2Id(str name)

#### Parameters

name  
The name of the index.

#### Return Value

The ID of the index that is specified by the name parameter; 0 (zero) if there is no index that has a name that equals the name value.

#### Examples

The following example shows the retrieval of the ID of an index that is specified by name.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print(strfmt("Index ID: %1", dt.indexName2Id("TypeIdx"))); 
    }

### Method indexNext

Returns the value of the next index ID during an index iteration of the table.

    public IndexId indexNext(IndexId id)

#### Parameters

id  
The ID of the index for which the next index ID is being queried.

#### Return Value

The ID of the next index in the index iteration for the table; 0 (zero) if there are no more indexes to iterate.

#### Remarks

The value of the id parameter should evaluate to 0 (zero) to start the index iteration, and the return value should be used for subsequent calls to the iteration.

#### Examples

The following example iterates through the indexes of a table.

    DictTable   dt; 
    DictIndex   di; 
    int         counter; 
    counter = 0; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        counter = dt.indexNext(counter); 
        while (counter) 
        { 
            di = dt.indexObject(counter); 
            if (di) 
            { 
                print strfmt("ID: %1 Name: %2", 
                             di.id(), 
                             di.name() ); 
            } 
            counter = dt.indexNext(counter); 
        } 
    }

### Method indexObject

Creates an instance of the DictTable class for the index that is specified by ID.

    public DictIndex indexObject(IndexId indexId)

#### Parameters

indexId  
The ID of the index to create.

#### Return Value

A DictIndex object for the index that is specified by the indexId parameter; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the object could not be created.

#### Examples

The following example shows how to create a DictIndex object for the unique index of a table.

    DictTable dt; 
    DictIndex di; 
    dt = new DictTable(tablenum(SysUserInfo)); 
    if (dt) 
    { 
         di = dt.indexObject(dt.indexUnique()); 
         if (di) 
         { 
            print di.name(); 
         } 
    }

### Method indexUnique

Returns the ID of the unique index for the table.

    public IndexId indexUnique()

#### Return Value

The ID of the unique index for the table.

#### Remarks

When there is more than one unique index on the table, the return value is one of the following:

-   The index that has the RecID column.
-   If no index has a record ID, the index that has the shortest size, based on the total size of columns.
-   If multiple indexes match with regard to the shortest size, the index that was added first.

#### Examples

The following example shows the retrieval of the unique index for a table.

    DictTable dt; 
    DictIndex di; 
    dt = new DictTable(tablenum(SysUserInfo)); 
    if (dt) 
    { 
         di = dt.indexObject(dt.indexUnique()); 
         if (di) 
         { 
            print di.name(); 
         } 
    }

### Method instanceRelationType

    public FieldId instanceRelationType()

#### Return Value

### Method isAbstract

Indicates whether this table is abstract.

    public boolean isAbstract()

#### Return Value

true if this table is abstract; otherwise, false.

### Method isBaseData

Indicates whether the table content is base data.

    public boolean isBaseData()

#### Return Value

true if the TableContents property in the AOT indicates that the table content is base data; otherwise, false.

#### Examples

The following example shows the retrieval of a value that indicates whether the table content is base data.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print strfmt("isBaseData: %1", dt.isBaseData()); 
        print strfmt("isDefaultData: %1", dt.isDefaultData()); 
    }

### Method isDefaultData

Indicates whether the table contains default data.

    public boolean isDefaultData()

#### Return Value

true if the table contains default data; otherwise, false.

#### Examples

The following example shows the retrieval of a value that indicates whether the table contains default data.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print strfmt("isDefaultData: %1", dt.isDefaultData()); 
    }

### Method isDerivedFrom

Indicates whether one table type derives from another.

    public boolean isDerivedFrom(TableName baseTableName)

#### Parameters

baseTableName  

#### Return Value

true if this table is derived from the table that is specified by the baseTableName parameter.

### Method isMap

Indicates whether the table is a map.

    public boolean isMap()

#### Return Value

true if the table is a map; otherwise, false.

#### Examples

The following example shows the retrieval of a value that indicates whether the table is a map.

    DictTable dt; 
    dt = new DictTable(tablenum(AddressMap)); 
    if (dt) 
    { 
        print(strfmt("Map: %1", dt.isMap())); 
    }

### Method isSql

Indicates whether the table is an SQL table.

    public boolean isSql()

#### Return Value

true if the table is an SQL table; otherwise, false.

#### Examples

The following example shows the retrieval of a value that indicates whether the table is an SQL table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print(strfmt("SQL table: %1", dt.isSql())); 
    }

### Method isSystemTable

Indicates whether the table is a system table.

    public boolean isSystemTable()

#### Return Value

true if the table is a system table; otherwise, false.

#### Examples

The following example shows the retrieval of a value that indicates whether the table is a system table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print(strfmt("System table: %1", dt.isSystemTable())); 
    }

### Method isTempDb

    public boolean isTempDb()

#### Return Value

### Method isTmp

Indicates whether the table is a temporary table.

    public boolean isTmp()

#### Return Value

true if the table is a temporary table; otherwise, false.

#### Examples

The following example shows the retrieval of a value that indicates whether the table is a temporary table.

    DictTable dt; 
    dt = new DictTable(tablenum(TmpWMSOrder)); 
    if (dt) 
    { 
        print(strfmt("Temporary table: %1", dt.isTmp())); 
    }

### Method isUnionAllView

    public boolean isUnionAllView()

#### Return Value

### Method isValidTimeStateTable

    public boolean isValidTimeStateTable()

#### Return Value

### Method isView

Indicates whether the table is a view.

    public boolean isView()

#### Return Value

true if the table is a view; otherwise, false.

#### Examples

The following example shows the retrieval of a value that indicates whether the table is a view.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print(strfmt("View: %1", dt.isView())); 
    }

### Method label

Returns the label text for the table.

    public str label()

#### Return Value

The label text for the table; an empty string if there is no label text for the table.

#### Examples

The following example shows the retrieval of the label text for a table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
         print(strfmt("Label: %1", dt.label())); 
    }

### Method labelDefined

Returns the value of the label property for the table.

    public str labelDefined()

#### Return Value

The value of the label property for the table; an empty string if there is no label text for the table.

### Method listPageRef

    public str listPageRef([boolean searchBaseTables])

#### Parameters

searchBaseTables  

#### Return Value

### Method makeRecord

Creates a blank record for the table.

    public Common makeRecord()

#### Return Value

A Common value if the record was successfully created; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the record could not be created.

#### Remarks

The Common value that is returned can be used in a call to the DictTable.callObject Method method.

### Method maxAccessMode

Returns the value of the MaxAccessMode property for a table, as set in the AOT.

    public AccessType maxAccessMode()

#### Return Value

A AccessType value that represents the maximum access mode for the table.

#### Examples

The following example shows the retrieval of the maximum access mode for a table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print strfmt("Maximum Access Mode: %1",dt.maxAccessMode()); 
    }

### Method name

Retrieves the name of the table.

    public str name([DbBackend db], [boolean pseudoname])

#### Parameters

db  
A Boolean value that indicates whether a pseudo name is returned; optional.

<!-- -->

pseudoname  
A Boolean value that indicates whether a pseudo name is returned; optional.

#### Return Value

The name of the table.

#### Remarks

If the table name is longer than 30 characters, the native name and SQL name of the table do not match.

#### Examples

The following example shows the retrieval of the name of a table.

    DictTable dt; 
    dt = new DictTable(1);  // 1 == tablenum(CustTable) 
    if (dt) 
    { 
        print(strfmt("The table name is %1.", dt.name())); 
    }

### Method objectMethod

Returns the name of an instance method that is specified by index.

    public str objectMethod(int methodNumber, [TableScope tableScope])

#### Parameters

methodNumber  

<!-- -->

tableScope  

#### Return Value

The name of the instance method that is specified by the methodNumber parameter; an empty string if the methodNumber value is not a valid instance method index.

#### Examples

The following example shows the retrieval of the name of each instance method in a table.

    DictTable dt; 
    int       i; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        for (i=1; i <= dt.objectMethodCnt() ; i++) 
        { 
            print dt.objectMethod(i); 
        } 
    }

### Method objectMethodCnt

Returns the number of instance methods for the table.

    public int objectMethodCnt([TableScope tableScope])

#### Parameters

tableScope  

#### Return Value

The number of instance methods for the table.

#### Examples

The following example shows the retrieval of the number of instance methods for a table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print (strfmt("The table has %1 instance methods.", dt.objectMethodCnt())); 
    }

### Method objectMethodObject

Returns an instance of the MethodInfo class for an object method that is specified by index.

    public DictMethod objectMethodObject(int methodNumber, [TableScope tableScope])

#### Parameters

methodNumber  

<!-- -->

tableScope  

#### Return Value

An instance of the MethodInfo class for the object method that is specified by the methodNumber parameter; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the instance could not be created.

#### Examples

The following example shows the retrieval of the object methods for a table.

    DictTable dt; 
    int       i; 
    MethodInfo mi; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        for (i=1; i <= dt.objectMethodCnt(); i++) 
        { 
            mi = dt.objectMethodObject(i); 
            if (mi) 
            { 
                print mi.name(); 
            } 
        } 
    }

### Method mapObject

Creates an instance of the \[T: DictTableMap\] class for a mapping that is specified by index.

    public DictTableMap mapObject(int methodNumber)

#### Parameters

methodNumber  

#### Return Value

A DictTableMap object for the field that is specified by the \_cnt parameter; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the object could not be created.

### Method mapCnt

Returns the count of available table mappings for the map that is specified by this DictTable instance.

    public int mapCnt()

#### Return Value

The count.

### Method occEnabled

Indicates whether the optimistic concurrency mode has been enabled for a table.

    public boolean occEnabled()

#### Return Value

true if the optimistic concurrency mode is enabled; otherwise, false.

#### Remarks

When this mode is enabled, data is not locked from future modification when it is fetched from the database. Data is locked only when the actual update is performed.

#### Examples

The following example shows a call to the occEnabled method.

    static public void Main(Args _args) 
    { 
        DictTable dt; 
        boolean enabled; 
        dt = new DictTable(tablenum(CustTable)); 
        enabled = dt.occEnabled(); 
    }

### Method primaryIndex

Returns the ID of the primary index for the table.

    public IndexId primaryIndex([boolean asDefinedInAOT])

#### Parameters

asDefinedInAOT  
A Boolean value that indicates whether the primary index to retrieve is defined in the AOT. A value of true returns the primary index as defined in the AOT. A value of false returns the primary index as defined in the SQL table; optional.

#### Return Value

The ID of the primary index for the table; 0 (zero) if there is no primary index for the table.

#### Examples

The following example shows the retrieval of the primary index for a table.

    DictTable dt; 
    DictIndex di; 
    int       i; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        i = dt.primaryIndex(); 
        if (0 != i) 
        { 
            di = new DictIndex(tablenum(CustTable), i); 
            print di.name(); 
        } 
    }

### Method primaryKeyField

Returns the ID of the field that is used for the primary key of the table.

    public FieldId primaryKeyField()

#### Return Value

The ID of the field that is used for the primary key of the table; 0 (zero) if no single field serves as the primary key of the table.

#### Examples

The following example shows the retrieval of the field ID of the primary key for the table.

    DictTable dt; 
    DictField df; 
    tableId   tID; 
    fieldId   fID; 
    tID = tablenum(CustTable); 
    dt = new DictTable(tID); 
    if (dt) 
    { 
       fID = dt.primaryKeyField(); 
       if (0 != fID) 
       { 
           df = new DictField(tID, fID); 
           if (df) 
           { 
                print strfmt("Primary key field name: %1", df.name()); 
           } 
       } 
    }

### Method relation

Returns the name of a relation that is specified by index.

    public str relation(int RelationNumber, [TableScope tableScope])

#### Parameters

RelationNumber  

<!-- -->

tableScope  

#### Return Value

The name of the relation that is specified by the RelationNumber parameter; an empty string if the RelationNumber value is not a valid relation index.

#### Examples

The following example shows the retrieval of the name for each relation in a table.

    DictTable dt; 
    int       i; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        for (i=1; i <= dt.relationCnt() ; i++) 
        { 
            print dt.relation(i); 
        } 
    }

### Method relationCnt

Returns the number of relations for the table.

    public int relationCnt([TableScope tableScope])

#### Parameters

tableScope  

#### Return Value

The number of relations for the table.

#### Examples

The following example shows the retrieval of the number of relations for a table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print (strfmt("The table has %1 relations.", dt.relationCnt())); 
    }

### Method replacementKey

    public IndexId replacementKey()

#### Return Value

### Method reportRef

Returns the name of the default report for the table.

    public str reportRef()

#### Return Value

The name of the default report for the table; an empty string if there is no default report for the table.

#### Examples

The following shows the retrieval of the name of the default report for a table.

    DictTable dt; 
    str       strReport; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        strReport = dt.reportRef(); 
        print strfmt("Default report: %1", strReport != "" ? strReport : "None specified"); 
    }

### Method rights

Returns the access rights of the current user that is specified for the table.

    public AccessType rights([boolean ignoreContext])

#### Parameters

ignoreContext  

#### Return Value

The access rights of the current user that is specified for the table. The return value can be one of the values in the AccessType system enumeration.

### Method securityKeyId

Returns the ID of the security key for the table.

    public SecurityKeyId securityKeyId()

#### Return Value

The ID of the security key for the table; 0 (zero) if there is no security key for the table.

#### Examples

The following example shows the retrieval of the security key ID for a table.

    DictTable dt; 
    DictSecurityKey dsk; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        if (0 != dt.securityKeyId()) 
        dsk = new DictSecurityKey(dt.securityKeyId()); 
        if (dsk) 
        { 
            print (strfmt("The table's security key is %1.", dsk.name())); 
        } 
    }

### Method singularLabel

    public str singularLabel([boolean labelTranslation])

#### Parameters

labelTranslation  

#### Return Value

### Method staticMethod

Returns the name of a static method that is specified by index.

    public str staticMethod(int methodNumber)

#### Parameters

methodNumber  
The one-based index to the list of static methods for the table, in AOT order.

#### Return Value

The name of the static method that is specified by the methodNumber parameter; an empty string if the methodNumber value is not a valid static method index.

#### Examples

The following example shows the retrieval of the name of each static method in a table.

    DictTable dt; 
    int       i; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        for (i=1; i <= dt.staticMethodCnt() ; i++) 
        { 
            print dt.staticMethod(i); 
        } 
    }

### Method staticMethodCnt

Returns the number of static methods for the table.

    public int staticMethodCnt()

#### Return Value

The number of static methods for the table.

#### Examples

The following example shows the retrieval of the number of static methods for a table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        print (strfmt("The table has %1 static methods.", dt. staticMethodCnt())); 
    }

### Method staticMethodObject

Returns an instance of the MethodInfo class for a static method that is specified by index.

    public DictMethod staticMethodObject(int methodNumber)

#### Parameters

methodNumber  
The one-based index to the static methods for the table, in AOT order.

#### Return Value

An instance of the MethodInfo class for the static method that is specified by the methodNumber parameter; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the instance could not be created.

#### Examples

The following example shows the retrieval of the static methods for a table.

    DictTable dt; 
    int       i; 
    MethodInfo mi; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        for (i=1; i <= dt.staticMethodCnt(); i++) 
        { 
            mi = dt.staticMethodObject(i); 
            if (mi) 
            { 
                print mi.name(); 
            } 
        } 
    }

### Method supportInheritance

    public boolean supportInheritance()

#### Return Value

### Method tableGroup

Returns the table group for a table.

    public TableGroup tableGroup()

#### Return Value

A TableGroup value that represents the table group of the table.

#### Remarks

The return value corresponds to the TableGroup property of the table in the AOT.

#### Examples

The following example shows the retrieval of the table group of the table.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
       print strfmt("Table Group: %1", dt.tableGroup()); 
    }

### Method tableType

Indicates the type of the table.

    public TableType tableType()

#### Return Value

The error state, if there is any error state.

### Method titleField1

Returns the ID of the field that represents the titleField1 property of the table.

    public FieldId titleField1([boolean includeBaseTables], [boolean extendedFieldId])

#### Parameters

includeBaseTables  

<!-- -->

extendedFieldId  

#### Return Value

The ID of the field that represents the titleField1 property of the table.

#### Remarks

According to best practice guidelines, the titleField1 property represents the key field for the records in the table.

#### Examples

The following example shows the retrieval of the ID of the field that is used for the titleField1 property of the table.

    DictTable dt; 
    DictField df; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        df = new DictField(tablenum(CustTable),dt.titleField1()); 
        if (df) 
        { 
            print df.name(); 
        } 
    } 
    pause;

### Method titleField2

Returns the ID of the field that represents the titleField2 property of the table.

    public FieldId titleField2([boolean includeBaseTables], [boolean extendedFieldId])

#### Parameters

includeBaseTables  

<!-- -->

extendedFieldId  

#### Return Value

The ID of the field that represents the titleField2 property of the table.

#### Remarks

According to best practice guidelines, the titleField2 property represents the description of the records of the table.

#### Examples

The following example shows the retrieval of the ID of the field that is used for the titleField2 property of the table.

    DictTable dt; 
    DictField df; 
    dt = new DictTable(tablenum(CustTable)); 
    if (dt) 
    { 
        df = new DictField(tablenum(CustTable),dt.titleField2()); 
        if (df) 
        { 
            print df.name(); 
        } 
    }

### Method validRelationship

    public boolean validRelationship()

#### Return Value

### Method visible

Determines whether the table is visible.

    public boolean visible()

#### Return Value

true if the table is is visible; otherwise, false.

### Method construct

    public static DictTable construct(str tableName)

#### Parameters

tableName  

#### Return Value

### Method getRelationTypeFromTableName

    public static RecId getRelationTypeFromTableName(TableName tableName)

#### Parameters

tableName  

#### Return Value

### Method getTableNameFromRelationType

    public static TableName getTableNameFromRelationType(RecId relationType)

#### Parameters

relationType  

#### Return Value

### Method createRecord

    public static Common createRecord(str tableName)

#### Parameters

tableName  

#### Return Value

### Method reloadSecurity

Reloads the feature key system for the table.

    public void reloadSecurity()

#### Examples

The following example reloads the feature key system for a table.

    dt.reloadSecurity()

### Method new

Initializes a new instance of the Object class.

    public void new(TableId tableId)

#### Parameters

tableId  
The ID of the table that is used to create the instance of the DictTable class.

#### Examples

The following example shows how to create an instance of the DictTable class.

    DictTable dt; 
    dt = new DictTable(tablenum(CustTable)); 
    if (!dt) 
    { 
        // Take error action. 
    }

### Method reindex

Performs a reindex of the table.

    public void reindex()

#### Remarks

Do not use this method to reindex SQL tables; instead, use the SqlDataDictionary::tableReindex method. Additionally, the DictTable::reindex method is not supported when it is run on the client.

## Class DictTableMap
    class DictTableMap extends Object

The DictTableMap class provides information about a table mapping.

### Remarks

### Examples

### Methods

| Method                                 | Description                                                    |
|----------------------------------------|----------------------------------------------------------------|
| public int table()                     | Retrieves the table that the mapping references.               |
| public int fieldCnt()                  | Retrieves the count of fields in the table mapping.            |
| public int fieldCnt2FieldTo(int cnt)   | Retrieves the table field that is referenced by the map field. |
| public int fieldCnt2FieldFrom(int cnt) | Retrieves the map field that is referencing a table field.     |

### Method table

Retrieves the table that the mapping references.

    public int table()

#### Return Value

The table ID.

#### Remarks

Use this method to get to the table mappings, instead of traversing to the tree node.

### Method fieldCnt

Retrieves the count of fields in the table mapping.

    public int fieldCnt()

#### Return Value

The count.

#### Remarks

Use this method to get to the table mappings, instead of traversing to the tree node.

### Method fieldCnt2FieldTo

Retrieves the table field that is referenced by the map field.

    public int fieldCnt2FieldTo(int cnt)

#### Parameters

cnt  

#### Return Value

The table field ID.

#### Remarks

Use this method to get to the table mappings, instead of traversing to the tree node.

### Method fieldCnt2FieldFrom

Retrieves the map field that is referencing a table field.

    public int fieldCnt2FieldFrom(int cnt)

#### Parameters

cnt  

#### Return Value

The map field ID.

#### Remarks

Use this method to get to the table mappings, instead of traversing to the tree node.

## Class DictType
    class DictType extends Object

The DictType class manages extended data types.

### Remarks

The SysDictType class extends DictType.

### Examples

### Methods

| Method                                                                | Description                                                                                                                                                              |
|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public Alignment alignment()                                          | Retrieves the alignment for the extended data type.                                                                                                                      |
| public int arraySize()                                                | Provides the array size for an extended data type.                                                                                                                       |
| public Types baseType()                                               | Provides the data type on which an extended data type is based, by using the Types enumeration.                                                                          |
| public ConfigurationKeyId configurationKeyId()                        | Returns the ID of the configuration key for the extended data type.                                                                                                      |
| public int displayHeight(\[boolean useDefaults\])                     | Retrieves the display height for the type.                                                                                                                               |
| public int displayLength(\[boolean useDefaults\])                     |                                                                                                                                                                          |
| public EnumId enumId()                                                | Provides the ID for the enumeration type on which an extended data type is based.                                                                                        |
| public ExtendedTypeId extend()                                        | Provides the ID for the extended data type that an extended data type extends.                                                                                           |
| public List extendedBy(\[boolean allLevels\])                         | Retrieves a list of type IDs for extended data types (EDTs) that are extended by the current EDT.                                                                        |
| public str formHelp()                                                 |                                                                                                                                                                          |
| public str getControlClass()                                          |                                                                                                                                                                          |
| public container getCountryRegionCodes()                              | Retrieves a container that holds the country/region codes that are defined.                                                                                              |
| public DictRelation getLookupRelation(\[int arrayIndex\])             |                                                                                                                                                                          |
| public AnyType getValue(\[int arrayIndex\])                           |                                                                                                                                                                          |
| public str help(\[int arrayIndex\], \[boolean useInterfaceLanguage\]) | Provides the Help text that is displayed for an extended data type or a specified array element, or for the extended data type that an extended data type extends.       |
| public str helpDefined(\[int arrayIndex\])                            | Returns the value of the help property for the extended data type.                                                                                                       |
| public ExtendedTypeId id()                                            | Provides the ID for an extended data type.                                                                                                                               |
| public boolean isExtendedFrom(str baseEDTName)                        | Determines whether the extended data type extends from the base extended data type that is provided.                                                                     |
| public int isRadioStyle()                                             | Indicates whether the style of an extended data type that is based on an Enum data type is a radio button or a combo box.                                                |
| public str label(\[int arrayIndex\])                                  | Provides the label that is displayed for an extended data type or a specified array element, or the label for the extended data type that an extended data type extends. |
| public str labelDefined(\[int arrayIndex\])                           | Returns the value of the label property for the extended data type.                                                                                                      |
| public str lookupTable(\[boolean useInheritedMetaData\])              |                                                                                                                                                                          |
| public str name()                                                     | Provides the name of an extended data type.                                                                                                                              |
| public DictRelation relationObject(\[int arrayIndex\])                | Provides information about relations that are defined for an extended data type or a specified array element by returning a DictRelation object.                         |
| public int stringLen()                                                | Provides the string length for an extended data type that is based on the string data type.                                                                              |
| public boolean stringRight()                                          | Indicates whether the string is right-justified for an extended data type that is based on the string data type.                                                         |
| ::public static Alignment getTypeAlignment(Types type)                |                                                                                                                                                                          |
| ::public static int getTypeDisplayHeight(Types type)                  |                                                                                                                                                                          |
| ::public static int getTypeDisplayLength(Types type)                  | Retrieves the display length for built-in types.                                                                                                                         |
| public void setValue(AnyType Value, \[int arrayEntry\])               |                                                                                                                                                                          |
| public void new(ExtendedTypeId typeId)                                | Initializes a new instance of the Object class.                                                                                                                          |
| public void setStringLen(int stringLen)                               | Sets the string length for an extended data type that is based on the string data type.                                                                                  |
| public void setStringRight(boolean right)                             | Indicates the string justification for an extended data type that is based on a String data type.                                                                        |

### Method alignment

Retrieves the alignment for the extended data type.

    public Alignment alignment()

#### Return Value

The alignment for the extended data type.

### Method arraySize

Provides the array size for an extended data type.

    public int arraySize()

#### Return Value

An integer value for the array size; 1 if an extended data type does not have array elements.

#### Examples

In the following example, the arraySize method returns the array size for the XMLMapDimension extended data type.

        DictType dicttype; 
        int i; 
        dicttype = new DictType(extendedTypeNum(XMLMapDimension)); 
        for (i = 1;  i < dicttype.arraySize(); i++) 
        { 
            print dicttype.label(i); 
            pause; 
        }

### Method baseType

Provides the data type on which an extended data type is based, by using the Types enumeration.

    public Types baseType()

#### Return Value

A Types enumeration value that indicates the data type.

#### Remarks

You can convert the return value to a string by using the Global::Enum2Value method.

### Method configurationKeyId

Returns the ID of the configuration key for the extended data type.

    public ConfigurationKeyId configurationKeyId()

#### Return Value

The ID of the configuration key for the extended data type.

### Method displayHeight

Retrieves the display height for the type.

    public int displayHeight([boolean useDefaults])

#### Parameters

useDefaults  
A Boolean value that indicates whether to use the default values if the type does not have a length.

#### Return Value

The display height for the type.

### Method displayLength

    public int displayLength([boolean useDefaults])

#### Parameters

useDefaults  

#### Return Value

### Method enumId

Provides the ID for the enumeration type on which an extended data type is based.

    public EnumId enumId()

#### Return Value

The ID of the enumeration type on which the extended data type is based; 0 (zero) if the extended data type is not based on an enumeration.

#### Remarks

You can use the baseType method to determine what the data type of an extended data type is.

### Method extend

Provides the ID for the extended data type that an extended data type extends.

    public ExtendedTypeId extend()

#### Return Value

The ID for the extended data type than an extended data type extends; 0 (zero) if the extended data type does not extend an extended data type.

#### Examples

In the following example, the extend method returns the ID for the extended data type that the ABCPercentA extended data type extends.

        DictType dicttype; 
        dicttype = new DictType(extendedTypeNum(ABCPercentA)); 
        print dicttype.name() + " extends: " + extendedTypeId2Name(dicttype.extend());

### Method extendedBy

Retrieves a list of type IDs for extended data types (EDTs) that are extended by the current EDT.

    public List extendedBy([boolean allLevels])

#### Parameters

allLevels  

#### Return Value

A list of type IDs for EDTs that are extended by the current EDT.

### Method formHelp

    public str formHelp()

#### Return Value

### Method getControlClass

    public str getControlClass()

#### Return Value

### Method getCountryRegionCodes

Retrieves a container that holds the country/region codes that are defined.

    public container getCountryRegionCodes()

#### Return Value

A container that holds country/region codes.

### Method getLookupRelation

    public DictRelation getLookupRelation([int arrayIndex])

#### Parameters

arrayIndex  

#### Return Value

### Method getValue

    public AnyType getValue([int arrayIndex])

#### Parameters

arrayIndex  

#### Return Value

### Method help

Provides the Help text that is displayed for an extended data type or a specified array element, or for the extended data type that an extended data type extends.

    public str help([int arrayIndex], [boolean useInterfaceLanguage])

#### Parameters

arrayIndex  
A Boolean value that indicates whether the user interface language is used for the Help text; optional.

<!-- -->

useInterfaceLanguage  
A Boolean value that indicates whether the user interface language is used for the Help text; optional.

#### Return Value

A string value for the Help text that is displayed for the extended data type, or for an array element if the arrayEntry value is provided. The Help text corresponds to the Help Text property for an extended data type or array element in the Microsoft Dynamics 365 for Operations Application Object Tree (AOT). When an extended data type does not have Help text, the method returns the Help text that is defined for the extended data type that the extended data type extends.

### Method helpDefined

Returns the value of the help property for the extended data type.

    public str helpDefined([int arrayIndex])

#### Parameters

arrayIndex  

#### Return Value

The value of the help property for the extended data type, or for an array element if the arrayEntry value is provided. The Help text corresponds to the Help Text property for an extended data type or array element in the AOT.

### Method id

Provides the ID for an extended data type.

    public ExtendedTypeId id()

#### Return Value

A data type value that indicates the ID for an extended data type.

### Method isExtendedFrom

Determines whether the extended data type extends from the base extended data type that is provided.

    public boolean isExtendedFrom(str baseEDTName)

#### Parameters

baseEDTName  
The name of the extended data type.

#### Return Value

true if the extended data type extends from the base extended data type that is provided; otherwise, false.

### Method isRadioStyle

Indicates whether the style of an extended data type that is based on an Enum data type is a radio button or a combo box.

    public int isRadioStyle()

#### Return Value

1 if the style is a radio button; otherwise, 0 (zero).

### Method label

Provides the label that is displayed for an extended data type or a specified array element, or the label for the extended data type that an extended data type extends.

    public str label([int arrayIndex])

#### Parameters

arrayIndex  

#### Return Value

The label that is displayed for an extended data type, or the label for an array element if the arrayEntry value is provided. When an extended data type does not have a label, this method returns the label defined for the extended data type that an extended data type extends.

#### Remarks

The label that is returned corresponds to the Label property for an extended data type or array element in the AOT.

### Method labelDefined

Returns the value of the label property for the extended data type.

    public str labelDefined([int arrayIndex])

#### Parameters

arrayIndex  

#### Return Value

The value of the label property for the extended data type, or for an array element if the arrayEntry value is provided.

#### Remarks

The return value corresponds to the Label property for an extended data type or array element in the AOT.

### Method lookupTable

    public str lookupTable([boolean useInheritedMetaData])

#### Parameters

useInheritedMetaData  

#### Return Value

### Method name

Provides the name of an extended data type.

    public str name()

#### Return Value

A string value for the name. The name corresponds to the Name property for an extended data type in the AOT.

### Method relationObject

Provides information about relations that are defined for an extended data type or a specified array element by returning a DictRelation object.

    public DictRelation relationObject([int arrayIndex])

#### Parameters

arrayIndex  

#### Return Value

A DictRelation object that provides information about relations.

#### Remarks

If no relations are defined for the extended data type and array elements, subsequent use of the DictRelation instance will cause a run-time error.

#### Examples

In the following example, the relationObject method returns the DictRelation object for the XMLMapDimension extended data type.

        DictType dicttype; 
        DictRelation dictrelation; 
        dicttype = new DictType(extendedTypeNum(XMLMapDimension)); 
        dictrelation = dicttype.relationObject(); 
        if(dictrelation) 
        { 
            print "Relation lines: " + int2str(dictrelation.lines()); 
        } 
        else 
        { 
            print "No relations defined."; 
         }

### Method stringLen

Provides the string length for an extended data type that is based on the string data type.

    public int stringLen()

#### Return Value

An integer that indicates the string length; 0 (zero) if an extended data type is not based on the string data type.

### Method stringRight

Indicates whether the string is right-justified for an extended data type that is based on the string data type.

    public boolean stringRight()

#### Return Value

true if the string is right-justified; otherwise, false.

#### Remarks

The return value corresponds to the Adjustment property for the extended data type in the AOT.

### Method getTypeAlignment

    public static Alignment getTypeAlignment(Types type)

#### Parameters

type  

#### Return Value

### Method getTypeDisplayHeight

    public static int getTypeDisplayHeight(Types type)

#### Parameters

type  

#### Return Value

### Method getTypeDisplayLength

Retrieves the display length for built-in types.

    public static int getTypeDisplayLength(Types type)

#### Parameters

type  
The type.

#### Return Value

The display length for the built-in type.

### Method setValue

    public void setValue(AnyType Value, [int arrayEntry])

#### Parameters

Value  

<!-- -->

arrayEntry  

### Method new

Initializes a new instance of the Object class.

    public void new(ExtendedTypeId typeId)

#### Parameters

typeId  
A data type that indicates the ID for an extended data type.

#### Remarks

This constructor does not fail if the typeId value is an invalid extended data type ID; however, when the DictType instance is used, a run-time error occurs. You can pass the name of the extended data type instead of an ID by using the extendedTypeNum function.

#### Examples

The following example shows how to create an instance of the DictType class.

        DictType dicttype; 
        dicttype = new DictType(extendedTypeNum(ABCModelType));

### Method setStringLen

Sets the string length for an extended data type that is based on the string data type.

    public void setStringLen(int stringLen)

#### Parameters

stringLen  
An integer that indicates the string length.

#### Remarks

This method lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called. The string length corresponds to the StringSize property for the extended data type in the AOT.

#### Examples

The following example sets the StringSize property to 10 for the AccountName extended data type.

    server static public void Main(Args _args) 
    { 
        DictType  dt; 
        dt = new DictType(ExtendedTypeNum(AccountName)); 
        if (dt) 
        { 
            dt.setStringLen(10); 
        } 
    }

### Method setStringRight

Indicates the string justification for an extended data type that is based on a String data type.

    public void setStringRight(boolean right)

#### Parameters

right  
A Boolean value: true for a right-justified string and false for a left-justified string.

#### Remarks

This method lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

#### Examples

The following example sets the justification of the AccountName extended data type.

    server static public void Main(Args _args) 
    { 
        DictType dt; 
        dt = new DictType(ExtendedTypeNum(AccountName)); 
        if (dt) 
        { 
            dt.setStringRight(true); 
        } 
    }

## Class DictView
    class DictView extends DictTable

The DictView class provides access to information about a particular view.

### Remarks

### Examples

### Methods

| Method                                                                                                                               | Description                                                                                                 |
|--------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| public str computedColumnString(str dataSourceName, str fieldName, \[FieldNameGenerationMode generationMode\], \[boolean needTrim\]) | Retrieves the table alias.                                                                                  |
| public int datasourceCnt()                                                                                                           | Counts data sources in the view.                                                                            |
| public str datasourceDataareaIdName(int cnt)                                                                                         | Retrieves the SQL name that is used in the view definition to identify the legal entity of the data source. |
| public TableId datasourceID2TableId(TableId dataSourceId)                                                                            | Gets the table ID of the given data source.                                                                 |
| public TableId datasourceTableId(int cnt)                                                                                            | Retrieves the table ID of the indexed data source.                                                          |
| public SelectionField fieldAggregation(FieldId fieldId)                                                                              | Retrieves the type of aggregation that a given field performs.                                              |
| public int fieldDatasource(FieldId fieldId)                                                                                          | Retrieves the ID of the data source that the given field originates from.                                   |
| public TableId fieldDatasourceID(FieldId fieldId)                                                                                    | Retrieves the ID of the data source in the view that the given field maps to.                               |
| public FieldId fieldId(FieldId fieldId)                                                                                              | Retrieves the field ID from the underlying table.                                                           |
| public boolean isAggregatedView()                                                                                                    | Checks whether the view is aggregated.                                                                      |
| public Query query()                                                                                                                 |                                                                                                             |
| public boolean isDataEntity()                                                                                                        |                                                                                                             |
| public boolean isUpdatable()                                                                                                         |                                                                                                             |
| public boolean isPublic()                                                                                                            |                                                                                                             |
| public str collectionName()                                                                                                          |                                                                                                             |
| public boolean isVirtualField(str fieldName)                                                                                         |                                                                                                             |
| public FieldAccessModifier getFieldAccessModifier(str fieldName)                                                                     |                                                                                                             |
| public boolean isStaged()                                                                                                            |                                                                                                             |
| public str version()                                                                                                                 |                                                                                                             |
| public MessagingRole messagingRole()                                                                                                 |                                                                                                             |
| public void new(TableId tableId)                                                                                                     | Initializes a new instance of the Object class.                                                             |

### Method computedColumnString

Retrieves the table alias.

    public str computedColumnString(str dataSourceName, str fieldName, [FieldNameGenerationMode generationMode], [boolean needTrim])

#### Parameters

dataSourceName  

<!-- -->

fieldName  

<!-- -->

generationMode  

<!-- -->

needTrim  

#### Return Value

The formatted field name string.

#### Remarks

The table alias is an SQL field name in a database-style format that can be used together with a computed column definition.

### Method datasourceCnt

Counts data sources in the view.

    public int datasourceCnt()

#### Return Value

The number of data sources in the view.

### Method datasourceDataareaIdName

Retrieves the SQL name that is used in the view definition to identify the legal entity of the data source.

    public str datasourceDataareaIdName(int cnt)

#### Parameters

cnt  

#### Return Value

The SQL name that is used in the view definition to identify the legal entity of the data source; a empty string if an error occurs.

### Method datasourceID2TableId

Gets the table ID of the given data source.

    public TableId datasourceID2TableId(TableId dataSourceId)

#### Parameters

dataSourceId  

#### Return Value

The table ID of the given data source.

### Method datasourceTableId

Retrieves the table ID of the indexed data source.

    public TableId datasourceTableId(int cnt)

#### Parameters

cnt  

#### Return Value

The table ID of the given data source; 0 (zero) if an error occurs.

### Method fieldAggregation

Retrieves the type of aggregation that a given field performs.

    public SelectionField fieldAggregation(FieldId fieldId)

#### Parameters

fieldId  

#### Return Value

The type of aggregation.

### Method fieldDatasource

Retrieves the ID of the data source that the given field originates from.

    public int fieldDatasource(FieldId fieldId)

#### Parameters

fieldId  

#### Return Value

The data source ID.

### Method fieldDatasourceID

Retrieves the ID of the data source in the view that the given field maps to.

    public TableId fieldDatasourceID(FieldId fieldId)

#### Parameters

fieldId  

#### Return Value

The data source ID.

### Method fieldId

Retrieves the field ID from the underlying table.

    public FieldId fieldId(FieldId fieldId)

#### Parameters

fieldId  

#### Return Value

The field ID from the underlying table.

### Method isAggregatedView

Checks whether the view is aggregated.

    public boolean isAggregatedView()

#### Return Value

true if the view is aggregated; otherwise, false.

### Method query

    public Query query()

#### Return Value

### Method isDataEntity

    public boolean isDataEntity()

#### Return Value

### Method isUpdatable

    public boolean isUpdatable()

#### Return Value

### Method isPublic

    public boolean isPublic()

#### Return Value

### Method collectionName

    public str collectionName()

#### Return Value

### Method isVirtualField

    public boolean isVirtualField(str fieldName)

#### Parameters

fieldName  

#### Return Value

### Method getFieldAccessModifier

    public FieldAccessModifier getFieldAccessModifier(str fieldName)

#### Parameters

fieldName  

#### Return Value

### Method isStaged

    public boolean isStaged()

#### Return Value

### Method version

    public str version()

#### Return Value

### Method messagingRole

    public MessagingRole messagingRole()

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(TableId tableId)

#### Parameters

tableId  
The table ID to use to create the class instance.

## Class DLL
    class DLL extends Object

The DLL class enables communication with a MicrosoftWindows dynamic-link library (DLL).

### Remarks

If you are using a Unicode DLL, do the following:

-   Use ExtTypes::WString instead of ExtTypes::String to specify a string type.
-   Use Binary::WString instead of Binary::String if you have character data embedded in a binary structure.
-   Use the Binary.wstring method instead of the Binary.string method if you have to read a string from a binary object.

### Examples

The following example uses the DLL and DLLFunction classes to interoperate with the GetVersion API in Kernel32.dll. This example asserts the use of the InteropPermission class, which is required only if the code is running on the server. It loads the DLL and, if it is successful, sets the return type from the call to the DLLFunction class.

    void DLLExample() 
    { 
        Dll               dll; 
        DllFunction       dllFunc; 
        anytype           retVal; 
        InteropPermission perm; 
        perm = new InteropPermission(InteropKind::DllInterop); 
        // Grants permission to execute the DLL.new method.  
        // DLL.new runs under code access security. 
        perm.assert(); 
        dll = new Dll("Kernel32.dll"); 
        // Closes the code access permission scope. 
           CodeAccessPermission::revertAssert(); 
        if (dll != null) 
        { 
            perm = new InteropPermission(InteropKind::DllInterop); 
        // Grants permission to execute the DLLFunction.new method.  
        // DLLFunction.new runs under code access security. 
            perm.assert(); 
            dllFunc = new DllFunction(dll, "GetVersion"); 
            if (dllFunc != null) 
            { 
                 dllFunc.returns(ExtTypes::DWord); 
                retVal = dllFunc.call(); 
            } 
            // Closes the code access permission scope. 
           CodeAccessPermission::revertAssert(); 
        } 
    }

### Methods

| Method                             | Description                                                                               |
|------------------------------------|-------------------------------------------------------------------------------------------|
| ::public static int lastDLLError() | Sets or retrieves the last error that was reported by the DLL.                            |
| public void new(str filename)      | Creates an instance of the DLL class.                                                     |
| public void finalize()             | Releases resources and performs clean-up before an instance of the DLL class is released. |

### Method lastDLLError

Sets or retrieves the last error that was reported by the DLL.

    public static int lastDLLError()

#### Return Value

The last error that was reported by the DLL.

### Method new

Creates an instance of the DLL class.

    public void new(str filename)

#### Parameters

filename  
The file name of the DLL to use to create the instance of the DLL class.

#### Remarks

To access a DLL function, use a created instance of the DLL class in a call to the DLLFunction::new method. If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the InteropPermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

#### Examples

The following example uses the DLL and DLLFunction classes to interoperate with the GetVersion API in Kernel32.dll. This example asserts the use of the InteropPermission class. It loads the DLL and, if it is successful, sets the return type from the call in the DLLFunction class.

    void DLLExample() 
    { 
        Dll               dll; 
        DllFunction       dllFunc; 
        anytype           retVal; 
        InteropPermission perm; 
        perm = new InteropPermission(InteropKind::DllInterop); 
        // Grants permission to execute the DLL.new method. 
        // DLL.new runs under code access security. 
        perm.assert(); 
        dll = new Dll("Kernel32.dll"); 
        // Closes the code access permission scope. 
           CodeAccessPermission::revertAssert(); 
        if (dll != null) 
        { 
            perm = new InteropPermission(InteropKind::DllInterop); 
           // Grants permission to execute the DLLFunction.new method. 
           // DLLFunction.new runs under code access security. 
            perm.assert(); 
            dllFunc = new DllFunction(dll, "GetVersion"); 
            if (dllFunc != null) 
            { 
                 dllFunc.returns(ExtTypes::DWord); 
                retVal = dllFunc.call(); 
            } 
            // Close the code access permission scope. 
           CodeAccessPermission::revertAssert(); 
        } 
    }

### Method finalize

Releases resources and performs clean-up before an instance of the DLL class is released.

    public void finalize()

## Class DLLFunction
    class DLLFunction extends Object

### Remarks

### Examples

### Methods

| Method                                           | Description                                     |
|--------------------------------------------------|-------------------------------------------------|
| public AnyType call(VarArg )                     |                                                 |
| public ExtTypes returns(\[ExtTypes returnType\]) |                                                 |
| public void new(DLL dll, str functionname)       | Initializes a new instance of the Object class. |
| public void finalize()                           |                                                 |
| public void arg(VarArg )                         |                                                 |

### Method call

    public AnyType call(VarArg )

#### Parameters

  

#### Return Value

#### Remarks

If an attacker can control input to the call method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

#### Examples

The following example uses the DLL and DLLFunction classes to interoperate with the GetVersion API in Kernel32.dll. It asserts the use of the InteropPermission class to provide code access protection, and then it loads the DLL. If this is successful, the return type is set from the call to the DLLFunction class.

    { 
        Dll               dll; 
        DllFunction       dllFunc; 
        anytype           retVal; 
        InteropPermission perm; 
        perm = new InteropPermission(InteropKind::DllInterop); 
        // Grants permission to execute the DLL.new method. 
        // DLL.new is protected by code access security. 
        perm.assert(); 
        dll = new Dll("Kernel32.dll"); 
        // Closes the code access permission scope. 
        CodeAccessPermission::revertAssert(); 
        if (dll != null) 
        { 
            // Grants permission to execute the DLLFunction.new method. 
            // DLLFunction.new is protected by code access security. 
            perm = new InteropPermission(InteropKind::DllInterop); 
            perm.assert(); 
            dllFunc = new DllFunction(dll, "GetVersion"); 
            if (dllFunc != null) 
             { 
                dllFunc.returns(ExtTypes::DWord); 
                 retVal = dllFunc.call(); 
             } 
           // Closes the code access permission scope. 
           CodeAccessPermission::revertAssert(); 
        } 
    }

### Method returns

    public ExtTypes returns([ExtTypes returnType])

#### Parameters

returnType  

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(DLL dll, str functionname)

#### Parameters

dll  

<!-- -->

functionname  

### Method finalize

    public void finalize()

### Method arg

    public void arg(VarArg )

#### Parameters

  

## Class DocNode
    class DocNode extends TreeNode

The DocNode class provides the information and functions for a documentation node.

### Remarks

This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                                                                                                                                            | Description                                                                                                                             |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| public str AOTgetSource()                                                                                                                                                                         | Returns the source code for the node.                                                                                                   |
| public str changedBy(\[str value\])                                                                                                                                                               | Gets or sets the name of the user who last changed the application object.                                                              |
| public Date changedDate(\[Date value\])                                                                                                                                                           | Gets or sets the date that an application object was last changed.                                                                      |
| public str changedTime(\[str value\])                                                                                                                                                             | Gets or sets the time that an application object was last changed.                                                                      |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                                                                                                          | Gets or sets the configuration key that is assigned to the control.                                                                     |
| public str createdBy(\[str value\])                                                                                                                                                               | Gets or sets the name of the user who created the application object.                                                                   |
| public Date creationDate(\[Date value\])                                                                                                                                                          | Gets or sets the date that an application object was created.                                                                           |
| public str creationTime(\[str value\])                                                                                                                                                            |                                                                                                                                         |
| public str description(\[str value\])                                                                                                                                                             | Sets or returns the description of the documentation node.                                                                              |
| public str name(\[str value\])                                                                                                                                                                    | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object. |
| public int neededAccessLevel(\[int value\])                                                                                                                                                       | Gets or sets the neededAccessLevel property for the MenuFunction class.                                                                 |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                                                                                                         | Sets or returns the security key for the documentation node.                                                                            |
| public str title(\[str value\])                                                                                                                                                                   | Sets or returns the title of the documentation node.                                                                                    |
| ::public static DocNode findAOTElementDocNode(ApplCodeDocType HelpType, str Name, \[str ParentName\], \[int Mode\])                                                                               | Performs a search for an element documentation node in the Microsoft Dynamics 365 for Operations Application Object Tree (AOT).                         |
| ::public static DocNode findApplicationDocNode(ApplHelpType HelpType, str Name, \[str ParentName\], \[int Mode\])                                                                                 | Performs a search for an application element documentation node.                                                                        |
| ::public static DocNode findKernelDocNode(KernelHelpType HelpType, str Name, \[str ParentName\], \[int Mode\])                                                                                    | Performs a search for a kernel element documentation node.                                                                              |
| ::public static DocNode getNodeDetached(UtilFileType helpType, int UtilType, str Name, \[int ParentId\], \[int Type\], \[UtilEntryLevel Utillevel\], \[boolean Forcelevel\], \[boolean OldUtil\]) | Returns the specified documentation node.                                                                                               |
| public void AOTsetSource(str source, \[boolean isStatic\])                                                                                                                                        | Sets the source code for the node.                                                                                                      |
| public void AOTedit(\[int Line\], \[int Column\])                                                                                                                                                 | Opens the appropriate editor for this node.                                                                                             |

### Method AOTgetSource

Returns the source code for the node.

    public str AOTgetSource()

#### Return Value

The source code for the node as a string; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if there is no source code for the node.

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  
The value that is being assigned as the user who changed the documentation node.

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date that an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  
The value that is being assigned as the change date for the documentation node.

#### Return Value

The date that an application object was last changed.

### Method changedTime

Gets or sets the time that an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  
The value that is being assigned as the change time for the documentation node.

#### Return Value

The time that an application object was last changed.

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  
The value that is being assigned for the configuration key ID.

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  
The value that is being assigned as the user who created the documentation node.

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date that an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  
The value that is being assigned as the creation date for the documentation node.

#### Return Value

The date that an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method description

Sets or returns the description of the documentation node.

    public str description([str value])

#### Parameters

value  
The value that is being assigned as the description of the documentation node.

#### Return Value

The description of the documentation node.

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  
The name that is being assigned to the documentation node.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must begin with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, and classes.

### Method neededAccessLevel

Gets or sets the neededAccessLevel property for the MenuFunction class.

    public int neededAccessLevel([int value])

#### Parameters

value  

#### Return Value

The current value of the neededAccessLevel property.

#### Remarks

The possible values for the AccessType system enumuration value are as follows:

-   AccessType::NoAccess.
-   AccessType::View.
-   AccessType::Edit.
-   AccessType::Add.
-   AccessType::Delete.

### Method securityKey

Sets or returns the security key for the documentation node.

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  
The value that is being assigned for the security key ID.

#### Return Value

The security key ID for the documentation node; 0 (zero) if no security key is associated with the documentation node.

### Method title

Sets or returns the title of the documentation node.

    public str title([str value])

#### Parameters

value  
The title that is being assigned to the documentation node.

#### Return Value

The title of the documentation node.

### Method findAOTElementDocNode

Performs a search for an element documentation node in the Microsoft Dynamics 365 for Operations Application Object Tree (AOT).

    public static DocNode findAOTElementDocNode(ApplCodeDocType HelpType, str Name, [str ParentName], [int Mode])

#### Parameters

HelpType  
The mode to use for the search; optional.

<!-- -->

Name  
The mode to use for the search; optional.

<!-- -->

ParentName  
The mode to use for the search; optional.

<!-- -->

Mode  
The mode to use for the search; optional.

#### Return Value

The node that is found; otherwise, null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic).

### Method findApplicationDocNode

Performs a search for an application element documentation node.

    public static DocNode findApplicationDocNode(ApplHelpType HelpType, str Name, [str ParentName], [int Mode])

#### Parameters

HelpType  
The mode to use for the search; optional.

<!-- -->

Name  
The mode to use for the search; optional.

<!-- -->

ParentName  
The mode to use for the search; optional.

<!-- -->

Mode  
The mode to use for the search; optional.

#### Return Value

The node that is found; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the node was not found.

### Method findKernelDocNode

Performs a search for a kernel element documentation node.

    public static DocNode findKernelDocNode(KernelHelpType HelpType, str Name, [str ParentName], [int Mode])

#### Parameters

HelpType  
The mode to use for the search; optional.

<!-- -->

Name  
The mode to use for the search; optional.

<!-- -->

ParentName  
The mode to use for the search; optional.

<!-- -->

Mode  
The mode to use for the search; optional.

#### Return Value

The node that is found; otherwise, null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic).

### Method getNodeDetached

Returns the specified documentation node.

    public static DocNode getNodeDetached(UtilFileType helpType, int UtilType, str Name, [int ParentId], [int Type], [UtilEntryLevel Utillevel], [boolean Forcelevel], [boolean OldUtil])

#### Parameters

helpType  
Reserved; optional.

<!-- -->

UtilType  
Reserved; optional.

<!-- -->

Name  
Reserved; optional.

<!-- -->

ParentId  
Reserved; optional.

<!-- -->

Type  
Reserved; optional.

<!-- -->

Utillevel  
Reserved; optional.

<!-- -->

Forcelevel  
Reserved; optional.

<!-- -->

OldUtil  
Reserved; optional.

#### Return Value

The specified documentation node.

### Method AOTsetSource

Sets the source code for the node.

    public void AOTsetSource(str source, [boolean isStatic])

#### Parameters

source  
A Boolean value that indicates whether the method is static.

<!-- -->

isStatic  
A Boolean value that indicates whether the method is static.

### Method AOTedit

Opens the appropriate editor for this node.

    public void AOTedit([int Line], [int Column])

#### Parameters

Line  
The column of the cursor position; optional.

<!-- -->

Column  
The column of the cursor position; optional.

#### Remarks

If the node is a method, the code editor opens. If the node is a documentation object, the Help editor opens.

## Class DynamicPropertyCallback
    class DynamicPropertyCallback

### Remarks

### Examples

### Methods

| Method                                                              | Description |
|---------------------------------------------------------------------|-------------|
| public boolean propChanged(str propertyName, AnyType propertyValue) |             |

### Method propChanged

    public boolean propChanged(str propertyName, AnyType propertyValue)

#### Parameters

propertyName  

<!-- -->

propertyValue  

#### Return Value

## Class DynamicPropertyManager
    class DynamicPropertyManager extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                                      | Description                                                     |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| public DynamicPropertyCallback callbackObject()                                                                                                                                             |                                                                 |
| public str getConfigString()                                                                                                                                                                | Microsoft internal use only.                                    |
| public int hasSheetChanged()                                                                                                                                                                | Microsoft internal use only.                                    |
| public Struct propertyValues()                                                                                                                                                              |                                                                 |
| public void allowEdit(str name, boolean allow)                                                                                                                                              |                                                                 |
| public void updateValue(str propertyname, str value)                                                                                                                                        |                                                                 |
| public void new()                                                                                                                                                                           | Initializes a new instance of the DynamicPropertyManager class. |
| public void getPropertySheet(str configString, boolean canWebletTypeChange)                                                                                                                 | Microsoft internal use only.                                    |
| public void noProperties()                                                                                                                                                                  |                                                                 |
| public void allowDisplay(str name, boolean allow)                                                                                                                                           |                                                                 |
| public void refresh()                                                                                                                                                                       |                                                                 |
| public void setProperties(int propertySetId, str caption, Struct values, \[Struct defaultValues\], \[Struct categories\], \[DynamicPropertyCallback callbackObject\], \[boolean setFocus\]) |                                                                 |

### Method callbackObject

    public DynamicPropertyCallback callbackObject()

#### Return Value

### Method getConfigString

Microsoft internal use only.

    public str getConfigString()

#### Return Value

A configuration string.

### Method hasSheetChanged

Microsoft internal use only.

    public int hasSheetChanged()

#### Return Value

A value that indicates whether the sheet has changed.

### Method propertyValues

    public Struct propertyValues()

#### Return Value

### Method allowEdit

    public void allowEdit(str name, boolean allow)

#### Parameters

name  

<!-- -->

allow  

### Method updateValue

    public void updateValue(str propertyname, str value)

#### Parameters

propertyname  

<!-- -->

value  

### Method new

Initializes a new instance of the DynamicPropertyManager class.

    public void new()

### Method getPropertySheet

Microsoft internal use only.

    public void getPropertySheet(str configString, boolean canWebletTypeChange)

#### Parameters

configString  
A value that indicates whether the weblet type can change.

<!-- -->

canWebletTypeChange  
A value that indicates whether the weblet type can change.

### Method noProperties

    public void noProperties()

### Method allowDisplay

    public void allowDisplay(str name, boolean allow)

#### Parameters

name  

<!-- -->

allow  

### Method refresh

    public void refresh()

### Method setProperties

    public void setProperties(int propertySetId, str caption, Struct values, [Struct defaultValues], [Struct categories], [DynamicPropertyCallback callbackObject], [boolean setFocus])

#### Parameters

propertySetId  

<!-- -->

caption  

<!-- -->

values  

<!-- -->

defaultValues  

<!-- -->

categories  

<!-- -->

callbackObject  

<!-- -->

setFocus  





