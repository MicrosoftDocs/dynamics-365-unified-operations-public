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

Not yet. Dual-write requires that the Finance and Operations apps environment and and the Common Data Service environment be in the same tenant. That is, dual-write doesn’t support linking a Finance and Operations apps and Common Data Service across two different tenants. Because Finance and Operations apps are not available in GCC, you can't have both environments in GCC. For more information, see [Microsoft Power Apps US Government](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-us-government).

### If I don't have a license for Dynamics 365 Sales or Dynamics 365 Field Service, but I want to have the sales order data in Common Data Service, can I do it without buying a license?

If you have a valid Finance and Operations app license, you can enable dual-write between the Common Data Service and the Finance and Operations app. The license does not include capacity consumed by the replicated data. If you need additional capacity, you must purchase it separately. The license does not include use rights for the customer engagement apps, for example, Dynamics 365 Sales and Dynamics 365 Marketing. You must purchase those licenses separately.

### Do you plan to let dual-write use Common Data Service as a hub between multiple Finance and Operations environments? That would allow synchronizing data between two or more Finance and Operations environments.

The current plan of record is to restrict this to a 1:1 mapping between a single Finance and Operation environment and a single Common Data Service environment.

### Can you control the sequencing of maps in dual-write, like in data integrator?

Dual-write is transaction-based. For example, if a change in a Finance and Operations app triggers multiple maps to sync with Common Data Service, then these will be in sequenced by default as they are updated in the database.
This makes more sense in the context of initial sync. Tne system provides related entity map in a specified order and you can reorder the list to best suit to your environment.

### Do application users need to have any special permissions to enable or configure dual-write?

