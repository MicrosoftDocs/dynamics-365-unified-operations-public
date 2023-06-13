---
title: Work with added efficiency in quote-to-cash with Dynamics 365 Sales
description: This article describes how to work with the improved quote-to-cash features when integrating with Dynamics 365 Sales.
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

This article describes how to work with the improved quote-to-cash features when integrating with Dynamics 365 Sales. It provides information about how the integrated system will behave based on which enhanced features you choose to enable. For details about how to enable these improvements for your system, see [Enable extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md).

## Set the default ownership for all sales quotations

When the *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is enabled, you can set the default ownership of for all new sales quotations (regardless of which system they are created in) in Supply Chain Management. Follow these steps:

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Dynamics 365 Sales integration** tab.
1. Expand the **Sales quotation** FastTab.
1. Set **Default ownership** to one of the following values:
    - *Based on origin* – The ownership of all new sales quotations will be set to match the system they were created in.
    - *Supply Chain Management* – The ownership of all new sales quotations will be set to Supply Chain Management, regardless of which system they are created in.
    - *Dynamics 365 Sales* – The ownership of all new sales quotations will be set to Dynamics 365 Sales, regardless of which system they are created in.

## Change ownership for a sales quotation

You can change the ownership of a sales quotation by opening it in Supply Chain management. You can't do so from Sales.

> [!NOTE]
> To change ownership of a sales quotation, the following conditions must be met:
>
> - Your user account must have the *Change defaulted sales quotation ownership* privilege and *Maintain sales quotation ownership* duty. By default, the required privilege and duty are assigned to the *Sales manager* role, but not to the *Sales clerk* role.
> - The sales quotation must be in status *Created* or *Send* in Supply Chain Management.
> - The sales quotation must be in status *Draft* or *Active* in Sales.

Follow these steps:

1. Find and select the quotation you want to work with, for example by going to **Sales and marketing \> Sales quotations \> All quotations**. You can't change ownership for multiple sales quotations at a time, so select only one quotation.
1. On the Action Pane, open the **Follow up** tab and select **Change ownership** to open a drop-down dialog box. Then set **Ownership** to one of the following values:
    - *Based on origin* – The ownership will be inherited from the **Origin** value.
    - *Supply Chain Management* – The ownership will be assigned to Supply Chain Management.
    - *Dynamics 365 Sales* – The ownership will be assigned to Dynamics 365 Sales.
1. Select **OK** to apply the change.

Ownership change events are logged in a table in Supply Chain Management that isn't available from the user interface. To see it, enter the following URL in your browser: `https://<DomainName>/?cmp=<CompanyName>&mi=SysTableBrowser&TableName=SalesQuotationOwnershipChangeLog`, where `<DomainName>` is the domain name of your environment and `<CompanyName>` is the name of your legal entity.

## Make Supply Chain Management price master

When the feature *Make Supply Chain Management price master when integrated with Dynamics 365 Sales* is enabled, Supply Chain Management becomes the price master for making calculations for sales quotations and sales orders. Therefore, the following conditions apply when this feature is enabled:

- When a quotation or sales order is created in Sales, and a price list exists in Sales, then that price will be used.
- Sales behaves as though its **Use system price calculation** setting is set to *No*.
- The following changes are made in the Sales user interface for sales quotation and sales order lines:
    - The **Volume discount** field is hidden.
    - The **Line discount amount** field replaces the **Manual discount** field and is expressed as per-unit discount amount.
    - The **Manual discount** field is made read-only and relabeled to **Discount** which represents total discount amount which is calculated from Supply Chain Management.
- In Sales, manual discounts can be entered for quotation and sales order lines in the **Line discount amount** field.
- The following fields in Sales are no longer calculated based on Sales logic but instead rely upon values that are calculated and synchronized from Supply Chain Management. When a quote and sales order line is created in Sales, these fields won't have values until they are synchronized from Supply Chain Management.
    - For sales quotations and sales order lines: **Discount** and **Extended amount**.
    - For sales quotations and sales order summaries: **Detail amount**, **(-) Discount**, **Pre-freight amount**, **(+) Freight amount**, **(+) Total tax**, and **Total amount**.
- For sales orders in Sales, the **Recalculate** option will have no effect.

> [!NOTE]
> When you create or update a sales quotation or sales order Dynamics 365 Sales, select **Price quote** (for quotes) or **Price order** (for orders) to make sure all of the relevant calculations are done in Supply Chain Management and synced back to Sales. This isn't necessary for quotes and sales orders created in Supply Chain Management provided the *Calculate sales totals* batch job is set to run on a regular schedule.

## Calculate and push prices, discounts, and totals from Supply Chain Management to Sales

After updating a sales quotation or sales order in Supply Chain Management, it's important to push the updated prices, discounts, and totals to Sales. To enable this ability, the *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* must be enabled in Supply Chain Management (see also [Enable extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md)).

