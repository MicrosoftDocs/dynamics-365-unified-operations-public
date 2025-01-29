---
title: Cancel service orders  
description: You can cancel a service order or service order line from the service order itself, or you can cancel multiple service orders by running a periodic job.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SMAServiceOrderTable
ms.topic: how-to
ms.date: 01/06/2025
ms.custom: 
  - bap-template
---

# Cancel service orders

[!include [banner](../includes/banner.md)]

You can cancel a service order or service order line from the service order itself, or you can cancel multiple service orders by running a periodic job.

> [!NOTE]
> Service orders cannot be canceled if the stage of the service order does not allow cancellation, if the service order has item requirements, or if the service order has already been posted.

## Cancel a service order on the Service orders page

1. Go to **Service management \> Service orders \> Service orders**.
1. Select the service order.
1. On the Action Pane, open the **Service order** tab and select **Cancel order**.

## Cancel a service order line

1. Go to **Service management \> Service orders \> Service orders**.
1. Open the service order that contains the line you want to cancel.
1. On the **Lines** FastTab, select the service order line that you want to cancel.
1. On the **Lines** FastTab toolbar, select **Cancel order line** to change the status of the line to *Canceled*.

> [!TIP]
> To reverse the cancellation of a service order line and change the status back to *Created*, select **Revoke cancel** on the toolbar.

## Cancel or uncancel multiple service orders

1. Go to **Service management \> Perform periodic tasks \> Service orders \> Cancel service orders**.
1. Make the following settings on the Parameters FastTab:
    - **Show Infolog** – Set to *Yes* to generate an Action center message that lists the canceled or uncanceled service orders.
    - **Revoke cancel** – Set to *No* to cancel the selected service orders (already *Canceled* orders aren't affected). Set to *Yes* to uncancel the selected service orders (*In process* orders aren't affected).
1. Select **Filter**.
1. In the **Inquiry** dialog, on the **Range** tab, set the criteria to select the service orders that you want to cancel or uncancel.
1. Select **OK** to close the **Inquiry** dialog.
1. Select **OK**.

The selected service orders are either canceled or uncanceled. Uncanceled orders have their *Canceled* status reversed to *In process*.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
