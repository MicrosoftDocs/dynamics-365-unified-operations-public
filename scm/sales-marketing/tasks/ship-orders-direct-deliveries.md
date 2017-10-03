--- 
# required metadata 
 
title: Ship orders as direct deliveries
description: This procedure demonstrates how to create a direct delivery for a sales order. 
author: omulvad
manager: AnnBe 
ms.date: 02/12/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Ship orders as direct deliveries

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure demonstrates how to create a direct delivery for a sales order. You use direct delivery when you want to ship goods to the customer directly from your vendor, instead of shipping them to your own warehouse first. You can run this procedure in demo data company USMF or on your own data. To successfully complete the second sub-task "Create direct deliveries from the workbench", make sure that the item that you choose on the sales order has a default Vendor specified on the Purchase FastTab of the Released product master.


## Set an individual order for direct delivery
1. Go to All sales orders.
2. Click New.
3. In the Customer account field, enter or select a value.
    * If you’re using USMF, you can select account US-001.  
4. Click OK.
5. In the Item number field, enter or select a value.
    * If you’re using USMF, you can select item T0020.  
6. Click Save.
7. On the Action Pane, click Sales order.
8. Click Direct delivery.
    * The Create delivery page lists all the open sales order lines as copied from the sales order. You can review the order details, and if required, you can modify details such purchase quantity and pricing terms before you create the direct delivery.  
9. Select Yes in the Include all field.
    * If you want to generate a direct delivery for only a subset of the sales order lines, select these individually.  
    * The Vendor account field may or may not already be populated with a vendor number. If the default vendor is set up for the product (on the associated Item coverage) then this vendor will be copied to the line. Otherwise, you must enter a vendor manually. In this example, we’ll select a new vendor in the next step, even if one is already populated.   
10. In the Vendor account field, enter or select a value.
    * If you’re using USMF, you can select account 1001.  
11. Click OK.
    * The message informs you that the purchase order has now been created.   
12. Expand the Line details section.
13. Click the Delivery tab.
    * The Direct delivery field is now set to Yes.  
    * The Direct delivery status shows the Purchase order created.   
14. On the Action Pane, click General.
15. Click Related orders.
16. Click to follow the link in the Purchase order field.
17. Expand the Line details section.
18. Click the Address tab.
    * Note that the delivery address for this purchase order line is the customer's delivery address and not your company's address.  
    * If you change the delivery address on either the purchase order line or the originating sales order line, the address on the corresponding order line will be automatically updated.  
19. Click the Delivery tab.
    * Like the sales order line, the associated purchase order line type is also set to Direct delivery.  
    * The purchase order line's Delivery  date and the Confirmed delivery date are set to the Requested receipt date and Confirmed receipt date of the originating sales order line respectively.   
    * If you update any of these dates on either the purchase line or the sales line, the dates on the corresponding order will be automatically updated.     
    * The purchase order that is set to deliver goods directly the customer is linked to the originating sales order by means of a special association. This association imposes the rule that the packing slip update of the sales order can't be done from the sales order itself and must be done by using the purchase order. However, customer invoicing must be carried out from the sales order.  
20. On the Action Pane, click Purchase.
21. Click Confirmation.
22. Click OK.
23. On the Action Pane, click Receive.
24. Click Product receipt.
25. In the Product receipt field, type a value.
26. Click OK.
27. On the Action Pane, click General.
28. Click Related orders.
29. In the list, mark the selected row.
    * After the purchase order has been updated as received, or in other words, after the vendor has shipped the goods to your customer's address, the status of the originating sales order is automatically updated to Delivered.  
    * The sales order can now be invoiced.    
30. Click OK.
31. Close the page.
32. Click OK.

## Create direct deliveries from the workbench
1. Close the page.
2. Close the page.
3. Go to All sales orders.
4. Click New.
5. In the Customer account field, enter or select a value.
6. Click OK.
7. In the Item number field, enter or select a value.
8. Expand the Line details section.
9. Click the Delivery tab.
    * Instead of creating a direct delivery as part of the sales order processing as in the previous procedure, you can choose to hand over this task to a purchasing professional. To include the sales order line in the direct delivery handling process, you must mark the line for direct delivery.  
10. Select Yes in the Direct delivery field.
    * 	If the item has already been set up for direct delivery by default, the field will automatically be set to Yes at the order line entry. You can set up an item for direct delivery on the Released product's master by setting the Direct delivery option to Yes and selecting a default Direct delivery warehouse.  
    * Because the purchase order has not yet been created, the Direct delivery status is set to To be direct delivered.   
11. Close the page.
12. Close the page.
13. Go to Direct delivery.
    * The Direct delivery page acts as a workbench that provides the purchasing agent with an overview of all the sales order lines that are to be direct delivered and it allows them to create the respective purchase orders. In addition, they can view the open direct delivery orders and the confirmed orders on the Confirmation and Delivery tabs.   
14. Click Create direct delivery.
15. Click the Confirmation tab.
    * After you have created a direct delivery order, it automatically moved to the Confirmation tab. You can choose to confirm the order directly from this page. When the purchase is confirmed, it will automatically move to the Delivery tab, from which you can registered its receipt.  

