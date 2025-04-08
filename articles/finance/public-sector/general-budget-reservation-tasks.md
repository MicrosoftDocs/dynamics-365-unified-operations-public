---
title: Maintain general budget reservations
description: Learn how to complete typical tasks for general budget reservations, including a step-by-step process on creating and encumbering a general budget reservation.
author: AlexRenney
ms.author: twheeloc
ms.topic: article
ms.date: 04/25/2019
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.industry: Public sector
ms.search.validFrom: 2018-10-31
ms.search.form: BudgetReservation_PSN, BudgetReservationYearEndClose_PSN
ms.dyn365.ops.version: 8.1
---

# Maintain general budget reservations

[!include [banner](../includes/banner.md)]

This article explains how to complete typical tasks for general budget reservations.

## Create and encumber a general budget reservation

After you set up your system to use general budget reservations, you can create reservation documents. General budget reservations are available to the documents that are required for the purchasing method that you select. These purchasing methods include purchase order, purchase requisition, and vendor invoice.

To create a general budget reservation, follow these steps.

1. Go to **Budgeting \> General budget reservations**.
2. Select **New**.
3. In the **Budget reservation** dialog box, set the fields as required.

    - The reservation type determines the type of document that will relieve this general budget reservation: a purchase requisition, a purchase order, or a vendor invoice.
    - If you select a purchase requisition reference in this dialog box, an upstream purchase requisition will be relieved. In this case, the reservation type you select must be configured for **Purchase order** or **Vendor invoice** as the relieving document.

4. Select **OK**.
5. On the details page, on the header, set the fields as required.
6. On the **General budget reservation lines** FastTab, select **Add line**. Enter the information for the first line of your reservation. Repeat this step until you've entered all the lines.

    - If a purchase requisition applies to the budget reservation but wasn't referenced earlier in the **Budget reservation** dialog box, on the **Line details** FastTab, you can select the purchase requisition line that the selected line in the budget reservation references. Items and services on the selected requisition line, together with the procurement category, are passed to the general budget reservation line. This behavior applies to both procurement catalog items and non-catalog items.
    - The general budget reservation line won't reflect any child amounts on a referenced purchase requisition. These child amounts include discounts, charges, or taxes.

7. If you use project accounting, on the **Line details** FastTab, on the **Project** tab, set the fields as required.
8. If you use project accounting, on the **General budget reservation lines** FastTab, select **Committed costs**. The **Committed costs** page appears and shows the committed costs that are related to the selected line.
9. When you've finished filling in the header and line values, either submit the reservation to the workflow system or post it, depending on your setup.

## View a general budget reservation

You can view the details of a general budget reservation, such as information about the vendor, the items or services that were ordered, and budget specifics. You can also access the source documents that the reservation references.

1. Go to **Budgeting \> General budget reservations**.
2. Select the document number of the reservation that you want to view. The details page appears.
3. On the Action Pane, select **Accounting**, and then select **Subledger journal**, **View distributions**, or **Voucher** to see those entries.
4. To view any related purchase requisition, on the **Line details** FastTab, select the reference number of the purchase requisition.
5. To see a summary of the financial accounting, on the Action Pane, select **Manage \> Financial summary**. In the **Reservation line** list, you can select the line that you want to see details for.
6. To see details of the budget reservation relief, on the Action Pane, select **Manage \> Relief details**. To see the original document that relieves this general budget reservation (such as an invoice or purchase order), select **View relieving document**.

    You can also access the **General budget reservation relief details** page from the **General budget reservation financial summary** page by selecting **Relief details**.

## Modify a general budget reservation

If the reservation is in a workflow, recall the workflow status to **Draft**, follow these steps, and then resubmit the amended reservation to the workflow.

1. Go to **Budgeting \> General budget reservations**.
2. Open the reservation that you want.
3. On the Action Pane, select **Edit**.
4. Make any required changes. For example, you can add or delete lines.

    When a reservation line is already referenced by a purchase order or vendor invoice, your ability to change or delete lines is limited.

5. On the Action Pane, select **Post**.

## Delete a general budget reservation

1. Go to **Budgeting \> General budget reservations**.
2. Select the reservation to delete.

    Reservations can be deleted only if they have a reservation status and a workflow status of **Draft**. You can delete only reservations that have never been posted.

3. On the Action Pane, select **Delete**.
4. Select **Yes**.

## Cancel a general budget reservation

1. Go to **Budgeting \> General budget reservations**.
2. Select the reservation to cancel.

    Reservations can be canceled only if they have a reservation status and a workflow status of **Posted**. You can cancel only reservations that have no downstream relieving activity.

3. On the Action Pane, select **General budget reservation \> Cancel**.
4. Select **Yes**.

    - The general ledger and budget control updates occur, and the transaction is recorded in the transaction log.
    - This procedure doesn't delete the reservation. It just cancels the reservation and generates the accounting and budget entries to reverse the impact of the document that was originally posted.
    - You can cancel a whole general budget reservation, but you can't cancel individual lines.

