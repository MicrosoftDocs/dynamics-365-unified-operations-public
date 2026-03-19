---
title: Tax integration overview
description: This article provides an overview of the flow of Tax integration, including an overview on the TaxIntegrationFacade class, which realizes the flow of tax integration.
author: Qiuchen-Ren
ms.author: qire
ms.topic: overview
ms.date: 03/19/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.custom: 
  - bap-template
---

# Tax integration overview

[!include [banner](../../includes/banner.md)]

Tax integration is a framework that replaces the legacy tax calculation engine and, as required, calls the [Tax Calculation service](global-tax-calcuation-service-overview.md). This article introduces the basic flow of tax integration.

## Entrance to tax integration

The `TaxIntegrationFacade` class contains most of the code and functions for tax integration. However, some additional code is required to enter the tax integration flow before `TaxIntegrationFacade`. This code is the entrance to tax integration. The entrance code constructs a document object, `TaxIntegrationDocumentObject`, which it passes to `TaxIntegrationFacade`. The entrance code also prepares some basic information that's used in the following integration actions.

### TaxIntegrationFacade

The `TaxIntegrationFacade` class implements and controls the real flow of tax integration by calling several classes, such as `TaxIntegration***ActivityOnDocument`. The class passes a `TaxIntegrationDocumentObject` from activity to activity. These activities perform their actions on the object in turn.

The following list shows all document-level activities that have the suffix "OnDocument." There are also line-level activities that work on `TaxIntegrationLineObject`. Those activities have the suffix "OnLine."

- **TaxIntegrationSettingRetrievalActivityOnDocument** – This activity retrieves settings that affect tax calculation and saves them to the `TaxIntegrationDocumentObject` object.
- **TaxIntegrationDataRetrievalActivityOnDocument** – This activity prepares the metadata that's required by tax calculation and then copies it to the `TaxIntegrationDocumentObject` object.
- **TaxIntegrationCalculationActivityOnDocument** – This activity transforms the `TaxIntegrationDocumentObject` object to a request, sends the request to the Tax Calculation service, and then parses the response.
- **TaxIntegrationErrorHandlingActivityOnDocument** – This activity handles the error message that's returned from the Tax Calculation service.
- **TaxIntegrationTaxIdActivityOnDocument** – This activity processes logic that's related to the **Multiple VAT ID** feature.
- **TaxIntegrationListCodeActivityOnDocument** – This activity processes logic that's related to the **List Code** feature.
- **TaxIntegrationCurrencyExchangeActivityOnDocument** – This activity processes logic that's related to the **Currency Exchange rate/Rounding/Penny difference adjustment** feature.
- **TaxIntegrationDataPersistenceActivityOnDocument** – This activity persists the tax calculation result and other information that must be saved to the database, including the value-added tax (VAT) ID and list code.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
