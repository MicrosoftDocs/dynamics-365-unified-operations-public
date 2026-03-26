---
title: Create and update store hours
description: Learn how to create and update store hours in Microsoft Dynamics 365 Commerce headquarters.
author: josaw1
ms.date: 02/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-07-30
ms.custom: 
  - bap-template
---

# Create and update store hours

[!include [banner](../../includes/banner.md)]

This article explains how to create and update store hours in Microsoft Dynamics 365 Commerce headquarters.

From a single place, retailers can create, maintain, and manage the store hours for different stores across geographic regions. Retailers can then show the store hours on point of sale (POS) terminals. In this way, cashiers can share store hours with customers and better help shoppers who are interested in inventory in other stores. Retailers can also print the store hours on receipts, in case customers want to return to the store later.

You can configure multiple store hours across different channels. These channels include brick-and-mortar stores, call centers, mobile devices, and e-Commerce sites.

If a customer has a pickup order for a different store, the cashier can select dates when the pickup is available in that store. The store lookup provides a reference to the dates and store times. The cashier can select a date and location, and can also print a pickup receipt that includes the store hours.

This functionality is available in Microsoft Dynamics 365 Retail versions 8.1.2 and later.

## Configure store hours

To configure store hours, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** > **Channel Setup** > **Store hours**.
1. Select **New** to create a new store hours template. To use an existing template, select the template in the left pane.
1. In the **Add range** dialog box, define the date range, the store hours, and any holidays that are required.

    - If store hours don't change, select **Never ends** in the **End date** field.
    - If the store hours are for a specific month, week, or day, set the appropriate dates in the **Start Date** and **End date** fields.

    > [!NOTE]
    > You can create multiple templates that have overlapping start and end dates. Therefore, you can, for example, define store hours for stores in different time zones.

    :::image type="content" source="../dev-itpro/media/Storehours1.png" alt-text="Screenshot of the Add range dialog box.":::

1. Associate the store hours template with the stores where it's used. In the **Choose organization nodes** dialog box, select the stores, regions, and organizations that the template should be associated with.

    - Associate each store with only one store hours template.
    - Use the arrow buttons to select stores, regions, or organizations. The calendar is available to the stores or store groups, and it's visible at the POS for reference.

    :::image type="content" source="../dev-itpro/media/Storehours2.png" alt-text="Screenshot of the Choose organization nodes dialog box.":::

1. On the **Distribution schedule** page, run the **1070** and **1090** jobs to make the store hours available to the POS.

## Add store hours to printed receipts

To add store hours to the printed POS receipts, follow these steps:

1. Open the receipt designer.
1. Select **Footer** in the lower-left corner.
1. Drag the **Store hours** element from the left pane to the footer at the bottom of the receipt template.
1. Edit the default label on the **Store hours** element as needed.
1. Save the receipt, and close the receipt designer.
1. On the **Distribution schedule** page, run the **1070** and **1090** jobs.
1. Sign in to the POS.
1. Complete a sale, and select to print a receipt.

POS receipts now include the store hours. If any holidays were included in the template, they are shown on the receipt.

![Receipt example.](../dev-itpro/media/Storehours3.png "Receipt example")

:::image type="content" source="../dev-itpro/media/Storehours3.png" alt-text="Screenshot of the receipt example.":::

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
