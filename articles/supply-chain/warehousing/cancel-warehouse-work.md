---
title: Cancel warehouse work for exception handling
description: Learn about the cancel work functionality that lets warehouse supervisors handle blocked work witha n outline on warehouse work that can be canceled.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 10/15/2019
ms.custom:
ms.reviewer: kamaybac
ms.search.form: WHSTroubIeshootingSeIfService, WHSTroubleshootingSelfService
---

# Cancel warehouse work for exception handling

[!include [banner](../includes/banner.md)]

The cancel work functionality in Microsoft Dynamics 365 Supply Chain Management lets the admin user cancel specific warehouse work that is currently in progress, but that is blocked by the system or can't be completed because of exceptional circumstances. This functionality is an attractive and secure alternative to SQL corrective scripts that fix inconsistent data. However, whereas these scripts are typically requested from IT professionals, the cancel work functionality can be used by users in the company who have admin rights.

You can access the cancel work functionality at **Warehouse management** \> **Periodic tasks** \> **Clean up \> Cancel work**. In the **Cancel work** dialog box, specify the work ID of the work to cancel, and then select **OK**.

## Warehouse work that can be canceled

During warehouse picking operations, a worker might encounter situations where they have registered quantities as picked from a storage location to their user location, but then they can't register the put operation. Inconsistent warehouse data is often, but not always, the reason why work is blocked.

Unlike the regular cancel functionality that can be accessed by using the **Cancel** button on the work header, the cancel work functionality doesn't require that the last completed work line be a work line of the **put** type. In other words, for the cancel work functionality, cancellation logic can be run even if the item quantity on a work line is in a user location.

> [!NOTE]
> For work that must be canceled for operational reasons, warehouse users must continue to use the regular cancel functionality on the work page.

Only work of the **Sales**, **Transfer issue**, **Raw material picking**, or **Replenishment** type can be canceled by using the cancel work functionality. Cancellation logic won't be run for frozen raw material picking work or work that can be canceled by using the regular cancel functionality (see the preceding note).

To unblock the work, the system cancels any remaining work lines and fixes the warehouse data that is associated with the work ID that the user specified. Any regular warehouse-handling operations that involve the affected item quantity can then resume.

To put the affected item in a specific location after the work is canceled, the user must use an inventory movement or quantity adjustment operation on a mobile device.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]