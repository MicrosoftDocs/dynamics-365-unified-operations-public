---
title: Serial number capturing
description: Learn about the serial number enabled items which use the warehouse management processes and how to capture the serial numbers.
author: ivanma
ms.author: ivanma
ms.topic: article
ms.date: 02/19/2025
ms.reviewer: kamaybac
ms.search.form: EcoResTrackingDimensionGroup
---

# Serial number capturing

This article explains how to use the **Capture serial number** setting in the **Tracking dimension groups** page for items which use the warehouse management processes. Depending on the setting, even if the items have the serial number activated, the actual serial number value on the inventory transactions (on-hand inventory) won't be populated until later in the process.

Here are several articles describing a similar, but slightly different serial number setting for the **Active in sales process** case:
- [Working with serialized items](../sales-marketing/register-serial-numbers-sales-process.md)
- [Serial Number Tracking for Service and Warranty in Microsoft Dynamics AX R3 - Microsoft Dynamics 365 Blog](https://www.microsoft.com/en-us/dynamics-365/blog/no-audience/2014/07/02/serial-number-tracking-for-service-and-warranty-in-microsoft-dynamics-ax-r3/)
- [Enable picking of sales serial number items with R3 warehouse management processes - Microsoft Dynamics 365 Blog](https://www.microsoft.com/en-us/dynamics-365/blog/business-leader/2015/12/06/enable-picking-of-sales-serial-number-items-with-r3-warehouse-management-processes)
- [How to use Serial Sales picking with Warehouse Management processing in Dynamics AX 2012 - Microsoft Dynamics 365 Blog](https://www.microsoft.com/en-us/dynamics-365/blog/business-leader/2016/11/04/how-to-use-serial-sales-picking-with-warehouse-management-processing-in-dynamics-ax-2012)

## Capture serial number during picking

Your business process might require knowing the exact serial number that's picked for a sales or a transfer order at the time of picking. To enable this setup, go to the **Tracking dimension group**, select **Serial number** and set the **Capture serial number** to **Picking**.

> [!NOTE]
> When the field is set to **Picking**, the **Blank receipt allowed** and **Blank issue allowed** fields are automatically selected and disabled for editing.

In the case when on-hand inventory is added, the user isn't asked to enter the serial number. This is true for the various warehouse inbound processes, like the purchase order receiving on the warehouse mobile device. Instead, the serial number is specified during the picking process, for example, when completing the sales picking work on the warehouse mobile device. At this point, the serial number is added to the inventory transactions (on-hand inventory).

## Capture serial number during packing

Your business process might require that need to know the exact serial number that's picked for a sales or a transfer order at the time when the packing is performed. To enable this setup, go to **Tracking dimension group**, select **Serial number** and set the **Capture serial number** to **Packing**.

> [!NOTE]
> When the field is set to **Packing**, the **Blank receipt allowed** and **Blank issue allowed** fields are automatically selected and disabled for editing.

In this case when the on-hand inventory is added, the user isn't asked to enter the serial number. This is true for the various warehouse inbound processes, like the purchase order receiving on the warehouse mobile device. Instead, the serial number is specified during the packing process, for example, when packing the items into containers in the **Pack** page. At this point, the serial number is added to the inventory transactions (on-hand inventory).

## Don't capture the serial number

The default setting for the **Capture serial number** field is **None**. In this case, the user isn't prompted to capture the serial number in the picking or packing process. Instead, the serial number is captured during the receiving process even if **Blank receipt allowed** is enabled. The serial number must be part of the inventory transactions (on-hand inventory) from the very beginning.

> [!NOTE]
> Depending on other settings, users might not be asked to capture the serial number during the receiving process if the serial number is generated in some other way. For example, if serial number auto-generation is enabled through the tracking number group.
