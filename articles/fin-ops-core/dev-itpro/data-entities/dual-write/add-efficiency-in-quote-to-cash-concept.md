---
title: Add efficiency in quote-to-cash with Dynamics 365 Sales
description: This article provides a conceptual overview of how the improved quote-to-cash system works and how it can help improve your business processes.
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

Microsoft Dynamics 365 Supply Chain Management uses dual-write to integrate with Dynamics 365 Sales. In Supply Chain Management version 10.0.34 and later, this capability has been improved to provide a more seamless quotation process flow across the two systems. Therefore, it allows for fewer touch points, better efficiency, and improved transparency. These changes are intended to be used only in the context of quote-to-cash integration between Sales and Supply Chain Management.

## Sales quotation origin and ownership

Both Supply Chain Management and Sales store and show origin and ownership information for each quotation.

- *Origin* indicates which system originally created a quotation. The possible values of the **Origin** field are *Supply Chain Management* and *Dynamics 365 Sales*. The value is set when the quotation is created, and is read-only afterward.
- *Ownership* indicates which system currently owns a quotation. It determines which system owns the processing of a quotation through its lifecycle, and which system is allowed to update the quotation through its lifecycle. The possible values of the **Ownership** field are *Based on origin*, *Dynamics 365 Sales*, and *Supply Chain Management*.

    - *Based on origin* – The **Origin** value determines ownership.
    - *Dynamics 365 Sales* – The quotation is processed through its lifecycle from Sales.
    - *Supply Chain Management* – The quotation is processed through its lifecycle from Supply Chain Management.

When the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is disabled, all sales quotations have an **Origin** value of *Supply Chain Management* and an **Ownership** value of *Based on origin*.

When the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is [enabled and fully configured](add-efficiency-in-quote-to-cash-enable.md), the **Origin** field works in the following way:

- Quotations that are created in Supply Chain Management have an **Origin** value of *Supply Chain Management*.
- Quotations that are created in Sales have an **Origin** value of *Dynamics 365 Sales*.

### View origin and ownership information in Supply Chain Management

In Supply Chain Management, follow these steps to view origin and ownership information for a sales quotation.

1. Go to **Sales and marketing \> Sales quotations \> All quotations**.
1. Follow one of these steps:

    - Find the quotation in the grid, and review the values in the **Origin** and **Ownership** columns.
    - Open the quotation to view its details. On the **Sales quotation header** FastTab, in the **Quotation creation** section, review the values in the **Origin** and **Ownership** fields.

    :::image type="content" source="media/qtc-origin-ownership.svg" alt-text="Origin and Ownership fields on a quotation details page." lightbox="media/qtc-origin-ownership.svg":::

### View origin and ownership information in Sales

In Sales, origin and ownership information is shown in the **Integration** section of the **Quote** page.

In addition, the message area of the **Quote** page shows informational messages that indicate ownership by Supply Chain Management. Therefore, users will know that they have limited control over the selected sales quotation and can't perform some actions. No message is shown for quotations that are owned by Sales.

For quotations that are owned by Supply Chain Management, the following informational message is shown:

> This quote is not owned by Dynamics 365 Sales

For quotations that are both owned by Supply Chain Management and active, the following combined message is shown:

> Read-only This record's status: Active<br>This quote is not owned by Dynamics 365 Sales

### Scenario 1: A sales quotation is created and then activated in Sales

The following steps show what happens when you create a sales quotation in Sales and activate it.

1. A user creates a sales quotation header in Sales.
1. Sales sets the **Origin** field to *Dynamics 365 Sales*, the **Ownership** field to *Based on origin*, and the **Status** field to *Draft*.
1. The system syncs the new sales quotation header through dual-write by using the *Dynamics 365 Sales quotation header* (*quotes*) entity.

    > [!NOTE]
    > The *Dynamics 365 Sales quotation header* (*quotes*) entity sets the **Origin** field to *Dynamics 365 Sales*. The value isn't synced from Dataverse but is set directly, based on the entity that's used. Because the *Dynamics 365 Sales quotation header* (*quotes*) entity should be used only in a Sales integration context, all inserts from this entity are assumed to originate from Sales.

1. When the sales quotation arrives in Supply Chain Management, it's assigned a **Status** value of *Created*.

    > [!NOTE]
    > The **Status** field in Sales is used only by Sales, and the **Status** field in Supply Chain Management is used only by Supply Chain Management. The two **Status** fields are distinct and can have different values. The **Status** value from Supply Chain Management is shown as the **Sales Quotation Status** value in Sales (on the **Integration** tab of the quotation).

