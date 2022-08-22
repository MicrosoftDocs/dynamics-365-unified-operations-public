---
# required metadata

title: Proactive quality updates
description: This article provides information about proactive delivery of quality updates.
author: rashmansur
ms.date: 08/22/2022
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

## Focus on quality updates

We currently provide seven [service updates](public-preview-releases.md) per year. For example, version 10.0.29 is a service update. Until recently, there were eight updates per year. However, we dropped one update in response to customer feedback that revealed a desire to avoid changes near the end of the calendar year.

We won't be changing the cadence of the service updates. Instead, our next step forward in the One Version journey is focused on *quality updates*. Quality updates are cumulative builds of hotfixes. They don't include new features. At any given time, our entire community of customers is spread between the three or four most recent service updates. However, for any given service update, dozens of different quality update versions can be used within the group, depending on the dates when people deployed. In our next step, we will proactively broadcast quality updates. We already use this model for our Dataverse-based applications and have seen the expected results of improved quality and decreased support incidents.

Of course, a reduction in defects could reduce or completely eliminate the need for quality updates. We have multiple initiatives in flight to reduce the defects that require quality updates. Even when payloads are reduced in the quality update, consistency across the customer base will improve supportability, get improvements to customers more quickly, and reduce the frequency of customers encountering issues that solutions already exist for.

## Making proactive distribution possible

Multiple advances have already been deployed that enable proactive delivery of quality updates:

- **Near-zero downtime updating** – To push more frequent environments, it's essential that the impact to environment availability be reduced to preserve Dynamics 365 Service Level Agreements (SLAs). Near-zero downtime updating was originally introduced to help improve monthly operating system patching by using a cluster failover to activate the updated image with minimal disruption. The mechanism for applying updates is being enhanced so that it's even less disruptive, and it will cover both operating system patching and quality update deployment.

    For interactive users, an active session might be interrupted, and the retry will go to the now-updated environment. With the introduction of [priority-based batch scheduling](../../dev-itpro/sysadmin/priority-based-batch-scheduling.md), which is now available on an opt-in basis, batch scheduling and processing recovers and resumes immediately after the update. Priority-based batch scheduling will be in place for customers before they start to participate in proactive distribution of quality updates for their production environments.

- **Dark hours** – Dark hours are defined for each Azure region, and near-zero downtime updates will occur during the dark hour period.

## The proactive update process

Deployment of proactive quality updates will follow a safe deployment process (SDP). The specifics of the SDP will evolve, but quality updates will initially be deployed to sandbox environments. The process will start with environments that opt in for early deployment. As the percentage of successfully deployed sandboxes increases, deployment to production environments will begin. Once again, the process will start with environments that opt in for early deployment. Listening systems will monitor system telemetry and Livesite incidents, and will stop the rollout of a specific version if any regression is detected. Customers will still be able to pull the quality updates ahead of proactive deployment if they want.

Current release management data shows that less than 3 percent of regressions are introduced in quality updates. With increased focus on eliminating regression and an enhanced SDP, the potential impact of regressions will be dramatically lower than the quality gains that are achieved by more quickly getting fixes deployed to customers broadly.

## Process changes

A set of process changes is being implemented ahead of the activation of proactive quality update deployment:

- **Schema** – Tooling will ensure that quality update builds include only schema changes that can be applied while the service is online. This approach will help preserve the ability to apply the update with near-zero downtime.
- **Increased change scrutiny** – Currently, there is already an extra process step to approve changes for inclusion in a quality update. The scrutiny in the extra step will be increased to help reduce the potential for regressions. Breaking changes aren't allowed in quality updates, and the increased change scrutiny will help ensure that we meet this target.
- **Visibility** – The Admin Center will include notification when a quality update is proactively delivered. It will also show the expected schedule for upcoming updates. In addition, support teams and incident leads will have visibility into where quality updates have been proactively deployed.
- **Version fallback** – Flighting will be used to group all changes in a proactive quality update. If fallback is required after a proactive deployment, it can be done through the flighting system.
- **Sandbox sync designation** – Many customers who have multiple sandboxes keep one sandbox deployed where the version matches production, to help with troubleshooting. Customers who have multiple sandboxes will be able to specify, via the Admin Center, that a sandbox environment should not receive the proactive update deployment together with other sandboxes but should instead receive it later, together with their production environment. Note that if a customer is using a sandbox to test a newer version than their production, that sandbox will receive quality updates to the newer version.

## When will proactive quality updates start?

Distribution of proactive quality updates for sandbox environments is expected to begin in late September or October 2022 for Azure public cloud customers. Trial environments will also start to receive proactive update deployment at that time. In September, a notification will be sent to each customer to inform them about the expected schedule for their environments. Exceptions to the proactive updated distribution process will be allowed only for FDA-regulated customers. We're still working out how regulated environments and sovereign and government cloud customers will be managed.

We will publish updates about the progress of the rollout of proactive quality updates. Our current expectation is that this process will apply only to sandboxes until sometime in March 2023. Proactive updating of production environments is then expected to begin later in March or in April 2023. During the six-month period, we will gradually increase the percentage of sandbox environments that receive proactive updates, until all designated environments are included. Throughout the period, we will monitor to ensure that the deployment process is seamless and that we're hitting our target of non-disruptive payloads.

Because customers will regularly receive smaller payloads, we expect the process of staying current to become simpler. We will adjust the frequency of update deployment as we demonstrate the ability to run the process without disruption. This process is already working effectively for our Dataverse platform and applications, and is delivering the anticipated improvements in service quality. We're anxious to take the same step forward for finance and operations applications.
