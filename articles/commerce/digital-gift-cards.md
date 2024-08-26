---
title: E-commerce digital gift cards
description: This article describes how digital gift cards work in the e-commerce implementation of Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 08/02/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# E-commerce digital gift cards

[!include [banner](includes/banner.md)]

This article describes how digital gift cards work in the e-commerce implementation of Microsoft Dynamics 365 Commerce. It also provides an overview of important configuration steps.

In Dynamics 365 Commerce, the purchase of digital gift cards follows the same flow as the purchase of other products in the system. No additional modules have to be configured. If multiple gift cards are added to the cart, the gift card items aren't aggregated on a single sales line. This behavior is required because each sales line is invoiced by using a separate gift card number.

The purchase of digital gift cards is supported in the Dynamics 365 Commerce 10.0.16 release and later.

The following illustration shows an example of the product details page (PDP) for a digital gift card on the Fabrikam e-commerce site.

![Example of a digital gift card PDP on the Fabrikam e-commerce site.](./media/GiftcardPDP.PNG)

## Turn on the digital gift card feature in Commerce headquarters

For the purchase flow for digital gift cards to work in Dynamics 365 Commerce, the **Purchasing gift card on e-Commerce feature** feature must be turned on in Commerce headquarters. You can find the feature in the **Feature management** workspace in Commerce headquarters, as shown in the following illustration.

![Feature management workspace in Commerce headquarters.](./media/Featureflag.PNG)

## Configure a digital gift card in Commerce headquarters

Digital gift card products should be configured in Commerce headquarters. The process resembles the process for other products. However, the following important steps are specific to the configuration of gift cards for purchase. For more information about how to create and configure products, see [Create a new product in Commerce](create-new-product-commerce.md).

- When you configure digital gift card products in the **New product** dialog box, set the **Product type** field to **Service**. (To open the dialog box, go to **Retail and commerce \> Products and categories \> Products by category**, and select **New**.) Products of the **Service** type aren't checked for available inventory before an order is placed. For more information, see [Create a new product](create-new-product-commerce.md#create-a-new-product).
- On the **Commerce parameters** page, on the **Posting** tab, the **Gift card product** field must be set to **Digital Gift Card**, as shown in the following illustration. If the product is an external gift card, see [Support for external gift cards](./dev-itpro/gift-card.md) for more information.

    ![Gift card product field in Commerce headquarters.](./media/PostGiftcard.png)

- If a gift card must support multiple predefined amounts (for example, $25, $50, and $100), the **Size** dimension should be used to set up those predefined amounts. Each predefined amount will be a product variant. For more information, see [Product dimensions](../supply-chain/pim/product-dimensions.md?toc=%2fdynamics365%2fretail%2ftoc.json).
- If customers must be able to specify a custom amount for a gift card in addition to predefined amounts, first set up a variant that allows for a custom amount. The **Size** attribute supports custom amount variants. Next, open the product from the **Released products in category** page, and then, on the **Commerce** FastTab, set the **Key in price** field to **Must key in new price**, as shown in the following example illustration. This setting ensures that customers can enter a price when they browse the product on a PDP.

    ![Key in price field in Commerce headquarters.](./media/KeyInPrice.png)
    
    The following example illustration shows a list of digital gift card product variants in Commerce headquarters, including two custom price variants.
    ![Digital gift card product variants with custom price variant example](./media/DigitalGiftCards_ProductVariantsWithCustom.png)

- The mode of delivery for a digital gift card must be set to **Electronic**. On the **Modes of delivery** page (**Retail and commerce \> Channel setup \> Modes of delivery**), select the **Electronic** mode of delivery in the list pane, and then add the digital gift card product to the grid on the **Products** FastTab, as shown in the following illustration. For more information, see [Set up modes of delivery](/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery).

    ![Digital gift card products on the Mode of delivery page in Commerce headquarters.](./media/ElectronicMode.PNG)
    
- Make sure that an online functionality profile has been created and associated with your online store in Commerce headquarters. In the functionality profile, set the **Aggregate products** option to **Yes**. This setting ensures that all items except gift cards are aggregated. For more information, see [Create an online functionality profile](online-functionality-profile.md).
- To ensure that customers receive an email after a gift card is invoiced, create a new email notification type on the **Email notification profiles** page, and set the **Email notification type** field to **Issue gift card**. For more information, see [Set up an email notification profile](email-notification-profiles.md).

## Add product images to the Commerce site builder Media library

You must add product images for digital gift card products to the Commerce site builder Media library. Make sure that the file names of the gift card image files follow your site's naming conventions for product images. For more information, see [Upload images](dam-upload-images.md).

## Configure a custom amount for a digital gift card in Commerce site builder

If a digital gift card is configured to allow for a custom amount, this behavior must also be enabled in the [buy box module](add-buy-box.md) that is used on your site's PDPs. The buy box module supports module configuration to allow for custom amounts. You can also define the minimum and maximum amounts that are allowed for custom amounts.

To configure a custom amount for a digital gift card in Commerce site builder, follow these steps.

1. Go to the buy box module that is used on your site's PDPs. This buy box module might be implemented in a fragment, in a template, or on a page.
1. Select **Edit**.
1. In the properties pane on the right, select the **Allow custom price** check box.
1. Optional: To define minimum and maximum amounts for custom amounts, enter amounts under **Minimum price** and **Maximum price**.
1. Select **Finish editing**, and then select **Publish**.

## Additional resources

[Buy box module](add-buy-box.md)

[Checkout module](add-checkout-module.md)

[Cart module](add-cart-module.md)

[Create a new product in Commerce](create-new-product-commerce.md)

[Set up modes of delivery](/dynamicsax-2012/appuser-itpro/set-up-modes-of-delivery)

[Product dimensions](../supply-chain/pim/product-dimensions.md?toc=%2fdynamics365%2fretail%2ftoc.json)

[Set up an email notification profile](email-notification-profiles.md)

[Create an online functionality profile](online-functionality-profile.md)

[Support for external gift cards](./dev-itpro/gift-card.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
