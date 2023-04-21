---
title: Convert Dynamics AX custom Help for use in Dynamics 365
description: This article describes how to reuse content from Microsoft Dynamics AX for your Dynamics 365 solution.
author: bholtorf
ms.date: 04/21/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: bholtorf
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Operations
---

# Convert Dynamics AX custom Help for use in Dynamics 365

[!include [banner](../includes/banner.md)]

If you have content from Microsoft Dynamics AX 2012, you can reuse it for Dynamics 365 Finance, Dynamics 365 Supply Chain Management, and Dynamics 365 Commerce. However, you must first transform the HTML files so that they can be used in the custom Help environment.

## Convert AX 2012 content

The **run_ax2012.ps1** Windows PowerShell script transforms AX 2012 HTML files so that they can be used in the custom Help environment. The script makes the following changes to the AX 2012 HTML files:

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

### Run the script

Run the following command from a Command Prompt window, or directly in Windows PowerShell.

```powershell
PowerShell.exe -File run_ax2012.ps1 "Original file location" "New file location"
```

The following metadata is used, or it's reserved so that it can be used during indexing.

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

For a description of the required metadata, go to [Metadata requirements for custom Help topics](preparing-content.md#metadata).

## <a name="moving-to-markdown"></a>Convert HTML content to Markdown

To convert your content to Markdown, use a third-party tool. Microsoft does not provide a tool that can convert HTML to Markdown.

After you've converted your content to Markdown, use an open-source tool to generate content for your website. Markdown gives you access to a wide range of open-source tools. For more information, go to [Contribute to the Help](contributor-guide.md).

## See also

[Custom Help overview](custom-help-overview.md)  
[Contriubute to the Help](contributor-guide.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]