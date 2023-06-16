---
title: Work with added efficiency in quote-to-cash with Dynamics 365 Sales
description: This article describes how to work with the improved quote-to-cash features when you integrate with Dynamics 365 Sales.
author: henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 05/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Work with added efficiency in quote-to-cash with Dynamics 365 Sales

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]

<!-- KFM: Preview until 10.0.34 GA -->

This article describes how to work with the improved quote-to-cash features when you integrate with Microsoft Dynamics 365 Sales. It provides information about how the  enhanced features that you enable affect the behavior of the integrated system. For more information about how to enable these improvements for your system, see [Enable extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md).

## Set the default ownership for all sales quotations

When the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is [enabled in Dynamics 365 Supply Chain Management](add-efficiency-in-quote-to-cash-enable.md), you can set a default ownership for sales quotations in Supply Chain Management. The default ownership applies to all new sales quotations, regardless of which system they're created in.

Follow these steps to set the default ownership for all sales quotations.

1. In Supply Chain Management, go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. On the **Dynamics 365 Sales integration** tab, on the **Sales quotation** FastTab, in the **Default ownership** field, select one of the following values:

    - *Based on origin* – The ownership of all new sales quotations will match the system that the quotations are created in.
    - *Supply Chain Management* – The ownership of all new sales quotations will be set to *Supply Chain Management*, regardless of which system the quotations are created in.
    - *Dynamics 365 Sales* – The ownership of all new sales quotations will be set to *Dynamics 365 Sales*, regardless of which system the quotations are created in.

## Change ownership for a sales quotation

You can change the ownership of a sales quotation by opening it in Supply Chain Management. You can't change ownership from Sales.

> [!NOTE]
> Before you can change the ownership of a sales quotation, the following conditions must be met:
>
> - Your user account must have the *Change defaulted sales quotation ownership* privilege and the *Maintain sales quotation ownership* duty. By default, the required privilege and duty are assigned to the *Sales manager* role but not to the *Sales clerk* role.
> - The sales quotation must have a status of *Created* or *Send* in Supply Chain Management.
> - The sales quotation must have a status of *Draft* or *Active* in Sales.

Follow these steps to change ownership for a sales quotation.

1. Find and select the quotation that you want to work with (for example, by going to **Sales and marketing \> Sales quotations \> All quotations**). You can't change ownership for multiple sales quotations at the same time. Therefore, be sure to select only one quotation.
1. On the Action Pane, on the **Follow up** tab, select **Change ownership**. Then, in the dropdown dialog box that appears, set the **Ownership** field to one of the following values:

    - *Based on origin* – Inherit the ownership from the **Origin** value.
    - *Supply Chain Management* – Assign ownership to Supply Chain Management.
    - *Dynamics 365 Sales* – Assign ownership to Sales.

1. Select **OK** to apply the change.

Ownership change events are logged in a table in Supply Chain Management. This table isn't available from the user interface (UI). To view it, enter the following URL in your browser's address bar. Replace `<DomainName>` with the domain name of your environment and `<CompanyName>` with the name of your legal entity.

`https://<DomainName>/?cmp=<CompanyName>&mi=SysTableBrowser&TableName=SalesQuotationOwnershipChangeLog`

## Make Supply Chain Management the price master

When the *Make Supply Chain Management price master when integrated with Dynamics 365 Sales* feature is [enabled in Supply Chain Management](add-efficiency-in-quote-to-cash-enable.md), Supply Chain Management becomes the price master for calculations for sales quotations and sales orders. Therefore, the following changes occur when this feature is enabled:

- When a quotation or sales order is created in Sales, if a price list exists in Sales, the price from that price list is used.
- Sales behaves as though its **Use system price calculation** option is set to *No*.
- The following changes are made in the Sales UI for sales quotations and sales order lines:

    - The **Volume discount** field is hidden.
    - The **Line discount amount** field replaces the **Manual discount** field, and its value is expressed as a per-unit discount amount.
    - The **Manual discount** field is made read-only and relabeled **Discount**. This field represents the total discount amount that's calculated from Supply Chain Management.

