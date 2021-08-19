---
# required metadata

title: Fetch environment metadata
description: This topic explains how to fetch environment metadata through Microsoft Dynamics Lifecycle Services (LCS) via the LCS Environment API. 
author: jorichar
ms.date: 08/19/2021
ms.topic: reference
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: jorichar
ms.search.validFrom: 2021-08-32

---

# Fetch environment metadata

[!include [banner](../../../includes/banner.md)]

You can fetch environment metadata through Microsoft Dynamics Lifecycle Services (LCS) via the LCS Environment API. This API returns a paginated list that, by default, includes all environments in the project. The optional query string parameters can be used to filter the response.

## Permissions

### API application

One of the following permissions is required to call this API. For more information about permissions and how to select them, see [Database movement API - Authentication](../../../database/api/dbmovement-api-authentication.md).

| Permission type                    | Permissions (from least privileged to most privileged) |
|------------------------------------|--------------------------------------------------------|
| Delegated (work or school account) | user\_impersonation                                    |

### LCS

In LCS, the user who is used in the API OAuth authentication must be added to the project as either a project owner or an environment administrator. The user must accept the invitation to the project.

## HTTP request

Use the following GET endpoint to fetch environment metadata.

**Fetch metadata for all environments in a project**

<!-- { "blockType": "ignored" } -->
```http
GET /environmentinfo/v1/detail/project/{projectId}/?page=1
```

**Fetch metadata for a single environment by ID**

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

For each environment, the following properties are available. If no value is available for a property, **null** is returned.

| Property | Description |
|----------|-------------|
| EnvironmentId | The LCS environment ID. |
| EnvironmentName | The environment name. |
| ProjectId | The ID of the LCS project that contains the environment. |
| EnvironmentInfrastructure | The infrastructure type of the environment (for example, **SelfService** or **MicrosoftManaged**). |
| EnvironmentType | The environment type (for example, **Production** or **Sandbox**). |
| EnvironmentGroup | The environment group (for example, **Primary** or **DiasterRecovery**). |
| EnvironmentProduct | The product that is running in the environment. |
| EnvironmentEndpointBaseUrl | The base URL of the environment. |
| DeploymentState | The state of the most recent environment operation. |
| TopologyDisplayName | The product topology that is deployed in the environment. |
| CurrentApplicationBuildVersion | A string of the application version. |
| CurrentApplicationReleaseName | A string of the application release name. |
| CurrentPlatformReleaseName | A string of the platform version. |
| CurrentPlatformVersion | A string of the platform release name. |
| DeployedOnUTC | A Coordinated Universal Time (UTC) date/time value that indicates when the environment was deployed. |
| CloudStorageLocation | The primary Azure location of the environment. |
| DisasterRecoveryLocation | The secondary Azure location of the environment. |
| DeploymentStatusDisplay | The current status of the environment. |
| CanStart | A Boolean value that indicates whether the environment can be started. |
| CanStop | A Boolean value that indicates whether the environment can be stopped. |

### Example response

**Successful response for a project-level request**

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

To better load balance requests, there are rate limits on this API:

* 6 calls for each project per minute

> [!NOTE]
> Requests that exceed the limits will be rejected, and an "HTTP 429 Too Many Requests" response will be returned. The **retry-after** header will indicate the number of seconds that the request can be retried after.

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
