---
# required metadata

title: Priority-based throttling FAQ
description: This topic provides information about frequently asked questions (FAQ) about priority-based throttling for Odata and custom service-based integrations.
author: hasaid
manager: AnnBe
ms.date: 09/14/2020
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
ms.search.scope: Operations
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

This topic provides answers to some frequently asked questions about [Priority-based throttling](priority-based-batch-scheduling.md). 

## How do I access the Data managment Yammer group?

[Data management Yammer group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=13408417)

## Will a retry request receive preferential treatment over a new request?

No. 

## Is there a report that determines when throttling might happen?

Yes. A report will be provided than can be accessed through LCS Raw logs within environment monitoring page.

## Will throttling impact DIXF and Batch?

No. Throttling is only for Odata and custom service integrations.

## In Preview, if Priorities are not configured, will my requests get throttled?

No, as only the telemetry is available. The actual throttling happens if you configure priorities, This is the recommended approach in NON-prod environment within the Preview period.

## What happens to the requests if user didn't retry the throttled request? 

Currently, if the request is not retried when a 429 error is received, the request will not be processed.

## Will historic throttling information be used to advise when resizing environments?

Yes. For one month, you can export the information to Microsoft Excel for more analysis and archiving.

## Is throttling functionality version specific? If yes, in which version is this available?

Priority based throttling will be available in Preview starting with the **Platform updates for version 10.0.13 of Finance and Operations apps** release.

## Are there plans to provide an option for the Priority mapping grid entry?

We will consider this request in a future release.

## Will my interactive users’ requests get throttled?

No. There will be no impact on interactive (Online) users requests.

## If I am facing performance issue in Dynamics 365 Finance while loading a page or processing a business document, how is that performance issue different from throttling?

Throttling will help maintain a healthy system when there is a resource constraint and it will not impact any page actions.

## How can I determine the wait time before retrying a throttled request?

When a request is throttled, the response header will include a time to be used in retry logic.

## Is it recommended to use a dedicated integration account, instead of just the generic admin user account?

Yes, it is recommended but is not mandatory.

## Is throttling dependent on the Tier your environment is running on?

In the initial release, No. Throttling will calculate its threshold based on the resources available for each environment.

## Is there any specification on legal entity?

No.

## Does throttling impact BYOD export?

No.

## Will throttling monitoring be available you are in Azure Application Insights?

Monitoring will be onboarded to any available tool in the future.

## If a Production environment is regularly running out of resources wouldn't Microsoft need to re-size it? 

Yes. Sizing estimate will also need to be revalidated and uploaded.

## After April 2021, could priority-based throttling be overridden by the system?

The system will use default values if no priorities are configured after April 2021.

## Can the throttling engine be configured (thresholds)?

No.



