---
# required metadata

title: Add a feature module to a page 
description: This topic covers feature modules and how to add them to site pages in Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Add a feature module to a page 

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers feature modules and how to add them to site pages in Dynamics 365 Commerce.

## Overview

A feature module is used for marketing products or promotions using a combination of image and text. For example, a retailer can add a feature module to a product details page to highlight the features of the product. 

The feature module is driven by CMS data and is a standalone module that does not depend on any other modules on the page. Feature modules can be placed on any site page where a retailer wants to market or promote something (products, sales, features, etc.).

## Examples of feature module uses in e-Commerce

A feature module can used on:

- A product details page to showcase product features.
- The home page to promote products.
- A category page to highlight a category of products.

## Feature module properties

|   Property name   | Values                                                       | Property description                                         |
| :---------------: | :----------------------------------------------------------- | :----------------------------------------------------------- |
|       Image       | Image file                                                   | The image that will be used for marketing the product or promotion. An image can be uploaded to the image gallery, or an existing image can be used. |
|      Heading      | Heading text<br /><br />Heading tag = H1, H2, H3, H4, H5, H6 | The heading text and heading tag. The default heading tag is H2 but can be changed to meet accessibility requirements. |
|     Paragraph     | Paragraph text                                               | Paragraph text in rich text format. Basic rich text functionality such as bold, underline, italics, and hyperlinks are supported. Some of this functionality may be overridden by the page theme applied to the module. |
|       Link        | Link text<br />Link url<br />Aria label<br />Open link in new tab | Feature modules support one or more "call to action" links. If a link is added, link text, an URL, and an ARIA label are required. ARIA labels should be descriptive for accessibility. Links can be configured to open in a new tab. |
|  Image placement  | Right<br />Left<br />Top<br />Bottom                         | Defines the position of the image relative to the text. For example, if Right is chosen, the image will appear on right of the text. |
| Image column size | Values from 1-12                                             | The size of the image relative to the text, in columns. There are 12 columns on a page. The image and text will have equal size (6 x 6) by default, but this can be adjusted as needed. |

## Add a feature module to a new page 

To add a feature module to a new page and set the required properties, do the following. 

1. Go to **Templates** and create a new page template named "feature template."

1. In the **Main** slot of the default page, add a feature module. 

1. Check in and publish the template. 

1. Create a new page named "feature page" with the feature template you created.

1. In the **Main** slot of the new page, click the ellipsis button (**...**) and select **Add Module**. The Add Module dialog box appears.

1. Under **Select Modules**, select a feature module and click **OK**.

1. Select the feature module in the outline tree. In the right-side properties pane, click **Add an image**. Select an existing image or upload a new asset to add. 

1. Click **Heading**. In the Heading dialog box, add the heading text, select the heading level, then click **OK**.

1. Under **Rich Text**, add text as needed.

1. Click **Add Action Link**. In the Action Link dialog box, add link text, a link URL, and an ARIA label for the link, then click **OK**.

1. Save the page and preview the changes.

1. Check in and publish the page.
