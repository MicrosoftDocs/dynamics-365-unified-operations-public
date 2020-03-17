---
# required metadata

title: Custom Help Toolkit
description: This topic describes the components in the custom help toolkit for Finance and Operations apps. 
author: edupont04
manager: AnnBe
ms.date: 02/24/2020
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

# Custom Help Toolkit: The ConvertHtmlToJson tool

[!include [banner](../includes/banner.md)]

The [Custom Help Toolkit](custom-help-toolkit.md) includes the **ConvertHtmlToJson** tool that converts HTML files to JSON files. The JSON files will be used by the search service so that the content can be indexed as the HTML files cannot be used for this purpose.  

## <a name="json"></a>Use the ConvertHtmlToJson tool to generate JSON files

The ConvertHtmlToJson tool transforms HTML files into JSON files. You can then add the JSON files to the Azure Search service that will generate context-sensitive links to your Help content.  

The JSON files include metadata that is used by the indexer to identify the form and language that the target Help page is intended for.  

Here is the syntax for ConvertHtmlToJson.exe:  

```
ConvertHtmlToJson.exe --h <path> -j <path> --v <true|false>
```

Here is an explanation of the parameters:

|Parameter   |Description  |
|------------|-------------|
|h|Specifies the path to the HTML files that you want to process. |
|j|Specifies the folder that the JSON files will be saved to. The folder must already exist.|
|v|True to enable verbose logging; otherwise false.|

## Examples

The following example generates JSON files without verbose logging:

```
ConvertHtmlToJson.exe --h D:\D365-Operations\d365F-O\supply-chain\de -j D:\D365-Operations\json\supply-chain\de
```

## See also

[Custom Help Overview](custom-help-overview.md)  
[Deploying custom help to Azure](walkthrough-help-azure.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)  
