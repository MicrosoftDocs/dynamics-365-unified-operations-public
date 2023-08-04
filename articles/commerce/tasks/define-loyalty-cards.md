--- 
# required metadata 
 
title: Define loyalty cards
description: This article describes how to define loyalty cards in Microsoft Dynamics 365 Commerce.
author: chuzho
ms.date: 07/31/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.region: Global
ms.author: chuzho
ms.search.validFrom: 2023-06-25 

---

# Define loyalty cards

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article describes how to define loyalty cards in Microsoft Dynamics 365 Commerce.

A loyalty card entitles the card holder to participate in the loyalty programs that are assigned to the card. Loyalty cards can be issued anonymously, or they can be assigned to a specific customer. You can view the loyalty transactions for a specific card and a summary of loyalty points that have accumulated on the card. You can issue loyalty cards from any channel. You can also manually adjust loyalty cards to upgrade customers to a different tier, add loyalty points, and transfer a loyalty point balance from one card to another.

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

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
