---
# required metadata

title: Fetch environment metadata
description: You can fetch environment metadata through Microsoft Dynamics Lifecycle Services (LCS) via the LCS Environment API. 
author: jorichar
ms.date: 08/17/2021
ms.topic: reference
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: jorichar
ms.search.validFrom: 2021-08-32

---

# Fetch environment metadata

[!include [banner](../../../includes/banner.md)]

You can fetch environment metadata through Microsoft Dynamics Lifecycle Services (LCS) via the LCS Environment API. This API will return a paginated list that by default includes all environments within the project. The response can be filtered using the optional query string parameters.

## Permissions

### API application
One of the following permissions is required to call this API. For more information about permissions and how to select them, see the [Database Movement API Authentication](../../../database/api/dbmovement-api-authentication.md) document.

| Permission type                    | Permissions (from least privileged to most privileged) |
|------------------------------------|--------------------------------------------------------|
| Delegated (work or school account) | user\_impersonation                                    |

### LCS
Within LCS, the user used in the API OAuth authentication will need to be added to the project as either a Project Owner or Environment Administrator. The user must accept the invite to the project. 

## HTTP request

Use the following GET endpoint to fetch environment metadata.

**Fetch metadata for all environments within a project**
<!-- { "blockType": "ignored" } -->
```http
GET /environmentinfo/v1/detail/project/{projectId}/?page=1
```

**Fetch metadata for a single environment by id**
<!-- { "blockType": "ignored" } -->
```http
GET /environmentinfo/v1/detail/project/{projectId}/?environmentId={environmentId}
```

**Fetch metadata for a single environment by name**
<!-- { "blockType": "ignored" } -->
```http
GET /environmentinfo/v1/detail/project/{projectId}/?environmentName={environmentName}
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
For each environment, the following properties will be available. If a value is not available, `null` will be returned for the property.

| Property | Detail |
|----------------|---------------------------|
| EnvironmentId | LCS Environment ID. |
| EnvironmentName | Environment name. |
| ProjectId | LCS project ID the environment is contained within. |
| EnvironmentInfrastructure | The infrastructure type of the environment like SelfService, MicrosoftManaged. |
| EnvironmentType | The environment type like Production, Sandbox. |
| EnvironmentGroup | The environment group like Primary or DiasterRecovery. |
| EnvironmentProduct | The product running on the environment. |
| EnvironmentEndpointBaseUrl | The base URL of the environment. |
| DeploymentState | The most recent environment operation's state. |
| TopologyDisplayName | The product topology deployed on the environment. |
| CurrentApplicationBuildVersion | A string of the application version. |
| CurrentApplicationReleaseName | A string of the application release name. |
| CurrentPlatformReleaseName | A string of the platform version. |
| CurrentPlatformVersion | A string of the platform release name. |
| DeployedOnUTC | A UTC date time of when the environment was deployed. |
| CloudStorageLocation | The primary Azure location of the environment. |
| DisasterRecoveryLocation | The secondary Azure location of the environment. |
| DeploymentStatusDisplay | The current status of the environment. |
| CanStart | A boolean if the environment can be started. |
| CanStop | A boolean if the environment can be stopped. |

### Example response

**Successful response of project-level request**
```json
{
    "ResultPageCurrent": 1,
    "ResultHasMorePages": true,
    "Data": [
        {
            "EnvironmentId": "d15ed3a8c2c14054840b946c93915da9",
            "EnvironmentName": "ProdEnvironment1",
            "ProjectId": 112233,
            "EnvironmentInfrastructure": "MicrosoftManaged",
            "EnvironmentType": "Production",
            "EnvironmentGroup": "Primary",
            "EnvironmentProduct": "Finance and Operations",
            "EnvironmentEndpointBaseUrl": "<example>",
            "DeploymentState": "Finished",
            "TopologyDisplayName": "Finance and Operations - High Availability (10.0.20 with Platform update 44)",
            "CurrentApplicationBuildVersion": "10.0.886.48",
            "CurrentApplicationReleaseName": "10.0.20",
            "CurrentPlatformReleaseName": "Update44",
            "CurrentPlatformVersion": "7.0.6060.45",
            "DeployedOnUTC": "8/5/2021 11:00 PM",
            "CloudStorageLocation": "East US",
            "DisasterRecoveryLocation": "West US",
            "DeploymentStatusDisplay": "Deployed",
            "CanStart": false,
            "CanStop": false
        },
        {
            "EnvironmentId": "60b557b2-fefb-4690-859e-f83caf98c17e",
            "EnvironmentName": "SandboxEnvironment1",
            "ProjectId": 112233,
            "EnvironmentInfrastructure": "MicrosoftManaged",
            "EnvironmentType": "Sandbox",
            "EnvironmentGroup": "Primary",
            "EnvironmentProduct": "Finance and Operations",
            "EnvironmentEndpointBaseUrl": "<example>",
            "DeploymentState": "Finished",
            "TopologyDisplayName": "Finance and Operations - Sandbox (10.0.20 with Platform update 44)",
            "CurrentApplicationBuildVersion": "10.0.960.24",
            "CurrentApplicationReleaseName": "10.0.21",
            "CurrentPlatformReleaseName": "Update45",
            "CurrentPlatformVersion": "7.0.6129.19",
            "DeployedOnUTC": "8/5/2021 12:42 PM",
            "CloudStorageLocation": "East US",
            "DisasterRecoveryLocation": "West US",
            "DeploymentStatusDisplay": "Failed",
            "CanStart": false,
            "CanStop": true
        }
    ],
    "IsSuccess": true,
    "OperationActivityId": "216ea45d-113d-445a-a393-f67041f7aafe",
    "ErrorMessage": null,
    "VersionEOL": "9999-12-31T23:59:59.9999999"
}
```

## Rate limits

To better load balance the requests, there are rate limits on this API:

 * 6 calls for each project per 1 minute

> [!NOTE]
> Requests that exceed the limits will be rejected with a "HTTP 429 Too Many Requests" response. The **retry-after** header will indicate the number of seconds when the request can be retried.

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
