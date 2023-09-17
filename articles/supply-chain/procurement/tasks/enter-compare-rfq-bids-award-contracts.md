--- 
# required metadata 
 
title: Enter and compare RFQ bids and award contracts
description: This article explains how to enter replies to a request for quotation (RFQ), score and compare bids, and then award the contract to one of the vendors. 
author: GalynaFedorova
ms.date: 07/09/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchRFQCaseTableListPage, PurchRFQCaseTable, PurchRFQReplyTable, PurchRFQCompare, PurchRFQEditLines, PurchRFQEditLinesParameters, PurchTable, PurchTablePart, PurchRFQCompareLinePrices, PurchRFQCompareRFQ
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

# Enter and compare RFQ bids and award contracts

[!include [banner](../../includes/banner.md)]

This article explains how to enter replies to a request for quotation (RFQ), score and compare bids, and then award the contract to one of the vendors. You can use this procedure in the **USMF** demo data company.

Before you start this procedure, you must have an RFQ that has two lines, and that has been sent to at least two vendors. To create this RFQ, complete the [Create a request for quotation](create-request-quotation.md) procedure. Scoring criteria must also be set up before you can complete this procedure.

You can enter the bid as either a vendor or a procurement professional. For more information, see [Set up and maintain vendor collaboration](../set-up-maintain-vendor-collaboration.md).

## Enter a reply as a vendor

1. Go to **Vendor collaboration \> Workspaces \> Vendor bidding**.
2. In the **New bid invitations** list, find an RFQ that was just sent. Select the RFQ to review what was requested.
3. Select **RFQ attachments** to review any attachments that have been added.
4. Select **Bid** to make the fields editable. Notice that the **Bid progress** field is set to **Vendor is updating**.
5. On the header and lines, enter the values from the bid reply.
6. If any attachments should be added to the bid, select **Bid attachments**.
7. Select the **Bidding guiding items** FastTab to view whether any documents are required.
8. Select the **Amendments** FastTab to view whether the RFQ has been amended.
9. Select the **Questionnaire** FastTab. Any questionnaires that appear here must be answered.
10. Select the **Line details** FastTab to view extended information about the line.
11. Select **Reset from RFQ** only if you must reset the values that have been entered to the original RFQ values.
12. You can save the bid at any time and do additional processing later, provided that the expiration date and time haven't passed. In this case, you can find the bid in the **Bids in progress** list in the **Vendor bidding** workspace.
13. When the bid is ready to be sent, select **Submit**. If you don't want to bid, select **Decline**. Submitted bids are available in the **Submitted bids** list in the **Vendor bidding** workspace.  
14. After the bid is submitted, you can recall it at any time before the expiration date and time. Note that when a bid is recalled, it isn't treated as submitted. When the bid is accepted or rejected by the procurement department, it appears in either the **Awarded bids** or **Lost bids** list in the **Vendor bidding** workspace.  

## Enter a reply from a vendor as a procurement professional

1. Make sure that the permission to edit vendor bids is set up. Go to **Procurement and sourcing \> Setup \> Procurement and sourcing parameters**. On the **Request for quotations** tab, set the **Purchaser can edit vendors bid** option to **Yes**.
2. Go to **Procurement and sourcing \> Requests for quotations \> All requests for quotations**.
3. Select an RFQ that has a status of **Sent**, and then select the link in the **Request for quotation case** field.
4. Select **Manage replies**. The page that appears shows an RFQ for each vendor that was invited to bid.
5. Select an RFQ that hasn't been replied to. (The **Reply progress** field should be set to **Not started**.)
6. Select **Edit \> Edit RFQ reply**. The **RFQ reply** page appears. As a procurement professional, you can now enter the reply on behalf of the vendor. Notice that the **Bid progress** field is set to **Purchaser is updating**.  
7. Enter the bid data. When you've finished, select **Submit**.

## Score the bids

1. On the **All requests for quotations** page, select the RFQ case that you want to score replies for.
2. Select **Manage replies**.
3. Select the reply to score.
4. Select **Header** so that you can view the scoring for the bid.
5. On the **Bid scoring** FastTab, enter a number in the **Score** field for one of the scoring criteria. If you hover over a scoring criterion, a tooltip shows the range that the score must be within. In this demo, you can enter a number between 1 and 5 for any of the scoring criteria.  
6. Repeat step 5 for another scoring criterion.
7. If the RFQ case has a questionnaire that was sent to the vendors, you can enter the vendor responses on the **Questionnaires** FastTab.
8. Close the page.
9. Repeat steps 1 through 8 for all the other bids.

## Compare the replies

1. On the Action Pane, on the **General** tab, select **Compare replies**.
2. In the **Rank** field, enter a number.  
    - This page shows the bids, together with the header and line information, and also the total score at the header level. You can compare the lines by sorting the grid so that comparable lines are next to each other. The following information is also included:
    - **Quantity** – The quantity that the vendor quoted. This quantity might not equal the quantity that is specified in the RFQ.
    - **Net amount** – The price that the vendor quoted for the items on the line, minus any discounts.
    - **Deviation** – The number of days by which the delivery date on the bid header or line differs from the requested delivery date on the RFQ header or line. You can enter a rank for each bid.  
3. Select the header line for the other bid that you want to rank.
4. In the **Rank** field, enter a number.
5. Select **Save**.

## Reject a bid

1. Select the header line for the bid that you want to reject. You can accept, reject, or return only one bid or the lines on only one bid at a time.
2. Select the **Mark** check box.  
    - If you select the **Mark** check box on the header of the bid, all the lines are also marked. To reject or accept only some of the lines on the bid, you can mark just those lines. Additionally, you can accept one vendor's bid for some lines of an RFQ and then award other RFQ lines to a different vendor. However, you must do one bid at a time.  
    - If alternate lines are present, you can accept either the original bid line or its alternate, but not both.  
3. Select **Reject**.
4. Select **Parameters**, and then, in the **Reason reject** field, enter or select your reason for rejecting the bid. The reason is stored in the reply.  
5. Select **OK**.
6. Select **OK**.

## Accept a bid

1. Select the bid to accept, and then select the link in the **Request for quotation** field. If you're on the **Compare request for quotation replies** page, the highlighted bid that has focus is the bid that the system will consider during the Accept action. You can accept lines from only one bid at a time.  
2. On the Action Pane, select **Reply**.
3. Select **Accept**. If you marked only specific lines, the Accept action will include only those lines. If you want to accept all the lines on the bid, you don't have to mark the lines.  
4. Select **Parameters**, and then, in the **Reason accept** field, enter or select your reason for accepting the bid. The reason is stored in the bid.  
5. Select **OK**.
6. Select **OK**. When you select **OK**, a purchase order is generated based on the lines that are included in the RFQ acceptance. If there are other bids that haven't been processed (accepted, rejected, or returned), the system prompts you to reject them.  

## View the purchase order that is generated

On the Action Pane, on the **General** tab, select **Purchase order**. The page that appears shows the purchase order that was generated when you accepted the bid.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]