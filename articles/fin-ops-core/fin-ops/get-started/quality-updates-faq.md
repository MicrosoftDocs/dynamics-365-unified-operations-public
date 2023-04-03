---
title: Proactive Quality Updates Frequently Asked Questions
description: This article provides answers to frequently asked questions about Proactive Quality Updates (PQUs) 
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

# Proactive Quality Updates Frequently Asked Questions

This article provides answers to frequently asked questions about Proactive Quality Updates (PQUs)

### How are the maintenance windows handled for customers that have one finance and operations apps instance but are active in multiple time zones?

There are no special schedules outside of the current supported maintenance windows where a finance and operations apps instance exists because we plan to roll out PQUs in a minimally disruptive manner with near [Zero Downtime (nZDT](/dynamics365/fin-ops-core/dev-itpro/deployment/plannedmaintenance-selfservice.md#what-does-near-zero-downtime-maintenance-mean).

### Can customers delay, reschedule, or pause a PQU?

No. The main objective of PQUs is to ensure fundamentals, like security, privacy, reliability, availability, and performance, are continuously improving for our customers.

### How do I know which set of changes are included in the PQU?

To identify the changes included in a PQU, follow these steps.

**For example** : Use 10.0.28 PQU train and the related App version 10.0.1265.89.

1. In Lifecycle Services, open the  **Environment details**  page for your sandbox.
2. In the  **Available Updates**  section, select  **View Update**  for the latest Quality Update build.
3. Export the build into a CSV or Microsoft Excel file.
4. In the exported file, filter and select the  **Build version**  that is less than or equal to build number 10.0.1265.89. You should now be able to see the delta payload.

  **Note**

The export to a CSV or Excel file must happen before the environment is updated. Otherwise, you can use an environment with a similar configuration that doesn't have the update installed and follow the steps above.

### What is the process if a critical issue is found after a PQU?

A critical issue is one or more events that cause multiple customers to have degraded experience with one or more of our services. These issues can cause unplanned downtime including unavailability, performance degradation, and interference with service management. If there's a customer impact due to an issue(s) with a PQU, we'll stop rollout of that PQU until we can communicate and fix the issue. Typically, the next PQU will have the necessary fix to resume rollout.

If only one customer environment is affected, contact Microsoft support to open a support ticket. Based on the justification, we'll stop rollout of that PQU to other customer environments in that project until the issue is mitigated.

### Can customers still manually apply hotfix updates from Lifecycle Services?

Yes. To ensure ongoing parity with how hot fixes work, hot fix updates can still be applied to customer environments in Lifecycle Services. PQUs are cumulative builds and continue to be available on Lifecycle Services as they're published. PQUs will be published to Microsoft Dynamics Lifecycle Services (LCS) for manual application per the change cutoff schedule - it's important to note that hot fixes that are deployed as part of a PQU go through rigorous Safe Deployment Practice (SDP) before the update is deployed. Customers should choose a PQU over manually applying an update because of increased reliability, minimal disruption, and [reduced downtime](/dynamics365/fin-ops-core/dev-itpro/deployment/plannedmaintenance-selfservice.md#what-does-near-zero-downtime-maintenance-mean).

### Can customers proactively install a PQU ahead of the schedule?

Yes. You can install a PQU proactively. Microsoft will skip the update if the environment's current build version is equal or higher than the PQU that is being deployed.

### Under which circumstances will a PQU be skipped?

- If a Service Update is scheduled within seven days of a PQU, then the scheduled PQU is skipped. For example, if a PQU is scheduled on January 28, 2023, for a prod env, and a Service Update is scheduled on February 4, 2023, for the same env, the PQU on January 28, 2023, is skipped.
- If a sandbox environment has the same or higher build version than the impending PQU, the PQU is skipped.
- If a production environment has the same or higher build version than the impending PQU, it's skipped.
- If a sandbox environment has the same or higher build version because of a PQU or a manual update to the production environment, the production environment still gets the scheduled version of the PQU. If you don't want the scheduled production environment receive the Service Update version, you can pause the Service Update from Lifecycle Services. 
- If any Lifecycle Services environment(s) or project is under exemption, PQUs are skipped.
- PQUs on a production environment are skipped if the update has failed or was skipped on other sandboxes in the Lifecycle Services project.

### If an environment has an upcoming scheduled action, and a scheduled PQU is within the same maintenance window, will it still receive the PQU?

If there's a conflict with a pre-scheduled action, for example a Point In Time Restore (PITR), the PQU is rescheduled to the next available maintenance window (within four-days).

### Can an environment be brought back to its previous state if there are issues after a PQU is applied?

As with any other code promotions, rollbacks can't be performed after a PQU is applied. For more information on how flighting can help mitigate an issue, see the [What are some of the investments Microsoft is making to enable safe deployments of PQUs](quality-updates.md#what-are-some-of-the-investments-microsoft-is-making-to-enable-safe-deployments-of-pqus).

### What is the guidance for customers with U.S. Food and Drug Administration (FDA) and Good Practice Quality (GxP) regulatory requirements?

The plan for customers subject to FDA validation and regulation is still evolving. Expect more updates in this space soon. Until then, customers subject to FDA/GxP regulations will be exempted from the PQU process until further updates in this space. Customers who fall under this regulation and don't have an exemption are required to raise a support ticket with justification related to the regulatory requirement for FDA/ GxP to receive an exemption for their LCS project(s). If Microsoft has already confirmed an exemption for such customers, no further action is required at this time. For more information on FDA or GxP regulations, please visit [Microsoft Azure GxP Offering](/azure/compliance/offerings/offering-gxp.md).

### What is the guidance for customers with Sarbanes-Oxley (SOX) requirements?

Microsoft commissions a full System and Organization Controls (SOC) 1 Type II and SOC 2 Type II examination of Microsoft Dynamics 365 online services two times each year. Microsoft Dynamics 365 Finance, Dynamics 365 Project Operations, Dynamics 365 Human Resources, and other Dynamics 365 online services are detailed in the [Microsoft Azure (including Dynamics 365) SOC 1 Type II report](https://servicetrust.microsoft.com/viewpage/SOC).  This and other reports are available on Microsoft's [Service Trust Portal](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fservicetrust.microsoft.com%2F&data=05%7C01%7Caleahy%40microsoft.com%7C44feaa9ec199455e1b0608db0e0ecd83%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C638119228989631258%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000%7C%7C%7C&sdata=OjXKP%2FxofSNwS1fzIZirt3M96YjFbVdv2vWog%2FjTDmI%3D&reserved=0). Customers can use the [Microsoft Azure (including Dynamics 365) SOC 1 Type II report](https://servicetrust.microsoft.com/viewpage/SOC) when pursuing their own financial compliance requirements such as Sarbanes-Oxley (SOX).

### Which versions of service updates are supported for PQUs?

All environments on a supported version will be included in the PQU process.

### Finance and operations apps deployments with Retail components typically require more work and need to redeploy Microsoft Point of Sale (MPOS). How will these PQUs impact the Retail SDK?

Because the nature of the hot fix itself doesn't change in the PQU payload, we don't anticipate any additional impact to Retail components currently.

### Are PQUs applied to customer managed environments also known as Cloud hosted environments (CHE)?

Customer managed environments are out of scope for PQUs because they are outside the purview of Microsoft.

### Are there any integration issues with Microsoft Dataverse?

There are no known integration issues for PQUs with Dataverse.

If you have a question that you require more clarification or is not covered in this document, please file a support case.
