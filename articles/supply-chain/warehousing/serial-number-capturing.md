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

This article explains how to use the **Capture serial number** setting in the **Tracking dimension groups** form for items which use the warehouse management processes. Depending on the setting, even though the items have the serial number activated, the actual serial number value on the inventory transactions (on-hand inventory) will not be populated until later in the process.

> [!NOTE]
> Here are several articles describing a similar, but slightly different serial number setting for the **Active in sales process** case:
> - [Working with serialized items - Supply Chain Management | Dynamics 365 | Microsoft Learn](https://learn.microsoft.com/en-us/dynamics365/supply-chain/sales-marketing/register-serial-numbers-sales-process)
> - [Serial Number Tracking for Service and Warranty in Microsoft Dynamics AX R3 - Microsoft Dynamics 365 Blog](https://www.microsoft.com/en-us/dynamics-365/blog/no-audience/2014/07/02/serial-number-tracking-for-service-and-warranty-in-microsoft-dynamics-ax-r3/)
> - [Enable picking of sales serial number items with R3 warehouse management processes - Microsoft Dynamics 365 Blog](https://www.microsoft.com/en-us/dynamics-365/blog/business-leader/2015/12/06/enable-picking-of-sales-serial-number-items-with-r3-warehouse-management-processes)
> - [How to use Serial Sales picking with Warehouse Management processing in Dynamics AX 2012 - Microsoft Dynamics 365 Blog](https://www.microsoft.com/en-us/dynamics-365/blog/business-leader/2016/11/04/how-to-use-serial-sales-picking-with-warehouse-management-processing-in-dynamics-ax-2012)

## Capture serial number during picking

Your business process might require that you only need to know the exact serial number that is picked for a sales or a transfer order, for example, at the time when the picking is performed. To enable this setup, the **Tracking dimension group** needs to have the **Serial number** active and the **Capture serial number** set to *Picking*.

> [!NOTE]
> When the field is set to *Picking*, the fields **Blank receipt allowed** and **Blank issue allowed** are automatically selected and disabled for editing.

The behavior of the system in this case is such that when the on-hand inventory is added, the user will not be asked to enter the serial number. This is true for the various warehouse inbound processes, like the purchase order receiving on the warehouse mobile device, for example. Instead, the serial number must be specified during the picking process, for example, when completing the sales picking work on the warehouse mobile device. At this point, the serial number will be added to the inventory transactions (on-hand inventory).

## Capture serial number during packing

Your business process might require that you only need to know the exact serial number that is picked for a sales or a transfer order, for example, at the time when the packing is performed. To enable this setup, the **Tracking dimension group** needs to have the **Serial number** active and the **Capture serial number** set to *Packing*

> [!NOTE]
> When the field is set to *Packing*, the fields **Blank receipt allowed** and **Blank issue allowed** are automatically selected and disabled for editing.

The behavior of the system in this case is such that when the on-hand inventory is added, the user will not be asked to enter the serial number. This is true for the various warehouse inbound processes, like the purchase order receiving on the warehouse mobile device, for example. Instead, the serial number must be specified during the packing process, for example, when packing the items into containers in the **Pack** form. At this point, the serial number will be added to the inventory transactions (on-hand inventory).

## Do not capture the serial number

There is a third (the default) setting for the **Capture serial number** field, which is *None*. In that case, the user is not prompted to capture the serial number in the picking or packing process. Instead, the serial number must be captured during the receiving process even if **Blank receipt allowed** is enabled. This basically means that the serial number must be part of the inventory transactions (on-hand inventory) from the very beginning.

> [!NOTE]
> Depending on other settings, the user might not be asked to capture the serial number during the receiving process, if the serial number is generated in some other way. For example, if serial number auto-generation is enabled through the tracking number group.