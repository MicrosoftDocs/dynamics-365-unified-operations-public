---
# required metadata

title: Mixed license plate receiving
description: This article describes how to use mixed license plate receiving to register and create work for multiple items with a mobile device.
author: Mirzaab
ms.date: 05/26/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  WHSMixedLPReceiving, WHSRFAutoConfirm, WHSLicensePlate, WHSRFMenuItem, WHSDeferredReceivingPolicy
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Mixed license plate receiving

[!include [banner](../includes/banner.md)]

Mixed license plate receiving allows you to build a license plate consisting of multiple items before you register and create putaway work.

A license plate that consists of multiple items doesn't have to be split at the receiving dock for you to register each item.

When using an item-related flow to identify the source document lines, you can scan bar codes on the item control. If the bar code has a quantity and a unit of measure (UOM) configured on it, the item and quantity will automatically be added to the mixed license plate, and you'll be returned to the screen to scan another item. This allows you to quickly scan all the items without having to make a confirmation at each step.

In the flow for mixed license plate receiving, you can display the list of items that are already scanned to the license plate and from here you can modify or correct the quantity of an item.

## Where it applies

Mixed license plate receiving is a mobile device receiving flow to register and create work for multiple lines/items at the same time. This is useful if you receive inbound license plates with multiple items.

The [*deferred receiving*](#deferred-receiving-processing) process uses both the specific *Mixed license plate receiving* mobile device flow and the data entities part of the **Mixed license plate receiving** page.  

## How to set up mixed license plate receiving

Mixed license plate receiving is set up as a mobile device menu item.

You need to create a new menu item with mode work that doesn't use existing work and use one of the following work creation processes:

- Mixed license plate receiving
- Mixed license plate receiving and put away

The following options for identifying the source document lines are available:

- Purchase order item receiving
- Purchase order line receiving
- Transfer order item receiving
- Transfer order line receiving
- Inbound shipment order item receiving
- Inbound shipment order line receiving
- Return order receiving
- Load item receiving

> [!NOTE]
> You can add multiple items to a license plate for all the source document line identification methods. However, although you can change the receiving order on a single license plate during the receiving process for all the other methods, you can't change the selected load for the *Load item receiving* method.

## <a name="deferred-receiving-processing"></a>Deferred receiving processing

The deferred receiving process lets you, for example, optimize the process of receiving shipments that include order lines for many items and/or serial numbers by assigning a **Deferred receiving policy ID** value to your mobile device menu item. In a scenario that involves several thousand serial numbers, the system quickly records the serial numbers and stores the information in the *mixed license plate receiving* entities. It then processes on-hand inventory updates and creates work in the background, so that warehouse workers can continue to do other work. Deferred receiving processing is useful for warehouse processes where different workers are responsible for inbound receiving and putaway.

You can configure mobile device menu items that use one of the following **Work creation process** settings to run a deferred receiving process that quickly records incoming inventory and group-registers on-hand inventory against license plates:

- *Purchase order item receiving*
- *Purchase order line receiving*
- *Transfer order item receiving*
- *Transfer order line receiving*
- *Load item receiving*

### Create and assign deferred receiving policies

To use deferred receiving processing, you must first create a deferred receiving policy and assign it to the relevant mobile device menu items.

1. Go to **Warehouse management \> Setup \> Mobile device \> Deferred receiving policies**.
1. Identify the policy that you want to use, or create a new one. Each policy defines when a receiving flow uses deferred receiving processing. It also sets a few other options that control how the process works. Use the tooltips that are provided on the page to learn how to use each setting.
1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. In the list pane, select the menu item that you want to set up. The selected menu item must use one of the previously listed work creation policies.
1. Set the **Deferred receiving policy ID** field to the policy that you identified in step 2.

> [!NOTE]
> As for the *Mixed license plate receiving* mobile device work creation process, the system can print license plate labels when you run a deferred receiving process. The options are among the settings that are established by the deferred receiving policy ID that's selected for each menu item.
>
> If you set the **Label printing on confirming receiving** field so that labels are printed before work is created, the labels won't include details such as the "to" location for the license plate, because this information won't be available until the system has finished running the deferred receiving asynchronous process.

### Deferred receiving asynchronous processing

*Deferred asynchronous receiving processing* automatically runs immediately after a mobile device menu item completes a *Receiving completed* process, which indicates that all the required *Mixed license plate receiving* data is available. You can monitor the status of the process on the **Mixed license plate receiving** page, where the **Mixed license plate receiving status** field shows one of the following values:

- *Building license plate*
- *Processing*
- *Error*
- *Received*

If an *Execute deferred receiving \[License plate ID\]* batch job fails, the related **Mixed license plate receiving status** field is set to *Error*. To view the reason for the failure, select the failed job, and then select **Processing errors**. Take the appropriate action to address the error (for example, by updating a line quantity or deleting a line). Then manually rerun the process by selecting **Complete license plate**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
