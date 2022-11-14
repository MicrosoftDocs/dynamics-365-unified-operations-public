---
title: Tax integration flow
description: This article introduces the flow of tax integration.
author: Qiuchen-Ren
ms.author: qire
ms.reviewer: kfend
ms.topic: conceptual
ms.date: 11/14/2022
ms.custom: bap-template
---

# Tax integration flow

[!include [banner](../includes/banner.md)]

The flow of **Tax Integration** is showed as below chart:

![IntegrationFlow.png](./media/tax-integration-flow.png)

## Core tax and tax integration

The left part in the chart is the original tax calculation engine, which is called **Core Tax**. It is by passed by the new **Tax Integration** framework which calls the new calculation engine **Tax Calculation Service**.

All the modules in the big square make up the **Tax Integration**.

## Entrance code to tax integration

`TaxIntegrationFacade` holds the real tax integration flow. However, we need an entrance to enter the tax integration flow.
This entrance code constructs `TaxIntegrationDocumentObject` and prepares some basic information which is used in the following integration flow.

## TaxIntegrationFacade

`TaxIntegrationFacade` controls the whole tax integration flow. It calls a bunch of classes with names like `TaxIntegration***ActivityOnDocument`. A `TaxIntegrationDocument` object is passed from activity to activity. And these activities carry out their action on the object in order.

The activities showed in the chart are all document level activities with suffix **OnDocument**. Actually, there is also line level activities that work on `TaxIntegrationLineObject`.

Simple introduction to these activites:

- Setting retrieval activity(TaxIntegrationSettingRetrievalActivityOnDocument): Retrieves the settings that will impact tax calculation and save them in the `TaxIntegrationDocumentObject`.
- Data retrieval activity(TaxIntegrationDataRetrievalActivityOnDocument): Prepares the metadata needed by tax calculation, copy them to a `TaxIntegrationDocumentObject`.
- Calculation activity(TaxIntegrationCalculationActivityOnDocument): Transforms `TaxIntegrationDocumentObejct` to a request, sends the request to tax calculation service and receives the response from it.
- Error handling activity(TaxIntegrationErrorHandlingActivityOnDocument): Handles the error message returned from tax calculation service.
- Tax ID activity(TaxIntegrationTaxIdActivityOnDocument): Processes logic regarding **Multiple VAT ID** feature.
- List code activity(TaxIntegrationListCodeActivityOnDocument): Processes logic regarding **List Code** feature.
- Currency exchange activity(TaxIntegrationCurrencyExchangeActivityOnDocument): Processed logic regarding **Currency Exchange rate/Rounding/Penny difference adjustment** feature.
- Data persistence activity(TaxIntegrationDataPersistenceActivityOnDocument): Persists the tax calculation result and other information (VAT ID, list code and etc.) that need to be saved to the database.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
