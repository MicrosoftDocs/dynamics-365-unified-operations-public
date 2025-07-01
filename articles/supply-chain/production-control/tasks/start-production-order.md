---
title: Start a production order
description: Learn how to start a production order on the shop floor, including a step-by-step process for starting production orders using the USMF demo data company.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: JmgRegistrationStartJob
ms.topic: how-to
ms.date: 06/17/2025
ms.custom: 
  - bap-template
---

# Start a production order

[!include [banner](../../includes/banner.md)]

This procedure shows how to start a production order on the shop floor. Time and material consumption are reported in this process. The demo data company used to create this procedure is USMF. This is the fifth procedure out of seven which explains the production order lifecycle.

## Start a production order

1. Go to **Production control** \> **Production orders** \> **All production orders**.
1. Select a production order that has the *Released* status.
1. On the Action Pane, select **Production order**.
1. Select **Start**. On this page, you can confirm the start of the production order.  
1. Select the **General** tab.
1. In the **From Oper. No.** field, enter *10*.
1. In the **Automatic route consumption** field, select *Always*.
1. Select the **Post route card now** checkbox.
1. In the **Automatic BOM consumption** field, select *Always*.
1. Select the **Post picking list now** checkbox.
1. Select the **Print picking list** checkbox.
1. Select **OK**. This is the printed picking list that shows the materials used for the production order.  
1. Close the page.

## Validate the picking list

1. On the Action Pane, select **View**.
2. Select **Picking list**.
3. In the list, find and select the desired record.
4. In the list, select the link in the selected row.
5. Select **Edit**.
6. In the **Consumption** field, enter a number.
7. Select **Post**.
8. Select **OK**. In the picking list journal, the materials consumed by the production order are posted. Before posting the journal, you can make adjustments if there's a difference between the estimated quantity and the actual consumed quantity.  
9. Select the **GridPanel** tab.
10. Close the page.

## Verify the route card journal

1. On the Action Pane, select **View**.
1. Select **Route card**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Edit**.
1. In the **Hours** field, enter a number.
1. Select **Post**.
1. Select **OK**.

In the route card journal, the time spent on the individual operations is recorded. Good and error quantity can also be reported.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
