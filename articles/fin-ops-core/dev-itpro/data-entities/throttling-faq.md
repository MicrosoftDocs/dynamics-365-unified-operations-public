---
# required metadata

title: Priority-based throttling FAQ
description: This topic provides answers to frequently asked questions (FAQ) about priority-based throttling for OData and custom service-based integrations.
author: hasaid
ms.date: 04/20/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 21311
ms.assetid: 5ff7fd93-1bb8-4883-9cca-c8c42ddc1746
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: Platform update 37

---

# Priority-based throttling FAQ

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic provides answers to some frequently asked questions (FAQ) about [priority-based throttling](priority-based-throttling.md) for Open Data Protocol (OData) and custom service-based integrations.

## How do I access the Data management Yammer group?
Follow this link: [Data management Yammer group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=13408417).

## In what product update will throttling be enabled by default?
The throttling feature has been in preview since Finance 10.0.13 and will be enabled by default starting in 10.0.19. You can manually trigger throttling in your environment by setting the priority for your OData and Custom service requests. However, starting with the release of Finance 10.0.19, throttling will be automatically enabled even if you haven't set priorties.

## What is the release date for the platform update for Finance 10.0.19?
Finance 10.0.19 will be available for pre-release in late April 2021 and will be generally available in June 2021.

## Will a retry request receive preferential treatment over a new request?
No.

## Will my environment be subjected to any API limits?
No. As part of this release we are primarily focused on resources-based performance. We will be analyzing and introducing usage-based limits in the future that will be subjected to API call volumes.

## Is there a report that determines when throttling might occur?
Yes. A report will is available and can be accessed through the **Raw logs** within environment monitoring page in Microsoft Dynamics Lifecycle Services (LCS). The requests that are listed in this view are likely to be throttled when this feature is turned on by default starting in PU43 (10.0.19)

## Will throttling affect the Data Import/Export Framework (DIXF) and batch?
No. Throttling is only for OData and custom service integrations.

## Is throttling available for on-prem?
No. Throttling is not available for on-prem environments.

## In Preview, will my requests be throttled if priorities aren't configured?
No, because only the telemetry is available. The actual throttling occurs if you configure priorities. We recommend that you use this approach in **non-production** environments during the Preview period.

## Can throttling be enabled in dev boxes?
No. You can only set priority adn trigger throttling in sandbox or production environments.

## What happens to requests if the user didn't retry a throttled request?
Currently, if a request isn't retried when a 429 error is received, the request won't be processed.

## Will historic throttling information be used to advise me when I resize environments?
Yes. For one month, you can export the information to Excel for more analysis and archiving.

## Is throttling functionality version-specific? If it is, which version is it available in?
Priority-based throttling will be available in Preview starting with the **Platform updates for version 10.0.13 of Finance and Operations apps** release.

## Are there plans to provide an option for the Priority mapping grid entry?
Microsoft will consider this request in a future release.

## Will the requests of my interactive users be throttled?
No. There will be no impact on the requests of interactive (online) users.

## If I experience a performance issue in Dynamics 365 Finance while a page is being loaded or a business document is being processed, how does that performance issue differ from throttling?
Throttling helps maintain a healthy system when there is a resource constraint. It won't affect any page actions.

## How can I determine the wait time before I retry a throttled request?
When a request is throttled, the response header includes a time that will be used in retry logic. You can use the **Retry-After** HTTP header to fetch the value that will be provided in seconds. For example: **Retry-After: 60**

## What is the message we will see as part of the 429 HTTP response?
You will receive "*This request could not be processed at this time due to system experiencing high resource utilization. Please retry the request after {0} seconds*".
Where {0} will have the dynamically calculated retry-after time interval.

## Does throttling apply to internal Microsoft services?
Internal Microsoft services, such as, DRA, WHSMobile, RetailAPI are currently exempt from throttling. However, we are collecting telemetry on the performance and effect of these services on the overall system health. We will be working with each of these internal services team to establish usage-based limits in the near future.

## Do you recommend that I use a dedicated integration account instead of just the generic admin user account?
Yes, we strongly recommend this approach. As these service protection settings are setup for user specific values, using the same user account for most/ all of your integration will limit your ability to assign relative priorites across your integration needs. Further if the same user account is used all integration requests originating from that user account will be subjected to throttling.

## Does throttling depend on the tier that my environment is running on?
In the initial release, no. Throttling will calculate its threshold based on the resources that are available for each environment.

## Is throttling functionality legal entity–specific?
No.

## Does throttling affect bring your own database (BYOD) export?
No.

## Will throttling monitoring be available in Application Insights?
Monitoring will be onboarded to any available tool in the future.

## If a production environment regularly runs out of resources, will Microsoft have to resize it?
Yes. Sizing estimate will also have to be revalidated and uploaded.

## After April 2021, will the system be able to override priority-based throttling?
The system will use default values if no priorities are configured after April 2021.

## Can the throttling engine be configured (thresholds)?
No.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
