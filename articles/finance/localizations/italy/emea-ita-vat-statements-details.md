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

## Address of the legal entity

The primary address of the legal entity must be in Italy. (Click **Organization administration** > **Organizations** > **Legal entities** > **Addresses** > **Country/region**.)

As of 10.0.39 version of Dynamics 365 Finance, ER format of Italian sales tax book can be generated from a legal entity with primary address outside of Italy. In this scenario, you must set up address and tax registration number in Italy. For more information, see [Set up a VAT ID for a legal entity, customers, and vendors](../global/emea-multiple-vat-registration-numbers.md#set-up-a-vat-id-for-a-legal-entity-customers-and-vendors) section of [Multiple VAT registration numbers](../global/emea-multiple-vat-registration-numbers.md) guidance.

## Number sequences

Set up as many number sequences as you require to cover all the required types of sales tax transactions. (Click <strong>Organization administration</strong> &gt; <strong>Number sequences</strong> &gt; <strong>Number sequences</strong>.) All these number sequences must be continuous and must have <strong>Company</strong> scope.

## Journal names

Set up the required journal names. (Click <strong>General Ledger</strong> &gt; <strong>Journal setup</strong> &gt; <strong>Journal names</strong> or <strong>Project management and accounting</strong> &gt; <strong>Setup</strong> &gt; <strong>Journals</strong> &gt; <strong>Journal names</strong>.) On the <strong>General</strong> FastTab, in the <strong>Sales tax</strong> section, in the <strong>Italian sales tax book</strong> field, specify one of the following values:

<ul>
<li><strong>Not included</strong> – Select this value for invoices and credit notes that come from countries/regions that are outside the European community.</li>
<li><strong>Purchase</strong> – Select this value for purchase invoices and credit notes.</li>
<li><strong>Sales</strong> – Select this value for sales invoices and credit notes.</li>
<li><strong>Empty</strong> – Select this value for all other types of transactions.</li>
</ul>

In some cases, the <strong>Italian sales tax book</strong> field is set automatically, based on the <strong>Journal type</strong> value. For example, if the <strong>Journal type</strong> field is set to <strong>Invoice register</strong>, the <strong>Italian sales tax book</strong> field is set to <strong>Purchase</strong> by default.

## Module parameters

For vouchers to follow the number sequences of the related invoices and credit notes, you must select the <strong>Reuse numbers</strong> check box when you define the number sequences for those invoices and credit notes. You can find this check box on the <strong>Number sequences</strong> tab of the following pages:

<ul>
<li><strong>Accounts receivable parameters</strong></li>
<li><strong>Accounts payable parameters</strong></li>
<li><strong>Project management and accounting parameters</strong></li>
</ul>

For example, on the <strong>Accounts receivable parameters</strong> page, on the <strong>Number sequences</strong> tab, select the <strong>Reuse numbers</strong> check box for <strong>Free text invoice voucher</strong> to synchronize number allocation for free text invoice vouchers and free text invoices.

In the Italian localization, corrections to the Italian sales tax payment report for an already settled sales tax period are not supported. So on the <strong>General ledger parameters</strong> page, on the <strong>Sales tax</strong> tab, set the Special report **Include corrections** option to **NO**.

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
