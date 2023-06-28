--- 
# required metadata 
 
title: Define loyalty cards
description: This article describes how to define loyalty cards in Microsoft Dynamics 365 Commerce. 
author: chuzho
ms.date: 06/28/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: chuzho
ms.search.validFrom: 2023-06-25 

---

# Define loyalty cards

[!include [banner](../includes/banner.md)]

This article describes how to define loyalty cards in Microsoft Dynamics 365 Commerce.

A loyalty card entitles the card holder to participate in the loyalty programs that are assigned to the card. Loyalty cards can be issued anonymously, or they can be assigned to a specific customer. You can view the loyalty transactions for a specific card, and a summary of loyalty points that have accumulated on the card. You can issue loyalty cards from any channel. You can also manually adjust a loyalty card to upgrade the customer to a different tier, add loyalty points, or transfer the loyalty point balance from one card to another.

To define loyalty cards in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Customers \> Loyalty \> Loyalty cards**.
1. Select **New**.
1. For **Card type**,  select one of the following types from the drop-down menu:
    - **As card tender** - The default value indicating the card can only redeem reward points that are earned on itself.
    - **As contact tender** - The card can redeem reward points that are earned on any cards of the same customer.
    - **No tender** - The card can only earn reward points but not redeem.
    - **Blocked** - The card is blocked.
1. For **Customer name**, enter a name for the customer who will own this card (optional). 
1. In the **Loyalty program** table, select **Add line** to add a loyalty program associated with the card (optional).
1. Select **Save**.
1. Select **Card adjustments** to adjust points for this card.
1. Select **Card transactions** to view all earn, redeem, and adjust transactions that occurred for this card.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
