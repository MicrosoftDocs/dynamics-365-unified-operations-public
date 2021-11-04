---
# required metadata

title: Set up general budget reservation rules and reservation types
description: This topic explains how to set up and modify general budget reservation rules and reservation types for Public sector.
author: AlexRenney
ms.date: 04/25/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BudgetReservation_PSN, BudgetReservationType_PSN
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
ms.search.industry: Public sector
ms.author: brpotter
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Set up general budget reservation rules and reservation types

[!include [banner](../includes/banner.md)]

Public sector entities often use general budget reservations to set aside or earmark budgeted funds so that they aren't available for other purposes. To use general budget reservations, you must specify budgetary rules, and you must set up at least one general budget reservation type.

> [!NOTE]
> If your organization is in France, you will use commitments instead of general budget reservations.

The following illustration shows how to set up the system to use general budget reservations. Each numbered step corresponds to a section of this topic.

![Setup for general budget reservation.](media/gbr-rules-reservations-process.jpg "Setup for general budget reservation")

## Prerequisites

The following table shows the prerequisites that must be in place before you start.

<table>
<thead>
<tr>
<th>Category</th>
<th>Prerequisite</th>
</tr>
</thead>
<tbody>
<tr>
<td>Related configuration tasks</td>
<td>
<ul>
<li>You must use posting definitions, unless you don't activate commitment accounting.</li>
<li>Budget control configuration must be activated, budget control must be turned on, and an original budget must be confirmed.</li>
</ul>
</td>
</tr>
</tbody>
</table>

## Set up budgeting parameters for regulatory accounting

To set up budgeting parameters for regulatory accounting, follow these steps.

1. Go to **Budgeting \> Setup \> Basic budgeting \> Budgeting parameters**.
2. On the **Budget** tab, on the **Regulatory** FastTab, set the **General budget reservations** option to **Yes**.
3. Optional: On the **Encumbrance control** FastTab, set the **Prevent carry-forward encumbrance increases** and **Use session date for GBR accounting** options to **Yes**.
4. Optional: On the **General budget reservation prior year corrections** FastTab, set the **Allow prior year corrections** option to **Yes**.

## Select source documents for budget control

To earmark budget funds for this purchasing method, configure the general budget reservation as a source document. 

To select source documents, follow these steps.

1. Go to **Budgeting \> Setup \> Budget control \> Budget control configuration**.
2. Select **Create draft**.
3. On the **Documents and journals** tab, select the **General budget reservation** and **Check at line entry** check boxes.
4. On the **Activate budget control** tab, select **Activate**.

When you create a general budget reservation, budget source-tracking entries and accompanying budget-checking results are also created, and budget checking occurs when you create a line or post a reservation.

## Set up general ledger information for general budget reservations

To help guarantee that general ledger accounts are correct, you must configure how general budget reservations are used to record accounting commitments.

To set up general ledger information for general budget reservations, follow these steps.

1. Go to **General ledger \> Ledger setup \> General ledger parameters**.
2. On the **Ledger** tab, on the **Accounting rules** FastTab, set the **Use posting definitions** option to **Yes**. Then, in the confirmation message box that appears, select **Yes**.
3. Select the **General budget reservations** check box. Then close the notification.

    When you select the **General budget reservations** check box, the **Enable encumbrance process** and **Enable pre-encumbrance process** check boxes are automatically selected and aren't available. These two processes are required when general budget reservations are used.

## Create posting definitions

You can configure transaction posting definitions to update different general ledger accounts for different types of general budget reservation.

To create posting definitions for general budget reservations, follow these steps.

1. Go to **General ledger \> Posting setup \> Posting definitions**.
2. Select **New**.
3. In the **Posting definition** field, enter a brief code for the definition (for example, **GBREnc**).
4. In the **Description** field, enter a description (for example, **GBR encumbrance**).
5. In the **Module** field, select **Budget reservation**.
6. Set the remaining fields on the page as you require.
7. On the Action Pane, on the **Posting definition** tab, in the **View** group, select **Transaction posting definitions**.
8. On the **Transaction posting definitions** page, on the **Budget reservation** tab, in the **Select** field group, **General budget reservation** is selected by default. Select **General budget reservation year-end close** if this option is appropriate.
9. Select **New**.
10. In the **Reservation type** field, select one of the following values:

    - To enter a new transaction posting definition that applies to all reservation types, select **All**. Then, in the **Posting definition** field, select the definition that you created earlier.
    - To enter a new transaction posting definition that applies to a single reservation type, select **Table**. Then, in the **Reservation type relation** field, select a reservation type. In the **Posting definition** field, select the definition that you created earlier.

11. Repeat steps 2 through 10 to create as many additional posting definitions as you require, and then select **Close**.

## Set up the reservation number sequence

To set up the number sequence that general budget reservations use, follow these steps.

1. Go to **Budgeting \> Setup \> Basic budgeting \> Budgeting parameters**.
2. On the **Number sequences** tab, in the **Reference** column, select the entry for general budget reservations.
3. In the **Number sequence code** column, select a code.

    You can also assign unique number sequences by reservation type.

## Create a general budget reservation type

The reservation type determines the nature of a general budget reservation, such as the type of document that relieves the budget reservation, the workflow that is used to approve the reservation, and the number sequence that is used.

To create a general budget reservation type, follow these steps.

1. Go to **Budgeting \> Setup \> General budget reservations \> Reservation type**.
2. Select **New**.
3. In the **Reservation type** field, enter a name for the reservation type.
4. In the **Description** field, enter a description.
5. In the **Relieving document** field, **Purchase requisition** is selected by default. Select a different value as you require. This field specifies the type of document that will relieve the general budget reservation.

    > [!NOTE]
    > After you create a general budget reservation by using the reservation type, you can't change the reservation to another type.

6. On the **Carry-forward budget** FastTab, set the **Reduce carry-forward budget** option to **Yes** if any remaining carry-forward budget that is associated with a general budget reservation should be reduced to 0 (zero) when the reservation is finalized.
7. Optional: If an approval task or other task is required before the reservation can be posted, on the **Workflow** FastTab, in the **Workflow** field, select a general budget reservation workflow. If you leave this field blank, a workflow isn't required in order to post general budget reservations of this type.
8. Optional: If different reservation types use unique number sequences, on the **Number sequence** FastTab, in the **Number sequence code** field, select the number sequence code that this reservation type should use.

    If a number sequence isn't configured for a reservation type, the budget parameters number sequence is used.

9. Repeat steps 2 through 8 to create any additional reservations types that you require.

## Next step

After you've set up rules, you can create general budget reservations. The reservations will apply to the documents that are required for the purchasing method that you select (purchase requisition, purchase order, or vendor invoice).

## Technical information for system administrators

If you don't have access to the pages that are used to complete this task, contact your system administrator, and provide the information that is shown in the following table.

| Category                  | Prerequisite                                                  |
|---------------------------|---------------------------------------------------------------|
| License configuration key | Public sector \> General budget reservation                   |
| Security roles            | You must be a member of the **Budget manager** security role. |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]