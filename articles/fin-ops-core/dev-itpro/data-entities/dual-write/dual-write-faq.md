---
# required metadata

title: Dual-write FAQ
description: This topic answers frequently asked questions about dual-write.
author: robinarh
manager: AnnBe
ms.date: 07/21/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-platform
ms.technology:

# optional metadata

# ms.search.form:
# ROBOTS:
audience: Developer
# ms.devlang:
ms.reviewer: rhaertle
# ms.tgt_pltfrm:
ms.custom: 21311
ms.assetid:
ms.search.region: Global
# ms.search.industry:
ms.author: rhaertle
ms.search.validFrom: 2020-07-21
ms.dyn365.ops.version: AX 7.0.0

---

# Dual-write FAQ

[!include [banner](../../includes/banner.md)]

This topic lists frequently asked questions about dual-write and provides brief answers to help you quickly get the information that you require.

## Dual-write setup

### Do you plan to enable dual-write to use Common Data Service as a hub between multiple Finance and Operations environments? If Common Data Service is used as a hub, data can be synced between two or more Finance and Operations environments.

The current plan of record is to restrict dual-write to a one-to-one (1:1) mapping between a single Finance and Operations environment and a single Common Data Service environment.

### Can I control the sequencing of maps in dual-write, as I can in Data integrator?

Dual-write is transaction-based. For example, if a change in a Finance and Operations app triggers synchronization of multiple maps with Common Data Service, by default, those changes will be sequenced in the order in which they are updated in the database. This pattern makes more sense in the context of initial synchronization. The system provides related entity maps in a specified order, and you can reorder the list so that it best suits your environment.

### Do application users require any special permissions to enable or configure dual-write?

