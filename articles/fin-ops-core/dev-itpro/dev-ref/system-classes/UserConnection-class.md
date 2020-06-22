---
title: UserConnection class
description: This topic describes the UserConnection class.
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

# Class UserConnection

[!include [banner](../../includes/banner.md)]

```xpp
class UserConnection extends Connection
```

The UserConnection class represents an auxiliary connection to the SQL database, based on the same logon properties as the main connection.

## Remarks

SQL statements are executed, and results are returned in the context of a UserConnection class. The UserConnection class can be used to obtain a separate transaction scope.

Note: Userconnection.finalize() needs to be called in the finally block to prevent user connection leak.  Number of open user connections is limited on the server, when it reaches the limit, no more connections can be opened, which can leads to business logic failures

## Examples

```xpp
static void example()  
{ 
    UserConnection Con;
    try
    {
        Statement Stmt; 
        Str sql; 
        ResultSet R; 
        SqlStatementExecutePermission perm; 
        Con = new UserConnection(); 
        sql = 'SELECT VALUE FROM SQLSYSTEMVARIABLES'; 
        Stmt = Con.createStatement(); 
        perm = new SqlStatementExecutePermission(sql); 
        // Check for permission to use the statement. 
        perm.assert(); 
        R = Stmt.executeQuery(sql); 
        while ( R.next() ) 
        { 
            print R.getString(1); 
        } 
    }
    finally
    {
        con.finalize();
    }
 }
```

## Methods

| Method                                                | Description                                         |
|-------------------------------------------------------|-----------------------------------------------------|
| public void new(\[boolean generateNewTransactionID\]) | Initializes a new instance of the Connection class. |

## Method new

Initializes a new instance of the Connection class.

```xpp
public void new([boolean generateNewTransactionID])
```

### Parameters - new

generateNewTransactionID  

