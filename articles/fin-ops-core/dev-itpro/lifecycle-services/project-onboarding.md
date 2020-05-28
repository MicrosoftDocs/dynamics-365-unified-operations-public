---
title: Project onboarding
description: This topic provides information about the Project onboarding wizard in Lifecycle Services.
author: vetrivicky
manager: AnnBe
ms.date: 05/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2020-5-12 
ms.dyn365.ops.version:  
---

# Project onboarding

[!include [banner](../includes/banner.md)]

Project Onboarding is a self-paced, wizard-driven onboarding experience that guides Lifecycle Services (LCS) project users to set up the key configuration components for the new implementation project of Dynamic 365 Finance, Dynamics 365 Supply Chain Management or Dynamics 365 Retail. This wizard can also be accessed during and after the implementation to update the information when needed.

At Microsoft, we rely on the information you provide. You must complete your Project onboarding with the most current and accurate data. After you have completed your Project onboarding, you will be able to deploy environments and proceed with the project implementation.

To access Project onboarding, log in to LCS and on the main menu, select **Project onboarding**.

> [!NOTE]
> Project Onboarding is available for implementation projects and must be completed before deploying any of the Microsoft-managed environments. For more information about the implementation project, see [Lifecycle Services (LCS) for Finance and Operations apps customers](lcs-works-lcs.md#lcs-workspace-for-the-current-versions-of-the-finance-and-operations-apps).

For more information about the onboarding process, see [Onboard an implementation project](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/imp-lifecycle/onboard#lcs-implementation-project-workspace) and watch the [Tech Talk, Finance and Operations: Onboarding to Dynamics 365](https://community.dynamics.com/365/b/techtalks/posts/finance-and-operations-onboarding-to-dynamics-365-1-10-19)

## Onboarding steps

Each step in Project onboarding is designed to give you more guidance on the project implementation or gather information on the project context so that the FastTrack team can better serve you. By providing accurate information in this wizard, you help us to understand your implementation plan which helps us guide you where appropriate.

You can navigate through the LCS Project Onboarding wizard using the **Next** and **Back** buttons, or by directly selecting each step. In some steps, you will find additional contextual information in the right-hand column to help you complete the step.

## Welcome

General guidance and information that will be needed to complete project onboarding.   

## Project overview 

- Provide the overview information for this implementation project.
- If you are upgrading from AX 2012, provide the same in the Legacy system. Also you can choose your Legacy system if not upgrading from AX 2012.
- Provide the vision and goals for this project in few sentences. This will help us understand the goals you want to achieve and how you define success for the project.
- Specify the estimated number of future user licenses (Full estimate – after complete roll-out). This number could be different from the current license purchase. If no change is planned, provide the current user license count. Use '0' (zero) if a license type is not applicable.
- If your implementation project is a demo project or moving from another tenant, provide the details.

## Project scope 

- Provide information about how you plan to scope this implementation in terms of features and products. This helps us understand your implementation and provide guidance as needed.
- After you toggle specific features to **Yes** in this step, you will need to provide additional data related to that feature which helps us to have a better engagement with you during the implementation. These additional data fields are mandatory.   

## Define your team 

- Verify all project team members are invited and configured.
- Set the **Primary contact for FastTrack** toggle to **'Yes'** for at least two users with an active email address in the user list. If no team member has this option enabled, FastTrack will reach out to all team members for implementation guidance during your implementation. if necessary, You should nominate at least one customer and one partner team member to be contacted by FastTrack.
- Each team member will be assigned a project security role and an implementation role. We highly recommend that you include representatives from the customer to the project team members with a monitored email address.
- The project security role is relevant to the LCS project workspace access. The implementation role is relevant to the individual team member’s role in the implementation team.

## Define milestone dates 

- Define all mandatory milestone steps. Use a tentative date if the milestone dates have not yet been decided. Keep the milestone dates updated as plans change. All milestone dates are used by Microsoft to provide you with relevant guidance for each milestone.
- Use the "pencil" icon to edit the milestone dates.
- Milestones are associated with the methodology of the project. 

## Associate LCS with Azure DevOps

- Connect LCS and Azure DevOps to maintain the application lifecycle.
- Enter the root URL of your Azure DevOps account and the personal access token you obtained from your Azure DevOps. The Azure DevOps account should belong to the customer.

## Configure Azure DevOps 

- Map work items between Lifecycle Services (LCS) and Business Process Modeler (BPM).
- Acknowledge the setup.
- If you choose to use a custom process template, follow the best practice in your custom template:

    - Don’t remove any existing work item types
    - Don’t remove any existing state of a work item type
    - Don’t add any required fields to a work item type

## FastTrack 

- The FastTrack program is introduced and information is provided about what the program consists of and how your implementation can benefit from it.
- We strongly recommend that you watch the existing *TechTalks* and subscribe to upcoming ones, as we continue to share best practice guidance and the changes that are happening in the product and platform. 

## Next Steps

This step provides additional resources about the most critical aspects of the implementation. You can access this page anytime during the implementation.

## Complete onboarding

- Complete the Project Onboarding to proceed with the next steps in your implementation. You will be able to complete onboarding only after all previous steps are completed.
- The **Complete onboarding** button will be visible only if all the steps are completed.
- Any skipped steps will be marked with an asterisk (\*). You will also be able to view any missing steps.
- After you complete Project onboarding, you can continue to update information, such as Project Scope values.
