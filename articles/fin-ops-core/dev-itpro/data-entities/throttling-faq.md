---
# required metadata

title: Priority-based throttling FAQ
description: This topic provides answers to some frequently asked questions (FAQ) about priority-based throttling for Open Data Protocol (OData) and custom service-based integrations.
author: hasaid
manager: AnnBe
ms.date: 09/23/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: sericks
# ms.search.scope: Operations
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

## Will a retry request receive preferential treatment over a new request?

No.

## Is there a report that determines when throttling might occur?

Yes. A report will be provided and can be accessed through the **Raw logs** within environment monitoring page in Microsoft Dynamics Lifecycle Services (LCS).

## Will throttling affect the Data Import/Export Framework (DIXF) and batch?

No. Throttling is only for OData and custom service integrations.

## In Preview, will my requests be throttled if priorities aren't configured?

No, because only the telemetry is available. The actual throttling occurs if you configure priorities. We recommend that you use this approach in **non-production** environments during the Preview period.

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

When a request is throttled, the response header includes a time that will be used in retry logic.

## Do you recommend that I use a dedicated integration account instead of just the generic admin user account?

Yes, we recommend this approach. However, it isn't mandatory.

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
