---
# required metadata

title: Custom Help Toolkit
description: This topic describes the components of the Custom Help Toolkit for Finance and Operations apps. 
author: edupont04
ms.date: 05/11/2020
ms.topic: article

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: edupont
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Operations

---

# Custom Help Toolkit

[!include [banner](../includes/banner.md)]

Microsoft has published a GitHub repository (repo) that includes scripts and tools that can help you prepare context-sensitive Help for customized Finance and Operations solutions. This context-sensitive Help can be accessed from the in-product **Help** pane.

## Tools in the toolkit

The Custom Help Toolkit is available at [https://github.com/microsoft/dynamics365f-o-custom-help](https://github.com/microsoft/dynamics365f-o-custom-help/). The repo contains the following tools and the source code for those tools:

- The **HtmlFromRepoGenerator** tool

    For more information, see [Custom Help Toolkit: The HtmlFromRepoGenerator tool](custom-help-toolkit-HtmlFromRepoGenerator.md).

- The **ConvertHtmlToJson** tool

    For more information, see [Custom Help Toolkit: The ConvertHtmlToJson tool](custom-help-toolkit-ConvertHtmlToJson.md).

- The **HtmlLocaleChanger** tool

    For more information, see [Custom Help Toolkit: The HtmlLocaleChanger tool](custom-help-toolkit-HtmlLocaleChanger.md).

- The **Help Pane extension** Microsoft Visual Studio project

    For more information, see [Connect a custom Help website to the Help pane](connect-help-pane.md).

- Dynamics AX 2012 metadata scripts

    For more information, see [Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md).

> [!NOTE]
> The first version of the toolkit is available as a [release in the GitHub repo](https://github.com/microsoft/dynamics365f-o-custom-help/releases).

## See also

[Custom Help overview](custom-help-overview.md)  
[Deploy custom Help to Azure](walkthrough-help-azure.md)  
[Connect a custom Help website to the Help pane](connect-help-pane.md)  
[Language and locale descriptors in the product and in Help](language-locale.md)  
[Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]