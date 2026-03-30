---
title: Point of sale (POS) application and user language settings
description: Learn how to change language settings in the Microsoft Dynamics 365 Commerce Store Commerce app and Store Commerce for web.
author: josaw1
ms.date: 01/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.assetid: 0030940c-e0a5-4345-9511-8c3bd1f487ad
ms.search.form: HcmWorker, RetailStoreTable
ms.custom:
  - bap-template
---

# Point of sale (POS) application and user language settings

[!include [banner](includes/banner.md)]

This article describes how to change language settings in the Microsoft Dynamics 365 Commerce Store Commerce app and Store Commerce for web.

The Store Commerce app and Store Commerce for web support environments where language settings and translations can vary between the store and user settings. For example, the store could be located in a region where English is most common for their customers, but some workers prefer to use the application with French translations.

## Data language

Regardless of the user's settings, the Store Commerce app and Store Commerce for web always use the store's language settings to determine the translations used for data. This approach ensures that all users and customers have a consistent experience. Examples of data include:

- Products
- Attributes and values
- Category names
- Printed or emailed transaction receipts
- Payment method names
- Line display messages

The store's language also appears on the main POS sign-in screen, since the user isn't known before signing in. If a translation isn't available for the store's language, the POS reverts to the company's language.

### Configuring the store's language setting

Set the store's language from **All stores** on the **Store** page under **General &gt; Regional Settings &gt; Language**. Use the drop-down list to choose the language for each store.

## User interface language

The POS user's language setting determines the translations used in the application user interface. This setting includes all labels, menus, and lists that aren't considered data. One exception is the text that appears on POS button grids. The button grids don't support translations, so they always show the text as defined on the button. To support translated buttons, you need to copy and maintain separate button grids and assign them to the users as appropriate.

### Configuring the user's language setting

Set the POS user's language from **All workers** on the **Worker** page under **Retail and Commerce > Language**. Don't set it on the main **Profile** tab. POS doesn't use the language setting from the Profile tab. If you don't set the user's language or set it to a language without translations, POS uses the store's language.

| &nbsp;      | UI language                | Data language (products, receipt formats, line display, etc.) |
|-------------|----------------------------|---------------------------------------------------------------|
| **Company** | Default                    | Default                                                       |
| **Store**   | Overrides company          | Overrides company                                             |
| **User**    | Overrides store or company | Never                                                         |


[!INCLUDE[footer-include](../includes/footer-banner.md)]
