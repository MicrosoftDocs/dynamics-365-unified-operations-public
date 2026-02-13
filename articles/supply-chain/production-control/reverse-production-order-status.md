---
title: Reverse the production order status
description: Learn how to reverse production order status, including outlines on reversing statuses from Estimated to Created and from Scheduled to Estimated. 
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: ProdParmStatusDecrease, ProdSetupStatusDecrease
ms.topic: how-to
ms.date: 09/19/2025
ms.custom:
  - bap-template
---

# Reverse the production order status

[!include [banner](../includes/banner.md)]

This article describes how to reverse production order status.

If you reverse the status of a production order, the order and all operations that are associated with the routes revert to a previous step in the production life cycle. For example, a production order has a status of *Scheduled*, and you change the status back to *Created*. In this case, the system first changes the status to *Estimated*, which is the status that immediately precedes *Scheduled*. It can then change the status to the status that you want, *Created*.

If your order reaches the *Report as finished* status, you can still reverse it to an earlier status. However, you must rerun estimation and operations scheduling, job scheduling, or both types of scheduling, to update the information on the order. This step is required, because any reservations of remaining item consumption and operations resource consumption must also be reset.

This article explains what occurs when you reverse the status of a production order in the following ways:

- From *Estimated* to *Created*
- From *Scheduled* to *Estimated*
- From *Released* to *Scheduled*
- From *Started* to *Released*

## From Estimated to Created

When you reverse the status of a production order from *Estimated* to *Created*, the following events occur:

- The system removes the item consumption that it calculated for the items in the bill of materials (BOM). 
- The system deletes inventory transactions on the production line, and resets the **Remain status** field on the production order's BOM lines to *Ended*.
- If the **Derived purchases** and **Derived production** options are selected, the system deletes any underlying purchase orders or production orders.
- If you estimated the costs of the production order, or if you manually reserved items so that they could be used in production, the system removes those transactions.

## From Scheduled to Estimated

When you reverse the status of a production order from *Scheduled* to *Estimated*, the following events occur:

- The system removes the scheduled start and end dates and times.
- The system removes capacity reservations that were made during scheduling, and deletes jobs that were created during job scheduling. 
- The system resets all information that is recorded about operation scheduling and job scheduling on the **Production order details** page.

## From Released to Scheduled

When you reverse the status of a production order from *Released* to *Scheduled*, the only change is the value in the status field.

## From Started to Released

When you reverse the status of a production order from *Started* to *Released*, the following events occur:

- The system reverts all items that were reported as finished.
- If you picked material, or if you made inbound and outbound deliveries to production, the systems reverses those settings.
- The system changes the **Remain status** field on the production order's BOM lines from *Ended* to *Material consumption*.
- If you registered time, or if you reported quantities as finished for the operations in the production route, the system reverses those settings.
- The system changes the **Remain status** field from *Ended* to *Route consumption* in the production route.
- The system reverses the settings for all items that you posted as in process or work in process.
- On the **Production order details** page, the system resets fields that show a quantity that was started or reported as finished. The system also resets the dates for those transactions.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
