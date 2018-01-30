---
# required metadata

title: Preparing for go live with a Microsoft Dynamics 365 for Finance and Operations, Enterprise edition project 
description: This topic describes how to prepare to go live with a Microsoft Dynamics 365 for Finance and Operations, Enterprise edition project using Microsoft Lifecycle Services.
author: ClaudiaBetz-Haubold
manager: AnnBe
ms.date: 01/18/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: chaubold
ms.search.validFrom: 2018-01-31
ms.dyn365.ops.version: July 2017 update
---

# Preparing for go live

[!include[banner](../includes/banner.md)]

This topic describes how to prepare to go live with a Microsoft Dynamics 365 for Finance and Operations, Enterprise edition project using Microsoft Lifecycle Services (LCS).

## Completing LCS Methodology

A major milestone in each implementation project is the cutover to the production environment.

To ensure the environment is used for live operations, we will provision the production instance only after the implementation nears the Operate phase after completion of the required activities in the LCS methodology. For more information about the environments
within your subscription, see the [Licensing Guide](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE1CkHI).

Customers must complete the *Analysis*, *Design and develop*, and *Test* phases in the LCS methodology before the Configure button to request the production environment becomes enabled. To complete a phase in LCS, you must first complete each required step in that phase. When all steps in a phase are completed, you can complete the entire phase. You can always reopen a phase later if you need
to make changes. If you need more help, see [Lifecycle Services for Finance and Operations customers](../../dev-itpro/lifecycle-services/lcs-works-lcs.md).

Completing a step has two components to it:

-   Performing the actual work, such as a Fit-gap analysis or a User acceptance test (UAT)
-   Marking the corresponding step in the LCS methodology as complete

It is good practice to complete the steps in the methodology as you progress with the implementation. Do not wait until the last minute. Do not simply click through all steps just to get to a Production environment; it is in the customer’s best interest to have a solid implementation. 

## User acceptance testing for your solution

Once you have completed the *Test* phase, you should have tested all the business processes that you have implemented as well as any customizations you have made on a *Sandbox: Standard Acceptance Test* environment in the implementation project. For a successful Go-live it is important to complete the UAT phase with the following in mind:

-   Test cases cover the entire scope of requirements
-   Test with migrated data including master data and opening balances even if those are not final yet
-   Test with the right security roles (default and custom roles) assigned to users
-   Make sure the solution adheres to company/industry specific compliance, if any
-   Document all features and get approval and sign off from the customer

It is not sufficient to test on an environment that is a developer or demo topology, no matter whether it is cloud-hosted or a downloaded VHD, for the following reasons:

-   The topology of the Tier-1 environments is different from that of your production environment. It is important to test every functionality, but especially integrations, printing, workflow, as well as warehouse and retail devices, on a Tier-2 or higher sandbox environment in the Microsoft-managed subscription.
-   The performance of the system cannot be measured when you do the UAT on local or privately hosted VMs.
-   It is important that the team experiences the servicing in LCS (applying deployable packages, creating service requests, moving database between environments, and others) during the implementation to prevent delays during the cutover process.

## FastTrack go live assessment

Dynamics 365 for Finance and Operations, Enterprise edition customers should complete a Pre-Go-live review with the Microsoft FastTrack team before requesting their production environment. If you are not familiar with Microsoft FastTrack, see the [Microsoft FastTrack for Dynamics 365 overview](../get-started/fasttrack-dynamics-365-overview.md).

The FastTrack team will ask you to populate a Pre-Go-Live Checklist about 8 weeks prior to go live:

-   If you have over 150 seats, and have a Microsoft solutions architect assigned to your project, they will reach out to you
-   If you have 20-149 seats, the checklist will be sent to you from <go-live@microsoft.com>.

You can also download the checklist from CustomerSource: [FastTrack Pre-Go-live Checklist for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition](https://mbs.microsoft.com/customersource/Global/365Enterprise/learning/documentation/installation-setup-guides/fasttrack-checklist-fin-and-ops).

The project manager or a key project member must complete this checklist during the Pre-Go-live phase of the project, generally 4–6 weeks before the proposed Go-live date, when UAT is completed or almost completed.

When you have completed this checklist:
-   If you have over 150 seats, and have a Microsoft solutions architect assigned to your project, send it to them.
-   If you have 20-149 seats, send it to <go-live@microsoft.com>.

After the checklist is submitted, a Microsoft solutions architect will review the project and provide an assessment that describes the potential risks, best practices, and recommendations for a successful Go-live of the project. In some cases, the solutions architect might highlight risk factors and ask for a mitigation plan. When the assessment is completed, the solutions architect will indicate that you’re ready to request the production environment in LCS.

If you request the production environment before the assessment is complete, the deployment will be on hold until the assessment has been finished successfully.

## Requesting the production environment

When the *Analysis*, *Design and develop*, and *Test* phases in the LCS methodology have been completed by you and the Go-live assessment concluded that the project is ready, you can request your production environment.

It is recommended that you select a generic user account to be the Admin user of the environments that you deploy. This is important because if you use a named user account you might not be able to access an environment if that user is not
available. Some scenarios where only the Admin user can access an environment are:

-   First log-on after initial deployment to any environment – in that case the Admin is the only user that can access the environment
-   First log-on to a sandbox environment after a database refresh from Production – in that case all user accounts except for the Admin account are disabled

Your production environment should be deployed to the same data center where your sandbox environments are deployed.

Once you have signed off on the request for production environment, Microsoft is responsible to deploy the Production environment for you. Microsoft’s service level agreement (SLA) for deploying production environment is *48 hours*. Production may be deployed
anytime within 48 hours from when you submitted the request, assuming your usage profile does not require additional information. You can see the progress of the deployment in LCS. It is normal for the request to remain in *Queued* state for
a few hours before it changes to *Deploying*.

When you submit the deployment request, a service request for the Microsoft Dynamics Service Engineering (DSE) team gets created automatically, and you can see it in the Service requests list in LCS. If DSE has questions for you that prevent them from deploying the Production environment – such as the ask to update the subscription estimate or to change the data center – they will add a
comment to the service request. In some cases, it might be necessary that you clear the sign off from the Production deployment request to make changes. This is possible while the Production environment request is in Queued state. When you click on the Queued button, you can then clear sign off. The environment will go back to the Configure status. You can then make any changes that are
necessary and sign off again.
