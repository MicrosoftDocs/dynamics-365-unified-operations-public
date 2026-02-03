---
title: Configure and work with call center order holds
description: Learn how to configure and work with call center holds on orders in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 01/30/2026
ms.topic: how-to
ms.search.form: MCRHoldCodeTable, MCRSalesTableOrderHistory, MCRHoldCodeTrans, MCROrderEventSetup, MCROrderEventTable
ms.reviewer: v-griffinc
ms.assetid: 7c00dc35-73e5-400a-8587-22f37ddfc0e0
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.custom: 
  - bap-template
---

# Configure and work with call center order holds

[!include [banner](includes/banner.md)]

This article describes how to configure and work with call center holds on orders in Microsoft Dynamics 365 Commerce.

## Configuring call center order holds

To use the call center order hold features, first define hold codes. To create a set of user-defined hold codes based on your business requirements, go to **Sales and marketing** > **Setup** > **Sales orders** > **Order hold codes**. You can optionally flag one of the hold codes as the default hold code by setting the **Default for sales order** option to **Yes** for it. This hold code is used whenever a sales order is on hold. If a sales order has reserved inventory, and the reservations must be automatically removed if the order is on hold for a particular reason, set the **Remove inventory reservations** option to **Yes** for the reason codes.

To specify the type of note that the system captures when users who put a sales order on hold enter optional notes, go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**. On the **Sales setup** FastTab, on the **General** tab, set the **Note type** field. Use the **On Hold sales order status** field to define the color that highlights sales orders that are on hold when users view them on the **Customer service** page.

To create an optional set of hold reason codes, go to **Retail and Commerce** > **Channel setup** > **Info codes**. Use these info codes as a secondary reason code to further define the main hold code. Select **New** to create a reason code set, and then select **Subcodes** to define the list of other reasons. To link any info codes that you define to the call center channel, go to **Retail and Commerce** > **Channels** > **Call centers** > **All call centers**. On the **General** FastTab, set the **Hold code** field.

## Putting orders on hold

Call center users can put orders on hold that they create in Commerce headquarters. Users can also put orders on hold automatically in specific situations.

During order entry, but before order submission and confirmation, call center users might want to put an order on hold to prevent it from being released to the warehouse for further processing. For example, the customer who is placing the order might not be ready to commit to it, or critical data that is required to process the order might be missing.

On the order entry page, the call center user can put an order on hold by using the **Order holds** option on the **Sales order** tab of the order entry menu. Alternatively, the user can select the **Hold** menu item on the **Sales order summary** page that appears when the user selects **Complete** on a call center sales order.

In both cases, the **Order holds** page appears. The user can then select **New** to create a hold for the order. In the **Hold code** field, the user should select the code that best describes the reason for the hold. In the **Reason code** field, the user can optionally select another code to provide a second level of description of the hold.

On the **Notes** FastTab, in the **Hold Notes** field, the user can enter additional, free-form notes to provide extra context or information about the hold. These notes can help other users who review or work with the hold order later.

After the user enters and saves the hold information, they can close the **Order holds** page. The user is then returned to the sales order entry page. If no further actions are required on the sales order, the user can close the sales order entry page.

If the **Enable order completion** flag is turned on in the call center channel, payment doesn't have to be applied to an order that's on hold. By contrast, for a sales order that isn't on hold, users can't leave the sales order entry page until payment is applied. Payment is required before the order hold is released.

Additionally, call center users can put a manual fraud hold on orders that are suspicious for some reason. Orders can also be put on hold automatically when they match active fraud criteria and rules. For more information on this type of order hold, see [Set up fraud alerts](/dynamics365/unified-operations/retail/set-up-fraud-alerts).

## Viewing and managing orders that are on hold

### Viewing hold information for a single sales order

On the **Customer service** page, users can visually identify orders that are on hold because the order lines are highlighted in a specific color. This color is defined by the **On Hold sales order status** field on the **Accounts receivable parameters** page.

> [!NOTE]
> If the line is selected on the page, the highlight color isn't visible.

Users can also view detailed status information for a sales order to learn whether the order is on hold. Users can access the detailed status information from the **All sales orders** or **Customer service** page. If an order is on hold, the **Do not process** flag is set for the order, and the **Detailed status** field shows a status of either **On Hold** or **Fraud Hold**, depending on the scenario.

To view the details of an individual order hold, users can open a detailed view of the **Order hold** page from the **Customer service** page by using the **Options** menu for the selected order. Users can also access this view from the **All sales order** page by selecting the **Order holds** menu item on the **Sales order** tab.

### Viewing all orders that are on hold

To view all orders that are on manual or automatic hold, go to **Retail and Commerce** \> **Customers** \> **Order holds**.

The **Order holds** workbench provides a list view of all orders that are on hold because of manual or fraud-related hold actions. By taking advantage of the standard filtering and sorting options on the page, users can create views that let them work with or manage specific hold codes that they're responsible for reviewing. The **Order holds** workbench also indicates the number of days that an order Is been on hold. This information can help users prioritize the queue.

To get a more detailed view of the orders that are on hold, users can select the **Order hold** option on the menu. This view provides information about the customer, any notes that users apply to the order, customer, or hold action. The view also provides details about the reason for an automatic hold if the order was put on hold because it matched a fraud rule.

From both the list view and the detailed view of the **Order holds** page, users can view or edit more order-related information, such as payments, totals, and notes.

The options on the **Hold checkout** tab might be useful if multiple users in your company work on the hold queue at the same time. By selecting the **Check out** option, users can indicate that they're working to review and investigate the order hold. In this way, other users don't waste time by trying to do the same work. From the detailed view of the **Order holds** page, users can view information about the checkout date and time, and the user who checked out the hold record.

After a hold record is checked out, only the user who checked it out can clear the checkout. This restriction prevents users from taking records that other users are already working on. To release an order back to the queue so that other users can work on it, the user who checked out the record selects the **Clear checkout** option.

> [!NOTE]
> The hold isn't released when the checkout is cleared.

In some situations, such as when a user is out sick or leaves the company, another user might have to reassign records that are checked out to that user. A manager can reassign records by using the **Override checkout** option.

## Releasing orders that are on hold

In both the list view and the detailed view of the **Order holds** page, the **Clear hold** tab contains the options that you use to release an order hold. Use the **Clear holds** option to release an order from the selected hold code.

Call center orders require payment. Therefore, you can't fully clear a hold if payment isn't applied to the order. On the **Call center parameters** page, on the **Holds** tab, make sure that the **Submit when cleared** parameter is turned on. This setting helps guarantee that a cleared hold order goes through the correct order submission logic to validate and authorize payments. If payments are missing, the user receives an error, and the hold code isn't cleared.

If the **Submit when cleared** parameter isn't set, users should select the **Clear and submit** option on the **Clear hold** menu to help guarantee that the order goes through all the required payment validations. If order submission fails when the **Enable order completion** flag is turned on in the call center channel, the order is released from its hold status, but the **Do not process** flag remains set. Therefore, the order isn't released to the warehouse until correct payments are applied and validated.

If users want to clear a hold but make more changes to the order before it's released for further processing, they can select the **Clear and modify** option. This option removes the hold code and opens the sales order details so that users can make additional changes to the order. Users can also apply payment and submit the sales order through payment validation logic when the **Enable order completion** flag is turned on in the call center channel.

## Reporting options

Go to **Retail and Commerce** \> **Inquiries and reports** \> **Call center reports** \> **Order holds report** to run a report about order holds by date range, hold code, or other related criteria.


[!INCLUDE[footer-include](../includes/footer-banner.md)]