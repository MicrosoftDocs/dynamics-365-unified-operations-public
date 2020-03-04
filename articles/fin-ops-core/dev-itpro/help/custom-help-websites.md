---
# required metadata

title: Deploy a custom Help website hosted in Azure
description: Learn why you will want to deploy your Help content to Azure so that it can be found by the Help pane in Finance and Operations apps. 
author: edupont04
manager: AnnBe
ms.date: 03/04/2020
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

# Deploying custom help websites

[!include [banner](../includes/banner.md)]

To provide the users of the solution with access to Help in the Help pane, you must publish your content to a website. The website can be private or public, but we recommend that users do not have to log in to access your content.  

You can deploy your content to an existing website, or you can set up a dedicated website to host your content. In this article, we will describe how you can host your content on Azure. If you choose a different deployment solution, you must make sure that your content can be indexed so that the Help pane can link to it. We offer no technical support for websites that are not hosted on Azure.  

In [Deploying custom help to Azure](walkthrough-help-azure.md), we describe an approach for hosting content on Azure, including how you can set up a search service that indexes your content so that it can be found by the in-product Help pane. We recommend this approach because the Azure portal includes many tools and features that can help you maintain your custom help website.  

If you host the Help content on another type of website, it is a requirement that the content is discoverable by the in-product Help pane, such as by using Azure Cognitive Search to index the content. For an example of how to set up a search service, see the [Configure the search service](walkthrough-help-azure.md#searchconfig) section in [Deploying custom help to Azure](walkthrough-help-azure.md).  

## Host your content on Azure

We recommend that you set up an Azure web app and host your content there for easy integration with the in-product Help pane. If you do not have an [Azure subscription](/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an account before you begin. You can start with a free account for 12 months. For more information, see [Create your Azure free account today](https://azure.microsoft.com/free/).  

There are several different ways of getting your content hosted on Azure. In [Deploying custom help to Azure](walkthrough-help-azure.md), we describe our recommended approach. You can find inspiration for other approaches in the Azure documentation. For more information, see [Azure Blob storage documentation](/azure/storage/blobs/).  

> [!TIP]
> It can seem like a large task to deploy custom help as we describe it here. However, tools and scripts in the custom help toolkit can help you. Once things are set up, then the Azure portal can help you maintain the site, and you can set up CI/CD to manage the content updates, for example.

### Content and search indexing

In order to make links to your custom help available in the in-product Help pane, the content must be discoverable. The in-product Help pane generates links to context-sensitive content based on a search string that is sent to the configured Help websites. The search string includes information about the form that the Help pane was activated from and searches for content that contains that form as part of the article's metadata.  

Your custom Help website must be able to return relevant links based on the metadata in the search query. This means customizing the Help pane to consume the content through a search index. We recommend using [Azure Cognitive Search](/azure/search/search-what-is-azure-search) to set up and run this search index.  

The search index is based on the presence of specific metadata in the Help articles as described in following table:

|Property  |Description  |
|----------|-------------|
|title | The value is used for full-text search from the Help pane. |
|description  | The value is used for full-text search from the Help pane.  |
|ms.search.form | The value contains the Application Object Tree (AOT) name of a form and is used for context-sensitive search from the Help pane. |
|ms.search.scope|The value determines which client the Help topic is shown in. You can specify one or more values. Values includes Core, Operations, Retail, and Human Resources.|
|ms.locale |This value indicates the language of the topic. This is mapped against the current browser locale when the Help pane searches the content. the target custom help website can configure language fallback. For more information, see [Language and locale descriptors in across product and Help](language-locale.md). |

All websites support searches using different technologies. In [Deploying custom help to Azure](walkthrough-help-azure.md), the search index is based on JSON files that are generated from the HTML files with your custom help content. You then make a search service generate a map of the content as defined by these JSON files. This search index is then used by the in-product Help pane to generate context-sensitive links to content based on where the user is in the product's user interface.  

## Reuse Dynamics AX 2012 content

In most cases, you can reuse content from a Dynamics AX 2012 solution. For more information, see [Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md).  

## Get updated content from Microsoft

If your Help solution extends Microsoft's content, then you can fork our repo and then use standard Git tools to keep your fork updated with our content updates. You can make it a habit to get updates from Microsoft every week, every month, or every 6 months, for example. In some cases, though, you may prefer to get a completely new clone of the content of our repo and regenerate the Help from the clone on a regular basis. For more information, see [Extend, Customize, and Collaborate on the Help](contributor-guide.md).  

> [!TIP]
> The Custom Help Toolkit includes a tool that can help integrate the latest Microsoft content with yours. For more information, see [Custom Help Toolkit: The HTML From Repos Generator tool](custom-help-toolkit-htmlfromrepogenerator.md).

## See also

[Deploying custom help to Azure](walkthrough-help-azure.md)  
[Running the Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Configure the Help experience for Finance and Operations apps](../../fin-ops/get-started/help-connect.md)  
[Help system](../../fin-ops/get-started/help-overview.md)  
