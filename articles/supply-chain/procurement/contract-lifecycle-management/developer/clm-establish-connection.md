---
title: Establish a connection from a CLM system to Supply Chain Management (preview)
description: This article describes how a third-party contract lifecycle management provider can simplify the process of establishing connections by efficiently configuring contract management parameters and initiating the connection.
author: Henrikan
ms.author: henrikan
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
<!-- KFM: Preview until 10.0.43 GA  -->

This article describes how a third-party contract lifecycle management (CLM) provider can simplify the process of establishing connections by efficiently configuring the contract management parameters in Supply Chain Management and initiating the connection. The process can be initiated from the CLM system and seamlessly transfers all the required configuration settings to the Supply Chain Management system.

<!-- KFM: Most of the examples in this topic describe GET operations. But it seems like the intro is suggesting that we use the API to set these values from the CLM side. Or am I confused? -->

## Access the data integration APIs

For information about which data integration APIs are available, how to enable change tracking, and how to authenticate with Supply Chain Management so your CLM system can access that data entities described in this article, see [Data integration APIs](clm-data-integration-apis.md).

## Available data entities

To streamline the connection process, Supply Chain Management offers built-in data entities that enable external CLM systems to automatically configure parameters and establish the connection. The following table lists the data entities.

| Entity | Target entity | Public name (OData) | Usage | Direction |
| --- | --- | --- | --- | --- |
| CLM integration service instance | `CLMIntegrationServiceInstanceEntity` | `CLMIntegrationServiceInstances` | Set up contract management parameters. | CLM -\> Supply Chain Management |
| CLM integration external navigation links | `CLMIntegrationExternalNavigationLinkEntity` | `CLMIntegrationExternalNavigationLinks` | Set up external navigation links. | CLM -\> Supply Chain Management |
| CLM integration external navigation link key-value pairs | `CLMIntegrationExternalNavigationLinkKeyValueEntity` | `CLMIntegrationExternalNavigationLinkKeyValues` | Set up external navigation link query strings. | CLM -\> Supply Chain Management |

The following diagram illustrates the integration.

:::image type="content" source="../media/establishment.png" alt-text="Integration diagram." lightbox="../media/establishment.png":::

> [!IMPORTANT]
> Your CLM system must update relevant status fields in the *CLM integration service instance* entity to reflect the **Connection status** indicator.

### The CLM integration service instance entity

The *CLM integration service instance* entity provides information about the CLM integration service instance which contains contract management parameters.

| Physical name | Property | Type | Description |
|---|---|---|---|
| `ID` (PK) | ID | Int | Parameter key (always be set to 0) |
| `InstanceName` | Connection name | String | Connection name |
| `BaseURL` | Base URL | String | Base URL |
| `ExternalNavigationBaseURL` | External navigation base URL | String | External navigation base URL |

<!--KFM: What does PK stand for?  -->

Here's an example request query for the CLM integration service instance entity:

```http
GET https://[baseURI]/data/CLMIntegrationServiceInstances
```

Here's an example response to that query:

```json
{
    "ID": 0,
    "InstanceName": "CLM instance",
    "BaseURL": "https://clm-instance.com",
    "ExternalNavigationBaseURL": "https://clm-instance.com"
}
```

### The CLM integration external navigation links entity

The *CLM integration external navigation links* entity provides information about the external navigation links.

| Physical name | Property | Type | Description |
|---|---|---|---|
| `ServiceInstanceName` | Connection name | String | Provide instance name. |
| `NavigationType` (PK) | Navigation type | Enum | Values: `ViewContract`, `EditContract`, `NewContract`, `NewContractFromPurchAgreement`, `AmendContract`. |
| `NavigationName` | Navigation name | String | Navigation name |
| `RelativeURL` | Relative URL | String | Relative URL |
| `Action` | Action | Enum | Values: `OpenInNewTab`, `OpenInExistingTab` |

Here's an example request query for the *CLM integration external navigation links* entity:

```http
GET https://[baseURI]/data/CLMIntegrationExternalNavigationLinks
```

Here's an example response to that query:

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

The *CLM integration external navigation link key-value pairs* entity provides information about the external navigation link key-value pairs.

| Physical name | Property | Type | Description |
|---|---|---|---|
| `NavigationType` (PK) | Navigation type | Enum | Values: `ViewContract`, `EditContract`, `NewContract`, `NewContractFromPurchAgreement`, `AmendContract`. |
| `KeyValueType` (PK) | Key-value type | Enum | Values: `QueryString`, `Header`. The `QueryString` is the only allowed value. |
| `Key` (PK) | Key | String | Key |
| `Value` | Value | String | Value |

<!--KFM: I'm confused by "The `QueryString` is the only allowed value". We list `Header` as a value too. What does this mean?  -->

Here's an example request query for the *CLM integration external navigation link key-value pairs* entity:

```http
GET https://[baseURI]/data/CLMIntegrationExternalNavigationLinkKeyValues
```

Here's an example response to that query:

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

- `CLMIntegrationServiceInstanceEntity.EstablishmentStatus` – Indicates whether a connection is established so the external CLM system can communicate with the Supply Chain Management. Report the connection status using one of the following values:
    - `NotStarted` – Connection establishment has't started yet.
    - `Success` – The connection is established.
    - `Error` – The connection failed to be established.
- `CLMIntegrationServiceInstanceEntity.ConfigurationStatus` – Indicates whether external configuration links have been configured. Report the configuration status using one of the following values:
    - `NotStarted` – Configuration of the external navigation links hasn't started yet.
    - `Success` – Configuration of the external navigation links has succeeded.
    - `Error` – Configuration of the external navigation links has failed.

Administrators can read this status on the **Contract management parameters** page in Supply Chain Management. Learn more in [Enable and configure CLM integration (preview)](clm-enable.md).

Here's an example request query for updating the status on the *CLM integration service instance* entity:

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
