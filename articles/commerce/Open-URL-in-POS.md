---
title: Open URL in POS
description: This article provides an overview of improvements that have been made to product and customer search functionality in  Dynamics 365 Commerce.
author: ShalabhjainMSFT
ms.date: 01/30/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application user
ms.reviewer: josaw
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2018-10-30
ms.dyn365.ops.version: 8.1.1
ms.custom: 141393
ms.assetid: 
ms.search.industry: Retail
---

# Open URL in POS

[!include [banner](includes/banner.md)]

This article describes how you can configure a button in Dynamics 365 Commerce point of sale (POS) to open a URL. This feature does not require a code customization, and can be configured by someone in a non-developer role. 

This feature allows configuration of a button in POS, using the button grid designer to open a URL. Currently, this is supported in the following configurations:

- Open in new window.
- Open within POS.
- Open a native app.

## Open in new window

This configuration defines whether to open the URL in a new window or within the app. When configured to open a web URL within the app, the side navigation panel and top bar of POS are visible and available for user interaction. When configured to open in a new window, the URL will open in a new app window on the Store Commerce app for Windows, and in a new browser tab in all other POS clients. To enable this, you must configure the URL with the **Open in new window** option selected.

## Open within POS

Opening a web URL within POS is currently only supported for the Store Commerce app for Windows. On other clients, this capability is under development and planned for release in future updates. To enable this, you must configure the URL with the **Open in new window** option not selected.

## Open a native app

This feature also allows you to specify non-web URLs to open a native app. For example, you can specify URL protocols such as MailTo, SIP, IM, or MSTEAMS, which can then be handled by respective native apps on the host device. To enable this, you must configure the URL with the **Open in new window** option selected.

- For Windows computers, see [Export or Import Default Application Associations](/windows-hardware/manufacture/desktop/export-or-import-default-application-associations) to set the default protocol associations if you are setting up your computer using Deployment Image Servicing and Management (DISM).
- If you are using MDM, such as Intune to manage your Windows computers, see [Policy CSP - ApplicationDefaults](/windows/client-management/mdm/policy-csp-applicationdefaults).
- If you are a developer building a custom website, see [Launch the default app for a URI](/windows/uwp/launch-resume/launch-default-app).

## Open a native app seamlessly

Windows, iOS, and Android also allow opening of apps more seamlessly, based on app protocol association. If your app is not already configured to handle opening from a web browser, you may need a developer to configure this.

- For Windows, see [Enable apps for websites using app URI handlers](/windows/uwp/launch-resume/web-to-app-linking).
- For iOS, see [Universal Links for Developers](https://developer.apple.com/ios/universal-links/).
- For Android, see [Handling Android App Links](https://developer.android.com/training/app-links/).

| Client                | Open in new window | Open native app | Open within POS | Details                           |
|-----------------------|--------------------|-----------------|-----------------|-----------------------------------|
| Store Commerce app for Windows | ✓\*                | ✓               | ✓              | \* Opens in new Store Commerce app window |
| Store Commerce for web             | ✓\*                | ✓               | X              | \* Opens in new browser tab        |
| Store Commerce app for iOS     | ✓\*                | ✓               | X              | \* Opens in new browser tab        |
| Store Commerce app for Android | ✓\*                | ✓               | X              | \* Opens in new browser tab        |

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
