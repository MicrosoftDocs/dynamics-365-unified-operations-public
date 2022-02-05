---
title: Extend, customize, and collaborate on the Help (contains video)
description: This topic provides tips and tricks for working with the GitHub repos and Markdown files for Finance and Operations apps.
author: edupont04
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
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Operations
ms.date: 05/11/2020
ms.author: edupont
---

# Extend, customize, and collaborate on the Help

The source files for the Microsoft Help for Finance and Operations apps are available in public GitHub repositories (repos). Any solution provider can easily extend and customize the content for specific solutions. This topic explains how to work with the GitHub repos and Markdown files.

For information about how to create Markdown files in GitHub repos, see the [Docs contributor guide](/contribute/). For information about how to deploy custom Help, see [Custom Help overview](custom-help-overview.md).

## Contribute to the content

One benefit of GitHub is that you can contribute to the core content that the Microsoft team provides in the [MicrosoftDocs/Dynamics-365-Unified-Operations-public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public) repo. For example, you have a new topic that you think will be helpful to other users, or you have a correction to an existing topic. If you want to contribute to the Dynamics-365-Unified-Operations-public repo, you can create a *pull request* from your repo to the Dynamics-365-Unified-Operations-public repo. The Microsoft team will then review the request and include your changes as appropriate.

You can also contribute and make edits to the existing documentation. To get started, select the **Edit** button (pencil symbol) in a topic. The following video shows how you can contribute to the Microsoft documentation.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE36liB]

> [!NOTE]
> Microsoft currently accepts pull requests only to the Dynamics-365-Unified-Operations-public repo, not to the language-specific repos. If you have feedback about translations, you can report a GitHub issue in the relevant repo.

## Extend and customize Microsoft source content from GitHub repos

Microsoft uses separate repos in GitHub for the source content and for each language that Microsoft translates content into. The [Dynamics-365-Unified-Operations-public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public) repo contains the source content in English (United States). If you want to access the content in other languages, the names follow the pattern **Dynamics-365-Operations.\<language\>-\<country\>**. For example, the version for German (Germany) is named [Dynamics-365-Operations.de-de](https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de).

When Microsoft publishes an update to the content, the *main* branch in the corresponding GitHub repo is updated. The source repo is updated weekly. However, the related language-specific repos are updated less often. The frequency depends on when new translations are made available. If you fork one of the Microsoft repos, you can choose to update your fork with updates from the Microsoft repo on a monthly basis or less often, depending on your preferred work processes. The GitHub platform and tooling will help you manage any potential merge conflicts if you change files that Microsoft has also changed. For more information, see [Set up Git repository locally for documentation](/contribute/get-started-setup-local) in the Docs authoring guide and [Fork a repo](https://help.github.com/articles/fork-a-repo/) in the Help for GitHub.

> [!IMPORTANT]
> In April 2021, the default branch in the public source repo has been renamed from *live* to *main*. If you have any scripts that rely on the *live* branch, please update them to rely on *main* instead. The default branches in the language-specific repos will be renamed later.

> [!TIP]
> If you just want to get the Microsoft content as it is, you don't have to be familiar with GitHub. For more information, see the [Get the content without a GitHub account](#get-the-content-without-a-github-account) section of this topic. However, if you want to extend or customize the Microsoft content, we recommend that you join Microsoft on GitHub.

<!--For guidance about what the Microsoft-provided content is all about, see [User Assistance Model](../user-assistance.md).-->

### Get started with GitHub

To join Microsoft in the world of GitHub and Markdown, you must be familiar with some new terminology and tools. The following list outlines the main steps, but you can find additional content, tools, and ideas in the [GitHub documentation](https://help.github.com/en/github) and other forums.

1. Sign up for GitHub.

    For more information, see [GitHub account setup](/contribute/get-started-setup-github) and [Install content authoring tools](/contribute/get-started-setup-tools) in the Docs contributor guide.

2. Fork the appropriate repo.

    To extend and customize Microsoft content for a custom Help solution, you must create a fork of the repo. If you want to customize Microsoft content in Markdown format, we recommend that you manually fork the relevant repo and use your favorite Markdown editor. For more information, see [Set up Git repository locally for documentation](/contribute/get-started-setup-local) and [Git and GitHub essentials for Docs](/contribute/git-github-fundamentals) in the Docs contributor guide.

    > [!TIP]
    > You aren't required to make your GitHub repos public. When you fork a public repo, in the settings for the new repo, you can specify whether the repo is public, private, or available only to specific GitHub accounts.

### Markdown format

The syntax that is used to format text for topics is named [Markdig](https://github.com/lunet-io/markdig) Flavored Markdown. This syntax complies with [CommonMark](https://commonmark.org/). To learn more about how to work with Markdown, see [Getting started with writing and formatting on GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/).

You can convert content from Microsoft Word to Markdown by using open-source tools or other tools. In this way, you can easily recycle content.


### Get updates from Microsoft

Microsoft makes frequent changes to the content, and those changes show up in the public GitHub repos. The base repo, MicrosoftDocs/Dynamics-365-Unified-Operations-public, is updated weekly. However, you can choose to get updates monthly, twice a year, or once a year, for example. The translation repos are updated less frequently, so you might want a monthly schedule or less frequent updates, as appropriate.  

When you decide that it's time to get the latest version of the content from Microsoft, you can use the Git command line or GitHub Desktop. The Help for GitHub provides [an example that shows how this process works in GitBash](https://help.github.com/en/articles/merging-an-upstream-repository-into-your-fork). In GitHub Desktop, you use the **Merge into current branch** command to pull changes from the origin into your fork.

If your solution is available in more than one country or region, you will probably want to make the content available in multiple languages. Although Microsoft has a GitHub repo for each supported language, the configuration files are available only in the English (United States) version of the base repo, MicrosoftDocs/Dynamics-365-Unified-Operations-public. You can use the HtmlFromRepoGenerator tool from the [Custom Help Toolkit](custom-help-toolkit.md) to get the files.

Because the Microsoft repos are public, you don't have to have a valid GitHub account to get the content. However, we recommend that, at a minimum, your organization have a system account that has access to GitHub.

For more information, see [Custom Help Toolkit](custom-help-toolkit.md).

## Get the content without a GitHub account

If you don't want to collaborate with Microsoft on the content, you can get the latest version of the content from GitHub even if you don't have a GitHub account. For example, you can just clone the relevant GitHub repo. A GitHub account isn't required to clone a repo. Because the Microsoft repos are public, anyone can always access them.

## Translate the content

You can use the [Dynamics 365 Translation Service](../lifecycle-services/translation-service-overview.md) (DTS) to translate your own or the Microsoft-provided content into other languages. The service is hosted in Microsoft Dynamics Lifecycle Services (LCS), and currently supports translation of content in Word documents and HTML files. For more information, see [Translate documentation files](../lifecycle-services/use-translation-service-ua.md).

## See also

[Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)  
[Docs contributor guide](/contribute/)  
[Docs Authoring Pack for Visual Studio Code](/contribute/how-to-write-docs-auth-pack)  
[Getting started with writing and formatting on GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)  
[Visual Studio Code](https://code.visualstudio.com/)  
[Atom](https://atom.io/)  
[DocFx](https://dotnet.github.io/docfx/)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
