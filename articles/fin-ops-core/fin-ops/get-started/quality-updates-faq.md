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
- If a sandbox environment has the same build version or a later build version because of a PQU or a manual update to the production environment, the production environment still receives the scheduled version of the PQU. If you don't want the production environment to receive the scheduled service update version, you can pause the service update from Lifecycle Services.
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

## More information

If you have a question that isn't covered in this article, or if you require clarification about any answer in this article, open a support case.

## Additional resources

- [Proactive quality updates overview](quality-updates.md)
- [Release schedule for proactive quality updates](quality-updates-schedule.md)
