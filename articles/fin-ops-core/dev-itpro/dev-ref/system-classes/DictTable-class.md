---
title: DictTable class
description: This topic describes the DictTable class.
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

# Class DictTable

[!include [banner](../../includes/banner.md)]

```xpp
class DictTable extends Object
```

The DictTable class provides information about a table.

## Remarks

## Examples

The following example shows how to create an instance of the DictTable class to determine whether the data in the table is stored on a per-company basis.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print (strfmt("The table is saved on a %1 basis.", dt.dataPrCompany() ? 
                      "per company" : "global")); 
}
```

## Methods

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

## Method doesMethodExist

Checks whether a given method exists on the table.

```xpp
public boolean doesMethodExist(str name)
```

### Parameters - doesMethodExist

name  

### Return Value - doesMethodExist

true if the given method exists on the table; otherwise, false.

### Remarks - doesMethodExist

This API is the preferred way to check whether a method exists on the table without checking whether the method compiled successfully.

## Method AOSAuthSetting

Retrieves an AOSAuthorization system enumeration value that specifies the type of operation that a user can perform on a table, depending on the permissions of the user.

```xpp
public AOSAuthorization AOSAuthSetting()
```

### Return Value - AOSAuthSetting

An AOSAuthorization system enumeration value.

### Remarks - AOSAuthSetting

The AOSAuthorization::None value indicates that an authorization check is not performed. Use table properties to set the AOSAuthorization property for a table. In the Application Object Tree (AOT), right-click the table, and then click Properties to access the table properties.

### Examples - AOSAuthSetting

This following example shows a call to the AOSAuthSetting method.

```xpp
static public void Main(Args _args) 
{ 
    DictTable dt; 
    AOSAuthorization a; 
    dt = new DictTable(tablenum(CustTable)); 
    a = dt.AOSAuthSetting(); 
}
```

## Method cacheLookup

Returns the record cache level for the table.

```xpp
public RecordCacheLevel cacheLookup()
```

### Return Value - cacheLookup

A RecordCacheLevel value that indicates the record cache level for the table.

### Examples - cacheLookup

The following example shows the retrieval of the cache level for a table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print dt.cacheLookup(); 
}
```

## Method cacheSize

Returns the cache size for the table, in the number of records.

```xpp
public int cacheSize()
```

### Return Value - cacheSize

The cache size for the table.

### Examples - cacheSize

The following example retrieves the cache size for a table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(SysUserInfo)); 
if (dt) 
{ 
     print strfmt("Cache size: %1", dt.cacheSize()); 
}
```

## Method callObject

Calls the specified object method for a table.

```xpp
public AnyType callObject(str methodName, Common Called, VarArg )
```

### Parameters - callObject

methodName  

<!-- -->

Called  

<!-- -->


### Return Value - callObject

The results of the call to the methodName parameter.

### Remarks - callObject

If an attacker can control input to the callObject method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Examples - callObject

This example calls the SysUserLog.onlineTime static method in the SysUserLog table and then prints the value that is returned from the call.

```xpp
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
```

## Method callStatic

Calls the specified static method for a table.

```xpp
public AnyType callStatic(str methodName, VarArg )
```

### Parameters - callStatic

methodName  

<!-- -->


### Return Value - callStatic

The results of the call to the methodName parameter.

### Remarks - callStatic

If an attacker can control input to this function, a security risk exists. Therefore, the callStatic method runs under Code Access Security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Examples - callStatic

This example calls the SysUserInfo:find static method in the SysUserInfo table and then prints the value that is returned from the call to the callStatic method.

```xpp
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
```

## Method clusterIndex

Returns the ID of the clustered index for the table.

```xpp
public IndexId clusterIndex([boolean asDefinedInAOT])
```

### Parameters - clusterIndex

asDefinedInAOT  
A value that indicates whether the clustered index to retrieve is defined in the AOT. A value of true returns the clustered index as defined in the AOT. A value of false returns the clustered index as defined in the SQL table; optional.

### Return Value - clusterIndex

The ID of the clustered index for the table; 0 (zero) if there is no clustered index for the table.

### Examples - clusterIndex

The following example shows the retrieval of the clustered index for a table.

```xpp
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
```

## Method configurationKeyId

Returns the ID of the configuration key for the table.

```xpp
public ConfigurationKeyId configurationKeyId()
```

### Return Value - configurationKeyId

The ID of the configuration key for the table; 0 (zero) if there is no configuration key for the table.

### Examples - configurationKeyId

The following example shows the retrieval of the configuration key ID for a table.

```xpp
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
```

## Method dataPerPartition

Returns a value that indicates whether the data of the table is saved on a per-partition basis, and corresponds to the SaveDataPerPartition property of the table.

```xpp
public boolean dataPerPartition()
```

### Return Value - dataPerPartition

true if the data is saved on a per-partition basis; otherwise, false, and the data is saved globally for all partitions.

## Method dataPrCompany

Returns a value that indicates whether the data of the table is saved on a per-company basis, and corresponds to the SaveDataPerCompany property of the table.

```xpp
public boolean dataPrCompany()
```

### Return Value - dataPrCompany

true if the data is saved on a per-company basis; otherwise, false, and the data is saved globally for all companies.

### Examples - dataPrCompany

The following example shows the retrieval of the value that indicates whether the data is saved on a per-company basis.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print (strfmt("The table is saved on a %1 basis.", dt.dataPrCompany() ? "per company" : "global")); 
}
```

