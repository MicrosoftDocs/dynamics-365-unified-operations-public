---
# required metadata

title: LCS API - Reference - v1 - Environment history
description: This topic provides a reference for version 1 of the LCS API.
author: jorichar
ms.date: 08/11/2021
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
ms.author: jorichar
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.0

---

# Fetch environment history

[!include [banner](../../../includes/banner.md)]

You can fetch environment history metadata through Microsoft Dynamics Lifecycle Services (LCS) via the LCS Environment API. This API will return a paginated list that includes ongoing and past operations.

## Permissions

### API Application
One of the following permissions is required to call this API. For more information about permissions and how to select them, see the [Database Movement API Authentication](../../../database/api/dbmovement-api-authentication.md) document.

| Permission type                    | Permissions (from least privileged to most privileged) |
|------------------------------------|--------------------------------------------------------|
| Delegated (work or school account) | user\_impersonation                                    |

### LCS
Within LCS, the user used in the API OAuth authentication will need to be added to the project as either a Project Owner or Environment Administrator. The user must accept the invite to the project. 

## HTTP request

Use the following GET endpoint to fetch environment history for a given environment. For regional LCS instances, replace `lcs.dynamics.com` with the appropriate LCS instance.

<!-- { "blockType": "ignored" } -->
```http
GET https://lcsapi.lcs.dynamics.com/environmentinfo/v1/history/project/{projectId}/environment/{environmentId}/?page=1
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

### HTTP
The response is always a **200 OK** response, unless you aren't correctly authenticated. Be sure to use the **IsSuccess** property to evaluate the success or failure of the action.

### Pagination
The result will include a boolean property `ResultHasMorePages` which indicates if another page of results is available. The `?page=` query string parameter can be used to specify an exact page to fetch.

### Data
For each history operation, the following properties will be available. If a value is not available, `null` will be returned for the property.

| Property | Detail |
|----------------|---------------------------|
| Name | The supplied operation history name |
| Type | The operation type |
| TypeDisplay | The operation type display string |
| StartDateTimeUtc | UTC date time of the start of the operation |
| EndDateTimeUtc | UTC date time of the end of the operation |
| Status | The status of the operation |
| ActivityId | The operation's activity id Guid |
| EnvironmentId | The environment id the operation was against |
| ProjectId | The project id the operation was against |

### Example response

**Successful response**
```json
{
    "ResultPageCurrent": 1,
    "ResultHasMorePages": false,
    "Data": [
        {
            "Name": "Finance insights",
            "Type": "InstallAddin",
            "TypeDisplay": "Install addin",
            "StartDateTimeUtc": "2021-06-03T15:10:00.0",
            "EndDateTimeUtc": "2021-06-03T15:11:00.0",
            "Status": "Completed",
            "ActivityId": "0924ecdd-1b80-40cc-8158-172785841c15",
            "EnvironmentId": "9ba7fcc3e3b941e09eccd40abde85429",
            "ProjectId": 112233
        },
        {
            "Name": "Contoso Package deployment",
            "Type": "ApplicationHotfix",
            "TypeDisplay": "Application deployable package",
            "StartDateTimeUtc": "2021-06-03T10:10:00.0",
            "EndDateTimeUtc": "2021-06-03T10:11:00.0",
            "Status": "Completed",
            "ActivityId": "34703e5c3d224d1685dbaa7f8677d237",
            "EnvironmentId": "9ba7fcc3e3b941e09eccd40abde85429",
            "ProjectId": 112233
        }
    ],
    "IsSuccess": true,
    "OperationActivityId": "47bb9956-6fae-49c1-8669-6ec0431e7ee9",
    "ErrorMessage": null,
    "VersionEOL": "9999-12-31T23:59:59.9999999"
}
```

## Rate limits

To better load balance the requests, there are rate limits on this API:

 * 6 calls for each environment per 30 seconds
 * 6 calls for each project per 1 minute

> [!NOTE]
> Requests that exceed the limits will be rejected with a "HTTP 429 Too Many Requests" response. The **retry-after** header will indicate the number of seconds when the request can be retried.

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
