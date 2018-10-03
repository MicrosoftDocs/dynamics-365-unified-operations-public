---
# required metadata

title: SQL connection error X++ exception
description: This topic describes the SQL connection error exception type(s) in X++.
author: yiqju
manager: AnnBe
ms.date: 09/27/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 150373
ms.assetid: f06da12e-911c-442c-97fd-280cbc970061
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2018-10-01
ms.dyn365.ops.version: Plaform update 21

---

# SQL connection errors and X++

[!include [banner](../includes/banner.md)]

TransientSqlConnectionError X++ exception
--------

TransientSqlConnectionError X++ exception will be thrown when a transient SQL connection error happens at the server side during a X++ SQL query execution.  It is recommened for the application to catch and handle this exception by performing necessary retry of the entire outermost transaction.

### Notes
1. TransientSqlConnectionError exception is not catchable within the transaction.  The X++ transaction that encounters this exception is aborted before the exception is being thrown.

## Example
```
public static void Foo()
{
    try
    {
        FooHelper::LongTransaction();
    }
    catch (Exception::TransientSqlConnectionError)
    {
        info("Caught sql connection error transient, ttslevel=" + int2Str(appl.ttsLevel()));
        // Indicate retry is possible
    }
    finally
    {
        // Do clean up
    }
}
```
