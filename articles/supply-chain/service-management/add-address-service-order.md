---
title: Add an address to a service order   
description: This article describes how to add a customer address to a service order.
author: sorenva
ms.date: 06/15/2020
ms.topic: article
ms.search.form: SMAServiceOrderTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: sorenand
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Add an address to a service order

[!include [banner](../includes/banner.md)]

This article describes how to add a customer address to a service order. When you create a service order, the address information is transferred from the project that the service order is attached to. However, you can select an alternative location from addresses that are already entered in Microsoft Dynamics AX for customers, vendors, sites, warehouses, service orders, and projects.

You can also create a new address. By default, the new address is transferred to the project. However, you can specify that the new address is only relevant for this instance of the service. If you do, the new address is not transferred to the project.

## Create a customer address for a service order

To add an address to a service order, follow these steps:

1. Go to **Service management** \> **Service orders** \> **Service orders**.

1. Open the service order that you want to create an address for.

1. Open the **Header** tab.

1. Expand the **Address** FastTab, and then select **Add address** from the FastTab toolbar.

1. In the **New address** dialog, enter a unique name for the address and complete the remaining fields. 

    > [!WARNING]
    > If you enter the same name as an existing address, the information that you enter in the remaining fields will overwrite information for the existing address.

1. Select **OK** to copy the new address to your service order.

## Specify an alternative address on a service order

To add an alternative address to a service order, follow these steps:

1. Go to **Service management** \> **Service orders** \> **Service orders**.

1. Open the service order that you want to enter an alternative address for.

1. Open the **Header** tab.

1. Expand the **Address** FastTab, and then select **Other address** from the FastTab toolbar.

1. In the **Address selection** dialog, select **Service orders** from the drop-down list above the gried.

1. Select an address, and then select **OK** to copy it to your service order.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]