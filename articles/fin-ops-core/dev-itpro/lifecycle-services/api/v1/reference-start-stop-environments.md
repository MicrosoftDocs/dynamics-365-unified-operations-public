---
title: Start and stop environments
description: Learn about how you can start and stop environments through Microsoft Dynamics Lifecycle Services (LCS) via the LCS Environment API.
author: laneswenka
ms.author: laswenka
ms.date: 03/06/2026
ms.topic: reference
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-01-31
---

# Start and stop environments

[!include [banner](../../../includes/banner.md)]
[!include [LCS freeze](../../../../../includes/lcs-freeze-banner.md)]

You can start and stop environments through Microsoft Dynamics Lifecycle Services (LCS) by using the LCS Environment API. By using these APIs, you ensure that the LCS environment status stays in sync with the actual environment. 

> [!NOTE]
> The same validation rules that apply to the details page in LCS also apply to the API.

> [!NOTE]
> - Only **Customer-managed** environments are supported. Self-service environments don't have the same concept of stop and start, so they're not supported by this API. Microsoft-managed environments aren't supported.
> - These APIs trigger the operation. A successful response only indicates that the trigger was successful.
> - For **stop**, the API returns an error if the environment is already undergoing another operation or if the environment is already stopped.
> - For **start**, the API returns an error if the environment is already undergoing another operation but returns success if the environment is already started.


## Permissions

You need one of the following permissions to call this API. For more information about permissions and how to select them, see [Database Movement API Authentication](../../../database/api/dbmovement-api-authentication.md).

| Permission type                    | Permissions (from least privileged to most privileged) |
|------------------------------------|--------------------------------------------------------|
| Delegated (work or school account) | user\_impersonation                                    |

## HTTP request

Use the following POST method to send an HTTP request that stops or starts an environment. 

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

Use the following header value in the HTTP request header. 

| Header         | Value                     |
|----------------|---------------------------|
| Authorization  | Bearer {token} (required) |
| 'x-ms-version' | '2017-09-15' (required)   |
| Content-Type   | application/json          |

## Request body

Don't supply a request body for this method.

## Response

The response is always a **200 OK** response, unless you're incorrectly authenticated. Use the **IsSuccess** property to evaluate the success or failure of the action.

## Example

**Request to stop an environment**
```http
POST /environment/v1/stop/project/{projectId}/environment/{environmentId}
```

**Successful response**
```json
{
    "IsSuccess": true,
    "OperationActivityId": "55eb4327-9346-4c7b-82bd-fe8ef15112c6",
    "ErrorMessage": null,
    "VersionEOL": "9999-12-31T23:59:59.9999999"
}
```
## Rate limits

To better load balance the request, the Start and Stop APIs have rate limits: 

For the **Start** API, the following limits apply:

 * 1 call for each environment every 5 minutes
 * 30 calls for each user every 30 minutes
                
For the **Stop** API, the following limits apply:

 * 1 call for each environment every 5 minutes
 * 30 calls for each user every 30 minutes

> [!NOTE]
> The API rejects requests that exceed these limits and returns a `HTTP 429 Too Many Requests` response. The **retry-after** header shows the number of seconds before you can retry the request.


[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
