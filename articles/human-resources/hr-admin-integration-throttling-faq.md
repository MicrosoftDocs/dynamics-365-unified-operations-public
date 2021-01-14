---
# required metadata

title: Priority-based throttling in Human Resources FAQ
description: This topic provides answers to some frequently asked questions (FAQ) about priority-based throttling for Open Data Protocol (OData) and custom service-based integrations in Dynamics 365 Human Resources.
author: andreabichsel
manager: tfehr
ms.date: 01/14/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Admin
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2021-01-14
ms.dyn365.ops.version: Human Resources

---

# Priority-based throttling in Human Resources FAQ

This topic provides answers to some frequently asked questions (FAQ) about [priority-based throttling](hr-admin-integration-throttling.md) for Open Data Protocol (OData) and custom service-based integrations.

## How do I access the Data management Yammer group?

Follow this link: [Data management Yammer group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=13408417).

## Will a retry request receive preferential treatment over a new request?

No.

## Will throttling affect the Data Import/Export Framework (DIXF) and batch?

No. Throttling is only for OData and custom service integrations.

## What happens to requests if the user didn't retry a throttled request?

Currently, if a request isn't retried when a 429 error is received, the request won't be processed.

## Are there plans to provide an option for the Priority mapping grid entry?

Microsoft will consider this request in a future release.

## Will the requests of my interactive users be throttled?

No. There will be no impact on the requests of interactive (online) users.

## If I experience a performance issue in Dynamics 365 Human Resources while a page is being loaded or a business document is being processed, how does that performance issue differ from throttling?

Throttling helps maintain a healthy system when there's a resource constraint. It won't affect any page actions.

## How can I determine the wait time before I retry a throttled request?

When a request is throttled, the response header includes a time that will be used in retry logic.

## Do you recommend that I use a dedicated integration account instead of just the generic admin user account?

Yes, we recommend this approach. However, it isn't mandatory.

## Is throttling functionality legal entity–specific?

No.

## Does throttling affect bring your own database (BYOD) export?

No.

## Can the throttling engine be configured (thresholds)?

No.
