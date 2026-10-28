---
title: Serial number capturing
description: Learn about serial number-enabled items that use the warehouse management processes and how to capture the serial numbers.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 10/28/2026
ms.reviewer: kamaybac
ms.search.form: EcoResTrackingDimensionGroup
---

# Serial number capturing

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to use the **Capture serial number** field on the **Tracking dimension groups** page for items that use the warehouse management processes. Depending on the setting of this field, the actual serial number value on inventory transactions (on-hand inventory) isn't populated until later in the process, even if serial numbers are activated for the items.

The following articles describe a similar, but slightly different, serial number setting for cases where **Active in sales process** is enabled:

- [Working with serialized items](../sales-marketing/register-serial-numbers-sales-process.md)
- [Serial Number Tracking for Service and Warranty in Microsoft Dynamics AX R3 - Microsoft Dynamics 365 Blog](https://www.microsoft.com/dynamics-365/blog/no-audience/2014/07/02/serial-number-tracking-for-service-and-warranty-in-microsoft-dynamics-ax-r3/)
- [Enable picking of sales serial number items with R3 warehouse management processes - Microsoft Dynamics 365 Blog](https://www.microsoft.com/dynamics-365/blog/business-leader/2015/12/06/enable-picking-of-sales-serial-number-items-with-r3-warehouse-management-processes)
- [How to use Serial Sales picking with Warehouse Management processing in Dynamics AX 2012 - Microsoft Dynamics 365 Blog](https://www.microsoft.com/dynamics-365/blog/business-leader/2016/11/04/how-to-use-serial-sales-picking-with-warehouse-management-processing-in-dynamics-ax-2012)

## Capture the serial number during picking

Your business process might require that you know the exact serial number that you pick for a sales or transfer order at the time of picking. To enable this setup, go to the tracking dimension group, select **Serial number**, and set the **Capture serial number** field to *Picking*.

> [!NOTE]
> When you set the field to *Picking*, the **Blank receipt allowed** and **Blank issue allowed** fields are automatically selected, and you can't change the settings.

In this case, when you add on-hand inventory, the system doesn't prompt you to enter the serial number during warehouse inbound processes such as purchase order receiving on the warehouse mobile device. Instead, you specify the serial number during the picking process, such as when you complete sales picking work on the warehouse mobile device. At this point, the system adds the serial number to the inventory transactions (on-hand inventory).

## Capture the serial number during packing

Your business process might require that you know the exact serial number you pick for a sales or transfer order at the time of packing. To enable this setup, go to the tracking dimension group, select **Serial number**, and set the **Capture serial number** field to *Packing*.

> [!NOTE]
> When you set the field to *Packing*, the **Blank receipt allowed** and **Blank issue allowed** fields are automatically selected, and you can't change the settings.

In this case, when you add on-hand inventory, the system doesn't prompt you to enter the serial number during warehouse inbound processes such as purchase order receiving on the warehouse mobile device. Instead, you specify the serial number during the packing process, such as when you pack the items into containers on the **Pack** page. At this point, you add the serial number to the inventory transactions (on-hand inventory).

## Don't capture the serial number

The default setting for the **Capture serial number** field is *None*. In this case, the system doesn't prompt you to capture the serial number during either the picking process or the packing process. For items that use warehouse management processes, *None* means that you capture the serial number during registration, such as during the receiving process. It doesn't mean that serial number tracking is optional. The serial number must be part of the inventory transactions (on-hand inventory) from the beginning.

Don't use the **Blank receipt allowed** and **Blank issue allowed** settings to intentionally create on-hand inventory without serial numbers when **Capture serial number** is set to *None*. Although this combination is allowed, it isn't recommended for items that use warehouse management processes. Warehouse Management mobile app flows that process on-hand inventory, such as cycle counting, require values for active tracking dimensions and prompt the worker to enter a serial number. If your process must postpone serial number capture, set **Capture serial number** to *Picking* or *Packing*, as appropriate.

> [!NOTE]
> Depending on other settings, the system might not prompt you to capture the serial number during the receiving process if it's generated in some other way. For example, the system doesn't prompt you to capture the serial number if you enable automatic generation of serial numbers through the tracking number group.
