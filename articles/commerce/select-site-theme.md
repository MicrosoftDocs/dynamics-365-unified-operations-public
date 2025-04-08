---
title: Select a site theme
description: This article describes how to set or change your site's theme in Microsoft Dynamics 365 Commerce.
author: bicyclingfool
ms.date: 08/23/2024
ms.topic: how-to
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.custom: 
  - bap-template
---

# Select a site theme

[!include [banner](includes/banner.md)]

This article describes how to set or change your site's theme in Microsoft Dynamics 365 Commerce.

A site's layout and style (for example, fonts, sizes, and colors) are defined by the theme that you select and apply to the site. A theme is created and deployed by a developer at your company. For an overview of themes, see [Theming overview](e-commerce-extensibility/theming.md). For more information about how to create and deploy themes, see [Create a new theme](e-commerce-extensibility/create-theme.md).

By default, when you first create a site, it uses a theme that is named **Fabrikam**. This default theme is provided as part of the Commerce module library. After you've deployed additional themes for your site, you can configure the site so that it uses one of them instead.

## Select the site theme

To select the theme that is applied to your site, follow these steps.

1. In Commerce site builder, go to your site.
1. Go to **Site settings** \> **Extensions**.
1. On the **Configuration** tab, under **Theme**, select a theme on the drop-down menu.
1. To apply the selected theme to your site, select **Save and publish**.

> [!NOTE]
> The theme that you select is published to your site as soon as you select **Save and publish** on the **Extensions** page. To preview a theme on your site before you apply it, you can use your development or sandbox environment.

## Additional resources

[Add a logo](add-logo.md)

[Work with CSS override files](css-override-files.md)

[Add a favicon](add-favicon.md)

[Add a copyright notice](add-copyright-notice.md)

[Add languages to your site](add-languages-to-site.md)

[Add script code to site pages to support telemetry](add-telemetry.md)

[Theming overview](e-commerce-extensibility/theming.md)

[Create a new theme](e-commerce-extensibility/create-theme.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
