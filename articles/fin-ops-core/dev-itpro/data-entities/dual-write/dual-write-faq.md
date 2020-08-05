---
# required metadata

title: Dual-write frequently asked questions
description: This topic answers frequently asked questions.
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
ms.search.scope: Operations
# ms.tgt_pltfrm:
ms.custom: 21311
ms.assetid:
ms.search.region: Global
# ms.search.industry:
ms.author: rhaertle
ms.search.validFrom: 2020-07-21
ms.dyn365.ops.version: AX 7.0.0

---

# Dual-write frequently asked questions

[!include [banner](../../includes/banner.md)]

We've compiled a list of frequently asked questions and provided brief answers to help you get to your information quickly.

## Dual-write setup

### Is dual-write available for Government Community Cloud (GCC)?

Dual-write isn't supported in GCC cloud yet. It will be made available once Finance & Operations goes live in GCC cloud. For more information, see [Microsoft Power Apps US Government](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-us-government).

### If I don't have a license for Dynamics 365 Sales or Dynamics 365 Field Service, but I want to have the sales order data in Common Data Service, can I do it without buying a license?

If you have a valid Finance and Operations app license, you can enable dual-write between the Common Data Service and the Finance and Operations app. The license does not include capacity consumed by the replicated data. If you need additional capacity, you must purchase it separately. The license does not include use rights for the customer engagement apps, for example, Dynamics 365 Sales and Dynamics 365 Marketing. You must purchase those licenses separately.

### Do you plan to let dual-write use Common Data Service as a hub between multiple Finance and Operations environments? That would allow synchronizing data between two or more Finance and Operations environments.

The current plan of record is to restrict this to a 1:1 mapping between a single Finance and Operation environment and a single Common Data Service environment.

### Can you control the sequencing of maps in dual-write, like in data integrator?

Dual-write is transaction-based. For example, if a change in a Finance and Operations app triggers multiple maps to sync with Common Data Service, then these will be in sequenced by default as they are updated in the database.
This makes more sense in the context of initial sync. Tne system provides related entity map in a specified order and you can reorder the list to best suit to your environment.

### Do application users need to have any special permissions to enable or configure dual-write?

