--- 
title: Create financial dimensions for retail channels and configure dimension values on stores
description: Learn how to create and configure financial dimensions for retail channels  in Microsoft Dynamics 365 Commerce.
author: jashanno
ms.date: 02/10/2026
ms.topic: how-to   
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2016-06-30 
ms.custom: 
  - bap-template
---
# Create financial dimensions for retail channels and configure dimension values on stores

[!include [banner](../includes/banner.md)]

This article explains how to create and configure financial dimensions for retail channels  in Microsoft Dynamics 365 Commerce.

The following procedure walks through creating a commerce channel financial dimension with dimension values and steps to configure financial dimension values on stores. This article doesn't include other related steps, such as creating dimension sets and account structures. This procedure uses the USRT company in demo data.

To create and configure financial dimensions for retail channels, follow these steps.

1. In Commerce headquarters, go to **General ledger** > **Chart of accounts** > **Dimensions** > **Financial dimensions**.
1. Select **New**.
1. In the **Use values from** field, select **Commerce channels**.
1. In the **Dimension name** field, enter a value.
1. Select **Activate**.
1. Select **Close**.
1. Select **Activate**.
1. Select **Dimension values**.
1. Close the page.
1. Select **Save**.
1. Close the page.
1. Go to **Retail and Commerce** > **Channels** > **Stores** > **All stores**.
1. In the list, select the link in the selected row.
1. Toggle the expansion of the **Financial dimensions** section.
1. Select **Edit**.
1. In the **Commerce channel** field, select the drop-down button to open the lookup.
1. In the list, find and select the dimension value for the store being updated.
1. In the list, select the link in the selected row.
1. In the **CostCenter** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Department** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Save**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
