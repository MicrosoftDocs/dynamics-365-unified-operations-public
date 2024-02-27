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

As of 10.0.39 version of Dynamics 365 Finance, the **Italian sales tax books** functionality supports reporting of Italian sales tax book in [Electronic reporting (ER) tool](/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting) and accommodates reporting for [multiple VAT registrations](../global/emea-multiple-vat-registration-numbers.md).

## Address of the legal entity

The primary address of the legal entity must be in Italy. (Click **Organization administration** > **Organizations** > **Legal entities** > **Addresses** > **Country/region**.)

As of 10.0.39 version of Dynamics 365 Finance, ER format of Italian sales tax books can be generated from a legal entity with primary address outside of Italy. In this scenario, you must set up address and tax registration number in Italy. For more information, see [Set up a VAT ID for a legal entity, customers, and vendors](../global/emea-multiple-vat-registration-numbers.md#set-up-a-vat-id-for-a-legal-entity-customers-and-vendors) section of [Multiple VAT registration numbers](../global/emea-multiple-vat-registration-numbers.md) guidance.

## <a id="number-sequences"></a> Number sequences and number sequence groups 

Set up as many number sequences and number sequence groups as you require to cover all the required types of sales tax transactions. For more information about number sequences in Finance, see [Number sequences overview](/dynamics365/fin-ops-core/fin-ops/organization-administration/number-sequence-overview).

For continuous numbering of document in Italian sales tax books, number sequences must be continuous and must have <strong>Company</strong> scope.

In parameters of **Accounts receivable**, **Accounts payable** and **Project management and accounting** modules of Finance you can set up number sequence groups to allocate specific number sequences to specific customers or vendors.

### Accounts receivable parameters

1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**, select **Number sequence** tab.
2. Select **Free text invoice** in the **Reference** column.
3. Click on **Group** button on the top of the table.
4. On the **Number sequence groups** page define necessary number sequence groups and associate previously set up number sequences with respective **Area** on References FastTab. **Sales tax book section** column displays the Sales tax book section that is associated with selected Number sequence when you set up [Sales tax book sections](emea-ita-sales-tax-books.md#sales-tax-book-sections).
5. For vouchers to follow the number sequences of the related invoices and credit notes, you must select the **Reuse numbers** check box when you define the number sequences for those invoices and credit notes. For example, on the **Accounts receivable parameters** page, on the **Number sequences** tab, select the **Reuse numbers** check box for **Free text invoice voucher** to synchronize number allocation for free text invoice vouchers and free text invoices.

### Accounts payable parameters

1. Go to **Accounts payable** > **Setup** > **Accounts payable parameters**, select **Number sequence** tab.
2. Select **Internal invoice** in the **Reference** column.
3. Click on **Group** button on the top of the table.
4. On the **Number sequence groups** page define necessary number sequence groups and associate previously set up number sequences with respective **Area** on References FastTab. **Sales tax book section** column displays the Sales tax book section that is associated with selected Number sequence when you set up [Sales tax book sections](emea-ita-sales-tax-books.md#sales-tax-book-sections).
5. For vouchers to follow the number sequences of the related invoices and credit notes, you must select the **Reuse numbers** check box when you define the number sequences for those invoices and credit notes. 

### Project management and accounting parameters

1. Go to **Project management and accounting** > **Setup** > **Project management and accounting parameters**, select **Number sequence** tab.
2. Select **Invoice voucher** in the **Reference** column.
3. Click on **Group** button on the top of the table.
4. On the **Number sequence groups** page define necessary number sequence groups and associate previously set up number sequences with respective **Area** on References FastTab. **Sales tax book section** column displays the Sales tax book section that is associated with selected Number sequence when you set up [Sales tax book sections](emea-ita-sales-tax-books.md#sales-tax-book-sections).
5. For vouchers to follow the number sequences of the related invoices and credit notes, you must select the **Reuse numbers** check box when you define the number sequences for those invoices and credit notes. 

## Journal names

Set up the required journal names. 

To set up journal names for **General ledger**, go to <strong>General Ledger</strong> &gt; <strong>Journal setup</strong> &gt; <strong>Journal names</strong>.

To set up journal names for **Project management and accounting parameters**, go to <strong>Project management and accounting</strong> &gt; <strong>Setup</strong> &gt; <strong>Journals</strong> &gt; <strong>Journal names</strong>.

The following table represents recommended setup of parameters of journal names for legal entities reporting Italian sales tax books:

| Parameter | Value |
|-----------|-------|
| **Number allocation at posting** | Yes |
| **Italian sales tax book** | **- Not included** – Select this value for invoices and credit notes that come from countries/regions that are outside the European community. <br> **- Purchase** – Select this value for purchase invoices and credit notes.<br> **- Sales** – Select this value for sales invoices and credit notes.<br> **- Empty** – Select this value for all other types of transactions. <br> In some cases, the **Italian sales tax book** field is set automatically, based on the **Journal type** value. For example, if the **Journal type** field is set to **Invoice register**, the **Italian sales tax book** field is set to **Purchase** by default. |
| **Voucher series** | Select number sequence previously set up in [Number sequences and number sequence groups](#number-sequences) section. |

## General ledger parameters

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
2. Select **New** to create a record and specify the parameters of the tax authority. For more information, see [Set up sales tax authorities](../../general-ledger/tasks/set-up-sales-tax-authorities.md).
3. In the **Report layout** field, select **Default**.
4. In the **Vendor account** field, select a vendor account that corresponds to the tax authority with primary address in Italy.
5. Select **Print blank page with no transactions** to print blank page on sales tax payment report for periods that have no transactions.
6. Select **Separate summary register** checkbox to use a separate tax book to number summary sections.
7. Specify main accounts in **Account gain** and **Account loss** fields. These main accounts are used during sales tax settlement procedure to automatically post rounding result. 

## Sales tax settlement periods

Per Italian legislation, rules apply to settlement periods. For example, after the settlement period is closed, no change is allowed. 
You are required to report if the settlement refers to the last period of the fiscal year. 
View the settlement period status and report if it refers to a year closing. 

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax settlement periods**.
2. Select **New** to create a record and specify the parameters of the sales tax settlement period. For more information, see [Set up sales tax settlement periods](../../general-ledger/tasks/set-up-sales-tax-settlement-periods.md).
3. Select **Attach report to Sales tax book status** checkbox to attach generated Italian sales tax book ER to the **Sales tax book status** records.
4. Select **Report in tax currency** checkbox to report amounts in Italian sales tax book ER in tax currency.

In legal entities with address in Italy, on **Sales tax settlement periods** page there are following columns added for **Period intervals**.

|    <strong>Field</strong>    |                                   <strong>Description</strong>                                    |
|------------------------------|---------------------------------------------------------------------------------------------------|
|   <strong>Closed</strong>    | Indicates if the interval of the sales tax settlement period has been settled and closed. |
| <strong>Last period</strong> |             Select this option if the period is the last period in a sales tax year.              |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
