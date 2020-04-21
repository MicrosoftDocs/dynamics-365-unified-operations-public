---
# required metadata

title: Work with serialized items in POS
description: This topic explains how to manage serialized items in POS application.
author: boycezhu
manager: annbe
ms.date: 04/21/2020
ms.topic: article
ms.prod:
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: global
# ms.search.industry:
ms.author: boycezhu
ms.search.validFrom:
ms.dyn365.ops.version: 10.0.11
---

# Work with serialized items in POS
[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

Many retailers sell products that require serial control, or "serialized items." Some retailers may want to maintain serial numbers in for tracking purposes, others may want to capture serial numbers during the sales process for service and warranty. This topic explains how you can manage serialized items in the Commerce point of sale (POS) application.

## Serial number configurations

An item is considered a serialized item when it is assigned a tracking dimension group that is set up to enable a serial number. In Commerce headquarters, on the **Tracking dimension groups** page, you can enable serial numbers for the inventory process by selecting the **Active** option, or for the sales process by selecting the **Active in sales process** option. 

On the **Tracking dimensions** FastTab, if the **Blank receipt allowed** option is enabled, the serial number is an optional input during the inventory receipt process, otherwise it’s required. 

On the **Serial numbers** FastTab, if the **Serial number control** option is enabled, the serial number must be unique per unit. In other words, duplicated serial numbers are not allowed.

## Serialized items in the receiving process

The **Inbound inventory** operation in POS enables users to perform the following tasks on serialized items.

-	Register serial numbers against serialized items when receiving them into the store via a purchase order.

-	Validate serial numbers that have been preregistered to serialized items when receiving them into the store via a purchase order or transfer order.

To begin the receiving process, in the inbound operation, you can start with the **Receiving now** view by scanning the item bar code or entering the item ID, or you can start with the **Full order list** view by manually selecting the item.

If the item being selected or received is a serialized item, the **Details** pane for the item contains a "Manage serial number" link which opens the **Serial number management** page. The **Serial number management** page lists all open serial number lines that are pending registration or validation. There may be two tabs in this view--one for the current item, the other for all the serialized items in the order. Alternatively, you can click **Serial number** on the app bar of the order details view to open this page, or click "Manage serial number" on the prompt dialog during the receiving flow.

The **Status** field on the **Serial number management** page provides information about the current stage each serial number is in.

- **Not registered**: the serial number has not been provided or the preregistered serial number has not yet been validated.

- **Registering**: the serial number has been registered and saved locally to the store’s channel database, or the preregistered serial number has been validated. Only the serial numbers in the "Registering" status will be submitted to Commerce headquarters upon **Finish receiving**.

### Register serial numbers against serialized items

For purchase order, during the receiving process of a serialized item, you will be prompted with **Manage serial number** option. If you want, you can open the **Serial number management** form from there to start registering serial numbers. You could choose to skip it during the receiving flow and provide later prior to the posting of the receipt.

By default, the current item tab is shown. All serial number lines have empty serial number value and are in **Not registered** status. You can scan serial number bar codes or alternatively select **Serial number** on the app bar to continuously type in serial numbers in the prompt dialog. The entered serial numbers will be filled into the list with their status changed to **Registering**. The maximal number of serial numbers you can register in the list is equal to the receiving quantity. In case of mistake, you can select **Edit** or **Clear** on the **Details** pane to make changes to the entered serial numbers.

You can also register serial numbers on **All serialized items** tab of the form, for which you must firstly select an item in the list to indicate which item to register against.

Duplication validation occurs during serial number registration in this form. If you try to enter a duplicated serial number against an item that has **Serial number control** enabled, you will receive an error indicating this is not allowed and you have to provide a different number.

### Validate serial numbers on serialized items

For transfer order, during shipment process the outbound side is required to preregister serial numbers on the serialized items. For purchase order, the supplier might provide serial number information through Advance Shipment Notice (ASN) and you can preregister them on the items that will be shipped. In either case, the serial numbers are known prior to the receipt, therefore from inbound side, you are basically to validate you have received what are supposed to get.

To validate serial numbers, similarly you could launch the **Serial number management** form during receiving process or open it at any time prior to the posting of the receipt. For a given serialized item with preregistered serial numbers, this form has all those serial numbers auto populated with initial status as **Not registered**. You can scan or type in serial numbers to validate them. As serial number are entered, the application validates whether they match preregistered serial numbers. If yes, their statuses are changed to **Registering**. Otherwise, an error will be shown. The maximal number of serial numbers you can validate in the list is equal to the receving quantity.

You can also validate serial numbers on **All serialized items** tab of the form, for which you must firstly select an item in the list to indicate which item to validate against.

## Additional resources

[Inbound inventory operation in POS](https://docs.microsoft.com/dynamics365/commerce/pos-inbound-inventory-operation)
