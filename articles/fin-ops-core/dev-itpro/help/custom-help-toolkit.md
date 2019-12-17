---
# required metadata

title: Custom Help Toolkit
description: This topic describes the components in the custom help toolkit for Finance and Operations apps. 
author: edupont04
manager: AnnBe
ms.date: 12/17/2019
ms.topic: article
ms.service: dynamics-ax-platform

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

# Custom Help Toolkit

[!include [banner](../includes/banner.md)]

Microsoft has published a GitHub repository with scripts and tools that can help you prepare content so that it can be accessed from the Help pane in the client that is used by the finance and operations apps. This way, users of custom solutions that are based on Dynamics 365 Finance, Supply Chain Management, Retail, or Talent can have access to context-sensitive Help.  

The toolkit is available at [https://github.com/microsoft/dynamics365f-o-custom-help/](https://github.com/microsoft/dynamics365f-o-custom-help/) and provides the following tools as well as the source code for the tools:

- ConsoleApp.exe

- run_ax2012.ps1 PowerShell script

- HTML Locale tool

- Convert HTML to JSON tool

- AzureSearchCustomHelp solution for Visual Studio

- HelppaneOption project for Visual Studio

- REST API index creation scripts

Each tool is described in the following sections.

## <a name="consoleapp"></a>Use the ConsoleApp to get MarkDown files and generate HTML files

ConsoleApp.exe provides functionality that supports the creation of custom Help based on source files from Microsoft. It is available from [the content tools repo](https://github.com/microsoft/dynamics365f-o-custom-help/tree/master/docfx%20scripts). You can use ConsoleApp.exe to:

- Clone a Microsoft documentation repo

    If you already have a clone of the Microsoft repo, your can run ConsoleApp without this command.

- Remove developer and administrator content from your clone of the Microsoft repo.
- Update links to files that are no longer in the clone.
- Update the **ms.locale** value to match the language options that are supported by the Finance and Operations client.

    The Finance and Operations client uses different language descriptors compared to the corresponding documentation repos on GitHub. For localized Help to be called, the language indicators of the content that has been downloaded from GitHub localized repos must be changed so that they match the language descriptors of the Finance and Operations client.
- Generate HTML files that can be used for publishing.
- Compare a localized Microsoft repo to the en-US repo to identify discrepancies and update the links accordingly.

Here is the syntax for ConsoleApp.exe:  

```
ConsoleApp.exe --Json <Articles/> --Out <path> --ExternalText <text> [--DoNotClone <true|false>] [--Repo <URL>] [--RemoveGitFolder <true|false>] [--ReplaceUrl <URL>] [--LogsDir <.\logs>] [--EnRepo <URL>] [--EnOut <path>] [--Lng <language code>] [--?[-]]
```

Here is an explanation of the parameters:

|Parameter   |Description  |
|------------|-------------|
|Json |Specify a relative path for the location of the docfx.json file. In Microsoft documentation repos, this location is typically ```articles/```. |
|Out |Specify the folder where your existing clone is, or the folder to clone the repo to. If you run ConsoleApp to clone a repo, this folder must not already exist. Use the language name as the folder name as described in [Language and locale descriptors in across product and Help](language-locale.md). |
|ExternalText |Specify text that must be added to the updated links if ConsoleApp must replace the original links.|
|DoNotClone |Set this parameter when you run the tool against previously cloned repos. |
|Repo |Specify the repo URL. This parameter is not required if you are using a previously cloned repo. Examples of Microsoft documentation repo URLs include *https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public* for English (US) and *https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de* for German (Germany).|
|RemoveGitFolder|Specify whether to remove the .git folder.|
|ReplaceUrl|Specify the URL that is used to replace links between files when those files are not present. This parameter is intended to be used to turn relative links into absolute links.|
|LogsDir|Specify the folder to save logs files to.|

The following additional parameters are used when the tool is run against the localized Microsoft documentation repos:

|Parameter   |Description  |
|------------|-------------|
|EnRepo|Specify the URL of the en-US repo. This parameter is not required if the repo is already cloned. The Microsoft documentation repo URL for English (US) is [https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public).|
|EnOut|Specify the folder where the en-US repo exists or the folder that it should be cloned to. This folder should not exist if the repo is being cloned by the tool.|
|Lng|Specify the language value to use for ms.locale metadata in the resulting HTML files. The value must correspond to the value that is used in the Finance and Operations client’s language setting that the Help content is intended for. If this parameter is omitted, en-US is used as a default value. Use the Finance and Operations language name as a parameter. For more information, see [Language and locale descriptors in across product and Help](language-locale.md).|
|Rtl|Set this parameter if the language uses right-to-left (RTL) formatting. Examples of RTL languages include Arabic and Hebrew.|

### Examples

The following example clones the en-US repo and generates HTML files for en-US.

```
ConsoleApp.exe --json articles/ --out "D:\D365-Operations\en-US" --repo "https://github.com/MicrosoftDocs/Dynamics-365-unified-Operations-public" --externalText "(This is an external link)" --replaceUrl "https://docs.microsoft.com/en-us/dynamics365/supply-chain" --LogsDir D:\D365-Operations\logs\en-US
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

The following example clones the de-DE repo, uses the existing en-US repo, and then generates HTML files for the *de* client locale.

```
ConsoleApp.exe --json articles/ --out "D:\D365-Operations\de" --repo "https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de" --externalText "(This is an external link)" --EnOut "D:\D365-Operations\en-us" --replaceUrl "https://docs.microsoft.com/de-de/dynamics365/supply-chain" --lng "de" --LogsDir D:\D365-Operations\logs\de
```

The following example uses the existing de-DE and en-US repos, and then generates HTML files for German. Make sure that the de-DE repo is up to date if you use the existing repo.

```
ConsoleApp.exe --json articles/ --out "D:\D365-Operations\de" --DoNotClone --externalText "(This is an external link)" --enOut "D:\D365-Operations\en-us" --replaceUrl "https://docs.microsoft.com/de-de/dynamics365/supply-chain" --lng "de" --LogsDir D:\D365-Operations\logs\de
```

> [!IMPORTANT]
> ConsoleApp.exe should not be run repeatedly on a cloned repo, because the folder that contains the files from your clone of the repository is already modified. Therefore, the files no longer contain the correct links that must be replaced. If you must rerun the tool, either let the tool re-clone the repo, or make sure that all local changes are reverted.

<!--TODO: Figure out what that alert really means. What is a one-off task and what is a regular task?-->

## <a name="htmllocale"></a>Use the HTML Locale Changer tool to align locales

The **HTML Locale Changer** tool can update your HTML files with a new value for *ms.locale*. For example, if you have HTML files for German (Germany) and you want to make the same content available in German (Austria), then you can run the tool to change the setting from *ms.locale: de-de* to *ms.locale:de-at*.

<!--TODO: Examples-->

## <a name="json"></a>Use the ConvertHtmlToJson tool to generate JSON files

[The ConvertHtmlToJson tool](https://github.com/microsoft/dynamics365f-o-custom-help/tree/master/Help%20Pane%20extension) transforms HTML files into JSON files that you can then add to the Azure Search service that will generate context-sensitive links to your Help content.  

The JSON files include metadata that is used by the indexer to identify which form and which language the target Help page is intended for.  

When you run the ConvertHtmlToJson tool, you must specify the location of the HTML files with your Help content, and you must specify the destination path.  

<!--TODO: Examples?-->

## <a name="helppane"></a>Use the development environment to extend the Help pane

The **Help Pane extension** folder of the toolkit contains the **AzureSearchCustomHelp** solution that you can open in the Finance and Operations development environment. The same folder also contains the **HelppaneOption.axpp** project that you can then import into the solution in Visual Studio.  

For an example of how to extend the Help, see [Connect your Help website with the Help pane](deploy.md#extendhelppane).  

## See also

[Deploying Custom Help](deploy.md)  
[Example of Deploying Custom Help on Azure](walkthrough-help-azure.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)  
