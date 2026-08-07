---
title: View and respond to RFQs in the supplier portal (preview)
description: Learn how vendors can view, bid on, and manage requests for quotation (RFQs) using the supplier portal's vendor bidding workspace.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 08/07/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# View and respond to RFQs in the supplier portal (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The **Vendor bidding** workspace in the supplier portal lets vendors view the requests for quotation (RFQs) that the buying company invited them to and submit bids. The workspace also shows all RFQs that the vendor lost or won.

## Open the vendor bidding workspace

To open the **Vendor bidding** workspace, sign in to the supplier portal and complete any of the following steps:

- On the top navigation bar, select **Vendor bidding** and then select any of the views listed.
- On the home page, select any of the links in the **Vendor bidding** panel.

The workspace provides the following tiles. Each tile represents a category or status of RFQs. Each tile shows the number of RFQs in that category and provides a link to view the related list of RFQs.

- **Bid invites** – RFQs that the vendor is invited to respond to. This category includes RFQs where bidding can begin or where an amended RFQ requires a new submission.
- **Submitted** – RFQs the vendor submitted that are awaiting the purchaser's response.
- **In progress** – RFQs that the vendor or a contact person is working on but hasn't yet submitted.
- **Awarded** – RFQs where the purchaser awarded at least one line item in the vendor's bid.
- **Returned** – RFQs that the purchaser returned so the vendor can provide more information or update the bid.
- **Lost** – Bids where all lines are rejected and the bid is closed as lost.
- **Declined** – RFQs where the vendor declined to participate in bidding.

## Bid on an RFQ

Bidding is the procedure through which a vendor submits an offer in response to an RFQ. To submit a bid, follow these steps:

1. Go to **Vendor bidding** > **Bid invites** and open the RFQ.
1. Examine the RFQ details, including the **General** tab for header information, the **Lines** tab for line items, and any amendments or comments provided by the purchaser.
1. Select **Bid** to start bidding on the RFQ.
1. Respond to the RFQ by entering your bid details. Work as follows:

    - When editing is enabled for bidding fields on the headers and lines of an RFQ, you can enter your bid directly in the **Lines** grid. Consider any additional bid information that you need to add to the line details.
    - At any time before the expiration date, save a bid by selecting **Save as draft** on the toolbar. This action lets you return later to finish and submit the bid. While you're working on a bid, and until you submit it, the bid is available in the **Bids in progress** section.
    - To remove all entered bid data on the **Lines** tab and restore the original RFQ details, select **Reset to default** on the toolbar.
    - To reset only one line, select **Reset line** from the line **Actions** column.
    - To work with alternates, select **Add alternate** or **Remove alternate** in the line grid. If the purchaser enables **Allow alternates on response lines** for a specific RFQ, you can only add alternate items for lines of the *Category* type.
    - When you're done reviewing and updating a line, select the check box in the **Done** column to mark it as complete.
    - To mark all lines as complete, select the **Mark as done** button at the top of the **Lines** grid.
    - The **Lines** and **Amendments** tabs include a **Communications** panel that vendors and purchasers can use to communicate.
        - Purchaser-provided information remains read-only. Vendor-added comments and attachments can be modified or removed.
        - Read and provide clarifications or notes in the **Comments** section.
        - Upload documents using the **Add Attachment** button.
    - If the Q&A feature is enabled for the RFQ, use the **Q&A** tab to ask questions and view answers from the purchaser. This tab is available if **Q&A** is set to *Yes* on the RFQ and is visible based on the cutoff date.
    - If any questions are shown on the **Questionnaire** tab, complete all required questions as part of the bid submission. You must complete the questionnaire in full before the system allows you to submit the bid.

1. Select **Submit** on the toolbar to submit the bid.

### Recall and resubmit a bid

You can recall and update a submitted bid up until the expiration date.

1. Go to **Vendor bidding** > **Submitted** and open the bid.
1. To bring the bid back to an editable state, select **Recall** on the toolbar.
1. Make changes and resubmit before the RFQ expires.

### Respond to a returned bid

If the purchaser returns a submitted bid, the vendor can find it on the **Returned** tile of the **Vendor bidding** workspace.

1. Go to **Vendor bidding** > **Returned** and open the returned bid.
1. Go to the **General** tab and check the **Reason Code** and **Reason comment** on the bid **General** tab.
1. Take the necessary actions and resubmit.

### Decline an RFQ

If you don't want to bid on an RFQ, open it and select **Decline** from the toolbar. After you decline, you can't recall the action and enter a bid.

## Amended RFQs

If the purchaser amends an RFQ, you must enter a new bid for it. Information about the amendment is on the **Amendments** tab of the RFQ page. Amended RFQs appear on the **Bid invites** page.

## Related information

- [Supplier portal overview](supplier-engagement-portal-overview.md)
- [Requests for quotation (RFQs) overview](../procurement/request-quotations.md)
- [View and confirm purchase orders in the supplier portal](supplier-engagement-portal-purchase-orders.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
