---
# required metadata

title: Convert Dynamics AX 2012 content for Dynamics 365
description: This topic describes how you can reuse content from Dynamics AX for your Dynamics 365 solution. 
author: edupont04
manager: AnnBe
ms.date: 10/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

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

# Convert Dynamics AX custom Help for use in Dynamics 365

[!include [banner](../includes/banner.md)]

## Converting Dynamics AX 2012 content

If you have existing content from Dynamics AX 2012, then you can reuse that for Dynamics 365. However, you must transform the HTML files so that they can be used in the custom Help environment.  

The Dynamics 365 custom Help Toolkit includes a Windows PowerShell script, ```run_ax2012.ps1```, that can transform Dynamics AX 2012 HTML files so that they can be used in the custom Help environment. The script makes the following changes to the Dynamics AX 2012 HTML files:  

- Replaces the Microsoft.Help.F1 metadata name with ms.search.form  

- Replaces the Title metadata name with title  

- Changes the file name extension from .htm to .html  

- Adds the following metadata:  

    ```yaml
    <meta name="ms.search.region" content="Global" />  
    <meta name="ms.search.scope" content="Operations, Core" />  
    <meta name="ms.dyn365.ops.version" content="AX 7.0.0" />  
    <meta name="ms.search.validFrom" content="2016-05-31" />  
    <meta name="ms.search.industry" content="cross" />  
    ```

You can run the following command from a Command Prompt window, or you can run the script directly in Windows PowerShell.  

```powershell
    PowerShell.exe -File run_ax2012.ps1 "Original file location" "New file location"  
```

The following metadata values are currently used or are reserved for use in indexing.  

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

Here is a description of the metadata values:  

|Property  |Description  |
|----------|-------------|
|title | The value is used for full-text search from the Help pane. |
|description  | The value is used for full-text search from the Help pane.  |
|ms.search.form | The value contains the Application Object Tree (AOT) name of a form. If a value is present, it’s used for context-sensitive search from the Help pane. |
|ms.locale |This value indicates the language of the topic. It isn't currently used in the Dynamics 365 Help pane, but it might be used in the future.   |

The following values are used in the Dynamics 365 client and will be added to the custom implementation of the Help pane:  

|Property  |Description  |
|----------|-------------|
|ms.search.scope| The value determines which client a Help topic is shown in. One or more values are supported.</br>
Values have the following meanings:</br>
- Core – If this value is present, the topic appears in the Help pane. Otherwise, the topic doesn’t appear in the Help pane. This value is useful for Microsoft since our GitHub repo serves multiple products and also includes us, because we publish many developer and IT Pro-specific topics that are not relevant for endusers.</br>
- Operations – Finance and or Operations Supply Chain Management topic.</br>  
- Retail – Retail topic.</br>  
- Talent – Talent topic.</br>
The following values are reserved for future use:  </br>
- ms.search.region: In the future, this value will be used to limit the content that is shown to content that is tagged either as global or for the region of the implementation.  </br>
- ms.search.validFrom: In the future, this value will be used to limit the content that is shown to content for a product that was released on a given date or earlier.  </br>
- ms.dyn365.ops.version: In the future, this value will be used to limit the content that is shown to content for a specific version of a product or earlier.  </br>
- ms.search.industry: In the future, this value will be used to limit the content that is shown to content for a specific industry.  |