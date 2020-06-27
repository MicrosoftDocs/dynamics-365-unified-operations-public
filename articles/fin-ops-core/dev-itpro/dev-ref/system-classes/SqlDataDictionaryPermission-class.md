---
title: SqlDataDictionaryPermission class
description: This topic describes the SqlDataDictionaryPermission class.
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

# Class SqlDataDictionaryPermission

[!include [banner](../../includes/banner.md)]

```xpp
class SqlDataDictionaryPermission extends CodeAccessPermission
```

The SqlDataDictionaryPermission class controls the ability to access the methods on the and is designed to check permissions for specific APIs. For a list of all protected APIs, see Secured APIs.

## Remarks

You must call the assert method on the same tier, usually the server tier, that the corresponding CodeAccessPermission::demand method is called on before the protected API is executed. Call a method on the server tier from one of the following:

-   A server static method
-   A class instance method that is set to run on the server by using the RunOn class property.

## Examples

The following example deletes data from the xRefNames table. The assert method is called to declare that the code can then instantiate the AsciiIo class that is used to read and write data to a file.

```xpp
{ 
    DictTable dictTable = new DictTable(tablenum(xRefNames)); 
    str sqlTableName; 
    SqlDataDictionary sqlTable; 
    if (dictTable && dictTable.enabled()) 
    { 
        sqlTableName = dictTable.name(DbBackend::Sql); 
        sqlTable = new SqlDataDictionary(); 
        // Try to truncate only if the table does exist 
        // in the SQL database. 
        if (sqlTable.tableExist(sqlTableName)) 
        { 
            new SqlDataDictionaryPermission( 
                methodstr(SqlDataDictionary, tableTruncate)).assert(); 
            sqlTable.tableTruncate(tablenum(xRefNames)); 
            CodeAccessPermission::revertAssert(); 
        } 
    } 
}
```

## Methods

| Method                                                 | Description                                                                      |
|--------------------------------------------------------|----------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of the current permission class object.               |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission. |
| public void new(IdentifierName methodName)             | Creates a new instance of the SQLDataDictionaryPermission class.                 |

## Method copy

Creates and returns a copy of the current permission class object.

```xpp
public CodeAccessPermission copy()
```

### Return Value - copy

A copy of the current permission object.

### Remarks - copy

You override this method when you derive a class from the CodeAccessPermission class. For more information, see .

## Method isSubsetOf

Determines whether a current permission is a subset of the specified permission.

```xpp
public boolean isSubsetOf(CodeAccessPermission target)
```

### Parameters - isSubsetOf

target  
A CodeAccessPermission class object.

### Return Value - isSubsetOf

true if a current permission is a subset of a specified permission; otherwise, false.

### Remarks - isSubsetOf

You override this method when you derive a class from the CodeAccessPermission class. For more information, see .

## Method new

Creates a new instance of the SQLDataDictionaryPermission class.

```xpp
public void new(IdentifierName methodName)
```

### Parameters - new

methodName  
The string that represents the name of the method to be called.

### Examples - new

The following code example deletes the data in the xRefNames table.

```xpp
server static void main(Args _args) 
{ 
    DictTable dictTable = new DictTable(tablenum(xRefNames)); 
    str sqlTableName; 
    SqlDataDictionary sqlTable; 
    if (dictTable && dictTable.enabled()) 
    { 
        sqlTableName = dictTable.name(DbBackend::Sql); 
        sqlTable = new SqlDataDictionary(); 
        // Only try to truncate if the table does exist 
        // in the SQL database 
        if (sqlTable.tableExist(sqlTableName)) 
        { 
            new SqlDataDictionaryPermission( 
                methodstr(SqlDataDictionary, tableTruncate)).assert(); 
            sqlTable.tableTruncate(tablenum(xRefNames)); 
            CodeAccessPermission::revertAssert(); 
        } 
    } 
}
```

