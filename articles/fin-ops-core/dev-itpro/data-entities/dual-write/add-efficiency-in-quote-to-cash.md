---
title: Add efficiency in quote-to-cash with Dynamics 365 Sales
description: This article provides information about Quote-to-cash in dual-write enhancements.
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

This article provides a conceptual overview of how the improved quote-to-cash system works and how it can be used to improve your business processes. It also provides information about how to the integrated system will behave based on which features you choose to enable. For details about how to enable these improvements for your system, see [Enable efficiency in quote-to-cash](enable-efficiency-in-quote-to-cash.md).

## Sales quotation origin and ownership

A concept of quotation creation origin and ownership is added to the sales quotation in Supply Chain Management. This concept is agnostic to any feature enablement and is visible from the user interface of the sales quotation details page header section from version 10.0.32 <!-- KFM: Not true. One of the new features needs to be turned on. Not sure which one, but I couldn't see this info until I enabled all the new features. Maybe just remove this paragraph? -->.

Both Supply Chain Management and Dynamics 365 Sales store and show origin and ownership information for each quotation.

- The **Origin** tells which system originally created a quotation. <!-- KFM: How does this affect the record and what I can do with it? What values are possible, and what do they mean? -->
- The **Ownership** tells which system currently owns a quotation. Ownership determines the system that owns the processing of the quotation through its lifecycle and the system that is allowed to perform updates to the quotation throughout its lifecycle. The owner can be *Based on origin*, *Dynamics 365 Sales*, or *Supply Chain Management*. When ownership is *Based on origin*, the value of the *Origin* field determines ownership. When ownership is *Dynamics 365 Sales*, processing of the quotation throughout its lifecycle is done from Dynamics 365 Sales. When ownership is “Supply Chain Management*, processing of the quotation throughout its lifecycle is done from Supply Chain Management.<!-- KFM: How does this affect the record and what I can do with it? What values are possible, and what do they mean? -->

When the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is disabled, all sales quotations have an **Origin** of *Supply Chain Management* and an **Ownership** of *Based on origin*.

When the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is [enabled and fully configured](enable-efficiency-in-quote-to-cash.md), the **Origin** works as follows:

- Quotations created in Supply Chain Management show an **Origin** of *Supply Chain Management*.
- Quotations created in Dynamics 365 Sales show an **Origin** of *Dynamics 365 Sales*.

### Origin and ownership displays in Supply Chain Management

In Supply Chain Management, follow these steps to view the origin and ownership of a sales quotation:

1. Go to **Sales and marketing \> Sales quotations \> All quotations**.
1. Do one of the following steps:
    - Find the quotation in the grid and check the values shown in the **Origin** and **Ownership** columns.
    - Open the quotation you want to view to view its details. Expand the **Sales quotation header** FastTab and check the values shown in the **Origin** and **Ownership** fields.

    :::image type="content" source="media/qtc-origin-ownership.svg" alt-text="Origin and ownership of a quotation" lightbox="media/qtc-origin-ownership.svg":::

### Origin and ownership displays in Dynamics 365 Sales

In Dynamics 365 Sales, **Origin** and **Ownership** are shown in the **Integration** section in the **Quote** page.

In Dynamics 365 Sales, quotations that are owned by Supply Chain Management also show the following info message in the message area on the **Quote** page:

> This quote is not owned by Dynamics 365 Sales

A quotation that is both active and owned by Supply Chain Management provide the following combined message in the message area on the **Quote** page:

> Read-only This record's status: Active<br/>This quote is not owned by Dynamics 365 Sales

These messages let the user know that they have limited control over the selected sales quotation, so some actions won't be possible.

Quotations that are owned by Dynamics 365 Sales don't show an ownership message in the message area.

### Scenario: Sales quotation is created in Dynamics 365 Sales and then activated <!-- KFM: Activated where? -->

The following steps show what happens when you create a sales quotation in Dynamics 365 Sales and activate it: <!-- KFM: *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature must be enabled? -->

