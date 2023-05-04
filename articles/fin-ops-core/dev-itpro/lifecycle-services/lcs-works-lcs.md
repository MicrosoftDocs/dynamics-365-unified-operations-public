---
# required metadata

title: Lifecycle Services for finance and operations apps customers
description: This article describes Microsoft Dynamics 365 Lifecycle Services for finance and operations apps customers.
author: angelmarshall
ms.date: 02/08/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 84711
ms.assetid: 785baef9-aa46-44c3-95fa-e34749c2b44e
ms.search.region: Global
# ms.search.industry: 
ms.author: tsmarsha
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Lifecycle Services for finance and operations apps customers

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-1.md)]

This article is intended for customers who have signed up for the current versions of finance and operations apps. Partners who are working with customers to help them move through the lifecycle of their Microsoft Dynamics 365 Lifecycle Services project will also find this information useful. 

## Lifecycle Services workspace for the current versions of the finance and operations apps

When you sign up for the current versions of finance and operations apps, your subscription includes an Implementation project workspace. After you activate the service, the tenant administrator must sign in at <https://lcs.dynamics.com> by using the tenant account. The project workspace is automatically created for your organization. The workspace includes the following elements:

-   Enabled features, based on the offer that you selected
-   Environments that are deployed and managed by Microsoft
-   Guidance that is provided through the Action center to help you complete required actions
-   A new methodology experience that includes tasks that lock as you move through the implementation
-   A more complete history that specifies who completed each methodology phase and task
-   Milestones that you can use to track critical project dates
-   Various services to help you with your implementation

## Methodologies
As a customer, you must complete the steps that are outlined in the methodology to gain access to the production environment. Before a phase can be marked as completed, you must complete the specified mandatory tasks. Locked tasks, such as tasks 1.6 and 1.9 in the following screenshot, are unlocked after you've completed the required actions. To learn which actions must be completed before a specific task can be unlocked, click the lock icon for that task. [![Locked tasks and a tooltip that indicates which actions are required in order to unlock one of the tasks.](./media/1-1024x622.jpg)](./media/1.jpg) In the case of prerequisites, after you complete the required tasks, you can mark the dependent tasks as completed. For example, in the following screenshot, tasks 1.6 and 1.9 depend on task 1.5. Because task 1.5 has now been completed, the two dependent tasks can be marked as completed. [![Dependent tasks that can be marked as completed](./media/7.jpg)](./media/7.jpg)

## Milestones
High-level milestones must be defined for a project. Milestones can help you track the deliverables that must be completed and your progress toward the milestone goals. Color indicators help you quickly learn whether you're behind schedule. For example, in the following screenshot, the milestones are yellow. To enter or update the milestone dates, click the diamond shape in the methodology, and then click the **Edit** button (pencil icon). You can change milestone dates at any time. 

[![Edit button for a milestone.](./media/4-1024x619.jpg)](./media/4.jpg) 

When you've finished entering milestones, the **Publish plan and milestone** task opens, and you can mark it as completed. 

[![Set up milestones dialog box.](./media/5.jpg)](./media/5.jpg) 

When you've completed all the required tasks in a phase, you can click **Complete phase** to mark the phase as completed. After you mark a phase as completed, next steps become available in Lifecycle Services. 

[![8.](./media/8.jpg)](./media/7.jpg)

### Reopen a completed milestone
If you need to make any changes to your completed milestone tasks or dates, select the **Reopen phase** button on a prior milestone. You can then make edits and complete it again.

[![Screenshot of the Phase history and the Reopen phase button.](./media/lcs-reopenphase.png)](./media/lcs-reopenphase.png)

### Methodology description and history

Descriptions can help you understand what is expected of you for a specific methodology task or phase. You can expand the methodology description to learn more about each task, and then collapse the description when you've finished. The task and phase history can tell you when a task or phase was completed or reopened. If you're a project manager, this information can help you stay on top of the high-level tasks that are required for your implementations. [![Expanded task history and methodology description.](./media/2.jpg)](./media/2.jpg)

## Subscription estimator
You can use the Subscription estimator tool to evaluate your subscription requirements for the current versions of the finance and operations apps. To use Subscription estimator, download the usage profile, which is a Microsoft Excel workbook. Then, in the workbook, complete the following worksheets:

-   Deployment details
-   Instance Characteristics
-   Retail & Commerce

After you've completed the worksheets, enter the data from the summary sheet into Subscription estimator by clicking **+ New estimate**. You must make one estimate the active estimate. Make sure that the estimate that you mark as active is same as the offer that you bought through the VL or CSP channel.

## New deployment experience
To provision your environment, you must to complete a configuration checklist. As you make progress through the methodology, environments become available to you. Click **Configure** to add deployment information. 



Because the information that you enter determines your experience, carefully review your input. After you've entered all the required information, sign-off is required for the deployment request. The user who completes the sign-off becomes the system administrator on the instance. Verify that the correct user completes the sign-off for the deployment. After the sign-off is completed, the Microsoft site reliability engagement team reviews the request. After the team has reviewed the information that you entered, it initiates the provisioning. If the information isn't correct, the team will contact you. After the provisioning is completed, the status is updated to indicate that the environment has been deployed, as shown in the following screenshot. If the provisioning takes longer than expected, the Microsoft site reliability engagement team reviews the status and takes appropriate actions. These actions might include contacting you. After the environment is provisioned, click **Full details** to open the **Detailed environment** page, where you can sign in to the system, view the monitoring status, or view relevant updates. 

[![Status for an environment that has been successfully provisioned.](./media/12.jpg)](./media/12.jpg)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

