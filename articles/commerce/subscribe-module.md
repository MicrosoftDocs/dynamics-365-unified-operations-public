---
# required metadata

title: Subscribe module
description: This topic covers subscribe modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 06/30/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.8

---
# Subscribe module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers subscribe modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

Subscribe modules can be used on site pages to capture customer information for newsletters or promotions. 

The following example image shows a subscribe module on the footer of an Adventure Works site page.

![Example of a subscribe module on the footer of an Adventure Works site page](./media/Subscribe.PNG)

>[!IMPORTANT]
> - The subscribe module is available in the Commerce module library as of the Dynamics 365 Commerce version 10.0.20 release.
> - The subscribe module is showcased in the Adventure Works theme.
> - The subscribe module requires a data action extension to work with some marketing email providers to send newsletter or promotional emails after customer information is captured.

## Subscribe module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Heading        | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | A text heading for the subscribe module, for example "Subscribe to the newsletter" or "Sign up for 10% off." |
| Paragraph      | Paragraph text | The subscribe module supports paragraph text in rich text format that can provide additional details for the heading call-to-action. |

## Add subscribe module to a new page

To add a subscribe list module to a new page and set the required properties in Commerce site builder, follow these steps.

1. Go to **Templates**, and open your site's home page marketing template (or create a new one).
1. In the **Main** slot of the default page, select the ellipsis (...), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Subscribe** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. OGo to **Pages** and open the site home page (or create a new one using the marketing template).
1. In the **Main** slot of the default page, select the ellipsis button (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Subscribe** module, and then select **OK**.
1. In the property pane for subscribe module, add a heading (for example, "Subscribe").
1. In the property pane for subscribe module, add paragraph text, for example "Latest trends, styles, & promotions. Are you on the list? Subscribe and get the latest hot deals!".
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it. 

## Additional resources

[Module library overview](starter-kit-overview.md)

[Adventure Works theme](adventure-works-theme.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
