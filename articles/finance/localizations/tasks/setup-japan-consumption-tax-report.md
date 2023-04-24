---
title: Setup Japan consumption tax report
description: This task walks you through setting up the system to support the Japan consumption tax report.
author: kfend
ms.date: 12/02/2019
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Japan
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: LedgerParameters, LedgerBadDebtAccounts_JP, OMLegalEntity, TaxTable
---
# Setup Japan consumption tax report

[!include [banner](../../includes/banner.md)]

This task walks you through setting up the system to support the Japan consumption tax report. In this task, you will modify General ledger parameters, a legal entity, sales tax reporting accounts and a sales tax code. 

This task was created using the demo data company JPMF.




## Enable the consumption tax report
1. Go to Tax > Setup > Parameters > General ledger parameters.
2. Click the Sales tax tab.
3. Expand the Japanese tax reporting section.
4. Select Yes in the Consumption tax reports field.

## Tax reporting accounts
1. Go to Tax > Setup > Sales tax > Tax reporting accounts.
2. Click Edit.
3. In the Bad debt field, specify the desired values.
    * Example: 84720  
4. In the Collected bad debt field, specify the desired values.
    * Example: 84710  

## Enter Japan reporting information for a legal entity
1. Go to Organization administration > Organizations > Legal entities.
2. Expand the Registration numbers section.
3. Click Edit.
4. In the Accounting personnel field, type a value.
5. In the Company representative field, type a value.

## Enter report setup information for a sales tax code
1. Go to Tax > Indirect taxes > Sales tax > Sales tax codes.
2. Use the Quick Filter to find records. For example, filter on the Sales tax code field with a value of 'JP Cons'.
3. Expand the Report setup section.
4. Click Edit.
    * Confirm the reporting codes were configured properly. 
    
  > [!NOTE] 
  > For setting reporting codes in sales tax codes you may use the table below.     
 
**Using reporting codes in Japanese sales tax report base items**

| **Reporting code** | **Reporting code name**                                                               | **Calculation Sheet column**                                  | **3 - (1) report column**  | **3 - (2) report**  **column**         |
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
