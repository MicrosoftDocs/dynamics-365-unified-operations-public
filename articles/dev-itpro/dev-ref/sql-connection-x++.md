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

# SQL connection error X++ exception

[!include [banner](../includes/banner.md)]

TransientSqlConnectionError X++ exception
--------

TransientSqlConnectionError X++ exception will be thrown when a transient SQL connection error happens at the server side during a X++ SQL query execution.  It is recommened for the application to catch and handle this exception depends on the application requirements.


### Notes
1. TransientSqlConnectionError exception is not catchable within the transaction.  The X++ transaction that encounters this exception is aborted before the exception is thrown.
2. Recommendation is to use the catch block to identify transient SQL connection error instead of generic X++ error exception, retry the outermost transaction or your entire application code logic.  This exception allows application to design on transient server failures.


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
        info("Caught transient sql connection error, ttslevel=" + int2Str(appl.ttsLevel()));
        // At this point, transaction is aborted
        // Code that indicates retry is possible
    }
    finally
    {
        // Do clean up
    }
}
```
