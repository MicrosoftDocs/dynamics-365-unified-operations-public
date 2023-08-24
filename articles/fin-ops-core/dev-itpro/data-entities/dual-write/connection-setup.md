---
title: Guidance for dual-write setup
description: This article describes the scenarios that are supported for dual-write setup.
author: RamaKrishnamoorthy
ms.date: 06/28/2022
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: sericks
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2020-01-06
---

# Guidance for dual-write setup

[!include [banner](../../includes/banner.md)]



You can set up a dual-write connection between a finance and operations environment and a Dataverse environment.

+ A **finance and operations environment** provides the underlying platform for **finance and operations apps** (for example, Microsoft Dynamics 365 Finance, Dynamics 365 Supply Chain Management, Dynamics 365 Commerce, and Dynamics 365 Human Resources).
+ A **Dataverse environment** provides the underlying platform for **customer engagement apps** (Dynamics 365 Sales, Dynamics 365 Customer Service, Dynamics 365 column Service, Dynamics 365 Marketing, and Dynamics 365 Project Service Automation).


> [!IMPORTANT]
> The Human Resources module in Dynamics 365 Finance supports dual-write connections, but the Dynamics 365 Human Resources app doesn't.

Dual-write can be setup from LCS for both new and existing evironments involving Finance and Operantions app and customer engagement app. You can follow the guidance from [Dual-write setup from Lifecycle Services](lcs-setup.md).

Before you start dual-write on an entity, you can run an initial synchronization to handle existing data on both sides: Finance and operations apps and customer engagement apps. You can skip the initial synchronization if you don't have to sync data between the two environments.

An initial synchronization lets you copy existing data from one app to another bidirectionally. There are several setup scenarios, depending on the environments that you already have and the type of data in them.

The following setup scenarios are supported:

+ [A new finance and operations app instance and a new customer engagement app instance](#new-new)
+ [A new finance and operations app instance and an existing customer engagement app instance](#new-existing)
+ [A new finance and operations app instance that has data and a new customer engagement app instance](#new-data-new)
+ [A new finance and operations app instance that has data and an existing customer engagement app instance](#new-data-existing)
+ [An existing finance and operations app instance and a new customer engagement app instance](#existing-new)
+ [An existing finance and operations app instance and an existing customer engagement app instance](#existing-existing)

## <a id="new-new"></a>A new finance and operations app instance and a new customer engagement app instance

To set up a dual-write connection between a new instance of a finance and operations app that has no data and a new instance of a customer engagement app, follow the steps in [Dual-write setup from Lifecycle Services](lcs-setup.md). When the connection setup is completed, the following actions automatically occur:

- A new, empty finance and operations environment is provisioned.
- A new, empty instance of a customer engagement app is provisioned, where the CRM prime solution is installed.
- A dual-write connection is established for DAT company data.
- Table maps are enabled for live synchronization.

Both environments are then ready for live data synchronization.

## <a id="new-existing"></a>A new finance and operations app instance and an existing customer engagement app instance

To set up a dual-write connection between a new instance of a finance and operations app that has no data and an existing instance of a customer engagement app, follow the steps in [Dual-write setup from Lifecycle Services](lcs-setup.md). When the connection setup is completed, the following actions automatically occur:

- A new, empty finance and operations environment is provisioned.
- A dual-write connection is established for DAT company data.
- Table maps are enabled for live synchronization.

Both environments are then ready for live data synchronization.

To sync the existing Dataverse data to the finance and operations app, follow these steps.

1. Create a new company in the finance and operations app.
2. Add the company to the dual-write connection setup.
3. [Bootstrap](bootstrap-company-data.md) the Dataverse data by using a three-letter International Organization for Standardization (ISO) company code.
4. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section later in this article.

## <a id="new-data-new"></a>A new finance and operations app instance that has data and a new customer engagement app instance

To set up a dual-write connection between a new instance of a finance and operations app that has data and a new instance of a customer engagement app, follow the steps in the [A new finance and operations app instance and a new customer engagement app instance](#new-new) section earlier in this article. When the connection setup is completed, if you want to sync the data to the customer engagement app, follow these steps.

1. Open the finance and operations app from the LCS page, sign in, and then go to **Data Management \> Dual-write**.
2. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section.

## <a id="new-data-existing"></a>A new finance and operations app instance that has data and an existing customer engagement app instance

To set up a dual-write connection between a new instance of a finance and operations app that has data and an existing instance of a customer engagement app, follow the steps in the [A new finance and operations app instance and an existing customer engagement app instance](#new-existing) section earlier in this article. When the connection setup is completed, if you want to sync the data to the customer engagement app, follow these steps.

1. Open the finance and operations app from the LCS page, sign in, and then go to **Data Management \> Dual-write**.
2. Run the **Initial sync** functionality for the tables that you want to sync data for.

To sync the existing Dataverse data to the finance and operations app, follow these steps.

1. Create a new company in the finance and operations app.
2. Add the company to the dual-write connection setup.
3. [Bootstrap](bootstrap-company-data.md) the Dataverse data by using a three-letter ISO company code.
4. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section.

## <a id="existing-new"></a>An existing finance and operations app instance and a new customer engagement app instance

The setup of a dual-write connection between an existing instance of a finance and operations app and a new instance of a customer engagement app occurs using LCS power platform integration setup.

1. [Connect finance and operations apps with a new Microsoft Dataverse instance](/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv.md).
2. A dual-write connection is established for all legal entities. You can remove legal entities from Dual write workspace within Finance and Operations apps if you do not wish to synchronise the data for a specific company.
3. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section.

## <a id="existing-existing"></a>An existing finance and operations app instance and an existing customer engagement app instance

The setup of a dual-write connection between an existing instance of a finance and operations app and an existing instance of a customer engagement app occurs in the Finance and Operation environment.

1. [Connect finance and operations apps with an existing Microsoft Dataverse instance](/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv.md).
2. A dual-write connection is established for all legal entities. You can remove legal entities from Dual write workspace within Finance and Operations apps if you do not wish to synchronise the data for a specific company.
3. To sync the existing Dataverse data to the finance and operations app, [bootstrap](bootstrap-company-data.md) the Dataverse data by using a three-letter ISO company code.
4. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section.

## Example

For an example, see [Enabling the Customers V3—Contacts table map](enable-entity-map.md#enable-table-map)

For an alternative approach that is based on data volumes in each entity that must run an initial synchronization, see [Considerations for initial synchronization](initial-sync-guidance.md).


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
