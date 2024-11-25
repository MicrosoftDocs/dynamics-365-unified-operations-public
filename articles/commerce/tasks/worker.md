---
title: Configure a worker
description: This article describes how to configure a worker as a sales representative who is eligible for commission on sales in Microsoft Dynamics 365 Commerce POS.
author: josaw1
ms.date: 08/02/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: anvenkat
ms.search.validFrom: 2016-06-30
ms.search.form: CommissionSalesGroup, CommissionSalesMember, DirPartyLookup, HcmWorker
ms.custom: 
  - bap-template
---
# Configure a worker

[!include [banner](../includes/banner.md)]

This article describes how to configure a worker as a sales representative who is eligible for commission on sales in Microsoft Dynamics 365 Commerce point of sale (POS). The following procedures use USRT company demo data.

## Create a commission sales group for a worker

> [!NOTE]
> - Workers can be assigned to one or more sales groups. In POS, you can choose any sales group that contains workers from the store's address book.
> - A sales group can contain more than one worker. Commissions can be split between workers based on how you define the commission share.

To create a commission sales group for a worker, follow these steps.

1. In Commerce headquarters, go to **Sales and marketing \> Commissions \> Sales groups**. 
2. Select **New**.
3. For **Group**, enter a value.
4. For **Name**, enter a value.
5. Select **Save**.
6. On the Action Pane, select **General**.
7. Select **Sales rep**. 
8. For **Name**, enter or select a value.
9. For **Commission share**, enter a number.
10. Select **Save**.
11. Close the page.

## Assign the workers default sales group

> [!NOTE]
> A worker can be assigned to a default sales group. The default sales group will be automatically added to sales lines in POS if the option is enabled in the functionality profile for the store.

To assign workers to a default sales group, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Employees \> Workers**.
2. In the list, find and select the desired record.
3. Select the link in the selected row.
4. Select the **Commerce** tab.  
5. Select **Edit**.
6. For **Default group**, enter or select a value.
7. Select **Save**.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
