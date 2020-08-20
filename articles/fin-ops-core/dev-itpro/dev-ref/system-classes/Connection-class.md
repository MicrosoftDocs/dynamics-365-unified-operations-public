---
title: Connection class
description: This topic describes the Connection class.
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

# Class Connection

[!include [banner](../../includes/banner.md)]

```xpp
class Connection extends Object
```

The Connection class establishes a current database session that you can use to execute SQL statements and return results.

## Remarks

The following classes extend the Connection class:

-   OdbcConnection
-   OciConnection
-   UserConnection

## Examples

In the following example, the createStatement method initializes the Statement object. The Statement.executeQuery method executes an SQL statement and then stores the retrieved data in the ResultSet object.

```xpp
server static void main(Args args) 
{ 
    Connection con = new Connection(); 
    Statement stmt = con.createStatement(); 
    ResultSet r; 
    str sql; 
    SqlStatementExecutePermission perm; 
```

```xpp
    sql = strfmt('SELECT VALUE FROM SQLSYSTEMVARIABLES'); 
```

```xpp
    // Set code access permission to help protect the use of 
    // Statement.executeUpdate. 
    perm = new SqlStatementExecutePermission(sql); 
    perm.assert(); 
```

```xpp
    try 
    { 
        r = stmt.executeQuery(sql); 
        while (r.next()) 
        { 
            print r.getString(1); 
            pause; 
        } 
    } 
    catch (exception::Error) 
    { 
        print "An error occurred in the query."; 
        pause; 
    } 
    // Code access permission scope ends here. 
    CodeAccessPermission::revertAssert(); 
}
```

## Methods

| Method                                                                                                           | Description                                                                                                                                                                             |
|------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public Statement createStatement(\[ResultSetType resultSetType\], \[ResultSetConcurrency resultSetConcurrency\]) | Creates a Statement object that is used to execute an SQL statement.                                                                                                                    |
| public int odbcGetInfoInt(int InfoId)                                                                            | Provides an interface to the SQLGetInfo Open Database Connectivity (ODBC) function to retrieve information about the ODBC driver and data source that are associated with a connection. |
| public int odbcGetInfoLong(int InfoId)                                                                           | Provides an interface to the SQLGetInfo ODBC function to retrieve information about the ODBC driver and data source that are associated with a connection.                              |
| public str odbcGetInfoStr(int InfoId)                                                                            | Provides an interface to the SQLGetInfo ODBC function to retrieve information, in string format, about the ODBC driver and data source that are associated with a connection.           |
| public str toString()                                                                                            | Converts the Connection object to a string.                                                                                                                                             |
| public int ttsLevel()                                                                                            | Returns the number for the last call to the ttsbegin method that is used to begin a transaction.                                                                                        |
| public boolean isInTransactionScope()                                                                            |                                                                                                                                                                                         |
| public void finalize()                                                                                           |                                                                                                                                                                                         |
| public void transactionScopeAbort()                                                                              |                                                                                                                                                                                         |
| public void ttsNotifyCommit()                                                                                    | Is called when the ttscommit method is called.                                                                                                                                          |
| public void transactionScopeBegin()                                                                              |                                                                                                                                                                                         |
| public void transactionScopeCommit()                                                                             |                                                                                                                                                                                         |
| public void ttsNotifyBegin()                                                                                     |                                                                                                                                                                                         |
| public void ttsbegin()                                                                                           | Begins a transaction.                                                                                                                                                                   |
| public void ttsabort()                                                                                           | Discards changes that are associated with a transaction and rolls the database back to the original state.                                                                              |
| public void new()                                                                                                | Initializes a new instance of the Connection class.                                                                                                                                     |
| public void ttsNotifyAbort()                                                                                     | Is called when an exception is thrown.                                                                                                                                                  |
| public void ttscommit()                                                                                          | Commits the changes that are associated with a transaction to the database.                                                                                                             |

## Method createStatement

Creates a Statement object that is used to execute an SQL statement.

```xpp
public Statement createStatement([ResultSetType resultSetType], [ResultSetConcurrency resultSetConcurrency])
```

### Parameters - createStatement

resultSetType  
A ResultSetConcurrency enumeration that specifies ReadOnly by default.

<!-- -->

resultSetConcurrency  
A ResultSetConcurrency enumeration that specifies ReadOnly by default.

### Return Value - createStatement

A data type value that is a new Statement object.

### Remarks - createStatement

