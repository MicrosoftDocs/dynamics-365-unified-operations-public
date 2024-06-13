--- 
# required metadata 
 
title: Define loyalty cards
description: This article describes how to define loyalty cards in Microsoft Dynamics 365 Commerce.
author: chuzho
ms.date: 12/21/2023
ms.topic: article
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: chuzho
ms.search.validFrom: 2023-06-25 

---

# Define loyalty cards

[!include [banner](../includes/banner.md)]

This article describes how to define loyalty cards in Microsoft Dynamics 365 Commerce.

A loyalty card entitles the card holder to participate in the loyalty programs that are assigned to the card. Loyalty cards can be issued anonymously, or they can be assigned to a specific customer. You can view the loyalty transactions for a specific card and a summary of loyalty points that have accumulated on the card. You can issue loyalty cards from any channel. You can also manually adjust loyalty cards to upgrade customers to a different tier, add loyalty points, and transfer a loyalty point balance from one card to another.

## Set up loyalty cards

To set up loyalty cards in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Customers \> Loyalty \> Loyalty cards**.
1. Select **New**.
1. In the **Card type** field, select one of the following types:

    - **As card tender** – The default type. The card can redeem only reward points that it earns.
    - **As contact tender** – The card can redeem reward points that are earned by any card that's assigned to the same customer.
    - **No tender** – The card can only earn reward points. (In other words, it can't redeem reward points.)
    - **Blocked** – The card is blocked.

1. Optional: In the **Customer name** field, enter a name for the customer who is associated with the card.
1. Optional: In the **Loyalty program** grid, select **Add line** to add a loyalty program that's associated with the card.
1. Select **Save**.
1. To adjust points for the card, select **Card adjustments**.
1. To view all earn, redeem, and adjust transactions that have occurred for the card, select **Card transactions**.

## Update loyalty card tiers

To update loyalty card tiers manually, follow these steps. 

1. In the **Loyalty program** grid, select **Add line** to add a loyalty program that's associated with the card. You can specify loyalty program, loyalty tier, start date and end date. 
1. Select **Remove line** to remove a loyalty program and tier. If you want to update an existing loyalty program and tier, you must first remove it and then readd it.

You can also update loyalty card tiers automatically so that when an earn, return earn, or adjustment transaction happens for a loyalty card, all loyalty card tiers are recalculated automatically. You can schedule the **Update loyalty card tiers** batch job to update loyalty tiers for all cards periodically.

The **Active** checkmark is calculated automatically based on today's date. For each loyalty program, the system sets the effective and max tiers as **Active**.

Once a loyalty tier is granted for a loyalty card, the future loyalty tier calculation only includes loyalty points earned after the grant date. 

For example, if a loyalty card is granted a Diamond tier on 11/01/2023 that is valid from 11/01/2023 to 11/01/2024, and the loyalty card then makes another transaction on 11/10/2023, this triggers the tier calculation again. For the 11/10/2023 tier calculation, the system only includes points earned between 11/01/2023 and 11/10/2023. If the total points don't meet the Diamond tier value threshold, the loyalty card's Diamond tier date range remains the same. If the total points meet the Diamond tier value threshold again, then the loyalty card's Diamond tier grant date becomes 11/10/2024 and the Diamond tier is now valid until 11/10/2024.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
