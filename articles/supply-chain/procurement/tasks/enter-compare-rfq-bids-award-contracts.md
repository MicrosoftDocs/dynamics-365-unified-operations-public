--- 
# required metadata 
 
title: Enter and compare RFQ bids, and award contracts
description: This procedure shows you how to enter replies to an RFQ, score and compare bids, and then award the bid to one of the vendors. 
author: mkirknel
manager: AnnBe 
ms.date: 02/26/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchRFQCaseTableListPage, PurchRFQCaseTable, PurchRFQReplyTable, PurchRFQCompare, PurchRFQEditLines, PurchRFQEditLinesParameters, PurchTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---

# Enter and compare RFQ bids, and award contracts

[!include [task guide banner](../../includes/task-guide-banner.md)]

This procedure shows you how to enter replies to an RFQ, score and compare bids, and then award the bid to one of the vendors. You can use this procedure in demo data company USMF. Before you start, you must have an RFQ with two lines that has been sent to at least two vendors. Complete [Create a request for quotation](create-request-quotation.md) as a prerequisite to create this. You need to have set up scoring criteria before you can run this procedure.

You can enter the bid as a vendor, or you can enter it as a procurement professional. 

## Enter a reply as a vendor

1.  Go to Dashboard
2.  Click **vendor bidding**.
3.  In the list of new bid invitations find a RFQ that was just sent.
4.  Select the RFQ, to review what was requested.
5.  Click **RFQ attachments** to review any attachments that have been added.
6.  Click **Bid**, and the fields will open for editing, notice that the Bid progress status have changed to **Vendor is updating**

7.  Enter the bid reply values on header and lines.

8.  Click **Bid attachments** if any attachments should be added to the bid

9.  The bidding guiding items will indicate if any documents are required.

10. The amendments will show if the RFQ has been amended.

11. Any questionnaires in the questionnaire tab has to be answered.

12. In the line details you can find extended information about the line.

13. Click **Reset from RFQ** only if you need to delete the entered values and reset to the original RFQ values.

14. The bid can be saved at any time and be picked up later for further processing as long as it is before the expiration date and time. In this case you can find the bid under **Bids in progress** list in the Vendor bidding workspace.

15. Click **Submit** when the bid is ready to be sent; If you do not want to bid then click **Decline**.

16. When the bid is submitted you can recall it at any time before the expiration date and time. Note when the bid is recalled then it is not regarded as submitted.

17. The submitted bid will be available in Submitted bid list in the Vendor bidding workspace.

18. When the bid is accepted or rejected by the procurement department it will appear in the Awarded bid or Lost bids on the Vendor bidding workspace

## Enter a reply from a vendor as a procurement professional

1.  Ensure that the permission to edit vendors bids is setup: **Procurement and sourcing parameters \>Request for quotations \> Purchaser can edit vendors bid**.

2.  Go to **Procurement and sourcing \> Requests for quotations \> All requests for quotations**.

3.  Select an RFQ that has a status of **Sent** and then click the link on the request for quotation case number.

4.  Click **Manage replies**, this opens a page where you find a RFQ per vendor that was invited to bid.

5.  Select one RFQ that has not been answered (The **Reply progress** should be **Not Started**).

6.  Click **Edit** and select **Edit RFQ reply** - Now you as a procurement professional have opened the **RFQ reply** page and can enter the reply on behalf of the vendor. Notice that the Bid progress is **Purchaser is updating**.
7.  Enter the bid data and the click **Submit** when finished.

## Score the bids

1.  Go to All request for quotation and select the RFQ case which replies you want to score.

2.  Click **Manage replies**.

3.  Select the reply that you want to score.

4.  Click **Header** to view the scoring of the bid.

5.  Expand the **Bid scoring** section.

6.  In the **Score** field, enter a number for one of the scoring criteria.

    -   If you hover over one of the scoring criteria a tooltip shows the range that you have to score within. In this demo you can add a number between 1 and 5 to any of the criteria.

7.  Select another scoring criterion.

8.  In the **Score** field, enter a number.

9.  Expand the **Questionnaires** section.

    -   If the RFQ case has a questionnaire that was sent to the vendors, you can enter their responses in the questionnaire section.

10. Close the page.

11. Repeat steps 1 through 10 for all bids.

## Compare the replies

1.  On the Action Pane, click **General > Compare replies**.

2.  In the **Rank** field, enter a number.

    > This page shows the bids with the header and lines, and the total score on the header level. You can compare the lines by sorting in the grid so that comparable lines are next to each other. The information also includes: 
    > - **Quantity**: The quantity quoted by the vendor. This might not equal the quantity specified in the RFQ. 
    > - **Net amount**: The price quoted by a vendor, after subtracting any discounts, for the items on the line. 
    > - **Deviation**: The number of days that the delivery date in the bid header or line deviates from the requested delivery date in the RFQ header or RFQ line. You can enter a rank for each bid.

4.  Select the header line for the other bid that you want to rank.

5.  In the **Rank** field, enter a number.

6.  Click **Save**.

## Reject a bid

1.  Select the header line for the bid that you want to reject.

    -   You can only accept, reject, or return one bid or lines within one bid at a time.

2.  Select the **Mark** check box.

    -   If you select the **Mark** check box on the header of the bid then all the lines will be marked as well. You could also choose to mark a subset of the lines within the bid to reject or accept those. It’s possible to accept one vendor’s bid for some lines of an RFQ, and then award other RFQ lines to a different vendor, however you need to do this in 2 steps, one bid at a time. If alternate lines are present, you can only accept either the original bid line or its alternate, but not both.

3.  Click **Reject**.

4.  Click **Parameters** to open the drop dialog.

5.  In the **Reason reject** field, enter or select a value.

    -   The reason for rejection will be stored on the reply.

6.  Click **OK**.

7.  Click **OK**.


## Accept a bid

1.  Select the bid that you want to accept and then click the link in the **Request for quotation** field. If you are in the compare form then please note that the highlighted bid having focus is the bid that the system are taking into account when accepting. It is only possible to accept lines from one bid at a time.

2.  On the Action Pane, click **Reply**.

3.  Click **Accept**.

    -   If you have marked specific lines and not others then the accept action will only include the marked lines. If you want to accept all lines on the bid then you do not have to mark the lines.

4.  Click **Parameters**.

    -   This allows you to record a reason for accepting the bid. The reason will be stored on the bid.

5.  In the **Reason accept** field, enter or select a value.

6.  Click **OK**.

7.  Click **OK**.

    -   When you click **OK** this generates a purchase order based on the lines that are included in the RFQ acceptance. If there are other bids that have not been processed (accepted, rejected, or returned) then the system will prompt you to reject the remaining bids.

## View the purchase order that's been generated

1.  On the Action Pane, click **General**.

2.  Click **Purchase order**.

    -   Here you can see the purchase order that was generated when you accepted
        the bid.