1. While a sales quotation has a **Status** value of *Draft* in Sales and *Created* in Supply Chain Management, users of both systems can add, delete, and modify lines for it, and all changes are synced between systems. However, because ownership lies with Sales, users who work in Supply Chain Management can't delete the quotation header or process it through its lifecycle.
1. When the quotation is ready to be sent to the customer, a Dynamics 365 user activates it. Activation makes the quotation read-only in Sales and triggers a quotation-send event in Supply Chain Management.

    - If the *Process Dynamics 365 Sales integration related events* feature is disabled, the quotation-send event is immediately and fully processed in Supply Chain Management. First, the quotation journal is created in Supply Chain Management, and the **Status** value of the sales quotation in Supply Chain Management is updated to *Sent*. Then the **Status** value of the sales quotation in Sales is updated to *Active*.
    - If the *Process Dynamics 365 Sales integration related events* feature is enabled and running, part of the quotation-send event to update the status is immediately processed while the quotation journal is created in batch mode. First, the **Status** value of the quotation in Supply Chain Management is updated to *Sent*. Then the **Status** value of the sales quotation in Sales is updated to *Active*, and a request to create the quotation journal in Supply Chain Management is sent to a message queue. When that request is picked up by the message queue processor, it creates the sales quotation journal. For more information, see [Process events related to Sales integration](add-efficiency-in-quote-to-cash-use.md#process-events).

1. When the sales quotation in Supply Chain Management has a **Status** value of *Sent*, and ownership lies with Sales, sales quotation data becomes read-only in Supply Chain Management.
1. Sales processes the sales quotation through its lifecycle, and relevant events trigger appropriate updates to the linked Supply Chain Management quotation.

### Scenario 2: A sales quotation is created and sent in Supply Chain Management

The following steps show what happens when you create and send a sales quotation in Supply Chain Management.

1. A user creates a sales quotation header in Supply Chain Management.
1. Supply Chain Management sets the **Origin** field to *Supply Chain Management* and the **Ownership** field to *Based on origin*.
1. When the new sales quotation header is inserted into Dataverse from the *Dynamics 365 Sales quotation header* (*quotes*) entity, the **Origin** value is synced. As a result, it's set to *Supply Chain Management*. The synchronization of the **Origin** value is one-directional: from Supply Chain Management to Dataverse only. After it's in Dataverse, the sales quotation can be accessed in Sales, where it has a **Status reason** value of *In progress* and a **Status** value of *Draft*.
1. While a sales quotation has a **Status** value of *Draft* in Sales and *Created* in Supply Chain Management, users of both systems can add, delete, and modify lines for it. However, because ownership lies with Supply Chain Management, users who work in Sales can't delete the quotation or process it through its lifecycle. Therefore, users who open the sales quotation from the **Quote** page in Sales receive the following message:

    > This quote is not owned by Dynamics 365 Sales

1. When the quotation is ready to be sent to the customer, a user in Supply Chain Management invokes the *generate send quotation* functionality. This functionality creates the sales quotation journal and updates the **Status** value of the quotation to *Sent*. The new **Status** value is then synced to Sales. As a result, the **Status** value of the quotation is updated to *Active* in Sales.

    > [!NOTE]
    > The *Process Dynamics 365 Sales integration related events* feature doesn't affect this scenario, because the sales quotation was processed from Supply Chain Management.

1. When a sales quotation in Sales has a **State** value of *Active*, default Sales logic ensures that the quotation data is shown as read-only in the Sales user interface (UI). For quotations where the **Origin** value is *Supply Chain Management* and the **Ownership** value is *Based on origin*, users who work in Sales can't select the **Create order**, **Close**, **Revise**, or **Delete** buttons. Users who open these sales quotations from the **Quote** page in Sales receive the following message:

    > Read-only This record's status: Active<br>This quote is not owned by Dynamics 365 Sales

1. Supply Chain Management processes the sales quotation through its lifecycle, and relevant events trigger appropriate updates to the linked Sales quotation.

## Example of an integrated sales quotation workflow

This section provides an example of an integrated sales quotation workflow for the following scenario:

- The *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is enabled.
- The sales quotation is created in and owned by Sales. (In other words, the **Origin** value is *Dynamics 365 Sales*, and the **Ownership** value is *Based on origin*.)

This example resembles the first scenario in the previous section. However, it provides more details about the status values and restrictions that apply to the sales quotation in each system.

### Step 1: Create the sales quotation

The process begins when a user creates a sales quotation in Sales. In Sales, the **Status reason** value is *In progress*, and the **Status** value is *Draft*. The new quotation is then synced to Supply Chain Management, where the **Status** value is shown as *Created*. Because ownership lies with Sales, the quotation can't be sent, lost, canceled, confirmed, or deleted from Supply Chain Management. However, users can edit the sales quotation in Supply Chain Management.

The following table summarizes the initial status values of the sales quotation in each system and the restrictions that apply.

| &nbsp; | Sales (owner) | Supply Chain Management |
|---|---|---|
| **Status** value | *Draft* | *Created* |
| **Status reason** value | *In Progress* | Not applicable |
| Lifecycle restrictions | None | The quotation can't be sent, lost, canceled, confirmed, or deleted. |
| Data restrictions | None | None |

> [!NOTE]
> In this table (and the other tables in this section), "None" indicates that the restrictions are the same as those that apply when the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is disabled.

### Step 2: Activate the sales quotation

When the quotation is ready to be sent to the customer, the user in Sales activates it. In Sales, the **Status reason** value is updated to *In progress*, and the **Status** value is updated to *Active*. As a result, the quotation becomes read-only in the Sales UI.

The quotation update is synced to Supply Chain Management, where the **Status** value is updated to *Sent*. Because ownership lies with Sales, the quotation can't be sent, lost, canceled, confirmed, or deleted from Supply Chain Management. Because of the **Status** value and the ownership, data in the sales quotation is now read-only in Supply Chain Management.

The following table summarizes the status values of the sales quotation in each system and the restrictions that apply.

| &nbsp; | Sales (owner) | Supply Chain Management |
|---|---|---|
| **Status** value | *Active* | *Sent* |
| **Status reason** value | *In Progress* | Not applicable |
| Lifecycle restrictions | None | The quotation can't be sent, lost, canceled, confirmed, or deleted. |
| Data restrictions | None | Data is read-only. |

### Step 3: Revise the sales quotation

If changes are required after a quotation has been activated, the quotation must be revised from the system that owns it. In this case, ownership lies with Sales.

When a quotation is revised, Sales creates a copy of it. It updates the now-outdated quotation so that it has a **Status** value of *Closed* and a **Status reason** value of *Revised*. The new copy has a **Status** value of *Draft* and a **Status reason** value of *In progress*.

The now-outdated quotation is synced to Supply Chain Management, where the **Status** value is shown as *Revised*. The new quotation is also synced to Supply Chain Management, where the **Status** value is shown as *Created*. Because ownership lies with Sales, the quotation can't be sent, lost, canceled, confirmed, or deleted from Supply Chain Management.

The following table summarizes the status values of the now-outdated (revised) and new sales quotations in each system and the restrictions that apply.

| &nbsp; | Revised quotation in Sales (owner) | New quotation in Sales (owner) | Revised quotation in Supply Chain Management | New quotation in Supply Chain Management |
|---|---|---|---|---|
| **Status** value | *Closed* | *Draft* | *Revised* | *Created* |
| **Status reason** value | *Revised* | *In progress* | Not applicable | Not applicable |
| Lifecycle restrictions | None | None | The quotation can't be sent, lost, canceled, confirmed, or deleted. | The quotation can't be sent, lost, canceled, confirmed, or deleted. |
| Data restrictions | None | None | Data is read-only. | None |

### Step 4: Close the sales quotation

When a user closes an activated sales quotation in Sales, they're asked to select one of the following reason codes to specify a reason:

- **The quotation is revised**
- **The quotation is lost**
- **The quotation is canceled**

> [!NOTE]
> No reason code is synced between systems for the lost and canceled events in Supply Chain Management.

The following table summarizes the status values and restrictions that apply in *Sales* when a sales quotation is closed in Sales for each of the common reasons.

| Result | Status | Status reason | Lifecycle restrictions | Data restrictions |
|---|---|---|---|---|
| Quotation Closed | *Closed* | *Revised* | None | None |
| Quotation Closed | *Closed* | *Lost* | None | None |
| Quotation Closed | *Closed* | *Canceled* | None | None |

The following table summarizes the status values and restrictions that apply in *Supply Chain Management* when a sales quotation is closed in Sales for each of the common reasons and then synced to Supply Chain Management.

| Result | Status | Lifecycle restrictions | Data restrictions |
|---|---|---|---|
| Quotation Revised | *Revised* | The quotation can't be sent, lost, canceled, confirmed, or deleted. | None |
| Quotation Lost | *Lost* | The quotation can't be sent, lost, canceled, confirmed, or deleted. | None |
| Quotation Canceled | *Canceled* | The quotation can't be sent, lost, canceled, confirmed, or deleted. | None |

### Step 4 variation: Create a sales order from the quotation

When a user creates a sales order from an activated sales quotation in Sales, the following events are triggered in Supply Chain Management.

1. The **Status** value of the sales quotation is updated to *Confirmed*, and the quotation confirmation journal is generated.
1. The sales order that was created in Sales is synced and becomes available in Supply Chain Management.
1. Supply Chain Management links the new sales order to the related sales quotation, so that users can navigate between them.

The following table summarizes the status values and restrictions that apply in *Sales* when a sales order is created from a sales quotation in Sales.

| Result | Status | Status reason | Lifecycle restrictions | Data restrictions |
|---|---|---|---|---|
| Quotation won | *Won* | *Won* | None | None |
| Sales order created | *Active* | *New* | None | None |

The following table summarizes the status values and restrictions that apply in *Supply Chain Management* when a sales order is created from a sales quotation in Sales and then synced to Supply Chain Management.

| Result | Status | Lifecycle restrictions | Data restrictions |
|---|---|---|---|
| Quotation confirmation journal created | *Won* | The quotation can't be sent, lost, canceled, confirmed, or deleted. | Data is read-only. |
| Sales order created | *Open* | None | None |

## Next steps

- [Enable extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md)
- [Work with added efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-use.md)
