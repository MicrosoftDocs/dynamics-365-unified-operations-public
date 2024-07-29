---
title: Add a copyright notice
description: This article describes how to add a copyright notice to your e-Commerce website.
author: josaw1
ms.date: 07/26/2024
ms.topic: how-to
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Add a copyright notice

[!include [banner](includes/banner.md)]

This article describes how to add a copyright notice to your e-Commerce website.

## Prerequisites

Before you can add a copyright notice to your site, you must have the following items:

- A template that includes a shared footer fragment.
- A page that uses that template.

## Add a copyright notice

To add a copyright notice to the bottom of every page that uses a specific template, follow these steps.

1. Go to **Fragments**, and then select **New**.
1. In the **New fragment** dialog box, select the **Footer** module, and name the fragment. For example, enter **Footer-Copyright**.
1. Select **OK**.
1. In the navigation pane, select the ellipsis button (**...**) next to **Footer**, and then select **Add Module**.
1. In the dialog box, select **Footer category**, and then select **OK**.
1. In the navigation pane, select the ellipsis button next to **Footer category**, and then select **Add Module**.
1. In the dialog box, select **Text block**, and then select **OK**.
1. In the navigation pane, select **Text block**.
1. In the properties pane on the right, in the **Paragraph** field, add your copyright message. For example, enter **(C) Fabrikam 2019**.
1. Select **Save**, select **Finish editing**, and then select **Publish**.
1. Go to **Templates**, select the template, and then select **Edit**.
1. Under **Page Outline**, expand **Body**, and then expand **Default Page**.
1. Select the ellipsis button next to **Footer Slot**, and then select **Add Fragment**.
1. Select the fragment that you created earlier, and then select **Select**.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it.

The footer that contains the copyright notice automatically appears at the bottom of all pages that use the selected template.

## Additional resources

[Add a logo](add-logo.md)

[Select a site theme](select-site-theme.md)

[Work with CSS override files](css-override-files.md)

[Add a favicon](add-favicon.md)

[Add languages to your site](add-languages-to-site.md)

[Add script code to site pages to support telemetry](add-telemetry.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