Dual-write setup requires two Azure Active Directory (AD) applications setup for the Finance and Operations environment and two app application users need to be setup in Common Data Service environments. These application users should contain the appropriate application IDs. For the connection to work properly, you need to give these application the relevant entity permissions by using a security role. For more information, see [Verify requirements and grant access](requirements-and-prerequisites#verify-requirements-and-grant-access).

### I have multiple legal entities and some of my maps are specific per legal entity, or they are valid for only some of the legal entities. What is the best way to address this requirement? Can we apply a filter, for example, **Company = USMF** to address this?

Legal entity mapping can be done when linking the Common Data Service environment. It is not possible to map entity maps to a specific legal entity.

### Can we use both data integrator and dual-write at the same? If yes, does it cause any referential integrity issues?

You can't run dual-write and the [Prospect to cash solution](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/sales-marketing/accounts-template-mapping-direct) for Data integrator side by side. If you're running the Prospect to cash solution for Data integrator, you must uninstall it before setting up dual-write. We suggest adopting one of the two patterns anytime. We recommend using dual-write as integration pattern.

### If dual-write solutions are installed in Common Data Service, can I uninstall them?

Dual-write solutions are managed solutions which can be uninstalled. However keep in mind that when a managed solution is uninstalled all components in the solution including data that is stored in these components get deleted. For more information see [Maintain managed solutions](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/maintain-managed-solutions).

### Suppose that we have data in both a customer engagement app and a Finance and Operations app, and we bootstrap our existing data in the customer engagement app. If our data is not currently aligned, can we specify a master source for the initialization run so that all differences are applied to the target?

After the bootstrapping is done, you can configure the initial sync to apply differences and chose a master. For more information, see [Bootstrap with company data FAQ](bootstrap-company-data.md) for bootstrapping and [Enable entity maps for dual-write](enable-entity-map.md) for the initial sync.

## Dual-write administration and management

### What is the purpose of the integration key and is it mandatory?

The integration key is the natural key which uniquely identifies records. Integration keys are only required for Common Data Service entities, and you can manually created one within dual-write. It can also be automatically created from the entity's alternate keys, if one is already provided for an entity. Integration keys are used for the same purpose of alternate keys, to provide an efficient and accurate way of integrating data with external systems. It’s essential in cases when an external system doesn’t store the Globally Unique Identifier (GUID) IDs that uniquely identify records in Common Data Service.

Dual-write uses integration keys to uniquely identify records using one or more entity field values that represent a unique combination. For example, to identify an account record with an integration key, you can use the account number or the account number field in combination with some other fields which have values that should not change. For more information, see [Define alternate keys using Power Apps portal](https://docs.microsoft.com/powerapps/maker/common-data-service/define-alternate-keys-portal.md).

It is important to ensure keys are matched on Finance and Operations and Common Data Service environments, otherwise it might cause problems in the initial sync phase.

### How do I move entity maps between environments? Is version control supported for entity maps?

You can export maps and imported them into a different environment. You can automate the process by using DevOps. For more information, see [Update entity maps and export them to other environments as a solution](app-lifecycle-management.md#update-entity-maps-and-export-them-to-other-environments-as-a-solution).

### Where can I find example and patterns for filtering dual-write maps?

You can find basic filtering examples in [Filter your data](customizing-mappings.md#filter-your-data).

You can find more advanced examples for Common Data Service in [Filter results](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/query-data-web-api#filter-results). Nested lookup is not supported in dual-write source filter. Only [standard filter operators](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/query-data-web-api#standard-filter-operators) directly against entity fields are supported.

More advanced Finance and Operations filters can be found using [Using Expressions in Query Ranges](https://docs.microsoft.com/dynamicsax-2012/developer/using-expressions-in-query-ranges) & [Advanced filtering and query syntax](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/advanced-filtering-query-options).

### Dual-write live sync introduces tight coupling across applications. What happens if one side fails? Will the other side fail, too?

When integration is in live sync mode, you will see an error and if one app fails, the other app will fail too. When integration is paused, changes are staged and are written once the target system is up and running. For more information about automatically pausing integrations see [Alert notifications](errors-and-alerts.md#alert-notifications)

### When live sync is paused and then resumed, does it follow the sequence of changes? For example, if the **Name** field changes in the Finance and Operations app from **NameA** to **NameB** to **NameC**, does the customer engagement data change from **NameA** to **NameB** to **NameC**, or **NameA** to **NameC**?

The integration follows the complete sequence of changes. In the above example, the customer engagement app data would change from **NameA** to **NameB** to **NameC**.

### How does dual-write work after a Disaster Recovery event? Does it automatically work with the secondary instance that deployed on the secondary Azure region?

In a failover event, dual-Write continues working after the failover transition finishes, if both the Finance and Operations environment and Common Data Service environment are accessible. Finance and Operations environments and Common Data Service environments adhere to the standard failover process. For more information about system availability, see [Cloud deployment overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/cloud-deployment-overview#availability).

### How we handle a Finance and Operations database transfer from PROD to STAGE? What is the effect on dual-write? After the transfer, the systems are not in sync anymore. Is the sync done automatically?

The transfer is a manual process of unlinking and linking the refreshed environments. Dual-write does not have APIs for these steps, otherwise this could automated in LCS by using LCS APIs and dual-write APIs.

### We need real-time integration and want to move some entities or scenarios from Data integrator to dual-write. How do we migrate and what are the implications of changing our integration pattern? 

For information on migrating Prospect to Cash to dual-write, see [Migrating data from Data Integrator to Dual Write](https://www.yammer.com/dynamicsaxfeedbackprograms/#/files/433337729024). In general, there are three things that might change during migration.

+ Manually migrating the maps from Data integrator to dual-write.
+ Entity changes, due to absence of advanced query capabilities.
+ Data migration, due to adapting to new concepts such as company striping.

### Can I develop unbounded fields on Finance and Operations data entities that flow to Common Data Service by using dual-write?

Yes. You can use both [computed and virtual fields](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/data-entity-computed-columns-virtual-fields), but you should monitor the performance overhead from the additional X++ logic required for reads and write. Round-tripping within the same transaction is not allowed, so avoid using virtual fields to transform or calculate additional values through X++. You should expect that to go back to Common Data Service within the same transaction.

### With the Common Data Service offline app, what if it is not possible to sync the data after reconnecting? Would that lead to an inconsistent state between the Common Data Service environment and the Finance and Operations environment?

You can access Common Data Service data offline by using Common Data Service applications by using the Field Service mobile app. In both cases, data is stored offline, and it can be synced with the server at your direction. If there are errors when the offline data is synced with the server, and updates cannot be performed because the other environment is failing, then you can handle the error by using conflict management settings. For more details about different conflict management settings, see [Common Data Service conflict management settings](https://docs.microsoft.com/en-us/dynamics365/mobile-app/setup-mobile-offline-for-admin#step-23-set-conflict-detection-for-mobile-offline) and [Resco conflict resolution settings](https://docs.resco.net/wiki/Conflict_resolution).

## Mapping concepts between apps

### How are number sequences handled? For example, the customer account number in Finance and Operations apps is autogenerated and in customer engagement apps it's manual.

Number sequences for Finance and Operations apps and customer engagement apps are not connected. In a multi-mastered entity scenario, you must plan for separate number sequence formats or create a range per app. Here are some examples:

+ In the Finance and Operations app, use **F0001, F0002, ...**. In the customer engagement app, use **C0001, C0002, ...**.
+ In the Finance and Operations app, use **US0001 to US4999**. In the customer engagement app, use **US5000 to US9999**.

If entity is created in only one system, then set up the number sequence in only the source app. For more details, see [Autonumber fields](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/autonumber-fields).

### Can we map company-specific entity in a customer engagement app with a global entity in a Finance and Operations app, or vice-versa?

Dual-write supports only mapping between cross-company entities or company-specific entities from both sides.

### How do I make an company-specific entity in Common Data Service?

Common Data Service custom entities can be made company specific by adding a M-1 relationship between your custom entities and the out-of-the-box standard company entity. You should also include the company foreign key as part of the entity key. For more information, see [Company concept in Common Data Service](company-data.md)

### Is there a document on best practices for entity usage? Should I use Customers V2, Customers V3, Customer Details? What is the difference and use case for each?

You should use the [out-of-the-box scenarios](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/customer-mapping) if possible, because they cover common scenarios like customer/vendor integration.
