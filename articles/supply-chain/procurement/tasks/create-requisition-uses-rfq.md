--- 
# required metadata 
 
title: Create a requisition that uses an RFQ
description: This article explains how to add price and vendor information to a purchase requisition from an RFQ process. 
author: GalynaFedorova
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchReqTableListPage, PurchReqCreate, PurchReqTable, PurchReqLineRelatedDocuments, EcoResCategorySingleLookup, PurchReqWorkflowDropDialog, WorkflowSubmitDialog, WorkflowStatus, WorkflowWorkItemActionDialog, WorkflowUserListLookup, PurchReqCopyRFQ, SysDataAreaSelectLookup, PurchRFQCaseTable, PurchRFQEditLines, PurchRFQReplyTable, UnitOfMeasureLookup   
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
# Create a requisition that uses an RFQ

[!include [banner](../../includes/banner.md)]

This article explains how to add price and vendor information to a purchase requisition from an RFQ process. The example shown in this guide can be used in the USMF demo data company, and you must be logged in as an Admin to complete all the steps. The tasks in this guide would typically be done by procurement professionals.


## Create a requisition
1. Go to **Procurement and sourcing > Purchase requisitions > Purchase requisitions prepared by me**.
2. Select **New**.
3. In the **Name** field, type a value.
4. In the **Requested date** field, enter a date.
5. In the **Accounting date** field, enter a date.
6. Select **OK**.
7. In the **Reason** field, enter or select a value.
8. Select **Add line**.
9. In the **Procurement category** field, select a category in the tree, and then select **OK**.
10. In the **Product name** field, type a value.
11. In the **Quantity** field, enter a number.
12. In the **Unit** field, enter or select a value.
13. Select **Save**.
14. Select **Workflow** to open the drop dialog.
15. Select **Submit**.
16. Close the page.
17. Select **Submit**.

## Reassign a workflow task
The next task is to create an RFQ to get bids from vendors for the product. In USMF demo data, the requisition workflow is set up with a rule so that if a vendor is not selected, or the unit price is 0 for a line, a task is assigned to a specific worker to create an RFQ. To continue with this guide, you need to re-assign that task to another user (yourself). You can only do this if you are logged in as an Admin.  

1. Select **Workflow** to open the drop dialog.
2. Select **View history**.
3. Refresh the page.
4. Expand the **Tracking details** section.
5. In the tree, select the line that starts with "Line workflow activated on".
6. Select **View workflow details**.
7. Expand the **Work items** section.
8. Select **Reassign**.
9. In the **User** field, select **Admin**.
10. Select **Reassign**.
11. Close the two pages.

## Create an RFQ

1. Refresh the page.
2. Select **Request for quotation**.
3. In the **Buying legal entity** field, select **USMF**. You must select the same legal entity that's on the requisition line.  
4. In the list, mark the selected row. If you had multiple lines on your purchase requisition, select all the lines that you want to add to the RFQ.  
5. Select **OK**.
6. Refresh the page.
7. Ensure that the FactBox is open, then expand the **Related documents** section.
8. Select the link in the **Request for quotation** field to open the RFQ that was just created.
9. Select **Header**.
10. Select **Add**.
11. In the **Vendor account** field, enter or select a value.
12. Select **Add**.
13. In the **Vendor account** field, enter or select a value.
14. Select **Send**.
15. Select **OK**.
16. Select **Enter reply**.
17. On the Action Pane, select **Reply**.
18. Select **Copy data to reply**. This copies data, such as the quantity and dates, from the RFQ to the reply.  
19. In the **Unit price** field, enter a number. This is the price that you've received from the vendor. You might also want to enter additional information from the vendor.  
20. Select **Accept**.
21. Select **OK**.

## Verify that vendor and price have been transferred to the requisition
1. Close the page.
2. Select **Lines**.
3. Select **Related information**.
4. Select **Purchase requisition**.
5. Select the line that was transferred to the RFQ. Verify that the price and vendor have been copied to the requisition.  
6. Select **Workflow** to open the drop dialog.
7. Select Complete.
8. Select the page.
9. Select Complete.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]