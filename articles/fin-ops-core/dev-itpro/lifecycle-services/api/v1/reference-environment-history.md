---
title: Fetch environment history
description: Learn about how to fetch environment history metadata through Microsoft Dynamics Lifecycle Services (LCS) via the LCS Environment API.
author: laneswenka
ms.author: laswenka
ms.date: 08/19/2021
ms.topic: reference
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-08-12
---

# Fetch environment history

[!include [banner](../../../includes/banner.md)]

You can fetch environment history metadata through Microsoft Dynamics Lifecycle Services (LCS) via the LCS Environment API. This API returns a paginated list that includes ongoing and past operations.

## Permissions

### API application

One of the following permissions is required to call this API. For more information about permissions and how to select them, see [Database movement API - Authentication](../../../database/api/dbmovement-api-authentication.md).

| Permission type                    | Permissions (from least privileged to most privileged) |
|------------------------------------|--------------------------------------------------------|
| Delegated (work or school account) | user\_impersonation                                    |

### LCS

In LCS, the user who is used in the API OAuth authentication must be added to the project as either a project owner or an environment administrator. The user must accept the invitation to the project.

## HTTP request

Use the following GET endpoint to fetch environment history for a given environment.

<!-- { "blockType": "ignored" } -->
```http
GET /environmentinfo/v1/history/project/{projectId}/environment/{environmentId}/?page=1
```

## Request headers

Use the following header values in the HTTP request header.

| Header         | Value                         |
|----------------|-------------------------------|
| Authorization  | **Bearer {token}** (required) |
| 'x-ms-version' | **'2017-09-15'** (required)   |
| Content-Type   | **application/json**          |

## Request body

Don't supply a request body for this method.

## Response

### HTTP

The response is always a "200 OK" response, unless you aren't correctly authenticated. Be sure to use the **IsSuccess** property to evaluate the success or failure of the action.

### Pagination

The result includes a Boolean **ResultHasMorePages** property that indicates whether another page of results is available. The **?page=** query string parameter can be used to fetch a specific page.

### Data

For each history operation, the following properties are available. If no value is available for a property, **null** is returned.

| Property | Description |
|----------|-------------|
| Name | The supplied operation history name. |
| Type | The operation type. |
| TypeDisplay | The display string for the operation type. |
| StartDateTimeUtc | The start date and time of the operation in Coordinated Universal Time (UTC). |
| EndDateTimeUtc | The end date and time of the operation in UTC. |
| Status | The status of the operation. |
| ActivityId | The globally unique identifier (GUID) for the operation's activity. |
| EnvironmentId | The ID of the environment that the operation was performed against. |
| ProjectId | The ID of the project that the operation was performed against. |

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
            "StartDateTimeUTC": "2021-06-03T15:10:00.0",
            "EndDateTimeUTC": "2021-06-03T15:11:00.0",
            "Status": "Completed",
            "ActivityId": "0924ecdd-1b80-40cc-8158-172785841c15",
            "EnvironmentId": "9ba7fcc3e3b941e09eccd40abde85429",
            "ProjectId": 112233
        },
        {
            "Name": "Contoso Package deployment",
            "Type": "ApplicationHotfix",
            "TypeDisplay": "Application deployable package",
            "StartDateTimeUTC": "2021-06-03T10:10:00.0",
            "EndDateTimeUTC": "2021-06-03T10:11:00.0",
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

* 6 calls for each environment every 30 seconds
* 6 calls for each project per minute

> [!NOTE]
> Requests that exceed the limits will be rejected, and an "HTTP 429 Too Many Requests" response will be returned. The **retry-after** header will indicate the number of seconds that the request can be retried after.

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
