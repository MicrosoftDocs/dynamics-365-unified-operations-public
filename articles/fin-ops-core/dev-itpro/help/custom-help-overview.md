---
# required metadata

title: Deploy your custom Help
description: Learn how to extend the Microsoft Help to reflect your solution and then connect your content to the Help pane. 
author: edupont04
manager: AnnBe
ms.date: 03/17/2020
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

# Custom Help Overview

[!include [banner](../includes/banner.md)]

Finance and Operations apps are often customized and extended to fit an organization's needs. You can connect solution-specific and customer-specific help content with the [Help pane](../../fin-ops/get-started/help-overview.md#in-product-help) in the Finance and Operations client if your solution is based on Dynamics 365 Finance, Supply Chain Management, or Commerce. This article describes the main steps and decision points.  

> [!NOTE]
> Users of Finance and Operations apps can create [custom task guides](/../../fin-ops/get-started/help-connect.md#create-custom-help-with-task-guides) to supplement conceptual content that describes the functionality of their solution. These conceptual descriptions are also referred to as help and can be provided by Microsoft, partners, and the organization itself. For more information, see [Help system](../../fin-ops/get-started/help-overview.md).

The following illustration and this section in general uses the term "help" for conceptual descriptions with or without how-to guides. The term "task guides" describes in-product task guides.  

:::image type="content" source="../../fin-ops/get-started/media/help-architecture.png" alt-text="Diagram showing a customized help solution and the Help pane.":::

## Custom help content

Custom help content will typically originate from one of three sources.

1. Microsoft documentation repositories

    You can use [HTMLFromRepoGenerator](custom-help-toolkit-HtmlFromRepoGenerator.md) to clone content from any of the Finance and Operations repositories and generate corresponding HTML files. These files can then be updated with content specific to your solution.

2. Existing customized Dynamics AX content

    You can [convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md).

3. HTML files that are created specifically for your solution

    [Learn more about the metadata](#metadata) that must be added to your HTML files for context-sensitive help and search to work correctly.

## Process

The end-to-end process depends on the actual customer's solution and the users' expectations. A typical end-to-end process will involve the following:

1. Creating the custom help content.
2. Publishing the content on a website.
3. Indexing the content using a search service.
4. Connecting the Custom Help pane to the website and the search service.

We provide a [toolkit](custom-help-toolkit.md) to assist with generating HTML files from the Microsoft help repositories, generating JSON files for search services, and changing the locale of HTML files to match the locale of your solution.

You are welcome to share your knowledge by contributing to this documentation through the link at the bottom of the page or by joining the [Dynamics 365 community](https://community.dynamics.com/).

The following table outlines the main objectives that administrators typically have for configuring the Help experience.

|Objective |Learn more  |
|----------|------------|
|I want to give my users a customized in-product help experience that reflects their actual solution|See [Custom help sites](#custom-help-sites) and [Create documentation or training with Task Recorder](../user-interface/task-recorder-training-docs.md) |
|I want to use Microsoft's Help content as a baseline for help specific to my solution| See [Custom Help Toolkit: The HtmlFromRepoGenerator tool](custom-help-toolkit-HtmlFromRepoGenerator.md)  |
|I want to contribute to Microsoft's Help content|See [Extend, customize, and collaborate on the Help](contributor-guide.md)        |
|I want to reuse my existing Dynamics AX content|See [Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)  |
|I want to set up a website for my Help content|See [Deploying help websites](#custom-help-sites) |
|I want to add my content to the Help pane|See [Connect your help website with the Help pane](connect-help-pane.md)  |
|Our technical writers want guidance for how to convert our legacy content into MarkDown for a better Help customization story going forward|See [Moving to MarkDown](migrate-dynamicsax2012.md#moving-to-markdown) |

## <a name="custom-help-sites"></a>Custom help sites

In order for the product to connect to your Help content, you must customize the in-product Help pane to display your content. This requires the following elements:

- Your content is available on a website

    You can deploy your content to an existing website, or you can set up a dedicated website to host your content. The website can be private or public, but we recommend that users do not have to sign in to access your content.

- Your content is indexed by a search service

    If you are planning to use the [AzureSearchCustomHelp solution](walkthrough-help-azure.md) provided as part of the [Custom Help Toolkit](custom-help-toolkit.md) for context-sensitive help, the Help pane will generate a query to be run against the search service's index. <a name="metadata"></a>The query depends on specific metadata in the Help articles as described in following table:

    |Property  |Description  |
    |----------|-------------|
    |title | The value is used for full-text search from the Help pane. |
    |description  | The value is used for full-text search from the Help pane.  |
    |ms.search.form | The value contains the Application Object Tree (AOT) name of a form and is used for context-sensitive search from the Help pane. |
    |ms.search.scope|The value determines which client the Help article is shown in. You can specify one or more values. Values includes Core, Operations, Retail, and Human Resources.|
    |ms.locale |This value indicates the language of the topic. This is mapped against the current browser locale when the Help pane searches the content. the target custom help website can configure language fallback. For more information, see [Language and locale descriptors in across product and Help](language-locale.md). |

In [Deploying custom help to Azure](walkthrough-help-azure.md), we describe an approach for hosting content on Azure, including how you can set up a search service that indexes your content so that it can be found by the in-product Help pane. If you do not have an [Azure subscription](/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an account before you begin. You can start with a free account for 12 months. For more information, see [Create your Azure free account today](https://azure.microsoft.com/free/). 

## See also

[Connect your Help website with the Help pane](connect-help-pane.md)  
[Deploying custom help to Azure](walkthrough-help-azure.md)  
[Running the Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Configure the Help experience for Finance and Operations apps](../../fin-ops/get-started/help-connect.md)  
[Help system](../../fin-ops/get-started/help-overview.md)  
