---
# required metadata

title: Custom Help Toolkit - The HtmlFromRepoGenerator tool
description: This topic describes the HtmlFromRepoGenerator tool that is included in the Custom Help Toolkit for Finance and Operations apps. 
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

# Custom Help Toolkit: The HtmlFromRepoGenerator tool

[!include [banner](../includes/banner.md)]

The Custom Help Toolkit includes the **HtmlFromRepoGenerator** tool, which gets Microsoft content in Markdown files and converts it to HTML files. You can then deploy the HTML files to a website.

## <a name="consoleapp"></a>Use the HtmlFromRepoGenerator tool to get Markdown files and generate HTML files

The **HtmlFromRepoGenerator** tool provides functionality that supports the creation of custom Help that is based on source files from Microsoft. You can use the tool to perform these tasks:

- Clone a Microsoft documentation repository (repo).
- Remove developer and admin content from your clone of the Microsoft repo.
- Update links to files that are no longer present in the clone.
- Update the value of the **ms.locale** property so that it matches the language options that are supported by the Finance and Operations client.

    The language descriptors that the client uses differ from the language descriptors that are used in the corresponding GitHub repos. Before localized custom Help can be called, the language descriptors in the source content must be changed so that they match the client's languages. For more information, see [Language and locale descriptors in the product and in Help](language-locale.md).

- Generate HTML files that can be used to publish content.

    The HTML files will be generated in the **d365F-O** subfolder. The files are generated based on style sheets and templates that are part of the tool. For more information, see the [Modifying the styling of the generated HTML files](#modifying-the-styling-of-the-generated-html-files) section of this topic.

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
| Repo | Specify the repo URL. This parameter is optional if you run the tool against a previously cloned repo. Examples of URLs for Microsoft documentation repos include `https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public` for English (United States) and `https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de` for German (Germany).|
| RemoveGitFolder| Specify whether the **.git** folder should be removed. |
| ReplaceUrl | Specify the URL that should replace links between files when the target files aren't present. This parameter is intended to be used to turn relative links into absolute links. |
| LogsDir | Specify the folder to save logs files to. |

The following additional parameters are used when the tool is run against the localized Microsoft documentation repos.

| Parameter | Description |
|-----------|-------------|
| EnRepo | Specify the URL of the en-US repo. This parameter is optional if you run the tool against a previously cloned repo. The URL of the Microsoft documentation repo for English (United States) is `https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public`. |
| EnOut | Specify the folder where the en-US repo exists, or the folder to clone it to. If you run the tool against a previously cloned repo, this folder must not already exist. |
| Lng | Specify the language value that should be used for **ms.locale** metadata in the generated HTML files. The value must correspond to the value that is specified in the language settings of the Finance and Operations client. If this parameter isn't set, the tool uses **en-US**. For more information, see [Language and locale descriptors in the product and in Help](language-locale.md). |
| Rtl | Include this parameter if the language uses right-to-left (RTL) formatting. Examples of RTL languages include Arabic and Hebrew. |

## Examples

> [!NOTE]
> Because the Microsoft repos contain many files, the process takes several minutes. If you run the tool against multiple localized repos, the process takes longer.

The following example clones the en-US repo and generates HTML files for en-US.

```dos
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\en-US" --repo "https://github.com/MicrosoftDocs/Dynamics-365-unified-Operations-public" --externalText "(This is an external link)" --replaceUrl "https://docs.microsoft.com/en-us/dynamics365/supply-chain" --LogsDir D:\D365-Operations\logs\en-US
```

The following example uses a previously cloned en-US repo and generates HTML files for en-US.

```dos
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\en-US" --externalText "(This is an external link)" --replaceUrl "https://docs.microsoft.com/en-us/dynamics365/supply-chain" --LogsDir D:\D365-Operations\logs\en-US
```

The following example clones the de-DE and en-US repos, and generates HTML files for de.

```dos
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\de" --repo "https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de" --externalText "(This is an external link)" --EnRepo "https://github.com/MicrosoftDocs/Dynamics-365-unified-Operations-public" --EnOut "D:\D365-Operations\en-us" --replaceUrl "https://docs.microsoft.com/de-de/dynamics365/supply-chain" --lng "de" --LogsDir D:\D365-Operations\logs\de
```

The following example uses the existing de-DE and en-US repos, and generates HTML files for de. If you use the existing de-DE repo, make sure that it's up to date.

```dos
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\de" --DoNotClone --externalText "(This is an external link)" --enOut "D:\D365-Operations\en-us" --replaceUrl "https://docs.microsoft.com/de-de/dynamics365/supply-chain" --lng "de" --LogsDir D:\D365-Operations\logs\de
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