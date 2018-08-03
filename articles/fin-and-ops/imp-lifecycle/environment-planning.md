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

-   **Cloud-hosted environments** are additional environments managed by the
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

### Tier-1 versus Tier-2+
INSERT TABLE HERE

## Microsoft Dynamics 365 for Finance and Operations Standard Cloud Offer

With each Microsoft Dynamics 365 for Finance and Operations Standard Cloud
Offer, three environments are included by default:

-   ***Tier-1 environment: Develop and Test:*** One Developer/Test instance for the
    duration of the subscription. Additional Developer/Test instances can be
    purchased separately as an optional add-on. This is a non-production single
    box instance that customer can use as an automated build environment and/or
    to customize Microsoft Dynamics 365 for Finance and Operations and unit test
    their changes.

-   ***Tier-2 environment: Standard Acceptance Testing:*** One Standard Acceptance
    Testing (UAT) instance for the duration of the subscription. Additional
    Sandbox/Staging instances can be purchased separately as an optional add-on.
    This is a non-production multi-box instance that customers can use for User
    Acceptance Testing, Integration Testing and Training.

-   ***PRODUCTION environment:*** One production instance per tenant. The production
    multi-box instance comes with Disaster Recovery and High Availability. It
    will be provisioned once the implementation nears the ‘operate’ phase after
    completion of the required activities in the Microsoft Dynamics Lifecycle
    Services (LCS) methodology and successful go-live assessment.

Additionally, a certain amount of File storage and Database storage is included
in the offer:

-   ***File storage:*** Each customer will receive 100GB of file/Azure Binary Large
    Objects (BLOBs) cloud storage for files and binary data. Additional
    file/blob storage can be purchased.

-   ***Database storage:*** Each Dynamics 365 for Finance and Operations
    subscription includes 10GB of Azure SQL database storage at no additional
    charge per customer. Additional storage capacity is granted at no charge as
    an organization increases the number of User and Device SLs.

