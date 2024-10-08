---
title: Data integration APIs (preview)
description: This article describes integration patterns available in Supply Chain Management and guidelines for synchronizing master data between Supply Chain Management and the contract lifecycle management (CLM) system.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Data integration APIs (preview)

[!include [banner](../../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.43 GA  -->

<!-- KFM: Most of this information was repeated in three of your topics. I collected here and added links. Agree? -->

This article describes integration patterns available in Supply Chain Management and guidelines for synchronizing master data between Supply Chain Management and the contract lifecycle management (CLM) system. Recommended integration patterns for CLM integration are listed in the following table.

| Pattern | Timing | Batch | Documentation |
| --- | --- | --- | --- |
| Data management package REST API | Asynchronous | Yes | [Data management package REST API](../../../../fin-ops-core/dev-itpro/data-entities/data-management-api.md) |
| OData | Synchronous | No | [Open Data Protocol (OData)](../../../../fin-ops-core/dev-itpro/data-entities/odata.md) |

## Guidelines

You should select an integration pattern based on your data volume and real-time requirements.

- For high-volume master data, we generally recommend using the *Data Management Package API*, while for low-volume master data, we recommend either the *Data Management Package API* or *OData*.
- For integrations requiring real-time data synchronization and error handling, we generally recommend that you use the *OData protocol* provided your peak data volume isn't excessively high. For handling large volumes of data, we recommend using the *Data Management Package API* instead.

Learn more about the integration patterns and scenarios in [Integration between finance and operations apps and third-party services](../../../../fin-ops-core/dev-itpro/data-entities/integration-overview.md).

## Enable change tracking

When using the *Data Management Package API* integration pattern there, it's possible to enable change tracking for selected data entities, which enables incremental exports. In an incremental export, only changed records are exported.

Learn more about how to enable change tracking for an entity in [Enable change tracking for entities](../../../../fin-ops-core/dev-itpro/data-entities/entity-change-track.md).

## Create data projects

Prerequisite for using the *Data Management Package API* integration pattern is to create a *data project* in the **Data management** workspace. You can create the data project manually in Supply Chain Management or from the external system using the *OData* protocol.

The following diagram shows how data projects are integrated and synchronized.

:::image type="content" source="../media/data-project.png" alt-text="Data projects integration diagram." lightbox="../media/data-project.png":::

The following table lists the data entities available for creating a data project.

| Entity | Target entity | Public name (OData) | Company specific | Direction |
| --- | --- | --- | --- | --- |
| Definition Groups | `DataManagementDefinitionGroupEntity` | `DataManagementDefinitionGroups` | No | CLM -> Supply Chain Management |
| Entities for a processing group | `DataManagementDefinitionGroupDetailEntity` | `DataManagementDefinitionGroupDetails` | No | CLM -> Supply Chain Management |

Learn more about data management and data import/export projects in [Data management overview](../../../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

## Configure and use service-based authentication

To gain access to the data entities through the API, your CLM system must authenticate with Supply Chain Management. Service-based authentication with Microsoft Entra ID provides a secure way of allowing an external CLM system to connect with Supply Chain Management. To set up service-based authentication, follow these steps:

1. Register an application in Microsoft Entra ID. Take a note of the application ID (client ID) for your new application.
1. In Supply Chain Management, go to **System administration** \> **Setup** \> **Microsoft Entra ID applications** and add a row with the following settings:
    - **Client ID** – Enter the  application ID (client ID) you noted when registering the application in Microsoft Entra ID.
    - **Name** – Enter a descriptive name of the application.
    - **User ID** – Select the service account under which to run the application. We recommend that you create a new user and assign them the *CLM integration role* role.

Learn more about how to register an application in Microsoft Entra ID and how to register external application in Supply Chain Management in [Service endpoints overview](../../../../fin-ops-core/dev-itpro/data-entities/services-home-page.md#authentication).

<!-- KFM: We should consider adding a few details and/or a link for how to actually authenticate (get a token, or whatever). -->

## Related information

- [Establish a connection from a CLM system to Supply Chain Management](clm-establish-connection.md)
- [Synchronize master data](clm-sync-master-data.md)
- [Synchronize contracts](clm-sync-contracts.md)