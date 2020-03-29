---
# required metadata

title: Dual currency support for tax
description: This topic explains how to extend dual currency accounting feature in tax domain and the impact for tax calculation and posting
author: EricWang
manager: Ann Beebe
ms.date: 12/16/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-01-14
ms.dyn365.ops.version: 10.0.9

---

# Dual currency support for sales tax
[!include [banner](../includes/banner.md)]

This topic explains how to extend dual currency accounting for sales taxes and the impact for sales tax calculations, posting and settlements.

The Dual currency feature for Dynamics 365 Finance was introduced in version 8.1 (October 2018). It changes the way that accounting entries in the reporting currency are calculated.

In earlier versions, transactions were converted to the reporting currency in the following sequence: 

- Transaction total was calculated in the transaction currency > Transaction amount was converted to the accounting currency > Accounting currency amount was converted to the Reporting currency

After enabling the dual currency feature, transactions were converted to the reporting currency in the following sequence:

- Transaction currency amount > Reporting currency amount

For more information about dual currency, please refer to [Dual currency](dual-currency.md).

As a consequence of support for dual currencies, two new features are available in feature management: 

- Sales tax conversion (Release in version 10.0.9)
- Tax settlement auto balance in reporting currency (Release in version 10.0.11)

Dual currency support for sales taxes ensures that taxes are calculated accurately in the tax currency, and that the sales tax settlement balance is calculated accurately in both the accounting currency and reporting currency. 

## Sales tax conversion

The **Sales tax conversion** parameter provides two options to convert tax amount from transaction currency to tax currency. 

- Accounting currency: The path will be "Amount in transaction currency > Amount in accounting currency > Amount in tax currency". The accounting currency exhange rate type (configured in Ledger setup) will be used for the currency conversion.
- Reporting currency: The path will be "Amount in transaction currency > Amount in reporting currency > Amount in tax currency". The reporting currency exhange rate type (configured in Ledger setup) will be used for the currency conversion.

### Example

A simple example to demonstrate this functionality is:

Currency setup for ledger and tax

| Transaction currency | Accounting currency | Reporting currency | Tax currency |
| -------------------- | ------------------- | ------------------ | ------------ |
| EUR                  | USD                 | GBP                | GBP          |

Exchange rate

| From currency | To currency | Factor | Exchange rate |
| ------------- | ----------- | ------ | ------------- |
| EUR           | USD         | 1      | 1.11          |
| EUR           | GBP         | 1      | 0.83          |
| USD           | GBP         | 1      | 0.75          |

Tax amount calculation in different parameter options

Tax amount = 100 EUR

| Sales tax conversion parameters | Transaction currency (EUR) | Accounting currency (USD) | Reporting currency (GBP) | Tax currency (GBP) |
| ------------------------------- | -------------------------- | ------------------------- | ------------------------ | ------------------ |
| Accounting currency             | 100                        | 111                       | 83                       | **83.25**          |
| Reporting currency              | 100                        | 111                       | 83                       | **83**             |

This parameter can be configured based on the compliance need from tax authority.


### Upgrade Consideration

This feature will only apply for new transactions. For tax transaction already saved in TAXTRANS table but not settled yet, system will not recalculate tax amount in tax currency because the exchange rate at time point of posting tax is already missing.

To prevent preceding scenario, we recommend changing this parameter value in a new (clean) tax settlement period that doesn't contain any unsettled tax transactions. To change this value in the middle of a tax settlement period, please run "Settle and post sales tax" program for current tax settlement period before changing this parameter value.


## Track reporting currency tax amount

Three new fields were added to tax-related tables to track amounts in the reporting currency. These fields are within the TAXUNCOMMITTED and TAXTRANS tables:

- TaxAmountRep: tax amount in reporting currency
- TaxBaseAmountRep: base amount in reporting currency
- TaxInCostPriceRep: non-deductible amount in reporting currency

For tax only saved in TAXUNCOMMITTED table but not posted yet, system will recalculate tax amount in reporting currency at the time of posting and save in TAXTRANS table.

This release will not include changes to reports and forms that show the tax amount in the reporting currency. Changes to reports and forms will be delivered in the future release.



## Tax settlement auto-balance in reporting currency

If the tax settlement is not balanced in the reporting currency for certain reason such as the sales tax conversion path is "Accounting currency", or the exchange rate change in a single tax settlement period, thebn the system will automatically generate accounting entries to adjust the tax amount variance and offset it against realized exchange gain/loss account, which is configured in Ledger setup.

Using the the previous example to demonstrate this feature, suppose that the data in TAXTRANS table at the time of posting is as follows.

| Sales tax conversion parameters | Transaction currency (EUR) | Accounting currency (USD) | Reporting currency (GBP) | Tax currency (GBP) |
| ------------------------------- | -------------------------- | ------------------------- | ------------------------ | ------------------ |
| Accounting currency             | 100                        | 111                       | 83                       | **83.25**          |
| Reporting currency              | 100                        | 111                       | 83                       | **83**             |

When you run the sales tax settlement program at month-end, the accounting entry will be as follows:.
#### Scenario: sales tax conversion = "Accounting currency"

| Main account           | Transaction currency (GBP) | Accounting currency (USD) | Reporting currency (GBP) |
| ---------------------- | -------------------------- | ------------------------- | ------------------------ |
| Tax Payable/Receivable | -83.25                     | -111                      | -83.25                   |
| Tax Settlement         | 83.25                      | 111                       | 83.25                    |
| Realized Gain/Loss     | 0                          | 0                         | -0.25                    |
| Tax Payable/Receivable | 0                          | 0                         | 0.25                     |

#### Scenario: sales tax conversion = "Reporting currency"


| Main account           | Transaction currency (GBP) | Accounting currency (USD) | Reporting currency (GBP) |
| ---------------------- | -------------------------- | ------------------------- | ------------------------ |
| Tax Payable/Receivable | -83                        | -110.67                   | -83                      |
| Tax Settlement         | 83                         | 110.67                    | 83                       |
| Realized Gain/Loss     | 0                          | 0.33                      | 0                        |
| Tax Payable/Receivable | 0                          | -0.33                     | 0                        |



For more information, see the following topics:

- [Dual currency](dual-currency.md)
- [Sales tax overview](indirect-taxes-overview.md)

