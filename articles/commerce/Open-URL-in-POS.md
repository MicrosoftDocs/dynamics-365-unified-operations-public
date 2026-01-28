---
title: Open URL in POS
description: Learn how to configure a button to open a URL in Microsoft Dynamics 365 Commerce point of sale (POS).
author: ShalabhjainMSFT
ms.date: 01/23/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2018-10-30
ms.custom: 
  - bap-template
---

# Open URL in POS

[!include [banner](includes/banner.md)]

This article describes how you can configure a button in Dynamics 365 Commerce point of sale (POS) to open a URL. This feature doesn't require a code customization, and someone in a nondeveloper role can configure it.

This feature allows configuration of a button in POS by using the button grid designer to open a URL. Currently, this feature is supported in the following configurations:

- Open in new window.
- Open within POS.

## Open in new window

This configuration defines whether to open the URL in a new window or within the app. When you configure the app to open a web URL within the app, the side navigation panel and top bar of POS are visible and available for user interaction. When you configure the app to open the URL in a new window, the URL opens in a new window on the Store Commerce app for Windows, and in a new browser tab in all other POS clients. To enable this feature, you must configure the URL by selecting the **Open in new window** option.

## Open within POS

Opening a web URL within POS is currently only supported for the Store Commerce app for Windows. On other clients, this capability is under development and planned for release in future updates. To enable this capability, you must configure the URL by not selecting the **Open in new window** option.

| Client                | Open in new window | Open within POS | Details                           |
|-----------------------|:--------------------:|:-----------------:|-----------------------------------|
| Store Commerce app for Windows | ✓\*  | ✓ | \* Opens in new Store Commerce app window. |
| Store Commerce for web         | ✓\*  | X | \* Opens in new browser tab.        |
| Store Commerce app for iOS     | ✓\*  | X | \* Opens in new browser tab.        |
| Store Commerce app for Android | ✓\*  | X | \* Opens in new browser tab.        |

## Before you begin

Before you begin, review how to configure [Screen layouts for the point of sale (POS)](pos-screen-layouts.md).

## Open URL in POS

To configure a URL to open in POS, follow these steps:

1. In headquarters, go to **Retail and Commerce > Channel Setup > POS Setup > POS > Screen Layouts**.
1. Select **Button Grids > Designer**.
1. Create a new button.
1. Select **Button** properties.
1. Select **Open URL** as the action.
1. Enter the URL that you want to use.
1. Configure whether to open the URL in a new window.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
