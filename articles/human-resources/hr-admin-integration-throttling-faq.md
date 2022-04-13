---
# required metadata

title: Throttling in Human Resources FAQ
description: This topic provides answers to some frequently asked questions (FAQs) about throttling for Open Data Protocol (OData) and custom service-based integrations in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 01/22/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Admin
# ms.devlang: 
# ms.search.scope: Human Resources
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2021-01-22
ms.dyn365.ops.version: Human Resources

---

# Throttling FAQ

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic provides answers to some frequently asked questions (FAQ) about throttling for Open Data Protocol (OData) and custom service-based integrations in Dynamics 365 Human Resources. Throttling prevents the over-utilization of resources. It preserves system responsiveness and ensures consistent availability and performance.

## What happens when a request is throttled?

For OData and custom service requests, a 429 error "Too many requests", will occur.  

When a request is throttled, the system provides a value indicating the duration before any new requests from the user can be processed. When a request is throttled and a 429 error occurs, the response header will include a **Retry-After** interval, which can be used to retry the request after a specific number of seconds. The following example shows this operation. 

```C#
    if (!response.IsSuccessStatusCode) 
            { 
                if ((int)response.StatusCode == 429) 
                { 
                    int seconds = 30; 
                    //Try to use the Retry-After header value if it is returned. 
                    if (response.Headers.Contains("Retry-After")) 
                    { 
                        seconds = int.Parse(response.Headers.GetValues("Retry-After").FirstOrDefault()); 
                    } 
                    Thread.Sleep(TimeSpan.FromSeconds(seconds)); 



                    // Retry sending the request.
                } 
            } 
```

## What are the current throttling limits for the Human Resources service?

The throttling limits for the Human Resources service are based on three categories:

- **API burst:** 500 requests in 5 minutes
- **Time usage:** 5 minutes of total execution time in 5 minutes
- **Concurrency:** 25 requests at any given time

## How do I access the Data management Yammer group?

Follow this link: [Data management Yammer group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=13408417).

## Will a retry request receive preferential treatment over a new request?

No.

## Will throttling affect the Data Import/Export Framework (DIXF) and batch?

No. Throttling is only for OData and custom service integrations.

## What happens to requests if the user didn't retry a throttled request?

Currently, if a request isn't retried when a 429 error is received, the request won't be processed.

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


[!INCLUDE[footer-include](../includes/footer-banner.md)]
