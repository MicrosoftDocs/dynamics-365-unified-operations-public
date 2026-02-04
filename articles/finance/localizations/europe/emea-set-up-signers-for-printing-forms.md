---
title: Set up signers for print forms
description: For legal entities in Czech Republic, Estonia, Hungary, Lithuania, Latvia, Poland, and Russia, you can set up signers and titles for customers and vendors.
author: kfend
ms.author: johnmichalak
ms.topic: article
ms.date: 12/05/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
---

# Set up signers for print forms

[!include [banner](../../includes/banner.md)]

For legal entities in the Czech Republic, Estonia, Hungary, Lithuania, Latvia, Poland, and Russia, you can set up signers and titles for customers and vendors that print documents such as invoices and cash orders.

## Set up default values

To set up signers for the documents that a company prints, use the **Officials** page. You can set up signers and their titles both for the company and for customers or vendors, depending on the document type. The following table describes the tabs on the **Officials** page.

| Tab | Description |
|-----|-------------|
| General | Add positions and related information for signers (Director and Chief accountant) who can sign print documents of all types. |
| Ledger | Add the position and related information for signers who can sign the following internal financial documents that are related to cash flow:<ul><li>Cash slips</li><li>Advance report</li><li>Page of cash book</li><li>Count statement</li><li>Deferrals*</li></ul> |
| Sales orders | Add positions and related information for signers who can sign the following outgoing primary documents that are related to customers:<ul><li>Invoice for payment*</li><li>Invoice</li><li>Facture*</li><li>Invoice - credit-note</li><li>Facture - credit-note*</li><li>Tax transaction facture (client)*</li></ul> |
| Purchase orders | Add positions and related information for signers who can sign the following incoming primary documents that are related to vendors:<ul><li>Invoice</li><li>Facture*</li><li>Invoice - credit-note</li><li>Facture - credit-note*</li><li>Invoice for payment*</li><li>Tax transaction facture (vendor)*</li></ul> |
| Inventory item management | Add positions and related information for signers who can sign the following warehouse documents when tangible assets are issued to a customer or received from a vendor:<ul><li>Issue slip for sales order (M-15)*</li><li>Rmb. slip/Receipt order</li><li>Issue slip for transfer order (M-15)*</li></ul> |

\* This document type is available only for legal entities that have their primary address in Russia. The following table describes the fields on the **Officials** page.

| Field | Description |
|-------|-------------|
| Position | Select the signer's post title. |
| Name | Select the signer's name. The names in the list come from either the Contacts table or the Employees table, depending on the type of signer (that is, depending on whether the **Our** check box is selected). If the signer's name isn't in the list, manually enter the signer's full name. |
| Job title | Select the signer's job title. If the signer's title isn't in the list, manually enter the signer's title. |
| Account code | Select whether the signer can sign all documents of the selected document type, or only documents for a specific customer or vendor. |
| Account relation | Select the customer or vendor account that is related to the selected account code. This field is available only if you select **Record** in the **Account code** field. |
| Our | A selected check box indicates that the position is internal. |
| Association with warehouse | Select whether the signer is assigned to all warehouses or only a specific warehouse. The following options are available:<ul><li>**All** – The signer is assigned to all warehouses.</li><li>**Record** – The signer is assigned to a specific warehouse.</li></ul> |
| Warehouse | Select the warehouse code that corresponds to the warehouse that the signer is assigned to. This field is available only if you select **Record** in the **Association with warehouse** field. |

## Set up a number sequence code for officials

You can assign a number sequence code for officials in the **Number sequences** section of the **Legal entities** page. Select a number sequence code for the **Officials session ID** reference.

## Modify signers in primary documents

The Officials functionality shows the default predefined signers from the Officials table. On the **Posting invoice** page, on the **Officials** tab, you can change a signer's name and title on the primary document for the following document types:

- Customer invoice
- Vendor invoice
- Ship transfer order
- Cash order

> [!NOTE]
> After you post a document, you can't edit the officials.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
