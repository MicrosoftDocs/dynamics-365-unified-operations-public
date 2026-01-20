---
title: Enable multilanguage support for self-checkout (preview)
description: Learn how to configure and use multilanguage features in Microsoft Dynamics 365 Commerce Store Commerce self-checkout, including localization of button grids and screen layout tabs.
author: anush6121
ms.author: anvenkat 
ms.topic: how-to
ms.date: 01/26/2026
ms.custom: 
  - bap-template
ms.reviewer: 
---
# Enable multilanguage support for self-checkout (preview)

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article explains how to configure and use multilanguage features in Microsoft Dynamics 365 Commerce Store Commerce self-checkout that help you streamline checkout for both customers and store associates. including localization of button grids and screen layout tabs.

The 10.0.47 release of Store Commerce point of sale (POS) introduces enhanced multilanguage capabilities that allow retailers to offer a more accessible, and globally consistent experience for customers. The new multilanguage capabilities include language selection on the self-checkout welcome screen and new options to localize POS screen layout button grids and tabs.

## Multilanguage self-checkout

The Commerce 10.0.47 release includes the following multilanguage self-checkout capabilities:

- **Feature flag control**: Language selection on the welcome screen is enabled via a configuration flag in the functionality profile, allowing retailers to control rollout and experience. 
- **Language selection on the welcome screen**: Customers can choose their preferred language directly from the self-checkout welcome screen, without staff assistance.
- **Configurable per store**: Administrators can select which languages are available for each store, ensuring the right options for every location. 
- **Consistent UI localization**: All labels, buttons, and tabs automatically resolve to the selected language for the duration of the transaction.
- **Session-based language reset**: After checkout, the language resets to the store or associate default, ensuring a fresh experience for each customer.
- **Scan from welcome screen**: Customers can begin scanning items immediately from the welcome screen, streamlining the checkout process.
- **New change language operation**:  You can add a change language option to the transaction grid to allow customers to switch languages during checkout.
- **Localize button grids and tabs**: Configure multiple languages for button labels and tab names directly in the layout designer.  
- **Single configuration, multi-language support**: Design layouts once and reuse across all supported languages, avoiding duplicate layouts for each language.
- **Runtime resolution**: When a store associate logs into POS, the layout automatically resolves to the language configured for their worker profile.
- **Consistent experience**: UI elements update instantly to reflect the selected language, ensuring clarity and usability.

![Welcome screen showing Select language dialog.](media/multi-language-self-check-out.jpg)

### Enable the feature flag

To enable the flag, follow these steps:

1. In Commerce headquarters, go to **Functionality profile > Self-Checkout**.
1. Turn on **Enable language selection on Self-checkout Welcome page** feature flag.

### Enable additional languages for a store

To enable additional languages for a store, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce > Stores > General > Regional settings**.
1. Under **Secondary languages**, add the additional languages.

### Localize a button grid

To localize a button grid, follow these steps:

1. In the button grid designer, select **Properties**.
1. In the **Configure button** dialog, select **Localization**.

    ![Button grid showing Configure button dialog.](media/button-grid-localization.jpg)

1. In the **Localization** dialog, for each language, select **Add row** to add the language and its corresponding text string.

    ![Button grid showing Localization dialog.](media/button-grid-language-dialog.jpg)

1. Select **OK** to save and exit.

### Localize a tab

To localize a tab, follow these steps:

1. In the layout designer, select **Custom control**.
1. In the **Customization - tab control** dialog, select **Localization**.
1. In the **Localization** dialog, for each language, select **Add row** to add the language and its corresponding text string.
1. Select **OK** to save and exit.

![Screen layout showing Customization - Tab control dialog.](media/tab-localization.jpg)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
