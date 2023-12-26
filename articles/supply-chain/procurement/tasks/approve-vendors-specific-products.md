--- 
# required metadata 
 
title: Approve vendors for specific products
description: This procedure shows you how to approve vendors for specific products. 
author: GalynaFedorova
ms.date: 07/22/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: EcoResProductDetailsExtended, PdsApprovedVendorList, VendTable   
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
# Approve vendors for specific products

[!include [banner](../../includes/banner.md)]

This procedure shows you how to approve vendors for specific products. This allows you to control which vendors can be used when the product is added to a purchase order. You can use this procedure in demo data company USMF, or on your own data. This task would typically be carried out by a Purchasing manager.

1. Go to **Product information management > Products > Released products**.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. Expand the **Purchase** fastTab. If there is a primary vendor shown in the **Vendor** field, then you need to add this vendor as an approved vendor in the following steps. Make a note of the vendor number, if one is shown.  
5. On the Action Pane, click **Purchase**.
6. Click **Setup**.
7. Click **Add**.
8. In the Vendor field, enter or select a value. Select the approved vendor. At least one of the lines has to be the primary vendor if there was one in the product record. If you made a note of the vendor number earlier, select it here.  
9. In the **Expiration** field, enter a date. Choose a date a that is a few months ahead.  
10. Click **Add**.
11. In the **Vendor** field, enter or select a value.
12. In the **Expiration** field, enter a date. Choose a date that is different than the previous expiration date.  
13. Close the page.
14. On the Action Pane, click **Approved vendors**.
15. In the **Expiration** field, enter a date. This date acts as a filter so you can see who the approved vendors are, up to a certain date.  
16. Close the page.
17. On the Action Pane, click **Effective period**.
18. In the **Show vendors expired by** field, enter a date. You can use this page to identify vendors where the approval status will expire after a certain date.  
19. Close the page.
20. Click **Edit**.
21. In the **Approved vendor check method** field, select an option. This field allows you to select the policy for what should happen if the product is added to a purchase order line where the vendor is not an approved vendor.  
22. Click **Save**.
23. Close the page.
24. Close the page.
25. Go to **Procurement and sourcing > Vendors > Vendor/item relations > Approved vendor list by item**. This page gives you an overview of all products and the approved vendors.  
26. Close the page.
27. Go to **Procurement and sourcing > Vendors > All vendors**. You can also start from a vendor and then go to the list of approved products for that vendor account.  
28. In the list, find and select the desired record.
29. On the Action Pane, click **Procurement**.
30. Click **Approved vendor list by vendor**.
31. Close the page.
32. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]