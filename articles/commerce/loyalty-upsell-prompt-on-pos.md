---
title: Loyalty Upsell Prompt on POS
description: Learn how Loyalty Upsell Prompt feature is assists store associates in informing customers about their loyalty program status and tier qualifying points. 
author: ashishmsft
ms.date: 04/01/2025
ms.topic: how-to
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2025-04-20
ms.custom: 
  - bap-template
---


# Loyalty Upsell Prompt in Point of Sale 

## Overview
The Loyalty Upsell Prompt feature is designed to assist store associates in informing customers about their loyalty program status and tier qualifying points. This feature aims to enhance customer engagement and satisfaction, resulting in increased loyalty, repeat purchases, and overall sales.

## Challenge
Retailers are striving to win more customers and convert their user base into loyalty members. However, promoting loyalty programs effectively and ensuring customers are aware of the benefits poses significant challenges. This often leads to lower engagement and missed opportunities for customer retention. For instance, frequent shoppers might not realize they are close to reaching the next tier in a loyalty program, missing out on significant discounts or rewards.

## Solution: Loyalty Upsell Prompt for Store Associates in POS
The Loyalty Upsell Prompt will enable store associates to provide customers with information about their tier qualifying points and loyalty program status. By showing customers how close they are to reaching the next tier, retailers can motivate them to continue engaging with the brand to unlock new benefits, which can result in additional purchases and increased Average Order Value (AOV). This feature enhances customer engagement and satisfaction, leading to increased loyalty and repeat purchases, ultimately boosting sales and customer retention.

## End-to-End Experience

### Feature Management Flag
From the Feature Management workspace, enable “Retail Loyalty Upsell Prompt.” This feature is available starting from version 10.0.44 and will not be backported.

### Configure Settings of Loyalty Upsell Prompt
- Select your Loyalty program (e.g., Fabrikam Rewards).
- Select your Loyalty Tier (e.g., Gold).
- Select one of the Tier rules with Reward points of type “Amount” (e.g., Total Spent, Date Interval: PrevMonth, Min Tier qualifying points – 500).
- Define the threshold for the Loyalty Upsell Prompt to show up (e.g., Threshold of 100 for the Tier rule for Reward point “Total Spent” with Date interval as PrevMonth).

![Loyalty upsell prompt configuration in HQ](./media/HQ_Setup_Loyalty_Threshold.png)

### Loyalty upsell prompt via Transaction Screen on POS
If more than one loyalty card is associated with a customer, store associates are prompted to choose a “Loyalty Card.” Upon choosing a loyalty card:
- For selected card with only one loyalty program: Directly view loyalty card details and see a new bell icon next to the Loyalty program tier information if the customer’s tier qualifying points are within the threshold of the Loyalty Upsell Prompt.
- For selected card with multiple loyalty programs: If the Loyalty Upsell Prompt tier rule is chosen with defined thresholds, and if the user’s tier qualifying points are within those thresholds, then you will see a new bell icon for each program separately.
![Loyalty upsell prompt from Transaction page](./media/Multiple_LoyaltyPrograms_TransactionScreen_LoyaltyUpsellPromptFeature.png) 

| Customer   | Current loyalty tier | Tier qualifying points | Loyalty upsell prompt for next tier                                      |
|------------|----------------------|------------------------|--------------------------------------------------------------------------|
| Customer A | Silver               | 420 points             | 80 points away from Gold tier.                                           |
| Customer B | Silver               | 380 points             | No loyalty upsell prompt as they are more than 100 points away from Gold tier. |
> [!Note]
> If Tier qualifying points are beyond the threshold: No bell icon will be shown for members with TQP being beyond the configured threshold.
#### Example for Loyalty upsell prompt 

### Loyalty upsell prompt via Customer Details Page
To view Loyalty card details via Customer details page, same new Fluent UI controls as the transaction screen, except that the user chooses a “Loyalty card” before the new slider loads.
e.g., Loyalty card details from CDP with at least one or more loyalty program tier within the threshold of the next loyalty tier.
![Loyalty upsell prompt from Customer details page](./media/Multiple_LoyaltyPrograms_CustomerScreen_LoyaltyUpsellPromptFeature.png) 

> [!Note] 
> ## Requirement
> Only reward point types of “Amount” are allowed for the Loyalty Upsell Prompt experience.
> - If you attempt to select a Tier Rule with Loyalty reward points as “Total transactions,” you will see a warning in a yellow band at the top of the screen: “Only reward points of type ‘Amount’ are considered for the Loyalty Upsell Prompt.”
> 
> ## Constraints
> ### Immediate Effect of Tier Rule Switching
> When you switch the tier rule for loyalty prompt sell consideration, no CDX jobs are expected to be run, and it’s effective immediately. For example, when switching between permitted tier rules that have reward points of type “Amount,” you will see a notification to confirm the switch. Upon confirming the switch, the newly selected tier rule becomes effective immediately.
> 
> ### Loyalty Upsell Prompt Threshold Value
> The threshold value for the Loyalty Upsell Prompt consideration cannot be more than the minimum issued points for the tier rule. For example, if a user defines a loyalty upsell prompt threshold value of 600 for a selected tier rule with a minimum issued points (tier qualifying points - TQP) of 500, they will see a user warning: “Threshold should be less than the minimum issued points for the loyalty upsell prompt.”
