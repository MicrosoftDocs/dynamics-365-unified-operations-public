---
# required metadata

title: Convert Dynamics AX custom Help for use in Dynamics 365
description: This topic describes how you can reuse content from Microsoft Dynamics AX for your Dynamics 365 solution. 
author: edupont04
ms.date: 05/11/2020
ms.topic: article
ms.prod: 
ms.technology: 

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

# Convert Dynamics AX custom Help for use in Dynamics 365

[!include [banner](../includes/banner.md)]

If you have existing content from Microsoft Dynamics AX 2012, you can reuse it for Dynamics 365 Finance, Dynamics 365 Supply Chain Management, and Dynamics 365 Commerce. However, you must first transform the HTML files so that they can be used in the custom Help environment.

## Converting AX 2012 content

The Microsoft [Custom Help Toolkit](custom-help-toolkit.md) includes a Windows PowerShell script, **run_ax2012.ps1**, that can transform AX 2012 HTML files so that they can be used in the custom Help environment. The script makes the following changes to the AX 2012 HTML files:

- Replace the **Microsoft.Help.F1** metadata name with **ms.search.form**.
- Replace the **Title** metadata name with **title**.
- Change the file name extension from **.htm** to **.html**.
- Add the following metadata.

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

The following metadata is currently used, or it's reserved so that it can be used during indexing.

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

For a description of the required metadata, see [Metadata requirements for custom Help topics](preparing-content.md#metadata).

## <a name="moving-to-markdown"></a>Moving to Markdown

To convert your existing content to Markdown, you can use various third-party tools, such as [PanDoc](https://pandoc.org) and the [Writage](http://www.writage.com) plug-in for Word.

After you've converted your content to Markdown, you can use open-source tools such as [DocFx](https://dotnet.github.io/docfx/) to generate content for your website. In general, by working in Markdown, you gain access to a wide range of open-source tools. For more information, see [Extend, customize, and collaborate on the Help](contributor-guide.md).

## See also

[Custom Help overview](custom-help-overview.md)  
[Custom Help Toolkit](custom-help-toolkit.md)  
[Extend, customize, and collaborate on the Help](contributor-guide.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]