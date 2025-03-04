---
title: Serial number capturing
description: Learn about serial number-enabled items that use the warehouse management processes and how to capture the serial numbers.
author: ivanma
ms.author: ivanma
ms.topic: article
ms.date: 02/19/2025
ms.reviewer: kamaybac
ms.search.form: EcoResTrackingDimensionGroup
---

# Serial number capturing

This article explains how to use the **Capture serial number** field on the **Tracking dimension groups** page for items that use the warehouse management processes. Depending on the setting of this field, the actual serial number value on inventory transactions (on-hand inventory) isn't populated until later in the process, even if serial numbers are activated for the items.

The following articles describe a similar, but slightly different, serial number setting for cases where **Active in sales process** is enabled:

- [Working with serialized items](../sales-marketing/register-serial-numbers-sales-process.md)
- [Serial Number Tracking for Service and Warranty in Microsoft Dynamics AX R3 - Microsoft Dynamics 365 Blog](https://www.microsoft.com/dynamics-365/blog/no-audience/2014/07/02/serial-number-tracking-for-service-and-warranty-in-microsoft-dynamics-ax-r3/)
- [Enable picking of sales serial number items with R3 warehouse management processes - Microsoft Dynamics 365 Blog](https://www.microsoft.com/dynamics-365/blog/business-leader/2015/12/06/enable-picking-of-sales-serial-number-items-with-r3-warehouse-management-processes)
- [How to use Serial Sales picking with Warehouse Management processing in Dynamics AX 2012 - Microsoft Dynamics 365 Blog](https://www.microsoft.com/dynamics-365/blog/business-leader/2016/11/04/how-to-use-serial-sales-picking-with-warehouse-management-processing-in-dynamics-ax-2012)

## Capture the serial number during picking

Your business process might require that the exact serial number that is picked for a sales or transfer order is known at the time of picking. To enable this setup, go to the tracking dimension group, select **Serial number**, and set the **Capture serial number** field to *Picking*.

> [!NOTE]
> When the field is set to *Picking*, the **Blank receipt allowed** and **Blank issue allowed** fields are automatically selected, and the settings can't be changed.

In this case, when on-hand inventory is added, the user isn't prompted to enter the serial number during warehouse inbound processes such as purchase order receiving on the warehouse mobile device. Instead, the user specifies the serial number during the picking process, such as when sales picking work is completed on the warehouse mobile device. At this point, the serial number is added to the inventory transactions (on-hand inventory).

## Capture the serial number during packing

Your business process might require that the exact serial number that is picked for a sales or transfer order is known at the time of packing. To enable this setup, go to the tracking dimension group, select **Serial number**, and set the **Capture serial number** field to *Packing*.

> [!NOTE]
> When the field is set to *Packing*, the **Blank receipt allowed** and **Blank issue allowed** fields are automatically selected, and the settings can't be changed.

In this case, when on-hand inventory is added, the user isn't prompted to enter the serial number during warehouse inbound processes such as purchase order receiving on the warehouse mobile device. Instead, the user specifies the serial number during the packing process, such as when the items are packed into containers on the **Pack** page. At this point, the serial number is added to the inventory transactions (on-hand inventory).

## Don't capture the serial number

The default setting for the **Capture serial number** field is *None*. In this case, the user isn't prompted to capture the serial number during either the picking process or the packing process. Instead, the serial number is captured during the receiving process, even if **Blank receipt allowed** is enabled. The serial number must be part of the inventory transactions (on-hand inventory) from the very beginning.

> [!NOTE]
> Depending on other settings, the user might not be prompted to capture the serial number during the receiving process if it was generated in some other way. For example, the user isn't prompted to capture the serial number if automatic generation of serial numbers is enabled through the tracking number group.
