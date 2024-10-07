---
title: Synchronize master data (preview)
description: This article describes the data entities and integration methods that you can use to synchronize master data between Dynamics 365 Supply Chain Management and an external contract lifecycle management (CLM) system.
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
<!-- KFM: Preview until 10.0.43 GA  -->

This article describes the data entities and integration methods that you can use to synchronize master data between Dynamics 365 Supply Chain Management and an external contract lifecycle management (CLM) system. Master data is essential for the CLM system to integrate contracts and related purchase agreements into Supply Chain Management. Supply Chain Management serves as the master system for providing the master data.

## Access the data integration APIs

For information about which data integration APIs are available, how to enable change tracking, and how to authenticate with Supply Chain Management so your CLM system can access that data entities described in this topic, see [Data integration APIs](clm-data-integration-apis.md).

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

## Related information

- [Data integration APIs](clm-data-integration-apis.md)
