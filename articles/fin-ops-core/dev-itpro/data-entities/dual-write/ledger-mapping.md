---
title: Integrated ledger
description: This topic describes the integration of ledger data between Finance and Operations and other Dynamics 365 applications using the Dataverse.
author:  tonyafehr
ms.date: 09/06/2019
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: tfehr
ms.search.region: global
ms.author: tfehr
ms.search.validFrom: 2020-01-06
---

# Integrated ledger

[!include [banner](../../includes/banner.md)]



In a business application, ledger data defines the core set up for how a company does business. For example, ledger data describes the fiscal year the company follows, the currencies it transacts in, and the accounts it uses. This topic describes the integration of this core financial data.

## Templates

Ledger data includes a collection of core financial table maps that work together during data interaction, as shown in the following table.

Finance and operations apps | Customer engagement apps     | Description
---------------------------------|----------------------------------|------------
[CDS Exchange Rates](mapping-reference.md#123) | msdyn_currencyexchangerates |
[Chart of accounts](mapping-reference.md#121) | msdyn_chartofaccountses |
[Currencies](mapping-reference.md#218) | transactioncurrencies |
[Exchange rate currency pair](mapping-reference.md#122) | msdyn_currencyexchangeratepairs |
[Exchange rate type](mapping-reference.md#129) | msdyn_exchangeratetypes |
[Financial dimension format](mapping-reference.md#130) | msdyn_financialdimensionformats |
[Financial dimensions](mapping-reference.md#128) | msdyn_dimensionattributes |
[Fiscal calendar integration entity](mapping-reference.md#132) | msdyn_fiscalcalendars |
[Fiscal calendar period](mapping-reference.md#131) | msdyn_fiscalcalendarperiods |
[Fiscal calendar year integration entity](mapping-reference.md#133) | msdyn_fiscalcalendaryears |
[Ledger](mapping-reference.md#148) | msdyn_ledgers |
[Main account](mapping-reference.md#152) | msdyn_mainaccounts |
[Main account categories](mapping-reference.md#151) | msdyn_mainaccountcategories |

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