## Method deleteActionCnt

Retrieves the number of delete actions for the table.

```xpp
public int deleteActionCnt()
```

### Return Value - deleteActionCnt

The number of delete actions for the table.

### Examples - deleteActionCnt

The following example shows the retrieval of the number of delete actions for the table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print (strfmt("The table has %1 delete actions.", dt.deleteActionCnt())); 
}
```

## Method deleteActionRelation

```xpp
public str deleteActionRelation(int cnt)
```

### Parameters - deleteActionRelation

cnt  

### Return Value - deleteActionRelation

## Method deleteActionTableId

Returns the table ID of a table's delete action that is specified by an index.

```xpp
public TableId deleteActionTableId(int cnt)
```

### Parameters - deleteActionTableId

cnt  
A one-based index to the list of the delete actions for the table. The list is in AOT order.

### Return Value - deleteActionTableId

The table ID of the table's delete action that is specified by cnt; 0 (zero) if the cnt value does not represent a valid delete action index.

### Examples - deleteActionTableId

The following example shows the use of the deleteActionTableId method to retrieve the names of tables that have delete actions for the CustTable table.

```xpp
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
```

## Method deleteActionType

Retrieves the type of a delete action for a table.

```xpp
public int deleteActionType(int cnt)
```

### Parameters - deleteActionType

cnt  
The one-based index to the list of the delete actions for the table. The list is in AOT order.

### Return Value - deleteActionType

An integer that represents the type of the delete action of the table that is specified by the cnt parameter. It can be one of the values in the following table.

|     |                      |
|-----|----------------------|
| 0   | None                 |
| 1   | Cascade              |
| 2   | Restricted           |
| 3   | Cascade + Restricted |

### Examples - deleteActionType

The following example shows the retrieval of the type of delete actions for a table.

```xpp
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
```

## Method developerDocumentation

```xpp
public str developerDocumentation()
```

### Return Value - developerDocumentation

## Method developerDocumentationLabelId

```xpp
public str developerDocumentationLabelId()
```

### Return Value - developerDocumentationLabelId

## Method enabled

Returns a value that indicates whether the table is enabled.

```xpp
public boolean enabled()
```

### Return Value - enabled

true if the table is enabled; otherwise, false.

### Examples - enabled

The following example shows the retrieval of the value that indicates whether the table is enabled.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print (strfmt("The table is %1.", dt.enabled() ? "enabled" : "not enabled")); 
}
```

## Method enforceRelationRules

```xpp
public boolean enforceRelationRules()
```

### Return Value - enforceRelationRules

## Method entityRelationshipType

```xpp
public EntityRelationshipType entityRelationshipType()
```

### Return Value - entityRelationshipType

## Method extendedBy

```xpp
public List extendedBy([boolean allLevels])
```

### Parameters - extendedBy

allLevels  

### Return Value - extendedBy

## Method extends

Returns the table ID of a base table.

```xpp
public TableId extends()
```

### Return Value - extends

The table ID of the base table.

## Method fieldCnt

Returns the number of fields for a table.

```xpp
public int fieldCnt([TableScope tableScope])
```

### Parameters - fieldCnt

tableScope  

### Return Value - fieldCnt

The number of fields for the table.