You must have two Azure Active Directory (Azure AD) applications set up for the Finance and Operations environment and two application users set up in the Common Data Service environment. These application users should contain the appropriate application IDs. For the connection to work properly, you must give the applications the relevant entity permissions by using a security role. For more information, see [Verify requirements and grant access](requirements-and-prerequisites.md#verify-requirements-and-grant-access).

End users who are configuring dual-write mappings should have System Administrator security roles assigned in both Common Data Service and Finance and Operations environments. 

### I have multiple legal entities. Some of my maps are legal entity–specific or valid for only some of the legal entities. What is the best way to address this requirement? Can I apply a filter such as Company = USMF to address it?

Legal entity mapping can be done when the Common Data Service environment is linked. You can't map entity maps to a specific legal entity.

### If dual-write solutions are installed in Common Data Service, can I uninstall them?

Dual-write solutions are managed solutions that can be uninstalled. However, when a managed solution is uninstalled, all components in the solution are deleted. Any data that is stored in the components is also deleted. For more information, see [Maintain managed solutions](https://docs.microsoft.com/powerapps/developer/common-data-service/maintain-managed-solutions).

### I have data in both a customer engagement app and a Finance and Operations app, and I bootstrap my existing data in the customer engagement app. If my data isn't currently aligned, can I specify a master source for the initialization run, so that all differences are applied to the target?

After the bootstrapping is done, you can configure the initial synchronization to apply differences and select a master. For more information about bootstrapping, see [Bootstrap with company data FAQ](bootstrap-company-data.md). For more information about the initial synchronization, see [Enable entity maps for dual-write](enable-entity-map.md).

## Dual-write administration and management

### What is the purpose of the integration key, and is it mandatory?

The integration key is the natural key that uniquely identifies records. Integration keys are required only for Common Data Service entities. You can manually create an integration key in dual-write. An integration key can also be automatically created from the entity's alternate keys, if an alternate key is already provided for the entity. Integration keys are used for the same purpose as alternate keys: they provide an efficient and accurate way to integrate data with external systems. Integration keys are essential in cases where an external system doesn't store the globally unique identifiers (GUIDs) that uniquely identify records in Common Data Service.

Dual-write uses integration keys to uniquely identify records, by using one or more entity field values that represent a unique combination. For example, to identify an account record by using an integration key, you can use the account number field. Alternatively, you can use the account number field together with other fields that have values that should not change. For more information, see [Define alternate keys using Power Apps portal](https://docs.microsoft.com/powerapps/maker/common-data-service/define-alternate-keys-portal.md).

It's important that keys be matched between the Finance and Operations environment and the Common Data Service environment. Otherwise, issues might occur during the initial synchronization phase.

### How do I move entity maps between environments? Is version control supported for entity maps?

You can export maps and then import them into a different environment. You can automate the process by using Azure DevOps. You can have version control on your dual-write mappings, because the mappings are solution-aware components. For more information, see [Update entity maps and export them to other environments as a solution](app-lifecycle-management.md#update-entity-maps-and-export-them-to-other-environments-as-a-solution).

### Where can I find examples and patterns for filtering dual-write maps?

For basic filtering examples, see [Filter your data](customizing-mappings.md#filter-your-data).

For more advanced examples for Common Data Service, see [Filter results](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/query-data-web-api#filter-results). Nested lookup isn't supported in dual-write source filters. Only [standard filter operators](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/query-data-web-api#standard-filter-operators) directly against entity fields are supported.

For more advanced Finance and Operations filters, see [Using Expressions in Query Ranges](https://docs.microsoft.com/dynamicsax-2012/developer/using-expressions-in-query-ranges) and [Advanced filtering and query syntax](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/advanced-filtering-query-options).

### Dual-write live synchronization introduces tight coupling across applications. What happens if one side fails? Will the other side fail too?

When the integration is in live sync mode, if the sync fails on one of the apps, then the other app will fail as well and users will receive an error. When the integration is paused, changes are staged. They are then written when the target system is up and running. For more information about how to automatically pause integrations, see [Alert notifications](errors-and-alerts.md#alert-notifications)

### When live synchronization is paused and then resumed, does it follow the sequence of changes? For example, if the Name field in the Finance and Operations app is changed from NameA to NameB to NameC, is customer engagement data changed from NameA to NameB to NameC, or is it changed directly from NameA to NameC?

The integration follows the complete sequence of changes. In the example, the customer engagement app data is changed from **NameA** to **NameB** to **NameC**.

### How do I handle a Finance and Operations database transfer from PROD to STAGE? What is the effect on dual-write? After the transfer, the systems are no longer in sync. Is the synchronization done automatically?

Each linked environment-pair (Finance and Operations apps environment and Common Data Service environment) should be treated as a single unit and refreshed accordingly. For example, if you are refreshing a sandbox from production, then both Finance and Operations app sandbox environment and the Common Data Service sandbox environment should be refreshed from their production counterparts. If dual-write is already used in target environments, those environments need to be unlinked. After the data refresh on target environments, these tables should be cleaned up:

+ Finance and Operations apps tables: **DualWriteProjectConfiguration**, **DualWriteProjectFieldConfiguration**, and **BusinessEventsDefinition**. 
+ Common Data Service entities: **DualwriteRuntimeConfiguration**. 
    
The environments need to be relinked and maps reactivated manually.

### I need real-time integration, and I want to move some entities or scenarios from Data integrator to dual-write. How do I migrate, and what are the implications of changing my integration pattern? 

For information about how to migrate Prospect to cash to dual-write, see [Migrating data from Data Integrator to Dual Write](https://www.yammer.com/dynamicsaxfeedbackprograms/#/files/433337729024). In general, three things might change during migration:

+ Manual migration of the maps from Data integrator to dual-write
+ Entity changes, because of the absence of advanced query capabilities
+ Data migration, because of adaptation to new concepts such as company striping

### On Finance and Operations data entities, can I develop unbounded fields that flow to Common Data Service by using dual-write?

Yes. You can use both [computed fields and virtual fields](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/data-entity-computed-columns-virtual-fields). However, you should monitor the performance overhead from the additional X++ logic that is required for reads and writes. Round-tripping within the same transaction isn't allowed. Therefore, you should avoid using virtual fields to transform or calculate additional values through X++ and expect that to go back to Common Data Service within the same transaction.

### When I use the Common Data Service offline app, what happens if I can't sync the data after reconnection? Does this situation cause an inconsistent state between the Common Data Service environment and the Finance and Operations environment?

You can interact with Common Data Service data offline when using the [Dynamics 365 for phones app](https://docs.microsoft.com/dynamics365/mobile-app/install-dynamics-365-for-phones-and-tablets) or the [Field Service Mobile app](https://docs.microsoft.com/dynamics365/field-service/field-service-mobile-overview) in offline mode. In both apps, data is stored offline and can be synced with the server at your discretion. If there are errors when the offline data is synced with the server, and updates can't be done because the other environment is failing, data sync will fail, and Common Data Service will not be updated. When the integration is paused, you can re-run the sync and save your updates on the server. These changes will be staged and then synced with the Finance and Operations environment when the mapping is up and running again. 

## Mapping concepts between apps

### How are number sequences handled? For example, the customer account number is automatically generated in Finance and Operations apps, but it's added manually in customer engagement apps.

Number sequences for Finance and Operations apps and customer engagement apps aren't connected. In a scenario that involves a multi-mastered entity, you must either plan for separate number sequence formats or create a range for each app. Here are some examples:

+ In the Finance and Operations app, use **F0001, F0002, F0003**. In the customer engagement app, use **C0001, C0002, C0003**.
+ In the Finance and Operations app, use **US0001 to US4999**. In the customer engagement app, use **US5000 to US9999**.

If an entity is created in only one system, set up the number sequence in the source app only. For more information, see [Autonumber fields](https://docs.microsoft.com/powerapps/maker/common-data-service/autonumber-fields).

### Can I map a company-specific entity in a customer engagement app with a global entity in a Finance and Operations app, or a global entity in a customer engagement app with a company-specific entity in a Finance and Operations app?

Dual-write supports mappings only between cross-company entities or company-specific entities from both sides.

### How do I make a company-specific entity in Common Data Service?

You can make Common Data Service custom entities company-specific by adding a many-to-one (N:1) relationship between your custom entities and the out-of-box company entity. You should also include the company foreign key as part of the entity key. For more information, see [Company concept in Common Data Service](company-data.md).

To enable entity maps for dual-write, you must define an alternate key in Common Data Service. The value of the alternative key in Common Data Service must match the key that is defined in the Finance and Operations app. For more information, see [Criteria for linking entities](enable-entity-map.md#criteria-for-linking-entities).

### Is there a document about best practices for entity usage? Should I use Customers V2, Customers V3, or Customer Details? What is the difference between these entities, and what is the use case for each?

You should use the [out-of-box scenarios](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/customer-mapping) if you can, because they cover common scenarios such as customer/vendor integration.
