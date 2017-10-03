--- 
# required metadata 
 
title: Create a requisition that uses an RFQ
description: This guide shows how to add price and vendor information to a purchase requisition from an RFQ process. 
author: mkirknel
manager: AnnBe 
ms.date: 08/25/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: bis
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a requisition that uses an RFQ

[!include[task guide banner](../../includes/task-guide-banner.md)]

This guide shows how to add price and vendor information to a purchase requisition from an RFQ process. The example shown in this guide can be used in the USMF demo data company, and you must be logged in as an Admin to complete all the steps. The tasks in this guide would typically be done by procurement professionals.


## Create a requisition
1. Go to Procurement and sourcing > Purchase requisitions > Purchase requisitions prepared by me.
2. Click New.
3. In the Name field, type a value.
4. In the Requested date field, enter a date.
5. In the Accounting date field, enter a date.
6. Click OK.
7. In the Reason field, enter or select a value.
8. Click Add line.
9. In the Procurement category field, select a category in the tree, and then click OK.
10. In the Product name field, type a value.
11. In the Quantity field, enter a number.
12. In the Unit field, enter or select a value.
13. Click Save.
14. Click Workflow to open the drop dialog.
15. Click Submit.
16. Close the page.
17. Click Submit.

## Reassign a workflow task
    * The next task is to create an RFQ to get bids from vendors for the product. In USMF demo data, the requisition workflow is set up with a rule so that if a vendor is not selected, or the unit price is 0 for a line, a task is assigned to a specific worker to create an RFQ. To continue with this guide, you need to re-assign that task to another user (yourself). You can only do this if you are logged in as an Admin.  
1. Click Workflow to open the drop dialog.
2. Click View history.
3. Refresh the page.
4. Expand the Tracking details section.
5. In the tree, select 'the line that starts with “Line workflow activated on”'.
6. Click View workflow details.
7. Expand the Work items section.
8. Click Reassign.
9. In the User field, select Admin.
10. Click Reassign.
11. Close the page.
12. Close the page.

## Create an RFQ
1. Refresh the page.
2. Click Request for quotation.
3. In the Buying legal entity field, select USMF.
    * You must select the same legal entity that’s on the requisition line.  
4. In the list, mark the selected row.
    * If you had multiple lines on your purchase requisition, select all the lines that you want to add to the RFQ.  
5. Click OK.
6. Refresh the page.
7. Open the FactBox and then expand the Related documents section.
    * You may already have the FactBox open. Look for the icon with an arrow on it, to the right of the Lines/Header toggle buttons. If the arrow is pointing to the right, the FactBox is already open. If the arrow points to the left, click it to open the FactBox.  
8. Click the link in the Request for quotation field to open the RFQ that was just created.
9. Click Header.
10. Click Add.
11. In the Vendor account field, enter or select a value.
12. Click Add.
13. In the Vendor account field, enter or select a value.
14. Click Send.
15. Click OK.
16. Click Enter reply.
17. On the Action Pane, click Reply.
18. Click Copy data to reply.
    * This copies data, such as the quantity and dates, from the RFQ to the reply .  
19. In the Unit price field, enter a number.
    * This is the price that you’ve received from the vendor. You might also want to enter additional information from the vendor.  
20. Click Accept.
21. Click OK.

## Verify that vendor and price have been transferred to the requisition
1. Close the page.
2. Click Lines.
3. Click Related information.
4. Click Purchase requisition.
5. Select the line that was transferred to the RFQ.
    * Verify that the price and vendor have been copied to the requisition.  
6. Click Workflow to open the drop dialog.
7. Click Complete.
8. Close the page.
9. Click Complete.

