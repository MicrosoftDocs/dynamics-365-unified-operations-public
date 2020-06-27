---
title: Dictionary class
description: This topic describes the Dictionary class.
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

# Class Dictionary

[!include [banner](../../includes/banner.md)]

```xpp
class Dictionary extends Object
```

The Dictionary class provides information about tables, extended data types, classes, and other items in the Application Object Tree (AOT).

## Remarks

## Examples

## Methods

| Method                                                                                                                                       | Description                                                                                                      |
|----------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| public int classCnt()                                                                                                                        | Indicates the number of classes.                                                        |
| public ClassId classCnt2Id(int cnt)                                                                                                          | Provides the ID of a specified class.                                                                            |
| public str className(ClassId classId)                                                                                                        | Provides the name of a specified class.                                                                          |
| public ClassId className2Id(str name)                                                                                                        | Provides the ID for a specified class, based on the class name.                                                  |
| public ClassId classNext(ClassId classId)                                                                                                    | Indicates the class that succeeds a specified class, based on the class IDs.                                     |
| public DictClass classObject(ClassId classId)                                                                                                | Provides information about a specified class by returning a DictClass object.                                    |
| public int configurationKeyCnt()                                                                                                             | Indicates the number of configuration keys.                                             |
| public ConfigurationKeyId configurationKeyCnt2Id(int cnt)                                                                                    | Provides the ID of a specified configuration key.                                                                |
| public str configurationKeyName(ConfigurationKeyId configurationKey)                                                                         | Provides the name of a specified configuration key.                                                              |
| public ConfigurationKeyId configurationKeyName2Id(str name)                                                                                  | Provides the ID for a specified configuration key, based on the configuration key name.                          |
| public ConfigurationKeyId configurationKeyNext(ConfigurationKeyId configurationKey)                                                          | Indicates the configuration key that succeeds a specified configuration key, based on the configuration key IDs. |
| public DictConfigurationKey configurationKeyObject(ConfigurationKeyId configurationKey)                                                      | Provides information about a specified configuration key by returning a DictConfigurationKey object.             |
| public SelectableDataArea currentCompany()                                                                                                   | Indicates the current company for which data is available in the database.                                       |
| public int enumCnt()                                                                                                                         | Indicates the number of enumeration types.                                              |
| public EnumId enumCnt2Id(int cnt)                                                                                                            | Provides the ID of a specified enumeration type.                                                                 |
| public str enumName(EnumId typeId)                                                                                                           | Provides the name for a specified enumeration.                                                                   |
| public EnumId enumName2Id(str name)                                                                                                          | Provides the ID of a specified enumeration, based on the name.                                                   |
| public EnumId enumNext(EnumId typeId)                                                                                                        | Indicates the enumeration type that succeeds a specified enumeration type, based on the enumeration type IDs.    |
| public DictEnum enumObject(EnumId typeId)                                                                                                    | Provides information about a specified enumeration by returning a DictEnum object.                               |
| public int licenseCodeCnt()                                                                                                                  | Indicates the number of license codes.                                                  |
| public LicenseCodeId licenseCodeCnt2Id(int cnt)                                                                                              | Provides the ID of a specified license code.                                                                     |
| public str licenseCodeName(LicenseCodeId licenseCode)                                                                                        | Provides the name of a specified license code.                                                                   |
| public LicenseCodeId licenseCodeName2Id(str name)                                                                                            | Provides the ID for a specified license code, based on the license code name.                                    |
| public LicenseCodeId licenseCodeNext(LicenseCodeId licenseCode)                                                                              | Indicates the license code that succeeds a specified license code, based on the license code IDs.                |
| public DictLicenseCode licenseCodeObject(LicenseCodeId licenseCode)                                                                          | Provides information about a specified license code by returning a DictLicenseCode object.                       |
| public int tableCnt()                                                                                                                        | Indicates the number of tables.                                                         |
| public TableId tableCnt2Id(int cnt)                                                                                                          | Provides the ID of a specified table.                                                                            |
| public str tableName(TableId tableId)                                                                                                        | Provides the name of a specified table.                                                                          |
| public TableId tableName2Id(str name)                                                                                                        | Provides the ID for a specified table, based on the table name.                                                  |
| public TableId tableNext(TableId tableId)                                                                                                    | Indicates the table that succeeds a specified table, based on the table IDs.                                     |
| public DictTable tableObject(TableId tableId)                                                                                                | Provides information about a specified table by returning a DictTable object.                                    |
| public boolean tableSql(TableId tableId)                                                                                                     | Indicates whether a table is a SQL table.                                                                        |
| public boolean tableSystem(TableId tableId)                                                                                                  | Indicates whether a table is a system table.                                                                     |
| public int testCode(int id, str value, str name, str serialno, str expiryDate, \[int userCount\], \[boolean verifyCert\], \[str timestamp\]) |                                                                                                                  |
| public int typeCnt()                                                                                                                         | Indicates the number of extended data types.                                            |
| public ExtendedTypeId typeCnt2Id(int cnt)                                                                                                    | Provides the ID of a specified extended data type.                                                               |
| public str typeName(ExtendedTypeId typeId)                                                                                                   | Provides the name of a specified extended data type.                                                             |
| public ExtendedTypeId typeName2Id(str name)                                                                                                  | Provides the ID for a specified extended data type, based on the extended data type name.                        |
| public ExtendedTypeId typeNext(ExtendedTypeId typeId)                                                                                        | Indicates the extended data type that succeeds a specified extended data type, based on the IDs.                 |
| public DictType typeObject(ExtendedTypeId typeId)                                                                                            | Provides information about a specified extended data type by returning a DictType object.                        |
| ::public static boolean safeMode()                                                                                                           |                                                                                                                  |
| ::public static void loginSettingsFlush()                                                                                                    | Refreshes the logon settings.                                                          |
| ::public static void dataFlush(\[TableId tableId\])                                                                                          | Refreshes the table data.                                                               |
| public void tableFlush()                                                                                                                     | Refreshes the tables.                                                                   |
| public void enumFlush()                                                                                                                      | Refreshes the enumeration types.                                                        |
| public void new()                                                                                                                            | Initializes a new instance of the Dictionary class.                                                              |
| public void classFlush()                                                                                                                     | Refreshes the classes.                                                                  |
| public void reloadSecurity(\[boolean reloadCodes\], \[boolean setSynchronizeRequired\], \[boolean flushTable\])                              | Reloads the feature key system.                                                                                  |
| public void typeFlush()                                                                                                                      | Refreshes the extended data types.                                                      |
| public void configurationKeyFlush()                                                                                                          | Refreshes the configuration keys.                                                       |
| public void licenseCodeFlush()                                                                                                               | Refreshes the license codes.                                                            |
| ::public static void aodFlush()                                                                                                              | Refreshes the .aod file.                                                                                         |

