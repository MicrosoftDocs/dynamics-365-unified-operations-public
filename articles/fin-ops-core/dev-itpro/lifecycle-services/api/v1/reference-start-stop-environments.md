---
# required metadata

title: Start and stop environments
description: You can start and stop environments through Microsoft Dynamics Lifecycle Services (LCS) via the LCS Environment API.
author: jorichar
ms.date: 08/17/2021
ms.topic: reference
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: jorichar
ms.search.validFrom: 2021-01-31

---

# Start and stop environments

[!include [banner](../../../includes/banner.md)]

You can start and stop environments through Microsoft Dynamics Lifecycle Services (LCS) via the LCS Environment API. Using these APIs will ensure the LCS environment status is synced with the actual environment. 

Note that the same validation rules from the details page in LCS apply to the API.

> [!NOTE]
> - Only **Customer-managed** environments are supported. Self-service environments do not have the same concept of stop and start and are not supported by this API. Microsoft-managed environments are not supported.
> - These APIs will trigger/invoke the operation. A successful response only indicates that the trigger was successful.
> - For **stop**, non-success will be returned if the environment is already undergoing another operation or if the environment is already stopped.
> - For **start**, non-success will be returned if the environment is already undergoing another operation but will return success if the environment is already started.


## Permissions

One of the following permissions is required to call this API. For more information about permissions and how to select them, see the [Database Movement API Authentication](../../../database/api/dbmovement-api-authentication.md) content.

| Permission type                    | Permissions (from least privileged to most privileged) |
|------------------------------------|--------------------------------------------------------|
| Delegated (work or school account) | user\_impersonation                                    |

## HTTP request

Use the following POST method to send an HTTP request to stop or start an environment. 

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

The response is always a **200 OK** response, unless you aren't correctly authenticated. Be sure to use the **IsSuccess** property to evaluate the success or failure of the action.

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

To better load balance the request, there are rate limits on the Start and Stop API: 

For **Start** API, the following limits will be enforced:

 * 1 call for each environment for 5 minutes
 * 30 calls for each user for 30 minutes
                
For **Stop** API, the following limits will be enforced:

 * 1 call for each environment for 5 minutes
 * 30 calls for each user for 30 minutes

> [!NOTE]
> Requests that exceed the limits will be rejected with a “HTTP 429 Too Many Requests” response. The **retry-after** header will indicate the number of seconds when the request can be retried.


[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
