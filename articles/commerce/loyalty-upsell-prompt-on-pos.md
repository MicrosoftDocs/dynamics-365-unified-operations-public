---
title: Loyalty upsell prompt feature (preview)
description: Learn how the loyalty upsell prompt feature assists store associates in informing customers about their loyalty program status and tier qualifying points in Microsoft Dynamics 365 Commerce.
author: ashishmsft
ms.date: 04/25/2025
ms.topic: how-to
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2025-04-20
ms.custom: 
  - bap-template
---

# Loyalty upsell prompt feature (preview)

[!INCLUDE [banner](includes/banner.md)]
[!INCLUDE [banner](includes/preview-banner.md)]

This article explains how the loyalty upsell prompt feature assists store associates in informing customers about their loyalty program status and tier qualifying points in Microsoft Dynamics 365 Commerce.

The loyalty upsell prompt feature is designed to assist store associates in informing customers about their loyalty program status and tier qualifying points. This feature aims to enhance customer engagement and satisfaction, resulting in increased loyalty, repeat purchases, and overall sales.

Retailers are striving to win more customers and convert their user base into loyalty members. However, effectively promoting loyalty programs and ensuring customers are aware of the benefits pose significant challenges that often lead to lower engagement and missed opportunities for customer retention. For example, frequent shoppers might not realize they are close to reaching the next tier in a loyalty program, thereby missing out on significant discounts or rewards.

The loyalty upsell prompt feature enables store associates to provide customers with information about their tier qualifying points and loyalty program status. By showing customers how close they are to reaching the next tier, retailers can motivate them to continue engaging with the brand to unlock new benefits, which can result in additional purchases and increased Average Order Value (AOV). The loyalty upsell prompt feature enhances customer engagement and satisfaction, leading to increased loyalty and repeat purchases and ultimately boosting sales and customer retention.

## Enable the loyalty upsell prompt feature

> [!NOTE]
> Tthe loyalty upsell prompt feature is available starting with Commerce version 10.0.44 and won't be backported.

To enable the loyalty upsell prompt feature, follow these steps.

1. In headquarters, go to **Systems administration \> Workspaces \> Feature management**.
1. Search for the **Retail Loyalty Upsell Prompt** feature, and then select it.
1. In the right pane, select Enable now.

## Configure the loyalty upsell prompt

To configure the loyalty upsell prompt feature, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Customers \> Loyalty \> Loyalty programs**.
1. In the left pane, select your loyalty program. For example, select **Fabrikam Rewards**.
1. On the **Program tiers** FastTab, select your loyalty tier. For example, select **Gold**.
1. On the **Tier rules** FastTab, select one of the tier rules with reward points of type **Amount**. For example, **Reward point** = "Total Spent", **Evaluation Date Interval** = "PrevMonth", **Minimum issued points** = "500".
1. In the **Threshold** column, define the threshold for when the loyalty upsell prompt appears. For example, **Threshold** = "100".

![Loyalty upsell prompt configuration in HQ](./media/HQ_Setup_Loyalty_Threshold.png)

> [!NOTE] 
> - Only reward point types of "Amount" are allowed for the loyalty upsell prompt experience.
> - If you attempt to select a tier rule with loyalty reward points as “Total transactions,” the following warning in a yellow band appears at the top of the screen: "Only reward points of type "Amount" are considered for the Loyalty Upsell Prompt."

## Loyalty upsell prompt via transaction screen on POS

If more than one loyalty card is associated with a customer, store associates are prompted to choose a loyalty card. Upon choosing a loyalty card:
- For a selected card with only one loyalty program: If the customer's tier qualifying points are within the threshold of the configured loyalty upsell prompt feature, a bell symbol appears next to the loyalty program tier information .
- For a selected card with multiple loyalty programs: For each loyalty program, if the loyalty upsell prompt tier rule is selected with defined thresholds, and if the user's tier qualifying points are within those thresholds, a bell symbol appears next to the loyalty program tier information.

> [!NOTE]
> If a customer's tier qualifying points are beyond the configured threshold, no bell symbol appears next to the loyalty program tier information in headquarters.

![Loyalty upsell prompt from Transaction page](./media/Multiple_LoyaltyPrograms_TransactionScreen_LoyaltyUpsellPromptFeature.png) 

### Examples of loyalty upsell prompts 

The following table shows examples of loyalty upsell prompts where the threshold is set to "100" and the Gold tier is 500 points.

| Customer   | Current loyalty tier | Tier qualifying points | Loyalty upsell prompt for next tier                                      |
|------------|----------------------|------------------------|--------------------------------------------------------------------------|
| Customer A | Silver               | 420 points             | "80 points away from Gold tier."                                           |
| Customer B | Silver               | 380 points             | (No loyalty upsell prompt appears as the customer is more than 100 points away from the Gold tier.) |

## Loyalty upsell prompt via the customer details page

To view Loyalty card details via Customer details page, same new Fluent UI controls as the transaction screen, except that the user chooses a “Loyalty card” before the new slider loads.
e.g., Loyalty card details from CDP with at least one or more loyalty program tier within the threshold of the next loyalty tier.

![Loyalty upsell prompt from Customer details page](./media/Multiple_LoyaltyPrograms_CustomerScreen_LoyaltyUpsellPromptFeature.png) 

## Constraints

### Immediate effect of tier rule switching

When you switch the tier rule for loyalty prompt sell consideration, if no Commerce Data Exchange (CDX) jobs are expected to be run the tier rule switch is effective immediately. For example, when you switch between permitted tier rules that have reward points of type "Amount", a notification appears asking you to confirm the switch. After you confirm the switch, the newly selected tier rule becomes effective immediately.
 
### Loyalty upsell prompt threshold value

The threshold value for the loyalty upsell prompt can't be more than the minimum issued points for the tier rule. For example, if a user defines a loyalty upsell prompt threshold value of "600" for a selected tier rule with a **Minimum issued points** value of "500", the following warning appears: "Threshold should be less than the minimum issued points for the loyalty upsell prompt."



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
