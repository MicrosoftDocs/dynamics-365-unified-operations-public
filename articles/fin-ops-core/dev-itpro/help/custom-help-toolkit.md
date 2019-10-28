---
# required metadata

title: Running the Custom Help Toolkit
description: This topic describes how you can extend the Microsoft Help to reflect your solution and then connect that to the Help pane in certain Dynamics 365 apps. 
author: edupont04
manager: AnnBe
ms.date: 10/28/2019
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

# Running the Custom Help Toolkit

[!include [banner](../includes/banner.md)]

XYZ

## ConsoleApp

ConsoleApp.exe is one of the tools that are provided in the content tools repo to support the custom Help solution (https://github.com/Microsoft/dynamics365f-o-custom-help). ConsoleApp.exe is used to:

- Clone a Microsoft documentation repo (unless you already cloned it).
- Remove developer and administrator content from the cloned repo.
- Update links to files that are no longer in the clone.
- Update the me.locale value to match the language options supported by Dynamics 365.

    Dynamics 365 Finance, Supply Chain Management, and Retail use different language descriptiors compared to the corresponding documentation repos on GitHub. For localized Help to be called, the language indicators of the content that has been downloaded from GitHub localized repos must be changed so that they match the language descriptors.
- Generate HTML files that can be used for publishing.
- When the tool is run against a localized Microsoft repo, compare that repo against the en-US repo to identify discrepancies and update the links accordingly.

Here is the syntax for ConsoleApp.exe:  

```
ConsoleApp.exe --Json <Articles/> --Out <path> --ExternalText <text> [--DoNotClone <true|false>] [--Repo 
<URL>] [--RemoveGitFolder <true|false>] [--ReplaceUrl <URL>] [--LogsDir <.\logs>] [--EnRepo <URL>] [--
EnOut <path>] [--Lng <language code>] [--?[-]] 
```

Here is an explanation of the parameters: 

|Parameter   |Description  |
|------------|-------------|
|Json |Specify a relative path for the location of the docfx.json file. In Microsoft documentation repos, this location is typically ```articles/```. |
|Out |Specify the folder where a repo already exists or the folder to clone the repo to. This folder should not exist if the repo is being cloned by the tool. Use the language name as a folder name (see Appendix A). |
|ExternalText |Specify text that should be added to the updated links, in cases where the original links are replaced by the tool.|
|DoNotClone |Use this parameter only when you run the tool against previously cloned repos |
|Repo |Specify the repo URL. This parameter isn’t required if you’re using a previously cloned repo. Examples of Microsoft documentation repo URLs include *https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public* for English (US) and *https://github.com/MicrosoftDocs/Dynamics-365-Operations.ar-sa* for Saudi Arabian.|
|RemoveGitFolder|Specify whether to remove the .git directory.|
|replace URL|Specify the URL that is used to replace links between files when those files aren't present. This parameter is intended to be used to turn relative links into absolute links.|
|LogsDir|Specify the location where the log files are placed.|

The following additional parameters are used when the tool is run against the localized Microsoft documentation repos:

|Parameter   |Description  |
|------------|-------------|
|EnRepo|Specify the URL of the en-US repo. This parameter isn’t required if the repo is already cloned. The Microsoft documentation repo URL for English (US) is *https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public*.|
|EnOut|Specify the folder where the en-US repo exists or the folder that it should be cloned to. This folder should not exist if the repo is being cloned by the tool.|
|Lng|Specify the language value to use for ms.locale metadata in the resulting HTML files. The value must correspond to the value that is used in the Finance and Operations client’s language setting that the Help content is intended for. If this parameter is omitted, en-US is used as a default value. Use the Finance and Operations language name as a parameter (see Appendix A).|
|Rrl|Include this parameter if the intended language uses right-to-left (RTL) formatting. Examples of RTL languages include Arabic and Hebrew.|

### Examples

The following example clones the en-US repo and generates HTML files for en-US.

```
ConsoleApp.exe --json articles/ --out "D:\D365-Operations\en-US" --repo 
"https://github.com/MicrosoftDocs/Dynamics-365-unified-Operations-public" --externalText "(This is an external link)" --replaceUrl "https://docs.microsoft.com/en-us/dynamics365/supply-chain" --LogsDir D:\D365-Operations\logs\en-US 
```

The following example uses the previously cloned en-US repo and generates HTML files for en-US.

```
ConsoleApp.exe --json articles/ --out "D:\D365-Operations\en-US" --externalText "(This is an external link)" --replaceUrl "https://docs.microsoft.com/en-us/dynamics365/supply-chain" --LogsDir D:\D365-
Operations\logs\en-US
```

The following example clones both the de-DE and en-US repos, and generates HTML files for German.

```
ConsoleApp.exe --json articles/ --out "D:\D365-Operations\de" --repo "https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de" --externalText "(This is an external link)" --EnRepo "https://github.com/MicrosoftDocs/Dynamics-365-unified-Operations-public" --EnOut "D:\D365-Operations\en-us" --replaceUrl "https://docs.microsoft.com/de-de/dynamics365/supply-chain" --lng "de" --LogsDir D:\D365-Operations\logs\de
```

The following example clones the de-DE repo, uses the existing en-US repo, and then generates HTML files for de.

```
ConsoleApp.exe --json articles/ --out "D:\D365-Operations\de" --repo "https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de" --externalText "(This is an external link)" --EnOut "D:\D365-Operations\en-us" --replaceUrl "https://docs.microsoft.com/dede/dynamics365/supply-chain" --lng "de" --LogsDir D:\D365-Operations\logs\de
```

The following example uses the existing de-DE and en-US repos, and then generates HTML files for German. Make sure that the de-DE repo is up to date if you’re using the existing repo.

```
ConsoleApp.exe --json articles/ --out "D:\D365-Operations\de" --DoNotClone --externalText "(This is an external link)" --enOut "D:\D365-Operations\en-us" --replaceUrl "https://docs.microsoft.com/dede/dynamics365/supply-chain" --lng "de" --LogsDir D:\D365-Operations\logs\de 
```

> [!IMPORTANT]
> ConsoleApp.exe should not be run repeatedly on the repo, because the folder that contains repository files is already modified. Therefore, the files no longer contain the correct links that must be replaced. If you must rerun the tool, either let the tool re-clone the repo, or make sure that all local changes are reverted.

<!--TODO: Figure out what that alert really means. What is a one-off task and what is a regular task?-->

## Use the Convert HTML to JSON tool to generate JSON files

The Convert HTML to JSON tool transforms HTML files into JSON files that you can then add to the Azure Search service that will generate context-sensitive links to your Help content.  

When you run the Convert HTML to JSON tool, you must specify the location of the HTML files with your Help content, and you must specify the destination path.  


## See also

[Deploying custom Help](deploy.md)  
[Connect a custom help site](../../fin-ops/get-started/help-custom.md)  