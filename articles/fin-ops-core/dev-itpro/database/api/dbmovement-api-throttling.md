---
title: Database movement API - Throttling
description: Learn about an overview of throttling for the Database Movement application programming interface (API) about throttling.
author: laneswenka
ms.author: laswenka
ms.topic: article
ms.date: 02/23/2024
# ms.custom: [used by loc for topics migrated from the wiki]
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-09-30
ms.search.form:
ms.dyn365.ops.version: 10.0.0
---

# Throttling

[!include [banner](../../includes/banner.md)]

This article provides an overview of throttling for the Database Movement application programming interface (API).

## Rate limits

To help maintain the reliability of the service and reduce costs, excessive calls to the Database Movement API are being throttled. Throttling helps protect against malicious and excessive use of the RESTful endpoints. Database movement operations are some of the most time-consuming and CPU-intensive tasks that can be run from Lifecycle Services. Therefore, database movement operations are throttled.

### Current limits

Currently, the Database Movement API has a global call limit of **three executions per 24-hour timeframe per environment** for all actions that trigger a new operation. These operations include database refresh operations.

Calls to the API that exceed the limit are presented with the following error message:

```json
{
    "IsSuccess": false,
    "OperationActivityId": "55eb4327-9346-4c7b-82bd-fe8ef15112c6",
    "ErrorMessage": "Maximum allowed API operations are 3 from 2019-09-30T04:01:01.9999999",
    "VersionEOL": "9999-12-31T23:59:59.9999999"
}
```

### Frequently asked questions

The following are frequently asked questions, and related answers regarding throttling limits for the Lifecycle Services APIs.

#### Which start time is used by the throttling, the start time of the database operation or the end time?
The start time of the database operation is used for the throttling logic. If you have three database operations started in the last 24 hours, then the fourth is blocked until sufficient time elapses.

#### How can I monitor this throttling limit?
You may review the activity on an environment in the **History** view in Lifecycle Services, or using the Environment History API. 

#### If the limit is reached via API, are manual operations still possible via Lifecycle Services and if yes how many?
Only API operations are throttled. You can perform as many manual operations as time allows in Lifecycle Services. Keep in mind that manual operations are included in throttling limits for service level protection.

#### Is the throttling a maximum of three operations for the entire Lifecycle Services project or customer tenant? Or, is it per environment?
The throttling limit is per environment (three requests per environment per 24 hours).

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
