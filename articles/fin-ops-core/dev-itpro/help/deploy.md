---
# required metadata

title: Deploy your custom Help
description: This topic describes how you can extend the Microsoft Help to reflect your solution and then connect that to the Help pane in certain Dynamics 365 apps. 
author: edupont04
manager: AnnBe
ms.date: 10/25/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: SystemParameters
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 16141
ms.assetid: 0b9c8630-9474-4473-80fd-7db5d54b2275
ms.search.region: Global
# ms.search.industry: 
ms.author: edupont
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Deploying custom Help

[!include [banner](../includes/banner.md)]

You can configure your own help to connect to the Help pane in Dynamics 365 Finance, Supply Chain Management, Retail, and Talent. In this topic, you can read about how to do that.  

## Plan your Help system

Depending on the customer's Dynamics 365 solution, their final Help system can come from a number of different sources. In the following, we assume that you are a consultant from a Dynamics 365 partner who wants to add custom Help to their customer's solution.  

There are at least three different scenarios for where the source content for the customer's Help experience comes from:

- The Help pane serves content from Microsoft and one additional provider on a custom help tab  

- The Help pane serves content from Microsoft and multiple additional providers on a custom help tab  

- The Help pane serves content from one provider on a custom help tab, and does not include Microsoft Help content  

- The Help pane serves content from multiple providers on each their custom help tab, and does not include Microsoft Help content  

The choice of scenario that you support in your implementation determines whether your custom Help implementation includes Microsoft Help content, and whether you need to collaborate with other solution providers or partners to combine help from multiple solutions.  

### Help site

In order to provide the users of the solution with access to Help in the Help pane, you must publish your content on a website. The website can be private or public, but we recommend that users do not have to log in so that they can access your content.  

You can deploy your content to an existing website, or you can set up a dedicated website based on Azure.  

### Reuse Dynamics AX 2012 content

You can reuse content from Dynamics AX 2012. For more information, see [Convert Dynamics AX custom Help for use in Dynamics 365](migrate-dynamicsax2012.md).  