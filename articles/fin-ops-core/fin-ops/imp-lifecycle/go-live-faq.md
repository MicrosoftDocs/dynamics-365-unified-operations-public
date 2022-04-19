---
# required metadata

title: Go-live for implementation projects FAQ
description: This topic lists frequently asked questions about how to go live with an implementation project.
author: OlgaPetrovaFT
ms.date: 04/19/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: olpetrov
ms.search.validFrom: 2018-01-31
ms.dyn365.ops.version: July 2017 update

---

# Go-live for implementation projects FAQ

[!include [banner](../includes/banner.md)]

This topic lists frequently asked questions about how to go live with an implementation project.

## When can I configure and request my production environment?

Typically, a production environment is deployed after all customizations are code-complete, user acceptance testing (UAT) is completed, customer has signed off on the solution, there are no blocking issues for go-live, and a **Go-live Readiness Review** is successfully completed with Microsoft. To understand the process, see [Prepare for go-live](prepare-go-live.md). 

A production environment can be used exclusively for running your business operations and should not be used for testing or training purposes. You will be able to perform the cutover, and if planned, to mock the cutover in production. To test the solution you must use a sandbox environment, which is designed with the necessary elements and services for testing.

## What are the prerequisites to deploy a production environment?

For a list of prerequisites, see [Prepare for go-live](prepare-go-live.md).

## What is a Go-live Readiness Review and why is it required?

The Go-live Readiness Review is aimed to assess project readiness and help you have a smooth and successful go-live. To understand the process, see [Prepare for go-live](prepare-go-live.md). 

This review is mandatory for every implementation project before you can deploy a production environment.

## I want to request my production environment. Who do I contact for a Go-live Readiness Review?
Please follow the guidance in this article to understand how to initiate the Go-live Readiness Review.  For more information, see [Prepare for go-live](prepare-go-live.md).

## The Production button isn't available in LCS. How do I request my production environment?

The **Production** button in LCS is available only after you've completed the **Analysis**, **Design & develop**, and **Test** phases of the LCS implementation methodology and a **Go-live Readiness Review** is completed with Microsoft. For more information, see [Prepare for go-live](prepare-go-live.md).

For more information about how to complete methodology phases in LCS, see [Lifecycle Services (LCS) for Finance and Operations apps customers](../../dev-itpro/lifecycle-services/lcs-works-lcs.md).

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

Please log a support ticket to address the issue.

## How long does it take to deploy my production environment?

After the Go-live Readiness Review with Microsoft is complete, a production environment slot in LCS is enabled and the project team (customer/partner) can trigger the environment deployment. The deployment process takes approximately 30 minutes.

## What level of access do I have in my production environment? Can I sign in to the VM?

No. Access to the production environment is limited. You can't access the virtual machine (VM) or Microsoft Internet Information Services (IIS). You also can't access the database through Microsoft SQL Server Management Studio.

## How often is my production database backed up?

Databases are protected by automatic backups. Full database backups are done weekly, differential database backups are done hourly, and transaction log backups are done every five minutes. Automatic backups are retained for 28 days.

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
