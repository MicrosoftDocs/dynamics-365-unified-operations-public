---
title: Mixed license plate receiving
description: Learn how to use mixed license plate receiving to register and create work for multiple items with a mobile device with an outline on where it applies.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 01/29/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:  WHSMixedLPReceiving, WHSRFAutoConfirm, WHSLicensePlate, WHSRFMenuItem, WHSDeferredReceivingPolicy
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
- *Inbound shipment order item receiving*
- *Inbound shipment order line receiving*
- *Load item receiving*
- *License plate receiving*

### Prerequisites

Deferred receiving processing requires Supply Chain Management 10.0.38 or higher.

### Create and assign deferred receiving policies

To use deferred receiving processing, you must first create a deferred receiving policy and assign it to the relevant mobile device menu items.

1. Go to **Warehouse management \> Setup \> Mobile device \> Deferred receiving policies**.
1. Identify the policy that you want to use, or create a new one. Each policy defines when a receiving flow uses deferred receiving processing. It also sets a few other options that control how the process works. Use the tooltips that are provided on the page to learn how to use each setting.
1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. In the list pane, select the menu item that you want to set up. The selected menu item must use one of the previously listed work creation policies.
1. Set the **Deferred receiving policy ID** field to the policy that you identified in step 2.

#### Print license plate labels as part of the receiving process

For other mobile menu item receiving processes, the system can generate and print license plate labels when you run a deferred receiving process. You can enable this capability by using the settings that are established by the deferred receiving policy that's selected for each menu item.

You can set the system to generate up to two license plate labels by using the following options:

- **Label printing on confirming receiving** – Generate and print labels immediately (before registration and work creation).
- **Label printing on deferred receiving async processing** – Generate and print labels based on the work data.

If you set the **Label printing on confirming receiving** option so that labels are printed before work is created, the labels don't include details such as the "to" location for the license plate. This information is omitted because it isn't available until after the system finishes running the deferred receiving asynchronous process.

> [!NOTE]
> You can use the **Reprint label** mobile device menu item as a detour process to print the label that's generated by the **Label printing on deferred receiving async processing** option as part of the putaway process.
  
### Deferred receiving asynchronous processing

*Deferred asynchronous receiving processing* automatically runs immediately after a mobile device menu item completes a *Receiving completed* process, which indicates that all the required *Mixed license plate receiving* data is available. You can monitor the status of the process on the **Mixed license plate receiving** page, where the **Mixed license plate receiving status** field shows one of the following values:

- *Building license plate*
- *Processing*
- *Error*
- *Received*

If an *Execute deferred receiving* batch job fails, the related **Mixed license plate receiving status** field is set to *Error*. To view the reason for the failure, select the failed job, and then select **Processing errors**. Take the appropriate action to address the error (for example, by updating a line quantity or deleting a line). Then manually rerun the process by selecting **Complete license plate**.

> [!TIP]
> If you want the page to show the **Receiving processing ID** value that's used for each background processing task, use the [personalization tools](../../fin-ops-core/dev-itpro/get-started/personalize-user-experience.md) to add the column to the **Mixed license plate receiving** grid.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
