---
# required metadata

title: Insider program
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: sarvanisathish
manager: AnnBe
ms.date: 12/07/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global 
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: 8.1.1

---

# Modern Infrastructure Stack

[!include[banner](../includes/banner.md)]

## Overview

Welcome to the modern infrastructure stack for Dynamics 365 Finance & Operations! We are excited to launch Finance and Operations service on our next generation infrastructure. This new architecture will benefit both customers and Microsoft, as it will provide easier deployment options.

## Value proposition

As a customer onboarding to the modern infrastructure stack, some of the key benefits you will experience are:

-   **Significantly reduced deployment times:** Deployment times reduced by more than 30% - 50%.

-   **Self-service deployment:** Self-service deployment is now available, which means that you no longer need to log a service request to acquire an environment.

-   **Repeatable deployments:** You will now have a high degree of repeatability and reliability in pushing your customization updates from Sandbox to Production.

## Who is eligible to deploy on the modern infrastructure stack?

Finance and Operations customers who are provisioned with an LCS project on or after 12/10/2018 are eligible to deploy on the modern infrastruture.

## Release build version

|    |   |
|-------------|-----------|
| **Application** | 8.1.1     |
| **Platform**   | Update 21 |

## Customizations

Customizations built on Application version 8.1 and Platform update 20 are compatible with the current release.

## What’s new or changed?

-   LCS project: You will be assigned a new Lifecycle Services (LCS) project that is different from the current implementation project type. You will use this project to perform all actions on your environments. Environment types and actions included in the modern infrastructure are for Tier 2+ Sandbox environments only. There is no change in experience to the Tier 1 Sandbox environments.

-   Self-service deployment: You will now be able to trigger the environment deployment directly from LCS, which means that you no longer need a service request for deployment.

-   Move customizations from DevTest to Sandbox: Self-service will be enabled so you can easily apply updates and database movement scenarios across all environments.

-   No remote desktop access: You will no longer be able to remote desktop into Sandbox environments. Self-service will be enabled for all tasks that are commonly performed on these environments.
