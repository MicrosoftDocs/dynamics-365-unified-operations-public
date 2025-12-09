---
title: Set up Japan consumption tax report
description: Learn how to set up the system to support the Japan consumption tax report in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerParameters, LedgerBadDebtAccounts_JP, OMLegalEntity, TaxTable
ms.custom: 
  - bap-template
---

# Set up Japan consumption tax report

[!include [banner](../../includes/banner.md)]

This article explains how to set up the system to support the Japan consumption tax report in Microsoft Dynamics 365 Finance.

The following procedures walk you through how to set up the system to support the Japan consumption tax report. 

The procedures use the demo data company JPMF.

## Enable the consumption tax report

To enable the consumption tax report, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Parameters \> General ledger parameters**.
1. Select the **Sales tax** FastTab.
1. Expand the **Japanese tax reporting** section.
1. In the **Consumption tax reports** field, select **Yes**.

## Configure tax reporting accounts

To configure tax reporting accounts, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Setup \> Sales tax \> Tax reporting accounts**.
1. Select **Edit**.
1. In the **Bad debt** field, enter a value. For example, enter "84720".  
1. In the **Collected bad debt** field, enter a value. For example, enter "84710".

## Enter Japan reporting information for a legal entity

To enter Japan reporting information for a legal entity, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration \> Organizations \> Legal entities**.
1. Expand the **Registration numbers** section.
1. Select **Edit**.
1. In the **Accounting personnel** field, enter a value.
1. In the **Company representative** field, enter a value.

## Enter report setup information for a sales tax code

To enter report setup information for a sales tax code, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Indirect taxes \> Sales tax \> Sales tax codes**.
1. Use the Quick Filter to find records. For example, filter on the **Sales tax code** field with a value of "JP Cons".
1. Expand the **Report setup** section.
1. Select **Edit**.
1. Confirm that the reporting codes are configured properly using the information in the following table.

### Reporting codes in Japanese sales tax report base items

| **Reporting code** | **Reporting code name**                                                               | **Calculation sheet column**                                  | **3 - (1) report column**  | **3 - (2) report**  **column**         |
|--------------------|---------------------------------------------------------------------------------------|---------------------------------------------------------------|----------------------------|----------------------------------------|
| 1                  | Taxable sales                                                                         | Item 1                                                        | Item 1                     | Item 1, Item 2-Item 6 (at tax rates) |
| 202                | Tax-exempted sales                                                                    | Item 2                                                        | Item 15                    | \-                                     |
| 203                | Non-taxable assets for export                                                         | Item 3                                                        | Item 15                    | \-                                     |
| 206                | Non-taxable sales                                                                     | Item 6                                                        | Item 16                    | \-                                     |
| 208                | Taxable purchase related to only taxable sales                                        | Item 8, Item 14 (if Ratio \<0.95 & Individual method)         | \-                         | \-                                     |
| 210                | Taxable import                                                                        | \-                                                            | \-                         | \-                                     |
| 214                | Taxable purchase related to non-taxable sales                                         | Item 8                                                        | \-                         | \-                                     |
| 215                | Common taxable purchase in common                                                     | Item 8, Item 15 (if Ratio \<0.95 & Individual method)         | \-                         | \-                                     |
| 7001               | Consumption tax amount of taxable sales - Credit note                                 | Item 8                                                        | Item 5                     | Item 18                                |
| 7208               | Consumption tax amount of taxable purchase related to taxable sales - Credit note     | Item 8, Item 9, Item14 (if Ratio \<0.95 & Individual method)  | Item 4                     | Item 22-Item 23 (at tax rates)         |
| 7210               | Consumption tax amount of taxable import - Credit note                                | Item 10                                                       | Item 4                     | Item 22-Item 23 (at tax rates)         |
| 7214               | Consumption tax amount of taxable purchase related to non-taxable sales - Credit note | Item 8, Item 9                                                | Item 4                     | Item 22-Item 23 (at tax rates)         |
| 7215               | Consumption tax amount of taxable purchase in common - Credit note                    | Item 8, Item 9, Item 15 (if Ratio \<0.95 & Individual method) | Item 4                     | Item 22-Item 23 (at tax rates)         |
| 8001               | Consumption tax amount of taxable sales                                               | \-                                                            | Item 2                     | Item 12-Item 16 (at tax rates)       |
| 8208               | Consumption tax amount of taxable purchase related to taxable sales                   | Item 8, Item 9, Item 14 (if Ratio \<0.95 & Individual method) | Item 4                     | Item 22-Item 23 (at tax rates)         |
| 8210               | Consumption tax amount of taxable import                                              | Item 10                                                       | Item 4                     | Item 22-Item 23 (at tax rates)         |
| 8214               | Consumption tax amount of taxable purchase related to non-taxable sales               | Item 8, Item 9                                                | Item 4                     | Item 22-Item 23 (at tax rates)         |
| 8215               | Consumption tax amount of taxable purchase in common                                  | Item 8, Item 9, Item 15 (if Ratio \<0.95 & Individual method) | Item 4                     | Item 22-Item 23 (at tax rates)         |
| 8308               | JP Debt                                                                               | \-                                                            | Item 6                     | Item 22-Item 23 (at tax rates)         |
| 8310               | JP Debt - Paid                                                                        | Item 25                                                       | \-                         | \-                                     |
| 9001               | Taxable sales - Credit note                                                           | \-                                                            | Item 5                     | \-                                     |
| 9202               | Tax-exempted sales - Credit note                                                      | Item 2                                                        | Item 15                    | \-                                     |
| 9203               | Non-taxable assets for export - Credit note                                           | Item 3                                                        | Item 15                    | \-                                     |
| 9206               | Non-taxable sales - Credit note                                                       | Item 6                                                        | Item 16                    | \-                                     |
| 9208               | Taxable purchase related to only taxable sales - Credit note                          | Item 8, Item 14 (if Ratio \<0.95 & Individual method)         | Item 4                     | Item 22-Item 23 (at tax rates)         |
| 9210               | Taxable import - Credit note                                                          | \-                                                            |                            |                                        |
| 9214               | Taxable purchase related to non-taxable sales - Credit note                           | Item 8                                                        | Item 4                     | Item 22-Item 23 (at tax rates)         |
| 9215               | Common taxable purchase in common - Credit note                                       | Item 8, Item 15 (if Ratio \<0.95 & Individual method)         | Item 4                     | Item 22-Item 23 (at tax rates)         |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
