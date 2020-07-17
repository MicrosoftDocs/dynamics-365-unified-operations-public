---
title: SqlSystem class
description: This topic describes the SqlSystem class.
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

# Class SqlSystem

[!include [banner](../../includes/banner.md)]

```xpp
class SqlSystem extends Object
```

The SqlSystem class holds information about the active SQL system, typically login information.

## Remarks

## Examples

## Methods

| Method                                                                                                                                   | Description                                                                                             |
|------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| public LoginProperty createLoginProperty()                                                                                               | Creates the login property to the  database.                                       |
| public DatabaseId databaseId()                                                                                                           | Returns the  ID for the database vendor used as the SQL database backend.          |
| public str databaseName()                                                                                                                | Returns the name of the database vendor used as the SQL database backend.                               |
| public boolean dbRequestedUnicodeEnabled()                                                                                               | Retrieves the value that indicates if Unicode is supported in the database.                             |
| public str filenameDeadlocks(str Userid)                                                                                                 | Retrieves the name of the user specific deadlocks trace logfile.                                        |
| public str filenameQuerytimelimit(str Userid)                                                                                            | Retrieves the name of the user specific querytime limit logfile.                                        |
| public str filenameSqlTrace(str Userid)                                                                                                  | Retrieves the filename of the SQL trace log file for specific user.                                     |
| public str filenameWarnings(str Userid)                                                                                                  | Retrieves the name of the user specific warnings log file.                                              |
| public str logfileName(\[boolean fromCommandline\])                                                                                      | Retrieves the name of the standard  SQL error log file.                            |
| public str loginConnectString()                                                                                                          | Retrieves the full ODBC connection string.                                                              |
| public str loginDatabase()                                                                                                               | Retrieves the name of the database currently connected to.                                              |
| public str loginDSN()                                                                                                                    | Retrieves the open database connectivity (ODBC) data source name (DSN) used to connect to the database. |
| public str loginName()                                                                                                                   | Retrieves the user name that is used to log-in to the database.                                         |
| public str loginServer()                                                                                                                 | Retrieves the name of the database server currently connected to.                                       |
| public str monocaseFmt(\[TableId tableId\], \[FieldId fieldId\], \[boolean includingFieldName\], \[boolean considerSystemVariables\])    | Retrieves the format string that is used for casting the string to one case (e.g. "NLS\_LOWER(%1)").    |
| public str sqlLiteral(AnyType data, \[boolean forWhereClause\], \[boolean likeOperand\], \[boolean rightJustify\], \[int stringLength\]) | Formats the input AX datatype to correct SQL type.                                                      |
| ::public static boolean clusteredIndexes()                                                                                               |                                                                                                         |
| ::public static str databaseBackendDesc()                                                                                                |                                                                                                         |
| ::public static DatabaseId databaseBackendId()                                                                                           |                                                                                                         |
| ::public static str databaseBackendName()                                                                                                |                                                                                                         |
| ::public static DatabaseCLI databaseCallLevelInterface()                                                                                 |                                                                                                         |
| ::public static int databaseHints(\[int new\_hint\_value\])                                                                              |                                                                                                         |
| ::public static boolean functionalIndexes()                                                                                              |                                                                                                         |
| ::public static str modelDatabaseBackendName()                                                                                           | Retrieves the name of the model database AOS currently connected to.                                    |
| ::public static str managedConnectionString()                                                                                            |                                                                                                         |
| public void new()                                                                                                                        | Initializes a new instance of the SqlSystem class.                                                      |
| public void logfileWrite(str Text)                                                                                                       | Writes a text string into the standard  SQL error logfile.                         |

## Method createLoginProperty

Creates the login property to the  database.

```xpp
public LoginProperty createLoginProperty()
```

### Return Value - createLoginProperty

The login property that was created.

## Method databaseId

Returns the  ID for the database vendor used as the SQL database backend.

```xpp
public DatabaseId databaseId()
```

### Return Value - databaseId

The  ID for the database vendor used as the SQL database backend.

### Remarks - databaseId

If the database vendor cannot be determined for any reason, the enumeration DbBackend::UNKNOWN is returned.

## Method databaseName

Returns the name of the database vendor used as the SQL database backend.

```xpp
public str databaseName()
```

### Return Value - databaseName

The name of the database vendor used as the SQL database backend.

## Method dbRequestedUnicodeEnabled

Retrieves the value that indicates if Unicode is supported in the database.

```xpp
public boolean dbRequestedUnicodeEnabled()
```

### Return Value - dbRequestedUnicodeEnabled

The value that indicates if Unicode is supported in the database.

## Method filenameDeadlocks

Retrieves the name of the user specific deadlocks trace logfile.

```xpp
public str filenameDeadlocks(str Userid)
```

### Parameters - filenameDeadlocks

Userid  

### Return Value - filenameDeadlocks

The name of the user specific to deadlocks trace log file.

## Method filenameQuerytimelimit

Retrieves the name of the user specific querytime limit logfile.

```xpp
public str filenameQuerytimelimit(str Userid)
```

### Parameters - filenameQuerytimelimit

Userid  

### Return Value - filenameQuerytimelimit

The name of the user specific querytime limit logfile.

## Method filenameSqlTrace

Retrieves the filename of the SQL trace log file for specific user.

```xpp
public str filenameSqlTrace(str Userid)
```

### Parameters - filenameSqlTrace

Userid  
The User Id.

### Return Value - filenameSqlTrace

The filename of SQL trace log.

## Method filenameWarnings

Retrieves the name of the user specific warnings log file.

```xpp
public str filenameWarnings(str Userid)
```

