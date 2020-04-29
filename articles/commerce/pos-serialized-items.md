---
# required metadata

title: Work with serialized items in the POS
description: This topic explains how to manage serialized items in the point of sale (POS) application.
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

# Work with serialized items in the POS

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

Many retailers sell products that require serial control. These items are referred to as *serialized items*. Some retailers might want to maintain serial numbers for tracking purposes. Other retailers might want to capture serial numbers during the sales process, for service and warranty purposes. This topic explains how you can manage serialized items in the Microsoft Dynamics 365 Commerce point of sale (POS) application.

## Serial number configurations

An item is considered a serialized item if it's assigned a tracking dimension group that is set up to allow for serial numbers. In Commerce headquarters, on the **Tracking dimension groups** page, select the **Active** option to enable serial numbers for the inventory process. To enable serial numbers for the sales process, select the **Active in sales process** option.

On the **Tracking dimensions** FastTab, if the **Blank receipt allowed** option is turned on, the serial number is an optional input during the inventory receipt process. If the option is turned off, the serial number is required.

On the **Serial numbers** FastTab, if the **Serial number control** option is turned on, the serial number must be unique per unit. In other words, duplicated serial numbers aren't allowed.

## Serialized items in the receiving process

The **Inbound inventory** operation in the POS application lets users perform the following tasks for serialized items:

- Register serial numbers against serialized items when those items are received in the store via a purchase order.
- Validate preregistered serial numbers against serialized items when those items are received in the store via a purchase order or transfer order.

> [!NOTE]
> To use the **Inbound inventory** operation to register or validate a serialized item, the item must be assigned a tracking dimension group that is set up to allow for serial numbers for the **Active** option, not the **Active in sales process** option.

To begin the receiving process, in the **Inbound inventory** operation, you can start in the **Receiving now** view by scanning the item bar code or entering the item ID. Alternatively, you can start in the **Full order list** view by manually selecting the item.

If the item that is being selected or received is a serialized item, the **Details** pane for the item contains a **Manage serial number** link that opens the **Serial number management** page. Alternatively, you can open the **Serial number management** page either by selecting **Serial number** on the app bar of the order details view or by selecting **Manage serial number** in the dialog box that prompts you during the receiving process. The **Serial number management** page lists all open serial number lines that are pending registration or validation. There might be two tabs on this page: one for the current item and one for all the serialized items in the order.

The **Status** field on the **Serial number management** page provides information about the current stage that each serial number is in:

- **Not registered** – The serial number hasn't been provided, or the preregistered serial number hasn't yet been validated.
- **Registering** – The serial number has been registered and saved locally to the store's channel database, or the preregistered serial number has been validated. Only serial numbers that have a status of **Registering** will be submitted to Commerce headquarters when you finish receiving.

### Register serial numbers against serialized items

For a purchase order, a dialog box that prompts you during the receiving process of a serialized item offers the **Manage serial number** option. You can select that option to open the **Serial number management** page and start to register serial numbers. You can also skip this step during the receiving process and provide the input later, before the receipt is posted.

By default, the tab for the current item is shown. All serial number lines have an empty serial number value and a status of **Not registered**. You can scan serial number bar codes, or you can select **Serial number** on the app bar to continuously enter serial numbers in the dialog box. The serial numbers that you enter appear in the list, and the status of the serial number lines is changed to **Registering**. The maximum number of serial numbers that you can register in the list equals the receiving quantity. If you make a mistake, you can select **Edit** or **Clear** in the **Details** pane to make changes to the serial numbers that you entered.

You can also register serial numbers on the **All serialized items** tab of the **Serial number management** page. In the list, select the item that you want to register serial numbers against.

During serial number registration on this page, duplication validation occurs. If you try to enter a duplicated serial number against an item that serial number control is turned on for, you receive an error message and must provide a different number.

### Validate serial numbers on serialized items

For a transfer order, the outbound side must preregister serial numbers on the serialized items during the shipment process. For a purchase order, the supplier might provide serial number information through an Advance Shipment Notice (ASN), and you can preregister the numbers on the items that will be shipped. In both cases, the serial numbers are known before the receipt. Therefore, on the inbound side, you just have to validate that you received what you were supposed to receive.

To validate serial numbers, you can open the **Serial number management** page either during the receiving process or at any time before the receipt is posted. For each serialized item that has preregistered serial numbers, all the serial numbers are automatically set to an initial status of **Not registered** on this page. To validate serial numbers, you can scan or enter them. As serial number are entered, the application validates whether they match preregistered serial numbers. If they match, their status is changed to **Registering**. Otherwise, you receive an error message. The maximum number of serial numbers that you can validate in the list equals to the receiving quantity.

You can also validate serial numbers on the **All serialized items** tab of the **Serial number management** page. In the list, select the item that you want to validate serial numbers against.

## Additional resources

[Inbound inventory operation in POS](https://docs.microsoft.com/dynamics365/commerce/pos-inbound-inventory-operation)
