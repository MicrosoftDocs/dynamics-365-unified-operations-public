---
# required metadata

title: Custom Help Toolkit
description: This topic describes the components in the custom help toolkit for Finance and Operations apps. 
author: edupont04
manager: AnnBe
ms.date: 01/14/2020
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

Microsoft has published a GitHub repository with scripts and tools that can help you prepare content so that it can be accessed from the Help pane in the client that is used by the finance and operations apps. This way, users of custom solutions that are based on Dynamics 365 Finance, Supply Chain Management, Retail, or Talent can have access to context-sensitive Help.  

## Tools in the toolkit

The toolkit is available at [https://github.com/microsoft/dynamics365f-o-custom-help/](https://github.com/microsoft/dynamics365f-o-custom-help/) and provides the following tools as well as the source code for the tools:

- HtmlFromRepoGenerator tool

    For more information, see [Custom Help Toolkit: The HTML Locale Changer tool](custom-help-toolkit-HtmlLocaleChanger.md)

- Convert HTML to JSON tool

    For more information, see [Custom Help Toolkit: The Convert HTML To JSON tool](custom-help-toolkit-ConvertHtmlToJson.md)

- HtmlLocaleChanger tool

    For more information, see [Custom Help Toolkit: The HTML Locale Changer tool](custom-help-toolkit-HtmlLocaleChanger.md)

- Help Pane extension Visual Studio project

- REST API index creation scripts

- AX 2012 metadata scripts

> [!NOTE]
> The first version of this toolkit is available as a release in the GitHub repo.  


## <a name="helppane"></a>Use the development environment to extend the Help pane

The **Help Pane extension** folder of the toolkit contains the **AzureSearchCustomHelp** solution that you can open in the Finance and Operations development environment. The same folder also contains the **HelppaneOption.axpp** project that you can then import into the solution in Visual Studio.  

For an example of how to extend the Help, see [Connect your Help website with the Help pane](deploy.md#extendhelppane).  

## See also

[Deploying Custom Help](deploy.md)  
[Example of Deploying Custom Help on Azure](walkthrough-help-azure.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)  
