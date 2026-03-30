---
title: Define loyalty schemes
description: Learn how to define loyalty schemes in Microsoft Dynamics 365 Commerce. 
author: jashanno
ms.date: 02/11/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2016-06-30
ms.custom: 
  - bap-template
---

# Define loyalty schemes

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to define loyalty schemes in Microsoft Dynamics 365 Commerce.

The following procedure walks through how to define a loyalty scheme. Loyalty schemes are reward earning and redeeming rules for a loyalty program. The procedure uses the USRT demo data company.

To define loyalty schemes, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce > Customers > Loyalty > Loyalty schemes**.
1. Select **New**.
1. In the **Scheme ID** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Name** field, select the drop-down button to open the lookup.
    * You can have multiple loyalty schemes for a loyalty program. Loyalty schemes can be for all channels or only a subset of channels.  
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Save**.
1. Select **Add line**.
1. In the **Activity type** field, select an option.
    - Select **Purchase products by amount** if you want customers to earn rewards based on how much they spend. Select **Purchase products by quantity** if you want customers to earn rewards based on how many products they buy. Select **Sales transaction count** if you want customers to earn rewards for each sales transaction, regardless of what or how much is purchased.  
    - Select a category. The category limits which products this earning rule applies to.  
    - If you want the earning rule to apply to all products, leave this field blank.  
1. In the **Activity amount/quantity** field, enter a number.
        - For activity type **Sales transaction count**, always use a value of `1.0`. For activity types of **Purchase by amount** or **Purchase by quantity**, any transaction that's less than the value you enter doesn't trigger the earning rule. For example, if the activity type is **Purchase by amount**, and you enter "10.00," then a sales transaction for "9.00" doesn't earn rewards for this earning rule.
1. In the **Activity currency** field, enter a value.
1. In the **Reward point ID** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Reward points** field, enter a number. Amount type reward points record earned amounts with decimals. For example, if the earning rule states one reward point earned for every one Canadian Dollar spent, and the customer spends 1.25 Canadian Dollars, the customer earns 1.25 reward points. Quantity type reward points record earned amounts in integers. Using the example where the earning rule states 1 reward point earned for every one Canadian Dollar spent, and the customer spends 1.25 Canadian Dollars, the customer earns 1.0 reward points.  
1. Select **Save**.
1. Select **Add line**. Redemption rules are used when the loyalty payment method is used.  
1. In the **Reward point ID** field, select the drop-down button to open the lookup. Only redeemable reward points are shown.  
1. In the list, select the link in the selected row.
1. In the **Reward points** field, enter a number.
1. In the **Redemption type** field, select an option.
        - Selecting **Payment by amount** causes the **Amount or quantity** field to be treated as a currency value. In this case, the number of reward points used per currency unit of payment is a fixed ratio. Selecting **Payment by quantity** causes the **Amount or quantity** field to be treated as a quantity value. In this case, the number of reward points used per item quantity is a fixed ratio, however, the amount in currency can vary if the price of items paid for by using loyalty reward points varies for the same quantity. A redemption type of **Loyalty points discount** is only valid when the 'Russia' Country/Region specific features configuration key is enabled, and the POS functionality profiles has an ISO code of 'RU'.    
    - Select a category. The category limits which products this redemption rule applies to.  
    - If you want the redemption rule to apply to all products, leave this field blank.  
1. In the **Amount or quantity** field, enter a number.
1. In the **Currency** field, enter a value.
1. Select **Save**.
1. Select **Add line**. Select one or more nodes from the **Available organization nodes** list and move them to the **Selected organization nodes** list by selecting the arrow between the two lists.  
1. Select **OK**.
1. Select **Save**. Anytime you change the channels for a loyalty scheme, you must run **Process loyalty schemes**. That way, the channels get updated loyalty schemes.  

[!INCLUDE [footer-include](../../includes/footer-banner.md)]
