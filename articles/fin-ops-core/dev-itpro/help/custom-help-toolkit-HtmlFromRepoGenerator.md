---
# required metadata

title: Generate HTML files from the contents of a Microsoft GitHub repository
description: This topic describes the HtmlFromRepoGenerator tool in the custom help toolkit for Finance and Operations apps. 
author: edupont04
manager: AnnBe
ms.date: 03/10/2020
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

# Custom Help Toolkit: The HtmlFromRepoGenerator tool

[!include [banner](../includes/banner.md)]

The custom help toolkit includes the **HtmlFromRepoGenerator** tool that gets Microsoft's content in MarkDown format and converts it to HTML format in preparation for customization.  

## <a name="consoleapp"></a>Use the HtmlFromRepoGenerator tool to get MarkDown files and generate HTML files

HtmlFromRepoGenerator.exe provides functionality that supports the creation of custom Help based on source files from Microsoft. You can use HtmlFromRepoGenerator.exe to:

- Clone a Microsoft documentation repo
- Remove developer and administrator content from your clone of the Microsoft repo
- Update links to files that are no longer in the clone
- Update the **ms.locale** value to match the language options that are supported by the Finance and Operations client

    The client uses language descriptors that are different from the language descriptors used in the corresponding GitHub repos. For localized Help to be called, the language indicators in the content from GitHub must be changed so that they match how the client understands languages. See [Language and locale descriptors in across product and Help](language-locale.md) for more information.
- Generate HTML files that can be used for publishing.

    The HTML files will be generated in the **d365F-O** subfolder. The files are generated based on stylesheets and templates that are part of the tool. For more information, see [Modifying the styling of the generated HTML files](#modifying-the-styling-of-the-generated-html-files).

- Compare a localized Microsoft repo to the en-US repo to identify discrepancies and update the links accordingly.

In the first version of the toolkit, this tool had the name ConsoleApp.exe.  

### Syntax

Here is the syntax for HtmlFromRepoGenerator.exe:  

```
HtmlFromRepoGenerator.exe --Json <Articles/> --Out <path> --ExternalText <text> [--DoNotClone <true|false>] [--Repo <URL>] [--RemoveGitFolder <true|false>] [--ReplaceUrl <URL>] [--LogsDir <.\logs>] [--EnRepo <URL>] [--EnOut <path>] [--Lng <language code>] [--?[--]]
```

The following table provides an explanation of the parameters:

|Parameter   |Description  |
|------------|-------------|
|Json |Specifies a relative path for the location of the docfx.json file. In Microsoft documentation repos, this location is typically ```articles/```. |
|Out |Specifies the folder where your existing clone is, or the folder to clone the repo to. If you run HtmlFromRepoGenerator to clone a repo, this folder must not already exist. Use the language name as the folder name as described in [Language and locale descriptors in across product and Help](language-locale.md). |
|ExternalText |Specifies text that must be added to the updated links if HtmlFromRepoGenerator must replace the original links.|
|DoNotClone |Set this parameter when you run the tool against previously cloned repos. |
|Repo |Specifies the repo URL. This parameter is not required if you run the tool based on a previously cloned repo. Examples of Microsoft documentation repo URLs include *https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public* for English (US) and *https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de* for German (Germany).|
|RemoveGitFolder|Specifies whether to remove the `.git` folder.|
|ReplaceUrl|Specifies the URL must replace links between files when the target files are not present. This parameter is intended to be used to turn relative links into absolute links.|
|LogsDir|Specifies the folder to save logs files to.|

The following additional parameters are used when the tool is run against the localized Microsoft documentation repos:

|Parameter   |Description  |
|------------|-------------|
|EnRepo|Specifies the URL of the en-US repo. This parameter is not required if you run the tool based on a previously cloned repo. The Microsoft documentation repo URL for English (US) is [https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public).|
|EnOut|Specifies the folder where the en-US repo exists, or the folder that it must be cloned to. This folder must not already exist if you run the tool based on a previously cloned repo.|
|Lng|Specifies the language value to use for `ms.locale` metadata in the generated HTML files. The value must correspond to the value that is specified in the Finance and Operations client's language settings. If this parameter is not set, the tool uses en-US. For more information, see [Language and locale descriptors in across product and Help](language-locale.md).|
|Rtl|Set this parameter if the language uses right-to-left (RTL) formatting. Examples of RTL languages include Arabic and Hebrew.|

## Examples

> [!NOTE]
> The Microsoft repos contain many files, so the process takes several minutes. If you run the tool against multiple localization repos, the process takes longer.

The following example clones the en-US repo and generates HTML files for en-US.

```
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\en-US" --repo "https://github.com/MicrosoftDocs/Dynamics-365-unified-Operations-public" --externalText "(This is an external link)" --replaceUrl "https://docs.microsoft.com/en-us/dynamics365/supply-chain" --LogsDir D:\D365-Operations\logs\en-US
```

The following example uses a previously cloned en-US repo and generates HTML files for en-US.

```
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\en-US" --externalText "(This is an external link)" --replaceUrl "https://docs.microsoft.com/en-us/dynamics365/supply-chain" --LogsDir D:\D365-
Operations\logs\en-US
```

The following example clones both the de-DE and en-US repos, and generates HTML files for de.

```
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\de" --repo "https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de" --externalText "(This is an external link)" --EnRepo "https://github.com/MicrosoftDocs/Dynamics-365-unified-Operations-public" --EnOut "D:\D365-Operations\en-us" --replaceUrl "https://docs.microsoft.com/de-de/dynamics365/supply-chain" --lng "de" --LogsDir D:\D365-Operations\logs\de
```

The following example uses the existing de-DE and en-US repos, and then generates HTML files for de. Make sure that the de-DE repo is up to date if you use the existing repo.

```
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\de" --DoNotClone --externalText "(This is an external link)" --enOut "D:\D365-Operations\en-us" --replaceUrl "https://docs.microsoft.com/de-de/dynamics365/supply-chain" --lng "de" --LogsDir D:\D365-Operations\logs\de
```

> [!IMPORTANT]
> Do not run HtmlFromRepoGenerator.exe repeatedly on a previously-cloned repo. HtmlFromRepoGenerator modifies the links during processing, so running HtmlFromRepoGenerator more than once on the same content will result in incorrect links. If you want to rerun HtmlFromRepoGenerator, either use HtmlFromRepoGenerator to create a new clone of the repo, or revert all local changes to your existing clone.

## Modifying the styling of the generated HTML files

The tool generates the HTML files based a set of predefined templates. In most cases you can modify the stylesheets in the ```d365F-O\styles``` folder to modify the appearance of your content.

For advanced scenarios, you can modify the templates used by the HtmlFromRepoGenerator tool. The source files are included in the *SourceCode* folder in the GitHub repo, and the templates are in the *SourceCode\HtmlFromRepoGenerator\HtmlFromRepoGenerator\HtmlFromRepoGenerator\Resources* subfolder. If you modify the templates, you must rebuild HtmlFromRepoGenerator.exe. For more information, see [Introduction to DocFX Template System](https://dotnet.github.io/docfx/tutorial/intro_template.html).

## See also

[Custom Help Toolkit](custom-help-toolkit.md)  
[Custom Help Overview](custom-help-overview.md)  
[Deploying custom help to Azure](walkthrough-help-azure.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)  
