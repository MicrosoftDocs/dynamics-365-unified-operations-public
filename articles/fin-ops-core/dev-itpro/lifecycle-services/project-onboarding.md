---
title: Project onboarding
description: This article provides information about the Project onboarding wizard in Microsoft Dynamics 365 Lifecycle Services.
author: vetrivicky
ms.date: 06/20/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: vetric
ms.search.validFrom: 2020-5-12 
ms.dyn365.ops.version:  
---

# Project onboarding

[!include [banner](../includes/banner.md)]


Project onboarding is a self-paced, wizard-driven onboarding experience that guides project users in Microsoft Dynamics 365 Lifecycle Services through the process of setting up the key configuration components for a new implementation project for Dynamic 365 Finance, Dynamics 365 Supply Chain Management, or Dynamic 365 Retail. This wizard can also be accessed during and after the implementation, and can be used to update the information as required.

Microsoft relies on the information that you provide. You must provide the most current and accurate data as you complete Project onboarding. After you complete Project onboarding, you can deploy environments and continue with the project implementation.

To access Project onboarding, sign in to Lifecycle Services, and then, on the main menu, select **Project onboarding**.

> [!NOTE]
> Project onboarding is available for implementation projects and must be completed before any of the Microsoft-managed environments are deployed. For more information about implementation projects, see [Lifecycle Services for finance and operations apps customers](lcs-works-lcs.md#lifecycle-services-workspace-for-the-current-versions-of-the-finance-and-operations-apps).

> [!NOTE]
> Before completing the project onboarding it is important to consider any data residency requirements and make sure the implementation project is created in the correct Lifecycle Services geography. For more information about deployment options across different geographies, see [Dynamics 365 Finance, Supply Chain Management, and Commerce in local geographies](../deployment/deployment-options-geo.md).


For more information about the onboarding process, see [Onboard an implementation project](../../fin-ops/imp-lifecycle/onboard.md#lcs-implementation-project-workspace), and watch the [finance and operations: Onboarding to Dynamics 365](https://community.dynamics.com/365/b/techtalks/posts/finance-and-operations-onboarding-to-dynamics-365-1-10-19) TechTalk.


## Onboarding steps

Each step in Project onboarding is designed to give you guidance about the project implementation or to gather information about the project context, so that the FastTrack team can better serve you. By providing accurate information in the wizard, you help Microsoft understand your implementation plan, so that it can provide appropriate guidance.

You can move through the wizard either by using the **Next** and **Back** buttons, or by selecting each step directly. For some steps, the right column of the page shows additional contextual information that will help you complete the step.

## Welcome

The **Welcome** page provides general guidance and information that you will need to complete Project onboarding.

## Project overview

- Provide the overview information for the implementation project.
- Describe the vision and goals for the project in a few sentences. This information will help Microsoft understand the goals that you want to achieve and how you define success for the project.
- Provide the Partner MPN ID, which you can get from the implementation partner team. If a partner is not involved or not yet identified, choose the appropriate option in the implementation partner drop-down list. Note that providing accurate partner data is a pre-requisite for [FastTrack Program](/dynamics365/fasttrack/?toc=/dynamics365/commerce/toc.json) assignment. You could miss the opportunity for valuable services if you do not provide the correct partner information. Once partner identified, you need to update the MPN ID.
- Specify the estimated number of user licenses after full roll-out including current licenses. This number can differ from the current license purchase. If no change is planned, provide the current user license count. If a license type isn't applicable, enter **0** (zero).
- If your implementation project is a demo project, or if you're moving from another tenant, provide the details.

## Project scope

- Provide information about how you plan to scope the implementation in terms of features and products. This information will help Microsoft understand your implementation and provide any guidance that is required.
- After you set the option for specific features to **Yes** in this step, you must provide additional data that is related to those features. This data will help Microsoft have a better engagement with you during the implementation. The additional data fields are mandatory.

## Define your team

- Verify that all project team members are invited and configured.
- Set the **Primary contact for FastTrack** option to **Yes** for at least two users who have an active email address in the user list. If this option isn't set to **Yes** for any team member, FastTrack will reach out to all team members for implementation guidance during your implementation. If necessary, you should nominate at least one customer and one partner team member to be contacted by FastTrack.
- Each team member will be assigned a project security role and an implementation role. The project security role is relevant to access to the Lifecycle Services project workspace, and the implementation role is relevant to the individual team member's role on the implementation team. We highly recommend that you include representatives from the customer among the project team members who have a monitored email address.

For more information, see [Configuring project security](configure-lcs-security.md#configuring-project-security) and [Roles in a Dynamics 365 implementation](/training/modules/get-started-implementation-project/01-2-roles).

## Define milestone dates

- Define all mandatory milestone steps. Milestones are associated with the methodology of the project. If the milestone dates haven't yet been decided, use tentative dates.
- Update the milestone dates as plans change. Microsoft uses the milestone dates to provide appropriate guidance for each milestone. To edit milestone dates, select the pencil symbol.

## Associate Lifecycle Services with Azure DevOps

- Connect Lifecycle Services and Azure DevOps to maintain the application lifecycle.
- Enter the root URL of your Azure DevOps account and the personal access token that you obtained from Azure DevOps. The Azure DevOps account should belong to the customer.

> [!NOTE]
> Lifecycle Services requires entering the Azure DevOps root URL in the legacy format. The legacy format is `https://ACCOUNT.visualstudio.com` and `https://contoso.visualstudio.com` is an example.

## Configure Azure DevOps

- Map work items between Lifecycle Services and Business process modeler (BPM).
- Acknowledge the setup.
- If you choose to use a custom process template, follow these best practices:

    - Don't remove any existing work item types.
    - Don't remove any existing state for a work item type.
    - Don't add any required fields to a work item type.

## FastTrack

- The **FastTrack** page introduces the FastTrack program. It explains what the program consists of and how your implementation can benefit from it.
- We strongly recommend that you watch the existing [TechTalks](https://community.dynamics.com/365/b/alltechtalks) and subscribe to upcoming TechTalks as Microsoft continues to share best practice guidance and information about the changes that are occurring in the product and platform.

## Next steps

The **Next Steps** page provides additional resources about the most critical aspects of the implementation. You can access this page at any time during the implementation.

## Complete onboarding

- Complete Project onboarding so that you can move on to the next steps in your implementation.
- You can complete Project onboarding only after all previous steps have been completed. If any previous steps haven't been completed, the **Complete onboarding** button won't be available.
- Any skipped steps are marked with an asterisk (\*). You can also view any missing steps.
- After you complete Project onboarding, you can continue to update information, such as project scope values.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
