---
title: Tax point date (Date of VAT register)
description: Learn how to indicate when the tax date is different from the transaction date regarding VAT registration for the UK in Microsoft Dynamics 365 Finance.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/04/2025
ms.reviewer: johnmichalak
ms.search.region: United Kingdom
ms.search.validFrom: 2020-09-06
---

# Tax point date (Date of VAT register)

[!include [banner](../../includes/banner.md)]

This article explains how to indicate when the tax date is different from the transaction date regarding VAT registration for the UK in Microsoft Dynamics 365 Finance.

The *tax point date* for a transaction is the date on which the transaction occurs for VAT purposes. Use the Date of VAT register feature when the tax point date is different from the transaction date and it must be noted. To specify the tax point date, use the **Date of VAT register** field.

The **Date of VAT register** field is shared globally and can be enabled in legal entities with a primary address in any country/region.

## Activate the Date of VAT register feature

The **Date of VAT register** feature is enabled in the **Feature management** workspace.

![Feature management workspace.](../media/date-of-vat-activating.png)

After the feature is enabled, you can also define tax point transactions dates by using the **Date of VAT register** field in all of the legal entities in your application.

The **Date of VAT register** field appears on more than 20 pages. These pages include journals, sales orders, purchase orders, free-text invoices, vendor invoice journals, and project invoices. When you update or post the documents, all taxes are posted by using the corresponding date of the VAT register. The date is included on pages such as the Customer and Vendor invoice journals pages.

The **Date of VAT register** field is also included in the following reports:

- **Specification** report (**Tax** \> **Inquiries and reports** \> **Sales tax reports** \> **Specification**)
- **Sales tax transactions** report (**Tax** \> **Inquiries and reports** \> **Sales tax reports** \> **Sales tax transactions**)
- **Sales tax transactions - details** report (**Tax** \> **Inquiries and reports** \> **Sales tax reports** \> **Sales tax transactions – details**)
- **Sales tax specification by ledger transaction** report (**Tax** \> **Inquiries and reports** \> **Sales tax reports** \> **Sales tax specification by ledger transaction**)

## Auto-fill the **Date of VAT register** field

You can use the functionality in the **Date of VAT register** feature to auto-fill the **Date of VAT register** field. To set this up, set the **Date of VAT register filling** parameter on the **Sales tax groups** page.

![Date of VAT register filling parameter on the Sales tax groups page.](../media/date-of-vat-filling.png)

When you create an invoice, the **Date of VAT register** field is automatically filled in. One of the following methods will be added based on the selection in the **Date of VAT register filling** field:

- **Manually** – No value will be defined. You can manually define the value before you post the invoice.
- **Document date** – The value will be defined automatically on the date that the invoice is updated.
- **Posting date** - The value will be the date that the invoice is posted.
- **Last delivery date** - The date of the last packing slip (for a sales order) or product receipt (for a purchase order) for the invoice. This option is not applicable in scenarios where a posted invoice is based on multiple sales orders.”
- **Customize** – The value can be calculated based on the posting date or the document date. The date of VAT register is determined by adding a number of periods (Day, Month, or Year) to the posting date or document date. The option is available under the **Date of VAT register filling: new calculation choice** feature in the **Feature management** workspace starting in version 10.0.17.

## Setting the Date of VAT register field after the invoice is posted

If for some reason an invoice is posted and the **Date of VAT register** field is empty, it is still possible to enter a value in the field. 

To enter a value in the **Date of VAT register** field after posting, follow these steps: 

1. In Dynamics 365 Finance, go to the **Tax** \> **Periodic tasks** \> **VAT register transactions** page, which represents sales tax transactions where the **Date of VAT register** field is empty. 
1. Select one record to update, or select multiple records by using the filter function. 
1. To define the value for the field, select **Date of VAT register** on the Action Pane, and enter the value in the dialog. The updated records are automatically filtered out from the list of records on the **VAT register transactions** page.

## Sales tax transactions extension consistency check

The **Date of VAT register** field is stored in a TaxTrans_W table. This table is an extension of the TaxTrans table. When a company enables the **Date of VAT register** feature, data source queries on some pages in the system start to work differently. Those queries now join the TaxTrans_W table. Therefore, users might not be able to see tax transactions that were posted in an earlier period. This issue occurs because the TaxTrans_W table wasn't previously used, and therefore there are no corresponding transactions in the table.

To help avoid this issue, you can run the **Sales tax transactions extension** consistency check. 

To run the **Sales tax transactions extension** consistency check, follow these steps:

1. Go to **System administration** \> **Periodical tasks** \> **Database** \> **Consistency check**. 
1. In the **Consistency check** dialog, expand **Program** \> **General ledger** \> **Sales tax**, and then select the **Sales tax transactions extension** checkbox. You don't have to select the parent checkboxes if you only want to run the **Sales tax transactions extension** consistency check.

    ![Consistency check dialog with Sales tax transactions extension checkbox highlighted.](../media/date-of-vat-consistency-check.png)

1. When you run the **Sales tax transactions extension** consistency check, set the following options:
    - **Check**: Determine whether any transactions are missing in the TaxTrans_W table. The system will notify you about the number of transactions in the TaxTrans table that lack corresponding records in the TaxTrans_W table.
    - **Fix**: Compensate for missing records in the TaxTrans_W table. The system inserts corresponding records into the TaxTrans_W table. Sales tax transactions that were posted in previous periods are again seen everywhere in the system. 
1. In the **Consistency check** dialog, in the **From date** field, ensure that you select the correct date. If you want to recover all the tax transactions in the system, leave the **From date** field blank.

The **Sales tax transactions extension** consistency check is available in build version 10.0.234.21 and later for version 10.0.6 of the application, and for version 10.0.7 and later. In these versions, it's available only when the Date of VAT register feature is turned on in the **Feature management** workspace.

## Sales tax settlement by date of VAT register

Starting in the 10.0.25 release, the **Sales tax settlement and reporting by date of VAT register** feature is available. With this feature enabled, you can settle and report sales tax by using the VAT register date. When this feature is enabled, you can set the **Date of VAT register** option to **Yes** on the **General ledger parameters** page on the **Sales tax** tab. The periodic settlement will collect sales tax transaction by the date of VAT register instead of the transaction date.

![Date of VAT register option is ON in General ledger parameters.](../media/GLParameters-DateOfVATRegister.png)

> [!NOTE]
> - To enable the **Sales tax settlement and reporting by date of VAT register** feature, the **Date of VAT register** feature should be enabled in the **Feature management** workspace.
> - To disable the **Sales tax settlement and reporting by date of VAT register** feature, ensure the **Date of VAT register** checkbox on the **General ledger parameters** page is set to **No**. A warning displays if the checkbox is active for some legal entities.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