### Examples - fieldCnt

The following example shows the retrieval of the number of fields for a table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print (strfmt("The table has %1 fields.", dt.fieldCnt())); 
}
```

## Method fieldCnt2Id

Returns the field ID of the field that is specified by an index.

```xpp
public FieldId fieldCnt2Id(int cnt, [TableScope tableScope])
```

### Parameters - fieldCnt2Id

cnt  

<!-- -->

tableScope  

### Return Value - fieldCnt2Id

The field ID of the field that is specified by an index.

### Examples - fieldCnt2Id

The following example shows the retrieval of the fields of a table by index.

```xpp
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
```

## Method fieldGroup

Returns the name of a field group that is specified by index.

```xpp
public str fieldGroup(int FieldGroupNumber, [TableScope tableScope])
```

### Parameters - fieldGroup

FieldGroupNumber  

<!-- -->

tableScope  

### Return Value - fieldGroup

The name of the field group that is specified by the FieldGroupNumber parameter.

### Examples - fieldGroup

The following example shows the retrieval of the names of the field groups for a table.

```xpp
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
```

## Method fieldGroupCnt

Returns the number of field groups for the table.

```xpp
public int fieldGroupCnt([TableScope tableScope])
```

### Parameters - fieldGroupCnt

tableScope  

### Return Value - fieldGroupCnt

The number of field groups for the table.

### Examples - fieldGroupCnt

The following example shows the retrieval of the number of field groups for a table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print (strfmt("The table has %1 field groups.", dt.fieldGroupCnt())); 
}
```

## Method fieldName

Returns the name of the field that is specified by field ID.

```xpp
public str fieldName(FieldId fieldId, [DbBackend db], [int arrayindex], [FieldNameGenerationMode generationMode], [str tableAlias])
```

### Parameters - fieldName

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

### Return Value - fieldName

The name of the field that is specified by its field ID.

### Remarks - fieldName

If db is not specified, the DbBackend::Native object is used.

### Examples - fieldName

The following example shows the retrieval of field names of a table as specified by the field IDs.

```xpp
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
```

## Method fieldName2Id

Returns the field ID of a field that is specified by name.

```xpp
public FieldId fieldName2Id(str name)
```

### Parameters - fieldName2Id

name  
The name of the field for which the field ID is being retrieved.

### Return Value - fieldName2Id

The field ID of the field that is specified by the name parameter; 0 (zero) if name does not represent a valid field name for the table.

### Examples - fieldName2Id

The following example shows the retrieval of a field ID by its field name.

```xpp
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
```

## Method fieldNext

Returns the value of the next field ID during a field iteration of the table.

```xpp
public FieldId fieldNext(FieldId fieldId, [TableScope tableScope])
```

### Parameters - fieldNext

fieldId  

<!-- -->

tableScope  

### Return Value - fieldNext

The ID of the next field in the field iteration for the table; 0 (zero) if there are no more fields to iterate.

### Remarks - fieldNext

The value of the fieldId parameter should evaluate to 0 (zero) to start the field iteration, and the return value should be used for subsequent calls to the iteration.

### Examples - fieldNext

The following example iterates through the fields of a table.

```xpp
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
```

## Method fieldObject

Creates an instance of the DictField class for the field that is specified by field ID.

```xpp
public DictField fieldObject(FieldId fieldId)
```

### Parameters - fieldObject

fieldId  
The ID of the field to create.

### Return Value - fieldObject

A DictField object for the field that is specified by the fieldId parameter; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the object could not be created.

### Examples - fieldObject

The following example shows how to create a DictField object for the fields in a table.

```xpp
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
```

## Method fieldOrigin2Id

```xpp
public IndexId fieldOrigin2Id(Guid fieldOrigin, [TableScope tableScope])
```

### Parameters - fieldOrigin2Id

fieldOrigin  

<!-- -->

tableScope  

### Return Value - fieldOrigin2Id

## Method fieldSqlDefault

Returns the SQL default value for the field that is specified by field ID.

```xpp
public str fieldSqlDefault(FieldId fieldId)
```

### Parameters - fieldSqlDefault

fieldId  
The ID of the field for which the SQL default data is being retrieved.

### Return Value - fieldSqlDefault

A string that represents the SQL default value for the field that is specified by the fieldId parameter; an empty string if the field has no SQL default value or the table is not an SQL table.

