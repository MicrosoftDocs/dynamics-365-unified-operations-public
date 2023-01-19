---
title: Migration to Planning Optimization for master planning
description: This article provides information about the new master planning engine, Planning Optimization, and about migration from the existing engine. 
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 01/30/2023
ms.custom: bap-template
audience: Application User
---

# Migration to Planning Optimization for master planning

[!include [banner](../includes/banner.md)]

The built-in master planning engine is obsolete (deprecated). It's being replaced by the Planning Optimization Add-in for Microsoft Dynamics 365 Supply Chain Management. This article provides information about the impact on new and existing deployments. It includes information about required actions.

Planning Optimization enables master planning calculations to occur outside Supply Chain Management and its Azure SQL database. The benefits that are associated with Planning Optimization include improved performance and minimized impact on the SQL database during master planning runs. Because quick planning runs can be done even during office hours, planners can immediately react to demand or parameter changes.

For more information about Planning Optimization, see [Master planning system architecture](master-planning-architecture.md).

## Obsolescence of the existing master planning engine

Microsoft has deprecated the built-in master planning engine in favor of Planning Optimization. This change affects all cloud environments. On-premises installations aren't affected.

For more information about the deprecated master planning engine, see the announcements in [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md).

## New deployments

Planning Optimization is the standard master planning engine for all new cloud deployments. It must be used for all new deployments that don't generate planned production orders during master planning. If you're setting up a new deployment that requires functionality that isn't currently supported by Planning Optimization, you can request an exception that will allow you to use the deprecated master planning engine instead.

## Existing deployments

Owners of existing cloud-based deployments that depend on master planning must plan to migrate to Planning Optimization. If your implementation depends on functionality that Planning Optimization doesn't currently support, you must request an exception to continue using the deprecated master planning engine.

## Migration recommendations

There are several differences between the deprecated master planning engine and Planning Optimization.

For distribution companies, the two planning engines provide very similar feature sets. Based on our experience helping other customers to migrate, we recommend that distribution companies enable and test Planning Optimization in a test environment and, when testing is successful, enable it on production environment.

Manufacturing companies may be affected by some of the minor architectural differences that exist between Planning Optimization and the deprecated planning engine. Based on our experience helping other customers to migrate, we recommend that you set up a test environment and proceed as follows:

1. Create two testing plans, one for Planning Optimization and another for the deprecated planning engine, and use the same settings for both.
1. With the deprecated planning engine enabled, run the plan you created for that engine.
1. Now enable Planning Optimization and run the Planning Optimization plan.
1. For each plan, export the planned orders to an excel file.
1. For the existing plan, sum the planned order quantities for each of several regular time periods (for example, every month).
1. For the Planning Optimization plan, sum the planned order quantities for each of several regular time periods (for example, every month).
1. Compare the quantities for each plan to make sure the result is the same (or very similar). Some variation can be expected for orders that occur at the start or end of a time period
1. If your test is successful, continue testing on the test environment.
1. If all of your tests are successful, then enable Planning Optimization on your production system.

## Exception process for version 10.0.32 and newer

Starting with Supply Chain Management version 10.0.32, the process of evaluating your system and moving to Planning Optimization is fully automated. The system will analyze your setup and automatically show you the right instructions based on your situation. The following subsections describe the possible cases and provide details about each of them.

### Deployments where Planning Optimization is supported for all required features

If the system detects that all of the relevant features that you're using are supported by Planning Optimization, but you're still running the deprecated planning engine, it will ask you to migrate. The next time you run master planning manually, the system will show the following message:

