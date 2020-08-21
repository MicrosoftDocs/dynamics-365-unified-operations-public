---
# required metadata

title: Social share module 
description: This topic covers social share modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 08/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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
ms.dyn365.ops.version: Release 10.0.14

---

# Social share module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers social share modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

Social share modules allow users to share e-Commerce site page URLs on social media such as Facebook, Twitter, Pinterest, and LinkedIn. Site page URLs can also be shared via email. Social share modules are commonly used on product details pages (PDPs) to help users share product information. This module was enabled as of Commerce release 10.0.13.

Each social share module is a container for social share item modules. Each social share item module can be configured to point to a specific social media site. Integration with Facebook, Twitter, Pinterest, Linkedin, and email is supported out of the box. When a site user interacts with a social media icon, an HTML iframe is launched for the respective social media site. Within the iframe, the user can sign in and post the page content that they were viewing.

Each social media platform may track some cookies, so this module requires site users to accept the cookie consent message. When cookie consent is not accepted, the module will be hidden on the page. For more information on cookie compliance, see [Cookie compliance](cookie-compliance.md).

The following illustration shows an example of a social share module used on a product details page.

![Example of a social share module](./media/ecommerce-socialshare.png)

## Social share module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Caption                  | Text | This property specifies a caption for the module. |
| Orientation | **Horizontal** or **Vertical**  | This property defines the layout orientation for the social media items. |

## Social share item module properties
| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Social media              | **Facebook**, **Twitter**, **Pinterest**, **LinkedIn**, **Mail** | A dropdown with a list of social media platforms to chose from|
| Icon |Image    | This will be the icon that will be shown for the respective social media. As a best practice, refer to the social media platform's SDK for the recommended icon for each platform |

## Add a social share module to a buy box module

The social share module can be added to the buy box module within the **Social share slot**.  

1. In Fabrikam, open the the **DefaultPDP** page which is the product details page 
1. To the Buy box module, **Social share slot** add the **Social share module**. Set caption if needed. Set Orientation=Horizontal
1. To the **Social share** add a **Social share item** module.
1. On the **Social share item** module, select Social Media = Facebook. Set Icon to the Facebook icon.
1. Conitnue adding more **Social share item**s.
1. Select **Save**, and then select **Preview** to preview the page. The page will show the social share module.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Buy box module](add-buy-box.md)

[Cookie compliance](cookie-compliance.md)
