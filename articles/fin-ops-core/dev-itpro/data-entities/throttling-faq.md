---
# required metadata

title: Priority-based throttling FAQ
description: This topic provides answers to frequently asked questions about priority-based throttling for OData and custom service-based integrations.
author: hasaid
ms.date: 06/17/2021
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


This topic provides answers to some frequently asked questions about [priority-based throttling](priority-based-throttling.md) for Open Data Protocol (OData) and custom service-based integrations.

## How do I access the Data management Yammer group?
To access the Data management Yammer group, go to [Data management Yammer group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=13408417).

## When will throttling be enabled by default?
The throttling feature has been in preview since Finance 10.0.13 and will be enabled by default starting in version 10.0.19. You can manually trigger throttling in your environment by setting the priority for your OData and Custom service requests. However, starting with the release of Finance 10.0.19, throttling will be automatically enabled even if you haven't set priorities.

Finance version 10.0.19 will be available for pre-release in late April 2021 and will be generally available in June 2021.

## Will a retry request receive preferential treatment over a new request?
No.

## Will my environment be subject to any API limits?
No. At this time, environments are not subject to any API limits. 

Telemetry data is collected to assess the impact of the workloads across environments. This data helps establish baseline API limits as we define a roadmap for introducing usage-based limits.

## Is there a report that determines when throttling might occur?
Yes. A report is available and can be accessed through the **Raw logs** on the **Environment monitoring** page in LCS. The requests that are listed in this view are likely to be throttled when this feature is turned on by default starting in Finance version 10.0.19.

## Will throttling affect the Data Import/Export Framework (DIXF) and batch?
No. Throttling is only for OData and custom service integrations.

## Is throttling available for on-premises environments?
No. Throttling is not available for on-premises environments.

## In Preview, will my requests be throttled if priorities aren't configured?
No, because only the telemetry is available. The actual throttling occurs if you configure priorities. We recommend that you use this approach in **non-production** environments during the Preview period.

## Can throttling be enabled on dev boxes?
No. You can only set priority and trigger throttling in sandbox or production environments.

## What happens to requests if the user didn't retry a throttled request?
Currently, if a request isn't retried when a 429 error is received, the request won't be processed.

## Will historic throttling information be used to advise me when I resize environments?
Yes. For one month, you can export the information to Excel for more analysis and archiving.

## Is throttling functionality version-specific? If it is, which version is it available in?
Priority-based throttling will be available in Preview starting with the version 10.0.13 of Finance and Operations apps.

## Are there plans to provide an option for the Priority mapping grid entry?
Microsoft will consider this request in a future release.

## Will the requests of my interactive users be throttled?
No. There will be no impact on the requests of interactive (online) users.

## If I experience a performance issue in Dynamics 365 Finance while a page is being loaded or a business document is being processed, how does that performance issue differ from throttling?
Throttling helps maintain a healthy system when there is a resource constraint. It won't affect any page actions.

## How can I determine the wait time before I retry a throttled request?
When a request is throttled, the response header includes a time that will be used in retry logic. You can use the **Retry-After** HTTP header to fetch the value that will be provided in seconds. For example, **Retry-After: 60**.

## What is the message that is shown as part of the 429 HTTP response?
You will receive the message, "This request could not be processed at this time due to system experiencing high resource utilization. Retry the request after {0} seconds".
Where **{0}** will have the dynamically calculated retry-after time interval.

## Does throttling apply to Microsoft services?
Starting in Finance version 10.0.19, the following Microsoft services are initially exempt, and throttling doesn't apply to them: 

   - Document Routing Agent (DRA)
   - Warehouse Mobile (WHSMobile)
   - RetailAPI
   - Office Integration
   - Data Import/Export Framework (DIXF)
   - Data Integrator
   - Dual-write
   - Finance and Operations apps - Power Platform Integration (Virtual Entities)
   - Finance and Operations apps Connector 

Though these services are exempt, telemetry is being collected on the performance and impact of these services on the overall system health. 

The owners of the exempt services are prioritizing the implementation of 429 handlers by the end of 2021. At that time, the services will no longer be exempt and throttling will apply. Notification will be provided ahead of these changes, and the documentation will be updated.

Even if these services implement their own handlers, we still recommended that you have client-side handling. Consider implementing the 429 handler with *retry-after* logic.

## Is it recommended to use a dedicated integration account instead of just the generic admin user account?
Yes, we strongly recommend this approach. As these service protection settings are set up for user-specific values, using the same user account for most or all of your integration will limit your ability to assign relative priorities across your integration needs. Further, if the same user account is used, all integration requests that originate from that user account will be subjected to throttling.

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