## Method classCnt

Indicates the number of classes.

```xpp
public int classCnt()
```

### Return Value - classCnt

An integer value that indicates the number of classes.

## Method classCnt2Id

Provides the ID of a specified class.

```xpp
public ClassId classCnt2Id(int cnt)
```

### Parameters - classCnt2Id

cnt  
An integer value that specifies a class, based on the order of classes.

### Return Value - classCnt2Id

A classId system data type value that indicates the class ID; 0 (zero) if you pass a cnt value that is larger than the number of classes that is returned by the Dictionary::classCnt method.

## Method className

Provides the name of a specified class.

```xpp
public str className(ClassId classId)
```

### Parameters - className

classId  
A classId system data type that indicates the class ID.

### Return Value - className

A string that indicates the class name.

### Remarks - className

Class IDs are unsigned integers.

## Method className2Id

Provides the ID for a specified class, based on the class name.

```xpp
public ClassId className2Id(str name)
```

### Parameters - className2Id

name  
A string that indicates the class name.

### Return Value - className2Id

A classId system data type value that indicates the class ID; 0 (zero) if you pass a name value for a nonexistent class.

## Method classNext

Indicates the class that succeeds a specified class, based on the class IDs.

```xpp
public ClassId classNext(ClassId classId)
```

### Parameters - classNext

classId  
A classId system data type that indicates a class ID.

### Return Value - classNext

A classId system data type value that indicates the class that succeeds the specified class.

## Method classObject

Provides information about a specified class by returning a DictClass object.

```xpp
public DictClass classObject(ClassId classId)
```

### Parameters - classObject

classId  
A classId system data type that indicates a class ID.

### Return Value - classObject

A DictClass object that contains information about the specified class.

## Method configurationKeyCnt

Indicates the number of configuration keys.

```xpp
public int configurationKeyCnt()
```

### Return Value - configurationKeyCnt

An integer value that indicates the number of configuration keys.