- In Sales, manual discounts for quotation and sales order lines can be entered in the **Line discount amount** field.
- The following fields in Sales are no longer calculated based on Sales logic. Instead, they rely on values that are calculated and synced from Supply Chain Management. When quotations and sales order lines are created in Sales, these fields won't have values until they're synced from Supply Chain Management.

    - For sales quotations and sales order lines: **Discount** and **Extended amount**
    - For sales quotations and sales order summaries: **Detail amount**, **(-) Discount**, **Pre-freight amount**, **(+) Freight amount**, **(+) Total tax**, and **Total amount**

- For sales orders in Sales, the **Recalculate** option has no effect.

> [!NOTE]
> When you create or update a sales quotation or sales order in Sales, select **Price quote** (for quotations) or **Price order** (for orders) to ensure that all the relevant calculations are done in Supply Chain Management and then synced back to Sales. This step isn't required for quotations and sales orders that are created in Supply Chain Management, provided that the *Calculate sales totals* batch job is set up to run on a regular schedule.

## Calculate and push prices, discounts, and totals from Supply Chain Management to Sales

After you update a sales quotation or sales order in Supply Chain Management, it's important that you push the updated prices, discounts, and totals to Sales. Before you can use this capability, the *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* feature must be [enabled in Supply Chain Management](add-efficiency-in-quote-to-cash-enable.md).