Dual-write setup requires 2 Azure AD applications setups in for the Finance and Operations app and that application users are setup in Common Data Service. These application users should contain the appropriate application IDs. For the connection to work properly, you need to give these application the relevant entity permissions by using a security role. For more information, see [Verify requirements and grant access](requirements-and-prerequisites#verify-requirements-and-grant-access).

### I have multiple legal entities and some of my maps are specific per legal entity, or they are valid for only some of the legal entities. What is the best way to address this requirement? Can we apply a filter, for example, **Company = USMF** to address this?

It is not possible to map entity maps applicable to specific legal entity. Legal entity mapping can be done when the linking Common Data Service environment.

### Can we use both data integrator and dual-write at the same? If yes, does it cause any referential integrity issues?

You can't run dual-write and the [Prospect to cash solution](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/sales-marketing/accounts-template-mapping-direct) for Data integrator side by side. If you're running the Prospect to cash solution for Data integrator, you must uninstall it before setting up dual-write. We suggest adopting one of the two patterns anytime. We recommend using dual-write as integration pattern.

### If dual-write solutions are installed in Common Data Service, can I uninstall them?

These are managed solutions. Uninstalling and reinstalling a managed solution is practically never an option when the solution contains entities or attributes. This is because data is lost when entities are deleted. For more information see [Maintain managed solutions](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/maintain-managed-solutions).

### Suppose that we have data in both a customer engagement app and a Finance and Operations app, and we bootstrap our existing data in the customer engagement app. If our data is not currently aligned, can we specify a master source for the initialization run so that all differences are applied to the target?

After the bootstrapping is done, you can configure the initial sync to apply differences and chose a master. For more information, see [Bootstrap with company data FAQ](bootstrap-company-data.md) for bootstrapping and [Enable entity maps for dual-write](enable-entity-map.md) for the initial sync.

## Dual-write administration and management

### What is the purpose of the integration key and is it mandatory?

The integration key is the natural key which uniquely identifies records. Integration keys are only required for Common Data Service entities, and you can manually created one within dual-write. It can also be automatically created from the entity's alternate keys, if one is already provided for an entity. Integration keys are used for the same purpose of alternate keys, to provide an efficient and accurate way of integrating data with external systems. It’s essential in cases when an external system doesn’t store the Globally Unique Identifier (GUID) IDs that uniquely identify records in Common Data Service.

Dual-write uses integration keys to uniquely identify records using one or more entity field values that represent a unique combination. For example, to identify an account record with an integration key, you can use the account number or the account number field in combination with some other fields which have values that should not change. For more information, see [Define alternate keys using Power Apps portal](https://docs.microsoft.com/powerapps/maker/common-data-service/define-alternate-keys-portal.md).

### How do I move entity maps between environments? Is version control supported for entity maps?

You can export maps and imported them into a different environment. You can automate the process by using DevOps. For more information, see [Update entity maps and export them to other environments as a solution](app-lifecycle-management.md#update-entity-maps-and-export-them-to-other-environments-as-a-solution).

### Where can I find example and patterns for filtering dual-write maps?

You can find basic filtering examples in [Filter your data](customizing-mappings.md#filter-your-data).

You can find more advanced examples for Common Data Service in [Filter results](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/query-data-web-api#filter-results). Nested lookup is not supported in dual-write source filter. Only [standard filter operators](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/query-data-web-api#standard-filter-operators) directly against entity fields are supported.

More advanced Finance and Operations filters can be found using [Using Expressions in Query Ranges](https://docs.microsoft.com/en-us/dynamicsax-2012/developer/using-expressions-in-query-ranges) & [Advanced filtering and query syntax](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/advanced-filtering-query-options).

### With Dual write live sync introducing tight coupling across Dynamics applications. What is the impact to user experience of one side fails, will the other side fail too?

When integration is in live sync mode, user will see error and if one side fails and other side will fail. When integration is paused, changes will be staged and will be written once the target system is up and running. You can find more details about automatically pausing integrations [here](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/errors-and-alerts#alert-notifications)

### When data flow is paused and then resumed, does it follow the sequence of changes? E.g. customer name changes in Finance and Operations from A to B, and then to C. Will CE show all changes, or will it just show A to C?

It follows sequence of changes. In the above example  changes A,B,C will be synched in sequence

### How does Dual-write work after a Disaster Recovery event? Does it automatically work with the secondary instance that deployed on the secondary azure region?

In case of a failover event, Dual-Write solution will continue working as it is once the failover transition is completed.
After failover transition is completed, Dual write solution will continue to work as it is, as long as both Finance and Operations apps environment and Common Data Service environment are accessible. Finance and Operations apps environment and Common Data Service environment will adhere to standard failover process.
You can find the documentation around system availability [here](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/cloud-deployment-overview#availability).

### How do you deal with a Finance and Operations apps database transfer from PROD to STAGE? What will be the effect from dual write point of view? After this process, the systems are not in sync anymore. Is the sync done automatically?

Today this is a manual process of unlinking and linking the refreshed environments.
Dual write does not have APIs for these steps yet, otherwise this could be orchestrated hands-free with using LCS APIs followed by Dual write APIs.

### How to move some entities or scenarios from DI to DW set up just because of they need real time integration, and implications of changing pattern (I referred this as cutover)?

Migration path for Prospect to cash scenarios already documented [here](https://www.yammer.com/dynamicsaxfeedbackprograms/#/files/433337729024)
In general, the migration consists of 3 possible changes: 1) Manual maps migration from DI to DW , 2) Possible entity changes (Due to absence of advanced query capabilities) and 3) Possible data migration due to adapting to new concepts such as Company striping.

### Can I develop unbounded fields on Finance and Operations data entities to flow to Common Data Service via DW?

Yes. Both [computed and virtual fields](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/data-entity-computed-columns-virtual-fields) can be used, but you should pay special attention to performance overhead from additional X++ logic required for reads/write. Also roundtripping within the same transaction is not allowed, so avoid using virtual fields to transform / calculate additional values through X++ and expect that to go back to Common Data Service within same transaction.

### With Common Data Service offline app, What if it is not possible to update the 'other' side after reconnecting? Would that cause incorrect state between Common Data Service and Finance and Operations

Users can access Common Data Service data offline either via using Common Data Service applications or through using Field Service Mobile app. In both options, data will be kept offline, and it can be synced with the server in user's discretion. In case of any issues when the offline data is being synced with the server and updates cannot be performed because other end of Dual write is failing the error can be handled by utilizing conflict management settings in both options. For more details about different conflict management settings, see [Common Data Service conflict management settings](https://docs.microsoft.com/en-us/dynamics365/mobile-app/setup-mobile-offline-for-admin#step-23-set-conflict-detection-for-mobile-offline) and [Resco conflict resolution settings](https://docs.resco.net/wiki/Conflict_resolution).

## Mapping concepts between apps

### How are the numbers sequences handled? For instance, customer account in Finance and Operations apps is auto generated and customer account in CE is manual

Number sequences for Finance and Operations apps and Common Data Service apps are not connected. In a multi mastered entity scenario, plan for separate number sequence format or range per app, such as:
+ F0001,F0002 in Finance and Operations apps and C0001, C0002 in Common Data Service, OR
+	US0001 to US4999 in Finance and Operations apps and US5000 to US9999 in Common Data Service.
If entity is solely created in one system, then number sequencing needs setup in source only. You can refer to [Common Data Service autonumbering features](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/autonumber-fields) for more details.

### Can we map Common Data Service company specific entity with an Finance and Operations global entity or vice versa?

Dual-write only supports mapping between cross-company entities or company-specific entities from both sides.

### How can I make Common Data Service entity company specific?

Common Data Service custom entities can be made company specific by simply adding a M-1 relationship between your custom entities and our standard company entity. You should also include the company FK as part of the entity key. You can find full documentation of company concept [here](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/company-data)

### Is there a document on best practice entity usage? Should I use Customers V2, Customers V3, Customer Details? What is the difference and use case for each?

You should leverage the [out-of-the-box scenarios](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/customer-mapping) where possible, as it already covers common scenarios such as customer / vendor integration.
