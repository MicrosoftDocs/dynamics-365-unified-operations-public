---
title: Integrated ledger
description: This topic describes the integration of ledger data between Finance and Operations and other Dynamics 365 applications using the Dataverse.
author:  robinarh
ms.date: 09/06/2019
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: rhaertle
ms.search.region: global
ms.author: rhaertle
---

# Integrated ledger

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

In a business application, ledger data defines the core set up for how a company does business. For example, ledger data describes the fiscal year the company follows, the currencies it transacts in, and the accounts it uses. This topic describes the integration of this core financial data.

## Templates

Ledger data includes a collection of core financial table maps that work together during data interaction, as shown in the following table.

Finance and Operations apps      | Model-driven app in Dynamics 365 | Description
---------------------------------|----------------------------------|------------
[CDS Exchange Rates](#123) | msdyn_currencyexchangerates |
[Chart of accounts](#121) | msdyn_chartofaccountses |
[Currencies](#218) | transactioncurrencies |
[Exchange rate currency pair](#122) | msdyn_currencyexchangeratepairs |
[Exchange rate type](#129) | msdyn_exchangeratetypes |
[Financial dimension format](#130) | msdyn_financialdimensionformats |
[Financial dimensions](#128) | msdyn_dimensionattributes |
[Fiscal calendar integration entity](#132) | msdyn_fiscalcalendars |
[Fiscal calendar period](#131) | msdyn_fiscalcalendarperiods |
[Fiscal calendar year integration entity](#133) | msdyn_fiscalcalendaryears |
[Ledger](#148) | msdyn_ledgers |
[Main account](#152) | msdyn_mainaccounts |
[Main account categories](#151) | msdyn_mainaccountcategories |

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
