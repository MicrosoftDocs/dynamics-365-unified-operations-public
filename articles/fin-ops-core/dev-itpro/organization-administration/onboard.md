---
title: Onboard an implementation project
description: Learn about how to onboard a project by using Microsoft Dynamics Lifecycle Services (LCS), including an overview of the Microsoft 365 Admin Center.
author: OlgaPetrovaFT
ms.author: johnmichalak 
ms.topic: article
ms.date: 03/17/2026
ms.custom:
ms.reviewer: johnmichalak 
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-01-31
ms.search.form:
ms.dyn365.ops.version: July 2017 update
---

# Onboard an implementation project

[!include [banner](../../../finance/includes/banner.md)]

This article describes how to onboard a finance and operations project by using Microsoft Dynamics Lifecycle Services (LCS).

## Microsoft 365 Admin Center

After your organization purchases a subscription to a finance and operations app, a tenant administrator must activate the service on your organization's Microsoft Entra tenant. For more information about Microsoft Entra roles, see [Understand roles in Microsoft Entra ID](/azure/active-directory/roles/concept-understand-roles).

The tenant administrator must complete the following steps:

1. Open an InPrivate or Incognito browser session and go to the [Microsoft 365 Admin Center](https://admin.microsoft.com/).
1. Sign in by using your tenant administrator credentials.
1. Go to **Billing** > **Products & services** and confirm that there's an active subscription for the application that you want to deploy. 
   > [!NOTE]
   > If you don't see an active subscription, consult with your licensing partner to confirm the status of the subscription transaction. It's important to confirm that you purchased the subscriptions for the correct Microsoft Entra tenant.  By default, all Microsoft online services run on the same Microsoft Entra tenant. The most frequent cause for onboarding delays is that subscriptions are inadvertently placed on an incorrect Microsoft Entra tenant. 
1. If the subscription is active, proceed to the next step by signing in to LCS to trigger the implementation project creation flow.
1. Open another private browser tab and go to [Lifecycle Services](https://lcs.dynamics.com). Select **Login** to access LCS by using your current tenant administrator credentials.
   > [!NOTE]
   > Connection endpoints might be different for Government Community Cloud (GCC) and other local cloud deployment options. For more information, see [Sovereign and local cloud deployment options for Dynamics 365 Finance and Dynamics 365 Supply Chain Management](../deployment/deployment-options-geo.md).
1. Accept and confirm any other prompts displayed to complete the implementation project provisioning.
1. The tenant administrator is assigned the Project Owner security role in the provisioned implementation project.  
   > [!NOTE]
   > If the tenant administrator won't be a participant in the implementation, assign at least one additional Project Owner to the implementation project.

   For an overview of LCS user management, including the security roles that you can assign to users, see [Configure Lifecycle Services (LCS) security](../lifecycle-services/configure-lcs-security.md#configuring-project-security).

## LCS implementation project workspace

After the tenant administrator finishes the finance and operations subscription activation and adds extra project users as needed, those team members can access the **Implementation project** workspace.

The first step to complete in LCS is **Project onboarding**. This step is required for all LCS implementation projects that are created **on or after August 22, 2019, PST**, before deploying any of the Microsoft-managed environments. You can access the **Project onboarding** feature by using the action center notification or the LCS Implementation project menu. You must be assigned to the Project owner security role to access **Project onboarding** in LCS.

To get started with LCS, see [Lifecycle Services (LCS) for finance and operations apps customers](../lifecycle-services/lcs-works-lcs.md). 

## FastTrack onboarding services

After the LCS **Implementation project** workspace is provisioned, the Microsoft FastTrack team monitors your onboarding progress. If you don't complete project onboarding within a few weeks after creating an LCS **Implementation project**, the FastTrack team sends a reminder to the project team. 

For more information about the FastTrack program and the services it provides, see [Microsoft FastTrack](/dynamics365/fasttrack/).

For more information about LCS project onboarding, see [LCS project onboarding](../lifecycle-services/project-onboarding.md).


> [!NOTE]
> All onboarding-related emails from the FastTrack team come from Dynamics 365 Onboarding (<ond365@microsoft.com>). Make sure your spam blocker or filter allows email from this address.


## Key data to keep current in LCS

Add key project members, such as project managers, from the customer and partner teams to the LCS implementation project. Include each person's work email address. By keeping this information current, you help us work best with you and help ensure that project members don't miss important communication from us.

Keep the milestone dates in your LCS project current. By keeping these dates up to date, you help us connect with you at different project stages. When you're closer to your go-live date, we contact you for a project Go-live assessment before we deploy your production environment.

LCS stores milestone dates in the implementation methodology. For more information, see the [Methodologies](../lifecycle-services/lcs-works-lcs.md#methodologies) section of the *LCS for Customers* article.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
