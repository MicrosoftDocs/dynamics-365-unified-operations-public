---
title: Pricing data import and export entities
description: Learn about the set of data entities designed for importing and exporting pricing rules for Unified pricing management.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 01/26/2026
ms.custom:
  - bap-template
---

# Pricing data import and export entities

Microsoft Dynamics 365 Supply Chain Management and Dynamics 365 Commerce use the data management framework (DMF) for import and export. The following articles provide more information about it:

- [Data management overview](../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md)
- [Data import and export jobs overview](../../fin-ops-core/fin-ops/data-entities/data-import-export-job.md)

Unified pricing management provides an enhanced set of data entities designed specifically for importing and exporting pricing rules. These improvements strengthen DMF mapping accuracy, data validation, and staging performance.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.46 or later.
- The feature named *Unified pricing management pricing rule performance enhancement* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Available entities

Unified pricing management includes an enhanced set of data entities designed for importing and exporting pricing rules. The set comprises the following entities:

- `GUPMarginComponentPriceAdjustmentLineV2Entity`
- `GUPMarginComponentPriceAdjustmentV2Entity`
- `GUPOpenTradeAgreementJournalLineV2Entity`
- `GUPPriceDiscPriceAttributeCustomerGroupV2Entity`
- `GUPPriceTermJournalTransV2Entity`
- `GUPRetailDiscountLineV2Entity`
- `GUPRetailDiscountV2Entity`
- `GUPSalesAutomaticSalesDocumentHeaderChargeTableV2Entity`
- `GUPSalesAutomaticSalesDocumentLineChargeTableV2Entity`
- `GUPSalesAutomaticSalesDocumentLineChargeV2Entity`
- `GUPTAMRebateAndDeductionsAgreementHeaderV2Entity`
