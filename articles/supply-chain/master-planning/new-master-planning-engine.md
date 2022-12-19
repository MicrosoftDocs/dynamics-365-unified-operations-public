---
# required metadata

title: Migration to Planning Optimization for master planning
description: This article provides information about the new master planning engine, Planning Optimization, and about migration from the existing engine. 
author: t-benebo
ms.date: 05/11/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 19311
ms.assetid: 5ffb1486-2e08-4cdc-bd34-b47ae795ef0f
ms.search.region: Global
ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2020-11-05
ms.dyn365.ops.version: 

---

# Migration to Planning Optimization for master planning

[!include [banner](../includes/banner.md)]

The built-in master planning engine is obsolete (deprecated). It's being replaced by the Planning Optimization Add-in for Microsoft Dynamics 365 Supply Chain Management. This article provides information about the impact on new and existing deployments. It includes information about required actions.

Planning Optimization enables master planning calculations to occur outside Supply Chain Management and its Azure SQL database. The benefits that are associated with Planning Optimization include improved performance and minimized impact on the SQL database during master planning runs. Because quick planning runs can be done even during office hours, planners can immediately react to demand or parameter changes.

For more information about Planning Optimization, see [Master planning system architecture](master-planning-architecture.md).

## Obsolescence of the existing master planning engine

Microsoft has deprecated the built-in master planning engine obsolete in favor of Planning Optimization. This change affects all cloud environments. On-premises installations aren't affected. 

For more information about the deprecated master planning engine, see the announcements in [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/removed-deprecated-features-scm-updates.md).

## New deployments

Planning Optimization must be considered the default master planning engine for all new deployments in the cloud. In general, Planning Optimization should be used for all new deployments that don't generate planned production orders during master planning. If a new deployment depends on functionality that Planning Optimization doesn't currently support, you can request an exception so that you can continue to use the deprecated master planning engine.

## Existing deployments

Owners of existing cloud-based deployments that depend on master planning should plan to migrate to Planning Optimization. If your implementation depends on functionality that Planning Optimization doesn't currently support, you can request an exception so that you can continue to use the deprecated master planning engine.

## Exception process from release 10.0.32 and onwards

From release 10.0.32 the release process is fully automated and from inside the dynamics application. The system will show you the right instructions depending on your case. The following are the possible cases you could be in and details on each of them.

### Supported customers

When the system detects that the features you are using are supported by Planning Optimization it will ask you to migrate. You will see the following message in the application when you run master planning manually:

_You are supported to use the non-deprecated and faster master planning (Planning Optimization). More information about it on [Get started with Planning Optimization](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/get-started#install-and-enable-planning-optimization)_

_We need you to provide some information regarding master planning. 

Do you have customizations on the master planning engine?_

If you do not have customizations, then you must migrate to Planning Optimization. If you need some time to test and migrate, it will be possible to select some time from the shown dialog and an exception will be automatically applied for the selected time.

If you have customizations, you must move them to the existing extensibility point [Planning Optimization extensibility](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/extensibility)

### Not supported yet customers

If you are not yet supported on Planning Optimization, you will also get a message when running planning manually so that you are made aware that you must move to Planning Optimization once you are supported. 

The action required from you is to evaluate your customizations if you have them to be migrated to the existing extensibility point, or to prepare for the migration, for example, contacting your partner and preparing for the migration.


### Your environment does not support Plannning Optimization

You must be running Supply Chain Management on an LCS enabled high-availability environment, tier 2 or higher (not a OneBox environment), with Dynamics 365 Supply Chain Management version 10.0.7 or later. If you try to install the add-in on a OneBox environment, the installation will not complete and you will need to cancel the installation.

If this is the case, you will be prompted on the screen _You can only run deprecated master plannign in this environment. If you would like to get and enviornment that supports non-deprecated planning (Planning Optimization) please follow the instructions:_ _[Get started with Planning Optimization](https://learn.microsoft.com/en-us/dynamics365/supply-chain/master-planning/planning-optimization/get-started)_

For partners or ISVs it is possible to obtain non-production environments with Biz Apps products and sales plays demo data to learn, test, and deliver end to end customer demos with their own solutions also supporting Planning Optimization for a reduced parice. These offers are only to be used on partner tenants, never on a customer’s tenant. You must request a license to do so on [the Partner sandbox request page](https://experience.dynamics.com/requestlicense/).


## Exception process for releases up to 10.0.31

Owners of existing environments who run the deprecated master planning engine without generating planned production orders will receive an email that provides details about the exception process. We recommend that you work with a partner to evaluate and plan the migration to Planning Optimization.

As has been mentioned, you will receive an error message in version 10.0.16 and later if you run the deprecated master planning engine without generating planned production orders. This error message includes guidance about migration and instructions for requesting an exception.



### Existing deployments

Owners of existing cloud-based deployments that depend on master planning should plan to migrate to Planning Optimization. If your implementation depends on functionality that Planning Optimization doesn't currently support, you can request an exception so that you can continue to use the deprecated master planning engine.

For environments that currently use master planning processes that are being made obsolete, Microsoft will send an email to the environment admin. This email will provide information about the actions that are required to migrate or to request an exception.

## The exception process

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
