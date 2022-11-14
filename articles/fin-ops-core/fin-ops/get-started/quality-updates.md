---
# required metadata

title: Proactive quality updates
description: This article provides information about proactive delivery of quality updates.
author: rashmansur
ms.date: 11/07/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: rashmim
ms.search.validFrom: 2022-08-19
ms.search.form:
ms.dyn365.ops.version: 10.0.29
---

# Proactive quality updates

[!include[banner](../includes/banner.md)]

Over the last several years, Microsoft has made continuous progress on what we refer to as [One Version](../../dev-itpro/lifecycle-services/oneversion-overview.md). The premise of One Version is simple: the closer that we can get to having all customers on the same software version, the higher the quality that we can deliver. We find and fix issues once, and we get those solutions into the hands of more customers more quickly.

This premise is confirmed by the results: lower incident counts across our products. When customers aren't on the same version, we consistently see that they are affected by issues that a solution is already available for. We've already made great progress with Dynamics 365 Finance, Dynamics 365 Supply Chain, Dynamics 365 Project Operations, and Dynamics 365 Commerce, and thanks to recent technical advances, it's now possible to take the next step. The following information lays out what we're going to do, what we've already done to set the stage, and how and when we will introduce the new capabilities without disruption.

## What you need to know

- Proactive quality updates are applied on a monthly basis.
- Microsoft will apply proactive quality updates to any sandbox environments that are running a service update that was [in service](./public-preview-releases.md#targeted-release-schedule-dates-subject-to-change) when the proactive quality updates were created.
- Exceptions for proactive quality updates will be allowed for customers that are regulated by the US Food and Drug Administration (FDA).
- Microsoft is determining how proactive quality updates will be managed for regulated environments, and for sovereign and government cloud customers.
- Notifications that are related to proactive quality updates are posted in the [Microsoft 365 Message Center](https://admin.microsoft.com/AdminPortal/) and on a banner in the customer's Microsoft Dynamics Lifecycle Services project.
- Five days before a proactive quality update is applied to an environment, customers are notified that the update will occur.
- Customers can't cancel or postpone proactive quality updates.
- Proactive quality updates are installed during the region-specific [planned maintenance window](../../dev-itpro/deployment/plannedmaintenance-selfservice.md#windows).
- Quality updates are engineered to have a low risk of issues or regressions, and this is supported by Microsoft data.
- Microsoft recommends targeted testing for specific issues or specific hotfixes that are related to a proactive quality update.

## Focus on quality updates

We currently provide seven [service updates](public-preview-releases.md) per year. For example, version 10.0.29 is a service update. Until recently, there were eight updates per year. However, we dropped one update in response to customer feedback that revealed a desire to avoid changes near the end of the calendar year.

We won't be changing the cadence of the service updates. Instead, our next step forward in the One Version journey is focused on *quality updates*. Quality updates are cumulative builds of hotfixes. They don't include new features. At any given time, our entire community of customers is spread between the three or four most recent service updates. However, for any given service update, dozens of different quality update versions can be used within the group, depending on the dates when people deployed. In our next step, we will proactively broadcast quality updates. We already use this model for our Dataverse-based applications and have seen the expected results of improved quality and decreased support incidents.

Of course, a reduction in defects could reduce or completely eliminate the need for quality updates. We have multiple initiatives in flight to reduce the defects that require quality updates. Even when payloads are reduced in the quality update, consistency across the customer base will improve supportability, get improvements to customers more quickly, and reduce the frequency of customers encountering issues that solutions already exist for.

## Making proactive distribution possible

Multiple advances have already been deployed that enable proactive delivery of quality updates:

- **Near-zero downtime updating** – To push more frequent environments, it's essential that the impact to environment availability be reduced to preserve Dynamics 365 Service Level Agreements (SLAs). Near-zero downtime updating was originally introduced to help improve monthly operating system patching by using a cluster failover to activate the updated image with minimal disruption. The mechanism for applying updates is being enhanced so that it's even less disruptive, and it will cover both operating system patching and quality update deployment.

    For interactive users, an active session might be interrupted, and the retry will go to the now-updated environment. With the introduction of [priority-based batch scheduling](../../dev-itpro/sysadmin/priority-based-batch-scheduling.md), batch scheduling and processing recovers and resumes immediately after the update. Priority-based batch scheduling will be in place for customers before they start to participate in proactive distribution of quality updates for their production environments.

- **Dark hours** – Dark hours are defined for each Azure region, and near-zero downtime updates will occur during the dark hour period.

## The proactive update process

Deployment of proactive quality updates will follow a safe deployment process (SDP). The specifics of the SDP will evolve, but quality updates will initially be deployed to sandbox environments. As the percentage of successfully deployed sandboxes increases, deployment to production environments will begin. Listening systems will monitor system telemetry and Livesite incidents, and will stop the rollout of a specific version if any regression is detected. Customers will still be able to pull the quality updates ahead of proactive deployment if they want.

Current release management data shows that less than 3 percent of regressions are introduced in quality updates. With increased focus on eliminating regression and an enhanced SDP, the potential impact of regressions will be dramatically lower than the quality gains that are achieved by more quickly getting fixes deployed to customers broadly.

## Process changes

A set of process changes is being implemented ahead of the activation of proactive quality update deployment:

- **Schema** – Tooling will ensure that quality update builds include only schema changes that can be applied while the service is online. This approach will help preserve the ability to apply the update with near-zero downtime.
- **Increased change scrutiny** – Currently, there is already an extra process step to approve changes for inclusion in a quality update. The scrutiny in the extra step will be increased to help reduce the potential for regressions. Breaking changes aren't allowed in quality updates, and the increased change scrutiny will help ensure that we meet this target.
- **Visibility** – Notifications are sent through the admin center, Lifecycle Services, and other available channels for upcoming proactive quality updates. In addition, support teams and incident leads will have visibility into where quality updates have been proactively deployed.

    > [!NOTE]
    > The Microsoft Communications team is investigating an ongoing degradation of the email tooling which is preventing the delivery of email notifications. Please continue to monitor the Microsoft 365 Message Center for onboarding and notification related messages.

- **Fail Safe via flighting** – Flighting will be used to guard code changes wherever applicable in a quality update bug fix or use the existing feature flighting relevant to the fix. If a fallback or turning a change off change is required after a proactive deployment, it can be done through the flighting system to avoid further failures.
- **Sandbox sync designation** – Less than 20 percent of customers today have multiple sandboxes and keep one sandbox deployed where the version matches production, to help with troubleshooting. If a customer is using a sandbox to test a newer version than their production, that sandbox will receive quality updates to the newer version.

## What is the rollout roadmap for quality updates?

Distribution of proactive quality updates for sandbox environments is expected to begin in late September or October 2022 for Azure public cloud customers. Trial environments will also start to receive proactive update deployment at that time. In September, a notification will be sent to each customer to inform them about the expected schedule for their environments. Exceptions to the proactive updated distribution process will be allowed only for FDA-regulated customers. We're still working out how regulated environments and sovereign and government cloud customers will be managed.

Over the next six-month period, we will gradually increase the percentage of sandbox environments that receive proactive updates, until all designated environments are included and progress to updating production environments. Throughout the period, we will monitor to ensure that the deployment process is seamless and that we're hitting our target of non-disruptive payloads.

Because customers will regularly receive smaller payloads, we expect the process of staying current to become simpler. We will adjust the frequency of update deployment as we demonstrate the ability to run the process without disruption. This process is already working effectively for our Dataverse platform and applications, and is delivering the anticipated improvements in service quality. We're anxious to take the same step forward for finance and operations applications.

## When will quality updates start for production environments?
At this time, quality updates are only targeting sandboxes. We will update this space with a start date for production environments when we have more concrete data and metrics from proactive updates for sandboxes to gauge readiness for prod.

## What is the schedule for sandbox proactive quality updates?
For information on the dark hours for each region, see [What are the planned maintenance windows by region?](../../dev-itpro/deployment/plannedmaintenance-selfservice.md#windows).

### Proactive quality update release: 10.0.28
**App version: 10.0.1265.89**  
**Corresponding latest KB article: 745340**

| Station | Regions | Completed Schedule| Upcoming Sandbox Schedule
|---|---|---|---|
| Station 1 | Canada Central, Canada East, France Central, India Central, Norway East, Switzerland West | September 15 to September 18, 2022, September 19 to September 22, 2022, and October 7 to October 10, 2022 | October 25 to October 28, 2022 |
| Station 2 | France South, India South, Norway West, Switzerland North, South Africa North, Australia East, UK South, UAE North, Japan East, Australia South East, South East Asia | September 25 to September 28, 2022, and October 7 to October 10, 2022 | October 25 to October 28, 2022 |
| Station 3 | East Asia, UK West, Japan West, Brazil South, West Europe, East US, UAE Central | September 26 to September 29, 2022, and October 7 to October 10, 2022 | October 25 to October 28, 2022 |
| Station 4 | North Europe, Central US, West US | September 28 to October 1, 2022, and October 7 to October 10, 2022 | October 25 to October 28, 2022 |
| Station 5 | DoD, Government Community Cloud, China | Not Scheduled | Not Scheduled |

### <a name="schedule"></a> Proactive quality update release: 10.0.29
**App version: 10.0.1326.70**  
**Corresponding latest KB article: 748926**

| Station | Regions | Completed Schedule | Upcoming Sandbox Schedule|
|---|---|---|---|
| Station 1 | Canada Central, Canada East, France Central, India Central, Norway East, Switzerland West | October 14 to October 17, 2022, November 2 to November 5, 2022 | November 13 to November 16, 2022 |
| Station 2 | France South, India South, Norway West, Switzerland North, South Africa North, Australia East, UK South, UAE North, Japan East, Australia South East, South East Asia | October 15 to October 18, 2022, November 2 to November 5, 2022 | November 13 to November 16, 2022 |
| Station 3 | East Asia, UK West, Japan West, Brazil South, West Europe, East US, UAE Central | October 16 to October 19, 2022, November 2 to November 5, 2022 | November 13 to November 16, 2022 |
| Station 4 | North Europe, Central US, West US | October 17 to October 20, 2022, November 2 to November 5, 2022 | November 15 to November 18, 2022 |
| Station 5 | DoD, Government Community Cloud, China | Not Scheduled | Not Scheduled |

### <a name="schedule"></a> Proactive quality update release: 10.0.30
**App version: TBD**
**Corresponding latest KB article: TBD**

| Station | Regions | Upcoming Sandbox Schedule |
|---|---|---|
| Station 1 | Canada Central, Canada East, France Central, India Central, Norway East, Switzerland West | December 1 to December 4, 2022 |
| Station 2 | France South, India South, Norway West, Switzerland North, South Africa North, Australia East, UK South, UAE North, Japan East, Australia South East, South East Asia | December 2 to December 5, 2022 |
| Station 3 | East Asia, UK West, Japan West, Brazil South, North Europe, East US, UAE Central | December 3 to December 6, 2022 |
| Station 4 | West Europe, Central US, West US | December 4 to December 7, 2022 |
| Station 5 | DoD, Government Community Cloud, China | Not Scheduled |

> [!IMPORTANT] 
> Five days in advance, Microsoft will update the preceding schedule and send a notification for the set of environments that are scheduled to receive these quality updates. The preceding schedule is applicable only to environments that have been notified about an upcoming update. For information on the dark hours for each region, see [What are the planned maintenance windows by region?](../../dev-itpro/deployment/plannedmaintenance-selfservice.md#windows).
>
> For each region group, or *station*, where a quality update is currently scheduled to be rolled out, the schedule shows a range of four days. Quality updates will start with only sandbox environments. Then, as the percentage of successfully deployed sandboxes increases, deployment to production environments will begin with advance notifications to customers.
> 
> Quality updates will always occur in a rolling manner that enables us to target a set of environments per schedule and complete all the sets by the end of the fourth day for a station. However, this doesn't mean that an environment update will span four days. It just means that we can't pre-determine which set of environments will be updated on a given day within the four-day range. All updates will be done during dark hours, with near-zero downtime. Updates will definitively end within the dark-hour window of a given region.

## How are the dark hours handled for customers that have one finance and operations apps instance but are active in multiple time zones? 
There are no special schedules outside of the dark hours where a finance and operations apps instance exists, as we plan to roll out quality updates in a minimally disruptive manner with [nZDT](../../dev-itpro/deployment/plannedmaintenance-selfservice.md#what-does-near-zero-downtime-maintenance-mean).

## What is the current rollout cadence for proactive quality updates?
Proactive quality updates (PQUs) are currently shipped once a month for each supported version of a Service Update. Only one update per month is being pushed for select sandbox environments unless customers move to a new service update version. In that case, they may get a pre-scheduled PQU as part of an existing train for the new service update. After the worldwide rollout is completed in 2023, the frequency of these updates will increase. You will always receive at least one month's notice whenever there is a change to the shipping cadence.

## How will Microsoft ensure the quality of these updates?
Microsoft strives to keep the release pipeline efficient enough to deliver small payloads to keep the validation cost low. Every fix in a quality update goes through a rigorous and safe deployment process which helps improve quality and reliability, thereby reducing customer impact. Deployment will happen in stages on sandbox environments first, followed by production. Staged deployments allow for proper monitoring to determine if further deployment is safe. We will stop the rollout if issues are detected with each group of customers deployed and ensure that each step in the rollout has enough time for issues to surface. For every upcoming quality update, we will provide visibility into the schedule through updates to public documentation and emails, so customers can plan ahead.

## Can customers delay, reschedule, or pause a quality update?
No. The main objective of quality updates is to ensure fundamentals like security, privacy, reliability, availability, and performance are continuously improving for our customers. By delaying or pausing an update, security, availability, and reliability will be at risk.

## How do I know what set of changes went into a quality update payload?
The following steps are a temporary solution as we continue to work on providing a better solution to identify the list of changes that go into a quality update payload. 

Use KB# 745340 for the 10.0.28 Quality Update train and the related App version 10.0.1265.89.

1. In Lifecycle Services, open the **Environment details** page for your sandbox. 
2. In the **Available Updates** section, select **View Update** for the latest Quality Update build. 
3. Export the build into a CSV or Microsoft Excel file.
4. In the exported file, sort the information based on time (oldest first) and then search for the KB number 745340 in the **Update Id** column. You should now be able to see the delta list of KBs.
 
> [!NOTE]
> The export to a CSV or Excel file must happen before the environment is updated. Otherwise, you can use an environment with a similar configuration that doesn't have the update installed and follow the steps above.

[![Example of environment with quality update.](./media/how-to-get-kb-list-pqu.png)](./media/how-to-get-kb-list-pqu.png)

## What is the process if a critical issue is found after a quality update?
A critical issue or regression is one or more events that typically cause multiple customers to have a degraded experience with one or more of our services. These issues can cause unplanned downtime including unavailability, performance degradation, and interference with service management. If there is a broad customer impact due to such regressions, we will stop the rollout of a quality update until we can communicate and fix the issue. Typically, the next quality update will have the necessary fix to resume rollout.

If a single customer environment is affected, contact Microsoft support to open a ticket. Based on the justification, we will stop the quality update rollout to all other environments in that project until the issue is mitigated.

## Can customers still manually apply hotfix updates from Lifecycle Services?
Yes. To ensure ongoing parity with how hotfixes work, hotfix updates can still be applied to customer environments in Lifecycle Services. However, it's important to note that hotfixes that are deployed as part of a quality update go through the standard SDP before the update is deployed. This reduces the risk of regressions due to higher quality. We recommend that you choose a quality update over manually applying hotfixes for increased reliability.

## Can customers proactively install a quality update build ahead of the schedule?
Yes. You can install a quality update proactively. Microsoft will skip the update if the environment's current build version is equal or higher than the quality update in question.

## If an environment has an upcoming scheduled monthly service update within a week, will it still receive quality updates?
- Quality updates aren't applied to production environments if there's an impending service update scheduled within a week from when the quality update is scheduled to happen.
- If a sandbox environment has the same or higher build version than the impending quality update, it will be skipped.
- If a production environment has the same or higher build version than the impending quality update, it will be skipped.
- If a sandbox has the same or higher build version because of a quality update or a manual update to the production, the production will still get the scheduled version of the monthly service update. If you don't want the scheduled production environment to be updated to the service update version, you can pause the service update from Lifecycle Services. 
- We recommend you utilize the latest quality update build to test your changes for an upcoming service update for better stability and results.

## If an environment has an upcoming scheduled action and a scheduled quality update in the same maintenance window, will it still receive the quality update?
If there is any contention with a pre-scheduled action, for example a Point In Time Restore (PITR), the quality update will be rescheduled to the next available maintenance window within the four-day window. For more details on the schedule, see [What is the schedule for proactive quality updates?](#schedule). 

## Can an environment be brought back to its previous state if there are issues after a quality update is applied?
After a quality update is applied, there is no rollback under any circumstances. There are only patch forward options available to mitigate issues.

## What about FDA regulation and GPX?
The plan for customers subject to FDA validation and regulation is still evolving. Expect more updates in this space soon. For now, all such customers are exempt from quality updates. To ensure a customer falls under FDA regulations, please visit [Microsoft Azure GPX Offering](/azure/compliance/offerings/offering-gxp).

## What versions of service updates are supported for these quality updates?
Customers on all supported version of service updates qualify for quality updates. 

## Finance and operations apps deployments with Retail components typically require additional work in addition to having to redeploy MPOS. How will these quality updates impact the Retail SDK? 
Because the nature of the hotfix itself doesn't change in the quality updates payload, we don't anticipate any additional impact specifically related to Retail components at this time.

## Is there any impact to Cloud Hosted Environments (CHE)? 
CHE environments are out of scope for quality updates because they are outside the purview of Microsoft.

## Are there any integration issues with Microsoft Dataverse? 
There are no known integration issues for quality updates with Dataverse.

