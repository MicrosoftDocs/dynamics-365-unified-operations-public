---
# required metadata

title: Generate invoice lines when importing vendor invoices
description: This topic describes the capability for creating invoice lines on vendor invoices automatically when invoices are imported. 
author: sunfzam
ms.date: 09/10/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2021-08-30
ms.dyn365.ops.version: 10.0.23

---

# Generate invoice lines when importing vendor invoices

[!include [banner](../includes/banner.md)]

This topic describes the capability for creating invoice lines on vendor invoices automatically when invoices are imported. 

Sometimes vendor invoices contain limited information, such as recipient information and subtotals, but no information for line items. When you import invoices, the system can generate invoice lines automatically based on information in the corresponding purchase order. 

To enable the automatic creation of invoice lines, complete the following steps. 

1.	Go to **Account payable > Setup > Account payable parameters**.
2.	Select **Vendor invoice automation**.
3.	Under group **Automatic line creation for imported invoices**, set **Automatically create invoice lines** field to **Yes**. 
4.	Select an option for the **Choose default quantity for automatic invoice lines creation** field.
This parameter determines whether the system uses the "Ordered quantity" or "Product receipt quantity" to automatically create invoice lines. 
•	**Ordered quantity**: This is default value. System will generate lines from purchase order lines.
•	**Product receipt quantity**: The system will use purchase order numbers to find the relevant product receipts, and then will use the product receipt quantities to generate invoice lines.

### Data entity changes
With the addition of the capability described in this topic, the data entity Vendor invoice header is also enhanced. Three additional fields have been added.

1. **HeaderOnlyImport**
This attribute needs to be set to **Yes**. System will only generate lines for such invoice headers

2. **PurchIdRange**: The list of purchase order numbers.  
The invoice numbers can be a range, like INV0001..INV0009(double dots between the numbers), or discrete value, like INV0001, INV0003, INV0006.
All purchase orders shall belong to the same vendor account on the invoice header. Otherwise, error will be raised: “Fail to generate invoice lines. Purchase orders have different vendor accounts”

3. **PackingslipRange**: The list of product receipt numbers. 
Vendor invoice lines can be created from product receipts. However, product receipt numbers normally are not contained on vendor invoice. The field can be used only if user can clearly identify the invoice is sent for which product receipts. And in this case, the setting in parameter **Choose default quantity for automatic invoice lines creation** won’t be considered.

All product receipts will belong to the same vendor account on the invoice header.

#### Result
If lines are generated successfully, a success message, Automatically create invoice lines: Succeeded, is logged in vendor invoice automation history. 
If system fails to generate lines, the error, Automatically create invoice lines: Failed, is logged.


 
