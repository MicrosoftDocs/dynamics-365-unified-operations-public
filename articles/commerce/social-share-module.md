---
title: Social share module
description: Learn about social share modules and how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/29/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Social share module

[!include [banner](includes/banner.md)]

This article covers social share modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

With social share modules, users can share e-commerce site page URLs on social media such as Facebook, Twitter, Pinterest, and LinkedIn. Users can also share site page URLs through email. To help users share product information, use social share modules on product details pages (PDPs).

Each social share module acts as a container for social share item modules. You can configure each social share item module to point to a specific social media site. The module supports integration with Facebook, Twitter, Pinterest, LinkedIn, and email. When a site user selects a social media symbol, the module launches an HTML iframe for the respective social media site. Within the iframe, the user can sign in and post the page content that they were viewing.

Each social media platform might track cookies, so this module requires site users to accept the cookie consent notification message. When users don't accept cookie consent, the module is hidden on the page. For more information, see [Cookie compliance](cookie-compliance.md).

The following illustration highlights an example of a social share module used on a product details page.

:::image type="content" source="./media/ecommerce-socialshare.png" alt-text="Screenshot of a social share module.":::

## Social share module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Caption                  | Text | This property specifies a caption for the module. |
| Orientation | **Horizontal** or **Vertical**  | This property defines the layout orientation for the social media items. |

## Social share item module properties
| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Social media              | **Facebook**, **Twitter**, **Pinterest**, **LinkedIn**, **Mail** | A drop-down menu with a list of social media platforms. |
| Icon |Image    | This image represents the respective social media platform. As a best practice, refer to the social media platform's SDK for the recommended image to use for each platform. |

## Add a social share module to a buy box module

To add a social share module to a buy box module, follow these steps:

1. In the Fabrikam site, select **Pages**, and then select the **DefaultPDP** page to open the product details page.
1. In the **Buybox (required)** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Social Share** module, and then select **OK**.
1. In the **Social Share** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **SocialShare** module, and then select **OK**.
1. In the properties pane of the **SocialShare** module, under **Orientation**, select **Horizontal**. Add a caption as needed.
1. In the **SocialShare** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **SocialShareItem** module, and then select **OK**.
1. In the properties pane of the **SocialShareItem** module, under **Social Media**, select **Facebook**.
1. In the properties pane of the **SocialShareItem** module, under **Icon**, select **+ Add an image**.
1. In the **Media Picker** dialog box, select the Facebook logo image, and then select **OK**. If no Facebook logo image is present, select **Upload new media item** to upload one.
1. Add and configure more **SocialShareItem** modules as needed.
1. Select **Save**, and then select **Preview** to preview the page. The page shows the social share module.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

[Module library overview](starter-kit-overview.md)

[Buy box module](add-buy-box.md)

[Cookie compliance](cookie-compliance.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