> You are supported to use the non-deprecated and faster master planning (Planning Optimization). For more information, see [Get started with master planning](planning-optimization/get-started.md#install-enable-po)
>
> We need you to provide some information regarding master planning.
>
> Do you have customizations on the master planning engine?

If you haven't customized the master planning engine for this deployment, then you must migrate to Planning Optimization. If you need some more time to test and migrate, then select the time you'll require and the system will automatically apply an exception for the selected time.

If you do have customizations, you must move them to the existing extensibility point. For more information, see [Planning Optimization extensibility](planning-optimization/extensibility.md).

### Deployments requiring features not yet supported be Planning Optimization

If the system detects that you're using features that aren't supported by Planning Optimization, it will show the following message the next time you run master planning manually:

> You are not supported yet to use the non-deprecated master planning (Planning Optimization). We expect to be supporting you in the coming future. When you are supported, you will be asked to move to Planning Optimization. If you have customizations on the master planning engine, you can already start evaluating them and preparing to move them to the Planning Optimization extensibility point https://go.microsoft.com/fwlink/?linkid=2220303

This message lets you know that you should start planning to move to Planning Optimization once it supports the features you're using. Therefore, you should evaluate any customizations you have made to the deprecated planning engine, plan to move them to the existing extensibility point (see [Planning Optimization extensibility](planning-optimization/extensibility.md), and take other actions to prepare for the migration (for example, by contacting your Microsoft partner or consultant).

See [Planning Optimization fit analysis](planning-optimization/planning-optimization-fit-analysis.md) for details about which features are already supported and estimates of when each feature will become available for Planning Optimization.

If you've already received an exception, then that exception will remain in place until the features you need are supported by Planning Optimization.

### <a name="unsupported-environments"></a>Environments that don't support Planning Optimization

Regardless of which features you're using, to use Planning Optimization, you must be running Supply Chain Management version 10.0.7 or later on an LCS enabled high-availability environment, tier 2 or higher (not a OneBox environment). If you try to install the add-in on a OneBox environment, the installation won't complete and you'll need to cancel the installation.

If your environment doesn't support Planning Optimization, you'll see the following message:

> You can only run deprecated master planning in this environment. If you would like to get an environment that supports non-deprecated planning (Planning Optimization) please follow the instructions: [Get started with master planning](planning-optimization/get-started.md)

If you are a Microsoft partner or independent software vendor (ISVs), then you can obtain a non-production environment at a reduced price that supports Planning Optimization and includes Microsoft business applications and demo data. These environments are only available to Partners and ISVs, and will enable you to learn how Planning Optimization works, test your solutions while using it, and deliver end-to-end customer demos. These environments can only be used on partner tenants, never on customer tenants. To request a license go to the [partner sandbox request page](https://experience.dynamics.com/requestlicense/).

## Exception process for version 10.0.31 and earlier

For Supply Chain Management version 10.0.31 and earlier, owners of existing environments who run the deprecated master planning engine without generating planned production orders will receive an email that provides details about the exception process. The system may also show an error message that includes guidance about migration and instructions for requesting an exception. If you receive such a message and/or email, we recommend that you work with a partner to evaluate and plan the migration to Planning Optimization.

If your implementation depends on functionality that Planning Optimization doesn't currently support, you can request an exception that will allow you to continue to use the deprecated master planning engine. (For a list of available features, see [Planning Optimization fit analysis](planning-optimization/planning-optimization-fit-analysis.md).) For environments that currently use master planning processes that are being made obsolete, Microsoft will send an email to the environment admin. This email will provide information about the actions that are required to migrate or to request an exception.

Currently, exceptions for Planning Optimization migration are only relevant if your master planning process doesn't include production (that is, planned production orders that are generated by master planning), and you require the deprecated master planning engine beyond Supply Chain Management version 10.0.15.

After the required features become available, Microsoft will provide a grace period until the exception expires. The environment admin will be informed when the required features have become available and the grace period has started.

The following flowchart summarizes the information provided in this article so you can quickly find out whether you should request an exception. If you do need to request an exception, please fill out and submit the [Planning Optimization migration and exception questionnaire](https://go.microsoft.com/fwlink/?linkid=2144962). The product group is responsible for evaluating and approving each exception request, so please submit your request directly to the product group using the link provided and don't create a support ticket for it. If your request is rejected, please don't create a support ticket because Microsoft Support isn't able to reevaluate or grant exceptions.

![Exception flowchart.](media/exception-diagram.png "Exception flowchart")

> [!NOTE]
> You can only request an exception for tenants that currently include, or will include, a production environment, not for tenants with sandbox environments only. If you need to disable the Planning Optimization exception error on an infrastructure as a service (IaaS) sandbox environment, run the SQL query provided in [Sandbox environments](#faq-sandbox).

## Frequently asked questions

### <a name="faq-sandbox"></a>Sandbox environments

Can I use the deprecated master planning engine on my sandbox environment? Do I need an exception?

**Answer:** Exceptions aren't normally relevant for sandbox environments because the Planning Optimization exception error doesn't prevent the deprecated master planning engine from running successfully. However, if the error message disturbs you, you can disable it on an IaaS (not Service Fabric) sandbox environment by running the following query on your database:

```sql
-- Insert or update an enabled flight:
DECLARE @flightName NVARCHAR(100) = 'ReqPlanningOptimizationExceptionToggle';
IF NOT EXISTS (SELECT TOP 1 1 FROM SysFlighting WHERE flightName = @flightName)
    INSERT INTO SYSFLIGHTING(FLIGHTNAME,ENABLED, FLIGHTSERVICEID,PARTITION)
    SELECT @flightName, 1, 12719367,RECID FROM DBO.[PARTITIONS];
ELSE
    UPDATE SysFlighting SET enabled = 1, flightServiceId = 12719367 WHERE flightName = @flightName;
```

### On-premises environments

My environment is on-premises. Do I need an exception?

**Answer:** No. An exception isn't required for on-premises environments. You can continue to use the deprecated master planning engine. Your environment admin will be informed if any action is required.

### Production scenarios

We use planned production orders, but I'm concerned about what will happen when we upgrade to version 10.0.16. Should I take any action?

**Answer:** You shouldn't be concerned. You can continue to use the deprecated master planning engine in version 10.0.16. However, we recommend that you evaluate whether migration to Planning Optimization can start with the current functionality. We also recommend that you remain informed about new functionality.

### Email from Microsoft

Our environment admin received an email from Microsoft. This email states that we should migrate to Planning Optimization or request an exception. Do I need to take any action?

**Answer:** Yes. Your environment will be affected unless you follow the instructions in the email. You can either migrate to Planning Optimization by the date specified or request an exception by using the link in the email. This link opens a questionnaire. After you've completed and submitted this questionnaire, you'll receive a reply via email. Although this process is manual, Microsoft tries to reply within a week after the questionnaire is submitted.

### Error messages

I'm using version 10.0.16 or later, and I receive the following error message when I run master planning. Is master planning blocked?

> You receive this error message because the deprecated master planning engine was used for scenarios supported by Planning Optimization. You should migrate to Planning Optimization now, as the built-in master planning engine has been deprecated. Note that this master planning run did complete successfully.
>
> In case your migration has strong dependencies on pending features, an exception to continued usage of the deprecated master planning engine can be requested.
>
> Please complete the following questionnaire to get started and if relevant request exception from migration to Planning Optimization.

**Answer:** No, master planning isn't blocked. Your master planning run was successfully completed, and you can use the result in the usual way. However, to avoid receiving this error message during future master planning runs, you must either migrate to Planning Optimization immediately or request an exception by using the link in the error message.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