## Finalize a general budget reservation

1. Go to **Budgeting \> General budget reservations**.
2. Open the reservation to finalize.

    Reservations can be finalized only if they have a reservation status and a workflow status of **Posted**. You can finalize only reservations or reservation lines that have downstream relieving activity.

3. Follow one of these steps:

    - To finalize the whole budget reservation, on the Action Pane, select **General budget reservation \> Finalize**.
    - To finalize just one line, select it, and then, in the **General budget reservation lines** section, select **Finalize line**.
    - To finalize multiple lines, select them, and then, in the **General budget reservation lines** section, select **Finalize line**.

    Accounting and budget control entries are posted. The remaining balance is removed from the document and returned to budget, unless the document is a carry-forward document, and the associated fund or reservation type is set to **Reduce carry-forward budget**.

## Relieve a general budget reservation

There are three ways to consume or relieve a general budget reservation:

- **Purchase requisition** – Reference the general budget reservation directly on a purchase requisition line. To use this approach, specify the budget reservation line on the **Line details** FastTab, on the **Details** tab when you create the requisition. Then submit the requisition to the workflow system. The reservation is relieved, or consumed, when the requisition is approved.

    General budget reservations that are relieved by using a purchase requisition can also be assigned to purchase agreements. They are associated with the various purchase agreement lines. When a purchase requisition is created, if a line on it is associated with an item or category that is defined on a purchase agreement, only the general budget reservations that were previously assigned to the purchase agreement can be relieved.

- **Purchase order** – Reference the general budget reservation directly on a purchase order line. No purchase agreement is involved. To use this approach, specify the budget reservation line on the **Line details** FastTab, on the **General** tab when you create the purchase order. The reservation is relieved, or consumed, when the purchase order is confirmed.
- **Vendor invoice** – Reference the general budget reservation directly on a vendor invoice. To use this approach, specify the budget reservation line on the **Line details** FastTab, on the **Line details** tab. The reservation is relieved when the vendor invoice is posted.

After you post or confirm a document that references a general budget reservation, the budget reservation balance reflects the relieving amount. If you edit, cancel, or finalize the referencing document, the relieved amount shown isn't reduced or removed. There is no way to return a relieved amount to the balance on the referencing document.

### Create a purchase requisition, purchase order, or vendor invoice to relieve the general budget reservation

Follow these steps to reference a general budget reservation on a purchase requisition, purchase order, or vendor invoice.

1. Follow one of these steps:

    - Go to **Procurement and sourcing \> Purchase requisitions \> All purchase requisitions**.
    - Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
    - Go to **Accounts payable \> Invoices \> Pending vendor invoices**.

2. Select **New** to create a new document, or modify an existing draft document.
3. Establish the reference, and post the document.

    To more easily identify the general budget reservation that you want, select **Advanced selection options** under the reference field.

4. On the Action pane, on the **Financials** tab, select **View distributions**.

    - The ledger account on the new accounting distributions (parent and child) is set to the ledger account from the accounting distribution of the general budget reservation line.
    - The reference distribution on the new accounting distributions (parent and child) references the accounting distribution for the general budget reservation line.

## Carrying forward general budget reservations

For any general budget reservation that hasn't expired and still has a remaining balance at the end of the fiscal year, you can carry forward (roll over) the document to the new year. The carry-forward process creates all the accounting and budgeting entries that are required to close the document in the current year and open the document in the new year.

### Carry forward a general budget reservation to a new fiscal year

1. Go to **General ledger \> Period close \> General budget reservation year-end process**.
2. In the **General budget reservation year-end process** dialog box, in the **Year-end option** field, select whether to carry forward the associated budget for the reservation.
3. Select the fiscal year for **Closing parameters** and **Opening parameters**.
4. Select **Retrieve documents**.
5. In the query dialog box that appears, enter the criteria to find the reservations that you want to process and carry forward to the new year.
6. Select **OK** to show the reservations in the **General budget reservation year-end process** dialog box.
7. In the list, select the documents to include, and then select **Process**.
8. If you selected **Process and carry forward budget** in the **Year-end option** field, you receive a message that lists all the budget entries that were created and all the general budget reservations that were processed. Any document that wasn't processed because of an error is also listed.

### Reduce carry-forward budget in a new fiscal year

If you've turned on budget control, you can reduce carry-forward budget for any carry-forward general budget reservations that are finalized, and that have a remaining balance. In this way, you can help guarantee that funds from the previous year aren't spent on purchases in the new year.

If the **Reduce carry-forward budget** option is set to **Yes** on the related fund or the reservation type, when you finalize the document in the new fiscal year, the remaining document balance and any remaining carry-forward budget are reduced to 0 (zero).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
