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

Microsoft Dynamics 365 for Finance and Operations, Enterprise edition is moving to a model of exclusively using extensions to customize the product. We're aware that this change impacts our entire partner ecosystem. We recommend that you read the resources listed on the [Extensibility home page](extensibility-home-page.md). These resources answer many questions and prepare you for building solutions using extensions.

You will discover that some customizations, which were possible with overlayering, cannot be done through extensions. We expect to add more extension capabilities, so that you will be able to do most of these things. For some customizations that were done with overlayering, you will need to file requests so that we are aware that we need to enable the appropriate extension points.

## What we are doing
We've been working toward an extension-based customization model for some time now. This started with enabling extensibility and sealing the platform and foundation models. Our focus then shifted to the application. We have worked with many ISV partners to collect extensibility requirements. The (July 2017) supports many new extensibility scenarios.

In future releases, we will be focusing on completing ISV requests and solving as many VAR-initiated requests as possible. Because we do not expect to be able to handle all requests right away, we will not enforce hard sealing of the Application Suite model in the next major product update. The next update will still support overlayering of this model; however, a warning will be shown when compiling overlayered code indicating that this is the last release in which the Application Suite model can be overlayered.

## How do I log extensibility requests?
If you discover a customization that you cannot implement as an extension, you can unblock yourself by using overlayering. Longer term this must be converted to an extension. You must log a request to Microsoft to ensure appropriate extension support is added to the product for your scenario.

Before logging the request, there are a few things to consider:  
- Could the requirement be met with existing extensibility features? Building solutions with extensions requires different design and implementation patterns.
- How important is the requirement to the customer and/or business analyst?  
- Will the implementation be upgrade friendly for the long term?

Extensibility requests are logged using the extensibility feedback program on the Connect site. Because we are essentially sharing deep roadmap information, we require that organizations be under NDA to be enrolled in this feedback community.

Partners only need to join the feedback community once and not for each of their employees. To enroll in the feedback community:

1. [Provide organization profile information.](http://aka.ms/feedbackcommunitynomination)
2. [Sign the NDA, Input agreement, code and data sharing policies.](http://aka.ms/feedbackcommunityagreement)

As a partner, after you have signed the agreements, people from your organization will be able to access the feedback Yammer groups. We recommend that you join the Yammer group 'Operations extensibility' where a broad range of extensibility topics are discussed.

For the extensibility feedback program to appear on the Connect site, use the Invitation link below. This link adds **DYNAMICS 365 FOR OPERATIONS EXTENSIBILITY FEEDBACK** under Programs on the Connect site. Use this feedback program when logging your extensibility requests.

[Invitation link for OPERATIONS EXTENSIBILITY FEEDBACK](https://connect.microsoft.com/site1321/InvitationUse.aspx?ProgramID=9338&InvitationID=EXT-W2TQ-3Y9Y) 

When you log extensibility requests, please enter detailed information about what you need to become enabled for extensibility, and include information on what it is you need to extend. This will help Microsoft to be efficient in addressing your requests. You are  welcome to propose how Microsoft could enable the functionality that you need in the standard application in a way that effectively addresses your needs.

Do not open a request for a hotfix. We will not release extensibility requests as hotfixes.  

Extensibility requests are exclusive for Dynamics 365 for Finance and Operations only. We are not planning to accommodate extensibility requests for Dynamics AX 2012 or earlier releases.

## When will my extensibility requests be enabled?

Extensibility requests are logged to a backlog. Microsoft engineers prioritize all requests, and then work on them in priority order. At this point, while overlayering is still an option, we prioritize requests that accommodate multiple customers, over a request that serves a single customer. We plan to make the backlog publicly available, enabling you to see progress and find how your requests are placed in the backlog.

## How will extensibility requests be made available to deploy?
Between the July 2017 update and the next major product update there are no application releases planned. This means that any extension requests not part of this update or requests made after this, would not be available until the next update. Plans beyond the next major update have not yet been determined.

Between the July 2017 update and the next major product update, the plan is to make community preview (CTPs) builds available as downloadable VHDs. The CTP builds will be application builds. You can leverage the CTP builds to minimize the preparation time of your solution when the next major product update is publicly available.

Details on how to obtain access to the CTP builds will be shared with the extensibility feedback Connect group.

## Still have questions?

Read the [Extensibility FAQ](app-sealing-faq.md) and the other resources listed on the [Extensibility home page](extensibility-home-page.md).
