---
title: Approve vendors for specific products
description: Learn how to approve vendors for specific products, including a step-by-step process for the task using the USMF demo data company.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form: EcoResProductDetailsExtended, PdsApprovedVendorList, VendTable  
ms.topic: how-to
ms.date: 05/21/2026
ms.custom: 
  - bap-template
---

# Approve vendors for specific products

[!include [banner](../../includes/banner.md)]

This procedure shows you how to approve vendors for specific products. When you approve vendors, you control which vendors can be used when adding the product to a purchase order. A purchasing manager typically carries out this task.

1. Go to **Product information management > Products > Released products**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Expand the **Purchase** FastTab. If there's a primary vendor shown in the **Vendor** field, add this vendor as an approved vendor in the following steps. Make a note of the vendor number, if one is shown.  
1. On the Action Pane, select **Purchase**.
1. Select **Setup**.
1. Select **Add**.
1. In the **Vendor** field, enter or select a value. Select the approved vendor. At least one of the lines has to be the primary vendor if there was one in the product record. If you made a note of the vendor number earlier, select it here.  
1. In the **Expiration** field, enter a date. Choose a date that is a few months ahead.  
1. Select **Add**.
1. In the **Vendor** field, enter or select a value.
1. In the **Expiration** field, enter a date. Choose a date that is different from the previous expiration date.  
1. Close the page.
1. On the Action Pane, select **Approved vendors**.
1. In the **Expiration** field, enter a date. This date acts as a filter so you can see who the approved vendors are, up to a certain date.  
1. Close the page.
1. On the Action Pane, select **Effective period**.
1. In the **Show vendors expired by** field, enter a date. Use this page to identify vendors where the approval status expires after a certain date.  
1. Close the page.
1. Select **Edit**.
1. In the **Approved vendor check method** field, select an option. This field allows you to select the policy for what should happen if the product is added to a purchase order line where the vendor isn't an approved vendor.  
1. Select **Save**.
1. Close the page.
1. Close the page.
1. Go to **Procurement and sourcing** > **Vendors** > **Vendor/item relations** > **Approved vendor list by item**. This page gives you an overview of all products and the approved vendors.  
1. Close the page.
1. Go to **Procurement and sourcing** > **Vendors** > **All vendors**. You can also start from a vendor and then go to the list of approved products for that vendor account.  
1. In the list, find and select the desired record.
1. On the Action Pane, select **Procurement**.
1. Select **Approved vendor list by vendor**.
1. Close the page.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
