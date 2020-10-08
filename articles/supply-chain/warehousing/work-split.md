---
# required metadata

title: Split work orders
description: Work split functionality lets you split large work orders into several smaller work orders to be assigned to multiple warehouse workers. This enables the same work to be picked by several warehouse workers simultaneously.
author: mirzaab
manager: AnnBe
ms.date: 02/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
ms.search.industry: WHSWorkTableListPage
ms.author: mirzaab
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: Release 10.0.8
---

# Work Split

Work split functionality lets you split large work orders (**Work ID's** with many lines) into several smaller work orders, which you can then assign to multiple warehouse workers. This enables the same **Work creation number** to be picked by several warehouse workers simultaneously.

After the **Split work** page has opened and the user has applied any filtering (either from the grid filters, or filter pane), they will select one or more records shown in the grid (using the normal record selection functionality).

When the user clicks **Split work** in the Action Pane, the system will create a new work header that contains all of the initial pick lines that are selected in the grid. The initial pick lines that are selected in the grid are canceled on the original work header, and the new work header will contain all the selected work lines.

The system needs to validate that the ‘Split Work’ Blocking Reason is still present when trying to perform the actual split operation. If it’s not, then show the user the error “**Work splitting session no longer valid. Please close form and try again.**”, splitting actions will not be performed.

> [!IMPORTANT]
> You can only split work orders that have a status of open or in-progress.

## Enable the work split functionality

Before you can use this feature, you must enable it on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. You must also enable a prerequisite feature.

First enable the prerequisite Organization-wide work blocking feature (if it isn't already). It's listed as:

- **Module** - Warehouse management
- **Feature name** - Organization-wide work blocking

> [!NOTE]
> In order for this feature to work data upgrade is performed once the feature is enabled across all legal entities.

Then enable the work-split feature, which is listed as:

- **Module** - Warehouse management
- **Feature name** - Work split
  - Provides capability to split warehouse work that is in status open or in progress. It is used to move selected lines from current work to another new work to balance workload. New work can be assigned to another employee.

## All work and work details form enhancements

When the **Work split** feature is enabled, two new buttons are added the work details (**Warehouse management \> Work \> Work details**) and all work (**Warehouse management \> Work \> All work**) forms. The buttons are added into the **Work** tab, **Work** group section of the Action Pane:

- **Split work** - Split the work ID into multiple smaller work IDs that can be processed by separate workers.
- **Cancel work split session** - Cancels work split session and makes the work it available for processing.

![Work split buttons](media/Work_split_buttons.png "Work split buttons")

> [!IMPORTANT]
> The **Work split** button provides the capability to split warehouse work that is in status open or in progress.
>
> The button will not be enabled if:
>
> - There is a **Container ID** associated on the work header.
>   - Systematically splitting a container is not possible as it requires physical actions.
> - The work is associated with a **Cluster**.
> - The **Work order type** is not:
>   - Sales orders
>   - Raw material picking
>   - Transfer issue
> - The work status is not **Open** or **In Process**.
> - The work is currently being split by another user.
>   - An error (*The work with ID #### is currently being split. Retry in a few minutes. If you continue to receive this message, contact a supervisor.*) will be thrown when trying to enter the splitting screen for a work which is already being split by another user.

A new **Work blocking reason** (*The work is currently being split.*) will be used to indicate if the work header is currently in the process of being split and will be referenced by both the **Split work** form and the mobile device when attempting to execute the work. The name of the **Blocked Wave** field from work header was modified to **Blocked** when using the blocking reasons.

## Split work form actions

A new form has been added to enable users to split work lines from the **Work ID**. When selected, by default the page displays the *Open* **Work status** lines that are available for splitting. In the Action Pane the **Split work** button is used to process the selected work in the grid to be split.

1. Navigate to one of the work pages:

    - **Work details** - *Warehouse management \> Work \> Work details*
    - **All work** - *Warehouse management \> Work \> All work*

1. In the grid, select a **Work ID** to split work. The **Work order type** must be one of the following:
    - Sales orders
    - Raw material picking
    - Transfer issue

1. In the Action Pane select the **Work** tab.
1. In the **Work** group select **Split work**
    1. If the *Work ID* selected does not have one of the Work order types listed above, the button will not be enabled.

1. The new **Split work** page opens and displays the work lines that are open and available to be split.
    1. An informational message is displayed, "**Users can't process lines of the work until you finish splitting and close this page.**"
    1. By default only available work lines are displayed. To see all lines for the work ID, such a **Work type** of *Put*, select the **Show all lines** check box above the grid.
    1. The **Split Work** blocking reason will be inserted for the current work and the work will be blocked.

![Blocking reason](media/Blocking_reason.png "Blocking reason")

6. Select one or more lines from the available lines to be split off the current Work ID and added to a new Work ID.
    1. When you split the work, the selected line, or lines, on the original work ID are Canceled, then copied to a new Work ID.
    1. The existing work template structure, and location of the put (as well as future pick/put pairs) will be maintained. The following work header fields will be copied from the original work to the new work:
        1. Load ID
        1. Shipment ID
        1. Work order type
        1. Order number
        1. Site
        1. Warehouse
        1. Work priority
        1. Work pool ID
        1. Wave ID
        1. Work creation number

    1. The following fields will not be copied to the new work header:
        1. Work ID (new work ID generated from number sequence)
        1. Work status (Open)
        1. Locked by (Blank initially)
        1. Target license plate ID (Blank)
        1. Created date and time (Current date/time)
        1. Blocked wave/Frozen (it will be recomputed for the original and new work header)

1. In the Action Pane, select **Split work**.
1. A processing message will be displayed **Processing operation - Split work** while the splitting of work is being processed.
    1. You have the ability to cancel this operation by selecting the **Cancel** button in the message window while it is displayed.

1. If you do not have the **Show all lines** check box selected, the line that was split off and canceled will no longer be displayed in the grid. If the check box is selected, you will see the line **Work status** change to **Canceled**.
1. A notification will be displayed in the *Message bar* indicating the new work ID that has been created. **Work #### has been created by splitting off from original work ####.**.
1. The original work ID's other work lines, such as *Put*, will be adjusted to reflect the lines of work that have been canceled.
    1. For example, if the original work ID's *Put* line was for a quantity of 15, and *Pick* lines totaling a quantity of 10 were canceled, the new *Put* quantity on the original work ID will be 5.

1. The new work will also not be assigned to any user immediately. If desired, a user can be assigned using the existing functionality from the work details form.

> [!IMPORTANT]
> Splitting work requires that the **Work ID** to be split contains two or more available lines. If there is only one available work line, when you process **Split work** you will receive an error message "**At least one work line must remain on initial work.**" and no splitting of work will be processed.

## Finish Split Work

To finish the splitting of a work, the **Split work** blocking reason must be removed.

- There are two ways to remove the ‘Split Work’ blocking reason.
  - The first way is for the user that is splitting the work to close the **Split Work** form (*X* button in the top right corner). When closing the form, the *Split Work* blocking reason will be removed. The *Blocked* state of this work will be recomputed (if there no blocking reasons left for this work, the work will be unblocked).
  - The second way is to press the **Cancel work split session** button in the Action Pane. When a work header is selected and this button is selected, the *Split work* blocking reason will be removed and the *Blocked* state of this work will be recomputed, similar as when closing the **Split work** page. This button can be clicked by a different user than the user that is splitting the work.

After the ‘Split Work’ blocking reason is removed (and if the *Blocked* state is set to No), the work can be executed on the mobile device.

## Mobile device user blocking

On the mobile device, if the work is being split, when the user tries to execute picking work against a work ID being split, an error will be displayed "**The work with ID** *%1* **is currently being split.**".

The user can click the **Cancel** button which will allow the user to exit the mobile device flow and process other work.

## Other operations blocking

Any operations that are modifying the work lines, work inventory transactions, or replenishment links related to a work that is being split will fail with an error : "**The work with ID** *%1* **is currently being split.**".

<!-- HHM: Logging is not being done
## Logging

When the new work header is created from the work that has been split, write a line in the work creation history log that the new work header was created by splitting the original work, and mention the original work Id : Work %1 has been created by splitting off from original work %2. -->
