---
# required metadata

title: Cloud platform monthly updates FAQ
description: This topic provides some important information about the monthly updates of the Microsoft Dynamics 365 for Finance and Operations cloud platform.
author: manalidongre
manager: AnnBe
ms.date: 05/03/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 273383
ms.assetid: ac5c9f89-98a6-481f-a0d6-a9627e01030e
ms.search.region: Global
# ms.search.industry: 
ms.author: meeram
ms.dyn365.ops.version: Platform update 5
ms.search.validFrom: 2017-03-31

---

# Cloud platform monthly updates FAQ

[!include [banner](../includes/banner.md)]

This topic provides important information about the monthly updates of the Microsoft Dynamics 365 for Finance and Operations cloud platform.

## What is the rationale behind the cloud platform monthly updates?

Since Platform update 3, Microsoft has been committed to backward compatibility in the cloud platform for Finance and Operations and has removed the capability to make intrusive customizations in the platform. (That method of customization is also known as *over-layering*.) In addition, because platform updates are binary-compatible with your custom code, you don't have to compile your code to take a platform update. Therefore, you can make rich customizations that use extensions, but you can still stay up to date without having to do costly code upgrades.

Starting with Platform update 4, monthly updates are released for the cloud platform. Therefore, you can keep new and existing environments up to date with the latest innovations at the click of a button. Monthly platform updates are compatible, and an explicit opt-in option will be added for features that modify the behavior of existing functionality.

## Why do I have to move to the latest platform update?

A move to the latest released platform version helps improve the overall reliability and service experience, and also fixes any known issues that exist in your environments. Therefore, we require that you be current with the latest platform update that Microsoft has released.

## Is this a one-time activity, or will future platforms also be pushed in a similar manner?

As stated in the [Software lifecycle policy](../migration-upgrade/versions-update-policy.md), Microsoft will continue to work closely with you to help guarantee that your environments are updated and current. Starting in July 2018, all customer environments will be continuously updated and kept current on the latest version. For more details about these changes, see [Software lifecycle policy](../migration-upgrade/versions-update-policy.md).

## What kind of update will be applied?

The platform update package will be applied to your environment. This package is a collection of new features and binary fixes that have been made to the platform. This package doesn't contain any application (X++ or binary) fixes.

## What is the overall process that will be used?

Microsoft will notify you five days before an update will be applied to the Tier 2 Standard Acceptance Test (Sandbox) environment that you purchased. You will have five days to test and validate the platform version in that sandbox environment before the update is applied to your production environment. No explicit sign-off will be required.

## What is the expected downtime?

The expected downtime of a successful update is one hour. However, we ask for three hours of downtime in case issues occur while the update is applied. We are actively working to reduce the downtime that is required, and you should see improvements in the upcoming releases.

## Where can I find details about the maintenance windows when the update will be applied?

An email notification will contain details about the environment that is being updated, the amount of downtime, and the time when the update will be applied. For more details, see [What is a planned maintenance window?](../lifecycle-services/planned-maintenance-window-faq.md)

## Who will receive the email notifications?

The Project owner, Organization administrator, and Environment manager roles in Microsoft Dynamics Lifecycle Services (LCS) will receive the email notifications. If you aren't part of the project but still want to be notified, on the environment details page for a specific environment, in the Notification list, add the email addresses of the interested stakeholders as a colon-separated list. In the future, we will consider publishing a schedule of upcoming updates.

## Do I have to do anything to prepare for the update?

We ask only that you sign off on any complete package applications in the purchased Tier 2 Standard Acceptance Test (Sandbox) and production environments. To sign off, on the environment details page, set the package application status to **Sign-Off**.

## What details will the release notes for platform updates provide? Will there be a list of fixes and new features, and information about the processes that those fixes and features affect?

To see a list of the new or changed features in the latest monthly update, see [What's new or changed](../../fin-and-ops/get-started/whats-new-changed.md). We also publish Microsoft Knowledge Base (KB) articles that document any new fixes and features. Feedback that is provided for the [What's new or changed](../../fin-and-ops/get-started/whats-new-changed.md) topic that we currently publish will help us understand whether there are gaps in the communication. 

Platform updates don't contain any application changes. Therefore, the impact should be minimal.

## What validations does Microsoft do for platform changes that will be applied during the update?

Before the update is applied, Microsoft runs validations to make sure that there is no impact on components outside the platform, such as Management reporter and Retail. Microsoft also makes sure that changes are backward-compatible.

After the update is applied, Microsoft validates that it was successful, and that the environment is running as expected. As part of this validation, Microsoft runs verification tests to make sure that Finance and Operations can be used to complete transactions.

## What kind of validation requirements do I have to complete?

When a platform update is applied, you don't have to complete any validations. Microsoft is responsible for making sure that the updates are backward-compatible with standard Finance and Operations. However, if you prefer, you can complete basic acceptance tests of your key scenarios, because Microsoft doesn't perform those validations after updates are applied. For example, platform components include Microsoft Office and Microsoft Excel integrations, workflows, form personalization, Data management framework, ODATA integrations, entity store, and Microsoft Power BI integration. You might find it beneficial to test functionality that involves these components.

We recommend that you automate functional validations to reduce the validation effort.

## What tools does Microsoft provide to manage and run acceptance tests?

