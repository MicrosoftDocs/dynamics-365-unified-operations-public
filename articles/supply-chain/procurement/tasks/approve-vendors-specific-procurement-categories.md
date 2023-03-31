--- 
# required metadata 
 
title: Approve vendors for specific procurement categories
description:  This article explains how to approve vendors for specific procurement categories in Dynamics 365 Supply Chain Management.
author: GalynaFedorova
ms.date: 07/30/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: VendTable, DirPartyEcoResCategory, EcoResCategorySingleLookup, ProcCategoryHierarchyManagement   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Approve vendors for specific procurement categories

[!include [banner](../../includes/banner.md)]

This article explains how to approve vendors for specific procurement categories in Dynamics 365 Supply Chain Management. When a purchase requisition is created, there may be a requirement to select an approved or preferred vendor, depending on how the purchasing policies are set up. This procedure shows you how to specify that a vendor is approved or preferred for a specific procurement category. This task would usually be carried out by a procurement professional. You can use this procedure in demo data company USMF.

1. Go to **Procurement and sourcing > Vendors > All vendors**.
2. Select the vendor that you want to set as an approved or preferred vendor for a category.
3. On the Action Pane, select **General**.
4. Select **Categories**.
5. Select **Add category**.
6. In the **Category** field, select **OFFICE AND DESK ACCESSORIES (OFFICE AND DESK ACCESSORIES)**.
7. In the **Vendor category status** field, select **Preferred**. It's possible to specify more than one preferred vendor for a category.  
8. Select **Save**.
9. Go to **Procurement and sourcing > Procurement categories**.
10. In the tree, select **CORP PROCUREMENT CATEGORIES\OFFICE AND DESK ACCESSORIES**.
11. Expand the **Vendors** section. Check if the vendor that you selected appears as a preferred vendor for the Office and desk accessories category. If you're running this procedure as a task guide, you may have to select the **Unlock** button to be able to scroll down to the list of vendors.  It's also possible to add preferred and approved vendors on this page.  
12. In the tree, expand **OFFICE AND DESK ACCESSORIES** and select **Scissors**.
13. Select **No** in the **Inherit vendors from parent category:** field.
14. Select **Yes** in the **Inherit vendors from parent category:** field.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]