## Method formRef

Returns the name of the default form for the table.

```xpp
public str formRef([boolean searchBaseTables])
```

### Parameters - formRef

searchBaseTables  

### Return Value - formRef

The name of the default form for the table.

### Remarks - formRef

If the AOT shows no value for the FormRef property of a table, the name of the default form for the table is considered to be the same as the name of the table. In this case, this method does not return an empty string.

### Examples - formRef

The following example shows the retrieval of the default form for a table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print strfmt("Default form: %1", dt.formRef()); 
}
```

## Method getCountryRegionCodes

```xpp
public container getCountryRegionCodes()
```

### Return Value - getCountryRegionCodes

## Method getCountryRegionContextField

```xpp
public FieldId getCountryRegionContextField()
```

### Return Value - getCountryRegionContextField

## Method getValidTimeStateValidFromFieldId

```xpp
public FieldId getValidTimeStateValidFromFieldId()
```

### Return Value - getValidTimeStateValidFromFieldId

## Method getValidTimeStateValidToFieldId

```xpp
public FieldId getValidTimeStateValidToFieldId()
```

### Return Value - getValidTimeStateValidToFieldId

## Method hasRecidIdx

Returns a value that indicates whether a record ID index for the table is in effect.

```xpp
public boolean hasRecidIdx()
```

### Return Value - hasRecidIdx

true if a record ID index is in effect for the table; otherwise, false.

### Remarks - hasRecidIdx

The return value corresponds to whether the CreateRecIdIndex property of the table is set to Yes.

### Examples - hasRecidIdx

The following example shows the retrieval of a value that indicates whether the record ID index of the table is in effect.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print (strfmt("A record ID index for the table %1 in effect.", 
           dt.hasRecidIdx() ? "is" : "is not") ); 
}
```

## Method hasSurrogateKey

```xpp
public boolean hasSurrogateKey()
```

### Return Value - hasSurrogateKey

## Method id

Returns the ID of the table.

```xpp
public TableId id()
```

### Return Value - id

The ID of the table.

### Examples - id

The following example shows the retrieval of the ID of a table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print (strfmt("The table ID is: %1", dt.id())); 
}
```

## Method indexCnt

Returns the number of indexes for the table.

```xpp
public int indexCnt()
```

### Return Value - indexCnt

The number of indexes for the table.

### Examples - indexCnt

The following example shows the retrieval of the number of indexes for a table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print (strfmt("The table has %1 indexes.", dt.indexCnt())); 
}
```

## Method indexCnt2Id

```xpp
public IndexId indexCnt2Id(int cnt)
```

### Parameters - indexCnt2Id

cnt  

### Return Value - indexCnt2Id

## Method indexName

Returns the name of an index that is specified by the indexId parameter.

```xpp
public str indexName(IndexId indexId, [DbBackend db])
```

### Parameters - indexName

indexId  
A DbBackend value that specifies the type of database back end; optional.

<!-- -->

db  
A DbBackend value that specifies the type of database back end; optional.

### Return Value - indexName

The name of the index that is specified by the indexId parameter.

### Examples - indexName

The following example shows the retrieval of the names of the indexes for a table.

```xpp
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
```

## Method indexName2Id

Returns the ID of an index that is specified by name.

```xpp
public IndexId indexName2Id(str name)
```

### Parameters - indexName2Id

name  
The name of the index.

### Return Value - indexName2Id

The ID of the index that is specified by the name parameter; 0 (zero) if there is no index that has a name that equals the name value.

### Examples - indexName2Id

