---
# required metadata

title: LCS API - Reference - v1 - Download RSAT certificate
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

# Fetch environment RSAT certificate ZIP

[!include [banner](../../../includes/banner.md)]

You can fetch an environment current RSAT certificate bundle through Microsoft Dynamics Lifecycle Services (LCS) via the LCS Environment API. This API will return a Base-64 encoded ZIP and Base-64 encoded password for the private certificate password.

## Permissions

### API Application
One of the following permissions is required to call this API. For more information about permissions and how to select them, see the [Database Movement API Authentication](../../../database/api/dbmovement-api-authentication.md) document.

| Permission type                    | Permissions (from least privileged to most privileged) |
|------------------------------------|--------------------------------------------------------|
| Delegated (work or school account) | user\_impersonation                                    |

### LCS
Within LCS, the user used in the API OAuth authentication will need to be added to the project as either a Project Owner or Environment Administrator. The user must accept the invite to the project. 

## HTTP request

Use the following GET endpoint to fetch an environment's RSAT certificate ZIP. For regional LCS instances, replace `lcs.dynamics.com` with the appropriate LCS instance.

**Fetch RSAT certificate by environment**
<!-- { "blockType": "ignored" } -->
```http
GET https://lcsapi.lcs.dynamics.com/environmentinfo/v1/rsatdownload/project/{projectId}/
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

### Data


### Example response

**Successful response of project-level request**
```json
{
    "Data": {
        "CertificateZipEncoded": "<base64 encoded zip>",
        "CertificateSecretEncoded": "<base64 encoded password>",
        "ExpirationDateTimeUTC": "Thursday, June 30, 2022 8:52:13 PM",
        "Filename": "RSATCertificate_TestEnv1_20210805-100102.zip"
    },
    "IsSuccess": true,
    "OperationActivityId": "2234bff0-432d-478b-a5ac-1ccb529ee698",
    "ErrorMessage": null,
    "VersionEOL": "9999-12-31T23:59:59.9999999"
}
```

## Parsing data via Powershell

Below is an example script that communicates with the LCS API to download the RSAT certificate ZIP to the local machine. It will display the private certificate's password on the console. An access token must be provided.

```powershell
# Basic LCS API RSAT certificate zip download script
#
# This will download the RSAT certificate bundle for an environment
# to the current directory and display the private certificate's password
# in the console.
#
# The user used in the API authentication must be added to the
# project as an Environment Admin or Project Owner

# Configuration
$accessToken = "{access token string}";
$projId = {project id integer};
$envId = "{environment id GUID}"

# If using a regional LCS instance, update the base domain
$url = "https://lcsapi.lcs.dynamics.com/environmentinfo/v1/rsatdownload/project/$projId/environment/$envId"
 
$headers = @{
    "Authorization" = "Bearer $accessToken"
    "x-ms-version" = "2017-09-15"
    "Content-Type" = "application/json"
}

# Reset variable between executions
$certificateResponse = $null 

# Could add HTTP 429 handling and other HTTP code checks
$certificateResponse = Invoke-RestMethod $url -Method 'GET' -Headers $headers

if ((-not $certificateResponse.IsSuccess) -or ($certificateResponse.Data -eq $null)) {
    Write-Host $certificateResponse.ErrorMessage
    throw
}

$certificateSecret = [System.Text.Encoding]::ASCII.GetString([System.Convert]::FromBase64String($certificateResponse.Data.CertificateSecretEncoded))
$certificateZip = [System.Convert]::FromBase64String($certificateResponse.Data.CertificateZipEncoded)
$fileName = $certificateResponse.Data.Filename

# Could add unzipping in memory and install certificates to correct local certificate stores
Set-Content $fileName -Value $certificateZip -Encoding Byte

Write-Host "Certificate bundle downloaded to $fileName with private certificate password $certificateSecret"
```

## Rate limits

To better load balance the requests, there are rate limits on this API. This limiting is also shared with the LCS web interface.

 * 1 call for each environment per 1 minute

> [!NOTE]
> Requests that exceed the limits will be rejected with a "HTTP 429 Too Many Requests" response. The **retry-after** header will indicate the number of seconds when the request can be retried.

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
