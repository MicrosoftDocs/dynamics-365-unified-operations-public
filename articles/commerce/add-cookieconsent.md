---
# required metadata

title: Cookie consent module 
description: This topic covers cookie consent module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 05/28/2020
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
ms.dyn365.ops.version: 
---

# Cookie consent module

[!include [banner](includes/banner.md)]

This topic covers cookie consent module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A cookie consent module is required to allow users to provide consent for any feature/module that tracks browser cookies. Per [Cookie compliance](cookie-compliance.md) its required for a site user to explicitly provide consent to these cookies. If user consent is not received modules that require the consent will not be rendered on the page. E.g. Checkout module, Social share module, Preferred store feature etc require cookie consent.

A cookie consent module is typically configured on the page Header fragment(author-header-module.md) so it can be enforced when the page loads.

![Example of a cookie consent module](./media/ecommerce_cookieconsent.PNG)

## Social share module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Caption                  | Caption text | The module can be provided with a caption for this module|
| Orientation |Horizontal or Vertical    | This defines the layout for the social media items, it can be Horizontal or Vertical |

## Social share item module properties
| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Social media              | Facebook, Twitter, Pinterest, Linkedin, Mail | A dropdown with a list of social media platforms to chose from|
| Icon |Image    | This will be the icon that will be shown for the respective social media. As a best practice, refer to the social media platform's SDK for the recommended icon for each platform |

## Add a social share module to a buy box module

The Social share module can be added to the buy box module within the **Social share slot**.  

1. In Fabrikam, open the the **DefaultPDP** page which is the product details page 
1. To the Buy box module, **Social share slot** add the **Social share module**. Set caption if needed. Set Orientation=Horizontal
1. To the **Social share** add a **Social share item** module.
1. On the **Social share item** module, select Social Media = Facebook. Set Icon to the Facebook icon.
1. Conitnue adding more **Social share item**s.
1. Select **Save**, and then select **Preview** to preview the page. The page will show the social share module.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Buy Box](add-buy-box.md)

[Cookie compliance](cookie-compliance.md)
