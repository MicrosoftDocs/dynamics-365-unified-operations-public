---
# required metadata

title: Database movement API - Reference - v1 - Get Status
description: This topic provides a reference for v1 of the Database Movement API. 
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

# Get status

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

Get the status of an ongoing operation.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Authentication](../dbmovement-api-authentication.md).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | user_impersonation   |

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
GET /datasemovement/v1/fetchstatus/project/{projectId}/environment/{environmentId}/operationactivity/{operationactivityId}
```
## Request headers

| Header        | Value                      |
|:--------------|:---------------------------|
| Authorization | Bearer {token} (required)  |
| 'x-ms-version'| '2017-09-15' (required)    |
| Content-Type  | application/json           |

## Request body
Do not supply a request body for this method.

## Response
The response is always a `200 OK` unless you are not properly authenticated.  Be sure to evaluate the IsSuccess property to evaluate the success or failure of the action.

## Example
```http
GET /datasemovement/v1/fetchstatus/project/12345/environment/5362377c-bc37-4f92-b30e-fe0c1e664cc0/operationactivity/55eb4327-9346-4c7b-82bd-fe8ef15112c6
```
```json
{
    "IsSuccess": true,

    "OperationActivityId": "6a90b45f-1764-4077-b924-3f4671540237",

    "ErrorMessage": null,

    "VersionEOL": "9999-12-31T23:59:59.9999999",

    "ProjectId": "12345",

    "EnvironmentId": "5362377c-bc37-4f92-b30e-fe0c1e664cc0",

    "ActivityId": "55eb4327-9346-4c7b-82bd-fe8ef15112c6",

    "CompletionDate": null,

    "OperationStatus": "InProgress"
}
```

### OperationStatus property
| Status       | Description|
|:---------------|:----------|
|NotStarted | Action has not yet started|
|InProgress | Action is in progress|
|Completed | Action completed successfully|
|Failed | Action halted|
|SignedOff | Action completed successfully and signed off|
|Aborted | Action cancelled without automated cleanup|
|RollbackInProgress | Action reversal in progress|
|RollbackFailed | Action reversal halted|
|RollbackCompleted | Action reversal completed successfully|