---
title: SqlStatementExecutePermission class
description: This topic describes the SqlStatementExecutePermission class.
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

# Class SqlStatementExecutePermission

[!include [banner](../../includes/banner.md)]

```xpp
class SqlStatementExecutePermission extends CodeAccessPermission
```

Controls the ability to use SQL.

## Remarks

This class is designed to check permissions for specific APIs. For a list of all protected APIs, see Secured APIs. You must call the assert method on the same tier, usually the server tier, that the corresponding CodeAccessPermission::demand method is called on before the protected API is executed. Call a method on the server tier from one of the following:

-   A server static method �or�
-   A class instance method that is set to run on the server by using the RunOn class property

## Examples

This example performs an SQL query on the CustTable table, which runs on the server. The result of the query is stored in the \_resultSet object. The assert method is called to declare that the code can then instantiate the AsciiIo class that is used to read and write data to a file.

```xpp
server static void main(Args _args) 
{ 
    DictTable  _dictTable; 
    Connection _connection; 
    Statement  _statement; 
    str        _sql; 
    ResultSet  _resultSet; 
    SqlStatementExecutePermission _perm; 
    _dictTable = new DictTable(tableNum(CustTable)); 
    if (_dictTable != null) 
        { 
           _connection = new Connection(); 
           _sql = strfmt( "SELECT * FROM %1", _dictTable.name(DbBackend::Sql) ); 
           _perm = new SqlStatementExecutePermission(_sql); 
           // Check for permission to use the _statement. 
           _perm.assert(); 
           _statement = _connection.createStatement(); 
           _resultSet = _statement.executeQuery(_sql); 
           // End the scope of the assert call. 
           CodeAccessPermission::revertAssert(); 
        } 
}
```

## Methods

| Method                                                 | Description                                                                      |
|--------------------------------------------------------|----------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of the current permission class object.               |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission. |
| public void new(str sqlStatement)                      | Creates a new instance of the SQLStatementExecutePermission class.               |

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

true if a current permission is a subset of a specified permission; otherwise false.

### Remarks - isSubsetOf

You override this method when you derive a class from the CodeAccessPermission class. For more information, see .

## Method new

Creates a new instance of the SQLStatementExecutePermission class.

```xpp
public void new(str sqlStatement)
```

### Parameters - new

sqlStatement  
The SQL string to be executed.

### Examples - new

The following example performs an SQL query on the CustTable table, which runs on the server. The result of the query is stored in the resultSet object.

```xpp
server static void main(Args _args) 
{ 
    DictTable  dictTable; 
    Connection connection; 
    Statement  statement; 
    str        sql; 
    ResultSet  resultSet; 
    SqlStatementExecutePermission perm; 
    dictTable = new DictTable(tableNum(CustTable)); 
    if (dictTable != null) 
        { 
           connection = new Connection(); 
           sql = strfmt( "SELECT * FROM %1", dictTable.name(DbBackend::Sql) ); 
           //Instantiate the permission class 
           perm = new SqlStatementExecutePermission(sql); 
           //check for permission to use statement 
           perm.assert(); 
           statement = connection.createStatement(); 
           resultSet = statement.executeQuery(sql); 
           //end the scope of the assert call 
           CodeAccessPermission::revertAssert(); 
        } 
}
```

