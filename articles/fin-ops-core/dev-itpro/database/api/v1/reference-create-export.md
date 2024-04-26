---
title: Database movement API - Reference - v1 - Create a database export
description: Learn a reference for version 1 (v1) of the Database Movement application programming interface (API) for creating database exports.
author: laneswenka
ms.author: laswenka
ms.topic: reference
ms.date: 09/30/2020
# ms.custom: [used by loc for topics migrated from the wiki]
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2020-03-31
ms.search.form: 
ms.dyn365.ops.version: 10.0.0
---

# Create a database export

[!include [banner](../../../includes/banner.md)]

You can create a database export from a sandbox environment to the project's asset library. Note that the same validation rules from the details page in Microsoft Dynamics Lifecycle Services (LCS) apply to the application programming interface (API).

## Permissions

One of the following permissions is required to call this API. For more information about permissions and how to select them, see [Authentication](../dbmovement-api-authentication.md).

| Permission type                    | Permissions (from least privileged to most privileged) |
|------------------------------------|--------------------------------------------------------|
| Delegated (work or school account) | user\_impersonation                                    |

## HTTP request

<!-- { "blockType": "ignored" } -->
```http
POST /databasemovement/v1/export/project/{projectId}/environment/{environmentId}/backupName/{backupName}
```

## Request headers

| Header         | Value                     |
|----------------|---------------------------|
| Authorization  | Bearer {token} (required) |
| Content-Type   | application/json          |

## Request body

Don't supply a request body for this method.

## Response

The response is always a **200 OK** response, unless you aren't correctly authenticated. Be sure to use the **IsSuccess** property to evaluate the success or failure of the action.

## Example

```http
POST /databasemovement/v1/export/project/12345/environment/5362377c-bc37-4f92-b30e-fe0c1e664cc0/backupName/TestBackupViaAPI
```

```json
{
    "IsSuccess": true,
    "OperationActivityId": "55eb4327-9346-4c7b-82bd-fe8ef15112c6",
    "ErrorMessage": null,
    "VersionEOL": "9999-12-31T23:59:59.9999999"
}
```


[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
