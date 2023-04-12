---
title: Language and locale descriptors in Help
description: This article maps the language names between the finance and operations client and the GitHub repos that contain translated Microsoft Help content.
author: edupont04
ms.date: 02/11/2023
ms.topic: article
audience: IT Pro
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: edupont
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Operations
---

# Language and locale descriptors in Help

The client that finance and operations apps use supports multiple languages and locales. To add custom Help content for one or more locales to the in-product **Help** pane, you must make sure that both the following conditions are met:

- The value of the **ms.locale** property in each HTML file matches the locale of the content.

    For example, the German (Germany) content must have a setting of **ms.locale: de-de**.

- On the custom Help website, the content is in a folder has the same name as the locale.

    For example, the German (Germany) content must be in a folder that is named **de-de**.

For more information, see [Deploy custom Help to Azure](walkthrough-help-azure.md).

## Languages and descriptors

The following table lists the languages that the finance and operations help can support.

| Language/locale  | Language/region name |
|-------------------------------|----------------------|
| ar | Arabic (Saudi Arabia) | 
| ar-ae | Arabic (United Arab Emirates) |
| cs | Czech | 
| da | Danish | 
| de | German (Germany) |
| de-at | German (Austria) |
| de-ch | German (Switzerland) |
| en-au | English (Australia) |
| en-ca | English (Canada) | 
| en-gb | English (United Kingdom) |
| en-ie | English (Ireland) |
| en-in | English (India) |
| en-my | English (Malaysia) |
| en-nz | English (New Zealand) |
| en-sg | English (Singapore) |
| en-us | English (US) |
| en-za | English (South Africa) |
| es | Spanish (Spain) |
| es-mx | Spanish (Mexico) |
| et | Estonian |
| fi | Finnish |
| fr | French (France) |
| fr-be | French (Belgium) |
| fr-ca | French (Canada) |
| fr-ch | French (Switzerland) |
| hu | Hungarian |
| is | Icelandic |
| it | Italian |
| it-ch | Italian (Switzerland) |
| ja | Japanese |
| lt | Lithuanian |
| lv | Latvian |
| nb-no | Norwegian Bokmål |
| nl | Dutch (Netherlands) |
| nl-be | Dutch (Belgium) |
| pl | Polish |
| pt-br | Portuguese (Brazil) |
| ru | Russian |
| sv | Swedish |
| th | Thai |
| tr | Turkish |
| zh-hans | Chinese |

## See also

[Custom Help overview](custom-help-overview.md)  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