### Parameters - filenameWarnings

Userid  
The identifier of interested user.

### Return Value - filenameWarnings

The name of the user specific warnings log file.

## Method logfileName

Retrieves the name of the standard  SQL error log file.

```xpp
public str logfileName([boolean fromCommandline])
```

### Parameters - logfileName

fromCommandline  
A boolean value. Passing a non-zero value as parameter makes the call return the logfile name passed on the command line; optional.

### Return Value - logfileName

The file name of the standard  SQL error log file.

### Remarks - logfileName

In version 2.11 or higher, an empty string is returned (for backward compatibility). Use the filenameSqlError method to retrieve the log file name.

## Method loginConnectString

Retrieves the full ODBC connection string.

```xpp
public str loginConnectString()
```

### Return Value - loginConnectString

The full ODBC connection string.

## Method loginDatabase

Retrieves the name of the database currently connected to.

```xpp
public str loginDatabase()
```

### Return Value - loginDatabase

The name of the database currently connected to.

### Examples - loginDatabase

```xpp
{ 
    SqlSystem SqlSystem = new SqlSystem(); 
    print SqlSystem.loginDatabase(); 
}
```

## Method loginDSN

Retrieves the open database connectivity (ODBC) data source name (DSN) used to connect to the database.

```xpp
public str loginDSN()
```

### Return Value - loginDSN

The name of the ODBC data source name that is used for connecting to the database.

### Remarks - loginDSN

The default DSN is "BMSDSN".

### Examples - loginDSN

```xpp
{ 
    SqlSystem SqlSystem = new SqlSystem(); 
    print SqlSystem.loginDSN(); 
}
```

## Method loginName

Retrieves the user name that is used to log-in to the database.

```xpp
public str loginName()
```

### Return Value - loginName

The user name that is used to log-in to the database.

### Examples - loginName

```xpp
{ 
    SqlSystem SqlSystem = new SqlSystem(); 
    print SqlSystem.loginName(); 
}
```

## Method loginServer

Retrieves the name of the database server currently connected to.

```xpp
public str loginServer()
```

### Return Value - loginServer

The name of the database currently connected to.

### Remarks - loginServer

An empty string is returned if the database does not support a server concept.

### Examples - loginServer

```xpp
{ 
    SqlSystem SqlSystem = new SqlSystem(); 
    print SqlSystem.loginServer(); 
}
```

## Method monocaseFmt

Retrieves the format string that is used for casting the string to one case (e.g. "NLS\_LOWER(%1)").

```xpp
public str monocaseFmt([TableId tableId], [FieldId fieldId], [boolean includingFieldName], [boolean considerSystemVariables])
```

### Parameters - monocaseFmt

tableId  

<!-- -->

fieldId  

<!-- -->

includingFieldName  

<!-- -->

considerSystemVariables  

### Return Value - monocaseFmt

The format string that is used for casting the string to one case.

### Remarks - monocaseFmt

Finance and Operations application style for placeholder(s) is used (i.e. "%1").

## Method sqlLiteral

Formats the input AX datatype to correct SQL type.

```xpp
public str sqlLiteral(AnyType data, [boolean forWhereClause], [boolean likeOperand], [boolean rightJustify], [int stringLength])
```

### Parameters - sqlLiteral

data  
The length of the string. By default equals zero.

<!-- -->

forWhereClause  
The length of the string. By default equals zero.

<!-- -->

likeOperand  
The length of the string. By default equals zero.

<!-- -->

rightJustify  
The length of the string. By default equals zero.

<!-- -->

stringLength  
The length of the string. By default equals zero.

### Return Value - sqlLiteral

The formatted SQL type string.

## Method clusteredIndexes

```xpp
public static boolean clusteredIndexes()
```

### Return Value - clusteredIndexes

## Method databaseBackendDesc

```xpp
public static str databaseBackendDesc()
```

### Return Value - databaseBackendDesc

## Method databaseBackendId

```xpp
public static DatabaseId databaseBackendId()
```

### Return Value - databaseBackendId

## Method databaseBackendName

```xpp
public static str databaseBackendName()
```

### Return Value - databaseBackendName

## Method databaseCallLevelInterface

```xpp
public static DatabaseCLI databaseCallLevelInterface()
```

### Return Value - databaseCallLevelInterface

## Method databaseHints

```xpp
public static int databaseHints([int new_hint_value])
```

### Parameters - databaseHints

new\_hint\_value  

### Return Value - databaseHints

## Method functionalIndexes

```xpp
public static boolean functionalIndexes()
```

### Return Value - functionalIndexes

## Method modelDatabaseBackendName

Retrieves the name of the model database AOS currently connected to.

```xpp
public static str modelDatabaseBackendName()
```

### Return Value - modelDatabaseBackendName

The name of the model database currently connected to.

## Method managedConnectionString

```xpp
public static str managedConnectionString()
```

### Return Value - managedConnectionString

## Method new

Initializes a new instance of the SqlSystem class.

```xpp
public void new()
```

## Method logfileWrite

Writes a text string into the standard  SQL error logfile.

```xpp
public void logfileWrite(str Text)
```

### Parameters - logfileWrite

Text  
The text (for example, a bookmark) to write to the logfile.

### Remarks - logfileWrite

Following an error situation of any kind (which is logged in the logfile), you may want to insert a personal bookmark that explains the current scenario.

### Examples - logfileWrite

```xpp
static void myExample(Args _args) 
{ 
    SqlSystem SqlSystem; 
    SqlSystem = new SqlSystem(); 
    SqlSystem.logfileWrite("Recheck the returned data."); 
}
```

