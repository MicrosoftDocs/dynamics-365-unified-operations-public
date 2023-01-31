---
title: Show translated product names and descriptions in the UI
description: This article describes how to translate product names and descriptions, and how to set up the UI to show product information in each user's preferred language.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: EcoResProductParameters, EcoResProductDetailsExtended, SysTranslationDetail, SysUserSetup
ms.topic: how-to
ms.date: 10/14/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Show translated product names and descriptions in the UI

[!include [banner](../includes/banner.md)]

For companies that operate worldwide, in multiple countries or regions, it's important that each user be able to work with product information in their own language. Sales representatives who communicate with customers by telephone will then see product names in their local language. Purchasers will be able to search for products in the language that they speak. Shop floor workers will get product names and instructions in familiar terms. In each case, the information can be shown in a language other than the system language.

All users of Microsoft Dynamics 365 Supply Chain Management can select the language that they prefer to see for all user interface (UI) elements (such as field names, button labels, and page names). The system also lets you enter product names and details for each product in as many different languages as you require, and each printed document can be set up to show this product information in any selected language. However, the UI doesn't necessarily show translated product information to users who work online. Instead, it shows product names and descriptions in the system language, unless you configure your system to use translated product names and descriptions. This behavior affects features such as the production floor execution interface and order line entry.

By entering product translations and configuring the system to show them in the UI, you enable each user to see product data (names and descriptions) in their own preferred language while they work online. For products where no name or description is available in the user's preferred language, the system will show the name or description in the system language instead.

The following video provides an introduction to this feature.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE59tCd]

## Turn the feature on or off in your system

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Product information management*
- **Feature name:** *Display product info in user's language*

## Configure your system to show translated product information

Follow these steps to set up the system to show translated product names and descriptions in the UI.

1. Go to **Product information management \> Setup \> Product information management parameters**.
1. On the **General** tab, in the **Product identification** section, set the **Display product info in user's language** option to one of the following values:

    - *Yes* – Show product names and descriptions in each user's preferred language in the UI. For products where the name or description isn't available in the user's preferred language, the system language will be used instead.
    - *No* – Always show product names and descriptions in the system language in the UI, regardless of each user's preferred language setting. Translated product names and descriptions will still be used in printed documents.

## Enter translated product names and details

Follow these steps to enter translated names and descriptions for products.

1. Go to **Product information management \> Products \> Released products**.
1. Find and select the product that you want to work with.
1. On the Action Pane, on the **Product** tab, select **Translations**.
1. On the **Text translations** page, on the Action Pane, select **Add**.
1. In the drop-down dialog box, select the language that you want to enter translations for. Then enter translations in the fields that are provided.
1. To add translations for more languages, switch to each language by using the **Language** drop-down list, and then enter translations as required.

## Select your preferred language

Follow these steps to select your preferred language. This language will be used for all UI elements and might also be used for product names and descriptions (if they have been entered and enabled as described earlier in this article).

1. Select the **Settings** button (gear symbol) in the upper-right corner, and then select **User options** on the menu.
1. On the **Preferences** tab, on the **Language and country/region** FastTab, set the **Language** field to your preferred language.