For more information, about the different environments and storage download the
latest Microsoft Dynamics 365 Licensing Guide from [Dynamics 365
pricing](https://dynamics.microsoft.com/en-us/pricing/)

### Standard Environments Provisioning

The different Dynamics 365 for Finance and Operations environments will get
provisioned at a different timing. This is the overview for the Microsoft
Dynamics 365 for Finance and Operations Standard Cloud Offer:
INSERT TABLE HERE

> [!IMPORTANT]
> Always deploy environments using an **unnamed** account (such as *dynadmin@customer.com*). Deploy and leverage the Develop and Test
environment with the build topology as it simplifies the builds management and initialize automatically the VSTS source repository.

### Production System Readiness

Production environment can be deployed when the project is ready for the initial
go-live. See [Prepare for go-live](prepare-go-live.md) for detailed information.

Production System readiness includes, but is not limited to:

-   Up to date subscription estimate activated as described in [Subscription estimator](../../dev-itpro/lifecycle-services/subscription-estimator.md)

-   Code, configuration and data are ready for cutover

-   Engineering process in place to manage critical fixes

-   Solution and UAT signed off by customer

-   Cutover plan in place

Production is an environment for the customer to **operate** the solution, not to build it. Production is sized to run your business based on the subscription estimate and performance testing telemetry data. Once deployed, customers can and should perform a mock cutover and a final round of validation on Production. Prior to the final cutover, a Point-In-Time (PiT) restore can be requested to restore Production to a clean snapshot (up to 35 days in the past).
INSERT GRAPHIC
To select the appropriate data center (DC) for Production, consider the latency from the geographic locations where the business operates. Leverage tools like [PsPing](https://docs.microsoft.com/en-us/sysinternals/downloads/psping) and [azurespeed.com](http://azurespeed.com/) to test latency to Azure data centers.

## Additional environments

Additional environments may be purchased as add-ons or deployed as cloud-hosted environments. Below you can find a *sample* overview of standard and additional environments based on complexity of the Microsoft Dynamics 365 for Finance and Operations implementation.
INSERT GRAPHIC

> [!IMPORTANT]
> Always deploy environments using an **unnamed** account (such as *dynadmin@customer.com*). Assign an owner to the environments who will be responsible for their status and maintenance (if applicable). Get an additional Tier-2+ environment post go-live to support Production if you plan to work on new releases

### Deployment considerations for development environments

For development environments there are three different deployment options:

-   Standard or add-on environment managed by Microsoft in a Microsoft subscription

-   Cloud-hosted managed by customer/partner in a customer/partner Azure subscription

-   Environment image (downloadable .VHD) hosted on-premises

Below overview provides a comparison between these different deployment options:

INSERT TABLE

Be aware that you must allocate one development environment per developer.


> [!IMPORTANT]
> The ***Administrator lockdown*** for Tier-1 environments is effective from Platform Update (PU) 12 and higher. Actions where local Administrator access is required are no longer possible (e.g. installing a 3rd party tool, developing Power BI reports…) If Administrator permissions are required, use cloud-hosted environments or environment image (downloadable .VHD) instead. For more information see [Development and build VMs that don't allow admin access FAQ](../../dev-itpro/sysadmin/vms-no-admin-access.md).

### Selecting the right Tier-2+ environment

Depending on the environment purpose (e.g. Performance Testing, UAT…) it is key to select the correct Tier-2+ environment. Below gives a ***baseline*** guidance. You must work with your implementation partner to adjust this *baseline* considering your specific business scenarios (type of users, complexity,volumes…).
INSERT GRAPHIC
Note that transaction lines per hour can be seen in LCS after activating a subscription estimate:
INSERT PICTURE

> [!IMPORTANT]
> The upcoming Administrator lockdown for Tier-2+ environments will no longer allow remote connection (.RDP) to the servers. Microsoft’s roadmap is to replace most common actions where .RDP access is needed by self-service tasks in Lifecycle Services (LCS). As an example, the procedure currently described in [Copy a Finance and Operations database from SQL Server to a production Azure SQL Database environment](../../dev-itpro/database/copy-database-from-sql-server-to-azure-sql.md) would be available as a service from Microsoft via a service request in LCS. More information will be shared through the [LCS Blog](https://blogs.msdn.microsoft.com/lcs/2018/02/27/notice-of-upcoming-change-removing-rdp-access-to-tiers-2-3-4-and-5-standard-acceptance-test-or-sandbox-environments-deployed-in-microsoft-subscription/) and on [Docs](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/).

### Purchasing add-on environments

For purchasing add-on environments, we advise you to work closely with your Cloud Solution Provider (CSP) or License Service Reseller (LSR). Take into consideration the potential lead time from *Placing the order* up to *Deployment of the environment*.
INSERT GRAPHIC

> [!IMPORTANT]
> You can subscribe to add-on environments on a month-by-month basis through the *Microsoft Products and Services Agreement* (MPSA) licensing program (if you have a Volume Licensing agreement with Microsoft) or through the *Cloud Solution Provider* program (CSP). For more information, about the different environments and Tiers, download the latest Microsoft Dynamics 365 Licensing Guide from [Dynamics 365 pricing](https://dynamics.microsoft.com/en-us/pricing/).

## Environments plan

Create the environments plan early in your implementation:

1.  Identify the project activities that require an environment (e.g. developing customizations, maintaining golden configuration data, etc.)

2.  Determine the ***activities lifecycle*** to determine the ***environments lifecycle*** (e.g. when and for how long do you need the environment; do you need it before or after go-live; etc.)

3.  Determine the type and topology of the required environments

4.  Summarize the list of required environments in a matrix

Once the environments are identified, the environments plan can be used to structure the ***Application Lifecycle Management (ALM)*** flows. For example, once you have finalized your environments plan, you can define the flows for building and moving the code and the data across environments.

It is strongly encouraged that you watch the [Environment Planning TechTalk](https://infopedia.eventbuilder.com/event?eventid=o8a5q2&source=Dynamics_365_for_Operations_-_FastTrack_Tech_Talks). From the link, you can also download the *Sample Environment Planning exercise* spreadsheet to get you jump-started on your environment planning exercise.


