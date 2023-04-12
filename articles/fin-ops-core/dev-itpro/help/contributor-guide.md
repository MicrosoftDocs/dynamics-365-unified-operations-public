---
title: Extend, customize, and collaborate on the Help (contains video)
description: This article provides tips and tricks for working with the GitHub repos and Markdown files for finance and operations apps.
author: edupont04
ms.date: 11/21/2022
ms.topic: article
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: edupont
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Operations
---

# Extend and collaborate on the Help

The source files for the Microsoft Help for finance and operations apps are available in public GitHub repositories (repos). Any solution provider can easily extend and customize the content for specific solutions. This article explains how to work with the GitHub repos and Markdown files.

For information about how to create Markdown files in GitHub repos, see the [Docs contributor guide](/contribute/). For information about how to deploy custom Help, see [Custom Help overview](custom-help-overview.md).

## Contribute to the content

One benefit of GitHub is that you can contribute to the core content that the Microsoft team provides in the [MicrosoftDocs/Dynamics-365-Unified-Operations-public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public) repo. For example, you have a new article that you think will be helpful to other users, or you have a correction to an existing article. If you want to contribute to the Dynamics-365-Unified-Operations-public repo, you can create a *pull request* from your repo to the Dynamics-365-Unified-Operations-public repo. The Microsoft team will then review the request and include your changes as appropriate.

You can also contribute and make edits to the existing documentation. To get started, select the **Edit** button (pencil symbol) in a article. The following video shows how you can contribute to the Microsoft documentation.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE36liB]

> [!NOTE]
> Microsoft currently accepts pull requests only to the Dynamics-365-Unified-Operations-public repo.

## Extend and customize Microsoft source content from GitHub repos

Microsoft provides a repo in GitHub for the source content. The [Dynamics-365-Unified-Operations-public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public) repo contains the source content in English (United States).

When Microsoft publishes an update to the content, the *main* branch in the repo is updated. The source repo is updated weekly. If you fork the Microsoft repo, you can choose to update your fork with updates from the Microsoft repo on a monthly basis or less often, depending on your preferred work processes. The GitHub platform and tooling will help you manage any potential merge conflicts if you change files that Microsoft has also changed. For more information, see [Set up Git repository locally for documentation](/contribute/get-started-setup-local) in the Docs authoring guide and [Fork a repo](https://help.github.com/articles/fork-a-repo/) in the Help for GitHub.

<!--For guidance about what the Microsoft-provided content is all about, see [User Assistance Model](../user-assistance.md).-->

### Get started with GitHub

To join Microsoft in the world of GitHub and Markdown, you must be familiar with some new terminology and tools. The following list outlines the main steps, but you can find additional content, tools, and ideas in the [GitHub documentation](https://help.github.com/en/github) and other forums.

1. Sign up for GitHub.

    For more information, see [GitHub account setup](/contribute/get-started-setup-github) and [Install content authoring tools](/contribute/get-started-setup-tools) in the Docs contributor guide.

2. Fork the appropriate repo.

    If you want to supplement Microsoft's content, then you do not need a fork of our repo. If you will customize Microsoft content using the MarkDown format, we recommend that you manually fork the relevant repo and use your favorite MarkDown editor. For more information, see [Set up Git repository locally for documentation](/contribute/get-started-setup-local) and [Git and GitHub essentials for Docs](/contribute/git-github-fundamentals) in the Docs contributor guide.

    > [!TIP]
    > You aren't required to make your GitHub repos public. When you fork a public repo, in the settings for the new repo, you can specify whether the repo is public, private, or available only to specific GitHub accounts.

### Markdown format

The syntax that is used to format text for topics is named [Markdig](https://github.com/lunet-io/markdig) Flavored Markdown. This syntax complies with [CommonMark](https://commonmark.org/). To learn more about how to work with Markdown, see [Getting started with writing and formatting on GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/).

You can convert content from Microsoft Word to Markdown by using open-source tools or other tools. In this way, you can easily recycle content.


### Get updates from Microsoft

Microsoft makes frequent changes to the content, and those changes show up in the public GitHub repos. The base repo, MicrosoftDocs/Dynamics-365-Unified-Operations-public, is updated weekly. However, you can choose to get updates monthly, twice a year, or once a year, for example. The translation repos are updated less frequently, so you might want a monthly schedule or less frequent updates, as appropriate.  

## Translate the content

If your solution is available in more than one country or region, you will probably want to make the content available in multiple languages. There are lots of options for doing that. The following are a few examples.

* Create the content in multiple languages without using Microsoft's content.
* Create the content in one language, without using Microsoft's content, and then translate it. For example, by using the [Dynamics 365 Translation Service (DTS)](#dynamics-365-translation-service).
* Pull Microsoft's English (United States) language content from our MicrosoftDocs/Dynamics-365-Unified-Operations-public repo, customize the Markdown files, translate them, and then use a third-party tool or DocFX to build the HTML files.

    > [!NOTE]
    > DTS isn't an option for translating the content in this scenario because it doesn't support Markdown files.

### Dynamics 365 Translation Service

You can use the [Dynamics 365 Translation Service](../lifecycle-services/translation-service-overview.md) (DTS) to translate your own or the Microsoft-provided content into other languages. The service is hosted in Microsoft Dynamics Lifecycle Services (LCS), and currently supports translation of content in Word documents and HTML files. For more information, see [Translate documentation files](../lifecycle-services/use-translation-service-ua.md).

## See also

[Docs contributor guide](/contribute/)  
[Docs Authoring Pack for Visual Studio Code](/contribute/how-to-write-docs-auth-pack)  
[Getting started with writing and formatting on GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)  
[Visual Studio Code](https://code.visualstudio.com/)  
[Atom](https://atom.io/)  
[DocFx](https://dotnet.github.io/docfx/)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