We recommend that you also enable and configure the *Process sales quotation related events* feature, so that you can process the calculations in the background. For more information, see the [Process events related to Sales integration](#process-events) section.

### Fully recalculate and push prices, discounts, and totals

When you fully recalculate and push prices, discounts, and totals, the system checks your trade agreement evaluation policies and, as necessary, searches trade agreements to determine whether line unit prices and discounts must be recalculated. It then retrieves the correct line unit prices and discounts, calculates all the required totals, and syncs them to Sales.

Follow these steps to fully recalculate and push prices, discounts, and totals.

1. In Supply Chain Management, select the sales quotation or sales order that you want to work with. If you're working in a list view, you can select more than one quotation or order.
1. On the Action Pane, on the **Quotation** tab (for quotations) or the **Sell** tab (for orders), select **Push price and totals**.

    The system runs the calculation either synchronously or asynchronously, depending on your configuration of Accounts receivable parameters. For more information, see the [Choose whether to process and push totals synchronously or asynchronously](#synch-async) section.

### Calculate and push totals only

When you calculate and push totals only, the system doesn't recalculate any line unit prices or discounts. Instead, it calculates only new line and header totals and syncs them to Sales.

Follow these steps to calculate and push totals only.

1. In Supply Chain Management, go to one of the following pages, depending on the type of document that you want to work with:

    - **Sales and Marketing \> Periodic tasks \> Calculate sales order totals for Sales**
    - **Sales and Marketing \> Periodic tasks \> Calculate sales quotation totals for Sales**

1. In the dialog box that appears, follow these steps:

    - In the **Ignore documents updated before** field, enter the age (in days) of the oldest document that you want to process.
    - To control which records should be processed, on the **Records to include** FastTab, select **Filter**. A standard query dialog box appears, where you can define selection criteria. The fields work just as they work for other types of queries in Supply Chain Management.

    > [!NOTE]
    > You can't set these jobs to recur on a schedule. They're intended for one-time calculations.

1. Select **OK**.

    The system runs the calculation either synchronously or asynchronously, depending on your configuration of Accounts receivable parameters. For more information, see the [Choose whether to process and push totals synchronously or asynchronously](#synch-async) section.

### <a name="synch-async"></a>Choose whether to process and push totals synchronously or asynchronously

Each time that you trigger a full or totals-only calculation, the system can run the calculation either synchronously or asynchronously, depending on your configuration. Follow these steps to set this option.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. On the **Dynamics 365 Sales integration** tab, set the **Calculate and push prices and totals in batch** option to *Yes* to run the calculation asynchronously. Set it to *No* to run the calculation synchronously.

> [!NOTE]
> We recommend that you set the **Calculate and push prices and totals in batch** option to *Yes*. In that way, users won't have to wait for the system to process data each time that they request a new calculation and push.

### Schedule the Calculate sales totals batch job

We recommend that you set up the *Calculate sales totals* scheduled task so that it runs at a regular interval. In this way, you ensure that all line and order totals are regularly calculated and synced to Sales. This task calculates and pushes the totals only (that is, it doesn't do the full price recalculation that was described earlier). It also pushes taxes and freight charges to Sales.

To set up this scheduled task, go to **Sales and marketing \> Accounts receivable \> Periodic tasks \> Calculate sales totals**.

## Copy Supply Chain Management sales quotation data to sales orders synced from Sales

Because of differences in the data models of the two systems, sales orders that are created from the sales quotation process in Sales don't have the same data as sales orders that are created from the sales quotation process in Supply Chain Management. For sales orders that are created from the sales quotation process in Sales, a small set of data is carried over from the sales quotation. However, when the sales order is synced from Sales to Supply Chain Management, Supply Chain Management might initialize some field values (such as financial dimensions) without using the standard Supply Chain Management logic. Although this behavior might be appropriate in some scenarios, it isn't appropriate in other scenarios.

To control this behavior, either [enable or disable](add-efficiency-in-quote-to-cash-enable.md) the *Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales* feature in Supply Chain Management. The system then works in one of the following ways, depending on whether the feature is enabled or disabled:

- **If the feature is enabled:** Every sales order in Supply Chain Management carries over field values from its related sales quotations in Supply Chain Management, regardless of ownership.
- **If the feature is disabled:** Sales orders in Supply Chain Management don't carry over related sales quotation field values when ownership lies with Sales. Instead, those field values are initialized.

When the *Process sales quotation related events* feature is [enabled in Supply Chain Management](add-efficiency-in-quote-to-cash-enable.md), and the *Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales* feature is also enabled, you can choose whether quotation information is copied in real time upon order creation or through the message processor. Follow these steps to set this option.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. On the **Dynamics 365 Sales integration** tab, set the **Copy quotation data to sales order in batch** option to *No* to copy quotation information in real time upon order creation. Set it to *Yes* to copy quotation information asynchronously.

> [!NOTE]
> We recommend that you set the **Copy quotation data to sales order in batch** option to *Yes*. In that way, users won't have to wait for the system to process the data.

## <a name="process-events"></a>Process events related to Sales integration

The previous sections of this article describe several features that support asynchronous processing of events that are related to the integration with Sales. When you use asynchronous processing, users don't have to wait until processing is completed each time that they make a relevant request. Instead, they can continue to work on other tasks, and the system will process requests when it has time to do so. These features work by adding messages to the *message processor queue*. You can monitor the progress of these messages by using the **Message processor messages** page. This page provides insight into queued, failed, and processed messages. It also supports error handling, manual processing, cancellation, and requeuing of messages.

Before you can use asynchronous processing, the *Process Dynamics 365 Sales integration related events* feature must be [enabled in Supply Chain Management](add-efficiency-in-quote-to-cash-enable.md).

### Set up a batch job to process the Dynamics 365 Sales Integration message queue

When the *Dynamics 365 Sales Integration message processor* batch job runs, the system processes only the *Dynamics 365 Sales Integration* message queue. Therefore, if you want to take advantage of asynchronous processing of integration-related events, follow these steps to schedule the batch job so that it runs regularly.

1. Go to **Sales and Marketing \> Periodic tasks \> Dynamics 365 Sales Integration message processor**.
1. In the **Dynamics 365 Sales integration message processor** dialog box, on the **Run in the background** FastTab, specify how, when, and how often messages in the *Dynamics 365 Sales Integration* queue should be processed. The fields work just as they do for other types of [background jobs](../../sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to apply your settings and close the dialog box.

### Set message processor options

When the *Process Dynamics 365 Sales integration related events* feature is [enabled in Supply Chain Management](add-efficiency-in-quote-to-cash-enable.md), follow these steps to configure how and when it works.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. On the **Dynamics 365 Sales integration** tab, set the following fields:

    - **Create quotation journal in batch** – Set this option to *Yes* to create quotation journals asynchronously by adding messages to the message processor queue. In that way, users won't have to wait until the journal is created each time that they activate a sales quotation from Sales.
    - **Create quotation confirmation journal in batch** – Set this option to *Yes* to create quotation confirmation journals asynchronously by adding messages to the message processor queue. In that way, users won't have to wait until the confirmation journal is created each time that they win a sales quotation from Sales.
    - **Messages per task** – Specify the maximum number of messages that can be processed in a single task. (A task is like a bundle.) In some cases, you might be able to improve your system performance by adjusting this value. You should set it to a value that results in an execution time of one to two minutes. A value of *50* usually works well. We don't recommend that you set a low value. A low value will cause a large number of tasks to be created and can therefore add overhead to the system. If you set this field to *0* (zero), the system will process 30 messages per task. The optimal value for this setting depends on the number of processor tasks that you've configured for the *Dynamics 365 Sales Integration* message queue. For more information, see [Create and process custom message queues and message types](../../../../supply-chain/supply-chain-dev/message-processor.md). Microsoft Support might advise you to adjust the value of this field if you experience performance issues.

### Work with the message queue

You can monitor the progress of your message queue by using the **Message processor messages** page. This page provides insight into queued, failed, and processed messages. It also supports error handling, manual processing, cancellation, and requeuing of messages. For information about how to work with this page and configure settings that are related to the message processor, see [Create and process custom message queues and message types](../../../../supply-chain/supply-chain-dev/message-processor.md).

### Message queue messages

When the *Process Dynamics 365 Sales integration related events* feature is [enabled in Supply Chain Management](add-efficiency-in-quote-to-cash-enable.md), the *Dynamics 365 Sales Integration* message queue is available from the [message processor UI](../../../../supply-chain/supply-chain-dev/message-processor.md). The system uses this queue to process messages that are related to the Sales integration. The following table describes the messages that might be shown in the queue and the features that are required for each message to be available.

| Message type | Required feature | Description |
|---|---|---|
| Calculate and push prices and totals for sales quotation | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | This message type does a full recalculation of prices, discounts, and totals for sales quotation and pushes the results to Sales. |
| Calculate and push prices and totals for sales order | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | This message type does a full recalculation of prices, discounts, and totals for sales order and pushes the results to Sales. |
| Calculate and push totals for sales order | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | This message type calculates and pushes totals for sales orders. |
| Calculate and push totals for sales quotation | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | This message type calculates and pushes totals for sales quotations. |
| Create sales quotation journal | *Process Dynamics 365 Sales integration related events* | This message type creates the sales quotation journal. |
| Create sales quotation confirmation journal | *Process Dynamics 365 Sales integration related events* | This message type creates the sales quotation confirmation journal. |
| Link sales order and sales quotation | *Process Dynamics 365 Sales integration related events* | This message type is created in response to a confirmation event. It updates the sales quotation/sales order relationship. |
| Copy sales quotation data to sales order | *Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365* | This message type copies Supply Chain Management sales quotation data to sales orders that are synced from Sales. |

> [!NOTE]
> *Create sales quotation confirmation journal* and *Link sales order and sales quotation* messages are interrelated, in that *Link sales order and sales quotation* depends on successful processing of *Create sales quotation confirmation journal*. Together, the two messages serve the same purpose as the **Confirm** action when a sales quotation is won in Supply Chain Management.
