---
# required metadata

title: General budget reservation rules and reservation types
description: This topic provides information about setting up and modifying general budget reservation rules and reservation types for public sector in Microsoft Dynamics 365 for Finance and Operations.
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
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# General budget reservation rules and reservation types

[!include [banner](../includes/banner.md)]

General budget reservations are often used by public sector entities to set aside or earmark budgeted funds so that they are not available for other purposes. To use general budget reservations, you must specify budgetary rules to enable your system to use them, and you must set up at least one general budget reservation type with the settings you want.

If your organization is in France, you will use commitments instead of general budget reservations.

The following illustration shows the steps that are required for setting up the system to use general budget reservations. The numbers correspond to the procedures later in this topic.

![Flow chart for general budget reservation setup](media/b3be3f5fb3656de3f42f96b6dac4f74c.jpg)

## Prerequisites

The following table shows the prerequisites that must be in place before you start.

| **Category**                | **Prerequisite**                                                                               |
|-----------------------------|------------------------------------------------------------------------------------------------|
| Related configuration tasks | You are using posting definitions (not required if you do not activate commitment accounting). |

-   Budget control configuration must be activated, budget control turned on, and an original budget confirmed.

## Set up budget parameters for regulatory accounting

To set up budget parameters for regulatory accounting, follow these steps.

1.  Go to Budgeting \> Setup \> Basic budgeting \> Budgeting parameters**.**

2.  Under Budget \> Regulatory select General budget reservations.

3.  Optionally, under Encumbrance control select Prevent carry-forward
    encumbrance increases and Use session date for GBR accounting

4.  Optionally, under General budget reservation prior year corrections select
    Allow prior year corrections

## Select source documents for budget control

You can specify which method of purchasing to use with general budget
reservations, in reserving funds for planned purchases.

To select source documents, follow these steps:

1.  Go to Budgeting \> Setup \> Budget control \> Budget control configuration.

2.  Click Create draft

3.  Click the Documents and journals tab.

4.  Select the General budget reservation check box, and also select the Check
    at line entry check box.

5.  Click the Activate budget control** **tab, then click Activate.

When you create a general budget reservation, budget source-tracking entries and
accompanying budget-checking results are also created, and budget checking
occurs when you create a line or post a reservation.

## Set up general ledger information for general budget reservations

To make sure that general ledger accounts are fairly stated, you must configure
how general budget reservations are used to record accounting commitments.

To set up general ledger information for general budget reservations, follow
these steps:

1.  Go to General ledger \> Ledger setup \> General ledger parameters.

2.  On the Ledger tab, expand the Accounting rules section.

3.  Click the Use posting definitions check box, and then click Yes in the
    confirmation dialog box.

4.  Click the General budget reservations check box, and in the Infolog message,
    click Close.

    -   The Enable encumbrance process and Enable pre-encumbrance process are
        marked and disabled by default upon this selection. These are required
        along with the General budget reservation.

## Create posting definitions

You can configure transaction posting definitions to update different general
ledger accounts for different types of general budget reservation.

To create posting definitions for general budget reservations, follow these
steps:

1.  Go to General ledger \> Posting setup \> Posting definitions.

2.  In the Posting definitions page, click New.

3.  In the Posting definition field, type a brief code for the definition (for
    example, GBREnc).

4.  Add a description (for example, GBR encumbrance).

5.  In the Module list, select Budget reservation.

6.  Fill out the rest of the page as needed.

7.  Click Posting definition in the Action bar then click View Transaction
    posting definitions.

8.  In the Transaction posting definitions page, click the Budget
    reservation tab.

9.  In the Select group, General budget reservation is selected by default. If
    appropriate, click General budget reservation year-end close.

10. Click New.

11. In the Reservation type field, do one of the following:

    -   To enter a new transaction posting definition that applies to all
        reservation types, select All. In the Posting definition field, select
        the definition that you created earlier in this topic.

    -   To enter a new transaction posting definition that applies to a single
        reservation type, select Table. In the Reservation type relation field,
        select the reservation type that you want. In the Posting
        definition field, select the definition that you created earlier in this
        topic.

12. Create as many definitions as you need, and then click Close.

## Set up the reservation number sequence

To set up the number sequence that general budget reservations will use, follow
these steps:

1.  Go to Budgeting \> Setup \> Basic budgeting \> Budgeting parameters.

2.  Click Number sequences.

3.  In the Reference column, click the entry for general budget reservations.

4.  In the Number sequence code column, select the code you intend to use.

    -   You can also assign unique number sequences by reservation type

## Create a general budget reservation type

The reservation type determines the nature of a general budget reservation, such
as the type of document that relieves the budget reservation, the workflow used
to approve the reservation, and the number sequence used.

To create a general budget reservation type, follow these steps:

1.  Go to Budgeting \> Setup \> General budget reservations \> Reservation type.

2.  Click New.

3.  In the Reservation type field, enter a name for the reservation type.

4.  In the Description field, enter a description.

5.  In the Relieving document field, Purchase requisition is selected by
    default. Change the setting if you need to. This setting specifies what type
    of document will relieve the General budget reservation.

    -   After you create a general budget reservation using the reservation
        type, you can’t change the reservation to another type.

6.  Select the Reduce carry-forward budget field to have any remaining
    carry-forward budget associated with a general budget reservation reduced to
    zero when the reservation is finalized.

7.  Optional: If an approval or other task is required prior to posting the
    reservation, in the Workflow field, select a General budget
    reservation workflow. (If a workflow is not selected, general budget
    reservations of this type can be posted without workflow.)

8.  Optional: If various reservation types use unique number sequences,
    the Number sequence field is used to select the number sequence code that
    you want the selected type to use. If a reservation type does not have a
    document number configured, use the budget parameters document number.

9.  Create more types if needed, by clicking New.

## Next step

After you have set up these rules, you can create general budget reservations.
The general budget reservations will apply to the documents that are required
for the purchasing method that you select (purchase requisition, purchase order,
or vendor invoice).

Technical information for system administrators
-----------------------------------------------

If you don't have access to the pages that are used to complete this task,
contact your system administrator and provide the information that is shown in
the following table.

| **Category**                  | **Prerequisite**                                                                    |
|-------------------------------|-------------------------------------------------------------------------------------|
| **License configuration key** | **Public Sector \> General budget reservation**                                     |
| **Security roles**            | To perform this task, you must be a member of the **Budget manager** security role. |
