--- 
# required metadata 
 
title: Ship orders as direct deliveries
description: This article demonstrates how to create a direct delivery for a sales order. 
author: Henrikan  
ms.date: 07/11/2019  
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, PurchCreateFromSalesOrder, VendAccountItemLookup, SalesTableReferences, PurchTable, PurchTablePart, PurchEditLines, PurchTable, PurchTableReferences, MCRDropShipWorkbench, SalesShippingLine   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: henrikan
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Ship orders as direct deliveries

[!include [banner](../../includes/banner.md)]

This article demonstrates how to create a direct delivery for a sales order. You use direct delivery when you want to ship goods to the customer directly from your vendor, instead of shipping them to your own warehouse first. You can run this procedure in demo data company USMF or on your own data. To successfully complete the second sub-task "Create direct deliveries from the workbench", make sure that the item that you choose on the sales order has a default Vendor specified on the Purchase FastTab of the Released product master.

## Set an individual order for direct delivery
1. Go to **Accounts receivable > Orders > All sales orders**.
2. Select **New**.
3. Enter or select a value in the **Customer accound** field, then select **OK**
4. Enter or select values in the **Item number** and **Site** fields, then select **Save**.
5. On the Action Pane, select **Sales order**, then select **Direct delivery**. The Create delivery page lists all the open sales order lines as copied from the sales order. You can review the order details, and if required, you can modify details such purchase quantity and pricing terms before you create the direct delivery.  
6. Select **Yes** in the **Include all** field.
    - If you want to generate a direct delivery for only a subset of the sales order lines, select these individually.  
    - The **Vendor account** field may or may not already be populated with a vendor number. If the default vendor is set up for the product (on the associated Item coverage) then this vendor will be copied to the line. Otherwise, you must enter a vendor manually. In this example, we'll select a new vendor in the next step, even if one is already populated.   
7. Enter or select a value in the **Vendor account** field, then select **OK**. The message informs you that the purchase order has now been created.   
8. Expand the **Line details** section.
9. Select the **Delivery** tab and verify that the **Direct delivery** field is set to **Yes**.
10. On the Action Pane, select **General**.
11. Select **Related orders**.
12. Select the link in the **Purchase order** field.
13. Expand the **Line details** section and select the **Address** tab.
    - The delivery address for this purchase order line is the customer's delivery address and not your company's address.  
    - If you change the delivery address on either the purchase order line or the originating sales order line, the address on the corresponding order line will be automatically updated.  
14. Select the **Delivery** tab.
    - Like the sales order line, the associated purchase order line type is also set to Direct delivery.  
    - The purchase order line's Delivery date and the Confirmed delivery date are set to the Requested receipt date and Confirmed receipt date of the originating sales order line respectively.   
    - If you update any of these dates on either the purchase line or the sales line, the dates on the corresponding order will be automatically updated.     
    - The purchase order that is set to deliver goods directly to the customer is linked to the originating sales order by means of a special association. This association imposes the rule that the packing slip update of the sales order can't be done from the sales order itself and must be done by using the purchase order. However, customer invoicing must be carried out from the sales order.  
15. On the Action Pane, select **Purchase**.
16. Select **Confirmation**.
17. Select **OK**.
18. On the Action Pane, select **Receive**.
19. Select **Product receipt**.
20. In the **Product receipt** field, type a value.
21. Select **OK**.
22. On the Action Pane, select **General**.
23. Select **Related orders** and highlight the desired record.
    - After the purchase order has been updated as received, or in other words, after the vendor has shipped the goods to your customer's address, the status of the originating sales order is automatically updated to Delivered.  
    - The sales order can now be invoiced.    
24. Select **OK**.
25. Close the page.
26. Select **OK**. Close the pages and return to the home page.

## Create direct deliveries from the workbench
1. Go to **Navigation > Modules > Accounts receivable > Orders > All sales orders**.
2. Select **New**.
3. Enter or select a value in the **Customer account** field, then select **OK**.
4. Enter or select a value in the **Item number** and **site** fields.
5. Expand the **Line details** section, then select the **Delivery** tab. Instead of creating a direct delivery as part of the sales order processing as in the previous procedure, you can choose to hand over this task to a purchasing professional. To include the sales order line in the direct delivery handling process, you must mark the line for direct delivery.  
6. Select **Yes** in the **Direct delivery** field.
    - If the item has already been set up for direct delivery by default, the field will automatically be set to Yes at the order line entry. You can set up an item for direct delivery on the Released product's master by setting the Direct delivery option to Yes and selecting a default Direct delivery warehouse.  
    - Because the purchase order has not yet been created, the Direct delivery status is set to "To be direct delivered".   
7. Select **Save**.
8. Close pages until you return to the home page.
9. Enter `Direct delivery` in the search bar.
    - The Direct delivery page acts as a workbench that provides the purchasing agent with an overview of all the sales order lines that are to be direct delivered and it allows them to create the respective purchase orders. In addition, they can view the open direct delivery orders and the confirmed orders on the Confirmation and Delivery tabs.  
    - After you have created a direct delivery order, it automatically moved to the Confirmation tab. You can choose to confirm the order directly from this page. When the purchase is confirmed, it will automatically move to the Delivery tab, from which you can registered its receipt.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]