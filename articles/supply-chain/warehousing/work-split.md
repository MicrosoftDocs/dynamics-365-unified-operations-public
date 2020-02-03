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
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: Release 10.0.8
---

# Split work orders

Work-split functionality lets you split large work orders into several smaller work orders, which you can then assign to multiple warehouse workers. This enables the same work to be picked by several warehouse workers simultaneously. You can only split work orders that have a status of open or in-progress. <!-- KAMAYBAC: is the term "work order" OK to use here? We normally just say "work", but that often generates sentences that seem ungrammatical  -->

## Enable the work-split functionality

Before you can use this feature, you must enable it on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. You must also enable a prerequisite feature.

First enable the prerequisite work-blocking feature (if it isn't already). It's listed as:

- **Module** - Warehouse management
- **Feature name** - Work blocking

Then enable the work-split feature, which is listed as:

- **Module** - Warehouse management
- **Feature name** - Work split

## All work and work details

Added a new button to the work details (_Warehouse management_ - _Work_ - _Work details)_ and all work (_Warehouse management_ - _ Work_ - _All work)_ forms in the WORK – WORK section of the ribbon called **Split work**.

### Validation

The button will not be enabled if:

- There is a container id associated on the work header
  - Systematically splitting a container is not possible as it requires physical actions.
- The work is associated with a cluster
- The work order type is not:
  - Sales orders
  - Raw material picking
  - Transfer issue
- The work status is not **Open** or **In Process**
- The work is currently being split by another user (an error will be thrown when trying to enter the splitting screen for a work which is already being Split by another user)

A new Blocking Reason will be used to indicate if the work header is currently in the process of being split and will be referenced by both the work split form and the mobile device.

## Work split form

### Design

Following has been added to a form.

#### Ribbon

Two buttons:

- Split work – Triggers the new work split process
- The standard Options tab to personalize, use the advanced filter/sort, etc.

#### Grid

Show one grid that contains work lines

Fields:

- Line number
- Work status
- Item number
- Item name
- Location
- Location profile
- Zone Id
- Work quantity
- Unit
- Inventory dimensions fields (similar to the existing WHSWorkTable form)

### Initialization

When the form opens, by default show all initial pick work lines that are in an open status. The **Split Work** Blocking Reason will be inserted for the current work and the work will be blocked.

The name of the **Blocked Wave** field from work header was modified to **Blocked** when using the blocking reasons.

#### Mobile device user blocking

On the mobile device, if the work is being split, when the user tries to execute work, an error will be displayed "The work with ID %1 is currently being split.".

The user can click Cancel button which will allow the user to exit the mobile device flow and process other work.

### Other operations blocking

Any operations that are modifying the work lines, work inventory transactions, or replenishment links related to a work that is being split will fail with an error : "The work with ID %1 is currently being split.".

### Grid options

Add an option above the grid to let the user show all work lines if desired. The default behavior should be that only the open (available to be split) work lines are visible. If the user changes the option, all work lines should be shown. Label the checkbox "Show all lines".

### Splitting

After the form has opened and the user has applied any filtering they want (either from the grid filters, location format filters, or query), they will select some or all the records shown in the grid (using the normal record selection functionality).

When the user clicks **Split work** in the action bar the system will create a new work header that contains all of the initial pick lines that are selected in the grid. The initial pick lines that are selected in the grid are cancelled on the original work header, and the new work header will contain all the selected work lines .

The system needs to validate that the **Split Work** Blocking Reason is still present when trying to perform the actual split operation. If it's not, then show the user the error "Work splitting session no longer valid. Please close form and try again." There will not be performed any splitting actions.

The existing work template structure, and location of the put (as well as future pick/put pairs) will be maintained. The following work header fields will be copied from the original work to the new work:

- Load ID
- Shipment ID
- Order number
- Site
- Warehouse
- Work priority
- Work pool ID
- Wave ID
- Work creation number

The following fields will not be copied to the new work header:

- Work ID (new work ID generated from number sequence)
- Work status (Open)
- Locked by (Blank initially)
- Target license plate ID (Blank)
- Created date and time (Current date/time)
- Blocked wave/Frozen (it will be recomputed for the original and new work header)

The new work will also not be assigned to any user immediately. If desired, a user can be assigned using the existing functionality from the work details form.

### Finishing splitting of a work.

In order to finish the splitting of a work, the **Split work** blocking reasons has to be removed.

There are two possibilities to remove the **Split Work** blocking reason.

The first one is that the user which is splitting the work to close the **Split Work** form(button in the top right corner). When closing the form, the **Split Work** blocking reasons will be removed, the **Blocked** state of this work will be recomputed(if there no blocking reasons left for this work, the work will be unblocked ).

The second possibility is to press the **Cancel work split session** button. When having a work header selected and pressing this button, the **Split work** blocking reason will be removed and the **Blocked** state of this work will be recomputed, similar as when closing the **split work** form. This button can be clicked by a different user than the user which is splitting the work.

After the **Split Work** blocking reason is removed(and if the **Blocked** state is set to No), the work can be executed on the mobile device.



### Logging

When the new work header is created from the work that has been split, write a line in the work creation history log that the new work header was created by splitting the original work, and mention the original work Id : Work %1 has been created by splitting off from original work %2.



<!-- KAMAYBAC: I assume we no longer need this section, right?

    ### Enable the feature
    
    In order to enable the Split work feature, this step must be followed.
    
    1. Enabled the **WHSWorkBlockingToggle** flight.
    2. Go to **Warehouse management parameters - General - Work**. Click **Upgrade blocking capabilities** button. This button is visible only if the **WHSWorkBlockingToggle** is enabled. When clicking this button, all the the works which are not Closed or Cancelled and with the **Blocked wave** field set to True will be processed and blocking reasons will be added according to why the work is blocked. The blocking reasons are a way to know why the work is blocked.
    The existing blocking reasons are **HeldWave**(work is blocked by a wave with status Held), **Unprocessed Replenishment work**(work is linked to unprocessed replenishment work), **Undefined reason**(either work was manually blocked or the work template is configured to block work) and **Unprocessed overpick work**(work is linked to unprocessed staging overpick work). It is possible to have a work blocked by multiple blocking reasons. The upgrade of the blocking reasons must be performed when there is no activity in the warehouse.
    3. Enabled the **WHSSplitWorkToggle** flight. When this flight is activated, the **Split work** blocking reason will be used.
    
    With the two flights enabled and the upgrade of the blocking reasons performed, the **Split Work** button will be visible, so the feature is activated.

 -->