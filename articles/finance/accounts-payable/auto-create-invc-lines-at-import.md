---
# required metadata

title: Generate invoice lines when you import vendor invoices
description: This article describes the functionality for automatically generating invoice lines on vendor invoices when invoices are imported.
author: sunfzam
ms.date: 09/10/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2021-08-30
ms.dyn365.ops.version: 10.0.23

---

# Generate invoice lines when you import vendor invoices

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article describes the functionality for automatically generating invoice lines on vendor invoices when invoices are imported.

Sometimes, vendor invoices contain limited information, such as recipient information and subtotals. However, they contain no information for line items. When you import invoices, the invoice lines will be automatically generated, based on information on the corresponding purchase order.

To enable automatic creation of invoice lines, follow these steps.

1.	Go to **Accounts payable \> Setup \> Accounts payable parameters**.
2.	On the **Vendor invoice automation** tab, under **Automatic line creation for imported invoices**, set the **Automatically create invoice lines** option to **Yes**. 
4.	In the **Choose default quantity for automatic invoice lines creation** field, select the quantity that should be used to automatically generate invoice lines:

    - **Ordered quantity** – Lines will be generated from purchase order lines. This value is the default value.
    - **Product receipt quantity** – The purchase order number will be used to find the relevant product receipts. It will then use the product receipt quantities to generate invoice lines.

## Data entity changes

To support the functionality that is described in this article, the **Vendor invoice header** data entity has been enhanced. Three fields have been added:

- **HeaderOnlyImport** – This field must be set to **Yes** to generate lines for invoice headers.
- **PurchIdRange** – The list of purchase order numbers. The invoice numbers can be a range, such as **PO0001..PO0009** (where two dots separate the start and end of the range), or discrete values, such as **PO0001, PO0003, PO0006**. All purchase orders must belong to the same vendor account on the invoice header. Otherwise, you will receive the following error message: "Failed to generate invoice lines. Purchase orders have different vendor accounts."
- **PackingslipRange** – The list of product receipt numbers. Vendor invoice lines can be created from product receipts. However, product receipt numbers aren't typically included on vendor invoices. Only enter the product receipt numbers into this field if you can clearly identify which product receipts are for which specific invoices. Invoice lines can be generated based on product receipts. If this field is used, the setting of the **Choose default quantity for automatic invoice lines creation** field on the **Accounts payable parameters** page is ignored. 

**Limitation**: If you enter multiple product receipt numbers, several pending vendor invoices will be created with the same invoice number. You must consolidate them manually before processing the invoice further. In future releases, we plan to consolidate the invoices automatically, so the limitation will be removed.

All product receipts must belong to the same vendor account on the invoice header.

## Result

If lines are successfully generated, the following message is logged in the vendor invoice automation history: "Automatically create invoice lines: Succeeded."

If lines don't generate, the following error message is logged: "Automatically create invoice lines: Failed."
