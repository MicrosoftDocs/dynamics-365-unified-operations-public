---
# required metadata

title: [Topic name]
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: [author's GitHub alias]
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: [Pick one: Application User/Developer/IT Pro]
# ms.devlang: 
ms.reviewer: [Content Strategist microsoft alias]
ms.search.scope: [Which Operations client to show this topic as help for, to be set by content strategist, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: [author's Microsoft alias]
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

# Environment planning

[!include[banner](../includes/banner.md)]

This article provides an overview of the different aspects you must consider
while doing the environment planning for your project. Discussing environment
planning early in the project is key to the success of your Dynamics 365 for
Finance and Operations Cloud implementation.

## Environment planning overview

Let’s start with a few important concepts:

-   ***Environment purpose*** represents the reason(s) why the environment exists.
    For example; development, system testing, User Acceptance Testing (UAT),
    Operations.

-   ***Environment topology*** represents the composition of the environment and
    ultimately the purpose. For example; **Develop** or **Build and Test** for
    Tier-1 environments.

-   ***Environment Tier*** represents the type or category of the environment. For
    example; Tier-1, Tier-2 environment. For more information, about the
    different environments and Tiers download the latest Microsoft Dynamics 365
    Licensing Guide from [Dynamics 365 pricing](https://dynamics.microsoft.com/en-us/pricing/)
    

### Environment types

-   **Standard environments** are included in the standard offer and managed by
    Microsoft in a Microsoft subscription. For example: the **Production**
    environment, one Tier-2 **Standard Acceptance Test** environment, and one
    Tier-1 **Develop and Test** environment.

-   **Add-on environments** are environments in a Microsoft managed subscription
    purchased by the customer in addition to the standard offer. For example; an
    additional Tier-4 environment for performance testing.

-   **Cloud-Hosted environments** are additional environments managed by the
    customer or partner in a customer or partner Azure subscription. For
    example; a Tier-1 demo environment.

-   **Environment image (.VHD)** are additional Tier-1 environments hosted
    on-premises through the use of a VHD downloadable from [Lifecycle
    Services](https://lcs.dynamics.com/v2) (LCS).

> [!IMPORTANT]
> A *customer or partner Azure subscription* means that the
customer or partner brings their own Azure subscription and deploys Dynamics 365
for Finance and Operations environments to it, for evaluation and development
purposes only. The customer or partner pays for the resources deployed to their
Azure subscription based on the Azure price list. A *Microsoft subscription*
means that the customer purchases Dynamics 365 for Finance and Operations
licenses which will then allow them to deploy environments to an Azure
subscription managed by Microsoft, therefore, the customer has no separate Azure
billing.

