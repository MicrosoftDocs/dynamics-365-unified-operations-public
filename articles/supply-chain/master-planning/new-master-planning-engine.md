---
title: Migration to Planning Optimization for master planning
description: This article provides information about the new master planning engine, Planning Optimization, and about migration from the existing engine. 
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 01/02/2023
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

Planning Optimization is the standard master planning engine for all new cloud deployments. It must be used for all new deployments that don't generate planned production orders during master planning. If you are setting up a new deployment that requires functionality that isn't currently supported by Planning Optimization, you can request an exception that will allow you to use the deprecated master planning engine instead.

## Existing deployments

Owners of existing cloud-based deployments that depend on master planning must plan to migrate to Planning Optimization. If your implementation depends on functionality that Planning Optimization doesn't currently support, you must request an exception to continue using the deprecated master planning engine.

## Migration recommendations

There are several differences between the deprecated master planning engine and Planning Optimization.

For distribution companies, the two planning engines provide very similar feature sets. Based on our experience helping other customers to migrate, we recommend that distribution companies enable and test Planning Optimization in UAT and, when testing is successful, enable it on production environment. <!-- KFM: What is "UAT". "User acceptance testing"? Or a type of test system? (sand box?) -->

Manufacturing companies may be affected by some of the minor architectural differences that exist between Planning Optimization and the deprecated planning engine. Based on our experience helping other customers to migrate, we recommend that you proceed as follows in UAT:

1. Create two testing plans, one for Planning Optimization and another for the deprecated planning engine, and use the same settings for both.
1. With the deprecated planning engine enabled, run the plan you created for that engine.
1. Now enable Planning Optimization and run the Planning Optimization plan.
1. For each plan, export the planned orders to an excel file.
1. For the existing plan, sum the planned order quantities for each of several regular time periods (for example, every month).
1. For the Planning Optimization plan, sum the planned order quantities for each of several regular time periods (for example, every month).
1. Compare the quantities for each plan to make sure the result is the same (or very similar). Some variation can be expected for orders that occur at the start or end of a time period
1. If successful, test in UAT.
1. If UAT is successful, then enable Planning Optimization on your production system. <!-- KFM: This wasn't clear. Is this what you mean? IMPORTANT! -->

## Exception process from version 10.0.32 and onwards  <!-- KFM: Is this really an "exception process"?-->

Starting with Supply Chain Management version 10.0.32, the release process <!-- KFM: Clarify "release process". (upgrade process from deprecated engine to Planning Optimization?) --> is fully automated and from inside the dynamics application. The system will show you the right instructions depending on your case. The following are the possible cases you could be in and details on each of them.

### Deployments where Planning Optimization is supported for all required features

If the system detects that all of the relevant features that you are using are supported by Planning Optimization, but you are still running the deprecated planning engine, it will ask you to migrate. The next time you run master planning manually, the system will show the following message <!-- KFM: This message contained a grammar error, and could be improved in other ways, which may need to be corrected in the code. -->:

