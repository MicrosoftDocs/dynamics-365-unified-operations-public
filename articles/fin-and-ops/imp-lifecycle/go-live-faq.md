---
# required metadata

title: Go-live frequently asked questions for Microsoft Dynamics 365 for Finance and Operations 
description: This topic lists frequently asked questions about going live with a Microsoft Dynamics 365 for Finance and Operations, Enterprise edition project.
author: sshashi7
manager: AnnBe
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sshashi
ms.search.validFrom: 2018-01-31
ms.dyn365.ops.version: July 2017 update

---

# Preparing for go live

[!include[banner](../includes/banner.md)]

This topic lists frequently asked questions about going live with a Microsoft Dynamics 365 for Finance and Operations, Enterprise edition project.

## When can I configure and request my production environment?

Typically, a production environment is deployed after all customizations are code-complete, user acceptance testing (UAT) is complete, the customer has signed off on the solution, and there are no go-live blocking issues.

When you're at this stage, the Microsoft FastTrack team will work with the project team to do a Pre-go-live review or assessment.

## What are the prerequisites to deploy production environment?

The prerequisites are listed in the topic [Preparing for Go-live](prepare-go-live.md)

## What is a Pre-go-live review and why is it required?

The Pre-go-live review is part of the [Microsoft FastTrack program](../fin-and-ops/get-started/fasttrack-dynamics-365-overview.md), in which a solutions architect assesses readiness of an implementation project for a successful cutover and Go-live. This review is mandatory for every Finance and Operations project before a request to go live in a production environment.

## I want to request my production environment but who do I contact for a Pre-Go-live review?

If you have a FastTrack solution architect assigned to your project, please reach out to him or her directly. Otherwise, based your Go-live date specified in LCS, you will receive an email to fill out the Pre-Go-live checklist and send it to <go-live@microsoft.com> few weeks before the Go-live date. If you’ve not received an email and you’re ready for Go-live, you can download the Pre-Go-live Checklist from here, fill it up and send it to <go-live@microsoft.com>.

## The Production button is not enabled in LCS. How do I request my production environment?**

To enable the **Production** button in LCS, you must have completed the **Analysis**, **Design & develop**, and **Test** phases of the LCS implementation methodology. Read more about completing [Methodology tasks and phases](../dev-itpro/lifecycle-services/lcs-works-lcs.md)

>   [!NOTE]
>   Your production environment will not be deployed until the Pre-Go-live review has been completed.

##  My sandbox environment is currently on a platform update which is set to expire in 2 months. Can I request a production environment with the latest platform update?

No, requests to have a production environment on a different version than your sandbox will be denied. When configuring a production environment, you must select the same application and platform version as that of the sandbox environment in which you signed off on your solution. If you want a production environment with the latest platform update, you must apply the latest platform update to your sandbox environment first, test it, and sign off.

For more information, see [Versions Update Policy](../dev-itpro/migration-upgrade/versions-update-policy.md)

## My sandbox environments are deployed in the Central US datacenter, but we would like to have our Production environments deployed in the West US datacenter. Can I select West US as my data center in my Production configuration?

No, requests to have a production environment in a different data center than your sandbox will be denied. We require that all of your environments reside in the same data center. If you want to have your production environment in the West US data center, you must first move your Sandbox environments to the West US data center, test it, and sign off.

See the [Network requirements section in the System requirements topic](/fin-and-ops/get-started/system-requirements.md#network-requirements) to help you choose the right data center.

## How will my production environment be sized?

Your production environment will be sized based on the current user license count and the information in subscription estimate that is active when you request the production environment.

> ![NOTE]
> If you add additional users in future, you must create a support ticket to activate a new subscription estimate. Whether resizing is necessary depends on the number of users, the type of user licenses and the expected peak transaction volume. Resizing of the production environment requires downtime.

1.  **I submitted the request for Production environment, but I made a mistake;
    can I still change it?**

>   Yes, as long as the Production environment is in *Queued* state you can
>   clear the sign off, make changes, and then sign off again.

1.  **How long does it take to deploy my production environment?**

>   Once the Pre-Go-live review with the Microsoft FastTrack team is complete
>   and the production request is submitted, the deployment of production should
>   complete within 2 business days.

1.  **What level of access do I have in my D365FFO Production environment? Can I
    login to the VM?**

>   No. Access to Production environment is limited. You cannot access the VM,
>   IIS or manipulate the database through SQL Management Studio.

1.  **How often is my production database backed up?**

>   Databases are protected by automatic back-ups per [Azure
>   capabilities](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-automated-backups).
>   Full database backups are taken weekly, differential database backups are
>   taken hourly, and transaction log backups are taken every 5 minutes.
>   Automatic back-ups are retained for 35 days.

1.  **Can I request a copy of the backup of my production database?**

>   No. However, you can raise a database refresh service request to copy your
>   production database to your tier-2 and above Sandbox environment. You can
>   take a backup of your Sandbox environment once the copy request is complete.

1.  My gold configuration database is in a tier 1 sandbox, what should I do to
    copy and restore it to production environment?"**?**

>   First, you will have to move your gold configuration database from tier 1 to
>   tier 2. Next, You can raise a service request to copy your golden
>   configuration from Tier 2 and above sandbox environment (like Sandbox:
>   Standard Acceptance Test) to Production environment.

>   **See**: Copy a Finance and Operations database from SQL Server to a
>   production Azure SQL Database environment

>   **Note**: In case your Golden configuration is in Data Packages, you will
>   have to import them in Production environment manually.

1.  **After going live, can I apply new code changes to the production
    environment?**

>   Yes. You can raise a service request in LCS to apply a deployable package to
>   your production environment. Applying 1 deployable package to production
>   involves a lead time of 5 hours and downtime of approximately 5 hours.

>   **Link**: [Apply deployable package
>   ](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/apply-deployable-package-system)

1.  **What should I do if my production environment is down?**

>   Please follow the process in the following link to report production outage

>   *New process to report a production outage through Lifecycle Services*



