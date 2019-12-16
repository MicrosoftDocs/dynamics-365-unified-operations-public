---
# required metadata

title: Language and locale descriptors
description: This topic describes how you can extend the Microsoft Help to reflect your solution and then connect that to the Help pane in certain Dynamics 365 apps. 
author: edupont04
manager: AnnBe
ms.service: dynamics-ax-platform

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

The client used by finance and operations apps supports many languages and locales. To add custom Help content for one or more locales to the in-product Help pane, the following must be true:

1. The value of the ```ms.locale``` property in each HTML file must match the locale of the content.  
2. The content must be uploaded to a folder with the same name as the locale on the website that hosts the content.  

For more information, see [Deploying custom Help](deploy.md) and [Example of Deploying Custom Help on Azure](walkthrough-help-azure.md).  

## Languages and descriptors

The following table maps the language names between the client and the GitHub repos with Microsoft's translated Help content.  

|Language region variation|Name of the GitHub repo|Name of the language in the client|
|-------------------------|-----------------------|----------------------------------|
|Arabic (United Arab Emirates)|[Dynamics-365-Operations.ar-sa](https://github.com/MicrosoftDocs/Dynamics-365-Operations.ar-sa)|ar|
|Arabic (Saudi Arabia)|[Dynamics-365-Operations.ar-sa](https://github.com/MicrosoftDocs/Dynamics-365-Operations.ar-sa)|ar|
|Czech|[Dynamics-365-Operations.cs-cz](https://github.com/MicrosoftDocs/Dynamics-365-Operations.cs-cz)|cs|
|Danish|[Dynamics-365-Operations.da-dk](https://github.com/MicrosoftDocs/Dynamics-365-Operations.da-dk/)|da|
|German (Austria)|[Dynamics-365-Operations.de-de](https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de)|de-at|
|German (Switzerland)|[Dynamics-365-Operations.de-de](https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de)|de-ch|
|German (Germany)|[Dynamics-365-Operations.de-de](https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de)|de|
|English (Australia)|[Dynamics-365-Unified-Operations-Public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-Public)|en-au|
|English (Canada)|[Dynamics-365-Unified-Operations-Public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-Public)|en-ca|
|English (United Kingdom)|[Dynamics-365-Unified-Operations-Public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-Public)|en-gb|
|English (Ireland)|[Dynamics-365-Unified-Operations-Public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-Public)|en-ie|
|English (India)|[Dynamics-365-Unified-Operations-Public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-Public)|en-in|
|English (Malaysia)|[Dynamics-365-Unified-Operations-Public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-Public)|en-my|
|English (New Zealand)|[Dynamics-365-Unified-Operations-Public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-Public)|en-nz|
|English (Singapore)|[Dynamics-365-Unified-Operations-Public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-Public)|en-sg|
|English (US)|[Dynamics-365-Unified-Operations-Public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-Public)|en-us|
|English (South Africa)|[Dynamics-365-Unified-Operations-Public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-Public)|en-za|
|Spanish (Spain)|[Dynamics-365-Operations.es-es](https://github.com/MicrosoftDocs/Dynamics-365-Operations.es-es)|es|
|Spanish (Mexico)|[Dynamics-365-Operations.es-es](https://github.com/MicrosoftDocs/Dynamics-365-Operations.es-es)|es-mx|
|Estonian|[Dynamics-365-Operations.et-ee](https://github.com/MicrosoftDocs/Dynamics-365-Operations.et-ee)|et|
|Finnish|[Dynamics-365-Operations.fi-fi](https://github.com/MicrosoftDocs/Dynamics-365-Operations.fi-fi)|fi|
|French (Belgium)|[Dynamics-365-Operations.fr-fr](https://github.com/MicrosoftDocs/Dynamics-365-Operations.fr-fr)|fr-be|
|French (Canada)|[Dynamics-365-Operations.fr-fr](https://github.com/MicrosoftDocs/Dynamics-365-Operations.fr-fr)|fr-ca|
|French (Switzerland)|[Dynamics-365-Operations.fr-fr](https://github.com/MicrosoftDocs/Dynamics-365-Operations.fr-fr)|fr-ch|
|French (France)|[Dynamics-365-Operations.fr-fr](https://github.com/MicrosoftDocs/Dynamics-365-Operations.fr-fr)|fr|
|Hungarian|[Dynamics-365-Operations.hu-hu](https://github.com/MicrosoftDocs/Dynamics-365-Operations.hu-hu)|hu|
|Icelandic|[Dynamics-365-Operations.is-is](https://github.com/MicrosoftDocs/Dynamics-365-Operations.is-is)|is|
|Italian (Switzerland)|[Dynamics-365-Operations.it-it](https://github.com/MicrosoftDocs/Dynamics-365-Operations.it-it)|it-ch|
|Italian|[Dynamics-365-Operations.it-it](https://github.com/MicrosoftDocs/Dynamics-365-Operations.it-it)|it|
|Japanese|[Dynamics-365-Operations.ja-jp](https://github.com/MicrosoftDocs/Dynamics-365-Operations.ja-jp)|ja|
|Lithuanian|[Dynamics-365-Operations.lt-lt](https://github.com/MicrosoftDocs/Dynamics-365-Operations.lt-lt)|lt|
|Latvian|[Dynamics-365-Operations.lv-lv](https://github.com/MicrosoftDocs/Dynamics-365-Operations.lv-lv)|lv|
|Norwegian Bokmål|[Dynamics-365-Operations.nb-no](https://github.com/MicrosoftDocs/Dynamics-365-Operations.nb-no)|nb-no|
|Dutch (Belgium)|[Dynamics-365-Operations.nl-nl](https://github.com/MicrosoftDocs/Dynamics-365-Operations.nl-nl)|nl-be|
|Dutch (Netherlands)|[Dynamics-365-Operations.nl-nl](https://github.com/MicrosoftDocs/Dynamics-365-Operations.nl-nl)|nl|
|Polish|[Dynamics-365-Operations.pl-pl](https://github.com/MicrosoftDocs/Dynamics-365-Operations.pl-pl)|pl|
|Portuguese (Brazil)|[Dynamics-365-Operations.pt-br](https://github.com/MicrosoftDocs/Dynamics-365-Operations.pt-br)|pt-br|
|Russian|[Dynamics-365-Operations.ru-ru](https://github.com/MicrosoftDocs/Dynamics-365-Operations.ru-ru)|ru|
|Swedish|[Dynamics-365-Operations.sv-se](https://github.com/MicrosoftDocs/Dynamics-365-Operations.sv-se)|sv|
|Thai|[Dynamics-365-Operations.th-th](https://github.com/MicrosoftDocs/Dynamics-365-Operations.th-th)|th|
|Turkish|[Dynamics-365-Operations.tr-tr](https://github.com/MicrosoftDocs/Dynamics-365-Operations.tr-tr)|tr|
|Chinese|[Dynamics-365-Operations.zh-cn](https://github.com/MicrosoftDocs/Dynamics-365-Operations.zh-cn)|zh-hans|

## See also

[Deploying custom Help](deploy.md)  
[Running the Custom Help Toolkit](custom-help-toolkit.md)  
[Connect a custom help site](../../fin-ops/get-started/help-custom.md)  
