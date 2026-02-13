---
title: Proactive quality updates FAQ
description: Access answers to frequently asked questions about proactive quality updates (PQUs), including questions about how to know what's included in a PQU.
author: najaidee
ms.author: najaidee
ms.topic: faq
ms.date: 02/11/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2022-08-19
ms.search.form:
ms.dyn365.ops.version: 10.0.29
---

# Proactive quality updates (PQU) - FAQ

This article provides answers to frequently asked questions about the proactive quality updates (PQUs), new biweekly proactive quality updates (PQUs), and the optional weekday update schedule.

### What is the biweekly cadence for PQU?

The biweekly cadence introduces a more frequent release cycle for proactive quality updates. Instead of receiving updates every 26 days, PQUs are now released every two weeks.

Each biweekly cycle includes:

- A release cut of the latest platform and application updates
- Deployment to all stations - Trail, OnlineDev, Sandbox, and Live environments

You can view the upcoming rollout calendar here: [PQU Release Calendar](/dynamics365/fin-ops-core/dev-itpro/get-started/quality-updates-schedule#high-level-pqu-train-schedule).

### Why is the rollout schedule changing from 26 days to a biweekly cadence?

This change ensures that customers receive fixes and improvements faster. A biweekly cadence helps:

- Reduce waiting time for important fixes.
- Provide more frequent validation cycles in Sandbox.
- Improve service stability through faster delivery.
- Keep customer environments closer to the most reliable build.

### What does "weekday schedule" mean for PQU?

Previously, Live environments received PQUs only during weekend maintenance windows. By using the new enhancement, customers can now opt to receive updates on weekdays as well.

Benefits of combining the biweekly cadence with weekday scheduling include:

- Greater flexibility in selecting maintenance windows.
- More buffer time to validate PQU updates in Sandbox.
- Better alignment with internal release and testing cycles.
- Improved control over update timing.

### How do I configure my Live environment to receive PQU updates on weekdays?

Follow these steps in the Power Platform Admin Center (PPAC):

1. Sign in to PPAC.
1. Select your Live environment.
1. Select **Settings**.
1. In the **Updates** section, select **Maintenance Settings**.

    :::image type="content" source="https://github.com/user-attachments/assets/372620cb-4c27-40ff-84a3-e79331f5a904" alt-text="Screenshot of the Maintenance Settings option in the updates section.":::

1. Choose your preferred days to receive PQUs.

    :::image type="content" source="https://github.com/user-attachments/assets/bc7ac1c8-8e76-4c45-a4ec-51964344f494" alt-text="Screenshot of the preferred day selection for receiving PQUs.":::

1. Select Maintenance Cadence as "Every Update". 
2. Select **Save**.

> [!NOTE]
> Live environments always receive updates at least five days after Sandbox. This process remains unchanged under the biweekly cadence.

### Which day should I choose for receiving PQU updates?

Choose any day that aligns with your organization’s internal operations and testing cycles.

> [!TIP]
> Selecting multiple weekdays ensures greater flexibility and reduces the risk of delays if one maintenance window is missed.

### What is the minimum timeline between Sandbox and PROD under the biweekly cadence?

The process always maintains a minimum five-day gap between when the PQU is applied to Sandbox (UAT) and when it becomes eligible for Live (PROD).

This version difference is expected and doesn't affect your ability to deploy custom packages, as long as you follow compatibility best practices.

### Can customers request exclusions from the new biweekly cadence?

No. Exclusions aren't supported.
The standardized biweekly cadence ensures consistent servicing, predictable timelines, and compliance with platform servicing requirements.

### How does the biweekly cadence work? Can you provide an example?

Yes. Consider this example:
If PQU-1 rolls out to Station-2 on April 13–14, 2026:
For customers using the default weekend-only schedule:

- PQU applied on April 13 → Live receives the update on April 18, 2026 (Sandbox + 5 days)
- PQU applied on April 14 → Live receives the update on April 19, 2026 (Sandbox + 5 days)

For customers who enabled weekday updates:
Live receives the update on the next available selected weekday, starting after the required 5-day minimum window.
Example:
For a PQU applied on April 13, the earliest eligible date is April 18, 2026, and the system selects the next chosen weekday from your maintenance settings.

### How are the maintenance windows handled for customers who have one finance and operations apps instance but are active in multiple time zones?

Aside from the currently supported maintenance windows, there are no special schedules for cases where an instance of finance and operations apps exists, because the rollout of PQUs involves a minimally disruptive manner that involves [near-zero downtime](../deployment/plannedmaintenance-selfservice.md#what-does-near-zero-downtime-maintenance-mean).

### Can customers delay, reschedule, or pause a PQU?

No. The main purpose of PQUs is to ensure that fundamentals such as security, privacy, reliability, availability, and performance continuously improve for customers.

### How do I know what set of changes is included in a PQU?

To identify the changes that a PQU includes, follow these steps. This example uses the 10.0.28 PQU train and related app version 10.0.1265.89.

1. In Microsoft Dynamics Lifecycle Services, open the **Environment details** page for your sandbox environment.
1. In the **Available Updates** section, select **View Update** for the latest quality update build.
1. Export the build to a comma-separated values (CSV) or Excel file.
1. In the exported file, filter for and select the build version that's less than or equal to build number 10.0.1265.89. You can now review the delta payload.

> [!NOTE]
> You must export to a CSV or Excel file before you update the environment. Otherwise, you can follow the preceding steps for an environment that has a similar configuration but doesn't have the update installed.

:::image type="content" source="../../fin-ops/get-started/media/how-to-get-kb-list-pqu.png" alt-text="Example of environment with quality update.":::

### What's the process if a critical issue is found after a PQU?

A critical issue is one or more events that cause multiple customers to have a degraded experience with one or more of Microsoft's services. These problems can cause unplanned downtime, including unavailability, performance degradation, and interference with service management. If an issue with a PQU causes customer impact, Microsoft stops the rollout of that PQU until it can communicate and fix the problem. Typically, the next PQU includes the fix that's required to resume the rollout.

If the problem affects only one customer environment, contact Microsoft support to open a support ticket. Based on the justification, Microsoft stops the rollout of the PQU to other customer environments in that project until the issue is mitigated.

### How do I see notifications about a PQU?

You can see notifications for PQUs in the message center in Microsoft 365 admin center. For more information, see [Track new and changed features in the Microsoft 365 Message center](/admin/manage/message-center).

### Can customers still manually apply hotfix updates from Lifecycle Services?

Yes. To ensure ongoing parity in the way that hotfixes work, customers can still apply hotfix updates to their environments in Lifecycle Services. PQUs are cumulative builds and continue to be available on Lifecycle Services as they're published. PQUs are published to Lifecycle Services for manual application according to the change cutoff schedule.

Hotfixes that are deployed as part of a PQU go through a rigorous safe deployment practice before the update is deployed. Because PQUs are more reliable, and involve minimal disruption and [reduced downtime](../deployment/plannedmaintenance-selfservice.md#what-does-near-zero-downtime-maintenance-mean), use a PQU instead of manually applying an update.

### Can customers proactively install a PQU ahead of the schedule?

Yes. You can proactively install a PQU. Microsoft skips the update if the environment's current build version is equal to or more than the PQU that's being deployed. If you apply the PQU manually the [customers AOT package will also be promoted.](../deployment/updateenvironment-newinfrastructure.md#things-to-consider-about-production-updates)

### Under what circumstances will a PQU be skipped?

- If a service update is scheduled within seven days of a scheduled PQU, the PQU is skipped. For example, a PQU is scheduled on January 28 for a production environment, and a service update is scheduled on February 4 for the same environment. In this case, the PQU on January 28 is skipped.
- If a sandbox environment has the same build version as the scheduled PQU, or if it has a later build version, the PQU is skipped.
- If a production environment has the same build version as the scheduled PQU, or if it has a later build version, the PQU is skipped.
- If a sandbox environment has the same build version or a later build version because of a PQU or a manual update to the production environment, the production environment still receives the scheduled version of the PQU.
- If any Lifecycle Services environment or project is under exemption, PQUs are skipped.
- PQUs for a production environment are skipped if the update failed or was skipped in other sandbox environments in the Lifecycle Services project.

### If an environment has an upcoming scheduled action, and a PQU is scheduled within the same maintenance window, will the environment still receive the PQU?

If there's a conflict with a prescheduled action, such as a point-in-time restore (PITR), the PQU is rescheduled for the next available maintenance window (within four days).

### Can an environment be brought back to its previous state if there are issues after a PQU is applied?

As with other code promotions, you can't roll back after a PQU is applied. For information about how flighting can help mitigate an issue, see [What investments is Microsoft making to enable safe deployments of PQUs?](quality-updates.md#what-investments-is-microsoft-making-to-enable-safe-deployments-of-pqus)

### What's the guidance for customers who are subject to U.S. Food and Drug Administration (FDA) regulatory requirements and "good practice" (GxP) quality regulatory requirements?

The plan for customers who are subject to U.S. Food and Drug Administration (FDA) validation and regulations is still evolving. Expect more updates in this space soon. Until those updates are made, customers who are subject to FDA regulations and "good practice" (GxP) quality regulations are exempt from the PQU process. Customers who are subject to these regulations and don't have an exemption must open a support ticket and provide justification that's related to the regulatory requirement for FDA/GxP to receive an exemption for their Lifecycle Services projects. If Microsoft already confirmed an exemption for these customers, no further action is required at this time. For more information about FDA and GxP regulations, see [Microsoft Azure GxP Offering](/azure/compliance/offerings/offering-gxp).

### What's the guidance for customers who are subject to Sarbanes-Oxley (SOX) requirements?

Microsoft commissions a full System and Organization Controls (SOC) 1 Type II and SOC 2 Type II examination of Dynamics 365 online services two times each year. Dynamics 365 Finance, Dynamics 365 Project Operations, Dynamics 365 Human Resources, and other Dynamics 365 online services are detailed in the [Microsoft Azure (including Dynamics 365) SOC 1 Type II report](https://servicetrust.microsoft.com/viewpage/SOC). This report and others are available in the [Microsoft Service Trust Portal](https://servicetrust.microsoft.com/). Customers can use the [Microsoft Azure (including Dynamics 365) SOC 1 Type II report](https://servicetrust.microsoft.com/viewpage/SOC) when they're pursuing their own financial compliance requirements, such as Sarbanes-Oxley (SOX).

### Which versions of service updates are supported for PQUs?

All environments on a supported version are included in the PQU process.

### Typically, finance and operations apps deployments that include Retail components require more work, and Retail Modern Point of Sale (MPOS) must be redeployed. How do these PQUs affect the Retail SDK?

Because the nature of the hotfix itself doesn't change in the PQU payload, we don't currently anticipate any additional impact on Retail components.

### Are PQUs applied to customer-managed environments (also known as cloud-hosted environments)?

Customer-managed environments are out of scope for PQUs, because they're outside the purview of Microsoft.

### Are there any integration issues with Dataverse?

There are no known integration issues for the use of PQUs with Dataverse.

### What's the purpose of Station 1 or the First Release Program for PQUs?

The First Release Program (FRP) for PQUs (also known as Station 1) gives all finance and operations apps customers an opportunity to receive PQUs ahead of the other stations. This program is optional and is open to all customers. Customers can take advantage of it by signing up a sandbox environment of their choice to receive PQUs. They can then provide early feedback so that Microsoft can address it before the PQUs are rolled out to the other stations. Customers who participate in the FRP for PQUs are the first select group of customers to receive a PQU in a sandbox environment of their choice. They have the benefit of a shorter feedback cycle and fast response before the rollout to other stations.

### How do I join the First Release Program for PQUs?

The program is always open to all finance and operations apps customers. Only sandbox environments qualify for selection. Anyone who has a **Project owner** security role for the Lifecycle Services project can select a sandbox environment in the project.

To select a sandbox environment for the FRP for PQUs, follow these steps:

1. In Lifecycle Services, select the project.
1. Select **Project Settings** for the project.
1. On the **Proactive quality update settings** tab, in the drop-down list, select a sandbox environment. Then select **Save**.

:::image type="content" source="../../fin-ops/get-started/media/pqu-setting-screen.png" alt-text="A screenshot of the Proactive quality update settings tab of the Project Settings page.":::

### Can customers revert or change the selection for Station 1?

After a selection, you can modify it at any time. However, if a PQU is already scheduled, the new selection isn't honored for the upcoming PQU. The selection is honored for subsequent PQUs.

### What does Microsoft expect from customers who participate in the First Release Program for PQUs?

1. Participants provide feedback about the PQU and receive direct support from Microsoft Dynamics product teams for any problems that the PQUs encounter.
1. If a critical problem is found, participants might have to take an additional PQU on short notice.
1. Participants shouldn't delay or pause a PQU on the sandbox environment that they selected to receive a PQU in Station 1 or the FRP.
1. If there's a critical problem, participants should open a support ticket with Microsoft Support to get faster response and action.

### How soon does a sandbox environment receive a PQU after it's selected for Station 1?

To learn when the group of sandbox environments in the FRP receive a PQU, see the [release schedule](quality-updates-schedule.md) for Station 1.<!--TO HERE-->

## More information

If you have a question that isn't covered in this article, or if you need clarification about any answer in this article, open a support case.

## Additional resources

- [Proactive quality updates overview](quality-updates.md)
- [Release schedule for proactive quality updates](quality-updates-schedule.md)
