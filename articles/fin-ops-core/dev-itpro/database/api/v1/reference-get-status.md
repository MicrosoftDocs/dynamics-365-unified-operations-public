---
title: Database movement API - Reference - v1 - Get status
description: Learn about a reference for version 1 (v1) of the Database Movement application programming interface (API) for getting statuses.
author: laneswenka
ms.author: laswenka
ms.topic: reference
ms.date: 09/22/2020
# ms.custom: [used by loc for topics migrated from the wiki]
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-09-30
ms.search.form: 
ms.dyn365.ops.version: 10.0.0
---

# Get status

[!include [banner](../../../includes/banner.md)]

You can get the status of an ongoing operation.

## Permissions

One of the following permissions is required to call this application programming interface (API). For more information about permissions and how to select them, see [Authentication](../dbmovement-api-authentication.md).

| Permission type                    | Permissions (from least privileged to most privileged) |
|------------------------------------|--------------------------------------------------------|
| Delegated (work or school account) | user\_impersonation                                    |

## HTTP request

<!-- { "blockType": "ignored" } -->
```http
GET /databasemovement/v1/fetchstatus/project/{projectId}/environment/{environmentId}/operationactivity/{operationactivityId}
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
GET /databasemovement/v1/fetchstatus/project/12345/environment/5362377c-bc37-4f92-b30e-fe0c1e664cc0/operationactivity/55eb4327-9346-4c7b-82bd-fe8ef15112c6
```

```json
{
    "IsSuccess": true,
    "OperationActivityId": "6a90b45f-1764-4077-b924-3f4671540237",
    "ErrorMessage": null,
    "VersionEOL": "9999-12-31T23:59:59.9999999",
    "ProjectId": 12345,
    "EnvironmentId": "5362377c-bc37-4f92-b30e-fe0c1e664cc0",
    "ActivityId": "55eb4327-9346-4c7b-82bd-fe8ef15112c6",
    "CompletionDate": null,
    "OperationStatus": "InProgress"
}
```

### OperationStatus property

| Status             | Description                                           |
|--------------------|-------------------------------------------------------|
| NotStarted         | The action hasn't yet been started.                   |
| InProgress         | The action is in progress.                            |
| Completed          | The action was successfully completed.                |
| Failed             | The action was halted.                                |
| SignedOff          | The action was successfully completed and signed off. |
| Aborted            | The action was canceled without automated cleanup.    |
| RollbackInProgress | Reversal of the action is in progress.                |
| RollbackFailed     | Reversal of the action was halted.                    |
| RollbackCompleted  | Reversal of the action was successfully completed.    |


[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
