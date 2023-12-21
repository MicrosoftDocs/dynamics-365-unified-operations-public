--- 
# required metadata 
 
title: Define a loyalty program with two loyalty tiers
description: This article describes how to set up a loyalty program with two loyalty tiers in Microsoft Dynamics 365 Commerce. 
author: jashanno
ms.date: 12/21/2023
ms.topic: article  
audience: Application User 
ms.reviewer: josaw
ms.search.region: Global
ms.author: chuzho
ms.search.validFrom: 2016-06-30 

---
# Define a loyalty program with two loyalty tiers

[!include [banner](../includes/banner.md)]

This article describes how to set up a loyalty program with two loyalty tiers in Microsoft Dynamics 365 Commerce.

## Set up a loyalty program with two loyalty tiers

The following procedure uses the USRT demo data company.

To set up a loyalty program with two loyalty tiers, follow these steps.

1. In Dynamics 365 Commerce headquarters, go to **Retail and Commerce \> Customers \> Loyalty \> Loyalty programs**.
1. Select **New**.
1. For **Name**, enter a name for the loyalty program.
1. For **Description**, enter a description for the loyalty program.
1. Select **Add line**.
1. For **Level**, enter a level number.
1. For **Tier**, enter a name for the loyalty tier.
1. For **Description**, enter a description for the loyalty tier.
1. Select **Date interval**, and then select a date interval code from the dropdown list.
    > [!NOTE]
    > The date interval should extend into the future. For example, if the date interval you select for gold tier is for a one-year period, any customer who qualifies for the gold tier can receive the rewards that are assigned to the gold tier for one year. If the customer requalifies for the gold tier while they are in the tier, the date that the tier expires is extended by another year from the date when they requalify.  
1. Select **Add line**.
1. For **Level**, enter a level number.
1. For **Tier**, enter a name for the loyalty tier.
1. For **Description**, enter a description for the loyalty tier.
1. Select **Date interval**, and then select a date interval code.
1. Select **Save**.
1. In the list, find and select the desired record. Tier rules define the minimum number of a reward point needed to be earned during a time period to qualify for the tier.  
1. On the **Tier rules** FastTab, select **New**.
    > [!NOTE]
    > You can have more than one tier rule per tier. For example, you can have three different criteria to earn a tier; by spending $500 in one month, by spending $1000 over one year, and by having 20 transactions in one year. To implement this scenario, you must create three tier rules. These three tier rules have an **OR** relationship, which means that when calculating a loyalty card tier, if any tier rule is met for the card, the loyalty card can be in the tier.
1. Select **Reward point**, and then select a non-redeemable loyalty reward point from the dropdown list.  
1. For **Minimum issued points**, enter a number. For the lowest level tier, if all customers qualify simply by participating in the program, enter "0".  
1. Select **Evaluation date interval**, and then select a date interval code from the dropdown list. This date interval should extend into the past. Only points earned during this date interval will be counted towards reaching the minimum issued points value.  
1. Select **Save**.
1. Select **New**.
1. Select **Reward point**, and then select a loyalty reward point from the dropdown list.
1. For **Minimum issued points**, enter a number.
1. Select **Evaluation date interval**, and then select a date interval code from the dropdown list. This date interval should extend into the past.  
1. Select **Save**.
1. Select **Price groups**, and then select a price group for the loyalty program from the dropdown list. If you want to give loyalty customers discounts, you must assign one or more price groups to the loyalty program and assign the price groups to discounts. It is a best practice to not mix price groups across different types of discounting entities. For example, don't use the same price group for a loyalty discount and a channel discount.  
1. On the **Program tiers** FastTab, select **Price groups**, and then select a price group for the loyalty tier from the dropdown list.
1. Select **Save**.
1. Close the page.
1. Select **Save**.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
