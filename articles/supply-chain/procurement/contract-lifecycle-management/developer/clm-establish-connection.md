---
title: Establish a connection from a CLM system to Supply Chain Management (preview)
description: Learn how a third-party contract lifecycle management (CLM) provider can simplify the process of establishing connections by efficiently configuring contract management parameters and initiating the connection.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Establish a connection from a CLM system to Supply Chain Management (preview)

[!include [banner](../../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.43 GA -->

This article explains how a third-party contract lifecycle management (CLM) provider can simplify the process of establishing connections by efficiently configuring the contract management parameters in Microsoft Dynamics 365 Supply Chain Management and initiating the connection. The process can be initiated from the CLM system. It seamlessly transfers all the required configuration settings to the Supply Chain Management system.

Most of the code examples in this article show how to *fetch* configuration information. However, a CLM provider can also use the same APIs to *post* configuration settings. Therefore, the provider can remotely configure the connection for their Supply Chain Management customers.

## Access the data integration APIs

Learn which data integration APIs are available in [Data integration APIs](clm-data-integration-apis.md). There, you can also learn how to enable change tracking, and how to authenticate with Supply Chain Management so that your CLM system can access the data entities that are described in this article.

## Available data entities

To streamline the connection process, Supply Chain Management offers built-in data entities that enable external CLM systems to automatically configure parameters and establish the connection. The following table describes the available data entities.

| Entity | Target entity | Public name (OData) | Purpose | Direction |
|---|---|---|---|---|
| CLM integration service instance | `CLMIntegrationServiceInstanceEntity` | `CLMIntegrationServiceInstances` | Set up contract management parameters. | CLM &rarr; Supply Chain Management |
| CLM integration external navigation links | `CLMIntegrationExternalNavigationLinkEntity` | `CLMIntegrationExternalNavigationLinks` | Set up external navigation links. | CLM &rarr; Supply Chain Management |
| CLM integration external navigation link key-value pairs | `CLMIntegrationExternalNavigationLinkKeyValueEntity` | `CLMIntegrationExternalNavigationLinkKeyValues` | Set up query strings for external navigation links. | CLM &rarr; Supply Chain Management |

The following illustration shows the integration.

:::image type="content" source="../media/establishment.png" alt-text="Diagram that shows the integration." lightbox="../media/establishment.png":::

> [!IMPORTANT]
> Your CLM system must update the relevant status fields in the *CLM integration service instance* entity so that they reflect the **Connection status** indicator.

### CLM integration service instance entity

The *CLM integration service instance* entity provides information about the instance of the CLM integration service that contains contract management parameters.

| Physical name | Property | Type | Description |
|---|---|---|---|
| `ID` (entity key) | ID | Int | The parameter key. The value should always be set to `0`. |
| `InstanceName` | Connection name | String | The connection name. |
| `BaseURL` | Base URL | String | The base URL. |
| `ExternalNavigationBaseURL` | External navigation base URL | String | The external navigation base URL. |

The following example shows a request query for the *CLM integration service instance* entity.

```http
GET https://[baseURI]/data/CLMIntegrationServiceInstances
```

The following example shows a response to the preceding query.

```json
{
    "ID": 0,
    "InstanceName": "CLM instance",
    "BaseURL": "https://clm-instance.com",
    "ExternalNavigationBaseURL": "https://clm-instance.com"
}
```

### The CLM integration external navigation links entity

The *CLM integration external navigation links* entity provides information about external navigation links.

| Physical name | Property | Type | Description |
|---|---|---|---|
| `ServiceInstanceName` | Connection name | String | The instance name. |
| `NavigationType` (entity key) | Navigation type | Enum | The navigation type. The possible values are `ViewContract`, `EditContract`, `NewContract`, `NewContractFromPurchAgreement`, and `AmendContract`. |
| `NavigationName` | Navigation name | String | The navigation name. |
| `RelativeURL` | Relative URL | String | The relative URL. |
| `Action` | Action | Enum | The action that is performed. The possible values are `OpenInNewTab` and `OpenInExistingTab`. |

The following example shows a request query for the *CLM integration external navigation links* entity.

```http
GET https://[baseURI]/data/CLMIntegrationExternalNavigationLinks
```

The following example shows a response to the preceding query.

```json
{
    "ServiceInstanceName": "CLM instance",
    "NavigationType": "ViewContract",
    "NavigationName": "View contract",
    "RelativeURL": "/view",
    "Action": "OpenInNewTab"
}
```

### The CLM integration external navigation link key-value pairs entity

The *CLM integration external navigation link key-value pairs* entity provides information about the key-value pairs for external navigation links.

| Physical name | Property | Type | Description |
|---|---|---|---|
| `NavigationType` (entity key) | Navigation type | Enum | The navigation type. The possible values are `ViewContract`, `EditContract`, `NewContract`, `NewContractFromPurchAgreement`, and `AmendContract`. |
| `KeyValueType` (entity key) | Key-value type | Enum | The key-value type. `QueryString` is the only allowed value. (The other possible value, `Header`, isn't supported.) |
| `Key` (entity key) | Key | String | The key. |
| `Value` | Value | String | The value. |

The following example shows a request query for the *CLM integration external navigation link key-value pairs* entity.

```http
GET https://[baseURI]/data/CLMIntegrationExternalNavigationLinkKeyValues
```

The following example shows a response to the preceding query.

```json
{
    "NavigationType": "ViewContract",
    "KeyValueType": "QueryString",
    "Key": "id",
    "Value": "%CLMIntegrationContractTable.ExternalContractId%"
}
```

## Update the connection status

To clearly reflect the connection status, the CLM system must use the *CLM integration external navigation links* entity to update the following two statuses:

- `CLMIntegrationServiceInstanceEntity.EstablishmentStatus` – This status indicates whether a connection was established, so that the external CLM system can communicate with Supply Chain Management. The following values are used to report the connection status:

    - `NotStarted` – Establishment of a connection hasn't yet begun.
    - `Success` – A connection was successfully established.
    - `Error` – Establishment of a connection failed.

- `CLMIntegrationServiceInstanceEntity.ConfigurationStatus` – This status indicates whether external navigation links were configured. The following values are used to report the configuration status:

    - `NotStarted` – Configuration of external navigation links hasn't yet begun.
    - `Success` – External navigation links were successfully configured.
    - `Error` – Configuration of external navigation links failed.

Administrators can read status information on the **Contract management parameters** page in Supply Chain Management. Learn more in [Enable and configure CLM integration](clm-enable.md).

The following example shows a request query to update the status on the *CLM integration service instance* entity.

```http
PATCH https://[baseURI]/data/CLMIntegrationServiceInstances(ID=0)
```

```json
{
    "EstablishmentStatus": "Success",
    "ConfigurationStatus": "Error"
}
```

## Related information

- [Data integration APIs](clm-data-integration-apis.md)
