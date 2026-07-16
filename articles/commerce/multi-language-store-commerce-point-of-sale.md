---
title: Enable multilanguage support for Store Commerce self-checkout
description: Learn how to configure and use multilanguage features in Microsoft Dynamics 365 Commerce Store Commerce self-checkout, including localization of button grids and screen layout tabs.
author: anush6121
ms.author: anvenkat 
ms.topic: how-to
ms.date: 06/08/2026
ms.custom: 
  - bap-template
ms.reviewer: mirao
---

# Enable multilanguage support for Store Commerce self-checkout

[!include [banner](includes/banner.md)]

This article explains how to configure and use multilanguage features in Microsoft Dynamics 365 Commerce Store Commerce self-checkout that help you streamline checkout for both customers and store associates.

The 10.0.47 release of Store Commerce point of sale (POS) introduces enhanced multilanguage capabilities that allow retailers to offer a more accessible and globally consistent experience for customers. The new multilanguage capabilities include language selection on the self-checkout welcome screen and new options to localize POS screen layout button grids and tabs.

## Multilanguage self-checkout

The Commerce 10.0.47 release includes the following multilanguage self-checkout capabilities:

- **Feature flag control**: Language selection on the welcome screen is enabled through a configuration flag in the functionality profile, so retailers can control rollout and experience. 
- **Language selection on the welcome screen**: Customers can choose their preferred language directly from the self-checkout welcome screen, without staff assistance.
- **Configurable per store**: Administrators can select which languages are available for each store, ensuring the right options for every location. 
- **Consistent UI localization**: All labels, buttons, and tabs automatically resolve to the selected language during the transaction.
- **Session-based language reset**: After checkout, the language resets to the store or associate default, ensuring a fresh experience for each customer.
- **Scan from welcome screen**: Customers can begin scanning items immediately from the welcome screen, streamlining the checkout process.
- **New change language operation**:  You can add a change language option to the transaction grid to allow customers to switch languages during checkout.
- **Localize button grids and tabs**: Configure multiple languages for button labels and tab names directly in the layout designer.  
- **Single configuration, multilanguage support**: Design layouts once and reuse across all supported languages, avoiding duplicate layouts for each language.
- **Runtime resolution**: When a store associate signs in to POS, the layout automatically resolves to the language configured for their worker profile.
- **Consistent experience**: UI elements update instantly to reflect the selected language, ensuring clarity and usability.

:::image type="content" source="media/multi-language-self-check-out.jpg" alt-text="Screenshot of the welcome screen showing the Select language dialog." lightbox="media/multi-language-self-check-out.jpg":::

### Enable the feature flag

To enable the flag, follow these steps:

1. In Commerce headquarters, go to **Functionality profile** > **Self-Checkout**.
1. Turn on the **Enable language selection on Self-checkout Welcome page** feature flag.

### Enable more languages for a store

To enable extra languages for a store, follow these steps:

1. In Commerce headquarters, go to **Retail and Commerce** > **Stores** > **General** > **Regional settings**.
1. Under **Secondary languages**, add the extra languages.

### Localize a button grid

To localize a button grid, follow these steps:

1. In the POS button grid designer, select **Properties**.
1. In the **Configure button** dialog, select **Localization**.

    :::image type="content" source="media/button-grid-localization.jpg" alt-text="Screenshot of the button grid showing the Configure button dialog." lightbox="media/button-grid-localization.jpg":::

1. In the **Localization** dialog, for each language, select **Add row** to add the language and its corresponding text string.

    :::image type="content" source="media/button-grid-language-dialog.jpg" alt-text="Screenshot of the button grid showing the Localization dialog." lightbox="media/button-grid-language-dialog.jpg":::

1. Select **OK** to save your changes and exit.

### Localize a tab

To localize a tab, follow these steps:

1. In the POS layout designer, select **Custom control**.
1. In the **Customization - tab control** dialog, select **Localization**.

    :::image type="content" source="media/tab-localization.jpg" alt-text="Screenshot of the screen layout showing the Customization - Tab control dialog." lightbox="media/tab-localization.jpg":::

1. In the **Localization** dialog, add each language and its corresponding text string.
1. Select **OK** to save your changes and exit.

## Search language behavior

Text search, search suggestions, and returned product data resolve in a specific language depending on how you use the register.

| Register configuration | Search language used | Notes |
| ---------------------- | -------------------- | ----- |
| Cashier or attended POS | Store (channel) language | Applies even when the worker's language differs from the store's language. The worker's language changes only the user interface (labels and menus). Text search, search suggestions, and returned product data stay in the store language, consistent with the [data language](pos-application-user-language-settings.md#data-language) rule. |
| Self-checkout that uses **language selection** on the welcome screen or the **change language** operation | Language that the customer selects | When a customer selects a language in self-checkout, the search follows that language. You must index each selectable language for the store's cloud-powered search catalog. Otherwise, text search and search suggestions don't return any results. |

The store language and the worker language often differ. For example, a store might be set to Spanish (es-ES) while a worker uses the English (en-GB) user interface. On an attended register, this difference is expected - The associate sees the user interface in their own language, but search matches the store's indexed language so that results are consistent for every worker at that store.

> [!NOTE]
> If text search or search suggestions don't return any results in a multilingual store (where the store language differs from the worker language) on Store Commerce version 10.0.47 or 10.0.48, this behavior is a known issue that's resolved in version 10.0.49. If you're affected before you can update, contact Microsoft Support for a temporary mitigation.

## More resources

[Install the POS layout designer](install-pos-layout-designer.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
