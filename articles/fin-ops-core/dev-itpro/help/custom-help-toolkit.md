---
# required metadata

title: Custom Help Toolkit
description: This topic describes the components in the custom help toolkit for Finance and Operations apps. 
author: edupont04
manager: AnnBe
ms.date: 02/04/2020
ms.topic: article
ms.service: dynamics-ax-platform

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: tfehr
ms.search.scope: Core, Operations
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

Microsoft has published a GitHub repository with scripts and tools that can help you prepare content that can be accessed from the in-product Help pane. This way, users of custom solutions that are based on Finance and Operations apps have access to context-sensitive Help for the customized solution.  

## Tools in the toolkit

The toolkit is available at [https://github.com/microsoft/dynamics365f-o-custom-help/](https://github.com/microsoft/dynamics365f-o-custom-help/). The repo contains the following tools and the source code for the tools:

- HTML From Repos Generator tool

    For more information, see [Custom Help Toolkit: The HTML From Repos Generator tool](custom-help-toolkit-HtmlFromRepoGenerator.md)

- Convert HTML to JSON tool

    For more information, see [Custom Help Toolkit: The Convert HTML to JSON tool](custom-help-toolkit-ConvertHtmlToJson.md)

- HTML Locale Changer tool

    For more information, see [Custom Help Toolkit: The HTML Locale Changer tool](custom-help-toolkit-HtmlLocaleChanger.md)

- Help Pane extension Visual Studio project

    For more information, see [Connect your Help website with the Help pane](connect-help-pane.md)

- REST API index creation scripts

- AX 2012 metadata scripts

    For more information, see [Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)

> [!NOTE]
> The first version of this toolkit is available as a [release in the GitHub repo](https://github.com/microsoft/dynamics365f-o-custom-help/releases).  

## Other products

Some of the tools in the toolkit can be used for custom help for solutions that are based on other Microsoft products, such as Dynamics 365 Business Central. However, the toolkit is currently only supported for Finance and Operations apps.

## See also

[Custom Help Overview](custom-help-websites.md)  
[Deploying custom help to Azure](walkthrough-help-azure.md)  
[Connect your Help website with the Help pane](connect-help-pane.md)
[Language and locale descriptors in across product and Help](language-locale.md)  
[Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)  
