---
# required metadata

title: Database movement API - Throttling
description: This topic provides an overview of throttling for the Database Movement application programming interface (API).
author: laneswenka
ms.date: 02/20/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.0

---

# Throttling

[!include [banner](../../includes/banner.md)]

This topic provides an overview of throttling for the Database Movement application programming interface (API).

## Rate limits

To help maintain the reliability of the service and reduce costs, throttling will be turned on for the Database Movement API. Throttling helps protect against malicious and excessive use of the RESTful endpoints. Database movement operations are some of the most time-consuming and CPU-intensive tasks that can be run from Microsoft Dynamics Lifecycle Services (LCS), and Microsoft might change the current call limits later.

### Current limits

Currently, the Database Movement API has a global call limit of **three executions per 24-hour timeframe** for all actions that trigger a new operation in LCS. These operations include database refresh operations.

If you exceed the limit, you won't be able to start a new operation and will receive an error that resembles the following example.

```json
{
    "IsSuccess": false,
    "OperationActivityId": "55eb4327-9346-4c7b-82bd-fe8ef15112c6",
    "ErrorMessage": "Maximum allowed API operations are 3 from 2019-09-30T04:01:01.9999999",
    "VersionEOL": "9999-12-31T23:59:59.9999999"
}
```


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]