> You are supported to use the non-deprecated and faster master planning (Planning Optimization). For more information, see [Get started with Planning Optimization](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/get-started#install-and-enable-planning-optimization)
>
> We need you to provide some information regarding master planning.
>
> Do you have customizations on the master planning engine?

If you haven't customized the master planning engine for this deployment, then you must migrate to Planning Optimization. If you need some more time to test and migrate, then select the time you will require and the system will automatically apply an exception for the selected time.

If you do have customizations, you must move them to the existing extensibility point. For more information, see [Planning Optimization extensibility](planning-optimization/extensibility.md).

### Deployments requiring features not yet supported be Planning Optimization

If the system detects that you are using features that aren't supported by Planning Optimization, it will show the following message the next time you run master planning manually:  <!-- KFM: Can we quote the message here? -->

> You are not supported yet to use the non-deprecated master planning (Planning Optimization). We expect to be supporting you in the coming future. When you are supported, you will be asked to move to Planning Optimization. If you have customizations on the master planning engine, you can already start evaluating them and preparing to move them to the Planning Optimization extensibility point https://go.microsoft.com/fwlink/?linkid=2220303


This message lets you know that you should start planning to move to Planning Optimization once it supports the features you are using. Therefore, you should evaluate any customizations you have made to the deprecated planning engine  and plan to move them to the existing extensibility point (see [Planning Optimization extensibility](planning-optimization/extensibility.md), and take other actions to prepare for the migration (for example, by contacting your Microsoft partner or consultant).

See [Planning Optimization fit analysis](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/planning-optimization-fit-analysis) for details about which features are already supported and estimates of up <!-- KFM: continue here... -->

Customers that previously had an exception will be kept until their needed features are supported.

### Environments that don't support Planning Optimization <!-- KFM: How is this different from the previous section? -->

You must be running Supply Chain Management on an LCS enabled high-availability environment, tier 2 or higher (not a OneBox environment), with Dynamics 365 Supply Chain Management version 10.0.7 or later. If you try to install the add-in on a OneBox environment, the installation will not complete and you will need to cancel the installation.

If your environment does not support Planning Optimization, you will see the following message:

> You can only run deprecated master planning in this environment. If you would like to get and environment that supports non-deprecated planning (Planning Optimization) please follow the instructions: [Get started with Planning Optimization](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/get-started) <!-- KFM: This message contained spelling errors, which may need to be corrected in the code. -->

These instructions are indicative, specially for partners and ISVs to bring awareness of Planning Optimization. For partners or ISVs it is possible to obtain non-production environments with Biz Apps products and sales plays demo data to learn, test, and deliver end to end customer demos with their own solutions also supporting Planning Optimization for a reduced price. These offers are only to be used on partner tenants, never on a customer’s tenant. You must request a license to do so on [the Partner sandbox request page](https://experience.dynamics.com/requestlicense/).

## Exception process for releases up to 10.0.31 <!-- KFM: Is this really an "exception process"?-->

For Supply Chain Management version 10.0.31 and earlier, owners of existing environments who run the deprecated master planning engine without generating planned production orders will receive an email that provides details about the exception process. We recommend that you work with a partner to evaluate and plan the migration to Planning Optimization.

As has been mentioned, you will receive an error message in version 10.0.16 and later if you run the deprecated master planning engine without generating planned production orders. This error message includes guidance about migration and instructions for requesting an exception.

### Existing deployments <!-- KFM: What is this heading for? ->

Owners of existing cloud-based deployments that depend on master planning should plan to migrate to Planning Optimization. If your implementation depends on functionality that Planning Optimization doesn't currently support, you can request an exception so that you can continue to use the deprecated master planning engine.

For environments that currently use master planning processes that are being made obsolete, Microsoft will send an email to the environment admin. This email will provide information about the actions that are required to migrate or to request an exception.

### Apply for an exception <!-- KFM: How is this different from the other two exception processes? -->

You can request an exception if you must continue to use the deprecated master planning engine because your business processes depends heavily on at least one feature that isn't currently implemented in Planning Optimization. For a list of available features, see [Planning Optimization fit analysis](planning-optimization/planning-optimization-fit-analysis.md).

Currently, exceptions for Planning Optimization migration are only relevant if your master planning process doesn't include production (that is, planned production orders that are generated by master planning), and you require the deprecated master planning engine beyond version 10.0.15.

After the required features become available, Microsoft will provide a grace period until the exception expires. The environment admin will be informed when the required features have become available and the grace period has started.

The following flowchart summarizes the information provided in this article so you can quickly find out whether you should request an exception. If you do need to request an exception, please fill out and submit the [Planning Optimization migration and exception questionnaire](https://go.microsoft.com/fwlink/?linkid=2144962). The product group is responsible for evaluating and approving each exception request, so please submit your request directly to the product group using the link provided and don't create a support ticket for it. If your request is rejected, please don't create a support ticket because Microsoft Support isn't able to re-evaluate or grant exceptions.

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

**Answer:** You should not be concerned. You can continue to use the deprecated master planning engine in version 10.0.16. However, we recommend that you evaluate whether migration to Planning Optimization can start with the current functionality. We also recommend that you remain informed about new functionality.

### Email from Microsoft

Our environment admin received an email from Microsoft. This email states that we should migrate to Planning Optimization or request an exception. Do I need to take any action?

**Answer:** Yes. Your environment will be affected unless you follow the instructions in the email. You can either migrate to Planning Optimization by the date specified or request an exception by using the link in the email. This link opens a questionnaire. After you've completed and submitted this questionnaire, you will receive a reply via email. Although this process is manual, Microsoft tries to reply within a week after the questionnaire is submitted.

### Error messages

I'm using version 10.0.16 or later, and I receive the following error message when I run master planning. Is master planning blocked?

> You receive this error message because the deprecated master planning engine was used for scenarios supported by Planning Optimization. You should migrate to Planning Optimization now, as the built-in master planning engine has been deprecated. Note that this master planning run did complete successfully.
>
> In case your migration has strong dependencies on pending features, an exception to continued usage of the deprecated master planning engine can be requested.
>
> Please complete the following questionnaire to get started and if relevant request exception from migration to Planning Optimization.

**Answer:** No, master planning isn't blocked. Your master planning run was successfully completed, and you can use the result in the usual way. However, to avoid receiving this error message during future master planning runs, you must either migrate to Planning Optimization immediately or request an exception by using the link in the error message.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
