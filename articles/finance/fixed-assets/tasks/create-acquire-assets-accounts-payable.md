--- 
# required metadata 
 
title: Create and acquire assets from Accounts payable
description: This procedure walks through the creation and acquisition of a fixed asset with the purchasing process. 
author: moaamer
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: AssetParameters, VendInvoiceWorkspace, VendEditInvoice, VendTableLookup, InventItemIdLookupSimple, AssetTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create and acquire assets from Accounts payable

[!include [banner](../../includes/banner.md)]

This procedure walks through the creation and acquisition of a fixed asset with the purchasing process. It uses the Accountant and Accounts payable clerks and the demo company USMF.


## Set Fixed assets parameters
1. Go to **Fixed assets > Setup > Fixed assets parameters**.
2. Expand the **Purchase orders** FastTab.
3. Select the **Allow asset acquisition from Purchasing** checkbox.
4. Select the **Create asset during product receipt or invoice posting** checkbox.

## Create a new vendor invoice
1. Go to **Accounts payable > Workspaces > Vendor invoice entry**.
2. Click **New vendor invoice**.
3. In the **Invoice account** field, click the drop-down button to open the lookup.
4. In the list, click the link in the selected row.
5. In the **Number** field, type a value.
6. In the **Posting date** field, enter a date.
7. Click **Add line**.
8. In the **Item number** field, click the drop-down button to open the lookup. Either non-stocked items or procurement categories can be used for fixed asset acquisition.  
9. In the list, click the link in the selected row.
10. In the **Quantity** field, enter a number. One invoice line will only create one fixed asset, regardless of quantity. The invoice quantity field value will be transferred to the fixed asset quantity.  
11. In the **Unit price** field, enter a number.
12. Expand the **Line details** FastTab.
13. Click the **Fixed assets** tab.
14. Check the **Create a new fixed asset** checkbox.
15. In the **Fixed asset group** field, click the drop-down button to open the lookup.
16. In the list, select the fixed asset group to be used when creating the new fixed asset.
17. In the list, click the link in the selected row.
18. Click **Post**. The fixed asset will be created and acquired when the invoice is posted.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