## Method configurationKeyCnt2Id

Provides the ID of a specified configuration key.

```xpp
public ConfigurationKeyId configurationKeyCnt2Id(int cnt)
```

### Parameters - configurationKeyCnt2Id

cnt  
An integer that specifies a configuration key, based on the order of configuration keys.

### Return Value - configurationKeyCnt2Id

A configurationKeyId system data type value that indicates a configuration key ID; 0 (zero) if you pass a cnt value that is larger than the number of configuration keys that is returned by the Dictionary::configurationKeyCnt method.

## Method configurationKeyName

Provides the name of a specified configuration key.

```xpp
public str configurationKeyName(ConfigurationKeyId configurationKey)
```

### Parameters - configurationKeyName

configurationKey  
A configurationKeyId system data type that indicates a configuration key ID.

### Return Value - configurationKeyName

A string that indicates the name of the configuration key.

## Method configurationKeyName2Id

Provides the ID for a specified configuration key, based on the configuration key name.

```xpp
public ConfigurationKeyId configurationKeyName2Id(str name)
```

### Parameters - configurationKeyName2Id

name  
A string that indicates a configuration key name.

### Return Value - configurationKeyName2Id

A configurationKeyId system data type value that indicates the configuration key ID; 0 (zero) if you pass a name value for a nonexistent configuration key.

## Method configurationKeyNext

Indicates the configuration key that succeeds a specified configuration key, based on the configuration key IDs.

```xpp
public ConfigurationKeyId configurationKeyNext(ConfigurationKeyId configurationKey)
```

### Parameters - configurationKeyNext

configurationKey  
A configurationKeyId system data type that indicates a configuration key ID.

### Return Value - configurationKeyNext

A configurationKeyId system data type value for the configuration key that succeeds the specified configuration key.

## Method configurationKeyObject

Provides information about a specified configuration key by returning a DictConfigurationKey object.

```xpp
public DictConfigurationKey configurationKeyObject(ConfigurationKeyId configurationKey)
```

### Parameters - configurationKeyObject

configurationKey  
A configurationKeyId system data type that indicates a configuration key ID.

### Return Value - configurationKeyObject

A DictConfigurationKey object that contains information about the specified configuration key.

## Method currentCompany

Indicates the current company for which data is available in the database.

```xpp
public SelectableDataArea currentCompany()
```

### Return Value - currentCompany

A selectableDataArea system data type value that indicates the current company.

## Method enumCnt

Indicates the number of enumeration types.

```xpp
public int enumCnt()
```

### Return Value - enumCnt

An integer that indicates the number of enumeration types.

## Method enumCnt2Id

Provides the ID of a specified enumeration type.

```xpp
public EnumId enumCnt2Id(int cnt)
```

### Parameters - enumCnt2Id

cnt  
An integer that specifies an enumeration type, based on the order of enumeration types.

### Return Value - enumCnt2Id

An enumId system data type value that indicates the enumeration type ID; 0 (zero) if you pass a cnt value that is larger than the number of classes that is returned by the Dictionary::enumCnt method.

## Method enumName

Provides the name for a specified enumeration.

```xpp
public str enumName(EnumId typeId)
```

### Parameters - enumName

typeId  
An enumId system data type for an enumeration.

### Return Value - enumName

A string that indicates the name of the enumeration.

## Method enumName2Id

Provides the ID of a specified enumeration, based on the name.

```xpp
public EnumId enumName2Id(str name)
```

### Parameters - enumName2Id

name  
A string that indicates the name of an enumeration.

### Return Value - enumName2Id

An enumId system data type value that indicates the ID of the enumeration.

## Method enumNext

Indicates the enumeration type that succeeds a specified enumeration type, based on the enumeration type IDs.

```xpp
public EnumId enumNext(EnumId typeId)
```

### Parameters - enumNext

typeId  
An enumId system data type that indicates an enumeration ID.

### Return Value - enumNext

An enumId system data type value for the enumeration that succeeds the specified enumeration.

## Method enumObject

Provides information about a specified enumeration by returning a DictEnum object.

```xpp
public DictEnum enumObject(EnumId typeId)
```

### Parameters - enumObject

typeId  
An enumId system data type that indicates an enumeration ID.

### Return Value - enumObject

A DictEnum object that contains information about the specified enumeration.

## Method licenseCodeCnt

Indicates the number of license codes.

```xpp
public int licenseCodeCnt()
```

