---
title: Proactive quality updates FAQ
description: This article provides answers to frequently asked questions about proactive quality updates (PQUs).
author: rashmansur
ms.author: rashmim
ms.topic: article
ms.date: 04/05/2023
ms.custom: bap-template
audience: Application User, Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2022-08-19
ms.search.form:
ms.dyn365.ops.version: 10.0.29
---

# Proactive quality updates FAQ

This article provides answers to frequently asked questions about proactive quality updates (PQUs).

### How are the maintenance windows handled for customers who have one finance and operations apps instance but are active in multiple time zones?

Aside from the currently supported maintenance windows, there are no special schedules for cases where an instance of finance and operations apps exists, because we plan to roll out PQUs in a minimally disruptive manner that involves [near-zero downtime](../../dev-itpro/deployment/plannedmaintenance-selfservice.md#what-does-near-zero-downtime-maintenance-mean).

### Can customers delay, reschedule, or pause a PQU?

No. The main purpose of PQUs is to ensure that fundamentals such as security, privacy, reliability, availability, and performance continuously improve for our customers.

### How do I know what set of changes is included in a PQU?

To identify the changes that are included in a PQU, follow these steps. This example uses the 10.0.28 PQU train and related app version 10.0.1265.89.

1. In Microsoft Dynamics Lifecycle Services, open the **Environment details** page for your sandbox environment.
2. In the **Available Updates** section, select **View Update** for the latest quality update build.
3. Export the build to a comma-separated values (CSV) or Excel file.
4. In the exported file, filter for and select the build version that's less than or equal to build number 10.0.1265.89. You should now be able to review the delta payload.

> [!NOTE]
> The export to a CSV or Excel file must occur before the environment is updated. Otherwise, you can follow the preceding steps for an environment that has a similar configuration but doesn't have the update installed.

:::image type="content" source="./media/how-to-get-kb-list-pqu.png" alt-text="Example of environment with quality update."::: 

### What's the process if a critical issue is found after a PQU?

A critical issue is one or more events that cause multiple customers to have a degraded experience with one or more of our services. These issues can cause unplanned downtime, including unavailability, performance degradation, and interference with service management. If an issue with a PQU causes customer impact, we'll stop the rollout of that PQU until we can communicate and fix the issue. Typically, the next PQU will have the fix that's required to resume the rollout.

If only one customer environment is affected, contact Microsoft support to open a support ticket. Based on the justification, we'll stop the rollout of the PQU to other customer environments in that project until the issue is mitigated.

### Can customers still manually apply hotfix updates from Lifecycle Services?

Yes. To ensure ongoing parity in the way that hotfixes work, hotfix updates can still be applied to customer environments in Lifecycle Services. PQUs are cumulative builds and continue to be available on Lifecycle Services as they're published. PQUs will be published to Lifecycle Services for manual application according to the change cutoff schedule.

It's important to note that hotfixes that are deployed as part of a PQU go through a rigorous safe deployment practice before the update is deployed. Because PQUs are more reliable, and involve minimal disruption and [reduced downtime](../../dev-itpro/deployment/plannedmaintenance-selfservice.md#what-does-near-zero-downtime-maintenance-mean), customers should use a PQU instead of manually applying an update.

### Can customers proactively install a PQU ahead of the schedule?

Yes. You can proactively install a PQU. Microsoft will skip the update if the environment's current build version is equal to or more than the PQU that's being deployed. If you apply the PQU manually the [customers AOT package will also be promoted.](../../dev-itpro/deployment/updateenvironment-newinfrastructure.md#things-to-consider-about-production-updates). 

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

As for other code promotions, rollbacks can't be done after a PQU is applied. For information about how flighting can help mitigate an issue, see [What investments is Microsoft making to enable safe deployments of PQUs?](quality-updates.md#what-investments-is-microsoft-making-to-enable-safe-deployments-of-pqus)

### What's the guidance for customers who are subject to U.S. Food and Drug Administration (FDA) regulatory requirements and "good practice" (GxP) quality regulatory requirements?

The plan for customers who are subject to U.S. Food and Drug Administration (FDA) validation and regulations is still evolving. Expect more updates in this space soon. Until those updates are made, customers who are subject to FDA regulations and "good practice" (GxP) quality regulations will be exempted from the PQU process. Customers who are subject to these regulations and don't have an exemption must open a support ticket and provide justification that's related to the regulatory requirement for FDA/GxP to receive an exemption for their Lifecycle Services projects. If Microsoft has already confirmed an exemption for these customers, no further action is required at this time. For more information about FDA and GxP regulations, see [Microsoft Azure GxP Offering](/azure/compliance/offerings/offering-gxp).

### What's the guidance for customers who are subject to Sarbanes-Oxley (SOX) requirements?

Microsoft commissions a full System and Organization Controls (SOC) 1 Type II and SOC 2 Type II examination of Dynamics 365 online services two times each year. Dynamics 365 Finance, Dynamics 365 Project Operations, Dynamics 365 Human Resources, and other Dynamics 365 online services are detailed in the [Microsoft Azure (including Dynamics 365) SOC 1 Type II report](https://servicetrust.microsoft.com/viewpage/SOC). This report and others are available in the [Microsoft Service Trust Portal](https://servicetrust.microsoft.com/). Customers can use the [Microsoft Azure (including Dynamics 365) SOC 1 Type II report](https://servicetrust.microsoft.com/viewpage/SOC) when they're pursuing their own financial compliance requirements, such as Sarbanes-Oxley (SOX).

### Which versions of service updates are supported for PQUs?

All environments on a supported version will be included in the PQU process.

### Typically, finance and operations apps deployments that include Retail components require more work, and Retail Modern Point of Sale (MPOS) must be redeployed. How will these PQUs affect the Retail SDK?

Because the nature of the hotfix itself doesn't change in the PQU payload, we don't currently anticipate any additional impact on Retail components.

### Are PQUs applied to customer-managed environments (also known as cloud-hosted environments)?

Customer-managed environments are out of scope for PQUs, because they're outside the purview of Microsoft.

### Are there any integration issues with Dataverse?

There are no known integration issues for the use of PQUs with Dataverse.

### What's the purpose of Station 1 or the First Release Program for PQUs?

The First Release Program (FRP) for PQUs (also known as Station 1) gives all finance and operations apps customers an opportunity to receive PQUs ahead of the other stations. This program is optional and is open to all customers. Customers can take advantage of it by signing up a sandbox environment of their choice to receive PQUs. They can then provide early feedback so that Microsoft can address it before the PQUs are rolled out to the other stations. Customers who participate in the FRP for PQUs are the first, select group of customers to receive a PQU in a sandbox environment of their choice. They have the benefit of a shorter feedback cycle and fast response before the rollout to other stations.

### What's the process for joining the First Release Program for PQUs? 

The program is open to all finance and operations apps customers at all times. Only sandbox environments qualify for selection. Anyone who has a **Project owner** security role for the Lifecycle Services project can select a sandbox environment in the project.

To select a sandbox environment for the FRP for PQUs, follow these steps.

1. In Lifecycle Services, select the project.
2. Select **Project Settings** for the project.
3. On the **Proactive quality update settings** tab, in the drop-down list, select a sandbox environment. Then select **Save**. 

:::image type="content" source="media/pqu-setting-screen.png" alt-text="A screenshot of the Proactive quality update settings tab of the Project Settings page."::: 

### Can customers revert or change the selection for Station 1?

After a selection is made, customers can modify it at any time. However, if a PQU is already scheduled, the new selection won't be honored for the upcoming PQU. The selection will be honored for subsequent PQUs.

### What's expected from customers who participate in the First Release Program for PQUs?

1. Participants are expected to provide feedback about the PQU and will receive direct support from Microsoft Dynamics product teams for any issues that are encountered from PQUs.
1. If a critical issue is found, participants might have to take an additional PQU on short notice.
1. Participants shouldn't delay or pause a PQU on the sandbox environment that they've selected to receive a PQU in Station 1 or the FRP.
1. If there is a critical issue, participants should open a support ticket with Microsoft Support to get faster response and action.

### How soon will a sandbox environment receive a PQU after it's selected for Station 1?

To learn when the group of sandbox environments in the FRP will receive a PQU, see the [release schedule](quality-updates-schedule.md) for Station 1.<!--TO HERE-->

## More information

If you have a question that isn't covered in this article, or if you require clarification about any answer in this article, open a support case.

## Additional resources

- [Proactive quality updates overview](quality-updates.md)
- [Release schedule for proactive quality updates](quality-updates-schedule.md)
