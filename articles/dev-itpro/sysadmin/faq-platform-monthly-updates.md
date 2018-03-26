---
# required metadata

title: Finance and Operations cloud platform monthly updates FAQ
description: This topic provides some key information about the monthly updates of the Microsoft Dynamics 365 for Finance and Operations cloud platform.
author: manalidongre
manager: AnnBe
ms.date: 03/26/2018
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

# Finance and Operations cloud platform monthly updates FAQ

[!include[banner](../includes/banner.md)]

This topic provides key information about the monthly updates of the Microsoft Dynamics 365 for Finance and Operations cloud platform.

## What's the rationale behind the cloud platform monthly updates?

Since platform update 3, Microsoft has committed to backward compatibility in the cloud platform of Dynamics 365 for Finance and Operations and has removed the possibility of making intrusive customizations (also known as *over-layering*) in the platform. In addition, platform updates are binary compatible with your custom code, meaning that you do not need to compile your code to take a platform update. This enables rich customizations that use extensions, while still allowing you to stay up to date without costly code upgrades.

Starting with platform update 4, the cloud platform releases monthly updates so that new and existing environments can stay up-to-date with the latest innovations with a click of a button. Monthly platform updates are compatible, an explicit opt-in option will be added for features that alter the behavior of existing functionality.

## Why do I need to move to the latest platform update?

Moving to the latest released platform version will improve the overall reliability and service experience. It will also fix known issues that exist on your environments and for these reasons we require you to be current on the latest platform update released by Microsoft.

## Is this a one-time activity or will future platforms also be pushed in a similar manner?

As stated in the [Software lifecycle policy](../migration-upgrade/versions-update-policy.md), Microsoft will continue to work closely with you to ensure your environments are updated and current. Starting July 2018, all customers’ environments will be continuously updated and kept current on the latest version. For more details on these changes, please see the [Software lifecycle policy](../migration-upgrade/versions-update-policy.md) topic.

## What kind of update will be applied?

The platform update package will be applied to your environment. This is a collection of new features and binary fixes that have been made to the platform. This package does not contain any application (X++ or binary) fixes.

## What is the overall process that will be used?

Microsoft will notify you 5 days before an update will be applied to your purchased Tier – 2 sandbox. You will be given 5 days to test and validate the platform version in the Tier-2 sandbox prior to the update being applied to your production environment. No explicit sign off will be required.

## What’s the expected downtime?

The expected downtime of a successful update is 1 hour. We do ask for 3 hours downtime in the event of issues when applying the update. We are also actively working on reducing the downtime taken and you should see improvements in the upcoming releases.

## Where can I find details on the maintenance windows when the update will be applied?

An email notification will contain details on the environment being updated, downtime duration, as well as time when the update will be applied. For more details, please see the [Planned maintenance FAQ](../lifecycle-services/planned-maintenance-window-faq.md) topic.

## Who will receive the email notifications?

The project owner, organization administrator, and environment manager roles in Lifecycle Services (LCS) receive the email notifications. If you are not part of the project but would still like to be notified, you can go to the Notification list on the Environment Details page for a specific environment and add the email addresses of the interested stakeholders in a colon separated list. In the future, we will look at publishing a predictable schedule of the upcoming updates.

## Is there anything I need to do in preparation for the update?

There is no action item on the customer when Microsoft is pushing the update. The only ask we have is for you to sign off on any complete package applications in the purchased Tier 2 Standard Acceptance Test (Sandbox) and Production environments. This can be done by navigating to the specific environment details page and setting the package application status to Sign-Off.  

## What details will the platform update release notes provide? Will there be a list of fixes and new features with information on which processes they impact?

To see a list of the new or changed features in the latest monthly update, see the [here](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed). We do put out release notes that document any new fixes and features. Any feedback on the What’s new we publish today will help us understand if there are gaps in the communication. Platform updates do not contain any application changes and so the impact should be minimal.

## What validations does Microsoft do for changes in the platform that will be applied during the update?

Before the update is applied, Microsoft runs validations to make sure there is no impact on components outside the platform, such as Management reporter or Retail. Microsoft also makes sure that changes are backward compatible and forward compatible.

After the update is applied, Microsoft validates that it was successful, and that the environment is running as expected. As part of this validation, Microsoft runs verification tests to make sure that Microsoft Dynamics 365 for Finance and Operations can be used to complete transactions.

## What kind of validation requirements do I have to complete?

When a platform update is applied, you don’t have to complete any validations. Microsoft is responsible for making sure that the updates are backward compatible and forward compatible with standard Dynamics 365 for Finance and Operations. However, if you prefer, you can complete basic acceptance tests of your key scenarios, because Microsoft doesn’t perform those validations after updates are applied. For example, platform components include Microsoft Office/Excel integrations, workflow, form personalization, data management framework, ODATA integrations, entity store, and Power BI integration; testing functionality around these components is beneficial.

