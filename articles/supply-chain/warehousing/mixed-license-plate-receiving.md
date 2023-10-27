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

With the deferred receiving process, you can, for example, optimize the process of receiving shipments that include order lines for many items and/or serial numbers by assigning a **Deferred receiving policy ID** for your mobile device menu item. In a scenario with several thousand serial numbers, the system records the serial numbers quickly and stores the information into the *mixed license plate receiving* entities. The system then processes on-hand inventory updates and creates work in the background, which frees warehouse workers to continue doing other work. Deferred receiving processing is useful for warehouse processes where different workers are responsible for inbound receiving and putaway, respectively.

You can configure mobile device menu items that use one of the following **Work creation process** settings to run a deferred receiving process that quickly records incoming inventory and group-registers on-hand inventory against license plates:

- *Purchase order item receiving*
- *Purchase order line receiving*
- *Transfer order item receiving*
- *Transfer order line receiving*
- *Load item receiving*

### Create and assign deferred receiving policies

To use deferred receiving processing, you must first create a deferred receiving policy and assign it to the relevant mobile device menu item(s).

1. Go to **Warehouse management \> Setup \> Mobile device \> Deferred receiving policies**. Identify the policy you want to use or create a new one. Each policy establishes when a receiving flow uses deferred receiving processing and makes a few other options for how the process should work. Use the tooltips provided on the page to learn about how to use each setting.
1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. In the list pane, select the menu item you want to set up. The selected menu item must use one of the work creation policies listed previously.
1. Set **Deferred receiving policy ID** to the policy you identified at the start of this procedure.

> [!NOTE]
> As with the *Mixed license plate receiving* mobile device **Work creation process**, the system can print license plate labels when you run a *deferred receiving* process. These options are among the settings established by the **Deferred receiving policy ID** selected for each menu item.
>
> If you choose to print labels before creating work (as established by the **Label printing on confirming receiving** for the receiving policy), the label won't include details such as the to-location for the license plate because this information won't be available until the system has finished the running the deferred receiving asynchronous process.

### Deferred receiving asynchronous processing

*Deferred asynchronous receiving processing* automatically runs immediately after a mobile device menu item finishes a *Receiving completed* process, which indicates that all the required *Mixed license plate receiving* data is available. You can monitor the status of the process on **Mixed license plate receiving** page, where the **Mixed license plate receiving status** field shows one of the following values:

- *Building license plate*
- *Processing*
- *Error*
- *Received*

If an *Execute deferred receiving [License plate ID]* batch job fails, the related **Mixed license plate receiving status** is set to *Error*. To view the reason for the failure, selected the failed job and then select the **Processing errors** button. Take the appropriate actions to address the error, such as updating a line quantity or deleting a line, and rerun the process manually by selecting the **Complete license plate** button.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
