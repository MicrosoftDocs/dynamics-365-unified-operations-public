---
title: Synchronize master data (preview)
description: This article describes the data entities and integration methods that you can use to synchronize master data between Dynamics 365 Supply Chain Management and an external contract lifecycle management (CLM) system.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: XXXX
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Synchronize master data (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.43 GA  -->

This article describes the data entities and integration methods that you can use to synchronize master data between Dynamics 365 Supply Chain Management and an external contract lifecycle management (CLM) system. Master data is essential for the CLM system to integrate contracts and related purchase agreements into Supply Chain Management. Supply Chain Management serves as the master system for providing the master data.

## Available data entities

Supply Chain Management offers several out-of-the-box data entities that external CLM systems can use to synchronize master data. The following table describes the available data entities necessary to synchronize contracts and purchase agreements. The required data entities may extend beyond those listed here, depending on the business requirements.

| Entity |Target entity | Public name (OData) | Company specific | Required by | Direction |
| --- | --- | --- | --- | --- | --- |
| CLM integration contract types | `CLMIntegrationContractTypeEntity` | `CLMIntegrationContractTypes` | No | Contracts | CLM -\> Supply Chain Management |
| Legal entities | `OMLegalEntity` | `LegalEntities` | No | Contracts / Purchase agreements | Supply Chain Management -\> CLM |
| Vendors V2 | `VendVendorV2Entity` | `VendorsV2` | Yes | Contracts / Purchase agreements | Supply Chain Management -\> CLM |
| smmContactPersonV2Entity | `smmContactPersonV2Entity` | `ContactPersons` | Yes | Contracts / Purchase agreements | Supply Chain Management -\> CLM |
| Purchase agreement classification | `PurchAgreementClassificationEntity` | N/A | No | Purchase agreements | Supply Chain Management -\> CLM |
| Sites V2 | `InventOperationalSiteV2Entity` | `OperationalSitesV2` | Yes | Purchase agreements | Supply Chain Management -\> CLM |
| Warehouses | `InventWarehouseEntity` | `Warehouses` | Yes | Purchase agreements | Supply Chain Management -\> CLM |
| Procurement product categories | `CatProcurementProductCategoryEntity` | `ProcurementProductCategories` | No | Purchase agreements | Supply Chain Management -\> CLM |
| CLM integration released products | `CLMIntegrationReleasedProductEntity` | `CLMIntegrationReleasedProducts` | Yes | Purchase agreements | Supply Chain Management -\> CLM |
| Released product variants V2 | `EcoResReleasedProductVariantV2Entity` | `ReleasedProductVariantsV2` | Yes | Purchase agreements | Supply Chain Management -\> CLM |
| Units | `UnitOfMeasureEntity` | `UnitsOfMeasure` | No | Purchase agreements | Supply Chain Management -\> CLM |
| Terms of payment | `PaymentTermEntity` | `PaymentTerms` | Yes | Purchase agreements | Supply Chain Management -\> CLM |
| Currencies | `CurrencyEntity` | `Currencies` | No | Purchase agreements | Supply Chain Management -\> CLM |
| Vendor payment method | `VendorPaymentMethodEntity` | `VendorPaymentMethods` | Yes | Purchase agreements | Supply Chain Management -\> CLM |
| Payment schedule | `PaymentScheduleEntity` | `PaymentSchedules` | Yes | Purchase agreements | Supply Chain Management -\> CLM |
| Terms of delivery | `DeliveryTermsEntity` | `DeliveryTerms` | Yes | Purchase agreements | Supply Chain Management -\> CLM |
| Projects | `ProjectEntity` | `Projects` | Yes | Purchase agreements | Supply Chain Management -\> CLM |
| CashDiscountEntity | `CashDiscountEntity` | `CashDiscounts` | Yes | Purchase agreements | Supply Chain Management -\> CLM |
| CLM integration country/regions | `CLMIntegrationAddressCountryRegionEntity` | `CLMIntegrationAddressCountryRegions` | No | Purchase agreements | Supply Chain Management -\> CLM |
| ... | ... | ... | N/A | N/A | N/A |

<!-- KFM: Can we use standard English names for CashDiscountEntity and smmContactPersonV2Entity in the first column here? -->
<!-- KFM: What does the final row mean? -->

> [!NOTE]
> Company-specific data entities include the `dataAreaId` field, which indicates the legal entity to which a record belongs. Your CLM system must adopt the same behavior that supports both company-specific and cross-company records. For more information about cross-company behavior, see [Cross-company behavior of data entities](../../../../fin-ops-core/dev-itpro/data-entities/cross-company-behavior.md).

The following diagram shows how master data is integrated and synchronized.

:::image type="content" source="../media/master-data.png" alt-text="Master data integration diagram." lightbox="../media/master-data.png":::

## Data integration APIs

This section describes integration patterns available in Supply Chain Management and guidelines for synchronizing master data between Supply Chain Management and the CLM system. Recommended integration patterns for CLM integration are listed in the following table.

| Pattern | Timing | Batch | Documentation |
| --- | --- | --- | --- |
| Data management package REST API | Asynchronous | Yes | [Data management package REST API](../../../../fin-ops-core/dev-itpro/data-entities/data-management-api.md) |
| OData | Synchronous | No | [Open Data Protocol (OData)](../../../../fin-ops-core/dev-itpro/data-entities/odata.md) |

### Guidelines

You should select an integration pattern based on your data volume and real-time requirements. For high-volume master data, we generally recommend using the *Data Management Package API*, while for low-volume master data, we recommend either the *Data Management Package API* or *OData*. For more information about the integration patterns and scenarios, see [Integration between finance and operations apps and third-party services](../../../../fin-ops-core/dev-itpro/data-entities/integration-overview.md).

### Enable change tracking

When using the *Data Management Package API* integration pattern there, it's possible to enable change tracking for selected data entities, which enables incremental exports. In an incremental export, only changed records are exported. For more information how to enable change tracking for an entity, see [Enable change tracking for entities](../../../../fin-ops-core/dev-itpro/data-entities/entity-change-track.md).

### Create data projects

Prerequisite for using the *Data Management Package API* integration pattern is to create a *data project* in the **Data management** workspace. You can create the data project manually in Supply Chain Management or from the external system using the *OData* protocol. For more information about data management and data import/export projects, see [Data management overview](../../../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

The following table lists the data entities available for creating a data project.

| Entity | Target entity | Public name (OData) | Company specific | Direction |
| --- | --- | --- | --- | --- |
| Definition Groups | `DataManagementDefinitionGroupEntity` | `DataManagementDefinitionGroups` | No | CLM -> Supply Chain Management |
| Entities for a processing group | `DataManagementDefinitionGroupDetailEntity` | `DataManagementDefinitionGroupDetails` | No | CLM -> Supply Chain Management |

The following diagram shows how data projects are integrated and synchronized.

:::image type="content" source="../media/data-project.png" alt-text="Data projects integration diagram." lightbox="../media/data-project.png":::

### Configure service-based authentication

Authentication with Microsoft Entra ID provides a secure way of authenticating external CLM with Supply Chain Management. To access resources within Supply Chain Management, you must register an application in Microsoft Entra ID. Once the application (client ID) is created, it should be registered as an external application in the **Microsoft Entra applications** page in Supply Chain Management. For the service account **User ID**, it's recommended to create a new user and assign them the **CLM integration role**. For more information about how to register an application in Microsoft Entra ID and how to register external application in the Supply Chain Management, see the following [Article](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/services-home-page#authentication).

<!--KFM: This is repeated from [Prepare a CLM system to connect to Supply Chain Management (preview)](clm-establish-connection.md), but I didn't edit this copy. I think we should move it to a new topic and reference it from both of these, plus maybe also [Synchronize contracts (preview)](clm-sync-contracts.md)  -->