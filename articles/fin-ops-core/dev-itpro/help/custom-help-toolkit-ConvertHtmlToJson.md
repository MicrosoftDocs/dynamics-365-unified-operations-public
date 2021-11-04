---
# required metadata

title: Custom Help Toolkit - The ConvertHtmlToJson tool
description: This topic describes the ConvertHtmlToJson tool that is included in the Custom Help Toolkit for Finance and Operations apps. 
author: edupont04
ms.date: 05/11/2020
ms.topic: article

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

# Custom Help Toolkit: The ConvertHtmlToJson tool

[!include [banner](../includes/banner.md)]

The [Custom Help Toolkit](custom-help-toolkit.md) includes the **ConvertHtmlToJson** tool, which converts HTML files to JavaScript Object Notation (JSON) files. The search service uses the JSON files to index Help content.

## <a name="json"></a>Use the ConvertHtmlToJson tool to generate JSON files

The **ConvertHtmlToJson** tool transforms HTML files into JSON files. You can then add the JSON files to the Microsoft Azure Search service, which will generate context-sensitive links to your Help content.

The JSON files include metadata that the indexer uses to identify the form and language that the target Help page is intended for.

Here is the syntax for running ConvertHtmlToJson.exe.

```
ConvertHtmlToJson.exe --h <path> -j <path> --v <true|false>
```

Here is an explanation of the parameters.

| Parameter | Description |
|-----------|-------------|
| h | Specify the path of the HTML files to process. |
| j | Specify the folder to save the JSON files to. The specified folder must already exist. |
| v | Set this parameter to **true** to turn on verbose logging. Otherwise, set it to **false**. |

## Example

The following example generates JSON files without verbose logging.

```
ConvertHtmlToJson.exe --h D:\D365-Operations\d365F-O\supply-chain\de -j D:\D365-Operations\json\supply-chain\de
```

## See also

[Custom Help overview](custom-help-overview.md)  
[Deploy custom Help to Azure](walkthrough-help-azure.md)  
[Language and locale descriptors in the product and in Help](language-locale.md)  
[Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]