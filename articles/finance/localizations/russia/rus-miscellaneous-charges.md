---
title: Allocation of miscellaneous charges in proportion to weight and volume
description: Learn about allocating miscellaneous charges, including a process for allocating charges according to weight or volume of goods.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1
---

# Allocation of miscellaneous charges in proportion to weight and volume
[!include [banner](../../includes/banner.md)]

Miscellaneous charges can be allocated to the cost of goods, either works or services, that are purchased or sold. Russian localization has two additional methods to allocate charges:

- **According to the gross weight** – Charges are allocated equally, according to the gross weight of the items that are received. This amount is equal to the quantity in the inventory transaction multiplied by the **Gross weight** field from the inventory item card.
- **According to the volume** – Charges are allocated equally, according to the volume of the items that are received. This amount is equal to the quantity in the inventory transaction multiplied by the **Volume** field from the inventory item card.

## Allocate charges according to weight or volume of goods

1. Select **Accounts payable \> Purchase orders \> All purchase orders** or **Accounts receivable \> Orders \> All sales orders.**
2. Create a new order.
3. In the **Charges allocation** field, select one of the new allocation methods:

    - **Gross weight:** Allocate charges according to the gross weight.
    - **Volume:** Allocate charges according to the volume.

4. Specify other details and post the sales order as usual.

## Allocate charges according to weight and volume of goods during facture creation

1. Select **Accounts payable \> Purchase orders \> All purchase orders** or **Accounts receivable \> Orders \> All sales orders**.
2. Create a new order, and then select **Update facture**.
3. On the **Update facture** page, you can maintain the charges in one of two ways:

    - On the Action Pane, select the **Financials** tab **\> Maintain charges \> Maintain charges**. Charges created in this way will be allocated between all the order lines according to the allocation method.
    - On the **Lines** FastTab, select the line on which the charges will be allocated, and then select **Financials \> Maintain charges** to maintain miscellaneous charges on the line.

![Maintain miscellaneous charges on a line.](../media/1%20Update%20facture.png)

4. On the Action Pane, select the **Financials** tab **\> Maintain charges \> Allocate charges** to allocate charges.
5. On the **Allocate charges** page, in the **Charges allocation** field, select one of the new allocation methods: **Gross weight** or **Volume**.

![Allocate charges page.](../media/2%20Allocate%20charges.png)

6. Specify other details and post the facture as usual.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
