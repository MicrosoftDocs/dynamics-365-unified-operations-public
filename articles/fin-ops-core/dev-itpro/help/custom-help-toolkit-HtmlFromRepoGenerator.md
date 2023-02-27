---
title: Custom Help Toolkit - The HtmlFromRepoGenerator tool
description: This article describes the HtmlFromRepoGenerator tool that is included in the Custom Help Toolkit for finance and operations apps.
author: edupont04
ms.date: 05/11/2020
ms.topic: article
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: edupont
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Operations
---

# Custom Help Toolkit: The HtmlFromRepoGenerator tool

[!include [banner](../includes/banner.md)]

[!INCLUDE [custom-help-toolkit-deprecation](../includes/custom-help-toolkit-deprecation.md)]

The Custom Help Toolkit includes the **HtmlFromRepoGenerator** tool, which gets Microsoft content in Markdown files and converts it to HTML files. You can then deploy the HTML files to a website.

## <a name="consoleapp"></a>Use the HtmlFromRepoGenerator tool to get Markdown files and generate HTML files

> [!NOTE]
> You can only use the HtmlFromRepoGenerator tool to retrieve content of the Markdown files for the English language.  

The **HtmlFromRepoGenerator** tool provides functionality that supports the creation of custom Help that is based on source files from Microsoft. You can use the tool to perform these tasks:

- Clone a Microsoft documentation repository (repo).
- Remove developer and admin content from your clone of the Microsoft repo.
- Update links to files that are no longer present in the clone.
- Generate HTML files that can be used to publish content.

    By default, the HTML files are generated in the **d365F-O** subfolder. The files are generated based on the style sheets and templates that are packaged by DocFX. For more information, see [Modifying the styling of the generated HTML files](#modifying-the-styling-of-the-generated-html-files).

- Compare a localized Microsoft repo to the en-US repo to identify differences and update links accordingly.

> [!NOTE]
> In the first version of the Custom Help Toolkit, this tool was named ConsoleApp. The tool was renamed and updated in 2020.

### Syntax

Here is the syntax for running HtmlFromRepoGenerator.exe.

```
HtmlFromRepoGenerator.exe --Json <Articles/> --Out <path> --ExternalText <text> [--DoNotClone <true|false>] [--Repo <URL>] [--RemoveGitFolder <true|false>] [--ReplaceUrl <URL>] [--LogsDir <.\logs>] [--EnRepo <URL>] [--EnOut <path>] [--Lng <language code>] [--Rtl] [--?[--]]
```

Here is an explanation of the parameters.

| Parameter | Description |
|-----------|-------------|
| Json | Specify a relative path for the location of the **docfx.json** file. In Microsoft documentation repos, this location is typically **articles/**. |
| Out | Specify the folder where your existing cloned repo exists, or the folder to clone the repo to. If you run the **HtmlFromRepoGenerator** tool to clone a repo, this folder must not already exist. Use the language name as the folder name, as described in [Language and locale descriptors in the product and in Help](language-locale.md). |
| ExternalText | Specify text that should be added to the updated links if the **HtmlFromRepoGenerator** tool must replace the original links. |
| DoNotClone | Set this parameter when you run the tool against a previously cloned repo. |
| Repo | Specify the repo URL. This parameter is optional if you run the tool against a previously cloned repo. The URL of the repo for the English (United States) content is https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public.|
| RemoveGitFolder| Specify whether the **.git** folder should be removed. |
| ReplaceUrl | Specify the URL that should replace links between files when the target files aren't present. This parameter is intended to be used to turn relative links into absolute links. |
| LogsDir | Specify the folder to save logs files to. |

## Examples

> [!NOTE]
> Because the Microsoft repos contain many files, the process takes several minutes.

The following example clones the en-US repo and generates HTML files for en-US.

```dos
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\en-US" --repo "https://github.com/MicrosoftDocs/Dynamics-365-unified-Operations-public" --externalText "(This is an external link)" --replaceUrl "https://learn.microsoft.com/dynamics365/supply-chain" --LogsDir D:\D365-Operations\logs\en-US
```

The following example uses a previously cloned en-US repo and generates HTML files for en-US.

```dos
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\en-US" --externalText "(This is an external link)" --replaceUrl "https://learn.microsoft.com/dynamics365/supply-chain" --LogsDir D:\D365-Operations\logs\en-US
```

> [!IMPORTANT]
> Because the **HtmlFromRepoGenerator** tool changes links during processing, don't run HtmlFromRepoGenerator.exe more than one time against a previously cloned repo. If it's run more than one time against the same content, links will be incorrect. If you want to rerun HtmlFromRepoGenerator.exe, either use the **HtmlFromRepoGenerator** tool to create a new clone of the repo, or revert all local changes that have been made to your existing clone.

## Modifying the styling of the generated HTML files

The HTML files that the **HtmlFromRepoGenerator** tool generates are based on a set of predefined templates. In most cases, you can edit the style sheets in the **d365F-O\\styles** folder to change the appearance of your content.

For advanced scenarios, you can change the templates that the **HtmlFromRepoGenerator** tool uses. The source files are included in the **SourceCode** folder in the GitHub repo. The templates are in the **SourceCode\\HtmlFromRepoGenerator\\HtmlFromRepoGenerator\\HtmlFromRepoGenerator\\Resources** subfolder.

> [!NOTE]
> If you change the templates, you must rebuild HtmlFromRepoGenerator.exe.

For more information, see [Introduction to DocFX Template System](https://dotnet.github.io/docfx/tutorial/intro_template.html).

## See also

[Custom Help Toolkit](custom-help-toolkit.md)  
[Custom Help overview](custom-help-overview.md)  
[Deploy custom Help to Azure](walkthrough-help-azure.md)  
[Language and locale descriptors in the product and in Help](language-locale.md)  
[Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
