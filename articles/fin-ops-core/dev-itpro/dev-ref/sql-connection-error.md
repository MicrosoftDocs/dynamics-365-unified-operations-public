---
title: SQL connection error X++ exception
description: Learn about the SQL connection error exception types in X++, including an overview of the TransientSqlConnectionError exception.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 09/27/2018
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-10-01
ms.dyn365.ops.version: Plaform update 21
---

# SQL connection error X++ exception

[!include [banner](../includes/banner.md)]

This article describes the SQL connection error exception types in X++.

## TransientSqlConnectionError X++ exception

During an X++ SQL query execution, when a transient SQL connection error occurs on the server side, a TransientSqlConnectionError X++ exception will occur. Depending on the application requirements, the application should catch and handle the exception.

This exception usually occurs during a large transaction or when the database is under a lot of processing pressure.

The TransientSqlConnectionError exception is not catchable within the transaction. The X++ transaction that encounters this exception is canceled (calling **ttsAbort**) before the exception occurs. This means that you need to use the catch block to identify the transient SQL connection error instead of a generic X++ error exception, and then retry the outermost transaction or retry application code logic in a new session. This exception allows the application to be designed for transient server failures.

If an application transaction takes a long time to process, you can use multiple incremental delays to catch the TransientSqlConnectionError exception. Retrying your application code in a new session is most likely to succeed after you have caught the exception.


### Example

```xpp
public static void LargeTransactionWrapper()
{
    try
    {
        LargeTransaction();
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


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
