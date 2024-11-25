---
title: Open URL in POS
description: This article provides an overview of improvements made to product and customer search functionality in Microsoft Dynamics 365 Commerce.
author: ShalabhjainMSFT
ms.date: 07/23/2024
ms.topic: article
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2018-10-30
ms.custom: 
  - bap-template
---

# Open URL in POS

[!include [banner](includes/banner.md)]

This article describes how you can configure a button in Dynamics 365 Commerce point of sale (POS) to open a URL. This feature doesn't require a code customization, and is configurable by someone in a nondeveloper role. 

This feature allows configuration of a button in POS using the button grid designer to open a URL. Currently, this feature is supported in the following configurations:

- Open in new window.
- Open within POS.

## Open in new window

This configuration defines whether to open the URL in a new window or within the app. When configured to open a web URL within the app, the side navigation panel and top bar of POS are visible and available for user interaction. When configured to open in a new window, the URL opens in a new window on the Store Commerce app for Windows, and in a new browser tab in all other POS clients. To enable this feature, you must configure the URL with the **Open in new window** option selected.

## Open within POS

Opening a web URL within POS is currently only supported for the Store Commerce app for Windows. On other clients, this capability is under development and planned for release in future updates. To enable this capability, you must configure the URL with the **Open in new window** option not selected.

| Client                | Open in new window | Open within POS | Details                           |
|-----------------------|:--------------------:|:-----------------:|-----------------------------------|
| Store Commerce app for Windows | ✓\*  | ✓ | \* Opens in new Store Commerce app window. |
| Store Commerce for web         | ✓\*  | X | \* Opens in new browser tab.        |
| Store Commerce app for iOS     | ✓\*  | X | \* Opens in new browser tab.        |
| Store Commerce app for Android | ✓\*  | X | \* Opens in new browser tab.        |

## Before you begin

Before you begin, review how to configure [Screen layouts for the point of sale (POS)](pos-screen-layouts.md).

## Open URL in POS

To configure a URL to be opened in POS, perform the following steps.

1. In head office, go to **Retail and Commerce \> Channel Setup \> POS Setup \> POS \> Screen Layouts**.
2. Select **Button Grids \> Designer**.
3. Create a new button.
4. Select **Button** properties.
5. Select **Open URL** as the action.
6. Enter the URL that you want to use.
7. Configure whether to open the URL in a new window.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