We recommend that you automate functional validations to reduce the validation effort.

## What tools does Microsoft provide to manage and execute acceptance tests?

<https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/dev-tools/continuous-delivery-home-page>

<https://blogs.msdn.microsoft.com/axdevalm/2016/08/12/automated-testing-guidance-for-ax-7/>

## What are the timeframes? How long will I have to validate?

You will have 5 business days between sandbox and production updates to validate your environment.

## How do I report an issue that is identified during validation of the update that was applied to the environment?

Issues should be reported through the existing support channel via LCS.

## What’s the process if I find issues in the sandbox environment?

If you find issues in the sandbox environment, you have the option to postpone the update by completing the op-out survey. You can postpone the update for up to 30 days. Please log a support incident for the issue that was found so it can be investigated by Microsoft.

## How can I revert a Platform update if I find an issue during validation?

You cannot rollback a successful update today. We will provide means to rollback a platform update in the coming months.

## What about MR/ Retail and DRA? Are these updated?

Management reporter and Retail are not included in the platform update release by Microsoft. However, Financial Reporting will also be included with updates starting in May 2018.

DRA updates are managed by the customer and are not part of the platform update.

## What about batch jobs – are they suspended and external pieces? How is this managed?

Batch jobs are suspended during the maintenance windows and resume when the maintenance is completed.

## How long can I stay on a specific monthly platform update?

The Software lifecycle policy states that a customer must stay current on the latest platform update released by Microsoft. You have the option to postpone an update for up to 30 days. After that your environment will be updated. For more details, please see the [Software Lifecycle Policy](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/migration-upgrade/versions-update-policy) topic.

## How can I get early access to the platform bits for validation?

If you are a partner that is interested in getting early access to the platform update, please join the [PEAP program](http://aka.ms/PEAPnomination) by completing this nomination survey: http://aka.ms/PEAPnomination. If you are a customer and want your environments to always run on the latest platform, please submit your nomination survey here: http://aka.ms/CAAPnomination.

## I would rather have Microsoft update a different Standard Acceptance test (sandbox) environment than the purchased Tier-2 sandbox. What can I do?

In the opt-out survey, Microsoft will provide a location for you to provide a different sandbox environment ID. Please note that Microsoft will not update the Tier 1 sandbox, which are environments that are deployed as a single virtual machine (VM).

## Can we opt-in to have Microsoft manage additional environments?

For now, the only environment that will be updated is the default Tier 2 Standard Acceptance Environment (Sandbox) environment. We will add a way to allow customers to opt-in additional Tier 2+ environments.

## What if the timeframe being proposed will not work with my schedule? Or if I want a different window for the update?

A link to an opt-out survey is included in the email communications where you can choose a different date. However, you will only be allowed to postpone the update for up to 30 days.

## Are the updates going to be forced monthly or would there be some allowance to delay the updates?

We want customers to stay current. We will allow customers to delay the update for up to 30 days. After that the environment will be updated with the latest release of the platform.

## When should I update my Dev/Build environment?

After Microsoft updates your production environment, apply the update to the rest of your environments (such as additional sandboxes and dev/build environments). You can take the latest platform update package from the ‘Platform Update’ tile on the environment details page in LCS. For additional instructions, please check the [Apply the latest platform update](https://docs.microsoft.com/en us/dynamics365/unified-operations/dev-itpro/migration-upgrade/upgrade-latest-platform-update) topic.

## I need to install a hotfix to my production environment, but my sandbox and production environments are on different platform versions. What process should I follow?

The Platform update package is available to you via Microsoft Lifecycle Services. You will be able to deploy directly to production as a package file. Because you will be applying the package to production, Microsoft will not redeploy the Platform update. You can also apply this package on your dev/build environments. Follow the Update to the latest platform topic to learn how to apply this update to your environment.

## How can I get early access to non-released platform updates?

You can join the Microsoft Continuous Auto-Update Advantage Program (CAAP) where Microsoft will keep your platform always current. If you are interested in learning more and signing up for the program, the nomination survey can be found here: http://aka.ms/CAAPnomination.

## We have seen ISVs being dependent on Platform Updates. How will we ensure that the PU compatible versions are available from all involved ISVs before the PU is applied?

ISVs develop on the minimum required platform release their code depends on. Platform updates to your customer environments will be compatible. Having said that we recommend for the ISVs to be part of our PEAP programs so they can get early access to the platform bits and validate their solutions against the platform before it is made generally available.

## What level of involvement do you foresee for the implementation partners?

We recommend for partners to sign up for the PEAP program so they get early access to the platform bits before they are applied to the customers environments. The only involvement is to ensure that other environments are updated as well. 

## Can partners see the platform update communication before the customer or get an update earlier?

Partners can sign up for the PEAP program to get access to the early access to the platform bits. We also ask that partners be added to the Customers project as a stakeholder or as an interested party in the Notification List. We are looking at publishing a predictable schedule of the updates in the upcoming months.
