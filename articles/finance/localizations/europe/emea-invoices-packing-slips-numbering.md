---
title: Invoice and packing slip numbering for Latvia and Lithuania
description: Learn how to set up number sequences for invoices and packing slips, and how to set up self-numbering ranges for documents.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Latvia, Lithuania
ms.search.validFrom: 2016-11-30
ms.search.form: LtInvoiceAutoNumberingGroups, LtInvoiceAutonumberingTable, NumberSequenceTableListPage
---

# Invoice and packing slip numbering for Latvia and Lithuania

[!include [banner](../../includes/banner.md)]

This article explains how to set up number sequences for invoices and packing slips, and how to set up self-numbering ranges for documents.

For legal entities that have a primary address in Latvia or Lithuania, you can set up conditional numbering for invoices and packing slips that is based on the assigned user or user group.

## Set up number sequences for invoices and packing slips

You can set up unique document number sequences for master data records and transaction records. If the tax authorities for your country or region assign your organization a specific document number sequence or format, you can associate the number sequence with a document type. You can assign each document number sequence to a user or user group. In this way, only the designated user or user group can assign the numbers in the series to a document. Set up number sequences for invoices and packing slips on the **Invoice numbering setup** page. (Select **Organization administration** > **Number sequences** > **Invoice numbering setup**.) Use the information in the following table to complete the fields on the **Invoice numbering setup** page.

| Field | Description |
|-------|-------------|
| Numbering | Enter the prefix for the document number sequence. |
| Module | Select the module that uses the number series. The module that you select determines the options that are available in the **Type** field. For customer invoices and customer packing slips, select **Sales** in this field. |
| Number sequence code | Select the number sequence code for the data area where the number series applies. |
| Type | Select whether the number sequence applies to invoices or packing slips. |
| Account code | Select how the number series applies to invoices. The following options are available: **Table** – The number series is available only to the user that is selected in the **Code** field. **Group** – The number series is available to the user group that is selected in the **Code** field. **All** – The number series is available to all users. |
| Code | Select the ID of the user or user group that the number series is assigned to for invoice numbering. |
| Last date | The date that the number series was last updated. |
| Continue | Select this option to search for number series that are assigned to the selected user or user group. |

## Set up document self-numbering ranges

You can assign specific number sequences to invoices and packing slips that you generate in the **Accounts receivable**, **Accounts payable**, **Inventory management**, and **Project management and accounting** modules. You can also specify individual number sequences for different users and user groups, customer groups and vendor groups, or warehouses. To set up number sequences for customer invoices and vendor invoices, use the **Counters management** page. (Select **Organization administration** > **Number sequences** > **Counters management**.) You can define the number sequence by user or user group, or for specific customer groups and vendor groups. Use the following table to complete the fields on the **Counters management** page.

| Field          | Description                                                                                                                                     |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| Module         | Select the module that the selected number sequence applies to.                                                                                 |
| Account code   | Select whether the number sequence code applies to all records in the selected module or to a specific group in the module.                     |
| Code           | Select the code for the selected module. **Note:** The **Code** field is available only if **Group** is selected in the **Account code** field. |
| Type           | Select the type of document to number: **Invoice** or **Packing slip**.                                                                         |
| Auto numbering | Select this option to automatically assign a number to a document. You can manually select or clear this option for individual documents.       |

For information about how to manually number invoices and packing slips, see [Edit invoice IDs on sales orders for Eastern Europe](emea-edit-invoice-id-sales-orders.md).

## Affected processes

The system updates the headers of the following documents with invoice and packing slip numbering:

- Sales orders
- Purchase orders
- Free text invoices
- Project invoice proposals

When you post the following documents, you can select a specific number sequence in the **Numbering** field:

- Sales packing slip
- Sales posting invoice
- Purchasing posting product receipt
- Purchasing vendor invoices
- Post project invoice proposals
- Post free text invoice

Additionally, the following forms include the **Documents to update** field:

- Purchasing Vendor invoices form
- Sales Packing slip posting form
- Sales Posting invoice form
- Purchasing Posting product receipt form

The **Documents to update** field affects the **Document status** field in **Packing slip journal** and **Invoice Journal**. When you create a **Packing slip**, the system sets the **Document status** field to **None**. If you select any **Packing slip** in the **Documents to update** field, the system sets its **Document status** to **Broken** and sets the **Document status** of the related **Packing slip** to **Canceled**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
