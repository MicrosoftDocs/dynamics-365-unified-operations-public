---
title: Enable Multi-language support for Self-checkout
description: Learn how to configure and use multi-language features in Store Commerce Self-Checkout including localization of button grids and screen layout tabs.
author: anush6121
ms.author: anvenkat 
ms.topic: how-to
ms.date: 01/08/2026
ms.custom: 
  - bap-template
ms.reviewer: 
---
### Multi-language Support in Store Commerce POS Self-Checkout & Button/Tab Localization ###

**Overview**

Store Commerce POS supports language selection at Self-Checkout and adds localization support for button grids and screen layout tabs.

**Multi-language Self-Checkout**

- **Language selection on the welcome screen** Shoppers can choose their preferred language directly from the Self-Checkout welcome screen, without staff assistance.
- **Configurable per store** Administrators can select which languages are available for each store, ensuring the right options for every location. To enable additional languages for a store , go to **Retail and Commerce ** -> Stores -> **General** -> **Regional settings** and list the additional languages in **Secondary languages**.
- **Consistent UI localization** All labels, buttons, and tabs automatically resolve to the selected language for the duration of the transaction.
- **Session-based language reset** After checkout, the language resets to the store or associate default, ensuring a fresh experience for each customer.
- **Scan from welcome screen** Customers can begin scanning items immediately from the welcome screen, streamlining the checkout process.
- **Feature flag control** Language selection on the welcome screen is enabled via a configuration flag in the functionality profile, allowing retailers to control rollout and experience. To enable the flag go to **Functionality profile**-> **Self-Checkout** and turn ON the flag **Enable language selection on Self-checkout Welcome page**.
- **New change language operation** can be added into the transaction grid for switching the language during checkout.

**Localization of Button labels and Screen layout tabs**

- **Localize button grids and tabs:** Configure multiple languages for button labels and tab names directly in the layout designer. To localize a button grid, open the button **propoerties** in the button grid designer and select **localization** and use the dialog to add languages with their corresponding text. Select **OK** to save and exit. To localize a tab, go to **Customize** option for a tab in the layout designer and select **localization** and use the dialog to add languages with their corresponding text. Select **OK** to save and exit. 
- **Single configuration, multi-language support:** Design layouts once and reuse across all supported languages—no need to duplicate layouts for each language.
- **Runtime resolution:** When a store associate logs into POS, the layout automatically resolves to the language configured for their worker profile.
- **Consistent experience:** UI elements update instantly to reflect the selected language, ensuring clarity and usability.


