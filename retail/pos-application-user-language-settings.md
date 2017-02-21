---
# required metadata

title: POS application and user language settings
description: This topic describes how to change language settings in Retail Modern POS (MPOS) and Cloud POS.
author: josaw1
manager: AnnBe
ms.date: 2016-04-07 15 - 08 - 29
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: HcmWorker, RetailStoreTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 41
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 78891
ms.assetid: 0030940c-e0a5-4345-9511-8c3bd1f487ad
ms.search.region: global
ms.search.industry: Retail
ms.author: jeffbl
ms.dyn365.ops.intro: 01-02-2016
ms.dyn365.ops.version: AX 7.0.0

---

# POS application and user language settings

This topic describes how to change language settings in Retail Modern POS (MPOS) and Cloud POS.

Overview
========

Retail Modern POS (MPOS) and Cloud POS support environments where language settings and translations can vary between the store and user settings. For example, the store could be located in a region where English is most common for their customers, but some workers prefer to use the application with French translations.

## Data language
Regardless of the user’s settings, MPOS and Cloud POS will always use the store's language settings to determine the translations used for data. This will ensure that all users and customers will have a consistent experience.  Examples of data include:

-   Products
-   Attributes and values
-   Category names
-   Printed or emailed transaction receipts
-   Payment method names
-   Line display messages

The store’s language will also be used for the main POS login screen, since the user is not known before logging in. If a translation is not available for the store’s language, the POS will revert to the company’s language.

### Configuring the store’s language setting

The store’s language setting is set from **All retail stores** on the **Retail Store** page under **General &gt; Regional Settings &gt; Language. **Use the drop down to choose the language for each store.

## User interface language
The POS user’s language setting determines the translations used in the application user interface. This includes all labels, menus, and lists that are not considered data. One exception is the text that is displayed on POS button grids. The button grids don't support translations, so they will always show the text as defined on the button. In order to support translated buttons, you'll have to copy and maintain separate button grids and assign them to the users as appropriate.

### Configuring the user’s language setting

The POS user’s language setting is set from **All workers** on the **Worker** page under **Retail &gt; Language**.  It is not set on the main Profile tab.  This setting is not used by POS. If the user’s language is not set or it is set to a language where translations are not available, the POS will revert to the store’s language.  

|             |                            |                                                                   |
|-------------|----------------------------|-------------------------------------------------------------------|
| ** **       | **UI language** ** **      | **Data language (products, receipt formats, line display, etc.)** |
| **Company** | Default                    | Default                                                           |
| **Store**   | Overrides company          | Overrides company                                                 |
| **User**    | Overrides store or company | Never                                                             |



