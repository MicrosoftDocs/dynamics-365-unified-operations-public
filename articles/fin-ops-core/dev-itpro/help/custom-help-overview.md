---
# required metadata

title: Custom Help overview
description: This topic explains how you can extend the Microsoft Help system so that it reflects your solution and then connect your content to the Help pane. 
author: edupont04
manager: AnnBe
ms.date: 05/11/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

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

# Custom Help overview

[!include [banner](../includes/banner.md)]

Finance and Operations apps are often customized and extended to fit an organization's needs. If your solution is based on Microsoft Dynamics 365 Finance, Dynamics 365 Supply Chain Management, or Dynamics 365 Commerce, you can connect solution-specific and customer-specific Help content to the [Help pane](../../fin-ops/get-started/help-overview.md#in-product-help) in the Finance and Operations client. This topic describes the main steps and decision points.

> [!NOTE]
> Users of Finance and Operations apps can create custom task guides to supplement conceptual content that describes the functionality of their solution. These conceptual descriptions are also referred to as Help and can be provided by Microsoft, partners, and an organization itself. For more information, see [Help system](../../fin-ops/get-started/help-overview.md).

The following illustration, and this topic in general, use the term *Help* for conceptual descriptions that either include or exclude how-to guides. The term *task guides* refers to in-product task guides.

![Customized Help solution and the Help pane](../../fin-ops/get-started/media/help-architecture.png)

## Custom Help content

Custom Help content typically originates from one of three sources:

- Microsoft documentation repositories (repos)

    You can use the [HTMLFromRepoGenerator](custom-help-toolkit-HtmlFromRepoGenerator.md) tool from the Custom Help Toolkit to clone content from any of the Finance and Operations repositories and generate corresponding HTML files. Those files can then be updated with content that is specific to your solution.

- Existing customized Dynamics AX content

    You can [convert Dynamics AX custom Help content so that it can be used in Dynamics 365](migrate-dynamicsax2012.md).

- HTML files that are created specifically for your solution

    [Learn more about the metadata](preparing-content.md#metadata) that must be added to your HTML files for context-sensitive Help and search to work correctly.

## Process

The end-to-end process depends on the actual customer solution and the users' expectations. A typical process involves the following steps:

1. Create the custom Help content.
2. Publish the content on a website.
3. Index the content by using a search service.
4. Connect the custom **Help** pane to the website and the search service.

Microsoft provides a [toolkit](custom-help-toolkit.md) that can help you generate HTML files from the Microsoft Help repositories, generate JavaScript Object Notation (JSON) files for search services, and change the locale of HTML files so that it matches the locale of your solution.

You're welcome to share your knowledge by contributing to this documentation through the link at the bottom of the page or by joining the [Dynamics 365 community](https://community.dynamics.com/).

The following table outlines the main objectives that admins typically have for configuring the Help experience.

| Objective | Learn more |
|-----------|------------|
| I want to give my users a customized in-product Help experience that reflects their actual solution. | See the [Custom Help websites](#custom-help-sites) section of this topic and [Create documentation or training with Task Recorder](../user-interface/task-recorder-training-docs.md). |
| I want to use the Microsoft Help content as a baseline for Help content that is specific to my solution. | See [Custom Help Toolkit: The HtmlFromRepoGenerator tool](custom-help-toolkit-HtmlFromRepoGenerator.md). |
| I want to contribute to the Microsoft Help content. | See [Extend, customize, and collaborate on the Help](contributor-guide.md). |
| I want to reuse my existing Dynamics AX content. | See [Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md). |
| I want to set up a website for my Help content. | See the [Custom Help websites](#custom-help-sites) section of this topic. |
| I want to add my content to the **Help** pane. | See [Connect a custom Help website to the Help pane](connect-help-pane.md). |
| Our technical writers want guidance that will help them convert our earlier content into Markdown so that it becomes easier for them to customize the Microsoft content. | See [Moving to Markdown](migrate-dynamicsax2012.md#moving-to-markdown). |

## <a name="custom-help-sites"></a>Custom Help websites

Before the product can connect to your Help content, you must customize the in-product **Help** pane so that it shows your content. The following conditions must be met:

- Your content must be available on a website.

    You can deploy your content to an existing website, or you can set up a dedicated website to host your content. The website can be private or public, but we recommend that users **not** be required to sign in to access your content.

- Your content must be indexed by a search service.

    If you use the [AzureSearchCustomHelp](walkthrough-help-azure.md) solution that is part of the [Custom Help Toolkit](custom-help-toolkit.md) for context-sensitive Help, the **Help** pane will generate a query that must be run against the search service's index. The query depends on specific metadata in the Help topics. For more information, see [Metadata requirements for custom Help topics](preparing-content.md#metadata).

The [Deploy custom Help to Azure](walkthrough-help-azure.md) topic describes an approach for hosting content on Azure. It includes information about how to set up a search service that indexes your content so that it can be found by the in-product **Help** pane. If you don't have an [Azure subscription](/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an account before you begin. You can start with a free account for 12 months. For more information, see [Create your Azure free account today](https://azure.microsoft.com/free/).

## See also

[Connect a custom Help website to the Help pane](connect-help-pane.md)  
[Deploy custom Help to Azure](walkthrough-help-azure.md)  
[Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in the product and in Help](language-locale.md)  
[Configure the Help experience for Finance and Operations apps](../../fin-ops/get-started/help-connect.md)  
[Help system](../../fin-ops/get-started/help-overview.md)