To process the calculations in the background, you must also enable the *Process sales quotation related events* feature (recommended). Background calculations are managed by the message processor as described in XXXX <!-- KFM: Link to later section about this. -->

### Fully recalculate and push prices, discounts, and totals

When you fully recalculate and push prices, discounts, and totals, the system checks trade agreement evaluation policies and, if necessary, searches trade agreements to see whether line unit prices and discounts need to be recalculated. It then retrieves the correct line unit prices and discounts, calculates all the totals required, and syncs them to Sales.

Do the following steps to work with this feature:

1. In Supply Chain Management, select the sales quotation or sales order you want to work with. If you are working in a list view, you can select more than one quotation or order.
1. On the Action Pane, open the **Quotation** tab (for quotations) or the **Sell** tab (for orders) and select **Push price and totals**.
1. The system will now run the calculation either synchronously or asynchronously based on your system preferences, as described in [Choose whether to process totals synchronously or asynchronously](#synch-async).

### Calculate and push totals only

When you calculate and push totals only, the system doesn't recalculate any line unit prices or discounts. Instead, it only calculates new line and header totals and syncs them to Sales.

Do the following steps to work with this feature:

1. In Supply Chain Management, go to one of the following, based on the type of document you want to work with:
    - **Sales and Marketing \> Periodic tasks \> Calculate sales order totals for Sales**
    - **Sales and Marketing \> Periodic tasks \> Calculate sales quotation totals for Sales**
1. A dialog box opens. Make the following settings:
    - **Ignore documents updated before** – Enter a number of days to define the oldest document that you want to process.
    - To control which records should be processed, on the **Records to include** FastTab, select **Filter**. A standard query dialog appears, where you can define selection criteria. The fields work just as they work for other types of queries in Microsoft Dynamics 365 Supply Chain Management.
    - Note that you can't set these jobs to recur on a schedule. They are intended for one-off calculations.
1. Select **OK**.
1. The system will now run the calculation either synchronously or asynchronously based on your system preferences, as described in [Choose whether to process totals synchronously or asynchronously](#synch-async).

### <a name="synch-async"></a> Choose whether to process totals synchronously or asynchronously

Each time you trigger a full or totals-only calculation, the system can run the calculation either synchronously or asynchronously based on your system preferences. To set your preferences, do the following steps:

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Dynamics 365 Sales integration** tab.
1. Set **Calculate and push prices and totals in batch** to *Yes* to run the calculation asynchronously. Set it to *No* to run the calculation synchronously.

> [!NOTE]
> We recommend that you enable the **Calculate and push prices and totals in batch** option because then users won't need to wait for the system to process the data.

### Schedule the Calculate sales totals batch job

We recommend that you set up the scheduled task called *Calculate sales totals* to run at a regular interval to ensure that all line and order totals are regularly calculated and synced to Sales. This task calculates and pushes the totals only (it doesn't do the full price recalculation described previously), and includes pushing taxes and freight charges to sales.

To set up this scheduled task, go to **Sales and marketing \> Accounts receivable \> Periodic tasks \> Calculate sales totals**.

## Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales

Sales orders created from the sales quotation process in Dynamics 365 Sales are not created with the same data as sales orders created from the sales quotation process in Supply Chain Management. This is due to differences in data models between Dynamics 365 Sales and Supply Chain Management. Sales orders created from the sales quotation process in Dynamics 365 Sales have a small set of data carried forward to the sales order from the sales quotation. When the sales order is synchronized from Dynamics 365 Sales to Supply Chain Management, Supply Chain Management initializes field values without using standard Supply Chain Management logic. While this may be appropriate in some scenarios, in other scenarios it is not. In a scenario where Supply Chain Management only fields such as financial dimensions are manually updated on a sales quotation in Supply Chain Management where ownership is with Dynamics 365 Sales, these manually updated financial dimension values are not carried forward to the resulting sales order in Supply Chain Management.

To control this behavior, either enable or disable the feature called *Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales* (see also [Enable extra efficiency in quote-to-cash with Dynamics 365 Sales](add-efficiency-in-quote-to-cash-enable.md)). Based on this condition, the system will work as follows:

- **When the feature is enabled** – The sales order in Supply Chain Management will have field values carried over from the sales quotation in Supply Chain Management regardless of ownership.
- **When the feature is disabled** – The sales order in Supply Chain Management the field values won't be carried over when ownership is with Dynamics 365 Sales. Instead they will be initialized.

When the *Process sales quotation related events* feature is enabled together with *Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales* feature, you can choose whether to copy quotation information on order creation in real time or through the message processor. Follow these steps to set this option:

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Dynamics 365 Sales integration** tab.
1. Set **Copy quotation data to sales order in batch** to *No* to copy quotation information on order creation in real time. Set it to *Yes* to copy quotation information asynchronously.

> [!NOTE]
> We recommend that you enable the **Copy quotation data to sales order in batch** option because then users won't need to wait for the system to process the data.

## <a name="process-events"></a>Process Dynamics 365 Sales integration related events

The *Process Dynamics 365 Sales integration related events* feature enables sales quotation events to be processed asynchronously using the message processor framework.

This topic describes several features that support asynchronous processing of events related to the integration with Dynamics 365 Sales. These features work by adding messages to the message processor queue. You can monitor the progress of these messages using the **Message processor messages** page. It provides insight into queued, failed, and processed messages. The page also supports error handling, manual processing, cancelling , and re-queuing of messages.

### Set up a batch job to process Dynamics 365 Sales Integration message queue

The system will only process the *Dynamics 365 Sales Integration* message queue when the *Dynamics 365 Sales Integration message processor* batch job runs. Therefore, if you want to take advantage of asynchronous processing of integration-related events, you must schedule this batch job to run on a regular basis, as described in the following procedure:

1. Go to **Sales and Marketing \> Periodic tasks \> Dynamics 365 Sales Integration message processor**.
1. The **Dynamics 365 Sales integration message processor** dialog opens. On the **Run in the background** FastTab, specify how, when, and how often to process messages in the *Dynamics 365 Sales Integration*  queue. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK** to apply your settings and close the dialog box.

### Set message processor options

When the *Process Dynamics 365 Sales integration related events* feature is enabled, you can configure the feature by following these steps:

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Dynamics 365 Sales integration** tab.
1. Make the following settings:
    - **Create quotation journal in batch** – Set this to *Yes* to create quotation journals asynchronously by adding a messages to the message processor queue, which will prevent the user from needing to wait for the journal to be created each time they activate a sales quotation from Sales.
    - **Create quotation confirmation journal in batch** – Set this to *Yes* to create quotation confirmation journals asynchronously by adding a messages to the message processor queue, which will prevent the user from needing to wait for the confirmation journal to be created each time they win a sales quotation from Dynamics 365 Sales.
    - **Messages per task** – Set the maximum number of messages to be processed in a single task (a task is similar to a bundle). In some cases, you may be able to improve your system performance by adjusting this value. If you set this field to *0*, then the system will process 30 messages per task. You should set it to a value which results in a 1-2 minute execution time. A value of 50 usually works well. We recommend against setting a low value because that will result in a large number of tasks being created, which will add overhead to the system. The optimal value for this setting also depends on how many processor tasks you have configured for the *Dynamics 365 Sales Integration* message queue (see also [Create and process custom message queues and message types](../../../../supply-chain/supply-chain-dev/message-processor.md)). Microsoft support may advise you to adjust this value if you are experiencing performance issues.

### Work with the message queue

You can monitor the progress of your message queue using the **Message processor messages** page. It provides insight into queued, failed, and processed messages. The page also supports error handling, manual processing, cancelling , and re-queuing of messages. For details about how to work with this page and configure settings related to the message processor, see [Create and process custom message queues and message types](../../../../supply-chain/supply-chain-dev/message-processor.md).

### Message queue messages

When feature *Process Dynamics 365 Sales integration related events* is enabled, the *Dynamics 365 Sales Integration* message queue is available from the [message processor user interface](../../../../supply-chain/supply-chain-dev/message-processor.md). The system uses this queue to process messages related to the Dynamics 365 Sales integration. The following table describes the messages that are available in the queue and the features required for each message to be available.

| Message type | Feature required | Description |
|---|---|---|
| Calculate and push prices and totals for sales quotation | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | Does a full recalculations of prices, discounts, and totals for sales quotation and pushes the results to Sales. |
| Calculate and push prices and totals for sales order | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | Does a full recalculations of prices, discounts, and totals for sales order and pushes the results to Sales. |
| Calculate and push totals for sales order | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | Calculate and push totals for sales order. |
| Calculate and push totals for sales quotation | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | Calculate and push totals for sales quotation. |
| Create sales quotation journal | *Process Dynamics 365 Sales integration related events* | Creates the sales quotation journal. |
| Create sales quotation confirmation journal| *Process Dynamics 365 Sales integration related events* | Creates the sales quotation confirmation journal. |
| Link sales order and sales quotation | *Process Dynamics 365 Sales integration related events* | Created is response to a confirmation event and updates the sales quotation/sales order relationship. |
| Copy sales quotation data to sales order | *Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365* | Copies Supply Chain Management sales quotation data to sales orders synced from Dynamics 365 Sales.  |

> [!NOTE]
> *Create quotation confirmation journal* and *Link sales order from quotation* are interrelated in that *Link sales order from quotation* is dependent on *Create quotation confirmation journal* being successfully processed. The two messages serve the same use case as the **Confirm** action when winning a sales quotation in Supply Chain Management.
