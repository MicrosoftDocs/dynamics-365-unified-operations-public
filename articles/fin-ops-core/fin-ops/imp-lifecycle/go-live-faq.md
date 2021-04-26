---
# required metadata

title: Go-live for implementation projects FAQ
description: This topic lists frequently asked questions about how to go live with an implementation project.
author: sshashi7
ms.date: 07/12/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sshashi
ms.search.validFrom: 2018-01-31
ms.dyn365.ops.version: July 2017 update

---

# Go-live for implementation projects FAQ

[!include [banner](../includes/banner.md)]

This topic lists frequently asked questions about how to go live with an implementation project.

## When can I configure and request my production environment?

Typically, a production environment is deployed after all customizations are code-complete, user acceptance testing (UAT) is completed, the customer has signed off on the solution, and there are no blocking issues for go-live.

When you're at this stage, the Microsoft FastTrack team will work with the project team to do a Go-live assessment/review.

## What are the prerequisites to deploy a production environment?

For a list of the prerequisites, see [Prepare for go-live](prepare-go-live.md).

## What is a Go-live assessment/review, and why is it required?

The Go-live assessment/review is part of the [Microsoft FastTrack program](/dynamics365/fasttrack/). During this review, a solution architect assesses whether an implementation project is ready for a successful cutover and go-live. This review is mandatory for every implementation project before you can request to go live in a production environment.

## I want to request my production environment. Who do I contact for a Go-live assessment/review?
If a FastTrack solution architect is assigned to your project, contact him or her directly. Otherwise, based on the go-live date that is specified in Microsoft Dynamics Lifecycle Services (LCS), you will receive an email that instructs you to fill out the Pre-go-live checklist and send it to <d365fogl@microsoft.com> a few weeks before the go-live date. If you haven't received an email, and you're ready for go-live, you can download the checklist from **Dynamics 365 Community** on the [Go-live Planning TechTalk](https://aka.ms/FastTrackPreGoLiveChecklist) page, complete it, and send it to d365fogl@microsoft.com.

## The Production button isn't available in LCS. How do I request my production environment?

The **Production** button in LCS is available only after you've completed the **Analysis**, **Design & develop**, and **Test** phases of the LCS implementation methodology. For more information about how to complete these phases, see [Lifecycle Services (LCS) for Finance and Operations apps customers](../../dev-itpro/lifecycle-services/lcs-works-lcs.md).

> [!NOTE]
> Your production environment won't be deployed until the Go-live assessment/review has been completed.

## My sandbox environment is currently on an update that is set to expire in two months. Can I request a production environment that has the latest update?

No. We will deny any request for a production environment that is on a different version than your sandbox environment. When you configure a production environment, the versions that you select must match the versions of the sandbox environment where you signed off on your solution. Therefore, you must first apply the latest update to your sandbox environment, test it, and sign off.

For more information, see [Software lifecycle policy and cloud releases](../../dev-itpro/migration-upgrade/versions-update-policy.md).

## Our sandbox environments are deployed in the Central US datacenter, but we want our production environments to be deployed in the West US datacenter. Can I select West US as the datacenter in my production configuration?

No. We will deny any request for a production environment that is in a different datacenter than your sandbox environment. We require that all your environments reside in the same datacenter. If you want your production environment to reside in the West US datacenter, you must first redeploy your sandbox environments to the West US datacenter, test them, and sign off.

For information that can help you select the correct datacenter, see the [Network requirements](../get-started/system-requirements.md#network-requirements) section of the "System requirements" topic.

## How will my production environment be sized?

Your production environment will be sized based on the current user license count and the information in the subscription estimate that is active when you request the production environment.

> [!NOTE]
> If you add additional users later, you must create a support ticket to activate a new subscription estimate. Your production environment might have to be resized, depending on the number of users, the type of user licenses, and the expected peak transaction volume. Downtime is required in order to resize a production environment.

## I submitted the request for a production environment, but I made a mistake. Can I still change it?

Yes. As long as the status of the production environment is **Queued**, you can clear the sign-off flag, make changes, and then sign off again.

## How long does it take to deploy my production environment?

After the Go-live assessment with the Microsoft FastTrack team is completed and the production request is submitted, deployment of the production environment should be completed within 48 hours.

## What level of access do I have in my production environment? Can I sign in to the VM?

No. Access to the production environment is limited. You can't access the virtual machine (VM) or Microsoft Internet Information Services (IIS). You also can't access the database through Microsoft SQL Server Management Studio.

## How often is my production database backed up?

Databases are protected by automatic backups. Full database backups are done weekly, differential database backups are done hourly, and transaction log backups are done every five minutes. Automatic backups are retained for 35 days.

For more information, see [Learn about automatic SQL Database backups](/azure/sql-database/sql-database-automated-backups).

## Can I request a copy of the backup of my production database?

No. However, you can submit a database refresh service request to copy your production database to your Tier 2 and higher sandbox environment. After the copy request is completed, you can back up your sandbox environment.

## My golden configuration database is in a Tier 1 sandbox environment. How can I copy and restore it to my production environment?
To copy and restore your database, follow the instructions in the topic, [Golden configuration promotion](../../dev-itpro/database/dbmovement-scenario-goldenconfig.md). 

> [!NOTE]
> If your golden configuration is in data packages, you must manually import the data packages to the production environment.

## After go-live, can I apply new code changes to the production environment?

Yes. In LCS, you can submit a service request to apply a deployable package to your production environment. Application of one deployable package to a production environment involves a lead time of five hours and downtime of approximately five hours.

For more information, see [Apply updates to cloud environments](../../dev-itpro/deployment/apply-deployable-package-system.md).

## What should I do if my production environment is down?

To report a production outage, follow the process described in the topic, [Report a production outage](../../dev-itpro/lifecycle-services/report-production-outage.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]