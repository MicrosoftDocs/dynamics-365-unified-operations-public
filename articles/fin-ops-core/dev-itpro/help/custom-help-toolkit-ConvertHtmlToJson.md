---
# required metadata

title: Custom Help Toolkit
description: This topic describes the components in the custom help toolkit for Finance and Operations apps. 
author: edupont04
manager: AnnBe
ms.date: 02/14/2020
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

# Custom Help Toolkit: The Convert HTML To JSON tool

[!include [banner](../includes/banner.md)]

The custom help toolkit includes the **ConvertHtmlToJson** tool that you can use to convert HTML files that are generated with the [HTML From Repos Generator tool](custom-help-toolkit-HtmlFromRepoGenerator.md) to JSON files for use with a search indexing service that connects your Help content with the in-product Help pane.  

## <a name="json"></a>Use the ConvertHtmlToJson tool to generate JSON files

[The ConvertHtmlToJson tool](https://github.com/microsoft/dynamics365f-o-custom-help/tree/master/Help%20Pane%20extension) transforms HTML files into JSON files that you can then add to the Azure Search service that will generate context-sensitive links to your Help content.  

The JSON files include metadata that is used by the indexer to identify which form and which language the target Help page is intended for.  

When you run the ConvertHtmlToJson tool, you must specify the location of the HTML files with your Help content, and you must specify the destination path.  

Here is the syntax for ConvertHtmlToJson.exe:  

```
ConvertHtmlToJson.exe --h <path> -j <path> --v <true|false>
```

Here is an explanation of the parameters:

|Parameter   |Description  |
|------------|-------------|
|h|Specifies the path to the HTML files that you want to process. |
|j|Specifies the folder that the JSON files will be saved to.|
|v|True to enable verbose logging; otherwise false.|

## Examples

The following example generates JSON files without verbose logging:

```
HtmlLocaleChanger.exe --h D:\D365-Operations\de --j D:\D365-Operations\json
```

## See also

[Deploying Custom Help](deploy.md)  
[Example of Deploying Custom Help on Azure](walkthrough-help-azure.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)  
