---
title: Go-live for implementation projects FAQ
description: Access frequently asked questions about how to go live with an implementation project and how to configure and request production environments.
author: alejandra-cabrales
ms.author: alcabral
ms.topic: article
ms.date: 06/22/2022
ms.custom:
ms.reviewer: johnmichalak   
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-01-31
ms.search.form:
ms.dyn365.ops.version: July 2017 update
---

# Go-live for implementation projects FAQ

[!include [banner](../../../finance/includes/banner.md)]

This article lists frequently asked questions about how to go live with an implementation project.

## When can I configure and request my production environment?

Typically, a production environment is deployed after all customizations are code-complete, user acceptance testing (UAT) is completed, customer has signed off on the solution, there are no blocking issues for go-live, and a **Go-live Readiness Review** is successfully completed with Microsoft. To understand the process, see [Prepare for go-live](prepare-go-live.md). 

A production environment can be used exclusively for running your business operations and should not be used for testing or training purposes. You will be able to perform the cutover, and if planned, to mock the cutover in production. To test the solution you must use a sandbox environment, which is designed with the necessary elements and services for testing.

## What are the prerequisites to deploy a production environment?

For a list of prerequisites, see [Prepare for go-live](prepare-go-live.md).

## What is a Go-live Readiness Review and why is it required?

The Go-live Readiness Review is aimed to assess project readiness and help you have a smooth and successful go-live. To understand the process, see [Prepare for go-live](prepare-go-live.md). 

This review is mandatory for every implementation project before you can deploy a production environment.

## I want to request my production environment. Who do I contact for a Go-live Readiness Review?
Please follow the guidance in the [Prepare for go-live](prepare-go-live.md) article to understand how to initiate the Go-live Readiness Review.  

## The Production button isn't available in LCS. How do I request my production environment?

The **Production** button in LCS is available only after you've completed the **Analysis**, **Design & develop**, and **Test** phases of the LCS implementation methodology and a **Go-live Readiness Review** is completed with Microsoft. For more information, see [Prepare for go-live](prepare-go-live.md).

For more information about how to complete methodology phases in LCS, see [Lifecycle Services (LCS) for finance and operations apps customers](../lifecycle-services/lcs-works-lcs.md).

## My sandbox environment is currently on an update that is set to expire in two months. Can I request a production environment that has the latest update?

We strongly recommended that you deploy the production environment with the same version used in the acceptance testing environment, which should be the version you are planning to go live with. Going live on a version different from the version you tested on is **not** recommended, as it can lead to unexpected behavior and unforeseen issues that can negatively impact the go-live experience. 

It is strongly recommended that you go live on a version that is **not** near end of service, so that you are able to apply quality updates for some time after the go-live, if needed. It is important to carefully plan the version on which you are conducting the User Acceptance Test (UAT), and keep it as up-to-date as possible.

For more information, see [Software lifecycle policy and cloud releases](../migration-upgrade/versions-update-policy.md) and [Service update availability](../get-started/public-preview-releases.md).

## Our sandbox environments are deployed in a different datacenter from where we want our production environment to be deployed. Can I select a different datacenter for my production environment?

It is strongly recommended to deploy the production environment in the same datacenter used in the acceptance testing environment, which should be the data center you are planning to go live with. Using the same datacenter helps ensure that you are validating latency as well as support for all services under production-like conditions. Going live on a datacenter different from the one you tested on is **not** recommended, as it can lead to unexpected performance issues and unforeseen functionality gaps that can negatively impact the go-live experience.

For information that can help you select the correct datacenter, see the [Network requirements](../get-started/system-requirements.md#network-requirements) section of the "System requirements" article.

## How will my production environment be sized?

Your production environment will be sized based on the current user license count and the information in the subscription estimate that is active when you request the production environment.

> [!NOTE]
> If you submit a new subscription estimate, your production environment might have to be resized, depending on the number of users, the type of user licenses, and the expected peak transaction volume. After the new estimate is processed, within 3 days, the next servicing operation on the environment will apply the update automatically. Alternatively, a support ticket can be created to request a specific time to apply the changes.

## I submitted the request for a production environment, but I made a mistake. Can I still change it?

No. Production environment deployment starts as soon as you submit the request. Please wait until the deployment has completed and then log a support ticket to have the production environment deleted, so that you can redeploy it.

## How long does it take to deploy my production environment?

After the Go-live Readiness Review with Microsoft is complete, a production environment slot in LCS is enabled and the project team (customer/partner) can trigger the environment deployment. The deployment process takes approximately 30 minutes.

## What level of access do I have in my production environment? Can I sign in to the VM?

No. Access to the production environment is limited. You can't access the virtual machine (VM) or Microsoft Internet Information Services (IIS). You also can't access the database through Microsoft SQL Server Management Studio.

## How often is my production database backed up?

Databases are protected by automatic backups. Full database backups are done weekly, differential database backups are done hourly, and transaction log backups are done every five minutes. Automatic backups are retained for 28 days.

For more information, see [Learn about automatic SQL Database backups](/azure/sql-database/sql-database-automated-backups).

## Can I request a copy of the backup of my production database?

No. However, you can copy your production database to your Tier 2 or higher sandbox environment. After the copy operation is completed, you can back up your sandbox environment. For more information, see [Database refresh](../database/database-refresh.md).

## My golden configuration database is in a Tier 1 sandbox environment. How can I copy and restore it to my production environment?
To copy and restore your database, follow the instructions in the article, [Golden configuration promotion](../database/dbmovement-scenario-goldenconfig.md). 

> [!NOTE]
> If your golden configuration is in data packages, you must manually import the data packages to the production environment.

## After go-live, can I apply new code changes to the production environment?

Yes. 

For more information, see [Apply updates to cloud environments](../deployment/apply-deployable-package-system.md).

## What should I do if my production environment is down?

To report a production outage, follow the process described in the article, [Report a production outage](../lifecycle-services/report-production-outage.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

