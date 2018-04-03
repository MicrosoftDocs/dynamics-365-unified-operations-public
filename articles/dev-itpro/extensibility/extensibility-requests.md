---
# required metadata

title: Extensibility requests
description: This topic explains how to file a request for additional extension points in Dynamics 365 for Finance and Operations. 
author: FrankDahl
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 89563
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: fdahl
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9
---

# Extensibility requests

[!include[banner](../includes/banner.md)]

Microsoft Dynamics 365 for Finance and Operations exclusively uses extensions to customize the product. We're aware that this change impacts our entire partner ecosystem. We recommend that you read the resources listed on the [Extensibility home page](extensibility-home-page.md). These resources answer many questions and prepare you for building solutions using extensions.

You will discover that some customizations, which were possible with overlayering, cannot be done through extensions. We have added many extension capabilities and expect to add more going forward, to enable the same business requirements without overlayering. For some customizations that were done with overlayering, you will need to log requests, to make us aware what you need.

## What we are doing
We've been working toward an extension-based customization model for some time now. Over the past several releases we have been gradually sealing models. The (April 2018) completes the sealing. From this release forward only extension based customizations are allowed. 

In future releases, we will be adding even more extensibility capabilites to enable ISV and VARs to deliver complete business solutions.  We will prioritize these on a customer-by-customer basis with frequent releases.

## How do I log extensibility requests?
If you discover a customization that you cannot implement as an extension, you must log a request to Microsoft to ensure appropriate extension support is added to the product for your scenario.

Before logging the request, there are a few things to consider:  
- Could the requirement be met with existing extensibility features? Building solutions with extensions requires different design and implementation patterns.
- How important is the requirement to the customer and/or business analyst?  
- Will the implementation be upgrade friendly for the long term?

Because we are essentially sharing deep roadmap information, we require that organizations be under NDA to be enrolled in our feedback community.

Partners only need to join the feedback community once and not for each of their employees. To enroll in the feedback community:

1. [Provide organization profile information.](http://aka.ms/feedbackcommunitynomination)
2. [Sign the NDA, Input agreement, code and data sharing policies.](http://aka.ms/feedbackcommunityagreement)

As a partner, after you have signed the agreements, people from your organization will be able to access the feedback Yammer groups. We recommend that you join the Yammer group 'Operations extensibility' where a broad range of extensibility topics are discussed.

> [!IMPORTANT]
> Coming soon:  Extensibility requests will be able to be submitted via Lifecycle Services.  In the meantime, please submit your request to daxcf@microsoft.com

When you log extensibility requests, please enter detailed information about what you need to become enabled for extensibility, and include information on what it is you need to extend. This will help Microsoft to be efficient in addressing your requests. You are  welcome to propose how Microsoft could enable the functionality that you need in the standard application in a way that effectively addresses your needs.

Please note: We will not release extensibility requests as hotfixes.  

Extensibility requests are exclusive for Dynamics 365 for Finance and Operations only. We are not planning to accommodate extensibility requests for Dynamics AX 2012 or earlier releases.

## When will my extensibility requests be enabled?

Extensibility requests are logged to a backlog. Microsoft engineers prioritize all requests, and then work on them in priority order. Please note that Microsoft is not guaranteeing requests will be fulfilled. Especially requests that are intrusive by nature, will not be supported, as they will prevent seamless upgrade.

## How will extensibility requests be made available to deploy?
After the Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 8.0 release we plan to release frequent application updates with new extensibility requests; following the same release cadence as the platform. 

## Still have questions?

Read the [Extensibility FAQ](app-sealing-faq.md) and the other resources listed on the [Extensibility home page](extensibility-home-page.md).
