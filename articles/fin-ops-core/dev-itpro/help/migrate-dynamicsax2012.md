---
# required metadata

title: Convert Dynamics AX 2012 content for Dynamics 365
description: This topic describes how you can reuse content from Dynamics AX for your Dynamics 365 solution. 
author: edupont04
manager: AnnBe
ms.date: 03/04/2020
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

# Convert Dynamics AX custom Help for use in Dynamics 365

[!include [banner](../includes/banner.md)]

If you have existing content from Dynamics AX 2012, then you can reuse that for Dynamics 365 Finance, Supply Chain Management, and Commerce. However, you must transform the HTML files so that they can be used in the custom Help environment.  

## Converting Dynamics AX 2012 content

Microsoft has published a [Custom Help Toolkit](custom-help-toolkit.md) that includes a Windows PowerShell script, ```run_ax2012.ps1```, that can transform Dynamics AX 2012 HTML files so that they can be used in the custom Help environment. The script makes the following changes to the Dynamics AX 2012 HTML files:  

- Replaces the **Microsoft.Help.F1** metadata name with **ms.search.form**  

- Replaces the **Title** metadata name with **title**  

- Changes the file name extension from **.htm** to **.html**  

- Adds the following metadata:  

    ```yaml
    <meta name="ms.search.region" content="Global" />  
    <meta name="ms.search.scope" content="Operations, Core" />  
    <meta name="ms.dyn365.ops.version" content="AX 7.0.0" />  
    <meta name="ms.search.validFrom" content="2016-05-31" />  
    <meta name="ms.search.industry" content="cross" />  
    ```

### Running the script

You can run the following command from a Command Prompt window, or you can run the script directly in Windows PowerShell.  

```powershell
    PowerShell.exe -File run_ax2012.ps1 "Original file location" "New file location"  
```

The following metadata is currently used or are reserved for use in indexing.  

```yaml
    <meta name="title" content="Title of file" />  
    <meta name="ms.locale" content="locale" />  
    <meta name="ms.search.form" content="FormAOTName" />  
    <meta name="description" content="Description of file" />  
    <meta name="ms.search.region" content="Global" />  
    <meta name="ms.search.scope" content="Operations, Core" />  
    <meta name="ms.dyn365.ops.version" content="AX 7.0.0" />  
    <meta name="ms.search.validFrom" content="2016-05-31" />  
    <meta name="ms.search.industry" content="cross" />  
```

The following table describes the metadata properties:  

|Property  |Description  |
|----------|-------------|
|title | The value is used for full-text search from the Help pane. |
|description  | The value is used for full-text search from the Help pane.  |
|ms.search.form | The value contains the Application Object Tree (AOT) name of a form. If a value is present, it's used for context-sensitive search from the Help pane. |
|ms.locale |This value indicates the language of the topic. It isn't currently used in the Dynamics 365 Help pane, but it might be used in the future.   |

The following property is used in the Finance and Operations client and will be added to the custom implementation of the Help pane:  

- ms.search.scope

    The value determines which client a Help topic is shown in. You can specify one or more values. The following table describes the values:

    |Value|Description|
    |-----|-----------|
    |Core|If this value is present, the topic appears in the Help pane. Otherwise, the topic doesn't appear in the Help pane. </br>This is set for the part of the Microsoft content that must always be available in the Help pane for any user across all supported Dynamics 365 solutions.|
    |Operations|Applies to solutions based on Dynamics 365 Finance or Supply Chain Management.|
    |Retail    |Applies to solutions based on Dynamics 365 Commerce.|
    |Human Resources  |Applies to solutions based on Dynamics 365 Human Resources.|
    |Talent    |Applies to solutions based on Dynamics 365 Talent (Dynamics 365 Talent: Attract and Onboard apps are being retired. Learn more at [Retiring Dynamics 365 Talent: Attract and Onboard apps](https://community.dynamics.com/365/talent/b/dynamics365fortalent/posts/retiring-dynamics-365-talent-attract-and-onboard-apps).).|

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

##  <a name="moving-to-markdown"></a>Moving to MarkDown

If you want to customize or extend the Microsoft Help, you can fork our public repo for either the source repo in English (US) at [https://github.com/MicrosoftDocs/Dynamics-365-unified-Operations-public](https://github.com/MicrosoftDocs/Dynamics-365-unified-Operations-public), or one of the related repos with translations into the supported languages. For more information, see [Extend, Customize, and Collaborate on the Help](contributor-guide.md).  

Converting your existing content to MarkDown can be done using third-party tools, including but not limited to [PanDoc](https://pandoc.org) or the [Writage](https://writage.com) plugin for Word.  

When you have converted your content to MarkDown, you can use a Git repo in Azure DevOps as your source repository, create a private or public repo in GitHub, or set up a project in [MkDocs](https://www.mkdocs.org/), for example. Then you can use open source tools such as [DocFx](https://dotnet.github.io/docfx/) to generate content for your website. In general, working in MarkDown means that you have access to a world of open source tools and do not have a hard dependency on Microsoft providing you with tools.  

## See also

[Deploying custom help sites](custom-help-overview.md)  
[Custom Help Overview](custom-help-overview.md)  
[Custom Help Toolkit](custom-help-toolkit.md)  
[Extend, Customize, and Collaborate on the Help](contributor-guide.md)  
