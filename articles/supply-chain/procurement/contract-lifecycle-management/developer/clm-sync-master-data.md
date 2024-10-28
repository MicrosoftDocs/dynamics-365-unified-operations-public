---
title: Synchronize master data (preview)
description: Learn about the data entities and integration methods that you can use to sync master data between Microsoft Dynamics 365 Supply Chain Management and an external contract lifecycle management (CLM) system.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Synchronize master data (preview)

[!include [banner](../../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.43 GA -->

This article describes the data entities and integration methods that you can use to sync master data between Microsoft Dynamics 365 Supply Chain Management and an external contract lifecycle management (CLM) system. Master data is essential for the CLM system to integrate contracts and related purchase agreements into Supply Chain Management. Supply Chain Management functions as the master system for providing the master data.

## Access the data integration APIs

Learn which data integration APIs are available in [Data integration APIs](clm-data-integration-apis.md). There, you can also learn how to enable change tracking, and how to authenticate with Supply Chain Management so that your CLM system can access the data entities that are described in this article.

## Available data entities

Supply Chain Management offers several out-of-box data entities that external CLM systems can use to sync master data. The following table describes the available data entities that are required for the synchronization of contracts and purchase agreements. Other data entities might be required, depending on your business requirements.

| Entity | Target entity | Public name (OData) | Company-specific | Required by | Direction |
|---|---|---|---|---|---|
| CLM integration contract types | `CLMIntegrationContractTypeEntity` | `CLMIntegrationContractTypes` | No | Contracts | CLM &rarr; Supply Chain Management |
| Legal entities | `OMLegalEntity` | `LegalEntities` | No | Contracts/Purchase agreements | Supply Chain Management &rarr; CLM |
| Vendors V2 | `VendVendorV2Entity` | `VendorsV2` | Yes | Contracts/Purchase agreements | Supply Chain Management &rarr; CLM |
| Contacts V2 | `smmContactPersonV2Entity` | `ContactPersons` | Yes | Contracts/Purchase agreements | Supply Chain Management &rarr; CLM |
| Purchase agreement classification | `PurchAgreementClassificationEntity` | Not applicable | No | Purchase agreements | Supply Chain Management &rarr; CLM |
| Sites V2 | `InventOperationalSiteV2Entity` | `OperationalSitesV2` | Yes | Purchase agreements | Supply Chain Management &rarr; CLM |
| Warehouses | `InventWarehouseEntity` | `Warehouses` | Yes | Purchase agreements | Supply Chain Management &rarr; CLM |
| Procurement product categories | `CatProcurementProductCategoryEntity` | `ProcurementProductCategories` | No | Purchase agreements | Supply Chain Management &rarr; CLM |
| CLM integration released products | `CLMIntegrationReleasedProductEntity` | `CLMIntegrationReleasedProducts` | Yes | Purchase agreements | Supply Chain Management &rarr; CLM |
| Released product variants V2 | `EcoResReleasedProductVariantV2Entity` | `ReleasedProductVariantsV2` | Yes | Purchase agreements | Supply Chain Management &rarr; CLM |
| Units | `UnitOfMeasureEntity` | `UnitsOfMeasure` | No | Purchase agreements | Supply Chain Management &rarr; CLM |
| Terms of payment | `PaymentTermEntity` | `PaymentTerms` | Yes | Purchase agreements | Supply Chain Management &rarr; CLM |
| Currencies | `CurrencyEntity` | `Currencies` | No | Purchase agreements | Supply Chain Management &rarr; CLM |
| Vendor payment method | `VendorPaymentMethodEntity` | `VendorPaymentMethods` | Yes | Purchase agreements | Supply Chain Management &rarr; CLM |
| Payment schedule | `PaymentScheduleEntity` | `PaymentSchedules` | Yes | Purchase agreements | Supply Chain Management &rarr; CLM |
| Terms of delivery | `DeliveryTermsEntity` | `DeliveryTerms` | Yes | Purchase agreements | Supply Chain Management &rarr; CLM |
| Projects | `ProjectEntity` | `Projects` | Yes | Purchase agreements | Supply Chain Management &rarr; CLM |
| Cash discount | `CashDiscountEntity` | `CashDiscounts` | Yes | Purchase agreements | Supply Chain Management &rarr; CLM |
| CLM integration country/regions | `CLMIntegrationAddressCountryRegionEntity` | `CLMIntegrationAddressCountryRegions` | No | Purchase agreements | Supply Chain Management &rarr; CLM |

> [!NOTE]
> Company-specific data entities include the `dataAreaId` field, which indicates the legal entity that a record belongs to. Your CLM system must adopt the same behavior to support both company-specific records and cross-company records. Learn more about cross-company behavior in [Cross-company behavior of data entities](../../../../fin-ops-core/dev-itpro/data-entities/cross-company-behavior.md).

The following illustration shows how master data is integrated and synced.

:::image type="content" source="../media/master-data.png" alt-text="Diagram that shows the integration of master data." lightbox="../media/master-data.png":::

## Related information

- [Data integration APIs](clm-data-integration-apis.md)
