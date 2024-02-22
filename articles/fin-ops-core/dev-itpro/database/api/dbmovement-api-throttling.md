---
# required metadata

title: Database movement API - Throttling
description: This article provides an overview of throttling for the Database Movement application programming interface (API).
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

This article provides an overview of throttling for the Database Movement application programming interface (API).

## Rate limits

To help maintain the reliability of the service and reduce costs, excessive calls to the Database Movement API are being throttled. Throttling helps protect against malicious and excessive use of the RESTful endpoints. Database movement operations are some of the most time-consuming and CPU-intensive tasks that can be run from Lifecycle Services (LCS) which is why they are being throttled.

### Current limits

Currently, the Database Movement API has a global call limit of **three executions per 24-hour timeframe per environment** for all actions that trigger a new operation. These operations include database refresh operations.

If you exceed the limit, you won't be able to start a new operation and will be presented with an error similar to following example.

```json
{
    "IsSuccess": false,
    "OperationActivityId": "55eb4327-9346-4c7b-82bd-fe8ef15112c6",
    "ErrorMessage": "Maximum allowed API operations are 3 from 2019-09-30T04:01:01.9999999",
    "VersionEOL": "9999-12-31T23:59:59.9999999"
}
```
### Frequently asked questions
The following are frequently asked questions, and related answers when it comes to throttling limits on the Lifecycle Services APIs.

**Question**: Which start time is used by the throttling, the beginning of the database operation or the end?
**Answer**:  The start time of the database operation is used for the throttling logic. If you have three database operations started in the last 24 hours, then the fourth is blocked until sufficient time has passed.

**Question**:  How can I monitor this throttling limit?
**Answer**:  You may review the activity on an environment in the history view within Lifecycle Services or using the Environment History API. 

**Question**:  If the limit is reached via API, are manual operations still possible via Lifecycle Services and if yes how many?
**Answer**: Only API operations are throttled, you can perform as many manual operations as time allows in Lifecycle Services.  Keep in mind that manual operations will be included in throttling limits for service level protection.

**Question**:  Is the throttling a maximum of three operations for the entire LCS project or customer tenant?  Or is it per environment?
**Answer**:  The throttling limit is per environment (3 requests per environment per 24 hours).

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]