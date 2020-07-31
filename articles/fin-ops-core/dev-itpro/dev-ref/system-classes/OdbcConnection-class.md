---
title: OdbcConnection class
description: This topic describes the OdbcConnection class.
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

# Class OdbcConnection

[!include [banner](../../includes/banner.md)]

```xpp
class OdbcConnection extends Connection
```

The OdbcConnection class establishes a database connection by using ODBC (Open Database Connectivity).

## Remarks

In the context of an OdbcConnection instance, SQL statements are run, and results are returned. If a connection to the ODBC data source cannot be established, an exception is thrown, and the reason is posted in the Infolog. This class works only if the correct ODBC drivers have been installed and configured in ODBC Manager in Control Panel.

## Examples

## Methods

| Method                               | Description                                                                                              |
|--------------------------------------|----------------------------------------------------------------------------------------------------------|
| public void new(LoginProperty Login) | Establishes a connection to a data source, based on logon properties such as the user name and password. |

## Method new

Establishes a connection to a data source, based on logon properties such as the user name and password.

```xpp
public void new(LoginProperty Login)
```

### Parameters - new

Login  
A LoginProperty class instance that contains the user name, password, data source name, database, and so on.

