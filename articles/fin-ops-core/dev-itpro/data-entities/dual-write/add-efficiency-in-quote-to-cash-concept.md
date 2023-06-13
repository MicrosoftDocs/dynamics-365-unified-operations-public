---
title: Add efficiency in quote-to-cash with Dynamics 365 Sales
description: This article provides a conceptual overview of how the improved quote-to-cash system works and how it can be used to improve your business processes.
author: henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 05/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Add efficiency in quote-to-cash with Dynamics 365 Sales

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]

<!-- KFM: Preview until 10.0.34 GA -->

Dynamics 365 Supply Chain Management uses dual-write to integrate with Dynamics 365 Sales. In Supply Chain Management version 10.0.34 and higher, this capability has been improved to provide a more seamless quotation process flow across the two systems, allowing for fewer touch points, higher efficiency, and improved transparency. These changes are intended for use within the context of quote-to-cash integration between Dynamics 365 Sales and Supply Chain Management only.

## Sales quotation origin and ownership

Both Supply Chain Management and Dynamics 365 Sales store and show origin and ownership information for each quotation.

- The **Origin** tells which system originally created a quotation. Possible values are *Supply Chain Management* and *Dynamics 365 Sales*. This value is set when the quotation is created and is read-only thereafter.
- The **Ownership** tells which system currently owns a quotation. Ownership determines the system that owns the processing of a quotation through its lifecycle and the system that is allowed to perform updates to the quotation throughout its lifecycle. The owner can be *Based on origin*, *Dynamics 365 Sales*, or *Supply Chain Management*. When ownership is *Based on origin*, the value of the **Origin** field determines ownership. When ownership is *Dynamics 365 Sales*, processing of the quotation throughout its lifecycle is done from Dynamics 365 Sales. When ownership is *Supply Chain Management*, processing of the quotation throughout its lifecycle is done from Supply Chain Management.

When the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is disabled, all sales quotations have an **Origin** of *Supply Chain Management* and an **Ownership** of *Based on origin*.

When the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is [enabled and fully configured](enable-efficiency-in-quote-to-cash.md), the **Origin** works as follows:

- Quotations created in Supply Chain Management show an **Origin** of *Supply Chain Management*.
- Quotations created in Dynamics 365 Sales show an **Origin** of *Dynamics 365 Sales*.

### Origin and ownership displays in Supply Chain Management

In Supply Chain Management, follow these steps to view the origin and ownership of a sales quotation:

1. Go to **Sales and marketing \> Sales quotations \> All quotations**.
1. Do one of the following steps:
    - Find the quotation in the grid and check the values shown in the **Origin** and **Ownership** columns.
    - Open the quotation you want to view its details. Expand the **Sales quotation header** FastTab and check the values shown in the **Origin** and **Ownership** fields.

    :::image type="content" source="media/qtc-origin-ownership.svg" alt-text="Origin and ownership of a quotation" lightbox="media/qtc-origin-ownership.svg":::

### Origin and ownership displays in Dynamics 365 Sales

In Dynamics 365 Sales, **Origin** and **Ownership** are shown in the **Integration** section in the **Quote** page.

In Dynamics 365 Sales, quotations that are owned by Supply Chain Management also show the following info message in the message area on the **Quote** page:

> This quote is not owned by Dynamics 365 Sales

A quotation that is both active and owned by Supply Chain Management provide the following combined message in the message area on the **Quote** page:

> Read-only This record's status: Active<br/>This quote is not owned by Dynamics 365 Sales

These messages let the user know that they have limited control over the selected sales quotation, so some actions won't be possible.

Quotations that are owned by Dynamics 365 Sales don't show an ownership message in the message area.

### Scenario: Sales quotation is created and then activated in Dynamics 365 Sales

The following steps show what happens when you create a sales quotation in Dynamics 365 Sales and activate it:

