---
# required metadata

title: Database movement API - Reference - v1 - Start and Stop environments 
description: This topic provides a reference for version 1 (v1) of the Database Movement application programming interface (API).
author: laneswenka
manager: AnnBe
ms.date: 09/22/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
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

# Start and Stop environments

[!include [banner](../../../includes/banner.md)]

You can start and stop of environments through Lifecycle Services (LCS) via this API. Using these APIs will ensure the LCS environment status is synced with the actual environment. 
Note that the same validation rules from the details page in Microsoft Dynamics Lifecycle Services (LCS) apply to the application programming interface (API).

.[!Note]
 - Only Customer Managed and Microsoft Managed environments are supported. Self Service environments do not have the same concept of stop and start and are not supported by this API. These APIs will trigger/invoke the operation and successful response only indicates the trigger was successful.
- For **stop**, non-success will be returned if the environment is already undergoing another operation or if the environment is already stopped.
- For **start**, non-success will be returned if the environment is already undergoing another operation but will return success if the environment is already started.


## Permissions

One of the following permissions is required to call this application programming interface (API). For more information about permissions and how to select them, see [Authentication](../dbmovement-api-authentication.md).

| Permission type                    | Permissions (from least privileged to most privileged) |
|------------------------------------|--------------------------------------------------------|
| Delegated (work or school account) | user\_impersonation                                    |

## HTTP request

**Stop an environment**
<!-- { "blockType": "ignored" } -->
```http
POST /environment/v1/stop/project/{projectId}/environment/{environmentId}
```
**Start an environment**
```http
POST /environment/v1/start/project/{projectId}/environment/{environmentId}
```

## Request headers

| Header         | Value                     |
|----------------|---------------------------|
| Authorization  | Bearer {token} (required) |
| 'x-ms-version' | '2017-09-15' (required)   |
| Content-Type   | application/json          |

## Request body

Don't supply a request body for this method.

## Response

The response is always a **200 OK** response, unless you aren't correctly authenticated. Be sure to use the **IsSuccess** property to evaluate the success or failure of the action.

## Example

```http
POST /environment/v1/stop/project/{projectId}/environment/{environmentId}
```

```json
{
    "IsSuccess": true,
    "OperationActivityId": "55eb4327-9346-4c7b-82bd-fe8ef15112c6",
    "ErrorMessage": null,
    "VersionEOL": "9999-12-31T23:59:59.9999999"
}
```