1. A user creates a sales quotation header in Dynamics 365 Sales.
1. Dynamics 365 Sales sets **Origin** to *Dynamics 365 Sales* and **Ownership** to *Based on origin*.
1. The system syncs the new sales quotation header through dual-write using the *Dynamics 365 Sales quotation header (quotes)* entity. <!-- KFM: Is this entity part of SCM? -->
1. The *Dynamics 365 Sales quotation header (quotes)* entity inserts the sales quotation order into Supply Chain Management and sets **Origin** to *Dynamics 365 Sales*. The value isn't synched from Dataverse but is set directly based on the entity used. Because the *Dynamics 365 Sales quotation header (quotes)* entity should only be used within a Dynamics 365 Sales integration context, all inserts from this entity are assumed to originate from Dynamics 365 Sales. <!-- KFM: Does the reader really care about this detail? If so, are we saying that these fields aren't actually sent from Sales but instead are just assumed by the entity and recreated in SCM? -->
1. The sales quotation status in Supply Chain Management is created. <!-- KFM: I don't understand what this means. What is a "status" in this context; what is it for and who creates it?  -->
1. While a sales quotation has a **State** of *Draft* and **Status** of *Created* users of both systems can add, delete, and modify lines for it <!-- KFM: and changes are synced continuously? -->. However, because ownership is with Dynamics 365 Sales, users working in Supply Chain Management can't delete the quotation <!-- KFM: header? --> or process it through its lifecycle.
1. When users working in Dynamics 365 Sales add products to the quotation, the related quotation lines are synchronized to Supply Chain Management<!-- KFM: Are we just repeating the previous paragraph here? -->. Then the sales quotation is activated from Dynamics 365 <!-- KFM: Which system do you mean? What does it mean to be "activated"? How/why is the quote "activated" and by whom? -->. Activation triggers a quotation-send event in Supply Chain Management.

    - When the *Process Dynamics 365 Sales integration related events* feature isn't enabled, then the quotation-send event is processed immediately and in full in Supply Chain Management. First, the quotation journal is created in Supply Chain Management and the **Status** of the sales quotation is updated to *Sent*. Then, the sales quotation in Dynamics 365 Sales is updated to have a **State** of *Active*. <!-- KFM: What is the State in SCM? What is the Status in Sales? What makes this happen? -->
    - When the *Process Dynamics 365 Sales integration related events* feature is enabled and running, then part of the quotation-send event to update the status can processed immediately while the creation of the quotation journal is processed in batch. First, the quotation **Status** is updated to *Sent*. Then the sales quotation in Dynamics 365 Sales is updated to have a **State** of *Active* and a request to create the quotation journal is sent to a message queue in Supply Chain Management. When the request is picked up by the message queue processor, it creates the sales quotation journal. For more details, see [Process Dynamics 365 Sales integration related events](#process-events).

1. When the sales quotation in Supply Chain Management has a **Status** of *Sent* and ownership is with Dynamics 365 Sales, sales quotation data becomes read-only in Supply Chain Management. Likewise, sales quotations that have a a **State** of *Active* become read-only in Dynamics 365 Sales. Because ownership is with Dynamics 365 Sales, this is respected in Supply Chain Management. Quotation data becomes read-only from the Supply Chain Management user interface <!-- KFM: Are we saying the same thing twice here? -->.
1. Dynamics 365 Sales now processes the sales quotation through its lifecycle with relevant events triggering appropriate updates to the linked Supply Chain Management quotation.

### Scenario: Sales quotation is created and sent in Supply Chain Management and then sent <!-- KFM: Sent where? How? -->

The following steps show what happens when you create a sales quotation in Supply Chain Management:<!-- KFM: *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature must be enabled? -->

1. A user creates a sales quotation header in Supply Chain Management.
1. Supply Chain Management sets **Origin** to *Supply Chain Management* and **Ownership** to *Based on origin*.
1. The system syncs the new sales quotation header through dual-write using the *Dynamics 365 Sales quotation header (quotes)* entity. <!-- KFM: Is this entity part of SCM? -->
1. When inserted into Dataverse from the *Dynamics 365 Sales quotation header (quotes)* entity, the **Origin** value is also synched and therefore set to *Supply Chain Management*. The synchronization of the **Origin** value is one directional&mdash;from Supply Chain Management to Dataverse only. Once in Dataverse, the sales quotation can be accessed in Dynamics 365 Sales with a **Status** of *In progress* and a **State** of *Draft*.
1. While a sales quotation has a **State** of *Draft* and **Status** of *Created* <!-- KFM: But the status is *In progress*? --> users of both systems can add, delete, and modify lines for it <!-- KFM: and changes are synced continuously? -->. However, because ownership is with Supply Chain Management, users working in Dynamics 365 Sales can't delete the quotation <!-- KFM: header? --> or process it through its lifecycle. Therefore, users who open the sales quotation from the Dynamics 365 Sales **Quote** page, will see the following message:

    > This quote is not owned by Dynamics 365 Sales

1. When users working in Supply Chain Management add products to the quotation, the related quotation lines are synchronized to Dynamics 365 Sales<!-- KFM: Are we just repeating the previous paragraph here? -->. Then the sales quotation is sent from Supply Chain Management using the generate send quotation functionality <!-- KFM: What does it mean to be "sent"? How/why is the quote "sent" and by whom? -->. When the **Status** is updated to *Sent*, the new status is synched to Dynamics 365 Sales and triggers an update of the quotation to Active <!-- KFM: What trigger is this? What field is set to "Active", and how does this new value affect SCM? -->.

    <!-- KFM: In the previous section, we describe different behaviors here based on whether the *Process Dynamics 365 Sales integration related events* feature is enabled. Does that not matter in this scenario? -->

1. When a sales quotation in Dynamics 365 Sales has a **State** of *Active*, default Dynamics 365 Sales logic ensures that the quotation data is shown as read-only in the Dynamics 365 Sales user interface. For quotations where **Origin** is *Supply Chain Management* and **Ownership** is *Based on origin*, users working in Dynamics 365 Sales won't be able select **Create order**, **Close**, **Revise**, or **Delete** actions. Users who open these sales quotation from the Dynamics 365 Sales **Quote** page, will see the following message:

    > Read-only This record's status: Active<br/>This quote is not owned by Dynamics 365 Sales

1. Supply Chain Management now processes the sales quotation through its lifecycle with relevant events triggering appropriate updates to the linked Dynamics 365 Sales quotation.

## Example of an integrated sales quotation workflow

This section provides an example of an integrated sales quotation workflow for the following scenario:

- The *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is enabled.
- The sales quotation is created in and owned by Dynamics 365 Sales (**Origin** is *Dynamics 365 Sales* and **Ownership** is *Based on origin*).

<!-- KFM: The tables in this section use **Status** and **Status reason**. In the previous section we have **State** and **Status**. Are we talking about three different fields here, or what?  -->

### Step 1: Create the sales quotation

The workflow begins when a user creates a sales quotation in Dynamics 365 Sales. The **Status** is *In progress* <!-- KFM: Earlier we say *Created*. We seem confused about this in a few places. --> and the **State** is *Draft*. 

The new quotation is then synchronized to Supply Chain Management. The **Status** is *Created* <!-- KFM: More status confusion! -->. Because ownership is with Dynamics 365 Sales, the quotation can't be sent, lost, canceled, confirmed, or deleted from Supply Chain Management. However, users are able to edit the sales quotation in Supply Chain Management.

The following table summarizes the initial status values of the sales quotation in each system and the restrictions that apply.

<!-- KFM: NOTE: For all tables I changed "Similar tos when the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is disabled" to simply "Standard"? -->

| &nbsp; | Sales (owner) | Supply Chain Management |
|---|---|---|
| **Status** value | *Draft* | *Created* |
| **Status reason** value | *In Progress* | N/A |
| Lifecycle restrictions | Standard | Can't be sent, lost, canceled, confirmed, or deleted |
| Data restrictions | Standard | Standard |

<!-- KFM: I think the following tables just repeat the previous one. I suggest deleting them. 

**Dynamics 365 Sales Quotation: Create quotation**

| Result | Status | Status reason | Lifecycle restrictions | Data restrictions |
|---|---|---|---|---|
| Quotation created | Draft | In Progress | *Similar to Integrate Sales Quotation lifecycle with Dynamics 365 Sales feature disabled* | *Similar to Integrate Sales Quotation lifecycle with Dynamics 365 Sales feature disabled* |

**Supply Chain Management Sales Quotation: Quotation synchronization**

| Result | Status | Lifecycle restrictions | Data restrictions |
|---|---|---|---|
| Quotation created | Created | Cannot Generate Send, Lost, Cancel, Confirm, Delete | *Similar to Integrate Sales Quotation lifecycle with Dynamics 365 Sales feature disabled* |

-->

### Step 2: Activate the sales quotation

The sales quotation is activated in Dynamics 365 Sales<!-- KFM: Who does this? Why? What does it indicate IRL? -->. The **Status** is changed to *In progress* and the **State** is changed to *Active*.

The quotation update is synchronized to Supply Chain Management, where the **Status** is changed to *Sent*<!-- KFM: So, this value is different in each system? -->. Because ownership is with Dynamics 365 Sales, the quotation can't be sent, lost, canceled, confirmed, or deleted from Supply Chain Management. Data on the sales quotation is now read-only in Supply Chain Management <!-- KFM: Because of the status value? -->. Activating a quotation in Dynamics 365 Sales also makes it read-only in the Sales user interface <!-- KFM: Because of the status value? -->.

The following table summarizes the status values of the sales quotation in each system and the restrictions that apply.

| &nbsp; | Sales (ownership) | Supply Chain Management |
|---|---|---|
| **Status** value | *Active* | *Sent* |
| **Status reason** value | *In Progress* | N/A |
| Lifecycle restrictions | Standard | Can't be sent, lost, canceled, confirmed, or deleted |
| Data restrictions |  None | Read-only |

<!-- KFM: I think the following tables just repeat the previous one. I suggest deleting them.

**Dynamics 365 Sales Quotation: Activate**

| Result | Status | Status reason | Lifecycle restrictions | Data restrictions |
|---|---|---|---|---|
| Quotation activated | Active | In Progress | *Similar to Integrate Sales Quotation lifecycle with Dynamics 365 Sales feature disabled* |

**Supply Chain Management Sales Quotation: Quotation synchronization**

| Result | Status | Lifecycle restrictions | Data restrictions |
|---|---|---|---|
| Quotation journal created | Sent | Cannot Generate Send, Lost, Cancel, Confirm, Delete | Read Only |

 -->

### Step 3: Revise the sales quotation

The sales quotation is revised in Dynamics 365 Sales.<!-- KFM: Who does this? Why? What does it indicate IRL? --> The **Status** is changed to *Closed* and the **State** is changed to *Revised*.

The quotation update is synchronized to Supply Chain Management, where the **Status** is also changed to *Revised*. Because ownership is with Dynamics 365 Sales, the quotation can't be sent, lost, canceled, confirmed, or deleted from Supply Chain Management. Data on the sales quotation is now read-only in Supply Chain Management <!-- KFM: Because of the status value? -->.

Dynamics 365 Sales automatically creates a new sales quotation based on the revised (and now closed) one <!-- KFM: Correct? -->. The **Status** is *In progress* <!-- KFM: Earlier we say *Created*. We seem confused about this in a few places. --> and the **State** is *Draft*.

The new quotation is then synchronized to Supply Chain Management. The **Status** is *Created* <!-- KFM: More status confusion! -->. Because ownership is with Dynamics 365 Sales, the quotation can't be sent, lost, canceled, confirmed, or deleted from Supply Chain Management. <!-- KFM: But can be edited in SCM? -->

The following table summarizes the status values of the revised sales quotation in each system and the restrictions that apply.

| &nbsp; | Revised quotation in Sales (owner) | New quotation in Sales (owner) | Revised quotation in Supply Chain Management | New quotation in Supply Chain Management |
|---|---|---|---|---|
| **Status** value | *Closed* | *Draft* | *Revised* | *Created* |
| **Status reason** value | *Revised* | *In progress* | N/A | N/A |
| Lifecycle restrictions | Standard | Standard | Can't be sent, lost, canceled, confirmed, or deleted | Can't be sent, lost, canceled, confirmed, or deleted |
| Data restrictions | Standard | Standard | Read-only | Standard |

<!-- KFM: I adapted the below tables into the above one. Maybe check and confirm. I suggest deleting the following tables. 

**Dynamics 365 Sales Quotation: Revise**

| Result | Status | Status reason | Lifecycle restrictions | Data restrictions |
|---|---|---|---|---|
| Quotation Revised | Closed | Revised | *Similar to Integrate Sales Quotation lifecycle with Dynamics 365 Sales feature disabled* | *Similar to Integrate Sales Quotation lifecycle with Dynamics 365 Sales feature disabled* |
| Quotation Created | Draft | In Progress | *Similar to Integrate Sales Quotation lifecycle with Dynamics 365 Sales feature disabled* | *Similar to Integrate Sales Quotation lifecycle with Dynamics 365 Sales feature disabled* |

**Supply Chain Management Sales Quotation: Quotation synchronization**

| Result | Status | Lifecycle restrictions | Data restrictions |
|---|---|---|---|
| Quotation Revised | Revised | Cannot Generate Send, Lost, Cancel, Confirm, Delete | Read Only |
| Quotation Created | Created | Cannot Generate Send, Lost, Cancel, Confirm, Delete | No |

-->

### Step 4: Close the sales quotation

When a user closes an activated sales quotation in Dynamics 365 Sales, different can be applied <!-- KFM: Different what can be applied? -->. Usually, a quotation is closed for one of the following reasons:

- **The quotation is revised**<br>The sales quotation is closed in Dynamics 365 Sales with a **Status reason** of *Revised*. The **Status** is *Closed* and the **State** is *Revised*. The update is then synchronized to Supply Chain Management. The **Status** is *Revised*. <!-- KFM: I'm confused here about Status reason, Status (2 different?), and State. --> Because ownership is with Dynamics 365 Sales, the quotation can't be sent, lost, canceled, confirmed, or deleted from Supply Chain Management. Data on the sales quotation is read-only in Supply Chain Management.

- **The quotation is lost**<br>The sales quotation is closed in Dynamics 365 Sales with a **Status reason** of *Lost*. The **Status** is *Closed* and the **State** is *Lost*. The update is synchronized to Supply Chain Management. The **Status** is *Lost*. <!-- KFM: I'm confused here about Status reason, Status (2 different?), and State. --> Because ownership is with Dynamics 365 Sales, the quotation can't be sent, lost, canceled, confirmed, or deleted from Supply Chain Management. Data on the sales quotation is read-only in Supply Chain Management.

- **The quotation is canceled**<br>The sales quotation is closed in Dynamics 365 Sales with a **Status reason** of *Canceled*. The **Status** is *Closed* and the **State** is *Canceled*. The update is synchronized to Supply Chain Management. The **Status** is *Canceled*. <!-- KFM: I'm confused here about Status reason, Status (2 different?), and State. --> Because ownership is with Dynamics 365 Sales, the quotation can't be sent, lost, canceled, confirmed, or deleted from Supply Chain Management. Data on the sales quotation is read-only in Supply Chain Management.

> [!NOTE]
> No reason code is synchronized between systems for the lost and canceled events in Supply Chain Management. <!-- KFM: Reason code = Status reason? -->

The following table summarizes the status values and restrictions that apply when closing a sales quotation in Dynamics 365 Sales for each of the common reasons.

| Result | Status | Status reason | Lifecycle restrictions | Data restrictions |
|---|---|---|---|---|
| Quotation Closed | *Closed* | *Revised* | Standard | Standard |
| Quotation Closed | *Closed* | *Lost* | Standard | Standard |
| Quotation Closed | *Closed* | *Canceled* | Standard | Standard |

The following table summarizes the status values and restrictions that apply in Supply Chain Management when a sales quotation is closed in Dynamics 365 Sales for each of the common reasons and then synced to Supply Chain Management.

| Result | Status | Lifecycle restrictions | Data restrictions |
|---|---|---|---|
| Quotation Revised | *Revised* | Can't be sent, lost, canceled, confirmed, or deleted | Standard |
| Quotation Lost | *Lost* | Can't be sent, lost, canceled, confirmed, or deleted | Standard |
| Quotation Canceled | *Canceled* | Can't be sent, lost, canceled, confirmed, or deleted | Standard |

### Step 4 variation: Create a sales order from the quotation

When a user creates as sales order from an activated sales quotation in Dynamics 365 Sales, the following events are triggered in Supply Chain Management:

1. Update the sales quotation **Status** to *Confirmed* and generate quotation confirmation journal.
1. The sales order that was created in Dynamics 365 Sales is synchronized and available in Supply Chain Management.
1. Supply Chain Management links the new sales order to the related sales quotation, which enables users to navigate between them.

The following table summarizes the status values and restrictions that apply when a sales order is created from a sales quotation in Dynamics 365 Sales.

| Result | Status | Status reason | Lifecycle restrictions | Data restrictions |
|---|---|---|---|---|
| Quotation won | *Won* | *Won* | Standard | Standard |
| Sales order created | *Active* | *New* | Standard | Standard |

The following table summarizes the status values and restrictions that apply in Supply Chain Management when a sales order is created from a sales quotation in Dynamics 365 Sales and then synced to Supply Chain Management.

| Result | Status | Lifecycle restrictions | Data restrictions |
|---|---|---|---|
| Quotation confirmation journal created | *Won* | Can't be sent, lost, canceled, confirmed, or deleted | Read Only |
| Sales order created | *Open* | <!-- KFM: Value missing --> | <!-- KFM: Value missing --> |

## Change ownership for a sales quotation

It is possible to change the defaulted ownership value on the sales quotation from the Dynamics Supply Chain management sales quotation user interface<!-- KFM: Describe how. -->. This capability is not available from Dynamics 365 Sales quotation. A separate security construct of privilege and duty is assigned to the sales manager role allowing the sales manager to change the ownership of a single sales quotation in Dynamics Supply Chain management <!-- KFM: Does the reader care about this detail? -->. It is not possible to change ownership for multiple sales quotations at a time. It is possible to change the ownership on a sales quotation in any from/to direction when the sales quotation status in Supply Chain management is created and active in Dynamics 365 Sales <!-- KFM: Specify the field names. -->. When the sales quotation status in Supply Chain Management is sent then it is possible to change the ownership to Supply Chain Management. It is possible to change ownership to based on origin, when origin is Supply Chain Management. When the sales quotation is in status sent in Supply Chain Management, it is not possible directly nor indirectly to change ownership to Dynamics 365 Sales. Beyond the status sent in Supply Chain Management, it is not possible to change ownership for a sales quotation.  <!-- KFM: If we really need this kind of detail here, we should have a table showing which combinations of status field values allow a change of ownership. -->

The ownership change event is captured in a separate table log in Supply Chain Management not accessible from the user interface.

## Set default ownership for sales quotations when integrated with Dynamics 365 Sales

By default, the ownership value assigned to a sales quotation when created is *Based on origin*. With feature *Set default ownership for sales quotations when integrated with Dynamics 365 Sales* a setting is added to the **Accounts receivables parameters** page, where the default ownership can be set different from Based on ownership. Default ownership can be set to *Based on origin*, *Dynamics 365 Sales*, or *Supply Chain Management*. When this feature is disabled, ownership is always based on origin.

This setting is per company and allows an organization to, regardless of sales quotation creation happing from Dynamics 365 Sales or Supply Chain Management, always have a constant default ownership.

## Make Supply Chain Management price master when integrated with Dynamics 365 Sales

With the feature Make Supply Chain Management price master when integrated with Dynamics 365 Sales you now have an option to disable Dynamics 365 Sales logic when doing calculations for sales quotations and sales orders.

When enabled, calculations for extended amounts, summary amounts, subtotals, and totals for sales quotations and sales orders will not be performed in Dynamics 365 Sales. When quotations or sales orders are created in Sales, and a price list exists in Sales, then that price will be used, but no other calculations will be made automatically in Sales. All calculated monetary fields are calculated in and synchronized from Supply Chain Management to Sales. When enabled, this feature behaves as if the Sales settings **Use system price calculation** is set to *No* and **Discount calculation method** is set to *Per unit* in Sales regardless of how the settings are in Dynamics 365 Sales. When enabled, the following changes are made in the Sales user interface for sales quotation and sales order lines: The **Volume discount** field is hidden, the "**Line discount amount** field is now replacing **Manual discount** field and is expressed as per-unit discount amount, and the **Manual discount** field is made read-only and relabeled to **Discount** which represents total discount amount which is calculated from Supply Chain Management. Manual discounts can henceforth be entered for a quotation and sales order line in Sales in the **Line discount amount** field.

When enabled, the following fields in Sales are no longer automatically calculated based on Sales logic but rely upon values being synchronized from Supply Chain Management. When a quote and sales order line is created the following fields in Sales will not have values until synchronized from Supply Chain Management:

- Quotation and Sales order line line discount and extended amount.
- Quotation and Sales order Detail Amount, (-) Discount, Pre-Freight Amount, Freight Amount, Total Tax, Total Amount.
- For the Sales Order, the Recalculate option will not perform any recalculation in Sales.

> [!NOTE]
> The following fields in Sales are not mapped 1:1 to fields in the sales order and sales quotation in Supply Chain Management, and require that a Calculate Sales Totals is run to aggregate the data to be synchronized to Sales: Line Discount, (-) Discount, (+) Freight Amount, (+) Total Tax Total Amount. It requires a Totals calculation to be done in Supply Chain Management management before the result is synchronized to Sales, and the amounts on a quotation and sales order in Sales are correctly updated.

## Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales

In some scenarios it is required for a user to on demand recalculate and push prices and totals for one or more sales quotations or sales orders from Supply Chain Management to Sales. This is possible when feature Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales is enabled.

When the feature is enabled a new menu item is added to the sales quotation and sales order list and details pages Push price and totals. When clicking Push price and totals the same update is performed as if a user in Sales clicked Price Quote or Price Order. When Price Quote or Price Order is a request for Supply Chain Management to price the sales order or sales quotation and then synchronize the changes back to Sales, Push price and totals will support scenarios where a user in Supply Chain Management needs to price the sales order or sales quotation and then push the changes to Sales. Same logic, but a push instead of a pull.

When the feature is enabled additionally two new menu items are added to Sales and Marketing>Periodic tasks: Calculate sales order totals for Sales and Calculate sales quotation totals for Sales. These two menu actions allow for use cases complementary and not replacing existing Calculate sales totals. Calculate sales totals supports the use case of calculating both sales order and sales quotation subtotals and totals and synchronizing these to Sales with a fixed recurrence. Calculate sales order totals for Sales and Calculate sales quotation totals for Sales support the use case of needing to perform a calculation of sales quotation or sales order totals for a range of source documents immediately in a non-recurring scenario. The range can be based on sales quotation and order numbers, customer account, and invoice account, while still considering the setting to ignore documents updated before (days). The two settings work in combination. Setting up a recurring batch job is not supported. Use these capabilities when you need to apply a specific range of quotations and orders for which a total calculation should be performed as a one off.

When the feature Process sales quotation related events is enabled together with Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales a setting is added to the Dynamics 365 Sales integration tab of the Accounts receivable parameters page: Calculate and push prices and totals in batch. This setting lets administrators choose whether to Calculate and push prices and totals in batch synchronously or asynchronously through the message processor. When using the message processor, four messages appear. Two for sales order: Calculate and push prices and totals for sales order and Calculate and push totals for sales order. Two for sales quotation: Calculate and push prices and totals for sales quotation and Calculate and push totals for sales quotation.

When the common use case is to select more sales orders and sales quotation for which to do the Push price and totals or Calculate sales order/quotation totals for Sales, then set Calculate and push prices and totals in batch to Yes. This setting will provide the better user experience when working in the Supply Chain Management.

## Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales

Sales orders created from the sales quotation process in Dynamics 365 Sales are not created with the same data as sales orders created from the sales quotation process in Supply Chain Management. This is due to differences in data models between Dynamics 365 Sales and Supply Chain Management. Sales orders created from the sales quotation process in Dynamics 365 Sales have a small set of data (payload) carried forward to the sales order from the sales quotation. When the sales order is synchronized from Dynamics 365 Sales to Supply Chain Management, Supply Chain Management initializes values fields without values using standard Supply Chain Management logic. While this may be appropriate in some scenarios, in other scenarios it is not. In a scenario where Supply Chain Management only fields such as financial dimensions are manually updated on a sales quotation in Supply Chain Management where ownership is with Dynamics 365 Sales, these manually updated financial dimension values are not carried forward to the resulting sales order in Supply Chain Management.

With the feature Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales you now have an option: Use the data from sales order created from the sales quotation in the Dynamics 365 Sales when the sales order is synched to and created in Supply Chain Management regardless of the data on the sales quotation in Supply Chain Management. Or, when the feature is enabled, have the sales order synched to and created in Supply Chain Management have the same field values carried over from the sales quotation in Supply Chain Management regardless of ownership with Dynamics 365 Sales or Supply Chain Management.

Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales is applicable only when the Integrate sales quotation lifecycle with Dynamics 365 Sales feature is enabled.

When the feature Process sales quotation related events is enabled together with Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales a setting is added to the Dynamics 365 Sales integration tab of the Accounts receivable parameters page. This setting lets administrators choose whether to copy quotation information on order creation in real time or through the message processor.

There are pros and cons to copy quotation information on order creation through the message processor.

When copy quotation information on order creation is using the message processor, then the Create Order action will complete be faster compared to not using the message processor. This gives a better user experience in the in the Dynamics 365 Sales user interface when clicking Create Order from a sales quotation. The sales order synched from Dynamics 365 Sales and created in Supply Chain Management will have the data from the sales quotation in Supply Chain Management copied, once the copy quotation information on order creation is processed. Depending on the job execution recurrence setup in the message processor, this can happen with a delay. If this delay is unacceptable, then copy quotation information on order creation can happen immediately upon sales order synched from Dynamics 365 Sales and created in Supply Chain Management. Please note, when copy quotation information on order creation is not using the message processor, the wait time added to the user experience in Dynamics 365 Sales upon Create Order depends on the number of lines on the sales quotation. Fewer lines, less wait time.

## <a name="process-events"></a>Process Dynamics 365 Sales integration related events

The Process Dynamics 365 Sales integration related events feature enables sales quotation events to be processed asynchronously using the message processor framework. The feature is applicable only when Integrate Sales Quotation lifecycle with Dynamics 365 Sales feature is enabled.

When the feature Process sales quotation related events is enabled, two settings are added to the Dynamics 365 Sales integration tab of the Accounts receivable parameters page: Create quotation journal in batch and Create quotation confirmation journal in batch. These settings let administrators choose whether to create the quotation journal or the quotation confirmation journal in real time upon the send and confirm events synchronously or through the message processor when sales quotation ownership is indirectly or directly with Dynamics 365 Sales.

The feature provides new messages for the message processor:

- Create sales quotation journal
- Create sales quotation confirmation journal
- Link sales order and sales quotation

Create quotation journal creates the sales quotation journal. Create quotation confirmation journal and Link sales order from quotation are interrelated in that Link sales order from quotation is dependent on Create quotation confirmation journal being successfully processed; Create quotation confirmation journal creates the sales quotation confirmation journal, Link sales order from quotation results from the confirmation event and updates the sales quotation/sales order relationship. The two messages serve the same use case as the Confirm action in the user interface (Sales and marketing>Sales quotations>All quotations, header ribbon Follow up; group Generate, Confirm action).

When feature Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 is enabled, the Copy sales quotation data to sales order message becomes available.

When feature Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales is enabled, additionally 4 messages are introduced. Two for sales order: Calculate and push prices and totals for sales order and Calculate and push totals for sales order. Two for sales quotation: Calculate and push prices and totals for sales quotation and Calculate and push totals for sales quotation.

When feature Process Dynamics 365 Sales integration related events is enabled, one new message queue is available from the message processor user interface:

- Dynamics 365 Sales Integration

### Setup Process Dynamics 365 Sales integration related events

When Process Dynamics 365 Sales integration related events has been enabled, then navigate to Sales and Marketing>Periodic tasks>Dynamics 365 Sales Integration message processor form to setup the required batch job. Setup the batch job to run with required recurrence. The batch job can also be setup from the System administration>Message processor>Message processor form.

When the feature is enabled, then the Send quotation and Confirm events are processed asynchronously. A single batch job must be setup and be running for the messages from the message queue to be processed automatically.

The messages can be processed using multithreading by defining the number of messages in a task and by defining the number of processor tasks.

When the feature is enabled, a new tab page Dynamics 365 Sales integration is available from Accounts receivables>Setup> Accounts receivables parameters form.

![Schematic representation of step 4](../dual-write/media/add_effciency_14.png)

In tab page Dynamics 365 Sales integration, you setup the number of messages per task. Messages per task represent the maximum number of messages to be processed in a single task. A task is similar to a bundle. The messages per tasks is defaulted to *0* (zero) in the user interface. Number of tasks *0* is interpreted as not being set, and a number of *30* is used implicitly as maximum. Any number higher than *0* (zero) is considered.

It is recommended not to set the (maximum) number of messages too low, such as to the value *1*. It is recommended to set the maximum number of messages in a task to a value which results in a 1-2 minute execution time.
Setting the number of messages per task goes hand in hand with setting the number of processor tasks.

Navigate to System administration>Message processor>Message queue setup form.

![Message queue setup form](../dual-write/media/add_effciency_15.png)

In this form you can specify a number of processor tasks for a specific queue, such as the queue Dynamics 365 Sales integration. If there is no record for the message queue, then the number *5* is used as maximum.
Number of processor tasks value represents the maximum number of processor tasks for the specific queue.

If set, the recommendation is to set the value higher than *1*, while not exceeding the number of maximum batch threads. The value must be considered as a balancing act between expected peak volume and with other workloads running on the same batch servers.

### Monitoring Process Dynamics 365 Sales integration related events

When events are processed leveraging the message queue framework, it is possible to monitor the process from the System Administration>Message Queue>Message process messages form. This form provides insight into queued, failed, and processed messages. The form supports error handling, manual processing, cancelling , and re-queuing of messages.

![Message process messages form](../dual-write/media/add_effciency_16.png)

For more information on the Message processor, see [Create and process custom message queues and message types](../../../../supply-chain/supply-chain-dev/message-processor.md).

## Next steps

- [Enable extra efficiency in quote-to-cash with Dynamics 365 Sales](enable-efficiency-in-quote-to-cash.md)