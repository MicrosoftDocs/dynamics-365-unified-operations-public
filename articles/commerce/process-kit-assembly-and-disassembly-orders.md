---
title: Process kit assembly and disassembly orders
description: This article describes the steps of processing kit assembly and disassembly orders.
author: tonyafehr
ms.date: 10/23/2023
ms.topic: article
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: wenxyang
ms.search.validFrom: 2023-10-23
---

# Process kit assembly and disassembly orders

[!include [banner](includes/banner.md)]

This topic describes how to process assembly and disassembly orders for retail product kits. After you generate assembly or disassembly orders for the different kit configurations and generate BOM journals to reserve the product inventory, the next step is to process the assembly and disassembly orders for the kit configurations.

## Process assembly orders

To process an assembly order, a warehouse worker must update the quantities for each kit configuration that is assembled. After the order is processed, post it to run the inventory process to update the status of the products from reserved to committed. Inventory for the product kit configurations is increased, and inventory for the individual products that are included in the kit configuration is decreased.

Use this procedure to process assembly orders.

1.  Click **Retail and Commerce \> Products and categories \> Kit orders**.

2.  In the **Kit orders** list, select a kit that has an order type of **Assembly order**.

3.  On the **Action Pane**, click **Assemble kit**.

4.  In the **Kit order** form, in the **Assembled** field, enter the number of kit configurations to assemble for each configuration.

5.  Click **Post** to post the assembly order and run the inventory process to update the status of the products.


    > [!NOTE]
    > <P>After the assembly order is posted, you can’t use it to assemble additional configurations. If you need to assemble additional kit configurations, you must create a new assembly order for the product kit.</P>



## Process disassembly orders

To process a disassembly order, a warehouse worker must update the quantities for each kit configuration that is disassembled. After the order is processed, post it to run the inventory process to update the status of the products from reserved to committed. Inventory for the product kit configurations is decreased, and inventory for the individual products that are included in the kit configuration is increased.

Use this procedure to process disassembly orders.

1.  Click **Retail and Commerce \> Products and categories \> Kit orders**.

2.  In the **Kit orders** list, select a kit that has an order type of **Disassembly order**.

3.  On the **Action Pane**, click **Disassemble kit**.

4.  In the **Kit order** form, in the **Disassembled** field, enter the number of kit configurations to disassemble for each configuration.

5.  Click **Post** to post the disassembly order and run the inventory process to update the status of the products.


    > [!NOTE]
    > <P>After the disassembly order is posted, you can’t use it to disassemble additional configurations. If you need to disassemble additional kit configurations, you must create a new disassembly order for the product kit.</P>



## See also

[Generate assembly and disassembly orders](generate-assembly-and-disassembly-orders.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
