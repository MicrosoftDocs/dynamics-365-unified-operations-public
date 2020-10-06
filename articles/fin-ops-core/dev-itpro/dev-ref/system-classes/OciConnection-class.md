---
title: OciConnection class
description: This topic describes the OciConnection class.
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

# Class OciConnection

[!include [banner](../../includes/banner.md)]

```xpp
class OciConnection extends Connection
```

The OciConnection class establishes a database connection that uses Oci (Oracle Call Interface).

## Remarks

In the context of an OciConnection instance, SQL statements are run, and results are returned. If the connection cannot be established based on the information that is specified for the LoginProperty instance, an exception is thrown, and the reason is posted in the Infolog. This class can be used only when Oracle client software is installed.

## Examples

## Methods

| Method                               | Description                                                                                                   |
|--------------------------------------|---------------------------------------------------------------------------------------------------------------|
| public void new(LoginProperty Login) | Establishes a connection to an Oracle database, based on logon properties such as the user name and password. |

## Method new

Establishes a connection to an Oracle database, based on logon properties such as the user name and password.

```xpp
public void new(LoginProperty Login)
```

### Parameters - new

Login  
A LoginProperty class instance that contains the user name, password, data source name, database, and so on.

