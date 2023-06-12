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

The *Process Dynamics 365 Sales integration related events* feature enables sales quotation events to be processed asynchronously using the message processor framework. The feature is applicable only when *Integrate Sales Quotation lifecycle with Dynamics 365 Sales* feature is enabled.

### Message queue options

When the feature Process sales quotation related events <!-- KFM: Do you mean *Process Dynamics 365 Sales integration related events*? --> is enabled, two settings are added to the **Dynamics 365 Sales integration** tab of the **Accounts receivable parameters** page: **Create quotation journal in batch** and **Create quotation confirmation journal** in batch. These settings let administrators choose whether to create the quotation journal or the quotation confirmation journal in real time upon the send and confirm events synchronously or through the message processor when sales quotation ownership is indirectly or directly with Dynamics 365 Sales.

### Work with the message queue

[Create and process custom message queues and message types](../../../../supply-chain/supply-chain-dev/message-processor.md)

### Message queue messages

When feature *Process Dynamics 365 Sales integration related events* is enabled, the *Dynamics 365 Sales Integration* message queue is available from the message processor user interface. The system uses this queue to process messages related to the Dynamics 365 Sales integration. The following table describes the messages that are available in the queue and the features required for each message to be available.

| Message type | Feature required | Description |
|---|---|---|
| Calculate and push prices and totals for sales quotation | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | Does a full recalculations of prices, discounts, and totals for sales quotation and pushes the results to Sales. |
| Calculate and push prices and totals for sales order | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | Does a full recalculations of prices, discounts, and totals for sales order and pushes the results to Sales. |
| Calculate and push totals for sales order | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | Calculate and push totals for sales order. |
| Calculate and push totals for sales quotation | *Calculate and push prices, discounts and totals for selective sales orders and sales quotations when integrated to Dynamics 365 Sales* | Calculate and push totals for sales quotation. |
| Create sales quotation journal | *Process Dynamics 365 Sales integration related events* | Creates the sales quotation journal. |
| Create sales quotation confirmation journal| *Process Dynamics 365 Sales integration related events* | Creates the sales quotation confirmation journal. |
| Link sales order and sales quotation | *Process Dynamics 365 Sales integration related events* | Results from the confirmation event and updates the sales quotation/sales order relationship. <!-- KFM: What do we mean by "results from"? --> |
| Copy sales quotation data to sales order | *Copy Supply Chain Management sales quotation data to sales orders synced from Dynamics 365* | <!-- KFM: Description needed -->  |


*Create quotation confirmation journal* and *Link sales order from quotation* are interrelated in that *Link sales order from quotation* is dependent on *Create quotation confirmation journal* being successfully processed. The two messages serve the same use case as the **Confirm** action in the user interface (**Sales and marketing \> Sales quotations \> All quotations**, header ribbon Follow up; group Generate, Confirm action).





### Set up Process Dynamics 365 Sales integration related events

When *Process Dynamics 365 Sales integration related events* has been enabled, then navigate to **Sales and Marketing \> Periodic tasks \> Dynamics 365 Sales Integration message processor** form to set up the required batch job. Setup the batch job to run with required recurrence. The batch job can also be set up from the **System administration > Message processor > Message processor** form. <!-- Give a procedure and describe all settings. -->

When the feature is enabled <!-- KFM: Which feature? -->, then the Send quotation and Confirm events are processed asynchronously <!-- KFM: Use proper names for each event. -->. A single batch job must be set up and be running for the messages from the message queue to be processed automatically. <!-- KFM: Describe how. -->

The messages can be processed using multithreading by defining the number of messages in a task and by defining the number of processor tasks.

When the feature <!-- KFM: Which feature? --> is enabled, a new tab **Dynamics 365 Sales integration** is available from **Accounts receivables \> Setup \> Accounts receivables parameters** page.

![Schematic representation of step 4](../dual-write/media/add_effciency_14.png)

On the **Dynamics 365 Sales integration** tab, you set up the number of messages per task. <!-- Give a procedure and describe all settings. --> Messages per task represent the maximum number of messages to be processed in a single task <!-- Is this a setting? What is the label? --> . A task is similar to a bundle. The messages per tasks is defaulted to *0* (zero) in the user interface. Number of tasks *0* is interpreted as not being set, and a number of *30* is used implicitly as maximum. Any number higher than *0* (zero) is considered.

It is recommended not to set the (maximum) <!-- KFM: Why the parenthesis here? What is the actual label? --> number of messages too low, such as to the value *1*. It is recommended to set the maximum number of messages in a task to a value which results in a 1-2 minute execution time. <!-- KFM: OK, so 2 is good? How do I know what value is right? -->

Setting the number of messages per task goes hand-in-hand with setting the number of processor tasks.<!-- KFM: How so? How do we do this? -->

Go to **System administration \> Message processor \> Message queue setup**.

![Message queue setup form](../dual-write/media/add_effciency_15.png)

In this form you can specify a number of processor tasks for a specific queue, such as the queue Dynamics 365 Sales integration <!-- KFM: Describe how, use field labels. -->. If there is no record for the message queue, then the number *5* is used as maximum. Number of processor tasks value represents the maximum number of processor tasks for the specific queue.

If set <!-- KFM: If what is set? -->, the recommendation is to set the value higher than *1*, while not exceeding the number of maximum batch threads <!-- KFM: Where do I find this? -->. The value must be considered as a balancing act between expected peak volume and with other workloads running on the same batch servers.

### Monitoring Process Dynamics 365 Sales integration related events

When events are processed leveraging the message queue framework, it is possible to monitor the process from the **System Administration \> Message Queue \> Message process messages** page. This page provides insight into queued, failed, and processed messages. The page supports error handling, manual processing, cancelling , and re-queuing of messages.

![Message process messages form](../dual-write/media/add_effciency_16.png)

For more information on the Message processor, see [Create and process custom message queues and message types](../../../../supply-chain/supply-chain-dev/message-processor.md).


