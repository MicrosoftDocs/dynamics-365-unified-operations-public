---
# required metadata

title: Deploy a custom Help website hosted in Azure
description: This topic describes how you can extend the Microsoft Help to reflect your solution and then connect that to the Help pane in Finance and Operations apps. 
author: edupont04
manager: AnnBe
ms.date: 02/04/2020
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

# Deploying custom help sites

[!include [banner](../includes/banner.md)]

To provide the users of the solution with access to Help in the Help pane, you must publish your content to a website. The website can be private or public, but we recommend that users do not have to log in to access your content.  

You can deploy your content to an existing website, or you can set up a dedicated website to host your content. In this article, we will describe how you can host your content on Azure. If you choose a different deployment solution, you must make sure that your content can be indexed so that the Help pane can link to it. We offer no support for websites that are not hosted on Azure.  

In [Example of Deploying Custom Help on Azure](walkthrough-help-azure.md), we describe an approach for hosting content on Azure, including how you can set up a search service that indexes your content so that it can be found by the in-product Help pane.  

If you host the Help content on another type of website, it is a requirement that the content is discoverable by the in-product Help pane, such as by using Azure Search to index the content. For an example of how to set up a search service, see the [Configure the search service](walkthrough-help-azure.md#searchconfig) section in [Example of Deploying Custom Help on Azure](walkthrough-help-azure.md).  

## Host your content on Azure

We recommend that you set up an Azure web app and host your content there for easy integration with the in-product Help pane. If you do not have an [Azure subscription](/azure/guides/developer/azure-developer-guide#understanding-accounts-subscriptions-and-billing), create an account before you begin. You can start with a free account for 12 months. For more information, see [Create your Azure free account today](https://azure.microsoft.com/free/).  

There are several different ways of getting your content hosted on Azure. In [Example of Deploying Custom Help on Azure](walkthrough-help-azure.md), we describe one approach. You can find inspiration for other approaches in the Azure documentation. For more information, see [Azure Blob storage documentation](/azure/storage/blobs/).  

## Reuse Dynamics AX 2012 content

In most cases, you can reuse content from a Dynamics AX 2012 solution. For more information, see [Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md).  

## Get updated content from Microsoft

If your Help solution extends Microsoft's content, then you can fork our repo and then use standard Git tools to keep your fork updated with our content updates. You can make it a habit to get updates from Microsoft every week, every month, or every 6 months, for example. In some cases, though, you may prefer to get a completely new clone of the content of our repo and regenerate the Help from the clone on a regular basis.  

> [!TIP]
> The Custom Help Toolkit includes a tool that can help integrate the latest Microsoft content with yours. For more information, see [Use the HtmlFromRepoGenerator tool to get MarkDown files and generate HTML files](custom-help-toolkit.md#consoleapp).

## See also

[Example of Deploying Custom Help on Azure](walkthrough-help-azure.md)  
[Running the Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Connect the Help system](../../fin-ops/get-started/help-connect.md)  
[Help system](../../fin-ops/get-started/help-overview.md)  
