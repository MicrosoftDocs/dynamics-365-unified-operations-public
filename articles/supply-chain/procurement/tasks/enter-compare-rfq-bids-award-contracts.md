--- 
# required metadata 
 
title: Enter and compare RFQ bids and award contracts
description: This procedure shows you how to enter replies to an RFQ, score and compare bids, and then award the bid to one of the vendors. 
author: mkirknel
manager: AnnBe 
ms.date: 06/07/2016
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
# Enter and compare RFQ bids and award contracts

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows you how to enter replies to an RFQ, score and compare bids, and then award the bid to one of the vendors. You can use this procedure in demo data company USMF. Before you start, you must have an RFQ with two lines that has been sent to at least two vendors. You can run the "Create a request for quotation" procedure as a prerequisite to create this. You need to have set up scoring criteria before you can run this procedure.


## Enter a reply from a vendor
1. Go to Procurement and sourcing > Requests for quotations > All requests for quotations.
2. Select an RFQ that has a status of Sent and click the link on the Request for quotation case number.
    * The RFQ should have been sent to at least 2 vendors.  
3. Click Header to go to the list of vendors.
4. Select the vendor for whom you want to enter a response on the RFQ.
5. Click Enter reply.
6. On the Action Pane, click Reply.
7. Click Copy data to reply.
    * This action will copy selected data, for example, the quantity from the RFQ case to the RFQ reply. Alternatively you can skip this action and fill in all the response fields manually when you edit the reply.  
8. Click Edit.
9. In the Unit price field, enter a number.
10. Choose the other quotation line.
11. In the Unit price field, enter a number.

## Score the bid
1. Click Header to go to the scoring of the bid.
2. Expand the Bid scoring section.
3. In the Score field, enter a number for one of the scoring criteria.
    * If you hover over one of the scoring criteria a tooltip shows the range that you have to score within. In this demo you can add a number between 1 and 5 to any of the criteria.  
4. Select another scoring criterion.
5. In the Score field, enter a number.
6. Expand the Questionnaires section.
    * If the RFQ case has a questionnaire that was sent to the vendors, you can enter their responses in the questionnaire section.  
7. Close the page.

## Enter a reply for another vendor
1. Select the next vendor by clearing the vendor you have just entered the reply for and then selecting the row for the next vendor.
2. In the list, find and select the desired record.
3. Click Enter reply.
4. Click Copy data to reply.
5. Click Edit.
6. In the Unit price field, enter a number.
7. Choose the other quotation line.
8. In the Unit price field, enter a number.

## Score the second bid
1. Click Header to go to scoring of the bid.
2. In the Score field, enter a number.
3. In the list, find and select the desired record.
4. In the Score field, enter a number.

## Compare the replies
1. On the Action Pane, click General.
2. Click Compare replies.
3. In the Rank field, enter a number.
    * This page shows the bids with the header and lines, and the total score on the header level. You can compare the lines by sorting in the grid so that comparable lines are next to each other. The information also includes:   Quantity: The quantity quoted by the vendor. This might not equal the quantity specified in the RFQ.   Net amount: The price quoted by a vendor, after subtracting any discounts, for the items on the line.   Deviation: The number of days that the delivery date in the bid header or line deviates from the requested delivery date in the RFQ header or RFQ line.   You can enter a rank for each bid.  
4. Select the header line for the other bid that you want to rank.
5. In the Rank field, enter a number.
6. Click Save.

## Reject a bid
1. Select the header line for the bid that you want to reject.
    * You can only accept, reject, or return one bid or lines within one bid at a time.  
2. Select the Mark check box.
    * If you select the Mark check box on the Header of the bid then all the lines will be marked as well. You could also choose to mark a subset of the lines within the bid to reject or accept those. It’s possible to accept one vendor’s bid for some lines of an RFQ, and then award other RFQ lines to a different vendor, however you need to do this in 2 steps, one bid at a time. If alternate lines are present, you can only accept either the original bid line or its alternate, but not both.  
3. Click Reject.
4. Click Parameters to open the drop dialog.
5. In the Reason reject field, enter or select a value.
    * The reason for rejection will be stored on the reply.  
6. Click OK.
7. Click OK.
8. Close the page.
9. Close the page.
10. Refresh the page.

## Accept a bid
1. Select the bid that you want to accept and then click the link in the Request for quotation field.
2. On the Action Pane, click Reply.
3. Click Accept.
    * If you have marked specific lines and not others then the accept action will only include the marked lines. If you want to accept all lines on the bid then you do not have to mark the lines.  
4. Click Parameters to open the drop dialog.
    * This allows you to record a reason for accepting the bid. The reason will be stored on the bid.  
5. In the Reason accept field, enter or select a value.
6. Click OK.
7. Click OK.
    * When you click OK this generates a purchase order based on the lines that are included in the RFQ acceptance. If there are other bids that have not been processed (accepted, rejected, or returned) then the system will prompt you to reject the remaining bids.  

## View the purchase order that's been generated
1. On the Action Pane, click General.
2. Click Purchase order.
    * Here you can see the purchase order that was generated when you accepted the bid.  
3. Close the page.
4. Close the page.
5. Close the page.
6. Close the page.

