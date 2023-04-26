---
# required metadata

title: Cancel service orders  
description: You can cancel a service order or service order line from the service order itself, or you can cancel multiple service orders by running a periodic job.
author: sorenva
ms.date: 01/19/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SMAServiceOrderTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sorenand
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Cancel service orders

[!include [banner](../includes/banner.md)]

You can cancel a service order or service order line from the service order itself, or you can cancel multiple service orders by running a periodic job.

> [!NOTE]
> Service orders cannot be canceled if the stage of the service order does not allow cancellation, if the service order has item requirements, or if the service order has already been posted.

## Cancel a service order in the Service orders form

1. Go to **Service management \> Service orders \> Service orders**.
1. Select the service order.
1. On the Action Pane, select **Cancel order**.

## Cancel a service order line

1. Go to **Service management \> Service orders \> Service orders**.
1. Open the service order that contains the line you want to cancel.
1. Select the service order line that you want to cancel.
1. Select **Cancel order line** to change the status of the line to *Canceled*.

> [!TIP]
> To reverse the cancellation of a service order line and change the status back to *Created*, select **Revoke cancel**.

## Cancel multiple service orders

1. Go to **Service management \> Perform periodic tasks \> Service orders \> Cancel service orders**.
1. Select the **Select** button.
1. In the **Inquiry** form, in the **Criteria** column, select the service orders that you want to cancel.
1. Select **OK** to close the **Inquiry** form.
1. Set **Show Infolog** to *Yes* generate an Action center message that lists the canceled service orders.
1. Set **Revoke cancel** to *Yes* if you want to reverse the *Canceled* status of a service order.
1. Select **OK**.

The selected service orders are either canceled or their progress status of *Canceled* has been reversed to *In process*.

> [!NOTE]
> If you select the **Revoke cancel** check box, service orders with a progress status of *Canceled* are reversed and service orders with a progress status of *In process* are not canceled.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]