---
title: Exchange rate type for sales tax
description: This article explains the logic for calculation of sales tax on the special exchange rate.
author: epodkolz
ms.date: 07/10/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: 
ms.author: epodkolzina
ms.search.validFrom: 
ms.dyn365.ops.version: AX 10.0.36
---

# Exchange rate type for sales tax

[!include [banner](../includes/banner.md)]

This article explains the logic for exchange rate type setup and calculation for sales tax.

Starting from the 10.0.35 version, the functionality for [VAT exchange rate](../finance/localizations/emea-vat-exchange-rate.md) is extetded for more counries/regions.

In addition, the following capabilities were enhanced:
 - Support of direct recalculation from transaction currency to tax currency.
 - Support of amounts adjustment in Tax currency.


## Prerequisites

This functionality is available only for the legal entities with the enabled Tax calculation service (TCS) for the selected business processes. To learn about TCS, its capabilities and how to set up, please refer to  [Tax Calculation overview] ().
In addition, enable features in Feature management workspace:
•	Date of VAT register Tax point date (Date of VAT register) - Finance | Dynamics 365 | Microsoft Learn. 
•	Enable exchange rate types for sales tax
After enabling features, You might need to refresh the page to get the UI updated. 
Note, if you haven’t used the Date of VAT register functionality, make sure you follow instructions described in [Tax point date (Date of VAT register)]().




