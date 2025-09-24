---
title: Contribute to the Help
description: Learn about tips and tricks for working with the GitHub repos and Markdown files for finance and operations apps.
author: edupont04
ms.author: edupont
ms.topic: article
ms.date: 07/17/2024
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Operations
---

# Contribute to the Help

This article describes how to contribute to our content in our [MicrosoftDocs/Dynamics-365-Unified-Operations-public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public) GitHub repo.

 For information about how to deploy custom Help, see [Custom Help overview](custom-help-overview.md).

## Contribute to the content

One benefit of GitHub is that you can contribute to the core content that the Microsoft team provides in the [MicrosoftDocs/Dynamics-365-Unified-Operations-public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public) repo. For example, you have a new article that you think will be helpful to other users, or you have a correction to an existing article. If you want to contribute to the Dynamics-365-Unified-Operations-public repo, you can create a *pull request* from your repo to the Dynamics-365-Unified-Operations-public repo. The Microsoft team will then review the request and include your changes as appropriate.

You can also contribute and make edits to the existing documentation. To get started, select the **Edit** button (pencil symbol) in a article. The following video shows how you can contribute to the Microsoft documentation.

> [!VIDEO https://learn-video.azurefd.net/vod/player?id=beb8146a-fbc8-4dbb-a78d-2a38039e6981]

> [!NOTE]
> Microsoft currently accepts pull requests only to the source files in English (US).

Learn how to get started with Markdown files in GitHub repos in the [Microsoft Learn contributor guide](/contribute/content/how-to-write-overview). Find tips and tricks that are particular to Dynamics 365 documentation at [Contribute to Dynamics 365 documentation](/dynamics365/get-started/contribute).

> [!TIP]
> You aren't required to make your GitHub repos public. When you fork a public repo, in the settings for the new repo, you can specify whether the repo is public, private, or available only to specific GitHub accounts.

### Markdown format

The syntax that is used to format text for topics is named [Markdig](https://github.com/lunet-io/markdig) Flavored Markdown. This syntax complies with [CommonMark](https://commonmark.org/). To learn more about how to work with Markdown, see [Getting started with writing and formatting on GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/).

You can convert content from Microsoft Word to Markdown by using open-source tools or other tools. In this way, you can easily recycle content.

## Translate the content

If your solution is available in more than one country or region, you'll probably want to make the content available in multiple languages. There are lots of options for doing that. The following are a few examples:

* Create the content in multiple languages.
* Create the content in one language, and then translate it. For example, by using the [Dynamics 365 Translation Service (DTS)](#dynamics-365-translation-service).
* Pull Microsoft's English (United States) language content from our MicrosoftDocs/Dynamics-365-Unified-Operations-public repo, customize the Markdown files, translate them, and then use a third-party tool to build the HTML files.

    > [!NOTE]
    > DTS isn't an option for translating the Microsoft content because it doesn't support Markdown files.

### Dynamics 365 Translation Service

You can use the [Dynamics 365 Translation Service](../lifecycle-services/translation-service-overview.md) (DTS) to translate your content into other languages. The service is hosted in Microsoft Dynamics Lifecycle Services (LCS), and currently supports translation of content in Word documents and HTML files. For more information, see [Translate documentation files](../lifecycle-services/use-translation-service-ua.md).

## See also

[Microsoft Learn contributor guide](/contribute/)  
[Learn Authoring Pack for Visual Studio Code](/contribute/how-to-write-docs-auth-pack)  
[Getting started with writing and formatting on GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)  
[Visual Studio Code](https://code.visualstudio.com/)  
[Atom](https://atom.io/)  
[DocFx](https://dotnet.github.io/docfx/)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
