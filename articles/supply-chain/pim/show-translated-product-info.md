---
title: Show translated product names and descriptions in the UI
description: This topic describes how to translate product names and descriptions and how to set up the UI to show product information in each user's preferred language
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: EcoResProductParameters, EcoResProductDetailsExtended, SysTranslationDetail, SysUserSetup
ms.topic: how-to
ms.date: 10/14/2022
ms.custom: bap-template
---


# Show translated product names and descriptions in the UI

For companies operating worldwide, in multiple countries or regions, it's important to enable each user to work with product information in their own language. Sales representatives communicating with customers by phone will see product names in their local language. Purchasers will be able to search for products in the language they speak. Shop floor workers will get product names and instructions in familiar terms. In each case, the information can be shown in a language other than the system language.

All Supply Chain Management users are able to choose which language they prefer to see for all user interface (UI) elements (such as field names, buttons, page names, and so on). The system also allows you to enter product names and details for each product for as many different languages as you need, and each printed document can be set up to show this product information in any selected language. However, the UI doesn't necessarily show translated product information to users working online, and will instead show product names and descriptions using the system language unless you configure your system to use translated product names and descriptions. This affects features such as the production floor execution interface and order line entry.

By entering product translations and enabling their use in the user interface (UI), each user will be able to see product data (names and descriptions) translated into their own preferred language while working online. For products where no name and/or description are available in the user's language, the system will instead show the system language.

## Turn this feature on or off for your system

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Product information management*
- **Feature name:** *(Preview) Display product info in user's language*

## Configure your system to show translated product information

Follow these steps to set the system to show translated product names and descriptions in the UI:

1. Go to **Product information management \> Setup \> Product information management parameters**.
1. Open the **General** tab.
1. In the **Product identification** section, set **Display product info in user's language** to one of the following values:
    - *Yes* – Show product names and descriptions in each user's preferred language when displayed in the UI. For products where the name and/or description aren't available in the user's language, the system language will be used instead.
    - *No* – Always show product names and descriptions in the system language when displayed in the UI, regardless of each user's preferred language setting. Translated product names and descriptions will still be used in printed documents.

## Enter translated product names and details

Follow these steps to enter translated names and descriptions for products:

1. Go to **Product information management \> Products \> Released products.**
1. Find and select the product you want to work with.
1. On the Action Pane, open the **Product** tab and select **Translations.**
1. The **Text translations** page opens.
1. On the Action Pane, select **Add** to open a drop-down dialog box, which lists available languages. Select the language you want to enter translations for.
1. Enter translations in the fields provided.
1. If you'd like to add translations for additional languages, switch to the new language using the **Language** drop-down list and then enter new translations as needed.

## Choose your preferred language

Follow these steps to choose your preferred language. This language will be used for all UI elements and may also be used for product names and descriptions (when specified and enabled, as described previously).

1. Open the **Settings** menu (gear icon) in the upper right corner and select **User options**.
1. Open the **Preferences** tab.
1. Expand the **Language and country/region** FastTab.
1. Set **Language** to your preferred language.