The following example shows the retrieval of the ID of an index that is specified by name.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print(strfmt("Index ID: %1", dt.indexName2Id("TypeIdx"))); 
}
```

## Method indexNext

Returns the value of the next index ID during an index iteration of the table.

```xpp
public IndexId indexNext(IndexId id)
```

### Parameters - indexNext

id  
The ID of the index for which the next index ID is being queried.

### Return Value - indexNext

The ID of the next index in the index iteration for the table; 0 (zero) if there are no more indexes to iterate.

### Remarks - indexNext

The value of the id parameter should evaluate to 0 (zero) to start the index iteration, and the return value should be used for subsequent calls to the iteration.

### Examples - indexNext

The following example iterates through the indexes of a table.

```xpp
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
```

## Method indexObject

Creates an instance of the DictTable class for the index that is specified by ID.

```xpp
public DictIndex indexObject(IndexId indexId)
```

### Parameters - indexObject

indexId  
The ID of the index to create.

### Return Value - indexObject

A DictIndex object for the index that is specified by the indexId parameter; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the object could not be created.

### Examples - indexObject

The following example shows how to create a DictIndex object for the unique index of a table.

```xpp
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
```

## Method indexUnique

Returns the ID of the unique index for the table.

```xpp
public IndexId indexUnique()
```

### Return Value - indexUnique

The ID of the unique index for the table.

### Remarks - indexUnique

When there is more than one unique index on the table, the return value is one of the following:

-   The index that has the RecID column.
-   If no index has a record ID, the index that has the shortest size, based on the total size of columns.
-   If multiple indexes match with regard to the shortest size, the index that was added first.

### Examples - indexUnique

The following example shows the retrieval of the unique index for a table.

```xpp
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
```

## Method instanceRelationType

```xpp
public FieldId instanceRelationType()
```

### Return Value - instanceRelationType

## Method isAbstract

Indicates whether this table is abstract.

```xpp
public boolean isAbstract()
```

### Return Value - isAbstract

true if this table is abstract; otherwise, false.

## Method isBaseData

Indicates whether the table content is base data.

```xpp
public boolean isBaseData()
```

### Return Value - isBaseData

true if the TableContents property in the AOT indicates that the table content is base data; otherwise, false.

### Examples - isBaseData

The following example shows the retrieval of a value that indicates whether the table content is base data.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print strfmt("isBaseData: %1", dt.isBaseData()); 
    print strfmt("isDefaultData: %1", dt.isDefaultData()); 
}
```

## Method isDefaultData

Indicates whether the table contains default data.

```xpp
public boolean isDefaultData()
```

### Return Value - isDefaultData

true if the table contains default data; otherwise, false.

### Examples - isDefaultData

The following example shows the retrieval of a value that indicates whether the table contains default data.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print strfmt("isDefaultData: %1", dt.isDefaultData()); 
}
```

## Method isDerivedFrom

Indicates whether one table type derives from another.

```xpp
public boolean isDerivedFrom(TableName baseTableName)
```

### Parameters - isDerivedFrom

baseTableName  

### Return Value - isDerivedFrom

true if this table is derived from the table that is specified by the baseTableName parameter.

## Method isMap

Indicates whether the table is a map.

```xpp
public boolean isMap()
```

### Return Value - isMap

true if the table is a map; otherwise, false.

### Examples - isMap

The following example shows the retrieval of a value that indicates whether the table is a map.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(AddressMap)); 
if (dt) 
{ 
    print(strfmt("Map: %1", dt.isMap())); 
}
```

## Method isSql

Indicates whether the table is an SQL table.

```xpp
public boolean isSql()
```

### Return Value - isSql

true if the table is an SQL table; otherwise, false.

### Examples - isSql

The following example shows the retrieval of a value that indicates whether the table is an SQL table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print(strfmt("SQL table: %1", dt.isSql())); 
}
```

## Method isSystemTable

Indicates whether the table is a system table.

```xpp
public boolean isSystemTable()
```

### Return Value - isSystemTable

true if the table is a system table; otherwise, false.

### Examples - isSystemTable

The following example shows the retrieval of a value that indicates whether the table is a system table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print(strfmt("System table: %1", dt.isSystemTable())); 
}
```

## Method isTempDb

```xpp
public boolean isTempDb()
```

### Return Value - isTempDb

## Method isTmp

Indicates whether the table is a temporary table.

```xpp
public boolean isTmp()
```

### Return Value - isTmp

true if the table is a temporary table; otherwise, false.

### Examples - isTmp

The following example shows the retrieval of a value that indicates whether the table is a temporary table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(TmpWMSOrder)); 
if (dt) 
{ 
    print(strfmt("Temporary table: %1", dt.isTmp())); 
}
```

## Method isUnionAllView

```xpp
public boolean isUnionAllView()
```

### Return Value - isUnionAllView

## Method isValidTimeStateTable

```xpp
public boolean isValidTimeStateTable()
```

### Return Value - isValidTimeStateTable

## Method isView

Indicates whether the table is a view.

```xpp
public boolean isView()
```

### Return Value - isView

true if the table is a view; otherwise, false.

### Examples - isView

The following example shows the retrieval of a value that indicates whether the table is a view.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print(strfmt("View: %1", dt.isView())); 
}
```

