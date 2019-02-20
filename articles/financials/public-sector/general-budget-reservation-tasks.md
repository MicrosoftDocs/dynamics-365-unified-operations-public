---
# required metadata

title: Maintain a general budget reservation
description: This topic provides steps for working with general budget reservations for public sector in Microsoft Dynamics 365 for Finance and Operations.
author: ShylaThompson
manager: AnnBe
ms.date: 02/20/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
ms.search.industry: Public sector
ms.author: brpotter
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Maintain a general budget reservation

[!include [banner](../includes/banner.md)]

This topic walks you through completign common tasks for general budget reservations.

## Create and encumber a general budget reservation
After you set up your system to use general budget reservations, you can create reservation documents. General budget reservations are available to the documents that are required for the purchasing method you choose. These methods include purchase order, purchase requisition, and vendor invoice. 

To create a general budget reservation, use the following steps.

1.  Go to **Budgeting \> General budget reservations**.

2.  Click **New**.

3.  In the **Creation** slider enter all necessary fields.

    -   Reservation type decides which type of document will relieve this General budget reservation (Purchase requisition, Purchase order or Vendor invoice).

    -   Selecting a Purchase requisition in this dialogue relieves an upstream Purchase requisition. Reservation type must be Purchase order or Vendor invoice relieved in this case.

4.  Click **OK**.

5.  In the details page, fill in the fields as necessary in the General budget reservation header.

6.  Under **General budget reservation** lines, click **Add line**. Enter the information for the first line of your reservation. Repeat this step until you have entered all lines.

    -   If a purchase requisition applies to the budget reservation and wasn’t referenced earlier in the creation dialogue, on the Line details section, you can select the purchase requisition line that the selected line in the budget reservation references. Items and services on the selected requisition line, including procurement category, are passed to the general budget reservation line. This is true for both procurement catalog items and non-catalog items.

    -   Any child amounts on a referenced purchase requisition, such as discounts, charges, or taxes, will not be reflected on the general budget reservation line.

7.  If you use project accounting, on the Line details section, click the Project tab, and then fill out the fields as necessary.

    -   If you use project accounting, on the General budget reservation lines section, click Committed costs. The Committed costs page opens, displaying the committed costs related to the selected line.

8.  When you are finished filling out the header and line values, either **Submit to workflow** or click **Post** (dependent on your setup).

## View a general budget reservation

You can view the details of a general budget reservation, including information about the vendor, items or services ordered, and budget specifics. You can also access the source documents that the reservation references.

1.  Go to **Budgeting \> General budget reservations**.

2.  On the list page, click the Document number of any reservation that you want to view. The details window opens.

3.  On the Action bar, click **Accounting \> Subledger journal**, View distributions or Voucher to see those entries.

4.  To view any related purchase requisition, click the **Line details** section, then click the purchase requisition reference number.

5.  To see a summary of the financial accounting, on the Action bar click **Manage \> Financial summary**. In the Reservation line list, you can select the line for which you want to see details.

6.  To see details of the budget reservation relief, on the Action bar click **Manage \> Relief details**. To see the original document that relieves this general budget reservation (such as an invoice or purchase order), click **View relieving document**.

    -   You can also access the General budget reservation relief details page from the **General budget reservation financial summary** page, by clicking Relief details from there.

## Modify a general budget reservation

If the reservation is in workflow, recall the workflow status to Draft status, follow the steps below, and then resubmit the amended reservation to workflow.

1.  Go to **Budgeting \> General budget reservations**.

2.  On the list page, open the reservation that you want.

3.  On the Action bar click **Edit**.

4.  Make any changes you want, including adding or deleting lines.

    -   When a reservation line has already been referenced by a purchase order or vendor invoice, your ability to change or delete lines will be limited.

5.  On the Action bar, click **Post**.

## Delete a general budget reservation

1.  Go to **Budgeting \> General budget reservations**.

2.  On the list page, click the reservation that you want to delete.

    -   It must have a Reservation status and Workflow status of Draft to be
        deleted. Delete can only be done on a reservation that has never before
        been posted.

3.  On the Action bar, click **Delete**.

4.  Click **Yes**.

## Cancel a general budget reservation

1.  Go to **Budgeting \> General budget reservations**.

2.  On the list page, click the reservation that you want to cancel.

    -   It must have a Reservation status and Workflow status of Posted to be canceled. Cancel can only be done on a reservation that has no downstream relieving activity.

3.  On the Action bar, click **Cancel**.

4.  Click **Yes**.

    -   The general ledger and budget control updates occur and the transaction is recorded in the Transaction log.

    -   This does not delete the reservation but cancels it, generating the accounting and budget entries to reverse the impact of the originally posted document.

    -   You can cancel an entire general budget reservation, not individual lines.

