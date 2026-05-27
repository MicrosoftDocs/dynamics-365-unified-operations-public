---
title: End a production order
description: Learn how to end a production order, including a step-by-step process for ending production orders using the USMF demo data company.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 05/27/2026
ms.update-cycle: 1095-days
ms.custom:
  - bap-template
  - evergreen
---

# End a production order

[!include [banner](../../includes/banner.md)]

This procedure shows how to end a production order. It is the final procedure out of seven procedures that explain the production order lifecycle.

## End a production order

To end a production order, follow these steps:

1. Go to **Production control** \> **Production orders** \> **All production orders**.
1. Select a production order that has the status *Reported as finished*.  
1. On the Action Pane, select **Production order**.
1. Select **End**. On this page, you can confirm that you want to end the production order.  
1. Open the **General** tab.
1. In the **Date** field, enter a date.
1. In the **Scrap method** field, select *Allocation*. When you select the allocation method, costs from the scrapped materials are added to the finished goods.  
1. Select **OK**.

## Validate calculation results

To validate the calculation results after you end the production order, follow these steps:

1. On the Action Pane, select **Manage costs**.
1. Select **View cost comparison**. After you end the production order, you can compare the estimated cost price against the realized cost price to get an overview of the production variances.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
