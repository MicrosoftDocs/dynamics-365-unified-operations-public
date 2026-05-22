---
title: Add recommendations to the transaction screen
description: Learn how to add a recommendations control to the transaction screen on a point of sale (POS) device using the screen layout designer in Microsoft Dynamics 365 Commerce.
author: bebeale
ms.date: 01/14/2026
ms.topic: how-to
ms.search.form: RetailStoreTable, RetailTillLayout
ms.reviewer: v-griffinc
ms.assetid: a4f9d315-9951-451c-8ee6-37f9b3b15ef0
ms.search.region: global
ms.author: asharchw
ms.custom: 
  - bap-template

---

# Add recommendations to the transaction screen

[!include [banner](includes/banner.md)]

This article describes how to add a recommendations control to the transaction screen on a point of sale (POS) device by using the screen layout designer in Microsoft Dynamics 365 Commerce. Learn more in [Add product recommendations on POS](product.md).

You can display product recommendations on your POS device when you use Commerce. To display product recommendations, add a control to the transaction screen by using the screen layout designer. 

## Open Layout designer

1. Go to **Retail and Commerce > Channel setup > POS setup > POS > Screen layouts**.
1. Use the Quick Filter to find the screen that you want to add the control to. For example, filter on the **Screen layout ID** field by entering "F2CP16:9M".
1. In the list, find and select the desired record. For example, select **Name: F2CP16:9M Screen Layout ID: F2CP16:9M**.
1. Select **Layout designer**.
1. Follow the prompts to launch the layout designer. When prompted for credentials, enter the same credentials that you used when you launched the Layout designer from **Screen layouts**.
1. When you sign in, a page similar to the one shown in the following image appears. The layout is different depending on the customizations that were made for your store.


    :::image type="content" source="./media/screenlayout-pic-1.png" alt-text="Screenshot of layout designer interface showing a point of sale transaction screen layout with customer information panel." lightbox="./media/screenlayout-pic-1.png":::

## Choose a display option

Two configuration options are available. Choose the option that works best for your store, and follow the remaining instructions to finish setting up the control. The two options are:

- Recommendations are always visible.
- A **Recommendations** tab appears in the grid on the right side of the screen.

### Make recommendations always visible

1. Reduce the height of the transaction lines details area so that it matches the height of the customer panel to its left.

    :::image type="content" source="./media/screenlayout-pic-2.png" alt-text="Screenshot of height of the transaction lines details area reduced." lightbox="./media/screenlayout-pic-2.png":::

1. From the menu on the left, drag and drop the recommendations control to the space between the transaction line details area and the button grid in the center bottom of the transaction screen. Resize the control so it fits in that space.

    :::image type="content" source="./media/screenlayout-pic-3.png" alt-text="Screenshot of recommendations control added to the layout." lightbox="./media/screenlayout-pic-3.png":::

1. Select the **X** to save and exit Layout designer.
1. In Commerce, go to **Retail and Commerce > Retail and Commerce IT > Distribution schedules**.
1. In the list, select **1090 Registers**.
1. Select **Run now**.

### Add a Recommendations tab to the button grid on the right side of the screen

1. Right-click the empty space below the last tab on the button grid located on the right side of the page.

1. Select **Customize**.

    :::image type="content" source="./media/pic-5.png" alt-text="Screenshot of Customization - Tab control dialog box." lightbox="./media/pic-5.png":::

1. Select **New tab**.
1. Find the new tab that you just added. You might need to scroll down.
1. In the **Contents** drop-down, select **Recommended products**.

    :::image type="content" source="./media/pic-6.png" alt-text="Screenshot of selecting Recommended products in the Contents field." lightbox="./media/pic-6.png":::

1. In the **Label** field, type a name for the recommendations tab. For example, enter "Recommended products."
1. In the **Image** field, select the image to appear on the tab.
1. Select **OK**. The new tab appears in the button grid.
1. Select the **X** to save and exit Layout designer.
1. In Commerce, go to **Retail and Commerce > Retail and Commerce IT > Distribution schedules**.
1. In the list, select **1090 Registers**.
1. Select **Run now**.

## Additional resources

[Product recommendations overview](product-recommendations.md)

[Enable Azure Data Lake Storage in a Dynamics 365 Commerce environment](enable-adls-environment.md)

[Enable product recommendations](enable-product-recommendations.md)

[Enable personalized recommendations](personalized-recommendations.md)

[Opt out of personalized recommendations](opt-out-personalization.md)

[Enable "shop similar looks" recommendations](shop-similar-looks.md)

[Add product recommendations on POS](product.md)

[Adjust AI-ML recommendations results](modify-product-recommendation-results.md)

[Manually create curated recommendations](create-editorial-recommendation-lists.md)

[Create recommendations with demo data](product-recommendations-demo-data.md)

[Product recommendations FAQ](faq-recommendations.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
