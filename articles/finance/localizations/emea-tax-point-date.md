---
# required metadata

title: Tax point date (Date of VAT register)
description: This topic provides information about how to indicate when the tax date is different from the transaction date regarding VAT registration.
author: LizaGolub
manager: AnnBe
ms.date: 012/14/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: United Kingdom
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2019-09-06
ms.dyn365.ops.version: AX 10.0.6

---

# Tax point date (Date of VAT register)

[!include [banner](../includes/banner.md)]

The **tax point date** for a transaction is the date on which the transaction occurs for VAT purposes. Use the **Date of VAT register** feature when the tax point date is different from the transaction date and it must be noted. To specify the tax point date, use the **Date of VAT register** field.

The **Date of VAT register** field is shared globally and can be enabled in legal entities with a primary address in any country.

## Activate the Date of VAT register feature

The **Date of VAT register** feature is enabled in the **Feature management** workspace.

![Feature management workspace](./media/date-of-vat-activating.png)

After the feature is enabled, you can also define tax point transactions dates by using the **Date of VAT register** field in all of the legal entities in your application.

The **Date of VAT register** field appears on more than 20 pages. These pages include journals, sales orders, purchase orders, free-text invoices, vendor invoice journals, and project invoices. When you update or post the documents, all taxes are posted by using the corresponding date of the VAT register. The date is included on pages such as the Customer and Vendor invoice journals pages.

The **Date of VAT register** field is also included in the following reports:

- **Specification** report (**Tax** \> **Inquiries and reports** \> **Sales tax reports** \> **Specification**)
- **Sales tax transactions** report (**Tax** \> **Inquiries and reports** \> **Sales tax reports** \> **Sales tax transactions**)
- **Sales tax transactions - details** report (**Tax** \> **Inquiries and reports** \> **Sales tax reports** \> **Sales tax transactions – details**)
- **Sales tax specification by ledger transaction** report (**Tax** \> **Inquiries and reports** \> **Sales tax reports** \> **Sales tax specification by ledger transaction**)

## Auto-fill the **Date of VAT register** field

You can use the functionality in the **Date of VAT register** feature to auto-fill the **Date of VAT register** field. To set this up, set the **Date of VAT register filling** parameter on the **Sales tax groups** page.

![Date of VAT register filling parameter on the Sales tax groups page](./media/date-of-vat-filling.png)

When you create an invoice, the **Date of VAT register** field is automatically filled in. One of the following methods will be added based on the selection in the **Date of VAT register filling** field:

- **Manually** – No value will be defined. You can manually define the value before you post the invoice.
- **Document date** – The value will be defined automatically on the date that the invoice is updated.
- **Posting date** - The value will be the date that the invoice is posted.
- **Last delivery date** - The date of the last packing slip (for a sales order) or product receipt (for a purchase order) for the invoice.
- **Customize** – The value can be calculated based on the posting date or the document date. The date of VAT register is determined by adding a number of periods (Day, Month, or Year) to the posting date or document date. The option is available under the **Date of VAT register filling: new calculation choice** feature in the **Feature management** workspace starting in version 10.0.17.

## Filling the **Date of VAT register** field after the invoice is posted

If for some reason an invoice is posted and the **Date of VAT register** field is empty, it is still possible to fill it in. To do this, go to **Tax** \> **Periodic tasks** \> **VAT register transactions**. The **VAT register transactions** page represents sales tax transactions where the field **Date of VAT register** is empty. Select one record to update, or select multiple records by using the filter function. To define the value for the field, select **Date of VAT register** on the Action Pane, and specify the value in the dialog. The updated records will be automatically filtered out from the list of records on the **VAT register transactions** page.

