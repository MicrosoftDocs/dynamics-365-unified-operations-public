---
title: Define loyalty reward points
description: Learn how to define loyalty reward points in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/11/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2016-06-30
ms.search.form: RetailLoyaltyRewardPoints
ms.custom: 
  - bap-template
---
# Define loyalty reward points

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to define loyalty reward points in Microsoft Dynamics 365 Commerce.

The following procedure walks through defining loyalty reward points. Set up loyalty reward points before you set up a loyalty program. The procedure uses the USRT demo data company.

To define loyalty reward points, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce > Customers > Loyalty > Loyalty reward points**.
1. Select **New**.
1. In the **Reward point ID** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Reward point type** field, select an option. Select **Quantity** if you want the reward points to be rounded to the nearest integer. Select **Amount** if you want the reward points to be rounded according to currency rounding rules. If you select **Quantity**, skip the next step of this procedure.  
1. In the **Currency** field, enter a value. For **Amount** type reward points, all points issued have the selected currency. For **Quantity** type reward points, this field doesn't apply - skip this step.  
1. Check or uncheck the **Redeemable** checkbox.
1. In the **Redeem ranking** field, enter a number. Use redeem ranking when two or more redeemable reward points can be used to pay for products. If the two reward points have the same redeem ranking, then the one that needs to lower number of points is used.  
1. In the **Expiration time value** field, enter a number. The reward points expire the specified number of days, months, or years after when the points are issued. A value of "0" means the loyalty reward points never expire.  
1. In the **Expiration time unit** field, select an option.
1. Select **Save**.

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
