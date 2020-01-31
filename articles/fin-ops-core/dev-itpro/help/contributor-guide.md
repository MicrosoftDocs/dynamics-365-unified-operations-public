---
title: Extend, customize, collaborate on the Help
description: Tips and tricks for working with the GitHub repos and MarkDown files for Finance and Operations apps.
author: edupont04
ms.custom: na
ms.reviewer: na
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
ms.date: 01/31/2020
ms.author: edupont
---

# Extend, Customize, and Collaborate on the Help

The source files for the Help for the base application is available in public GitHub repos so that you can easily extend and customize the content for your customers. In this section, you can learn about working with the GitHub repos and MarkDown files.  

You can also find guidance in the [Docs Contributor Guide](/contribute/).  

## Get content from the GitHub repos

There are different repos in GitHub for the source content and each of the languages that Microsoft translates to. The [Dynamics-365-Unified-Operations-public](https://github.com/MicrosoftDocs/Dynamics-365-Unified-Operations-public) repo contains the source content in English (US). If you want access to the content in other languages, navigate to the relevant repo - the names follow this pattern: ```Dynamics-365-Operations.\<language>-\<country>```, such as [Dynamics-365-Operations.de-de](https://github.com/MicrosoftDocs/Dynamics-365-Operations.de-de) for the German version.  

When Microsoft publishes an update to the content, the *live* branch in the corresponding GitHub repo is updated. The source repo is updated weekly, and the related language-specific repos are updated less frequently, based on when new translations are made available. If you fork one of our repos, you can choose to update your fork with updates from the Microsoft repo on a monthly basis or less frequently, depending on your preferred work processes. The GitHub platform and tooling will help you manage any potential merge conflicts if you have made changes to the same files as Microsoft has. For more information, see [Set up Git repository locally for documentation](/contribute/get-started-setup-local) in the Docs Authoring Guide and [Fork a repo](https://help.github.com/articles/fork-a-repo/) in the Help for GitHub.  

> [!TIP]
> You do not have to get acquainted with GitHub if you just want to get the Microsoft content in HTML format to deploy to a Help Server website, for example. For more information, see the [Getting by without GitHub](#get-the-content-without-a-github-account) section. However, if you want to extend or customize the Microsoft content, we recommend that you join us in GitHub.

<!--For guidance about what the Microsoft-provided content is all about, see [User Assistance Model](../user-assistance.md).-->

### Get started with GitHub

To join Microsoft in the world of GitHub and MarkDown, there are new terminology and tools to get used to. The following list outlines the main steps, but since this is all about open source, you can find additional content, tools, and ideas in the [GitHub documentation](https://help.github.com/en/github) and other forums.

1. Fork the right repo

    You cannot work directly in the [!INCLUDE [prodshort](../developer/includes/prodshort.md)] repos in the MicrosoftDocs GitHub org, such as the dynamics365smb-docs repo, so the first thing you need to do is create a fork of the repo under your GitHub account. A fork basically is copy of this repo that lets you work freely on the content without affecting the MicrosoftDocs/dynamics365smb-docs repo. For more information, see [Set up your GitHub account](/contribute/get-started-setup-github) and [Set up Git repository locally for documentation](/contribute/get-started-setup-local) in the Docs Authoring Guide.

    > [!TIP]
    > You are not required to make your GitHub repos public. When you fork a public repo, you can specify in the settings for the new repo if the repo is public, private, or available only to specific GitHub accounts.

2. Install GitHub Desktop (optional) and clone your forked repo.

    GitHub Desktop makes is easy to work and collaborate with repos locally from your own desktop. For more information, see [GitHub Desktop](https://desktop.github.com/).  

3. Get hold of your favorite MarkDown editor, and start making changes.

    The help content is stored in the *articles* folder of the repo. Articles use a syntax for formatting text called [Markdig](https://github.com/lunet-io/markdig) Flavored Markdown, which is [CommonMark](https://commonmark.org/) compliant. To learn more about working with markdown, see [Getting started with writing and formatting on GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/).

    If you want to work locally, you can edit using any text editor. Just save the file as a .md type. Here are a couple good tools that provide you with some nice features, including a preview of how the content will be rendered in HTML:

    - [Visual Studio Code](https://code.visualstudio.com/)

        Add the [Docs Authoring Pack for Visual Studio Code](/contribute/how-to-write-docs-auth-pack), which gives you spell checker, MarkDown validation, and many other productivity features  
    - [Atom](https://atom.io/)

        Atom has spell check and is good for managing many files

Internally at Microsoft, some authors use Code, others use Atom, and for light-weight work, we tend to just edit the content in the browser. You can find more guidance for how to get started with MarkDown in the [Docs Contributor Guide](/contribute/), which is published by the team that built the Docs.microsoft.com site where the Business Central team publishes their docs.

> [!IMPORTANT]
> The [Writate](https://writage.com/) plugin for Word can be very helpful for converting existing content to MarkDown, but we recommend that you do not use it to edit MarkDown files in Word. When you save the MarkDown file, all metadata tags and some of the formatting is erased.

<!--### What the GitHub repos contain

Microsoft's GitHub repos for Help contain the following folders:

- accountant

    Contains files that are relevant for Dynamics 365 — Accountant Hub
- business-central

    Contains files that are relevant for [!INCLUDE [prodshort](../developer/includes/prodshort.md)]
- invoicing

    Contains files that are relevant for Microsoft Invoicing
- media-source

    Contains source files for some of the pictures that are used in the [!INCLUDE [prodshort](../developer/includes/prodshort.md)] content

The repos also contain files in the root of the repos that are used internally by Microsoft for managing the content on the Docs.microsoft.com site and on GitHub. They are not relevant for the purpose of extending or customizing the content.
-->

### Get updates from Microsoft

Microsoft makes frequent changes to the content, and those changes show up in the public GitHub repos. The base repo, MicrosoftDocs/Dynamics-365-Unified-Operations-public, is updated weekly, and the translations are updated monthly. But you can choose to get updates monthly, twice a year, or once a year, for example. That is entirely up to you.  

When you decide it is time to get the latest version of the content from Microsoft, you can do that using GitBash or GitHub Desktop. In the Help for GitHub, you can see [an example of how this works in GitBash](https://help.github.com/en/articles/merging-an-upstream-repository-into-your-fork), but in GitHub Desktop, you simply use the *Merge into current branch* menu item to pull changes from the origin into your fork.  

However, if your solution is available in more than one country, then you are likely to want to make content available in multiple languages. Microsoft has a GitHub repo for each supported language, but the configuration files are only available in the English (US) source repo, MicrosoftDocs/Dynamics-365-Unified-Operations-public. To help you get the content that you need, you might want to run a PowerShell script that picks up content from the various GitHub repos.  

Because the Microsoft repos are public, you do not need a valid GitHub account in order to get the content. However, we recommend that your organization has a system account with access to GitHub at a minimum.  

For more information, see [Custom Help Toolkit](custom-help-toolkit.md).  

### Contributing

A benefit of GitHub is the ability for you to contribute to the core content that the Microsoft team provides in the dynamics365smb-docs repo. For example, you might have a new article that you think would be beneficial or you might have a correction to an existing article. If you would like to contribute to the MicrosoftDocs/dynamics365smb-docs repo, you create what is called a *pull request* from your repo to the MicrosoftDocs/dynamics365smb-docs repo. The Microsoft team will then review the request and include the changes as appropriate.

### Contribute to the documentation

You can contribute and make edits to the documentation. To get started, click the **Edit** (pencil) button on a topic. The following video shows how you can contribute to our documentation.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE36liB]

The [How to contribute to the Microsoft Dynamics 365 documentation](https://youtu.be/m5djioozRbg) video (shown above) is included in the Microsoft Dynamics 365 channel on YouTube.

> [!NOTE]
> Microsoft accepts pull requests to the *Dynamics-365-Unified-Operations-public* repo only, not the language-specific repos. If you have feedback about translations, you can report a GitHub issue in the relevant repo.

For example, to create a pull request to the MicrosoftDocs/Dynamics-365-Unified-Operations-public repo by using GitHub Desktop, do the following:

1. Commit the changes to your repo that you want to include in the pull request.
   Alternatively, here is the command for Git Shell:

   ```powershell
   git add -u
   git commit -m "update doc"
   git push
   ```

2. Choose **Sync** to push the changes up to your repo on GitHub.
3. When the sync is completed, choose **Pull Request**, make sure that the pull request points at the *live* branch, and then choose send **Pull Request**.

## Get the content without a GitHub account

If you do not want to collaborate with Microsoft on the content, you can get the latest version of the content from GitHub without a GitHub account. For example, you can get the latest content by simply downloading the content of the relevant GitHub repo, which you can do without a GitHub account - the Microsoft repos are public so that anyone can always get to them. Use the **HtmlFromRepoGenerator** tool from the [Custom Help Toolkit](custom-help-toolkit.md) to get the files.

## Translate the content

You can use the [Dynamics 365 Translation Service](/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/translation-service-overview) (DTS) to translate your own our the Microsoft-provided content into other languages. The service is hosted in Lifecycle Services and currently supports translation of content in Word documents and HTML files. For more information, see [Translate documentation files](/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/use-translation-service-ua).  

## See also

[Docs Contributor Guide](/contribute/)  
[Docs Authoring Pack for Visual Studio Code](/contribute/how-to-write-docs-auth-pack)  
[Getting started with writing and formatting on GitHub](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)  
[Visual Studio Code](https://code.visualstudio.com/)  
[Atom](https://atom.io/)  
[DocFx](https://dotnet.github.io/docfx/)  