### Return Value - licenseCodeCnt

An integer that indicates the number of license codes.

## Method licenseCodeCnt2Id

Provides the ID of a specified license code.

```xpp
public LicenseCodeId licenseCodeCnt2Id(int cnt)
```

### Parameters - licenseCodeCnt2Id

cnt  
An integer that specifies a license code, based on the order of license codes.

### Return Value - licenseCodeCnt2Id

A licenseCodeId system data type value that indicates the license code ID; 0 (zero) if you pass a cnt value that is larger than the number of license codes that is returned by the Dictionary::licenseCodeCnt method.

## Method licenseCodeName

Provides the name of a specified license code.

```xpp
public str licenseCodeName(LicenseCodeId licenseCode)
```

### Parameters - licenseCodeName

licenseCode  
A licenseCodeId system data type that indicates the license code ID.

### Return Value - licenseCodeName

A string that indicates the license code name.

## Method licenseCodeName2Id

Provides the ID for a specified license code, based on the license code name.

```xpp
public LicenseCodeId licenseCodeName2Id(str name)
```

### Parameters - licenseCodeName2Id

name  
A string that indicates the license code name.

### Return Value - licenseCodeName2Id

A licenseCodeId system data type value that indicates the license code ID; 0 (zero) if you pass a name value for a nonexistent license code.

## Method licenseCodeNext

Indicates the license code that succeeds a specified license code, based on the license code IDs.

```xpp
public LicenseCodeId licenseCodeNext(LicenseCodeId licenseCode)
```

### Parameters - licenseCodeNext

licenseCode  
A licenseCodeId system data type that indicates a license code ID.

### Return Value - licenseCodeNext

A licenseCodeId system data type value for the license code that succeeds the specified license code.

## Method licenseCodeObject

Provides information about a specified license code by returning a DictLicenseCode object.

```xpp
public DictLicenseCode licenseCodeObject(LicenseCodeId licenseCode)
```

### Parameters - licenseCodeObject

licenseCode  
A licenseCodeId system data that indicates a license code ID.

### Return Value - licenseCodeObject

A DictLicenseCode object that contains information about the specified license code.

## Method tableCnt

Indicates the number of tables.

```xpp
public int tableCnt()
```

### Return Value - tableCnt

An integer that indicates the number of tables.

## Method tableCnt2Id

Provides the ID of a specified table.

```xpp
public TableId tableCnt2Id(int cnt)
```

### Parameters - tableCnt2Id

cnt  
An integer that specifies a table, based on the order of tables.

### Return Value - tableCnt2Id

A tableId system data type value that indicates the table ID; 0 (zero) if you pass a cnt value that is larger than the number of tables that is returned by the Dictionary::tableCnt method.

## Method tableName

Provides the name of a specified table.

```xpp
public str tableName(TableId tableId)
```

### Parameters - tableName

tableId  
A tableId system data type that indicates the table ID.

### Return Value - tableName

A string that indicates the table name; UNKNOWN if you pass a tableId value that does not exist.

### Remarks - tableName

The method returns UNKNOWN if you pass a tableId value that does not exist.

## Method tableName2Id

Provides the ID for a specified table, based on the table name.

```xpp
public TableId tableName2Id(str name)
```

### Parameters - tableName2Id

name  
A string that indicates the table name.

### Return Value - tableName2Id

A tableId system data type value that indicates the table ID; 0 (zero) if you pass a name value for a nonexistent table.

## Method tableNext

Indicates the table that succeeds a specified table, based on the table IDs.

```xpp
public TableId tableNext(TableId tableId)
```

### Parameters - tableNext

tableId  
A tableId system data type that indicates a table ID.

### Return Value - tableNext

A tableId system data type value for the table that succeeds the specified table.

## Method tableObject

Provides information about a specified table by returning a DictTable object.

```xpp
public DictTable tableObject(TableId tableId)
```

### Parameters - tableObject

tableId  
A tableId system data type that indicates a table ID.

### Return Value - tableObject

A DictTable object that contains information about the specified table.

## Method tableSql

Indicates whether a table is a SQL table.

```xpp
public boolean tableSql(TableId tableId)
```

### Parameters - tableSql

tableId  
A tableId system data type that indicates the table ID.

### Return Value - tableSql

true if the table is a SQL table; otherwise, false.

## Method tableSystem

Indicates whether a table is a system table.

