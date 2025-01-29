---
title: Approve vendors for specific products
description: Learn how to approve vendors for specific products, including a step-by-step process for the task using the USMF demo data company.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: EcoResProductDetailsExtended, PdsApprovedVendorList, VendTable  
ms.topic: how-to
ms.date: 11/18/2024
ms.custom: 
  - bap-template
---

# Approve vendors for specific products

[!include [banner](../../includes/banner.md)]

This procedure shows you how to approve vendors for specific products. This allows you to control which vendors can be used when the product is added to a purchase order. This task would typically be carried out by a purchasing manager.

1. Go to **Product information management > Products > Released products**.
2. In the list, find and select the desired record.
3. In the list, select the link in the selected row.
4. Expand the **Purchase** FastTab. If there's a primary vendor shown in the **Vendor** field, then you need to add this vendor as an approved vendor in the following steps. Make a note of the vendor number, if one is shown.  
5. On the Action Pane, select **Purchase**.
6. Select **Setup**.
7. Select **Add**.
8. In the Vendor field, enter or select a value. Select the approved vendor. At least one of the lines has to be the primary vendor if there was one in the product record. If you made a note of the vendor number earlier, select it here.  
9. In the **Expiration** field, enter a date. Choose a date that is a few months ahead.  
10. Select **Add**.
11. In the **Vendor** field, enter or select a value.
12. In the **Expiration** field, enter a date. Choose a date that is different than the previous expiration date.  
13. Close the page.
14. On the Action Pane, select **Approved vendors**.
15. In the **Expiration** field, enter a date. This date acts as a filter so you can see who the approved vendors are, up to a certain date.  
16. Close the page.
17. On the Action Pane, select **Effective period**.
18. In the **Show vendors expired by** field, enter a date. You can use this page to identify vendors where the approval status will expire after a certain date.  
19. Close the page.
20. Select **Edit**.
21. In the **Approved vendor check method** field, select an option. This field allows you to select the policy for what should happen if the product is added to a purchase order line where the vendor isn't an approved vendor.  
22. Select **Save**.
23. Close the page.
24. Close the page.
25. Go to **Procurement and sourcing** \> **Vendors** \> **Vendor/item relations** \> **Approved vendor list by item**. This page gives you an overview of all products and the approved vendors.  
26. Close the page.
27. Go to **Procurement and sourcing** \> **Vendors** \> **All vendors**. You can also start from a vendor and then go to the list of approved products for that vendor account.  
28. In the list, find and select the desired record.
29. On the Action Pane, select **Procurement**.
30. Select **Approved vendor list by vendor**.
31. Close the page.
32. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
