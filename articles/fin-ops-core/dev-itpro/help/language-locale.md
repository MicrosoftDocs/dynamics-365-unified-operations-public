---
# required metadata

title: Language and locale descriptors
description: This topic describes how you can extend the Microsoft Help to reflect your solution and then connect that to the Help pane in certain Dynamics 365 apps. 
author: edupont04
manager: AnnBe
ms.date: 11/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: SystemParameters
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 16141
ms.assetid: 0b9c8630-9474-4473-80fd-7db5d54b2275
ms.search.region: Global
# ms.search.industry: 
ms.author: edupont
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Language and locale descriptors in across product and Help

The Finance and Operations client supports many languages and locales. To add custom Help content for one or more locales to the in-product Help pane, the following must be true:

1. The value of the ```ms.locale``` property in each HTML file must match the locale of the content.  
2. The content must be uploaded to a folder with the same name as the locale on the website that hosts the content.  

For more information, see [Deploying custom Help](deploy.md) and [Example of Deploying Custom Help on Azure](walkthrough-help-azure.md).  

## Languages and descriptors

|Language region variation|Name of the language-region folder in the GitHub repo|Name of the language in the client|
|-------------------------|-----------------------------------------------------|-----------------------|
|Arabic (Saudi Arabia)|ar-sa|ar|
|Czech|cs-cz|cs|
|Danish|da-dk|da|
|German (Austria)|de-at|de-at|
|German (Switzerland)|de-ch|de-ch|
|German (Germany)|de-de|de|
|English (Australia)|en-au|en-au|
|English (Canada)|en-ca|en-ca|
|English (United Kingdom)|en-gb|en-gb|
|English (Ireland)|en-ie|en-ie|
|English (India)|en-in|en-in|
|English (Malaysia)|en-my|en-my|
|English (New Zealand)|en-nz|en-nz|
|English (Singapore)|en-sg|en-sg|
|English (US)|en-us|en-us|
|English (South Africa)|en-za|en-za|
|Spanish (Spain)|es-es|es|
|Spanish (Mexico)|es-mx|es-mx|
|Estonian|et-ee|et|
|Finnish|fi-fi|fi|
|French (Belgium)|fr-be|fr-be|
|French (Canada)|fr-ca|fr-ca|
|French (Switzerland)|fr-ch|fr-ch|
|French (France)|fr-fr|fr|
|Hungarian|hu-hu|hu|
|Icelandic|is-is|is|
|Italian (Switzerland)|it-ch|it-ch|
|Italian|it-it|it|
|Japanese|ja-jp|ja|
|Lithuanian|lt-lt|lt|
|Latvian|lv-lv|lv|
|Norwegian Bokmål|nb-no|nb-no|
|Dutch (Belgium)|nl-be|nl-be|
|Dutch (Netherlands)|nl-nl|nl|
|Polish|pl-pl|pl-pl|
|Portuguese (Brazil)|pt-br|pt-br|
|Russian|ru-ru|ru-ru|
|Swedish|sv-se|sv|
|Thai|th-th|th|
|Turkish|tr-tr|tr|
|Chinese|zh-cn|zh-hans|

## See also

[Deploying custom Help](deploy.md)  
[Running the Custom Help Toolkit](custom-help-toolkit.md)  
[Connect a custom help site](../../fin-ops/get-started/help-custom.md)  
