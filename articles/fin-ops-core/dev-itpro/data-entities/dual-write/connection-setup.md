---
title: Guidance for dual-write setup
description: Understand the scenarios that are supported for dual-write setup, including various examples that provide guidance for dual-write setups.
author: RamaKrishnamoorthy
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/15/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Application User, IT Pro
ms.search.region: global
ms.search.validFrom: 2020-01-06
---

# Guidance for dual-write setup

[!include [banner](../../includes/banner.md)]

You can set up a dual-write connection between a finance and operations environment and a Dataverse environment.

+ A **finance and operations environment** provides the underlying platform for **finance and operations apps** (for example, Microsoft Dynamics 365 Finance, Dynamics 365 Supply Chain Management, Dynamics 365 Commerce, and Dynamics 365 Human Resources).
+ A **Dataverse environment** provides the underlying platform for **customer engagement apps** (Dynamics 365 Sales, Dynamics 365 Customer Service, Dynamics 365 Field Service, Dynamics 365 Marketing, and Dynamics 365 Project Service Automation).

> [!IMPORTANT]
> The Human Resources module in Dynamics 365 Finance supports dual-write connections, but the Dynamics 365 Human Resources app doesn't.

You can set up dual-write from Lifecycle Services for both new and existing environments that involve finance and operations apps and customer engagement apps. For more information, see [Dual-write setup from Lifecycle Services](lcs-setup.md).

Before you start dual-write on an entity, run an initial synchronization to handle existing data on both sides: finance and operations apps and customer engagement apps. You can skip the initial synchronization if you don't need to sync data between the two environments.

An initial synchronization copies existing data from one app to another bidirectionally. Several setup scenarios exist, depending on the environments that you already have and the type of data in them.

The following setup scenarios are supported:

+ [A new finance and operations app instance and a new customer engagement app instance](#new-new)
+ [A new finance and operations app instance and an existing customer engagement app instance](#new-existing)
+ [A new finance and operations app instance that has data and a new customer engagement app instance](#new-data-new)
+ [A new finance and operations app instance that has data and an existing customer engagement app instance](#new-data-existing)
+ [An existing finance and operations app instance and a new customer engagement app instance](#existing-new)
+ [An existing finance and operations app instance and an existing customer engagement app instance](#existing-existing)

## <a id="new-new"></a>A new finance and operations app instance and a new customer engagement app instance

To set up a dual-write connection between a new instance of a finance and operations app that has no data and a new instance of a customer engagement app, follow the steps in [Dual-write setup from Lifecycle Services](lcs-setup.md). When you complete the connection setup, the following actions automatically occur:

+ A new, empty finance and operations environment is provisioned.
+ A new, empty instance of a customer engagement app is provisioned, where the CRM prime solution is installed.
+ A dual-write connection is established for DAT company data.
+ Table maps are enabled for live synchronization.

Both environments are then ready for live data synchronization.

## <a id="new-existing"></a>A new finance and operations app instance and an existing customer engagement app instance

To set up a dual-write connection between a new instance of a finance and operations app that has no data and an existing instance of a customer engagement app, follow the steps in [Dual-write setup from Lifecycle Services](lcs-setup.md). When you complete the connection setup, the following actions automatically occur:

+ A new, empty finance and operations environment is provisioned.
+ A dual-write connection is established for DAT company data.
+ Table maps are enabled for live synchronization.

Both environments are then ready for live data synchronization.

To sync the existing Dataverse data to the finance and operations app, follow these steps:

1. Create a new company in the finance and operations app.
1. Add the company to the dual-write connection setup.
1. [Bootstrap](bootstrap-company-data.md) the Dataverse data by using a three-letter International Organization for Standardization (ISO) company code.
1. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section later in this article.

## <a id="new-data-new"></a>A new finance and operations app instance that has data and a new customer engagement app instance

To set up a dual-write connection between a new instance of a finance and operations app that has data and a new instance of a customer engagement app, follow the steps in the [A new finance and operations app instance and a new customer engagement app instance](#new-new) section earlier in this article. When the connection setup is completed, if you want to sync the data to the customer engagement app, follow these steps:

1. Open the finance and operations app from the Lifecycle Services page, sign in, and then go to **Data Management \> Dual-write**.
1. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section.

## <a id="new-data-existing"></a>A new finance and operations app instance that has data and an existing customer engagement app instance

To set up a dual-write connection between a new instance of a finance and operations app that has data and an existing instance of a customer engagement app, follow the steps in the [A new finance and operations app instance and an existing customer engagement app instance](#new-existing) section earlier in this article. When the connection setup is completed, if you want to sync the data to the customer engagement app, follow these steps:

1. Open the finance and operations app from the Lifecycle Services page, sign in, and then go to **Data Management \> Dual-write**.
1. Run the **Initial sync** functionality for the tables that you want to sync data for.

To sync the existing Dataverse data to the finance and operations app, follow these steps:

1. Create a new company in the finance and operations app.
1. Add the company to the dual-write connection setup.
1. [Bootstrap](bootstrap-company-data.md) the Dataverse data by using a three-letter ISO company code.
1. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section.

## <a id="existing-new"></a>An existing finance and operations app instance and a new customer engagement app instance

You set up a dual-write connection between an existing instance of a finance and operations app and a new instance of a customer engagement app by using Lifecycle Services power platform integration setup.

1. Follow [Connect finance and operations apps with a new Microsoft Dataverse instance](/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv) to establish the link by using Lifecycle Services.
1. The dual-write connection is created for all legal entities. If you don't want to synchronize data for a specific company, you can remove legal entities from the dual-write workspace within finance and operations apps.
1. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section.

## <a id="existing-existing"></a>An existing finance and operations app instance and an existing customer engagement app instance

You set up a dual-write connection between an existing instance of a finance and operations app and an existing instance of a customer engagement app in the finance and operation apps environment.

1. Follow [Connect finance and operations apps with an existing Microsoft Dataverse instance](/dynamics365/fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv) to establish the link by using Lifecycle Services.
1. The dual-write connection is created for all legal entities. If you don't want to synchronize data for a specific company, you can remove legal entities from the dual-write workspace within finance and operations apps.
1. To sync the existing Dataverse data to the finance and operations app, [bootstrap](bootstrap-company-data.md) the Dataverse data by using a three-letter ISO company code.
1. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section.

## Example

For an example, see [Enabling the Customers V3—Contacts table map](enable-entity-map.md#enable-table-map).

For an alternative approach that is based on data volumes in each entity that must run an initial synchronization, see [Considerations for initial synchronization](initial-sync-guidance.md).

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