See the [Continuous delivery home page](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/dev-tools/continuous-delivery-home-page) and the [Automated testing guidance for AX 7](https://blogs.msdn.microsoft.com/axdevalm/2016/08/12/automated-testing-guidance-for-ax-7/) blog post.

## What are the timeframes? How long will I have to validate?

You will have five business days to validate your environment between sandbox and production updates.

## How do I report an issue that is identified during validation of the update that was applied to the environment?

You should report issues through the existing support channel via LCS.

## What is the process if I find issues in the sandbox environment?

If you find issues in the sandbox environment, you can postpone the update by completing the op-out survey. You can postpone the update for up to 30 days. In this case, you should log a support incident for the issue that was found, so that Microsoft can investigate it.

## How can I revert a platform update if I find an issue during validation?

Currently, you can't roll back a successful update. However, in the coming months, we will provide a way to roll back platform updates.

## Are Management reporter, Retail, and Document routing agent updated?

Management reporter and Retail aren't included in the platform updates that Microsoft releases. However, starting in May 2018, Financial reporting will be included in updates.

Updates to Document routing agent are managed by the customer and aren't part of the platform update.

## Are batch jobs and external pieces suspended? How is this process managed?

Batch jobs are suspended during the maintenance windows and resume when the maintenance is completed.

## How long can I stay on a specific monthly platform update?

The [Software lifecycle policy](../migration-upgrade/versions-update-policy.md) states that a customer must stay current on the latest platform update that Microsoft releases. You can postpone an update for up to 30 days. After that time, your environment will be updated. For more details, see [Software lifecycle policy](../migration-upgrade/versions-update-policy.md).

## How can I get early access to the platform bits for validation?

If you're a partner and are interested in getting early access to the platform update, join the [PEAP program](http://aka.ms/PEAPnomination) by submitting the nomination survey at <http://aka.ms/PEAPnomination>. If you're a customer and want your environments to always run on the latest platform, submit the nomination survey at <http://aka.ms/CAAPnomination>.

## How can I get the exact package version that is applied to my Sandbox environment by Microsoft ?

When Microsoft updates your Tier 2 Sandbox environment, a copy of the package version is saved in the LCS Project Asset Library.

## I prefer that Microsoft update a Standard Acceptance Test (Sandbox) environment that differs from the Tier-2 sandbox environment that I purchased. What can I do?

In the opt-out survey, Microsoft will provide a place where you can enter a different sandbox environment ID. Note that Microsoft won't update Tier 1 sandbox environments. Tier 1 sandbox environments are environments that are deployed as a single virtual machine (VM).

## Can I opt in to have Microsoft manage additional environments?

Currently, the only environment that will be updated is the default Tier 2 Standard Acceptance Test (Sandbox) environment. However, we will provide a way for customers to opt in additional Tier 2+ environments.

## What if the timeframe that is proposed doesn't work with my schedule, or I want a different window for the update?

The email communications include a link to an opt-out survey. In this survey, you can choose a different date. However, you can postpone the update for only up to 30 days.

## Will the updates be forced every month, or will there be some allowance to delay the updates?

We want customers to stay current. We will allow customers to delay the update for up to 30 days. After that time, the environment will be updated with the latest release of the platform.

## When should I update my dev/build environment?

After Microsoft updates your production environment, apply the update to the rest of your environments (such as additional sandboxes and dev/build environments). You can take the latest platform update package from the **Platform update** tile on the environment details page in LCS. For additional instructions, see [Apply the latest platform update](../migration-upgrade/upgrade-latest-platform-update.md).

## In the scenario where Microsoft initiates platform updates, if an update is completed on a Tier 2 Standard Acceptance Test (Sandbox) environment but isn't yet applied to the production environment, there is a gap of five days when the sandbox and production environments are on different versions. If we find an issue in the production environment, can we still follow the process of applying a package to the sandbox environment and then moving it to the production environment, even though the versions the environments are on different versions?

Yes. Because platform updates are backward-compatible, even though your Tier 2 Standard Acceptance Test (Sandbox) and production environments are on different versions, you will still be able to apply packages on the sandbox environment first and then move it to the production environment. This flow is supported. You can also proactively update the platform of your production environment to the same version as the platform of your default Tier 2 Standard Acceptance Test (Sandbox) environment. 

## How can I get early access to non-released platform updates?

You can join the Microsoft Continuous Auto-Update Advantage Program (CAAP), where Microsoft will keep your platform always current. If you're interested in learning more and signing up for the program, you can find the nomination survey at <http://aka.ms/CAAPnomination>.

## We have seen cases where ISV solutions are dependent on platform updates. How can we make sure that versions that are compatible with the platform update are available from all involved ISVs before the platform update is applied?

Independent software vendors (ISVs) develop on the minimum required platform release that their code depends on. Platform updates to your customer environments will be compatible. Nevertheless, we recommend that the ISVs be part of our PEAP programs, so that they can get early access to the platform bits and validate their solutions against the platform before it's made generally available.

## What level of involvement do you foresee for the implementation partners?

We recommend that partners sign up for the PEAP program, so that they get early access to the platform bits before they are applied to customer environments. Their only involvement is to make sure that other environments are also updated. 

## Can partners see the communications about platform updates before the customer, or can they get an update earlier?

Partners can sign up for the PEAP program to get early access to the platform bits. We also ask that partners be added to the customer's project as a stakeholder or an interested party by using the Notification list. We are considering publishing a schedule of the updates in the upcoming months.
