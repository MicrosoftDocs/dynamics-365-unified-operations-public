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

Mixed license plate receiving allows you to build a license plate consisting of multiple items before you register and create put-away work.

A license plate that consists of multiple items does not have to be split at the receiving dock for you to register each item.

When using an item-related flow to identify the source document lines, you can scan bar codes on the item control. If the bar code has a quantity and a unit of measure (UOM) configured on it, the item and quantity will automatically be added to the mixed license plate, and you will be returned to the screen to scan another item. This allows you to quickly scan all the items without having to make a confirmation at each step.

In the flow for mixed license plate receiving, you can display the list of items that are already scanned to the license plate and from here you can modify or correct the quantity of an item.

## Where it applies

Mixed license plate receiving is a mobile device receiving flow to register and create work for multiple lines/items at the same time. This is useful if you receive inbound license plates with multiple items.

Besides the specific _Mixed license plate receiving_ mobile device flow, the [_deferred receiving process_](#deferred-receiving-processing) uses the data entities part of the _Mixed license plate receiving_ page.  

## How to set up mixed license plate receiving

Mixed license plate receiving is set up as a mobile device menu item.

You need to create a new menu item with mode work that does not use existing work and use one of the following work creation processes:

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
> You can add multiple items to a license plate for all the source document line identification methods. However, although you can change the receiving order on a single license plate during the receiving process for all the other methods, you can't change the selected load for the _Load item receiving_ method.

## <a name="deferred-receiving"></a>Deferred receiving processing

Besides using the _Mixed license plate receiving_ and _Mixed license plate receiving and put away_ mobile device menu items, to quickly record incoming inventory and get it inventory on-hand group-registered against a license plate, you can use the following below mobile device menu item flows to run a deferred receiving process:

- Purchase order item receiving
- Purchase order line receiving
- Transfer order item receiving
- Transfer order line receiving
- Load item receiving

With the deferred receiving process you can for example optimize the process of receiving shipments that include order lines for many items and/or serial numbers by assigning a **Deferred receiving policy ID** for your mobile device menu item. In a scenario with several thousand serial numbers the system can record the serial numbers in a quick manner and store the information into the _mixed license plate receiving_ entities. A background process will following process the actual inventory on-hand updates and work creation processes and thereby enabling the warehouse workers to continue to do other work while this process runs in the background. Deferred receiving processing is useful for warehouse processes where it is not the same warehouse worker making the inbound receiving following an immediately put-away process.

### Deferred receiving policy

Go to one of the above mobile device menu items and find the **Deferred receiving policy ID** field. From here you can assign or go to the policy settings **Warehouse management > Setup > Mobile device > Deferred receiving policies** controlling when a receiving flow will use the _deferred receiving_ processing and thereby store the recorded entries into the _Mixed license plate receiving_ entities instead of immediately processing the registration and add inventory on-hand.

### Deferred receiving async processing

The deferred async receiving processing will automatically be running as soon as the mobile device menu item process completes the receiving flow and thereby all the _Mixed license plate receiving_ data is available. You will be able to monitor the status of the process in the _Mixed license plate receiving_ page via the field _Mixed license plate receiving status_ which can have the following values:

- Building license plate
- Processing
- Error
- Received

In case of having a failing batch job (_Execute deferred receiving [License plate id]_) the related _Mixed license plate receiving status_ becomes equal to "Error" and you can view the reason by selecting the _Processing errors_ button and take the needed actions like for example updating a line quantity or deleting a line following a manual update to run the process again by selecting the _Complete license plate_ button.

> [!NOTE]
> Like the _Mixed license plate receiving_ mobile device activity code you can print license plate labels as part of the _deferred receiving_ process. You control at which point in time the labels should get generated and printed via the _Label printing on confirming receiving_ and the _Label printing on deferred receiving_ fields on the _Deferred receiving policies_ page.
>
> When printing a label before the work creation process (Label printing on confirming receiving), you will for example not be able to print details about the to-location for the license plate, because this data will not be found before the deferred receiving async processing has happened.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
