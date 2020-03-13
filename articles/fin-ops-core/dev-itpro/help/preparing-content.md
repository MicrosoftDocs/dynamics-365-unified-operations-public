---
# required metadata

title: Preparing content for use with the Help pane
description: This topic describes how you can prepare content for use with the Help pane. 
author: edupont04
manager: AnnBe
ms.date: 02/24/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

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

# Preparing content for use with the Help pane

[!include [banner](../includes/banner.md)]

Content for use with the Help pane for Dynamics 365 Finance, Supply Chain Management, and Commerce can be derived from Microsoft's existing content, migrated from existing Dynamics AX 2012 help, or created as new topics.

Microsoft creates help in multiple languages for locales supported by Dynamics 365 Finance, Supply Chain Management, and Commerce; however, locale support is not restricted to these locales.

## Creating custom help content derived from Microsoft's existing content

You can use Microsoft's help content as a baseline for content to describe your solution. The [HtmlFromRepoGenerator tool](custom-help-toolkit-HtmlFromRepoGenerator.md) can facilitate this reuse by retrieving the content in MarkDown format from Microsoft's repositories and converting the content to HTML format in preparation for customization.  

For more information about using Microsoft's existing content as a baseline for content to describe your solution, see [Extend, customize, collaborate on the Help](contributor-guide.md)

## Migrating content from existing Dynamics AX 2012 help topics

If you have existing content from Dynamics AX 2012, you can reuse that for Dynamics 365 Finance, Supply Chain Management, and Commerce. However, you must transform the HTML files so that they can be used in the custom Help environment. The [Custom Help Toolkit](custom-help-toolkit.md) includes a Windows PowerShell script, ```run_ax2012.ps1```, that transforms Dynamics AX 2012 HTML files so that they can be used in the custom Help environment.

## Creating new topics

If you are planning to use the [AzureSearchCustomHelp solution](walkthrough-help-azure.md) provided as part of the [Custom Help Toolkit](custom-help-toolkit.md), the Help pane will generate a query to be run against the search service's index. Context-sensitive help and full-text search in AzureSearchCustomHelp depends on each topic containing specific metadata.

### <a name="metadata"></a>Metadata requirements for custom help topics

The following metadata must be present in your topics for context-sensitive help and full-text search to return results in the [AzureSearchCustomHelp solution](walkthrough-help-azure.md):

|Property  |Description  |
|----------|-------------|
|title | The value is used for full-text search from the Help pane. |
|description  | The value is used for full-text search from the Help pane.  |
|ms.search.form | The value contains the Application Object Tree (AOT) name of a form and is used for context-sensitive search from the Help pane. |
|ms.search.scope|The value determines which client the Help topic is shown in. You can specify one or more values. Values includes Core, Operations, Retail, and Human Resources.|
|ms.locale |This value indicates the language of the topic. This is mapped against the current browser locale when the Help pane searches the content. the target custom help website can configure language fallback. For more information, see [Language and locale descriptors in across product and Help](language-locale.md). |

## Changing the locale of topics to match the locale of solutions

Your solution might be intended to support multiple markets and you'll want to provide help content for each markets. As an example, your solution might support German (Germany) and German (Austria), but you only have HTML files for German (Germany). To make the same content available in German (Austria), you can make a copy of the HTML files then use the [The HtmlLocaleChanger tool](custom-help-toolkit-HtmlLocaleChanger.md) to update the ms.locale metadata. You can then add content specific to Austria to these new HTML files.

## Converting HTML files to JSON for use with an Azure Search Service

If you are planning to use the [AzureSearchCustomHelp solution](walkthrough-help-azure.md) provided as part of the [Custom Help Toolkit](custom-help-toolkit.md), the search service requires all of your content in a JSON format. The [ConvertHtmlToJson tool](custom-help-toolkit-ConvertHtmlToJson.md) transforms HTML files into JSON files.

## See also

[Custom help overview](custom-help-overview.md)  
[Running the Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Connect the Help system](../../fin-ops/get-started/help-connect.md)  
[Help system](../../fin-ops/get-started/help-overview.md)  