## Method label

Returns the label text for the table.

```xpp
public str label()
```

### Return Value - label

The label text for the table; an empty string if there is no label text for the table.

### Examples - label

The following example shows the retrieval of the label text for a table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
     print(strfmt("Label: %1", dt.label())); 
}
```

## Method labelDefined

Returns the value of the label property for the table.

```xpp
public str labelDefined()
```

### Return Value - labelDefined

The value of the label property for the table; an empty string if there is no label text for the table.

## Method listPageRef

```xpp
public str listPageRef([boolean searchBaseTables])
```

### Parameters - listPageRef

searchBaseTables  

### Return Value - listPageRef

## Method makeRecord

Creates a blank record for the table.

```xpp
public Common makeRecord()
```

### Return Value - makeRecord

A Common value if the record was successfully created; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the record could not be created.

### Remarks - makeRecord

The Common value that is returned can be used in a call to the DictTable.callObject Method method.

## Method maxAccessMode

Returns the value of the MaxAccessMode property for a table, as set in the AOT.

```xpp
public AccessType maxAccessMode()
```

### Return Value - maxAccessMode

A AccessType value that represents the maximum access mode for the table.

### Examples - maxAccessMode

The following example shows the retrieval of the maximum access mode for a table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print strfmt("Maximum Access Mode: %1",dt.maxAccessMode()); 
}
```

## Method name

Retrieves the name of the table.

```xpp
public str name([DbBackend db], [boolean pseudoname])
```

### Parameters - name

db  
A Boolean value that indicates whether a pseudo name is returned; optional.

<!-- -->

pseudoname  
A Boolean value that indicates whether a pseudo name is returned; optional.

### Return Value - name

The name of the table.

### Remarks - name

If the table name is longer than 30 characters, the native name and SQL name of the table do not match.

### Examples - name

The following example shows the retrieval of the name of a table.

```xpp
DictTable dt; 
dt = new DictTable(1);  // 1 == tablenum(CustTable) 
if (dt) 
{ 
    print(strfmt("The table name is %1.", dt.name())); 
}
```

## Method objectMethod

Returns the name of an instance method that is specified by index.

```xpp
public str objectMethod(int methodNumber, [TableScope tableScope])
```

### Parameters - objectMethod

methodNumber  

<!-- -->

tableScope  

### Return Value - objectMethod

The name of the instance method that is specified by the methodNumber parameter; an empty string if the methodNumber value is not a valid instance method index.

### Examples - objectMethod

The following example shows the retrieval of the name of each instance method in a table.

```xpp
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
```

## Method objectMethodCnt

Returns the number of instance methods for the table.

```xpp
public int objectMethodCnt([TableScope tableScope])
```

### Parameters - objectMethodCnt

tableScope  

### Return Value - objectMethodCnt

The number of instance methods for the table.

### Examples - objectMethodCnt