1. A user creates a sales quotation header in Dynamics 365 Sales.
1. Dynamics 365 Sales sets **Origin** to *Dynamics 365 Sales* and **Ownership** to *Based on origin* and **Status** to *Draft*.
1. The system syncs the new sales quotation header through dual-write using the *Dynamics 365 Sales quotation header (quotes)* entity.

    > [!NOTE]
    > The *Dynamics 365 Sales quotation header (quotes)* entity sets **Origin** to *Dynamics 365 Sales*. The value isn't synched from Dataverse but is set directly based on the entity used. Because the *Dynamics 365 Sales quotation header (quotes)* entity should only be used within a Dynamics 365 Sales integration context, all inserts from this entity are assumed to originate from Dynamics 365 Sales.

1. When the sales quotation arrives in Supply Chain Management, it's assigned a **Status** of *Created*.

    > [!NOTE]
    > The **Status** field used by Dynamics 365 Sales is different from the **Status** field used by Supply Chain Management. The **Status** field used by Dynamics 365 Sales is only used by Sales. The **Status** field used by Supply Chain Management is only used in Supply Chain Management. They are actually two different fields and can have two different values. The **Status** field value from Supply Chain Management is shown as the **Sales Quotation Status** value in Sales (on the **Integration** tab of the quotation).

