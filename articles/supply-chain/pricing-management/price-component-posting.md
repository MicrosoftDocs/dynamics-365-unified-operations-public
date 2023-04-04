---
title: Price component posting
description: This article describes how to set up different sales order posting ledgers for each of several different price component codes.
author: sherry-zheng
ms.author: chuzheng
ms.reviewer: kamaybac
ms.search.form: GUPParameters, GUPPriceComponentCodePostingProfile, GUPPriceComponentCodeSetup, GUPPricingTree
ms.topic: how-to
ms.date: 04/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Price component posting

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Pricing management lets you set up a different sales order posting ledger for each of the following types of [price component codes](price-component-code.md):

- Base price
- Sales trade agreement price
- Margin component price adjustment
- Discounts

This capability enables the system to keep ledger accounts that distinguish between the many layers of your pricing composition at the price component level.

For more information about how to set up your pricing structures, including how to assign posting profiles for each relevant price component code in a structure, see [Arrange price component codes into a price structure](price-structure-details.md).

## Set up price component posting

Follow these steps to prepare your system to support price component posting.

1. Go to **Pricing management \> Setup \> Pricing management parameters**.
1. Open the **Posting** tab.

    [<img src="media/parameters-posting.png" alt="The Posting tab of the Pricing management parameters page." title="The Posting tab of the Pricing management parameters page" width="720" />](media/parameters-posting.png#lightbox)

1. Make the following settings on the **Sales base price** FastTab:
    - **Post sales base price** – Set to *Yes* to make it possible to post *base prices* and *sales agreement prices* to a specific ledger. When you post a sales invoice, the system will post using the ledger account specified by the posting profile assigned for each price component code line.
    - **Sales base price account** – Specify a fallback ledger account to use for sales base prices. This account will be used when needed for price component code lines where no posting profile is specified.
1. Make the following settings on the **Margin component adjustment** FastTab:
    - **Post margin component adjustments** – Set to *Yes* to make it possible to post *margin component price adjustment* to a specific ledger. When you post a sales invoice, the system will post using the account specified by the posting profile assigned for each price component code line.
    - **Margin component price adjustment account** – Specify a fallback ledger account to use for margin component price adjustments. This account will be used when needed for price component code lines where no posting profile is specified.
1. Make the following settings on the **Periodic discounts** FastTab:
    - **Post periodic discount** – Set to *Yes* to make it possible to post *discounts* to a specific ledger. When you post the sales invoice, the system will first check whether there is a specific discount account in the applied rule record and, if not, will instead post using the account specified by the posting profile assigned for each price component code line. Periodic discounts include mix and match discounts, quantity discounts, and discount offers.
    - **Ledger account type** – Set to *Periodic* to set up fallback ledger accounts using the other fields on this FastTab.
1. On the Action Pane, select **Save**.

## Configure price component posting profile

Follow these steps to set up your price component posting profiles.

1. Go to **Pricing management \> Setup \> Posting \> Pricing component posting**.

    [<img src="media/pricing-component-posting.png" alt="The Pricing component posting page." title="The Pricing component posting page" width="720" />](media/pricing-component-posting.png#lightbox)

1. Do one of the following steps:
    - To create a new profile, select **New** on the Action Pane.
    - To edit an existing profile, select it on the list pane.
    - To delete an existing profile, select it on the list pane and then select **Delete** on the Action Pane.

1. Make the following settings in the header of your new or selected record:

    - **Posting profile** - Enter a unique name.
    - **Description** - Enter a short description.
    - **Price component** – Select the price component type for which the posting profile will apply.

1. Use the **Lines** FastTab to set up the rules the profile will use to assign ledger accounts when posting price component codes of the selected **Price component** type. Use the toolbar buttons to add or remove lines as needed. Make the following settings for each line:
    - **Item code** – Select one of the following values to specify the scope of items where the line wil apply.
        - *Table* – Assign an account for a specific item.
        - *Group* – Assign an account for an item group.
        - *All* – Assign an account for all items.
    - **Item relation** – If you set the **Item code** field to *Table*, select a specific item. If you set the **Item code** field to *Group*, select an item group.
    - **Account code** – Select one of the following values to specify the scope of customer accounts where the line wil apply.
        - *Table* – Assign an account for a specific account.
        - *Group* – Assign an account for an account group.
        - *All* – AssAssign an account for all accounts.
    - **Account relation** – If you set the **Account code** field to *Table*, select a specific account. If you set the **Item code** field to *Group*, select an account group.
    - **Main account** – Select the account to use when the conditions established by the line are met.

1. Continue working until you have set up all of the lines you need for the current profile.
1. On the Action Pane, select **Save**.

## Associate price component posting to the price structure

Follow these steps to set up your pricing structures to use a specific posting profile for each relevant price component code.

1. Do one of the following steps:
    - For companies that use a single price structure, go to **Price management \> Setup \> Price component codes \> Price component code setup**. (See also [Set up company to use a single price structure](price-structure-single.md).)
    - For companies that use multiple price structures, go to **Price management \> Setup \> Price component codes \> Price trees**. Then select a price tree on the list pane. (See also [Set up company to use a multiple price structures](price-structure-multiple.md).)

1. Identify the price component code line that you want to assign posting for and select its **Post to price component code** check box. Then set **Posting profile** to the profile you want to use for that line.

    [<img src="media/price-component-posting-profile.png" alt="Assign a posting profile to a price component." title="Assign a posting profile to a price component" width="720" />](media/price-component-posting-profile.png#lightbox)

1. Continue working until you have assigned posting profiles for each relevant line.
1. On the Action Pane, select **Save**.
1. If you are using multiple pricing trees, then continue working to set up each tree.