## Finalize a general budget reservation

1.  Go to **Budgeting \> General budget reservations**.

2.  Open the reservation that you want to finalize.

    -   It must have a Reservation status and Workflow status of Posted to be finalized. Finalize can only be done on a reservation or reservation line that has downstream relieving activity.

3.  With the reservation open, do one of the following:

    -   To finalize the whole budget reservation, on the Action bar, click **General budget reservation \> Finalize**.

    -   To finalize one line only, select it and on the **General budget reservation lines** section, click **Finalize line**.

    -   To finalize multiple lines, select them and on the **General budget reservation lines** section, click Finalize line.

4.  Accounting and budget-control entries are posted. The remaining balance is removed from the document and returned to budget unless it’s a carry forward document and the associated fund or reservation type is set to **Reduce carry-forward budget**.

## Relieve a general budget reservation

There are three ways to consume or relieve a general budget reservation:

-   **Purchase requisition** – Reference the general budget reservation directly on a purchase requisition line. To do this, specify the budget reservation line in Line details \> Details when you create the requisition. Submit to workflow. The reservation is relieved, or consumed, when the requisition is approved.

    -   Purchase requisition relieved General budget reservations may also be assigned to Purchase agreements. They are associated with the various Purchase agreement lines. When a Purchase requisition is created with a line that’s associated with an item or category defined on a Purchase agreement, the available General budget reservation that can be relieved are limited to those that have been previously assigned to the Purchase agreement.

-   **Purchase order** - Reference the general budget reservation directly on a purchase order line. No purchase agreement is involved. To do this, specify the budget reservation line in Line details \> General when you create the Purchase order. The reservation is relieved, or consumed, when the purchase order is confirmed.

-   **Vendor invoice** - Reference the general budget reservation directly on a vendor invoice. To do this, specify the budget reservation line in Line details \> Line details. The reservation is relieved when the vendor invoice is posted.

After you post or confirm a document that references a general budget reservation, the budget reservation balance reflects the relieving amount. If you edit, cancel, or finalize the referencing document, the relieved amount shown is not reduced or removed; there is no way to return a relieved amount to the balance on the referencing document.

### Create a Purchase requisition, Purchase order or Vendor invoice to relieve the General budget reservation

Use the following steps to reference a general budget reservation on a purchase requisition, purchase order or vendor invoice.

1.  Do one of the following:

    -   Go to **Procurement and sourcing \> Purchase requisitions \> All purchase requisitions**.

    -   Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.

    -   Go to **Accounts payable \> Vendor invoices \> Pending vendor invoices**.

2.  Create your desired document by clicking **New** or modify an existing draft document.

3.  Establish the reference and post the document.

    -   Use Advanced selection options under the reference field to more easily identify the desired General budget reservation.

4.  Click **Financials**, then click **Distribute amounts**.

    -   The ledger dimension field on the new accounting distributions (parent and child) is set to the ledger dimension from the budget reservation line accounting distribution.

    -   The reference distribution on the new accounting distributions (parent and child) references the budget reservation line accounting distribution.

## Carrying forward general budget reservations

For any general budget reservation that has not expired and hold a remaining balance at the fiscal year-end, you can carry forward (roll over) the document to the new year. The carry-forward process creates all the accounting and budgeting entries to close the document in the current year and open the document in the new year.

### Carry forward a general budget reservation to a new fiscal year

1.  Go to **General ledger \> Period close \> General budget reservation year-end process**.

2.  On the **General budget reservation year-end process** page, in the **Year-end option** list, select whether to carry forward budget the associated budget for the reservation.

3.  Select the fiscal year for the **Closing parameters** and **Opening parameters**.

4.  Click **Retrieve documents**.

5.  In the query page that appears, enter the criteria to find the reservations you want to process and carry forward to the new year.

6.  Click **OK** to display the reservations in the General budget reservation year-end process page.

7.  Select the documents you’d like to include from the list and then click **Process**.

8.  If you selected **Process and carry forward budget** in the **Year-end option list**, a message displays the list of all the budget entries that were created and all the general budget reservations that were processed. Any document not processed because of an error is also listed.

### Reduce carry-forward budget in a new fiscal year

If you have enabled budget control, you can reduce carry-forward budget for any carry-forward general budget reservations that are finalized with a remaining balance. This ensures that prior-year funds are not spent on new-year purchases.
If the Reduce carry-forward budget check box is enabled on the related fund or on your reservation type, then finalizing the document in the new fiscal year reduces the remaining document balance to zero and reduces any remaining carry-forward budget to zero.
