---
# required metadata

title: Convert Dynamics AX 2012 content for Dynamics 365
description: This article describes how you can reuse content from Dynamics AX for your Dynamics 365 solution. 
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

# Convert Dynamics AX custom Help for use in Dynamics 365

[!include [banner](../includes/banner.md)]

If you have existing content from Dynamics AX 2012, you can reuse that for Dynamics 365 Finance, Supply Chain Management, and Commerce. However, you must transform the HTML files so that they can be used in the custom Help environment.  

## Converting Dynamics AX 2012 content

Microsoft's [Custom Help Toolkit](custom-help-toolkit.md) includes a Windows PowerShell script, ```run_ax2012.ps1```, that can transform Dynamics AX 2012 HTML files so that they can be used in the custom Help environment. The script makes the following changes to the Dynamics AX 2012 HTML files:  

- Replaces the **Microsoft.Help.F1** metadata name with **ms.search.form**  

- Replaces the **Title** metadata name with **title**  

- Changes the file name extension from **.htm** to **.html**  

- Adds the following metadata:  

    ```html
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

The following metadata is currently used or is reserved for use in indexing.  

```html
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

For a description of the required metadata, see [Metadata requirements for custom help articles](preparing-content.md#metadata).

##  <a name="moving-to-markdown"></a>Moving to MarkDown

Converting your existing content to MarkDown can be done using third-party tools, including but not limited to [PanDoc](https://pandoc.org) or the [Writage](https://writage.com) plugin for Word.  

When you have converted your content to MarkDown, you can use open source tools such as [DocFx](https://dotnet.github.io/docfx/) to generate content for your website. In general, working in MarkDown means that you have access to a world of open-source tools. For more information, see [Extend, Customize, and Collaborate on the Help](contributor-guide.md).  

## See also

[Deploying custom help sites](custom-help-overview.md)  
[Custom Help Overview](custom-help-overview.md)  
[Custom Help Toolkit](custom-help-toolkit.md)  
[Extend, Customize, and Collaborate on the Help](contributor-guide.md)  