There is risk of an SQL injection threat when you use the createStatement method to create an SQL statement and then allow a user to control input to the statement. For information, see [SQL Injection](https://go.microsoft.com/fwlink/?LinkId=114986). You can use Query Elements in the AOT, views, and X++ Select statements as safer alternatives to executing SQL statements.

## Method odbcGetInfoInt

Provides an interface to the SQLGetInfo Open Database Connectivity (ODBC) function to retrieve information about the ODBC driver and data source that are associated with a connection.

```xpp
public int odbcGetInfoInt(int InfoId)
```

### Parameters - odbcGetInfoInt

InfoId  
An integer that specifies an ID for the requested information according to the ODBC standard.

### Return Value - odbcGetInfoInt

An integer value for the information that is retrieved.

### Examples - odbcGetInfoInt

In the following example, the odbcGetInfoInt method returns an integer value for the maximum length of the column name.

```xpp
void getConnection() 
{ 
    Connection con; 
    Statement stmt; 
    int info; 
```

```xpp
    #define.SQL_MAX_COLUMN_NAME_LEN(30) 
    con = new Connection(); 
```

```xpp
    try 
    { 
        info = con.odbcGetInfoInt(#SQL_MAX_COLUMN_NAME_LEN); 
```

```xpp
        print info; 
        pause; 
     } 
```

```xpp
    catch(exception::Error) 
    { 
        print "An error occurred."; 
```

```xpp
    } 
```

```xpp
}
```

## Method odbcGetInfoLong

Provides an interface to the SQLGetInfo ODBC function to retrieve information about the ODBC driver and data source that are associated with a connection.

```xpp
public int odbcGetInfoLong(int InfoId)
```

### Parameters - odbcGetInfoLong

InfoId  
An Integer data type that specifies an ID for the requested information, according to the ODBC standard.

### Return Value - odbcGetInfoLong

An Integer data type value for the information that is retrieved.

### Remarks - odbcGetInfoLong

This method retrieves a 32-bit integer and returns it as an integer.

### Examples - odbcGetInfoLong

In the following example, the odbcGetInfoLong method returns an integer for the maximum row size.

```xpp
void getConnection() 
{ 
    Connection con; 
    Statement stmt; 
    int info; 
```

```xpp
    #define.SQL_MAX_ROW_SIZE(104) 
    con = new Connection(); 
```

```xpp
    try 
    { 
        info = con.odbcGetInfoLong(#SQL_MAX_ROW_SIZE); 
```

```xpp
        print info; 
        pause; 
     } 
```

```xpp
    catch(exception::Error) 
    { 
        print "An error occurred."; 
```

```xpp
    } 
```

```xpp
}
```

## Method odbcGetInfoStr

Provides an interface to the SQLGetInfo ODBC function to retrieve information, in string format, about the ODBC driver and data source that are associated with a connection.

```xpp
public str odbcGetInfoStr(int InfoId)
```

### Parameters - odbcGetInfoStr

InfoId  
An Integer data type that specifies an ID for the requested information, according to the ODBC standard.

### Return Value - odbcGetInfoStr

A String data type value for the information that is retrieved.

### Examples - odbcGetInfoStr

In the following example, the odbcGetInfoStr method returns the name of the database management system.

```xpp
void getConnection() 
{ 
    Connection con; 
    str info; 
```

```xpp
    #define.SQL_DBMS_NAME(17) 
    con = new Connection(); 
```

```xpp
    try 
    { 
        info = con.odbcGetInfoStr(#SQL_DBMS_NAME); 
```

```xpp
        print info; 
        pause; 
     } 
```

```xpp
    catch(exception::Error) 
    { 
        print "An error occurred."; 
    } 
}
```

## Method toString

Converts the Connection object to a string.

```xpp
public str toString()
```

### Return Value - toString

A string value for the Connection object.

## Method ttsLevel

Returns the number for the last call to the ttsbegin method that is used to begin a transaction.

```xpp
public int ttsLevel()
```

### Return Value - ttsLevel

An integer value that indicates the number for the last call to the ttsbegin method. For example, if the ttsLevel method is called after the third call to the ttsbegin method, the return value is 3.

## Method isInTransactionScope

```xpp
public boolean isInTransactionScope()
```

### Return Value - isInTransactionScope

## Method finalize

```xpp
public void finalize()
```

## Method transactionScopeAbort

```xpp
public void transactionScopeAbort()
```

## Method ttsNotifyCommit

Is called when the ttscommit method is called.

```xpp
public void ttsNotifyCommit()
```

## Method transactionScopeBegin

```xpp
public void transactionScopeBegin()
```

## Method transactionScopeCommit

```xpp
public void transactionScopeCommit()
```

## Method ttsNotifyBegin

```xpp
public void ttsNotifyBegin()
```

## Method ttsbegin

Begins a transaction.

```xpp
public void ttsbegin()
```

## Method ttsabort

Discards changes that are associated with a transaction and rolls the database back to the original state.

```xpp
public void ttsabort()
```

## Method new

Initializes a new instance of the Connection class.

```xpp
public void new()
```

## Method ttsNotifyAbort

Is called when an exception is thrown.

```xpp
public void ttsNotifyAbort()
```

## Method ttscommit

Commits the changes that are associated with a transaction to the database.

```xpp
public void ttscommit()
```

