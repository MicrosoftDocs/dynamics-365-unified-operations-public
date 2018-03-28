---
# required metadata

title: Set up a call center channel
description: This topic provides information about how to process orders for call centers using Microsoft Dynamics 365 for Retail. 
author: josaw1
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: MCROrderParameters, MCRSalesTableOrderHistory, SalesOrderProcessingWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 78973
ms.assetid: 09fca083-ac0d-4f30-baf2-bb00a626be12
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update


---

# Set up a call center channel

[!include[banner](includes/banner.md)]

A company can define multiple call center channels in Dynamics 365 for Retail. The call center channel is configured at **Retail > Channels > Call centers > All Call Centers** and they are specific to a legal entity.  

When a new call center channel is created, it will be systematically assigned an Operating Unit number. By making the call center an operating unit, users are then able to link the call center channel to a variety of Retail features including assortments, catalogs, and modes of delivery definitions.  

A default warehouse can be configured on the call center channel. When sales orders are created in this channel, the warehouse will default on the sales order header unless another warehouse has been defined on the selected customer for the sales order, in which case, the customer's warehouse would be the default.

A Dynamics 365 for Retail user is linked to a call center. Because of this, any sales order created by that user in Dynamics 365 for Retail is automatically linked to that call center channel. It's currently not possible for a single user to be linked to multiple call center channels at the same time.   

An email notification profile can also be configured on the call center channel. The profile defines the set of email templates that will be utilized when sending emails to customers placing orders through tje call center channel. The email triggers can be configured against system events, for example, against an order submission or order shipment.  

The call center channel must also have proper [payment methods](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/work-with-payments) and delivery modes defined before sales can be properly processed through the channel.  

Additional defaults related to the financial dimensions that will be linked to orders created by this channel can also be defined at the call center channel level.

## Order processing behavior options

There are three settings on the call center configuration that have a major impact in the features and functions that will be available on sales orders created against this call center:

-**Enable order completion**

Turning on the **Enable order completion** setting on the call center channel will have a major impact in the order processing flow of the sales orders entered for this channel. When enabled, all sales orders will go through a set of payment processing rules. This is executed through the addition of a **Complete** button that will be enabled on the ribbon toolbar of the sales order form. All sales orders created when **Enable order completion** is set must go through the order completion process. This enforces the capture of payment and an order "submission" process. The order submission process provides additional business logic and rules to ensure the order is properly validated for payments and additional [fraud checks](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/set-up-fraud-alerts) that you may configure in the system. Orders that fail these validations will be held for further action and can't be released to further processing (such as picking or shipping) until the issue resulting in the order being held is resolved.

If **Enable order completion** is turned on for the channel and the channel user tries to exit a sales order that has line items entered without first clicking the **Complete** button, the system will enforce the process by popping up the sales order recap form and requiring the user to properly submit the order. If the order can't be properly submitted with a payment, the user may use the [order holds](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/work-with-order-holds) functionality to put the order on hold. If the user is trying to cancel the order, they must properly cancel it using the cancel or delete functions, as their security allows. 

Turning on **Enable order completion** will also activate the use of the **Payment** status on the order.  The **Payment** status is calculated by the system at the time the sales order is submitted. Only approved or authorized payment status orders will be allowed to move through the system for additional order processing steps (such as picking and shipping). Declined or rejected payments will result in the payment status being set to a non-authorized condition and the order will be held by the system until the payment issue is resolved.

Additionally, when **Enable order completion** is turned on for the call center channel, users creating sales orders will find the **Source** field available on the main sales order header section while in line item entry mode of sales order entry. The **Source** field is used to capture the [catalog code](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/call-center-catalogs) in a direct marketing selling scenario. This code can then drive special prices and promotions. Even if **Enable order completion** is turned off, users will have access to apply a source code to a sales order, but they will have to open up the sales order header details to access the field, requiring some additional clicks. The same concept applies for features such as ship complete and expedited orders.  While these features are available for all call center created orders, when **Enable order completion** is turned on, we provide better visibility to the configuration of these features on the sales header while in the line entry view vs. the user having to drill into the sales order header details to find these settings and fields.

-**Enable direct selling**

If **Enable direct selling** is turned on in the call center channel, the user will have the ability to utilize the upsell and cross-sell features of Dynamics 365 for Retail. Upsell and cross-sell functionality provides on-screen pop-ups to the call center user to suggest other products to offer to a customer based on a product just ordered on the sales order line. These upsell and cross-sell suggestions are currently configured at the item level on products. If **Enable direct selling** is not configured for your call center channel, these prompts will not appear during order entry, even if a valid upsell or cross-sell was defined for an item being ordered.

**Enable direct selling** also turns on the scripts and images features of the sales order entry form. During the sales order entry process, if **Enable direct selling** is turned on, users will have access to a slider panel on right side of the sales order entry form. This panel can display scripting related to the generic order entry process, the catalog source code applied, or scripts related to the items being ordered. The images panel can display a product image related to the items being ordered if an image has been defined for the item in product setup.

-**Enable order price control**

**Enable order price control** provides the ability to restrict certain users from changing the sales price of products during the order entry process. When **Enable order price control** is configured, only authorized users will be able to change the sales price of an item during the order entry process, within defined tolerances. A user without proper authorization will only be able to submit a request for a price change. The request will then be processed through system workflows for review and approval

## Channel users

When defining the call center channel, **Channel users** must be linked to the call center for it to be usable in the system. When a user logs into Dynamics 365 for Retail and enters a sales order or return order entry related screen, their user ID will be validated against the call center channel setup. If the user is linked to a particular call center channel, the orders they create will take on the traits and defaults of the channel they are linked to.  

All sales orders created by call center users will have the **Retail sale** flag systematically enabled on the order header and these orders will take advantage of the retail-specific price and promotions features of the system.

If a user is not linked to a call center channel, that user will be utilizing standard Dynamics 365 for Finance and Operations order entry features. Orders entered by users not linked to a call center channel will not be identified as Retail orders and will not be subject to any of the order processing rules, retail pricing logic, or other order validations that can be defined in the call center channel setup or call center system parameters.  

After configuring the necessary setup on the call center channel and defining call center channel users, ensure that any necessary **Call center parameters** (**Retail > Channel setup > Call center setup > Call center parameters**) and related number sequences are also defined to ensure desired system behavior.  
