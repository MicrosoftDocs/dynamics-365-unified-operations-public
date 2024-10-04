---
title: Prepare a CLM system to connect to Supply Chain Management (preview)
description: This article describes how to prepare a third-party contract lifecycle management (CLM) system to connect with Supply Chain Management and confirm its configuration settings and connection status.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: XXXX
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Prepare a CLM system to connect to Supply Chain Management (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.43 GA  -->

This article describes how to prepare a third-party contract lifecycle management (CLM) system to connect with Supply Chain Management and confirm its configuration settings and connection status.

## Available data entities

To streamline the connection process, Supply Chain Management offers built-in data entities that enable external CLM systems to automatically configure parameters and establish the connection. The following table lists the data entities.

| Entity | Target entity | Public name (OData) | Usage | Direction |
| --- | --- | --- | --- | --- |
| CLM integration service instance | CLMIntegrationServiceInstanceEntity | CLMIntegrationServiceInstances | Set up contract management parameters. | CLM -\> Supply Chain Management |
| CLM integration external navigation links | CLMIntegrationExternalNavigationLinkEntity | CLMIntegrationExternalNavigationLinks | Set up external navigation links. | CLM -\> Supply Chain Management |
| CLM integration external navigation link key-value pairs | CLMIntegrationExternalNavigationLinkKeyValueEntity | CLMIntegrationExternalNavigationLinkKeyValues | Set up external navigation link query strings. | CLM -\> Supply Chain Management |

The following diagram illustrates the integration.

:::image type="content" source="../media/establishment.png" alt-text="Integration diagram." lightbox="../media/establishment.png":::

> [!IMPORTANT]
> Your CLM system must update relevant status fields in the *CLM integration service instance* entity to reflect the **Connection status** indicator.

### The CLM integration service instance entity

The *CLM integration service instance* entity provides information about the CLM integration service instance which contains contract management parameters.

| Physical name | Property | Type | Description |
|---|---|---|---|
| `ID` (PK) | ID | Int | Parameter key which will always be set to 0. |
| `InstanceName` | Connection name | String | N/A |
| `BaseURL` | Base URL | String | N/A |
| `ExternalNavigationBaseURL` | External navigation base URL | String | N/A |

<!--KFM: What does PK stand for?  -->

Here is an example request query for the CLM integration service instance entity:

```http
GET https://[baseURI]/data/CLMIntegrationServiceInstances
```

Here is an example response to that query:

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
| `NavigationName` | Navigation name | String | N/A |
| `RelativeURL` | Relative URL | String | N/A |
| `Action` | Action | Enum | Values: `OpenInNewTab`, `OpenInExistingTab` |

Here is an example request query for the *CLM integration external navigation links* entity:

```http
GET https://[baseURI]/data/CLMIntegrationExternalNavigationLinks
```

Here is an example response to that query:

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
| `Key` (PK) | Key | String | N/A |
| `Value` | Value | String | N/A |

<!--KFM: I'm confused by "The `QueryString` is the only allowed value". We list `Header` as a value too. What does this mean?  -->

Here is an example request query for the *CLM integration external navigation link key-value pairs* entity:

```http
GET https://[baseURI]/data/CLMIntegrationExternalNavigationLinkKeyValues
```

Here is an example response to that query:

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

- `CLMIntegrationServiceInstanceEntity.EstablishmentStatus` – Indicates whether connection has been established so the external CLM system can communicate with the Supply Chain Management. Report the connection status using one of the following values:
    - `NotStarted` – Connection establishment has't started yet.
    - `Success` – Connection establishment has succeeded.
    - `Error` – Connection establishment has failed.
- `CLMIntegrationServiceInstanceEntity.ConfigurationStatus` – Indicates whether external configuration links have been configured. Report the configuration status using one of the following values:
    - `NotStarted` – Configuration of the external navigation links hasn't started yet.
    - `Success` – Configuration of the external navigation links has succeeded.
    - `Error` – Configuration of the external navigation links has failed.

Administrators can read this status on the **Contract management parameters** page in Supply Chain Management. Learn more in [Enable and configure CLM integration (preview)](clm-enable.md).

Here is an example request query for updating the status on the *CLM integration service instance* entity:

```http
PATCH https://[baseURI]/data/CLMIntegrationServiceInstances(ID=0)
```

```json
{
    "EstablishmentStatus": "Success",
    "ConfigurationStatus": "Error"
}
```

## Configure service-based authentication

To gain access to the data entities, your CLM system must authenticate with Supply Chain Management. Service-based authentication with Microsoft Entra ID provides a secure way of allowing an external CLM system to connect with Supply Chain Management. To set up service-based authentication, follow these steps:

1. Register an application in Microsoft Entra ID. Take a note of the application ID (client ID) for your new application.
1. In Supply Chain Management, go to **System administration** \> **Setup** \> **Microsoft Entra ID applications** and add a row with the following settings:
    - **Client ID** – Enter the  application ID (client ID) you noted when registering the application in Microsoft Entra ID.
    - **Name** – Enter a descriptive name of the application.
    - **User ID** – Select the service account under which to run the application. We recommend that you create a new user and assign them the *CLM integration role* role.

For more information about how to register an application in Microsoft Entra ID and how to register external application in Supply Chain Management, see [Service endpoints overview](../../../../fin-ops-core/dev-itpro/data-entities/services-home-page.md#authentication).

<!-- KFM: We should consider adding a few details for how to actually authenticate (get a token, or whatever). -->

<!--KFM: This is repeated from [Synchronize master data (preview)](clm-sync-master-data.md). I think we should move it to a new topic and reference it from both of these, plus maybe also [Synchronize contracts (preview)](clm-sync-contracts.md) -->