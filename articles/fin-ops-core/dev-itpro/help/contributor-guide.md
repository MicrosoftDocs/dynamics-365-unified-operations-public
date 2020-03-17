---
title: Extend, customize, collaborate on the Help
description: Tips and tricks for working with the GitHub repos and MarkDown files for Finance and Operations apps.
author: edupont04
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
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Operations
ms.date: 03/17/2020
ms.author: edupont
---

# Extend, customize, and collaborate on the Help

The source files for Microsoft's Help for Finance and Operations apps are available in public GitHub repos. Any solution providers can easily extend and customize the content for specific solutions. In this section, you can learn about working with the GitHub repos and MarkDown files.  

For information about authoring MarkDown files in GitHub repos, see the [Docs Contributor Guide](/contribute/). For information about deploying custom Help, see [Custom Help Overview](custom-help-overview.md).  

## Contribute to the content

A benefit of GitHub is the ability for you to contribute to the core content that the Microsoft team provides in the Dynamics-365-Unified-Operations-public repo. For example, you have a new article that you think would be beneficial to others, or you have a correction to an existing article. If you would like to contribute to the MicrosoftDocs/Dynamics-365-Unified-Operations-public repo, you can create a *pull request* from your repo to the MicrosoftDocs/Dynamics-365-Unified-Operations-public repo. The Microsoft team will then review the request and include the changes as appropriate.

You can also contribute and make edits to the existing documentation. To get started, click the **Edit** (pencil) button on an article. The following video shows how you can contribute to our documentation.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE36liB]

> [!NOTE]
> Microsoft currently only accepts pull requests to the *Dynamics-365-Unified-Operations-public* repo, not the language-specific repos. If you have feedback about translations, you can report a GitHub issue in the relevant repo.

## Extend and customize Microsoft's source content from GitHub repos

Microsoft uses separate repos in GitHub for the source content and each of the languages that Microsoft translates to. The [Dynamics-365-Unified-Operations-public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public) repo contains the source content in English (US). If you want access to the content in other languages, the names follow this pattern: ```Dynamics-365-Operations.\<language>-\<country>```, such as [Dynamics-365-Operations.de-de](https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de) for the German version.  

When Microsoft publishes an update to the content, the *live* branch in the corresponding GitHub repo is updated. The source repo is updated weekly. The related language-specific repos are updated less frequently, based on when new translations are made available. If you fork one of our repos, you can choose to update your fork with updates from the Microsoft repo on a monthly basis or less frequently, depending on your preferred work processes. The GitHub platform and tooling will help you manage any potential merge conflicts if you have made changes to files that Microsoft has also changed. For more information, see [Set up Git repository locally for documentation](/contribute/get-started-setup-local) in the Docs Authoring Guide and [Fork a repo](https://help.github.com/articles/fork-a-repo/) in the Help for GitHub.  

> [!TIP]
> You do not have to get acquainted with GitHub if you just want to get the Microsoft content as-is. For more information, see the [Getting by without GitHub](#get-the-content-without-a-github-account) section. However, if you want to extend or customize the Microsoft content, we recommend that you join us in GitHub.

<!--For guidance about what the Microsoft-provided content is all about, see [User Assistance Model](../user-assistance.md).-->

### Get started with GitHub

To join Microsoft in the world of GitHub and MarkDown, there are new terminology and tools to get used to. The following list outlines the main steps, but you can find additional content, tools, and ideas in the [GitHub documentation](https://help.github.com/en/github) and other forums.

1. Sign up for GitHub

    For more information, see [GitHub account setup](/contribute/get-started-setup-github) and [Install content authoring tools](/contribute/get-started-setup-tools) in the Docs contributor guide.

2. Fork the appropriate repo

    To extend and customize Microsoft's content for a custom Help solution, you must create a fork of the repo. If you want to customize Microsoft's content in MarkDown format, we recommend that you fork the relevant repo manually and author using your favorite MarkDown editor. For more information, see [Set up Git repository locally for documentation](/contribute/get-started-setup-local) and [Git and GitHub essentials for Docs](/contribute/git-github-fundamentals) in the Docs contributor guide.

    > [!TIP]
    > You are not required to make your GitHub repos public. When you fork a public repo, you can specify in the settings for the new repo if the repo is public, private, or available only to specific GitHub accounts.

### Markdown format

Articles use a syntax for formatting text called [Markdig](https://github.com/lunet-io/markdig) Flavored Markdown, which is [CommonMark](https://commonmark.org/) compliant. To learn more about working with markdown, see [Getting started with writing and formatting on GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/).

You can convert content from Word to MarkDown using open-source tools or other tools for easy recycling.  

> [!IMPORTANT]
> The [Writage](https://writage.com/) plugin for Word can be very helpful for converting existing content to MarkDown, but we recommend that you do not use it to edit MarkDown files in Word. When you save the MarkDown file, all metadata tags and some of the formatting is erased.

### Get updates from Microsoft

Microsoft makes frequent changes to the content, and those changes show up in the public GitHub repos. The base repo, MicrosoftDocs/Dynamics-365-Unified-Operations-public, is updated weekly, and the translations are updated monthly. But you can choose to get updates monthly, twice a year, or once a year, for example.  

When you decide it is time to get the latest version of the content from Microsoft, you can do that using the Git command line or GitHub Desktop. In the Help for GitHub, you can see [an example of how this works in GitBash](https://help.github.com/en/articles/merging-an-upstream-repository-into-your-fork). In GitHub Desktop, you use the *Merge into current branch* menu item to pull changes from the origin into your fork.  

However, if your solution is available in more than one country, then you are likely to want to make content available in multiple languages. Microsoft has a GitHub repo for each supported language, but the configuration files are only available in the English (US) source repo, MicrosoftDocs/Dynamics-365-Unified-Operations-public. Use the **HtmlFromRepoGenerator** tool from the [Custom Help Toolkit](custom-help-toolkit.md) to get the files.  

Because the Microsoft repos are public, you do not need a valid GitHub account in order to get the content. However, we recommend that your organization has a system account with access to GitHub at a minimum.  

For more information, see [Custom Help Toolkit](custom-help-toolkit.md).  

## Get the content without a GitHub account

If you do not want to collaborate with Microsoft on the content, you can get the latest version of the content from GitHub without a GitHub account. For example, get the latest content by simply cloning the relevant GitHub repo. Cloning a repo does not require a GitHub account - the Microsoft repos are public so that anyone can always get to them.

## Translate the content

You can use the [Dynamics 365 Translation Service](/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/translation-service-overview) (DTS) to translate your own or the Microsoft-provided content into other languages. The service is hosted in Lifecycle Services and currently supports translation of content in Word documents and HTML files. For more information, see [Translate documentation files](/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/use-translation-service-ua).  

## See also

[Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)  
[Docs Contributor Guide](/contribute/)  
[Docs Authoring Pack for Visual Studio Code](/contribute/how-to-write-docs-auth-pack)  
[Getting started with writing and formatting on GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)  
[Visual Studio Code](https://code.visualstudio.com/)  
[Atom](https://atom.io/)  
[DocFx](https://dotnet.github.io/docfx/)  
