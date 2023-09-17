---
# required metadata

title: Set up call center channels
description: This article provides information about how to process orders for call centers by using Dynamics 365 Commerce.
author: josaw1
ms.date: 02/04/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: MCROrderParameters, MCRSalesTableOrderHistory, SalesOrderProcessingWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.assetid: 09fca083-ac0d-4f30-baf2-bb00a626be12
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Set up call center channels

[!include [banner](includes/banner.md)]

A company can define multiple call center channels in Dynamics 365 Commerce. Call center channels are configured at **Retail and Commerce** \> **Channels** \> **Call centers** \> **All call centers**, and they are specific to a legal entity.

When a new call center channel is created, it's systematically assigned an operating unit number. Because call centers are created as operating units, users can link the call center channel to various Commerce features, such as assortments, catalogs, and specific modes of delivery.

A default warehouse can be configured on the call center channel. Then, when sales orders are created in that channel, the default warehouse is automatically entered on the sales order header, unless another warehouse has been defined on the customer that is selected for the sales order. In that case, the customer's warehouse is entered by default.

Users must be linked to a call center channel to use the features of call center. Any sales order that a user creates is automatically linked to that user's call center channel. Currently, a single user may not be linked to multiple call center channels at the same time.

An email notification profile can also be configured on the call center channel. The profile defines the set of email templates that is used when email is sent to customers who place orders through the call center channel. The email triggers can be configured against system events, such as order submission or order shipment.

Before sales can be correctly process through a call center channel, correct [payment methods](/dynamics365/unified-operations/retail/work-with-payments) and delivery modes must be defined for the channel.

At the level of the call center channel, you can define other default values that are related to the financial dimensions that will be linked to orders that are created by that channel.

## Options for order processing behavior

Three settings in the configuration of a call center have a major effect on the features and functions that are available for sales orders that are created against that call center: **Enable order completion**, **Enable direct selling**, and **Enable order price control**.

### Enable order completion

The **Enable order completion** setting on the call center channel has a major effect on the order processing flow of sales orders that are entered for that channel. When this setting is turned on, all sales orders must go through a set of validation rules before they can be confirmed. You run these rules by selecting the **Complete** button that is added on the Action Pane of the sales order page. All sales orders that are created when the **Enable order completion** setting is turned on must go through the order completion process. This process enforces the capture of payment and payment validation logic. In addition to payment enforcement, the order submission process can trigger [fraud checks](/dynamics365/unified-operations/retail/set-up-fraud-alerts) that you configure in the system. Orders that fail payment or fraud validations are put on hold and can't be released to further processing (such as picking or shipping) until the issue that caused the hold is resolved.

When the **Enable order completion** setting is turned on for the call center channel, if line items are entered on a sales order and the channel user tries to close or navigate away from the sales order form without first selecting **Complete**, the system enforces the order completion process by opening the sales order recap page and requiring that the user correctly submit the order. If the order can't be correctly submitted together with payment, the user can use the [order holds](/dynamics365/unified-operations/retail/work-with-order-holds) functionality to put the order on hold. If the user is trying to cancel the order, they must correctly cancel it by using either the Cancel function or the Delete function, depending on the function that the user's security allows.

If the **Enable order completion** setting is turned on for the call center channel, the **Payment status** field will be tracked on the order. The system calculates the **Payment status** when the sales order is submitted. Only orders that have an approved payment status are allowed to move through the system for additional order processing steps, such as picking and shipping. If payments are declined, the **do not process** flag will be enabled on the detailed order status, this puts the order on hold until the payment issue is resolved.

Additionally, if the **Enable order completion** setting is turned on, when users create sales orders and are in line item entry mode, the **Source** field will be available on the main sales order header. The **Source** field is used to capture a [catalog source code](/dynamics365/unified-operations/retail/call-center-catalogs) in a direct marketing selling scenario. This code can then drive special prices and promotions.

Even if the **Enable order completion** setting is turned off, users can still apply a source code to a sales order. However, they must first open the sales order header details to access the **Source** field. In other words, some additional clicks are required. The same behavior applies to features such as ship complete and expedited orders. These features are available for all orders that are created in the call center. However, when the **Enable order completion** setting is turned on, users can see the configuration of these features on the sales header while they are in the line entry view. They don't have to drill into the sales order header details to find the appropriate settings and fields.

> [!NOTE]
> When the **Omni-channel Commerce order payments** feature is enabled, the call center **Enable order completion** button will be hidden in headquarters on the **General** FastTab of your channel at **Retail and Commerce \> Channels \> Call Centers**.

### Enable direct selling

If the **Enable direct selling** setting is turned for the call center channel, users can take advantage of the upsell and cross-sell features of Commerce. In this case, pop-up windows appear during order entry and suggest other products that the call center user can offer to the customer. The products that are suggested are based on the product that was just ordered on the sales order line. Currently, the upsell and cross-sell suggestions are configured at the item level on products or catalogs. If the **Enable direct selling** setting is turned off for the call center channel, pop-up windows don't appear during order entry, even if a valid upsell or cross-sell was defined for an item that is being ordered.

When the **Enable direct selling** setting is turned on, the scripts and images features of the sales order entry page are also turned on. In this case, an information panel is available on right side of the page during order entry. This panel can show scripts that are related to the generic order entry process, the catalog source code that was applied, or scripts that are related to the items that are being ordered. Additionally, the images panel can show a product image for the items that are being ordered, if an image has been defined for the item in the product setup.

### Enable order price control

When the **Enable order price control** setting is turned, only authorized users can change the sales price of an item during order entry. The changes must be within defined tolerances. Users who don't have the proper authorization must submit a request for a price change instead. The request will then be processed through system workflows for review and approval.

## Channel users

When you define the call center channel, you must link channel users to the call center. Otherwise, the call center can't be used in the system. When users sign in to Commerce and enter sales orders or return orders on a page that is related to order entry, their user ID is validated against the configuration of the call center channel. If a user is linked to a specific call center channel, orders that the user creates inherit the traits and default values of that channel.

By default, the **Sale** flag on the sales order header is turned on for all orders that call center users create. The orders can then take advantage of the system's commerce-specific price and promotions features.


Users who aren't linked to a call center channel use the standard order entry features of Microsoft Dynamics 365 Finance. Orders that these users enter through the sales order entry form will not be systematically identified as Commerce orders. Additionally, these orders entered by these users will not be subject to any of the order completion processing rules, pricing logic, or other order validations that can be defined in the call center channel configuration or call center system parameters.

After you've finished configuring the call center channel and defining channel users, to help ensure the desired system behavior, make sure that all required Call center parameters are defined at **Retail and Commerce** \> **Channel setup** \> **Call center setup** \> **Call center parameters**. Make sure that related number sequences are also defined.

> [!NOTE]
> To use call center functionality, the configuration key for **Multiple ship-to** must be enabled. This configuration key can be found in the **Trade configuration** keys under **System Administration**\> **Setup** \> **License Configuration**. This is required due to call center functionality that performs various validations based on the delivery address configured at the sales order line level. 



[!INCLUDE[footer-include](../includes/footer-banner.md)]
