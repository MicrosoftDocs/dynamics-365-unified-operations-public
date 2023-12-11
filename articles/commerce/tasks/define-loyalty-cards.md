--- 
# required metadata 
 
title: Define loyalty cards
description: This article describes how to define loyalty cards in Microsoft Dynamics 365 Commerce.
author: chuzho
ms.date: 07/31/2023
ms.topic: article
audience: Application User
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: chuzho
ms.search.validFrom: 2023-06-25 

---

# Define loyalty cards

[!include [banner](../includes/banner.md)]

This article describes how to define loyalty cards in Microsoft Dynamics 365 Commerce.

A loyalty card entitles the card holder to participate in the loyalty programs that are assigned to the card. Loyalty cards can be issued anonymously, or they can be assigned to a specific customer. You can view the loyalty transactions for a specific card and a summary of loyalty points that have accumulated on the card. You can issue loyalty cards from any channel. You can also manually adjust loyalty cards to upgrade customers to a different tier, add loyalty points, and transfer a loyalty point balance from one card to another.

## Setup loyalty card

To define loyalty cards in Commerce headquarters, follow these steps.

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

- The loyalty card tiers could be updated manually. In **Loyalty program** grid, select **Add line** to add a loyalty program that's associated with the card. You could specify loyalty program, loyalty tier, start date and end date. select **Remove line** to remove a loyalty program and tier. If you want to update an existing loyalty program and tier, you need remove it first and then add it back.

- The loyalty card tiers could also be updated automatically. When a earn, return earn or adjustment transaction happened in this loyalty card, all the loyalty card tiers will be recalculated automatically. You could also schedule the **Update loyalty card tiers** batch job to update loyalty tiers for all cards periodically.

- The **Active** tick is calculated automatically based on today's date. For each loyalty program, it will select effective and max tier as **Active**.

- Once a loyalty tier is granted for a loyalty card, the future loyalty tier calculation will only include loyalty points earned after the grant date. For example, a loyalty card is grant Diamond tier at 11/01/2023, valid from 11/01/2023 to 11/01/2024. Then the loyalty card makes another transaction at 11/10/2023, it will trigger the tier calculation again. In 11/10/2023 tier calculation, it will only includes points earned between 11/01/2023 and 11/10/2023, if the total points cannot meet Diamond tier value, this loyalty card's Diamond tier will keep the same. If the total points meet Diamond tier value again, then this loyalty card Diamond tier's valid from is still 11/01/2023 and valid to is changed to 11/10/2024, and the tier's grant date becomes 11/10/2024.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
