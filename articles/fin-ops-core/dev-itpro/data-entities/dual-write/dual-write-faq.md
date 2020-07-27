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

## Setup
### Is dual write available for Government Community Cloud (GCC)?
Not yet. 
Dual write requires Finance and Operations apps environment and CDS environment to be in the same tenant. Since Finance and Operations apps is not available in GCC yet, dual write doesn’t support linking Finance and Operations apps/CDS across two different tenants.
### If a customer doesn't have sales or field service, but they just want to have the sales order data in CDS, can they do it without buying sales/CE license?
When customers possess a valid Finance and Operations applications license, they are entitled to enable dual write between the Common Data Service and Finance and Operations applications. This entitlement does not include capacity consumed by the replicated data; if necessary, this is purchased separately. This entitlement does not include use rights for the Dynamics 365 for Customer Engagement applications, including Sales, Service, Marketing, etc; if necessary, this is purchased separately.
### Any plans to let DW use CDS as a hub between multiple F&O instances, allowing for data to synchronize between two or  more F&O instances?
The current plan of record is to restrict this to 1-1 mapping between F&O and CDS.
### Can you control the sequencing of maps in Dual write, like in DI?
DW is transaction based. For example, if one change in F&O happens to trigger multiple maps to sync with CDS, then these will be in sequenced by default as they are updated in the database.  
This makes more sense in the context of initial sync; system will provide related entity map in a specified order and you can reorder the list to best suit to your environment.
### Do the application users need to have any special permissions to enable/configure dual write ?
Dual write setup requires 2 Azure AD applications setups in Finance &Operations and relevant application users to be setup in CDS. These application users should contain the appropriate application IDs, see [documentation link](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/requirements-and-prerequisites#verify-requirements-and-grant-access) for more details, and they need to be given relevant entity permissions via a security role for the connection to work properly.
### I have multiple legal entities and some of my maps are specific per legal entity (or only valid for some legal entities). What is the best way to address this requirement? Can we apply a filter (e.g. Company = USMF) to address this? 
It is not possible to map entity maps applicable to specific legal entity.  Legal entity mapping can be done at the linking CDS environment.
### Can we adopt both DI and DW in the system and does it cause any referential integrity issues?
You can't run dual-write and the [Prospect to cash solution](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/sales-marketing/accounts-template-mapping-direct) for Data integrator side by side. If you're running the Prospect to cash solution for Data integrator, you must uninstall it.
We suggest adopting one of the two patterns anytime. We recommend using Dual Writes as integration pattern.
### If Dual-write solutions get installed in CDS, can I uninstall them?
These are managed solutions. Uninstalling and reinstalling a managed solution is practically never an option when the solution contains entities or attributes. This is because data is lost when entities are deleted. Please refer this [link](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/maintain-managed-solutions) for more details.
### Say we have data on both sides (CE & F&O) we bootstrap our existing data in CE. If our data is not currently aligned, can we specify a master source for the initialization run so that all differences are applied to the target?
After the bootstrapping is done, you can enable initial sync to apply differences and chose a master. You can refer more information [here](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/bootstrap-company-data) for bootstrapping and [here](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/dual-write/enable-entity-map) for initial sync.

## Dual-write administration and management
### What is the purpose of the Integration Key and is it mandatory?
Integration key is the natural key which uniquely identifies records. Integration keys are only required for CDS entities, and can be manually created within Dual-write, or automatically created from entity's alternate keys, if one is already provided for an entity. Integration keys are used for the same purpose of Alternate keys, to provide an efficient and accurate way of integrating data with external systems. It’s essential in cases when an external system doesn’t store the Globally Unique Identifier (GUID) IDs that uniquely identify records in Common Data Service.
Dual write uses integration keys to uniquely identify records using one or more entity field values that represent a unique combination. For example, to identify an account record with an integration key, you can use the account number or the account number field in combination with some other fields which have values that should not change. You can find more details on alternate keys [here](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/define-alternate-keys-portal)
