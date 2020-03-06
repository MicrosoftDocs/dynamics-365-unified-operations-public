---
# required metadata

title: Generate HTML files based on Microsoft's GitHub repos
description: This topic describes the HtmlFromRepoGenerator tool in the custom help toolkit for Finance and Operations apps. 
author: edupont04
manager: AnnBe
ms.date: 03/06/2020
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

# Custom Help Toolkit: The HTML From Repos Generator tool

[!include [banner](../includes/banner.md)]

The custom help toolkit includes the **HtmlFromRepoGenerator** tool that gets Microsoft's content in MarkDown format and prepares it for customization in HTML format.  

The tool can help automate how you get Microsoft's content and prepare it for customization and deployment to a custom help website.

## <a name="consoleapp"></a>Use the HtmlFromRepoGenerator tool to get MarkDown files and generate HTML files

HtmlFromRepoGenerator.exe provides functionality that supports the creation of custom Help based on source files from Microsoft. You can use HtmlFromRepoGenerator.exe to:

- Clone a Microsoft documentation repo

    If you already have a clone of the Microsoft repo, run HtmlFromRepoGenerator.exe without this command.

- Remove developer and administrator content from your clone of the Microsoft repo
- Update links to files that are no longer in the clone
- Update the **ms.locale** value to match the language options that are supported by the Finance and Operations client

    The client uses other language descriptors than the corresponding GitHub repos. For localized Help to be called, the language indicators in the content from GitHub must be changed so that they match how the client understands languages.
- Generate HTML files that can be used for publishing.

    The HTML files are in the **d365F-O** subfolder. The files are generated based on templates in the mstemplate.zip file that you also find in the GitHub repo <!--TODO -->. These templates are based on DocFx custom templates that you can customize for your own website. For more information, see [Introduction to DocFX Template System](https://dotnet.github.io/docfx/tutorial/intro_template.html).

- Compare a localized Microsoft repo to the en-US repo to identify discrepancies and update the links accordingly.

In the first version of the toolkit, this tool had the name ConsoleApp.exe but is now renamed.  

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
> The Microsoft repos contain many files, so the process takes several minutes. If you run the tol against several localization repos, the process takes longer.

The following example clones the en-US repo and generates HTML files for en-US.

```
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\en-US" --repo "https://github.com/MicrosoftDocs/Dynamics-365-unified-Operations-public" --externalText "(This is an external link)" --replaceUrl "https://docs.microsoft.com/en-us/dynamics365/supply-chain" --LogsDir D:\D365-Operations\logs\en-US
```

The following example uses the previously cloned en-US repo and generates HTML files for en-US.

```
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\en-US" --externalText "(This is an external link)" --replaceUrl "https://docs.microsoft.com/en-us/dynamics365/supply-chain" --LogsDir D:\D365-
Operations\logs\en-US
```

The following example clones both the de-DE and en-US repos, and generates HTML files for German.

```
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\de" --repo "https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de" --externalText "(This is an external link)" --EnRepo "https://github.com/MicrosoftDocs/Dynamics-365-unified-Operations-public" --EnOut "D:\D365-Operations\en-us" --replaceUrl "https://docs.microsoft.com/de-de/dynamics365/supply-chain" --lng "de" --LogsDir D:\D365-Operations\logs\de
```

The following example clones the de-DE repo, uses the existing en-US repo, and then generates HTML files for the *de* client locale.

```
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\de" --repo "https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de" --externalText "(This is an external link)" --EnOut "D:\D365-Operations\en-us" --replaceUrl "https://docs.microsoft.com/de-de/dynamics365/supply-chain" --lng "de" --LogsDir D:\D365-Operations\logs\de
```

The following example uses the existing de-DE and en-US repos, and then generates HTML files for German. Make sure that the de-DE repo is up to date if you use the existing repo.

```
HtmlFromRepoGenerator.exe --json articles/ --out "D:\D365-Operations\de" --DoNotClone --externalText "(This is an external link)" --enOut "D:\D365-Operations\en-us" --replaceUrl "https://docs.microsoft.com/de-de/dynamics365/supply-chain" --lng "de" --LogsDir D:\D365-Operations\logs\de
```

> [!IMPORTANT]
> Do not run HtmlFromRepoGenerator.exe repeatedly on a cloned repo, because the folder that contains the files from your clone of the repository is already modified the first time you run the tool. This means that the files no longer contain any links that must be replaced. If you must rerun the tool, either let the tool re-clone the repo, or make sure that all local changes are reverted.

<!--TODO: Figure out what that alert really means. What is a one-off task and what is a regular task?-->

## See also

[Custom Help Toolkit](custom-help-toolkit.md)  
[Custom Help Overview](custom-help-websites.md)  
[Deploying custom help to Azure](walkthrough-help-azure.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)  
