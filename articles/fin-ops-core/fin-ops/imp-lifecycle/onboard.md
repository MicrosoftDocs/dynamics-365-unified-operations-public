---
# required metadata

title: Onboard an implementation project
description: This topic describes how to onboard a project by using Microsoft Dynamics Lifecycle Services (LCS).
author: ClaudiaBetz-Haubold
manager: AnnBe
ms.date: 02/11/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: chaubold
ms.search.validFrom: 2018-01-31
ms.dyn365.ops.version: July 2017 update
---

# Onboard an implementation project

[!include [banner](../includes/banner.md)]

This topic describes how to onboard a Finance and Operations project by using Microsoft Dynamics Lifecycle Services (LCS).

## Microsoft 365 Admin Center

After your organization has purchased a subscription to Finance and Operations, it must be activated on your organization's Azure Active Directory (Azure AD) tenant by your Tenant Administrator, who completes the following steps:

1. Open an Inprivate/Incognito browser session and go to the [Microsoft 365 Admin Center](https://admin.microsoft.com/).
2. Sign in with the Tenant Administrator credentials.
3. Go to **Billing > Products & services** and confirm that there is an active subscription for the application that you want to deploy. 
   > [!NOTE]
   > If you do not see an active subscription, consult with your Licensing Partner to confirm the status of the subscription transaction as well as the tenant for the subscription. By default, all Microsoft Online Services should be running on the same Azure AD tenant.
4. If the subscription in question is shown as active, proceed to the next step by signing in to LCS to trigger the Implementation Project creation flow.
5. Open another private browser tab and go to [Lifecycle Services](https://lcs.dynamics.com). Select **Login** to access LCS with your current Tenant Admin credentials.
6. Accept and confirm any other prompts displayed to complete the Implementation Project provisioning.
7. The Tenant Administrator is assigned the Project Owner security role in the provisioned Implementation Project.  
   > [!NOTE]
   > If the Tenant Administrator will not be a participant in the implementation, at least one additional Project Owner must be assigned to the implementation project.

   For an overview of LCS user management, including the security roles that can be assigned to users, see [Configure Lifecycle Services (LCS) security](../../dev-itpro/lifecycle-services/configure-lcs-security.md#configuring-project-security).

## LCS implementation project workspace

After the Tenant Administrator has completed the Finance and Operations subscription activation and added additional project owners as appropriate, those team members can access the **Implementation project** workspace.

The first step to be completed in LCS is **Project onboarding**. This step is required for all LCS implementation projects that are created **on or after August 22, 2019, PST**, prior to deploying any of the Microsoft-managed environments. You can access the **Project onboarding** feature using the action center notification or the LCS Implementation project menu. You must be assigned to the Project owner security role to access **Project onboarding** in LCS.

To get started with LCS, see [Lifecycle Services (LCS) for Finance and Operations apps customers](../../dev-itpro/lifecycle-services/lcs-works-lcs.md). 

## FastTrack onboarding services

After the LCS **Implementation project** workspace is provisioned, the Microsoft FastTrack team will monitor your onboarding progress. For more information about the FastTrack program and the services provided, see [Microsoft FastTrack](../get-started/fasttrack-dynamics-365-overview.md).

All LCS **Implementation projects** will receive an email from the FastTrack team welcoming them to the service after they successfully complete the project onboarding. If project onboarding is not completed within a few weeks after creating an LCS **Implementation project** creation, a reminder will be sent to the project team.

> [!NOTE]
> All onboarding-related emails from the FastTrack team will originate from Dynamics 365 Onboarding (<ond365@microsoft.com>), so please ensure that any spam blocker/filter allows email from this address.


## Key data to keep current in LCS

We recommend that you add key project members (such as project managers) from the customer and partner teams to the LCS implementation project. Be sure to include each person's work email address. In this way, you help us work best with you and help ensure that project members don't miss important communication from us.

Be sure to keep the milestone dates in your LCS project current. In this way, you help us connect with you at different project stages. When you're closer to your go-live date, we will contact you for a project Go-live assessment before we deploy your production environment.

Milestone dates are stored in the LCS implementation methodology. For more information, see the [Methodologies](../../dev-itpro/lifecycle-services/lcs-works-lcs.md#methodologies) section of the "LCS for Customers" topic.


