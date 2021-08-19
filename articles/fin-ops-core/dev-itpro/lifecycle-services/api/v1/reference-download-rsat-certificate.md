---
# required metadata

title: Fetch an environment's RSAT certificate in a zip file
description: This topic explains how to fetch the Regression Suite Automation Tool (RSAT) certificate bundle for an environment through Microsoft Dynamics Lifecycle Services (LCS) via the LCS Environment API.
author: jorichar
ms.date: 08/19/2021
ms.topic: reference
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
# ms.search.industry: 
ms.author: jorichar
ms.search.validFrom: 2021-08-12

---

# Fetch an environment's RSAT certificate in a zip file

[!include [banner](../../../includes/banner.md)]

You can fetch the Regression Suite Automation Tool (RSAT) certificate bundle for an environment through Microsoft Dynamics Lifecycle Services (LCS) via the LCS Environment API. This API returns a Base 64–encoded zip file and a Base 64–encoded password for the private certificate password.

The full process for using the 

## Permissions

### API application

One of the following permissions is required to call this API. For more information about permissions and how to select them, see [Database movement API - Authentication](../../../database/api/dbmovement-api-authentication.md).

| Permission type                    | Permissions (from least privileged to most privileged) |
|------------------------------------|--------------------------------------------------------|
| Delegated (work or school account) | user\_impersonation                                    |

### LCS

In LCS, the user who is used in the API OAuth authentication must be added to the project as either a project owner or an environment administrator. The user must accept the invitation to the project.

## HTTP request

Use the following GET endpoint to fetch the zip file for an environment's RSAT certificate.

**Fetch the RSAT certificate by environment**

<!-- { "blockType": "ignored" } -->
```http
GET /environmentinfo/v1/rsatdownload/project/{projectId}/
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

### Data

| Property | Description |
|----------|-------------|
| CertificateZipEncoded | A zip containing the .PFX and .CER files in a Base64-encoded byte array. |
| CertificateSecretEncoded | The private certificate's private secret as a Base64-encoded string. This will change every request. |
| ExpirationDateTimeUTC | A date and time in UTC of when the certificate is not valid after. |
| Filename | The filename of the ZIP being returned. |

### Example response

**Successful response for a project-level request**

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

## Parsing data via PowerShell

The following example script communicates with the LCS API to download the zip file for the RSAT certificate to the local machine. It shows the private certificate's password in the console window. An access token must be provided.

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
$baseLCSAPI = "lcsapi.lcs.dynamics.com";

$url = "https://$baseLCSAPI/environmentinfo/v1/rsatdownload/project/$projId/environment/$envId"
 
$headers = @{
    "Authorization" = "Bearer $accessToken"
    "x-ms-version" = "2017-09-15"
    "Content-Type" = "application/json"
}

# Reset variable between executions
$certificateResponse = $null 
$shouldRetry = $false

do {
    $shouldRetry = $false

    try {
        # GET request to LCS API
        $certificateResponse = Invoke-RestMethod $url -Method 'GET' -Headers $headers
    } catch {
        # Check if this is a HTTP 429 error
        if ($_.Exception.Response.StatusCode.value__ -eq 429) {

            # Too many requests for this environment, wait and retry
            $shouldRetry = $true
            $retrySeconds = [int]$_.Exception.Response.Headers['Retry-After']
            Write-Host "Too many requests - Retrying in $retrySeconds seconds"
            Start-Sleep -Seconds $retrySeconds
        } else {
            throw
        }
    }
} while($shouldRetry)

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

To better load balance requests, there are rate limits on this API. These limits are also shared with the LCS web interface.

* 1 call for each environment per minute

> [!NOTE]
> Requests that exceed the rate limits will be rejected, and an "HTTP 429 Too Many Requests" response will be returned. The **retry-after** header will indicate the number of seconds that the request can be retried after.

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
