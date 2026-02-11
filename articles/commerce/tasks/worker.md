---
title: Configure a worker
description: Learn how to configure a worker as a sales representative who is eligible for commission on sales in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/11/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: anvenkat
ms.search.validFrom: 2016-06-30
ms.search.form: CommissionSalesGroup, CommissionSalesMember, DirPartyLookup, HcmWorker
ms.custom: 
  - bap-template
---
# Configure a worker

[!include [banner](../includes/banner.md)]

This article explains how to configure a worker as a sales representative who's eligible for commission on sales in Microsoft Dynamics 365 Commerce point of sale (POS).

The following procedures use USRT company demo data.

## Create a commission sales group for a worker

> [!NOTE]
> - Workers can be assigned to one or more sales groups. In POS, you can choose any sales group that contains workers from the store's address book.
> > - A sales group can contain more than one worker. You can split commissions between workers based on how you define the commission share.

To create a commission sales group for a worker, follow these steps:

1. In Commerce headquarters, go to **Sales and marketing \> Commissions \> Sales groups**. 
1. Select **New**.
1. Enter a value for **Group**.
1. Enter a value for **Name**.
1. Select **Save**.
1. On the Action Pane, select **General**.
1. Select **Sales rep**. 
1. Enter or select a value for **Name**.
1. Enter a number for **Commission share**.
1. Select **Save**.
1. Close the page.

## Assign the worker's default sales group

> [!NOTE]
> Assign a worker to a default sales group. If you enable the option in the functionality profile for the store, the default sales group automatically adds to sales lines in POS.

To assign workers to a default sales group, follow these steps:

1. In headquarters, go to **Retail and Commerce \> Employees \> Workers**.
1. In the list, find and select the desired record.
1. Select the link in the selected row.
1. Select the **Commerce** tab.  
1. Select **Edit**.
1. For **Default group**, enter or select a value.
1. Select **Save**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