1. While a sales quotation has a **Status** of *Draft* in Sales and *Created* in Supply Chain Management, users of both systems can add, delete, and modify lines for it (with all changes syncing between systems). However, because ownership is with Dynamics 365 Sales, users working in Supply Chain Management can't delete the quotation header or process it through its lifecycle.
1. When the quotation is ready to be sent to the customer, a Dynamics 365 user activates the quotation. Activation makes the quote read-only in Sales and triggers a quotation-send event in Supply Chain Management.

    - When the *Process Dynamics 365 Sales integration related events* feature isn't enabled, then the quotation-send event is processed immediately and in full in Supply Chain Management. First, the quotation journal is created in Supply Chain Management and the **Status** of the sales quotation in Supply Chain Management is updated to *Sent*. Then, the sales quotation in Dynamics 365 Sales is updated to have a **Status** of *Active*.
    - When the *Process Dynamics 365 Sales integration related events* feature is enabled and running, then part of the quotation-send event to update the status is processed immediately while the creation of the quotation journal is processed in batch. First, the quotation **Status** in Supply Chain Management is updated to *Sent*. Then, the sales quotation in Dynamics 365 Sales is updated to have a **Status** of *Active* and a request to create the quotation journal in Supply Chain Management is sent to a message queue. When the request is picked up by the message queue processor, it creates the sales quotation journal. For more information, see [Process events related to Dynamics 365 Sales integration](add-efficiency-in-quote-to-cash-use.md#process-events).

1. When the sales quotation in Supply Chain Management has a **Status** of *Sent* and ownership is with Dynamics 365 Sales, sales quotation data becomes read-only in Supply Chain Management.
1. Dynamics 365 Sales now processes the sales quotation through its lifecycle with relevant events triggering appropriate updates to the linked Supply Chain Management quotation.

### Scenario: Sales quotation is created and sent in Supply Chain Management

The following steps show what happens when you create and send a sales quotation in Supply Chain Management:

1. A user creates a sales quotation header in Supply Chain Management.
1. Supply Chain Management sets **Origin** to *Supply Chain Management* and **Ownership** to *Based on origin*.
1. When inserted into Dataverse from the *Dynamics 365 Sales quotation header (quotes)* entity, the **Origin** value is also synched and therefore set to *Supply Chain Management*. The synchronization of the **Origin** value is one directional&mdash;from Supply Chain Management to Dataverse only. Once in Dataverse, the sales quotation can be accessed in Dynamics 365 Sales with a **Status reason** of *In progress* and a **Status** of *Draft*.
1. While a sales quotation has a **Status** of *Draft* in Sales and *Created* in Supply Chain Management, users of both systems can add, delete, and modify lines for it. However, because ownership is with Supply Chain Management, users working in Dynamics 365 Sales can't delete the quotation or process it through its lifecycle. Therefore, users who open the sales quotation from the Dynamics 365 Sales **Quote** page, will see the following message:

    > This quote is not owned by Dynamics 365 Sales

1. When the quotation is ready to be sent to the customer, a user in Supply Chain Management invokes the *generate send quotation* functionality, which creates a sales quotation journal and updates the quotation **Status** to *Sent*. The new status is then synched to Dynamics 365 Sales and triggers an update of the quotation **Status** to *Active* in Sales.

    > [!NOTE]
    > The *Process Dynamics 365 Sales integration related events* feature doesn't affect this scenario because the sales quotation was processed from Supply Chain Management.

1. When a sales quotation in Dynamics 365 Sales has a **State** of *Active*, default Dynamics 365 Sales logic ensures that the quotation data is shown as read-only in the Dynamics 365 Sales user interface. For quotations where **Origin** is *Supply Chain Management* and **Ownership** is *Based on origin*, users working in Dynamics 365 Sales won't be able select the **Create order**, **Close**, **Revise**, or **Delete** actions. Users who open these sales quotation from the Dynamics 365 Sales **Quote** page, will see the following message:

    > Read-only This record's status: Active<br/>This quote is not owned by Dynamics 365 Sales

1. Supply Chain Management now processes the sales quotation through its lifecycle with relevant events triggering appropriate updates to the linked Dynamics 365 Sales quotation.

## Example of an integrated sales quotation workflow

This section provides an example of an integrated sales quotation workflow for the following scenario:

- The *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is enabled.
- The sales quotation is created in and owned by Dynamics 365 Sales (**Origin** is *Dynamics 365 Sales* and **Ownership** is *Based on origin*).

The example presented here is similar to the first scenario described in the previous section, but with more details about the status values and restrictions that apply to the sales quotation in each system.

### Step 1: Create the sales quotation

The process begins when a user creates a sales quotation in Dynamics 365 Sales. In Sales, the **Status reason** is *In progress* and the **Status** is *Draft*. The new quotation is then synchronized to Supply Chain Management, where the **Status** is shown as *Created*. Because ownership is with Dynamics 365 Sales, the quotation can't be sent, lost, canceled, confirmed, or deleted from Supply Chain Management. However, users are able to edit the sales quotation in Supply Chain Management.

The following table summarizes the initial status values of the sales quotation in each system and the restrictions that apply.

| &nbsp; | Sales (owner) | Supply Chain Management |
|---|---|---|
| **Status** value | *Draft* | *Created* |
| **Status reason** value | *In Progress* | N/A |
| Lifecycle restrictions | None | Can't be sent, lost, canceled, confirmed, or deleted |
| Data restrictions | None | None |

> [!NOTE]
> In this table (and others in this section), a value of "None" indicates that the referenced restrictions are the same as when the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is disabled.

### Step 2: Activate the sales quotation

When the quotation is ready to be sent to the customer, the user in Sales activates the quotation. In Sales, the **Status reason** is changed to *In progress* and the **Status** is changed to *Active*, which makes the quotation read-only in the Sales user interface.

The quotation update is synchronized to Supply Chain Management, where the **Status** is changed to *Sent*. Because ownership is with Dynamics 365 Sales, the quotation can't be sent, lost, canceled, confirmed, or deleted from Supply Chain Management. Data on the sales quotation is now read-only in Supply Chain Management as a result of its **Status** value and ownership.

The following table summarizes the status values of the sales quotation in each system and the restrictions that apply.

| &nbsp; | Sales (ownership) | Supply Chain Management |
|---|---|---|
| **Status** value | *Active* | *Sent* |
| **Status reason** value | *In Progress* | N/A |
| Lifecycle restrictions | None | Can't be sent, lost, canceled, confirmed, or deleted |
| Data restrictions |  None | Read-only |

### Step 3: Revise the sales quotation

If a change is needed after a quotation has been activated, then it must be revised from the owning system, which in this case is Dynamics 365 Sales. When this happens, Sales creates a copy of the quotation and then updates the now-outdated quotation to have a **Status** of *Closed* and a **Status reason** of *Revised*. The **Status** of the new copy is set to *Draft*, with a **Status reason** of *In progress*.

The now-outdated quotation is synchronized to Supply Chain Management, where the **Status** is shown as *Revised*.

The new quotation is synchronized to Supply Chain Management, where the **Status** is shown as *Created*. Because ownership is with Dynamics 365 Sales, the quotation can't be sent, lost, canceled, confirmed, or deleted from Supply Chain Management.

The following table summarizes the status values of the revised sales quotation in each system and the restrictions that apply.

| &nbsp; | Revised quotation in Sales (owner) | New quotation in Sales (owner) | Revised quotation in Supply Chain Management | New quotation in Supply Chain Management |
|---|---|---|---|---|
| **Status** value | *Closed* | *Draft* | *Revised* | *Created* |
| **Status reason** value | *Revised* | *In progress* | N/A | N/A |
| Lifecycle restrictions | None | None | Can't be sent, lost, canceled, confirmed, or deleted | Can't be sent, lost, canceled, confirmed, or deleted |
| Data restrictions | None | None | Read-only | None |

### Step 4: Close the sales quotation

When a user closes an activated sales quotation in Dynamics 365 Sales, they're asked to specify a reason by choosing one of the following reason codes:

- **The quotation is revised**
- **The quotation is lost**
- **The quotation is canceled**

> [!NOTE]
> No reason code is synchronized between systems for the lost and canceled events in Supply Chain Management.

The following table summarizes the status values and restrictions that apply when closing a sales quotation in *Dynamics 365 Sales* for each of the common reasons.

| Result | Status | Status reason | Lifecycle restrictions | Data restrictions |
|---|---|---|---|---|
| Quotation Closed | *Closed* | *Revised* | None | None |
| Quotation Closed | *Closed* | *Lost* | None | None |
| Quotation Closed | *Closed* | *Canceled* | None | None |

The following table summarizes the status values and restrictions that apply in *Supply Chain Management* when a sales quotation is closed in Dynamics 365 Sales for each of the common reasons and then synced to Supply Chain Management.

| Result | Status | Lifecycle restrictions | Data restrictions |
|---|---|---|---|
| Quotation Revised | *Revised* | Can't be sent, lost, canceled, confirmed, or deleted | None |
| Quotation Lost | *Lost* | Can't be sent, lost, canceled, confirmed, or deleted | None |
| Quotation Canceled | *Canceled* | Can't be sent, lost, canceled, confirmed, or deleted | None |

### Step 4 variation: Create a sales order from the quotation

When a user creates as sales order from an activated sales quotation in Dynamics 365 Sales, the following events are triggered in Supply Chain Management:

1. Update the sales quotation **Status** to *Confirmed* and generate quotation confirmation journal.
1. The sales order that was created in Dynamics 365 Sales is synchronized and available in Supply Chain Management.
1. Supply Chain Management links the new sales order to the related sales quotation, which enables users to navigate between them.

The following table summarizes the status values and restrictions that apply is *Dynamics 365 Sales* when a sales order is created from a sales quotation in Dynamics 365 Sales.

| Result | Status | Status reason | Lifecycle restrictions | Data restrictions |
|---|---|---|---|---|
| Quotation won | *Won* | *Won* | None | None |
| Sales order created | *Active* | *New* | None | None |

The following table summarizes the status values and restrictions that apply in *Supply Chain Management* when a sales order is created from a sales quotation in Dynamics 365 Sales and then synced to Supply Chain Management.

| Result | Status | Lifecycle restrictions | Data restrictions |
|---|---|---|---|
| Quotation confirmation journal created | *Won* | Can't be sent, lost, canceled, confirmed, or deleted | Read Only |
| Sales order created | *Open* | None | None |

## Next steps

- [Enable extra efficiency in quote-to-cash with Dynamics 365 Sales](enable-efficiency-in-quote-to-cash.md)
- [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-use.md)