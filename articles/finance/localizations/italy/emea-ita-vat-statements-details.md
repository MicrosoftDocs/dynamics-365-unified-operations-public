---
title: Configure system parameters to report Sales tax books
description: This article explains how to configure system parameters to report Sales tax books for legal entities in Italy.
author: liza-golub
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Italy
ms.author: egolub
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 269664
ms.assetid: af07d122-5694-4de6-96bf-7bf5478b0175
ms.search.form: TaxYearlyCom_IT, TaxAuthority, TaxPeriod
---

# Configure system parameters to report Sales tax books for Italy

[!include [banner](../../includes/banner.md)]

This article explains how to configure system parameters to report Sales tax books for legal entities in Italy.

As of 10.0.39 version of Dynamics 365 Finance, the **Italian sales tax books** functionality supports reporting of Italian sales tax book in [Electronic reporting (ER) tool](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting) and accomodates reporting for [multiple VAT registrations](../global/emea-multiple-vat-registration-numbers.md).

## Set up a company, vendors and customers fiscal code and tax registration number

> [!NOTE]
> When [Tax Calculation service](../global/global-tax-calcuation-service-overview.md) is used and [Multiple VAT registration numbers](../global/emea-multiple-vat-registration-numbers.md) functionality is enabled, you must set up [**Registration IDs**](../europe/emea-registration-ids.md) to define **Tax exempt number** (Tax registration number) of your legal entity, customers and vendors as it is described in the [Set up a VAT ID for a legal entity, customers, and vendors](../global/emea-multiple-vat-registration-numbers.md#set-up-a-vat-id-for-a-legal-entity-customers-and-vendors) section of [Multiple VAT registration numbers](../global/emea-multiple-vat-registration-numbers.md) guidance. 

### Company fiscal code and tax registration number

| **Field**        | **Description**                                                    | **Page > FastTab** |
|------------------|--------------------------------------------------------------------|--------------------|
| **Tax registration number** | Enter the tax registration number for the legal entity in Italy |  Legal entities > Tax registration <br> See *Note* above in this section for reference on setup in **Multiple VAT registration numbers** scenario. |
| **Fiscal Code**  | Enter the fiscal code from the legal entity registration in Italy. | Legal entities > Registration numbers |

### Customers fiscal code and tax registration number

| **Field**             | **Description**                                        | **Page > FastTab** |
|-----------------------|--------------------------------------------------------|--------------------|
| **Tax exempt number** | Enter the tax exempt number for VAT declaration.       | Account receivable > Customers > All customers > Invoice and delivery <br> See *Note* above in this section for reference on setup in **Multiple VAT registration numbers** scenario. |
| **Fiscal code**       | Enter the fiscal code for this customer.               | Account receivable > Customers > All customers > Invoice and delivery |

### Vendors fiscal code and tax registration number

| **Field**             | **Description**                                      | **Page > FastTab** |
|-----------------------|------------------------------------------------------|--------------------|
| **Tax exempt number** | Enter the tax exempt number for VAT declaration.     | Account payable > Vendors > All vendors > Invoice and delivery <br> See *Note* above in this section for reference on setup in **Multiple VAT registration numbers** scenario. |
| **Fiscal code**       | Enter the fiscal code for this vendor.               | Account payable > Vendors > All vendors > Invoice and delivery |

## Sales tax authority

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax authorities**.
2. Select **New** to create a record, and specify the parameters of the tax authority. For more information, see [Set up sales tax authorities](../../general-ledger/tasks/set-up-sales-tax-authorities.md).
3. In the **Report layout** field, select **Default**.
4. In the **Vendor account** field, select a vendor account that corresponds to the tax authority with primary address in Italy.
5. Select **Print blank page with no transactions** to print blank page on sales tax payment report for periods that have no transactions.
6. Select **Separate summary register** checkbox to use a separate tax book to number summary sections.
7. Specify main accounts in **Account gain** and **Account loss** fields. These main accounts are used during sales tax settlement procedure to automatically post rounding result. 

## Sales tax settlement periods

Per Italian legislation, rules apply to settlement periods. For example, after the settlement period is closed, no change is allowed. 
You are required to report if the settlement refers to the last period on the fiscal year. 
View the settlement period status and report if it refers to a year closing. 

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax settlement periods**.
2. Select **New** to create a record, and specify the parameters of the sales tax settlement period. For more information, see [Set up sales tax settlement periods](../../general-ledger/tasks/set-up-sales-tax-settlement-periods.md).

In legal entities with address in Italy, on **Sales tax settlement periods** page there are following columns added for **Period intervals**.

|    <strong>Field</strong>    |                                   <strong>Description</strong>                                    |
|------------------------------|---------------------------------------------------------------------------------------------------|
|   <strong>Closed</strong>    | Indicates if the interval of the sales tax settlement period has been settled and closed. |
| <strong>Last period</strong> |             Select this option if the period is the last period in a sales tax year.              |



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
