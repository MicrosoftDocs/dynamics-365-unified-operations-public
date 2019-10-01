---
# required metadata

title: Database movement API - Throttling
description: This topic provides an overview of throttling for the Database Movement API. 
author: laneswenka
manager: AnnBe
ms.date: 09/30/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
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
[!include [banner](../../includes/preview-banner.md)]

This topic provides an overview of throttling for the Database Movement API. 

## Rate limits
To maintain the reliability of the service and to reduce costs, the Database Movement API will have throttling enabled.  This will safeguard against malicious and excessive use of the RESTful endpoints.  Database Movement operations are some of the most time consuming and CPU-intesnive tasks that can be executed from Dynamics Lifeycle Services, and we may change these limits in the future.

### Current limits
Database Movement API currently has a global call limit of **3 executions per 24 hour timeframe** for all actions which trigger a new operation in LCS.  This includes database refresh.

If you exceed this limitation, you will be unable to start a new operation and will receive an error similar to the following:

```json
{
    "IsSuccess": false,

    "OperationActivityId": "55eb4327-9346-4c7b-82bd-fe8ef15112c6",

    "ErrorMessage": "Maximum allowed API operations are 3 from 2019-09-30T04:01:01.9999999",

    "VersionEOL": "9999-12-31T23:59:59.9999999"

}
```
