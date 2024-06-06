---
title: Configure system parameters to report sales tax books for Italy
description: Learn how to configure system parameters to report sales tax books for legal entities in Italy, including an outline on the address of the legal entity.
author: liza-golub
ms.author: egolub
ms.topic: article
ms.date: 03/04/2024
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 2016-11-30
ms.search.form: TaxYearlyCom_IT, TaxAuthority, TaxPeriod
ms.dyn365.ops.version: Version 1611
ms.assetid: af07d122-5694-4de6-96bf-7bf5478b0175
---

# Configure system parameters to report sales tax books for Italy

[!include [banner](../../includes/banner.md)]

This article explains how to configure system parameters to report sales tax books for legal entities in Italy.

As of Microsoft Dynamics 365 Finance version 10.0.39, the Italian sales tax books functionality supports reporting of Italian sales tax books in the [Electronic reporting (ER) tool](/dynamics365/fin-ops-core/dev-itpro/analytics/general-electronic-reporting). It also accommodates reporting for [multiple value-added tax (VAT) registrations](../global/emea-multiple-vat-registration-numbers.md).

## Address of the legal entity

The primary address of the legal entity must be in Italy. (Go to **Organization administration** \> **Organizations** \> **Legal entities** \> **Addresses** \> **Country/region**.)

As of Dynamics 365 Finance version 10.0.39, the ER format of Italian sales tax books can be generated from a legal entity that has a primary address that's outside Italy. In this scenario, you must set up an address and a tax registration number in Italy. For more information, see [Set up a VAT ID for a legal entity, customers, and vendors](../global/emea-multiple-vat-registration-numbers.md#set-up-a-vat-id-for-a-legal-entity-customers-and-vendors).

## <a id="number-sequences"></a>Number sequences and number sequence groups

Set up as many number sequences and number sequence groups as you require to cover all the required types of sales tax transactions. For more information about number sequences in Finance, see [Number sequences overview](/dynamics365/fin-ops-core/fin-ops/organization-administration/number-sequence-overview).

For continuous numbering of documents in Italian sales tax books, number sequences must be continuous, and they must have the **Company** scope.

In parameters of the **Accounts receivable**, **Accounts payable**, and **Project management and accounting** modules in Finance, you can set up number sequence groups to allocate specific number sequences to specific customers or vendors.

### Accounts receivable parameters

To set up number sequence groups in Accounts receivable parameters, follow these steps.

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2. On the **Number sequence** tab, in the **Reference** column, select **Free text invoice**.
3. Select the **Group** button above the grid.
4. On the **Number sequence groups** page, define the required number sequence groups. On the **References** FastTab, associate each number sequence that you previously set up with the appropriate area. The **Sales tax book section** column shows the sales tax book section that's associated with the selected number sequence when you set up [sales tax book sections](emea-ita-sales-tax-books.md#sales-tax-book-sections).
5. For vouchers to follow the number sequences of the related invoices and credit notes, you must select the **Reuse numbers** checkbox when you define the number sequences for those invoices and credit notes. For example, on the **Accounts receivable parameters** page, on the **Number sequences** tab, select the **Reuse numbers** checkbox for **Free text invoice voucher** to synchronize number allocation for free text invoice vouchers and free text invoices.

### Accounts payable parameters

To set up number sequence groups in Accounts payable parameters, follow these steps.

1. Go to **Accounts payable** \> **Setup** \> **Accounts payable parameters**.
2. On the **Number sequence** tab, in the **Reference** column, select **Internal invoice**.
3. Select the **Group** button above the grid.
4. On the **Number sequence groups** page, define the required number sequence groups. On the **References** FastTab, associate each number sequence that you previously set up with the appropriate area. The **Sales tax book section** column shows the sales tax book section that's associated with selected number sequence when you set up [sales tax book sections](emea-ita-sales-tax-books.md#sales-tax-book-sections).
5. For vouchers to follow the number sequences of the related invoices and credit notes, you must select the **Reuse numbers** checkbox when you define the number sequences for those invoices and credit notes.

### Project management and accounting parameters

To set up number sequence groups in Project management and accounting parameters, follow these steps.

1. Go to **Project management and accounting** \> **Setup** \> **Project management and accounting parameters**.
2. On the **Number sequence** tab, in the **Reference** column, select **Invoice voucher**.
3. Select the **Group** button above the grid.
4. On the **Number sequence groups** page define the required number sequence groups. On the **References** FastTab, associate each number sequence that you previously set up with the appropriate area. The **Sales tax book section** column shows the sales tax book section that's associated with the selected number sequence when you set up [sales tax book sections](emea-ita-sales-tax-books.md#sales-tax-book-sections).
5. For vouchers to follow the number sequences of the related invoices and credit notes, you must select the **Reuse numbers** checkbox when you define the number sequences for those invoices and credit notes.

## Journal names

Set up the required journal names.

To set up journal names for General ledger, go to **General ledger** \> **Journal setup** \> **Journal names**.

To set up journal names for Project management and accounting parameters, go to **Project management and accounting** \> **Setup** \> **Journals** \> **Journal names**.

The following table shows the recommended setup of journal name parameters for legal entities that report Italian sales tax books.

