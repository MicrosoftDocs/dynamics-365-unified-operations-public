---
# required metadata

title: Preparing content for use with the Help pane
description: This article describes how you can prepare content for use with the Help pane. 
author: edupont04
manager: AnnBe
ms.date: 03/18/2020
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

Content for use with the Help pane for Dynamics 365 Finance, Supply Chain Management, and Commerce can be derived from Microsoft's existing content, migrated from existing Dynamics AX 2012 help, or created as new files.

Microsoft creates help in multiple languages for locales supported by Dynamics 365 Finance, Supply Chain Management, and Commerce. However, locale support is not restricted to these locales.

## Creating custom help content derived from Microsoft's existing content

You can use Microsoft's help content as a baseline for content to describe your solution. The [HtmlFromRepoGenerator tool](custom-help-toolkit-HtmlFromRepoGenerator.md) can retrieve the content in MarkDown files from Microsoft's repositories and convert the content to HTML files.  

For more information about using Microsoft's existing content as a baseline for content to describe your solution, see [Extend, customize, collaborate on the Help](contributor-guide.md)

## Migrating content from existing Dynamics AX 2012 help files

If you have existing content from Dynamics AX 2012, you can reuse that for Dynamics 365 Finance, Supply Chain Management, and Commerce. However, you must transform the HTML files so that they can be used in the custom Help environment. The [Custom Help Toolkit](custom-help-toolkit.md) includes a Windows PowerShell script, ```run_ax2012.ps1```, that transforms Dynamics AX 2012 HTML files so that they can be used in the custom Help environment.

## Creating new help content

Use the [AzureSearchCustomHelp](walkthrough-help-azure.md) solution that is provided as part of the [Custom Help Toolkit](custom-help-toolkit.md) to connect your content with the Help pane. The Help pane will generate a query to be run against the search service's index. Context-sensitive help and full-text search in AzureSearchCustomHelp depends on each article containing specific metadata.

### <a name="metadata"></a>Metadata requirements for custom help articles

The following metadata must be present in your articles for context-sensitive help and full-text search to return results in the [AzureSearchCustomHelp](walkthrough-help-azure.md)  solution:

|Property  |Description  |
|----------|-------------|
|title | The value is used for full-text search from the Help pane. |
|description  | The value is used for full-text search from the Help pane.  |
|ms.search.form | The value contains the Application Object Tree (AOT) name of a form and is used for context-sensitive search from the Help pane. |
|ms.locale |This value indicates the language of the article. The value is mapped against the current browser locale when the Help pane searches the content. The target custom help website can configure language fallback. For more information, see [Language and locale descriptors in across product and Help](language-locale.md). |
|ms.search.scope|The value determines which client the Help article is shown in. You can specify one or more values. Values includes Core, Operations, Retail, and Human Resources.|

The `ms.search.scope`property determines which client a Help article is shown in. You can specify one or more values. The following table describes the values:

|Value|Description|
|-----|-----------|
|Core|If this value is present, the article appears in the Help pane. Otherwise, the article doesn't appear in the Help pane. </br>**Core** is set for the part of the Microsoft content that must always be available in the Help pane for any user across all supported Dynamics 365 solutions.|
|Operations|Applies to solutions based on Dynamics 365 Finance or Supply Chain Management.|
|Retail    |Applies to solutions based on Dynamics 365 Commerce.|
|Human Resources  |Applies to solutions based on Dynamics 365 Human Resources.|
|Talent    |Applies to solutions based on Dynamics 365 Talent (Dynamics 365 Talent: Attract and Onboard apps are being retired. Learn more at [Retiring Dynamics 365 Talent: Attract and Onboard apps](https://community.dynamics.com/365/talent/b/dynamics365fortalent/posts/retiring-dynamics-365-talent-attract-and-nboard-apps).).|

### Non-required metadata

The following properties are reserved for future use:

- ms.search.region

    In the future, this property may be used to limit the content that is shown to content that is tagged either as global or for the region of the implementation.
- ms.search.validFrom

    In the future, this property may be used to limit the content that is shown to content for a product that was released on a given date or earlier.
- ms.dyn365.ops.version

    In the future, this property may be used to limit the content that is shown to content for a specific version of a product or earlier.

- ms.search.industry

    In the future, this property may be used to limit the content that is shown to content for a specific industry.

> [!TIP]
> Microsoft's content in the public GitHub repos contain additional metadata that is used by Microsoft in internal processes that are not related to the mechanics of the help system. You can ignore these metadata properties if you extend or customize Microsoft's content.  

## Changing the locale of articles to match the locale of solutions

Your solution might be intended to support multiple markets and you'll want to provide help content for each market. As an example, your solution might support German (Germany) and German (Austria), but you only have HTML files for German (Germany). To make the same content available in German (Austria), you can make a copy of the HTML files, and then use the [The HtmlLocaleChanger tool](custom-help-toolkit-HtmlLocaleChanger.md) to update the ms.locale metadata. You can also add content specific to Austria to these new HTML files, for example.

## Converting HTML files to JSON for use with an Azure Search Service

If you use the [AzureSearchCustomHelp](walkthrough-help-azure.md)  solution that is provided as part of the [Custom Help Toolkit](custom-help-toolkit.md), the search service requires all of your content in a JSON format. The [ConvertHtmlToJson tool](custom-help-toolkit-ConvertHtmlToJson.md) transforms HTML files into JSON files.

## See also

[Custom help overview](custom-help-overview.md)  
[Running the Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Connect the Help system](../../fin-ops/get-started/help-connect.md)  
[Help system](../../fin-ops/get-started/help-overview.md)  
