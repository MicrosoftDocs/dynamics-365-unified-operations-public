---
title: Guidance for dual-write setup
description: This topic describes the scenarios that are supported for dual-write setup.
author: RamaKrishnamoorthy
ms.date: 10/12/2020
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: tfehr
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2020-01-06
---

# Guidance for dual-write setup

[!include [banner](../../includes/banner.md)]

[!include [preview-banner](../../includes/preview-banner.md)]



You can set up a dual-write connection between a Finance and Operations environment and a Dataverse environment.

+ A **Finance and Operations environment** provides the underlying platform for **Finance and Operations apps** (for example, Microsoft Dynamics 365 Finance, Dynamics 365 Supply Chain Management, Dynamics 365 Commerce, and Dynamics 365 Human Resources).
+ A **Dataverse environment** provides the underlying platform for **customer engagement apps** (Dynamics 365 Sales, Dynamics 365 Customer Service, Dynamics 365 column Service, Dynamics 365 Marketing, and Dynamics 365 Project Service Automation).

> [!IMPORTANT]
> The Human Resources module in Dynamics 365 Finance supports dual-write connections, but the Dynamics 365 Human Resources app doesn't.

The setup mechanism varies, depending on your subscription and the environment:

+ For new instances of Finance and Operations apps, the setup of a dual-write connection begins in Microsoft Dynamics Lifecycle Services (LCS). If you have a license for Microsoft Power Platform, you will get a new Dataverse environment if your tenant doesn't have one.
+ For existing instances Finance and Operations apps, the setup of a dual-write connection begins in the Finance and Operations environment.

Before you start dual-write on an entity, you can run an initial synchronization to handle existing data on both sides: Finance and Operations apps and customer engagement apps. You can skip the initial synchronization if you don't have to sync data between the two environments.

An initial synchronization lets you copy existing data from one app to another bidirectionally. There are several setup scenarios, depending on the environments that you already have and the type of data in them.

The following setup scenarios are supported:

+ [A new Finance and Operations app instance and a new customer engagement app instance](#new-new)
+ [A new Finance and Operations app instance and an existing customer engagement app instance](#new-existing)
+ [A new Finance and Operations app instance that has data and a new customer engagement app instance](#new-data-new)
+ [A new Finance and Operations app instance that has data and an existing customer engagement app instance](#new-data-existing)
+ [An existing Finance and Operations app instance and a new customer engagement app instance](#existing-new)
+ [An existing Finance and Operations app instance and an existing customer engagement app instance](#existing-existing)

## <a id="new-new"></a>A new Finance and Operations app instance and a new customer engagement app instance

To set up a dual-write connection between a new instance of a Finance and Operations app that has no data and a new instance of a customer engagement app, follow the steps in [Dual-write setup from Lifecycle Services](lcs-setup.md). When the connection setup is completed, the following actions automatically occur:

- A new, empty Finance and Operations environment is provisioned.
- A new, empty instance of a customer engagement app is provisioned, where the CRM prime solution is installed.
- A dual-write connection is established for DAT company data.
- Table maps are enabled for live synchronization.

Both environments are then ready for live data synchronization.

## <a id="new-existing"></a>A new Finance and Operations app instance and an existing customer engagement app instance

To set up a dual-write connection between a new instance of a Finance and Operations app that has no data and an existing instance of a customer engagement app, follow the steps in [Dual-write setup from Lifecycle Services](lcs-setup.md). When the connection setup is completed, the following actions automatically occur:

- A new, empty Finance and Operations environment is provisioned.
- A dual-write connection is established for DAT company data.
- Table maps are enabled for live synchronization.

Both environments are then ready for live data synchronization.

To sync the existing Dataverse data to the Finance and Operations app, follow these steps.

1. Create a new company in the Finance and Operations app.
2. Add the company to the dual-write connection setup.
3. [Bootstrap](bootstrap-company-data.md) the Dataverse data by using a three-letter International Organization for Standardization (ISO) company code.
4. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section later in this topic.

## <a id="new-data-new"></a>A new Finance and Operations app instance that has data and a new customer engagement app instance

To set up a dual-write connection between a new instance of a Finance and Operations app that has data and a new instance of a customer engagement app, follow the steps in the [A new Finance and Operations app instance and a new customer engagement app instance](#new-new) section earlier in this topic. When the connection setup is completed, if you want to sync the data to the customer engagement app, follow these steps.

1. Open the Finance and Operations app from the LCS page, sign in, and then go to **Data Management \> Dual-write**.
2. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section.

## <a id="new-data-existing"></a>A new Finance and Operations app instance that has data and an existing customer engagement app instance

To set up a dual-write connection between a new instance of a Finance and Operations app that has data and an existing instance of a customer engagement app, follow the steps in the [A new Finance and Operations app instance and an existing customer engagement app instance](#new-existing) section earlier in this topic. When the connection setup is completed, if you want to sync the data to the customer engagement app, follow these steps.

1. Open the Finance and Operations app from the LCS page, sign in, and then go to **Data Management \> Dual-write**.
2. Run the **Initial sync** functionality for the tables that you want to sync data for.

To sync the existing Dataverse data to the Finance and Operations app, follow these steps.

1. Create a new company in the Finance and Operations app.
2. Add the company to the dual-write connection setup.
3. [Bootstrap](bootstrap-company-data.md) the Dataverse data by using a three-letter ISO company code.
4. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section.

## <a id="existing-new"></a>An existing Finance and Operations app instance and a new customer engagement app instance

The setup of a dual-write connection between an existing instance of a Finance and Operations app and a new instance of a customer engagement app occurs in the Finance and Operation environment.

1. [Set up the connection from the Finance and Operations app](enable-dual-write.md).
2. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section.

## <a id="existing-existing"></a>An existing Finance and Operations app instance and an existing customer engagement app instance

The setup of a dual-write connection between an existing instance of a Finance and Operations app and an existing instance of a customer engagement app occurs in the Finance and Operation environment.

1. [Set up the connection from the Finance and Operations app](enable-dual-write.md).
2. To sync the existing Dataverse data to the Finance and Operations app, [bootstrap](bootstrap-company-data.md) the Dataverse data by using a three-letter ISO company code.
3. Run the **Initial sync** functionality for the tables that you want to sync data for.

For links to an example and an alternative approach, see the [Example](#example) section.

## Example

For an example, see [Enabling the Customers V3—Contacts table map](enable-entity-map.md#enable-table-map)

For an alternative approach that is based on data volumes in each entity that must run an initial synchronization, see [Considerations for initial synchronization](initial-sync-guidance.md).


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]