The following example shows the retrieval of the number of instance methods for a table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print (strfmt("The table has %1 instance methods.", dt.objectMethodCnt())); 
}
```

## Method objectMethodObject

Returns an instance of the MethodInfo class for an object method that is specified by index.

```xpp
public DictMethod objectMethodObject(int methodNumber, [TableScope tableScope])
```

### Parameters - objectMethodObject

methodNumber  

<!-- -->

tableScope  

### Return Value - objectMethodObject

An instance of the MethodInfo class for the object method that is specified by the methodNumber parameter; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the instance could not be created.

### Examples - objectMethodObject

The following example shows the retrieval of the object methods for a table.

```xpp
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
```

## Method mapObject

Creates an instance of the \[T: DictTableMap\] class for a mapping that is specified by index.

```xpp
public DictTableMap mapObject(int methodNumber)
```

### Parameters - mapObject

methodNumber  

### Return Value - mapObject

A DictTableMap object for the field that is specified by the \_cnt parameter; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the object could not be created.

## Method mapCnt

Returns the count of available table mappings for the map that is specified by this DictTable instance.

```xpp
public int mapCnt()
```

### Return Value - mapCnt

The count.

## Method occEnabled

Indicates whether the optimistic concurrency mode has been enabled for a table.

```xpp
public boolean occEnabled()
```

### Return Value - occEnabled

true if the optimistic concurrency mode is enabled; otherwise, false.

### Remarks - occEnabled

When this mode is enabled, data is not locked from future modification when it is fetched from the database. Data is locked only when the actual update is performed.

### Examples - occEnabled

The following example shows a call to the occEnabled method.

```xpp
static public void Main(Args _args) 
{ 
    DictTable dt; 
    boolean enabled; 
    dt = new DictTable(tablenum(CustTable)); 
    enabled = dt.occEnabled(); 
}
```

## Method primaryIndex

Returns the ID of the primary index for the table.

```xpp
public IndexId primaryIndex([boolean asDefinedInAOT])
```

### Parameters - primaryIndex

asDefinedInAOT  
A Boolean value that indicates whether the primary index to retrieve is defined in the AOT. A value of true returns the primary index as defined in the AOT. A value of false returns the primary index as defined in the SQL table; optional.

### Return Value - primaryIndex

The ID of the primary index for the table; 0 (zero) if there is no primary index for the table.

### Examples - primaryIndex

The following example shows the retrieval of the primary index for a table.

```xpp
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
```

## Method primaryKeyField

Returns the ID of the field that is used for the primary key of the table.

```xpp
public FieldId primaryKeyField()
```

### Return Value - primaryKeyField

The ID of the field that is used for the primary key of the table; 0 (zero) if no single field serves as the primary key of the table.

### Examples - primaryKeyField

The following example shows the retrieval of the field ID of the primary key for the table.

```xpp
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
```

## Method relation

Returns the name of a relation that is specified by index.

```xpp
public str relation(int RelationNumber, [TableScope tableScope])
```

### Parameters - relation

RelationNumber  

<!-- -->

tableScope  

### Return Value - relation

The name of the relation that is specified by the RelationNumber parameter; an empty string if the RelationNumber value is not a valid relation index.

### Examples - relation

The following example shows the retrieval of the name for each relation in a table.

```xpp
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
```

## Method relationCnt

Returns the number of relations for the table.

```xpp
public int relationCnt([TableScope tableScope])
```

### Parameters - relationCnt

tableScope  

### Return Value - relationCnt

The number of relations for the table.

### Examples - relationCnt

The following example shows the retrieval of the number of relations for a table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print (strfmt("The table has %1 relations.", dt.relationCnt())); 
}
```

## Method replacementKey

```xpp
public IndexId replacementKey()
```

### Return Value - replacementKey

## Method reportRef

Returns the name of the default report for the table.

```xpp
public str reportRef()
```

### Return Value - reportRef

The name of the default report for the table; an empty string if there is no default report for the table.

### Examples - reportRef

The following shows the retrieval of the name of the default report for a table.

```xpp
DictTable dt; 
str       strReport; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    strReport = dt.reportRef(); 
    print strfmt("Default report: %1", strReport != "" ? strReport : "None specified"); 
}
```

## Method rights

Returns the access rights of the current user that is specified for the table.

```xpp
public AccessType rights([boolean ignoreContext])
```

### Parameters - rights

ignoreContext  

### Return Value - rights

The access rights of the current user that is specified for the table. The return value can be one of the values in the AccessType system enumeration.

## Method securityKeyId

Returns the ID of the security key for the table.

```xpp
public SecurityKeyId securityKeyId()
```

### Return Value - securityKeyId

The ID of the security key for the table; 0 (zero) if there is no security key for the table.

## Method singularLabel

```xpp
public str singularLabel([boolean labelTranslation])
```

### Parameters - singularLabel

labelTranslation  

### Return Value - singularLabel

## Method staticMethod

Returns the name of a static method that is specified by index.

```xpp
public str staticMethod(int methodNumber)
```

### Parameters - staticMethod

methodNumber  
The one-based index to the list of static methods for the table, in AOT order.

### Return Value - staticMethod

The name of the static method that is specified by the methodNumber parameter; an empty string if the methodNumber value is not a valid static method index.

### Examples - staticMethod

The following example shows the retrieval of the name of each static method in a table.

```xpp
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
```

## Method staticMethodCnt

Returns the number of static methods for the table.

```xpp
public int staticMethodCnt()
```

### Return Value - staticMethodCnt

The number of static methods for the table.

### Examples - staticMethodCnt

