---
# required metadata

title: Deploy your custom Help
description: This topic describes how you can extend the Microsoft Help to reflect your solution and then connect that to the Help pane in Finance and Operations apps. 
author: edupont04
manager: AnnBe
ms.date: 02/18/2020
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

You can connect solution-specific and customer-specific help content with the [Help pane](../../fin-ops/get-started/help-overview.md#in-product-help) in the Finance and Operations client if your solution is based on Dynamics 365 Finance, Supply Chain Management, or Commerce. Finance and Operations apps are rarely used out-of-the-box. Rather, the solution is customized and extended to fit the organization's needs. Similarly, you can customize and extend the Help experience. This topic describes the main steps and decision points.  

> [!NOTE]
> Users of Finance and Operations apps can create [custom task guides](/../../fin-ops/get-started/help-connect.md#create-custom-help-with-task-guides) to supplement conceptual content that describes the functionality of their solution. These conceptual descriptions are referred to as Help and can be provided by Microsoft, partners, and the organization itself. For more information, see [Help system](../../fin-ops/get-started/help-overview.md).

:::image type="content" source="../../fin-ops/get-started/media/help-architecture.png" alt-text="Diagram showing a customized help solution and the Help pane.":::

## Custom help scenarios

Depending on the customer's solution, Help content can come from different sources. In the following, we assume that you are a consultant from a Dynamics 365 partner who wants to add custom Help to their customer's solution, and that you want to connect the customer's Help solution with the in-product Help pane. We start with a very simple scenario and then show two slightly more complex variants.  

For the sake of simplicity, we're assuming that the customer uses a solution based on Dynamics 365 Supply Chain Management with a large module added by the partner. There are no significant customizations of the core product functionality, and the users will not create or use task guides.  

In this simplified scenario, the partner deploys conceptual Help for their custom module to a website and then connects that website to the in-product Help pane as illustrated in the following diagram.  

:::image type="content" source="../media/help-architecture-custom1.png" alt-text="Diagram showing the Help pane with one custom help website connected and no task guides.":::

As a result, when a user opens the Help pane, they are offered links to Help from the partner's website as well as from *docs.microsoft.com*. The in-product Help pane shows context-sensitive links to Help content on the connected websites based on specific metadata values

If that scenario is too simple, then let us look at a couple of variants.

### Variant 1

In the first variant, the partner makes significant customizations of the core product as well. So on top of the Help that describes their own module, they also customize Microsoft's Help and deploy that customized content to their own website.

:::image type="content" source="../media/help-architecture-custom2.png" alt-text="Diagram showing the Help pane with one custom help website connected and no task guides.":::

### Variant 2

In the second variant, one partner makes significant customizations of the core product and also customize Microsoft's Help and deploy that customized content to their own website. The customer also uses a module provided by another partner, who has published their content to a website, and the internal administrator decides to connect both websites to their solution's Help pane.

:::image type="content" source="../media/help-architecture-custom3.png" alt-text="Diagram showing the Help pane with two custom help websites connected and no task guides.":::

There are, of course, more complex deployments in the real world, and by adding task guides, each customer can get the custom user assistance experience that they prefer.

## Custom help sites

In order to connect your Help content with the product, you must customize the in-product Help pane with your content. This requires the following elements:

- Your content is available on a website
- Your content is indexed by a search service
- Both website and search service are connected to the Help pane

You can see an example of how to get these pieces in place in [Example of Deploying Custom Help on Azure](walkthrough-help-azure.md).

> [!TIP]
> We recommend that you deploy your Help content to an Azure Web App. For more information, see [Deploying custom help sites](custom-help-websites.md).

## Process

The end-to-end process depends on the actual customer's solution and the users' expectations. We provide a toolkit with tools that can help in different ways, and we provide guidance for the main steps and some of the quirks. However, some steps are very particular to tools or processes that are not directly tied to Dynamics 365, and so we have to refer to external guidance. But if you want to share your own learnings with other administrators, you can either contribute to this documentation through the link at the bottom of the page, or join the Dynamics 365 community.

The following table outlines the mains steps with links to further guidance.

|Objective |Learn more  |
|----------|------------|
|I want to understand the end-to-end process |See the scenarios in the previous section |
|I want to host my Help content on Azure |See [Deploying custom help sites](custom-help-websites.md)         |
|I want to customize Microsoft's Help content |See [Extend, Customize, and Collaborate on the Help](contributor-guide.md)        |
|I just want a copy of Microsoft's content, thanks| See [Custom Help Toolkit: The HTML From Repos Generator tool](custom-help-toolkit-HtmlFromRepoGenerator.md)  |
|I want to reuse my Dynamics AX content|See [Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md)  |
|I want to add my content to the Help pane |See [Connect your Help website with the Help pane](connect-help-pane.md)  |

## See also

[Deploying custom help sites on Azure](custom-help-websites.md)  
[Connect your Help website with the Help pane](connect-help-pane.md)  
[Example of Deploying Custom Help on Azure](walkthrough-help-azure.md)  
[Running the Custom Help Toolkit](custom-help-toolkit.md)  
[Language and locale descriptors in across product and Help](language-locale.md)  
[Configure the Help experience for Finance and Operations apps](../../fin-ops/get-started/help-connect.md)  
[Help system](../../fin-ops/get-started/help-overview.md)  
