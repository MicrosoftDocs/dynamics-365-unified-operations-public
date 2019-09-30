---
# required metadata

title: Database movement API - Reference - v1 - Create database refresh
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

# Create database refresh

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

Create a database refresh between two environments.  Note that the same validation rules apply to the API as from the LCS environment details page.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Authentication](../dbmovement-api-authentication.md).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | user_impersonation   |

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
POST /datasemovement/v1/refresh/project/{projectId}/source/{sourceEnvironmentId}/target/{targetEnvironmentId}
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
POST /datasemovement/v1/refresh/project/12345/source/5362377c-bc37-4f92-b30e-fe0c1e664cc0/target/6a90b45f-1764-4077-b924-3f4671540237
```
```json
{
    "IsSuccess": true,

    "OperationActivityId": "55eb4327-9346-4c7b-82bd-fe8ef15112c6",

    "ErrorMessage": null,

    "VersionEOL": "9999-12-31T23:59:59.9999999"

}
```