The following example shows the retrieval of the number of static methods for a table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
    print (strfmt("The table has %1 static methods.", dt. staticMethodCnt())); 
}
```

## Method staticMethodObject

Returns an instance of the MethodInfo class for a static method that is specified by index.

```xpp
public DictMethod staticMethodObject(int methodNumber)
```

### Parameters - staticMethodObject

methodNumber  
The one-based index to the static methods for the table, in AOT order.

### Return Value - staticMethodObject

An instance of the MethodInfo class for the static method that is specified by the methodNumber parameter; null, Nothing, nullptr, unit, a null reference (Nothing in Visual Basic) if the instance could not be created.

### Examples - staticMethodObject

The following example shows the retrieval of the static methods for a table.

```xpp
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
```

## Method supportInheritance

```xpp
public boolean supportInheritance()
```

### Return Value - supportInheritance

## Method tableGroup

Returns the table group for a table.

```xpp
public TableGroup tableGroup()
```

### Return Value - tableGroup

A TableGroup value that represents the table group of the table.

### Remarks - tableGroup

The return value corresponds to the TableGroup property of the table in the AOT.

### Examples - tableGroup

The following example shows the retrieval of the table group of the table.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (dt) 
{ 
   print strfmt("Table Group: %1", dt.tableGroup()); 
}
```

## Method tableType

Indicates the type of the table.

```xpp
public TableType tableType()
```

### Return Value - tableType

The error state, if there is any error state.

## Method titleField1

Returns the ID of the field that represents the titleField1 property of the table.

```xpp
public FieldId titleField1([boolean includeBaseTables], [boolean extendedFieldId])
```

### Parameters - titleField1

includeBaseTables  

<!-- -->

extendedFieldId  

### Return Value - titleField1

The ID of the field that represents the titleField1 property of the table.

### Remarks - titleField1

According to best practice guidelines, the titleField1 property represents the key field for the records in the table.

### Examples - titleField1

The following example shows the retrieval of the ID of the field that is used for the titleField1 property of the table.

```xpp
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
```

## Method titleField2

Returns the ID of the field that represents the titleField2 property of the table.

```xpp
public FieldId titleField2([boolean includeBaseTables], [boolean extendedFieldId])
```

### Parameters - titleField2

includeBaseTables  

<!-- -->

extendedFieldId  

### Return Value - titleField2

The ID of the field that represents the titleField2 property of the table.

### Remarks - titleField2

According to best practice guidelines, the titleField2 property represents the description of the records of the table.

### Examples - titleField2

The following example shows the retrieval of the ID of the field that is used for the titleField2 property of the table.

```xpp
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
```

## Method validRelationship

```xpp
public boolean validRelationship()
```

### Return Value - validRelationship

## Method visible

Determines whether the table is visible.

```xpp
public boolean visible()
```

### Return Value - visible

true if the table is visible; otherwise, false.

## Method construct

```xpp
public static DictTable construct(str tableName)
```

### Parameters - construct

tableName  

### Return Value - construct

## Method getRelationTypeFromTableName

```xpp
public static RecId getRelationTypeFromTableName(TableName tableName)
```

### Parameters - getRelationTypeFromTableName

tableName  

### Return Value - getRelationTypeFromTableName

## Method getTableNameFromRelationType

```xpp
public static TableName getTableNameFromRelationType(RecId relationType)
```

### Parameters - getTableNameFromRelationType

relationType  

### Return Value - getTableNameFromRelationType

## Method createRecord

```xpp
public static Common createRecord(str tableName)
```

### Parameters - createRecord

tableName  

### Return Value - createRecord

## Method reloadSecurity

Reloads the feature key system for the table.

```xpp
public void reloadSecurity()
```

### Examples - reloadSecurity

The following example reloads the feature key system for a table.

```xpp
dt.reloadSecurity()
```

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(TableId tableId)
```

### Parameters - new

tableId  
The ID of the table that is used to create the instance of the DictTable class.

### Examples - new

The following example shows how to create an instance of the DictTable class.

```xpp
DictTable dt; 
dt = new DictTable(tablenum(CustTable)); 
if (!dt) 
{ 
    // Take error action. 
}
```

## Method reindex

Performs a reindex of the table.

```xpp
public void reindex()
```

### Remarks - reindex

Do not use this method to reindex SQL tables; instead, use the SqlDataDictionary::tableReindex method. Additionally, the DictTable::reindex method is not supported when it is run on the client.

