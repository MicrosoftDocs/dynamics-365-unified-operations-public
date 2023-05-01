---
# required metadata

title: Delete service orders   
description: Delete service orders 
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


# Delete service orders

[!include [banner](../includes/banner.md)]

1. Go to **Service management** \> **Periodic** \> **Service orders** \> **Delete service orders**.
1. On the **Delete service orders** form, select **Select** to specify the criteria to select the service orders to be deleted, and then select **OK**.
1. Set **Show Infolog** to *Yes* to generate an Action center message that displays the deleted service orders.
1. Select **OK**.

> [!NOTE]
> If you do not specify any criteria to select the service orders, all service orders are deleted. However, when you exit the **Delete service orders** page, you will have the option to delete all service orders.
>
> Also, you can only delete service orders with a stage that lets you delete them.

## Additional resources

- [Service orders](service-orders.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]