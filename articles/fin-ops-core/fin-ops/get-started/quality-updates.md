---
# required metadata

title: Quality updates
description: This template contains examples of Markdown syntax, as well as guidance on setting the metadata.
author: rashmansur
ms.date: 08/19/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: rashmim
ms.search.validFrom: 2022-08-19
ms.search.form:
ms.dyn365.ops.version: 10.0.29
---

# Quality updates 

[!include[banner](../includes/banner.md)]

Over the last several years, we have made continuous progress on what we refer to as [One Version](../../dev-itpro/lifecycle-services/oneversion-overview.md). The premise of One Version is simple – the closer that we can get to having all customers operating on the same software version, the higher the quality that we can deliver. We find and fix issues once, and we get those solutions in the hands of more customers more quickly. 

We see the results that confirm this with lower incident counts across our products. When we are not on the same version, we consistently see customers impacted by issues where the solution is already available. We’ve made great progress already with Dynamics 365 Finance, Supply Chain, Project Operations and Commerce, and thanks to recent technical advances, it’s now possible to take the next step. The following information lays out what we’re going to do, what we’ve already done to set the stage, and how and when we will introduce the new capabilities without disruption. 

## Focus on quality updates

Today, Dynamics 365 Finance and Operations workloads publish seven numbered updates per year, for example 10.0.29.This is a recent adjustment from eight per year, with one pdate dropped in response to customer feedback around the desire to avoid changes around calendar year end.    

We are not changing the cadence of number releases – instead, our next step forward on One Version focuses on Quality Updates. Quality Updates are cumulative builds of hotfixes: they do not include new features. At any given time, our entire community of customers is spread between the three or four most recent numbered updates. Within the group on any one given numbered update, however, there can be dozens of different quality update versions in use dependent on the dates people deployed. Our next step in the One Version journey will broadcast quality updates proactively. This follows the model we already use for our Dataverse-based applications where we see the expected results of improved quality and decreased support incidents. 

Of course, a reduction in defects could reduce or eliminate the need for Quality Updates altogether. We have multiple initiatives in flight to reduce the defects that require Quality Updates. Even with reduced payloads in the Quality Update, having consistency across the customer base will improve supportability, get improvements to customers more quickly, and reduce the frequency of customers encountering issues where solutions already exist. 

## Making proactive distribution possible

Multiple advances have already been deployed that enable proactive delivery of quality updates:

- **Near-zero downtime updating** – Near Zero Downtime Updating – In order to push more frequent environments, it is essential that the impact to environment availability be reduced to preserve Dynamics 365 Service Level Agreements (SLAs). Near Zero Downtime Updating was originally introduced to improve monthly OS Patching, leveraging a cluster failover to activate the updated image with minimal disruption. The mechanism for applying updates is being enhanced to be even less disruptive and will cover both OS patching and Quality Update deployment. For interactive users, an active session might be interrupted and the retry will go to the now updated environment. With the introduction of Priority Based Batch scheduling, now available on an opt-in basis, batch scheduling and processing recovers and resumes immediately after the update. Priority Based Batch Scheduling will be in place for customers before they begin participating in proactive quality update distribution for their Production environments. 

- **Dark hours** – Dark hours are defined for each Azure region and Near Zero Downtime updates will occur during the dark hour period. 

## The proactive update process

Proactive Quality Update deployment will follow a Safe Deployment Process (SDP). The specifics of the SDP will evolve, but Quality Updates will be deployed initially to sandbox environments, beginning with environments that opt-in for early deployment. As the percentage of sandboxes successfully deployed increases, deployment will begin to production environments – again starting with environments opting into early deployment. Listening systems will monitor system telemetry and Livesite incidents, stopping the rollout of a specific version if any regression is detected. Customers will still be able to pull the Quality Updates ahead of proactive deployment if desired. 

Looking at release management data today, less than 3% of regressions are introduced in Quality Updates. With increased focus on eliminating regression, along with an enhanced safe deployment process, the potential impact of regressions will be dramatically lower than the quality gains achieved by more rapidly getting fixes deployed to customers broadly.  

## Process changes

A set of process changes are being implemented ahead of the activation of proactive quality update deployment:

- **Schema** – Tooling will ensure that only schema changes which can be applied with the service on-line are included in Quality Update builds. This will ensure that the ability to apply the update with Near Zero Downtime is preserved. 

- **Increased change scrutiny** – today, there is already an extra process step to approve changes for inclusion in a Quality Update. The scrutiny at the extra step will be increased to reduce the potential for regressions. Breaking changes are not allowed in Quality Updates; the increased change scrutiny will help to ensure that we hit that target. 

- **Visibility** – the Admin Center will include notification when a Quality Update is proactively delivered and will show the expected schedule for upcoming updates. Support teams and incident leads will also have visibility of where Quality Updates have been proactively deployed. 

- **Version fallback** – flighting will be used to group all changes in a proactive Quality Update. If it is necessary to fall back after a proactive deployment, it will be possible to accomplish that through the flighting system. 

- **Sandbox sync designation** – many customers with multiple sandboxes keep one sandbox deployed with a version matching production to help with troubleshooting. Customers with multiple sandboxes will be able to designate via the Admin Center that a sandbox environment should receive the proactive update deployment together with their production environment rather than earlier with other sandboxes. Note that if a customer is using a sandbox to test a newer version than their production, that sandbox will receive quality updates to the newer version. 

## When will proactive quality updates start?

Proactive Quality update distribution is expected to begin for sandbox environments only in late September or October 2022 for Azure public cloud customers. Trial environments will also start receiving proactive update deployment at that time. Notification will be sent in September informing each customer of the expected schedule for their environments. There will be no exceptions to the proactive updated distribution process, other than for FDA regulated customers. We are still working out how regulated environments and sovereign and government cloud customers will be managed.  

We will publish monthly updates on Yammer reporting on progress with our rollout of proactive updating, but our current expectation is that this will only apply to sandboxes until sometime in March 2023, with proactive updating of production environments beginning in expected to start later in March or in April 2023. Over that six-month period, we will be gradually increasing the percentage of sandbox environments receiving proactive updates until all designated environments are included. Throughout, we will be monitoring to ensure that the deployment process is seamless and that we are hitting our target of non-disruptive payloads. 

With customers regularly receiving smaller payloads, we expect the process of staying current to become simpler. We will adjust the frequency of update deployment as we demonstrate the ability to run the process without disruption. This is already working effectively for our Dataverse platform and applications and delivering the anticipated improvements in service quality. We are anxious to take the same step forward for Dynamics 365 Finance and Operations applications. 

 