```xpp
public boolean tableSystem(TableId tableId)
```

### Parameters - tableSystem

tableId  
A tableId system data type that indicates a table ID.

### Return Value - tableSystem

true if the table is a system table; otherwise, false.

### Remarks - tableSystem

You can pass a table name to this method instead of a table ID by using the tableNum intrinsic function. For more information, see Intrinsic Functions.

## Method testCode

```xpp
public int testCode(int id, str value, str name, str serialno, str expiryDate, [int userCount], [boolean verifyCert], [str timestamp])
```

### Parameters - testCode

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

### Return Value - testCode

## Method typeCnt

Indicates the number of extended data types.

```xpp
public int typeCnt()
```

### Return Value - typeCnt

An integer that indicates the number of extended data types.

## Method typeCnt2Id

Provides the ID of a specified extended data type.

```xpp
public ExtendedTypeId typeCnt2Id(int cnt)
```

### Parameters - typeCnt2Id

cnt  
An integer that specifies an extended data type, based on the order of extended data types.

### Return Value - typeCnt2Id

An extendedTypeId system data type value that indicates the ID of the extended data type; 0 (zero) if you pass a cnt value that is larger than the number of extended data types that is returned by the Dictionary::typeCnt method.

## Method typeName

Provides the name of a specified extended data type.

```xpp
public str typeName(ExtendedTypeId typeId)
```

### Parameters - typeName

typeId  
An extendedTypeId system data type that indicates the ID of an extended data type.

### Return Value - typeName

A string that indicates the name of the extended data type.

## Method typeName2Id

Provides the ID for a specified extended data type, based on the extended data type name.

```xpp
public ExtendedTypeId typeName2Id(str name)
```

### Parameters - typeName2Id

name  
A string that indicates the name of the extended data type.

### Return Value - typeName2Id

An extendedTypeId system data type value that indicates the ID of the extended data type; 0 (zero) if you pass a name value for a nonexistent extended data type.

## Method typeNext

Indicates the extended data type that succeeds a specified extended data type, based on the IDs.

```xpp
public ExtendedTypeId typeNext(ExtendedTypeId typeId)
```

### Parameters - typeNext

typeId  
An extendedTypeId system data type that indicates the ID for an extended data type.

### Return Value - typeNext

An extendedTypeId system data type value for the extended data type that succeeds the specified extended data type.

## Method typeObject

Provides information about a specified extended data type by returning a DictType object.

```xpp
public DictType typeObject(ExtendedTypeId typeId)
```

### Parameters - typeObject

typeId  
An extendedTypeId system data type that indicates the ID for an extended data type.

### Return Value - typeObject

A DictType object that contains information about the specified extended data type.

## Method safeMode

```xpp
public static boolean safeMode()
```

### Return Value - safeMode

## Method loginSettingsFlush

Refreshes the logon settings.

```xpp
public static void loginSettingsFlush()
```

## Method dataFlush

Refreshes the table data.

```xpp
public static void dataFlush([TableId tableId])
```

### Parameters - dataFlush

tableId  
A tableId system data type that indicates a single table or all tables. The default value is ALL.

### Remarks - dataFlush

By default, this method refreshes data in all tables.

## Method tableFlush

Refreshes the tables.

```xpp
public void tableFlush()
```

## Method enumFlush

Refreshes the enumeration types.

```xpp
public void enumFlush()
```

## Method new

Initializes a new instance of the Dictionary class.

```xpp
public void new()
```

## Method classFlush

Refreshes the classes.

```xpp
public void classFlush()
```

## Method reloadSecurity

Reloads the feature key system.

```xpp
public void reloadSecurity([boolean reloadCodes], [boolean setSynchronizeRequired], [boolean flushTable])
```

### Parameters - reloadSecurity

reloadCodes  

<!-- -->

setSynchronizeRequired  

<!-- -->

flushTable  

### Remarks - reloadSecurity

The default value for the \_reloadCodes parameter is false. The default value for the \_setSynchronizeRequired parameter is true.

## Method typeFlush

Refreshes the extended data types.

```xpp
public void typeFlush()
```

## Method configurationKeyFlush

Refreshes the configuration keys.

```xpp
public void configurationKeyFlush()
```

## Method licenseCodeFlush

Refreshes the license codes.

```xpp
public void licenseCodeFlush()
```

## Method aodFlush

Refreshes the .aod file.

```xpp
public static void aodFlush()
```

