---
title: Data integration APIs (preview)
description: Learn about the integration patterns that are available in Microsoft Dynamics 365 Supply Chain Management and guidelines for syncing master data between Supply Chain Management and the contract lifecycle management (CLM) system.
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
<!-- KFM: Preview until 10.0.43 GA -->

This article describes the integration patterns that are available in Microsoft Dynamics 365 Supply Chain Management. It also provides guidelines for syncing master data between Supply Chain Management and the contract lifecycle management (CLM) system.

The following table describes the recommended integration patterns for CLM integration.

| Pattern | Timing | Batch | Documentation |
|---|---|---|---|
| Data management package REST API | Asynchronous | Yes | [Data management package REST API](../../../../fin-ops-core/dev-itpro/data-entities/data-management-api.md) |
| OData | Synchronous | No | [Open Data Protocol (OData)](../../../../fin-ops-core/dev-itpro/data-entities/odata.md) |

## Guidelines

You should select an integration pattern based on your data volume and real-time requirements.

- For high-volume master data, we generally recommend that you use the *Data management package REST API* pattern. For low-volume master data, use either the *Data management package REST API* pattern or the *OData* pattern.
- For integrations that require real-time data synchronization and error handling, we generally recommend that you use the *OData* pattern, provided that your peak data volume isn't excessively high. To handle large volumes of data, we recommend that you use the *Data management package REST API* pattern instead.

Learn more about the integration patterns and scenarios in [Integration between finance and operations apps and third-party services](../../../../fin-ops-core/dev-itpro/data-entities/integration-overview.md).

## Enable change tracking

When you use the *Data management package REST API* integration pattern, you can enable change tracking for selected data entities. In this way, you enable *incremental exports*. In an incremental export, only changed records are exported.

Learn how to enable change tracking for an entity in [Enable change tracking for entities](../../../../fin-ops-core/dev-itpro/data-entities/entity-change-track.md).

## Create data projects

As a prerequisite for using the *Data management package REST API* integration pattern, you must create a *data project* in the **Data management** workspace. You can manually create the data project in Supply Chain Management, or you can create it from the external system by using the *OData* pattern.

The following illustration shows how data projects are integrated and synced.

:::image type="content" source="../media/data-project.png" alt-text="Diagram that shows the integration of data projects." lightbox="../media/data-project.png":::

The following table lists the data entities that are available for the creation of a data project.

| Entity | Target entity | Public name (OData) | Company-specific | Direction |
|---|---|---|---|---|
| Definition Groups | `DataManagementDefinitionGroupEntity` | `DataManagementDefinitionGroups` | No | CLM &rarr; Supply Chain Management |
| Entities for a processing group | `DataManagementDefinitionGroupDetailEntity` | `DataManagementDefinitionGroupDetails` | No | CLM &rarr; Supply Chain Management |

Learn more about data management and data import/export projects in [Data management overview](../../../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

## Configure and use service-based authentication

To gain access to the data entities through the API, your CLM system must authenticate with Supply Chain Management. Service-based authentication with Microsoft Entra ID provides a secure way to allow an external CLM system to connect with Supply Chain Management. To set up service-based authentication, follow these steps.

1. Register an application in Microsoft Entra ID. Make a note of the application ID (client ID) for the new application.
1. In Supply Chain Management, go to **System administration** \> **Setup** \> **Microsoft Entra ID applications**.
1. Add a row, and set the following fields for it:

    - **Client ID** – Enter the application ID (client ID) that you noted when you registered the application in Microsoft Entra ID.
    - **Name** – Enter a descriptive name of the application.
    - **User ID** – Select the service account to run the application under. We recommend that you create a new user and assign the *CLM integration role* role to it.

Learn how to register applications in Microsoft Entra ID and external applications in Supply Chain Management in [Service endpoints overview](../../../../fin-ops-core/dev-itpro/data-entities/services-home-page.md#authentication).

After you register the Microsoft Entra ID application, you can use it to set up your external CLM system to authenticate with the Supply Chian Management API. Learn more about how authentication works in [Authentication](../../../../fin-ops-core/dev-itpro/data-entities/services-home-page.md#authentication).

## Related information

- [Establish a connection from a CLM system to Supply Chain Management](clm-establish-connection.md)
- [Synchronize master data](clm-sync-master-data.md)
- [Synchronize contracts](clm-sync-contracts.md)
