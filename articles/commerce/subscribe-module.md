---
# required metadata

title: Subscribe module
description: This topic covers subscribe modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 06/25/2021
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
# Subscribe 

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers subscribe modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

Subscribe modules can be used on site pages to capture customer information for newsletters or promotions. 

The following example image shows a subscribe module on the footer of an Adventure Works site page.

![Example of a subscribe module on the footer of an Adventure Works site page](./media/Subscribe.PNG)

>[!IMPORTANT]
> - The subscribe module is available in the Commerce module library as of the Dynamics 365 Commerce version 10.0.20 release.
> - The subscribe module is included in the Adventure Works theme.


>[!IMPORTANT]
> The subscribe module requires a data action extension to work with some marketing email providers to send newsletter or promotional emails after customer information is captured.

## Subscribe module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Heading        | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | Heading can be “Subscribe to Newsletter”  or  “Sign-up for 10% off”. |
| Paragraph      | Paragraph text | The module supports paragraph text in rich text format. Paragraph can provide additional details on offer. |

## Add subscribe module to a new page

To add Active image module to a new page and set the required properties, follow these steps.
1. Go to **Templates**, and open **Marketing template** which is used for the home page (or create a new one)
1. In the **Main** slot of the default page, add Subscribe module.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Open the site Home page or create a new one using Marketing template.
1. In the **Main** slot of the default page, select the ellipsis button (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, under **Select Modules**, select the Subscribe, and then select **OK**.
1. In the property panel for Subscribe module, add a Heading say “Subscribe”
In the property panel for Subscribe module, add a Paragraph say “Latest trends, styles & promotions. Are you on the list? Subscribe and get the latest hot deals!”
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it. 

## Additional resources

[Module library overview](starter-kit-overview.md)

[Adventure works]()

[!INCLUDE[footer-include](../includes/footer-banner.md)]
