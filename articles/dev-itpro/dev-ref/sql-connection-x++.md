---
# required metadata

title: SQL connection error X++ exception
description: This topic describes the SQL connection error exception types in X++.
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

## TransientSqlConnectionError X++ exception
When a transient SQL connection error happens on the server side during an X++ SQL query execution, a TransientSqlConnectionError X++ exception will occur. Depending on the application requirements, the application should catch and handle the exception.

> [!NOTE]
> The TransientSqlConnectionError exception is not catchable within the transaction. The X++ transaction that encounters this exception is aborted before the exception occurs. Use the catch block to identify the transient SQL connection error instead of a generic X++ error exception, and then retry the outermost transaction or your entire application code logic. This exception allows the application to design on transient server failures.


### Example
```
public static void LongTransactionWrapper()
{
    try
    {
        LongTransaction();
    }
    catch (Exception::TransientSqlConnectionError)
    {
        info("Caught transient SQL connection error, ttslevel=" + int2Str(appl.ttsLevel()));
        // At this point, transaction is canceled
        // Code that indicates retry is possible
    }
    finally
    {
        // Do clean up
    }
}
```