| Parameter | Value |
|-----------|-------|
| Number allocation at posting | Yes |
| Italian sales tax book | <ul><li><strong>Not included</strong> – Select this value for invoices and credit notes that come from countries/regions that are outside the European community.</li><li><strong>Purchase</strong> – Select this value for purchase invoices and credit notes.</li><li><strong>Sales</strong> – Select this value for sales invoices and credit notes.</li><li><strong>Empty</strong> – Select this value for all other types of transactions.</li></ul><p>In some cases, the <strong>Italian sales tax book</strong> field is automatically set based on the value of the <strong>Journal type</strong> field. For example, if the <strong>Journal type</strong> field is set to <strong>Invoice register</strong>, the <strong>Italian sales tax book</strong> field is set to <strong>Purchase</strong> by default.</p> |
| Voucher series | Select a number sequence that you set up in the [Number sequences and number sequence groups](#number-sequences) section of this article. |

## General ledger parameters

The Italian localization doesn't support corrections to the Italian sales tax payment report for a sales tax period that's already settled. Therefore, on the **General ledger parameters** page, on the **Sales tax** tab, in the **Special report** section, set the **Include corrections** option to **No**.

## Company, vendor, and customer fiscal codes and tax registration numbers

> [!NOTE]
> When [Tax Calculation service](../global/global-tax-calcuation-service-overview.md) is used, and functionality for [multiple VAT registration numbers](../global/emea-multiple-vat-registration-numbers.md) is enabled, you must set up [registration IDs](../europe/emea-registration-ids.md) to define the tax exempt number (tax registration number) of your legal entity, customers, and vendors, as described in [Set up a VAT ID for a legal entity, customers, and vendors](../global/emea-multiple-vat-registration-numbers.md#set-up-a-vat-id-for-a-legal-entity-customers-and-vendors).

### Company fiscal code and tax registration number

| Field | Description | Page \> FastTab |
|-------|-------------|-----------------|
| Tax registration number | Enter the tax registration number for the legal entity in Italy. | <p>Legal entities \> Tax registration</p><p>See the note earlier in this section for information about the setup in scenarios that involve multiple VAT registration numbers.</p> |
| Fiscal Code | Enter the fiscal code from the legal entity registration in Italy. | Legal entities \> Registration numbers |

### Customer fiscal code and tax registration number

| Field | Description | Page \> FastTab |
|-------|-------------|-----------------|
| Tax exempt number | Enter the tax exempt number for VAT declaration. | <p>Account receivable \> Customers \> All customers \> Invoice and delivery</p><p>See the note earlier in this section for information about the setup in scenarios that involve multiple VAT registration numbers.</p> |
| Fiscal code | Enter the fiscal code for the customer. | Account receivable \> Customers \> All customers \> Invoice and delivery |

### Vendor fiscal code and tax registration number

| Field | Description | Page \> FastTab |
|-------|-------------|-----------------|
| Tax exempt number | Enter the tax exempt number for VAT declaration. | <p>Account payable \> Vendors \> All vendors \> Invoice and delivery</p><p>See the note earlier in this section for information about the setup in scenarios that involve multiple VAT registration numbers.</p> |
| Fiscal code | Enter the fiscal code for the vendor. | Account payable \> Vendors \> All vendors \> Invoice and delivery |

## Sales tax authority

To set up a sales tax authority, follow these steps.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax authorities**.
2. Select **New** to create a record, and specify the parameters of the tax authority. For more information, see [Set up sales tax authorities](../../general-ledger/tasks/set-up-sales-tax-authorities.md).
3. In the **Report layout** field, select **Default**.
4. In the **Vendor account** field, select a vendor account that corresponds to the tax authority that has a primary address in Italy.
5. To print a blank page on the sales tax payment report for periods that have no transactions, select the **Print blank page with no transactions** option.
6. To use a separate tax book to number summary sections, select the **Separate summary register** checkbox.
7. In the **Account gain** and **Account loss** fields, specify main accounts. These main accounts are used to automatically post rounding results during the sales tax settlement procedure.

## Sales tax settlement periods

According to Italian legislation, rules apply to settlement periods. For example, after the settlement period is closed, no change is allowed. You're required to report whether the settlement refers to the last period of the fiscal year. To determine whether the settlement period refers to a year closing, view the settlement period status.

To set up sales tax settlement periods, follow these steps.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax settlement periods**.
2. Select **New** to create a record, and specify the parameters of the sales tax settlement period. For more information, see [Set up sales tax settlement periods](../../general-ledger/tasks/set-up-sales-tax-settlement-periods.md).
3. To attach the generated Italian sales tax book ER format to the **Sales tax book status** records, select the **Attach report to Sales tax book status** checkbox.
4. To report amounts in the Italian sales tax book ER format in the tax currency, select the **Report in tax currency** checkbox.

In legal entities that have an address in Italy, the following columns are added for period intervals on the **Sales tax settlement periods** page.

| Field | Description |
|-------|-------------|
| Closed | A value that indicates whether the interval of the sales tax settlement period has been settled and closed. |
| Last period | Select this option if the period is the last period in a sales tax year. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
