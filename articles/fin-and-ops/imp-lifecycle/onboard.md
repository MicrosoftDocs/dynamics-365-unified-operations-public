---
# required metadata

title: Onboard a Finance and Operations implementation project
description: This topic describes how to onboard a Microsoft Dynamics 365 for Finance and Operations project by using Microsoft Dynamics Lifecycle Services (LCS).
author: ClaudiaBetz-Haubold
manager: AnnBe
ms.date: 02/09/2018
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

# Onboard a Finance and Operations implementation project

[!include [banner](../includes/banner.md)]

This topic describes how to onboard a Microsoft Dynamics 365 for Finance and Operations project by using Microsoft Dynamics Lifecycle Services (LCS).

## Microsoft 365 Admin Center

After your organiation has purchased a subscription to Finance and Operations, it is activated on your organization's tenant by the Tenant Administrator who must complete the following steps:
1. Open an Inprivate/Incognito browser session and navigate to the [Microsoft 365 Admin Center](https://admin.microsoft.com/)
2. Login with the Tenant Administrator credentials.
3. Navigate to Billing > Subscriptions and confirm that there is an active Dynamics 365 Unified Operations subscription. Note that if you do not see a subscription, consult with your Licensing Partner to confirm the status of the subscription transaction as well as the tenant for the subscription. By default, all Microsoft Online Services should be running on the same AAD tenant.
4. If there is an active Dynamics 365 Unified Operations subscription, you may proceed by logging in LCS to trigger the LCS Implementation Project creation flow.
5. Open another private browser tab and naviate to [Lifecycle Services](https://lcs.dynamics.com). Click Login to login to LCS with your current Tenant Admin credentials.
6. Accept and confirm any other prompts displayed to complete the Implementation Project provisioning.
7. The Tenant Administrator has now been assigned as the Project Owner to the Implementation Project. 
8. As a final step, the Tenant Administrator must add the additional internal and partner team members who will be participating in the Dynamics 365 Finance and Operations implementation project. This is perfomed in LCS Project User Management:

![LCS Project User Management](./media/LCSProjectUsersMenu.PNG)

## LCS Implementation project workspace

After the Tenant Administrator has completed the Finance and Operations subscription activation, an **Implementation project** workspace is provisioned in LCS when the tenant administrator signs in for the first time. 

If you're a customer and require help to get started with LCS, see [Lifecycle Services for Finance and Operations customers](../../dev-itpro/lifecycle-services/lcs-works-lcs.md). For a comprehensive overview of LCS, see [Overview of Lifecycle Services](../../dev-itpro/lifecycle-services/lcs-works-lcs.md).

## FastTrack onboarding services

After your LCS **Implementation project** workspace is provisioned, the Microsoft FastTrack team will contact your project team to discuss onboarding services. For more information about the FastTrack program and the services that it offers, see [Microsoft FastTrack for Dynamics 365](../get-started/fasttrack-dynamics-365-overview.md).

The FastTrack team will contact all the partner and customer users in your LCS project to schedule a 60-minute onboarding call via Skype. During this call, the team will introduce the FastTrack program. The team will also help you with the initial configuration of the LCS project and related tasks:

- Tenant validation
- Introduction to LCS
- Setup of LCS project users
- Setup of Microsoft Azure DevOps
- Subscription estimator/Usage profiler
- Environment planning
- Environment deployment
- Introduction to servicing, support, and service health
- Readiness planning

We recommend that the people in the following project roles participate in the meeting. People in other roles are optional.

**Customer**

- Project owner
- Microsoft Business Center administrator, if the license was procured through a Volume Service agreement with Microsoft

**Partner**

- Delivery lead/solution architect
- Project manager

## Key data to keep current in LCS

We recommend that you add key project members (such as project managers) to the LCS project. Be sure to include each person's work email address. In this way, you help us work best with you and help guarantee that project members don't miss important communication from us.

Be sure to keep the milestone dates in your LCS project current. In this way, you help us connect with you at different project stages. When you're closer to your go-live date, we will contact you for a project Go-live assessment before we deploy your production environment.

Milestone dates are stored in the LCS implementation methodology. For more information, see the [Methodologies](../../dev-itpro/lifecycle-services/lcs-works-lcs.md#methodologies) section of the "LCS for Customers" topic.

The onboarding call is an optional service. Partners who are experienced with Finance and Operations implementations can work through the tasks with their customers without the help of the FastTrack team. In these cases, it's especially important that you keep the project users and milestone dates current.
