---
title: Cancel warehouse work for exception handling
description: Learn how to cancel blocked warehouse work and allow inventory recovery from user locations.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 10/28/2026
ai-usage: ai-assisted
ms.custom:
ms.reviewer: kamaybac
ms.search.form: WHSTroubIeshootingSeIfService, WHSTroubleshootingSelfService
---

# Cancel warehouse work for exception handling

[!INCLUDE [banner](../includes/banner.md)]

The cancel work functionality in Microsoft Dynamics 365 Supply Chain Management lets administrators cancel warehouse work that's blocked or can't be completed because of exceptional circumstances. This exception-handling operation is also known as *hard cancel*. It provides an alternative to SQL corrective scripts for handling inconsistent warehouse data.

You can access the cancel work functionality at **Warehouse management** > **Periodic tasks** > **Clean up** > **Cancel work**. In the **Cancel work** dialog box, specify the work ID of the work to cancel, and then select **OK**.

## Warehouse work that you can cancel

During warehouse picking operations, a worker might encounter situations where they register quantities as picked from a storage location to their user location, but then they can't register the put operation. Inconsistent warehouse data often causes blocked work.

Unlike the regular cancel functionality that you can access by using the **Cancel** button on the work header, the cancel work functionality doesn't require that the last completed work line be a work line of the **put** type. In other words, for the cancel work functionality, cancellation logic can run even if the item quantity on a work line is in a user location.

> [!NOTE]
> For work that you must cancel for operational reasons, warehouse users must continue to use the regular cancel functionality on the work page.

Only work of the **Sales**, **Transfer issue**, **Raw material picking**, or **Replenishment** type can be canceled by using the cancel work functionality. Cancellation logic won't run for frozen raw material picking work or work that you can cancel by using the regular cancel functionality (see the preceding note).

To unblock the work, the system cancels any remaining work lines and fixes the warehouse data that's associated with the work ID that you specified. Any regular warehouse-handling operations that involve the affected item quantity can then resume.

## Recover inventory from a user location

Canceling work doesn't complete the physical put operation. After cancellation, check the affected item's on-hand inventory, user location, and license plate against its physical location. Use an inventory movement to move existing inventory to the appropriate storage location. Use a quantity adjustment only when you must correct the recorded quantity to match the physical inventory.

The **Allow adjusting inventory on User location** option on the **Worker** page allows recovery of available inventory from a user location. The system checks the option for the work user whose **User ID** matches that location. Changing the setting for another work user doesn't allow adjustments from the affected location. If a worker has multiple work user accounts, select the account that corresponds to the affected user location.

### Allow recovery for the affected work user

A system administrator should turn on this troubleshooting option only for the work users involved in the recovery. To configure it, follow these steps.

1. Go to **Warehouse management** > **Setup** > **Worker**.
1. On the Action Pane, select **Edit**.
1. If the **Allow adjusting inventory on User location** column isn't shown on the **Users** FastTab grid, open the **Grid options** menu on the right side of the grid header and select **Insert columns** to add it. Learn more in [Personalize the user experience](../../fin-ops-core/dev-itpro/get-started/personalize-user-experience.md#personalization-toolbar).
1. On the **Users** FastTab, find the row for the work user whose **User ID** matches the affected user location. For that row, select the **Allow adjusting inventory on User location** check box.
1. On the Action Pane, select **Save**.

> [!IMPORTANT]
> This option doesn't cancel work or move inventory by itself. It permits recovery from the selected user location; other inventory validations still apply. Don't turn it on for all workers as part of routine setup.

### Complete and verify the recovery

Coordinate with the warehouse worker before making corrections, so they don't continue processing the affected work during recovery.

1. Confirm that the blocked work is canceled and identify the inventory that remains in the user location.
1. Use an appropriate inventory movement or quantity adjustment operation on a mobile device to recover the affected inventory.
1. Verify that the on-hand quantity, location, and license plate match the physical inventory, and review the related inventory transactions.
1. Set **Allow adjusting inventory on User location** back to **No** for the affected work user when recovery is complete.

Don't use a quantity adjustment merely to remove a location balance when the goods still exist. Move the inventory instead, so the recorded total quantity remains consistent with the physical stock.

## Related information

- [Manage warehouse workers](manage-warehouse-workers.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
