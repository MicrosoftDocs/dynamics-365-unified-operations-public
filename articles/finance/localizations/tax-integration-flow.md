---
title: Tax integration overview
description: This article provides an overview and introduces the flow of Tax integration.
author: Qiuchen-Ren
ms.author: qire
ms.reviewer: kfend
ms.topic: conceptual
ms.date: 04/25/2022
ms.custom: bap-template
---

# Tax integration overview

[!include [banner](../includes/banner.md)]

Tax integration is a framework that's designed to replace the legacy tax calculation engine and when needed, call the [Tax Calculation Service](global-tax-calcuation-service-overview.md). This article introduces the basic flow of tax integration.

## Entrance to tax integration

The `TaxIntegrationFacade` class contains most of the code and functions of tax integration. However, some additional code is needed to enter the tax integration flow before `TaxIntegrationFacade`, which is the entrance to tax integration.
This entrance code constructs a `TaxIntegrationDocumentObject`, which is passed to `TaxIntegrationFacade`. The entrance code also prepares some basic information, which is used in the following integration actions.

### TaxIntegrationFacade

The `TaxIntegrationFacade` class realizes and controls the real flow of tax integration calling several classes, such as `TaxIntegration***ActivityOnDocument`. A `TaxIntegrationDocument` object is passed from activity to activity. These activities carry out their actions on the object in turn.

The following list activities are all document-level activities iwht the suffix, **OnDocument**. There are also line-level activities that work on `TaxIntegrationLineObject`, which suffix is *OnLine*.

- TaxIntegrationSettingRetrievalActivityOnDocument: Retrieves settings that impact tax calculation and saves them to the `TaxIntegrationDocumentObject`.
- TaxIntegrationDataRetrievalActivityOnDocument: Prepares the metadata needed by tax calculation and then copies it to the `TaxIntegrationDocumentObject`.
- TaxIntegrationCalculationActivityOnDocument: Transforms the `TaxIntegrationDocumentObejct` to a request, sends the request to the Tax Calculation service,  and then  parses the response.
- TaxIntegrationErrorHandlingActivityOnDocument: Handles the error message returned from the Tax Calculation service.
- TaxIntegrationTaxIdActivityOnDocument: Processes logic regarding the **Multiple VAT ID** feature.
- TaxIntegrationListCodeActivityOnDocument: Processes logic regarding the **List Code** feature.
- TaxIntegrationCurrencyExchangeActivityOnDocument: Processes logic regarding the **Currency Exchange rate/Rounding/Penny difference adjustment** feature.
- TaxIntegrationDataPersistenceActivityOnDocument: Persists the Tax Calculation result and other information, including VAT ID and list code, that need to be saved to the database.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
