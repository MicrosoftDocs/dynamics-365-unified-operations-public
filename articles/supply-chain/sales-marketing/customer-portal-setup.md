---
# required metadata

title: Install, set up, and update the Customer portal
description: Licensing details and setup instructions for the Customer portal
author: dasani-madipalli
manager: tfehr
ms.date: 04/22/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: damadipa
ms.search.validFrom: 2020-04-22
ms.dyn365.ops.version: Release 10.0.13
---

# Install, set up, and update the Customer portal

## Licensing requirements

To implement the Customer portal, you must have the following licenses:

- **Power Apps portals** – This license is required to host the Customer portal. Portals are licensed based on usage. For details, see the [Power Apps portals licensing requirements](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#portals).
- **Dual-write** - You will need the necessary licenses to make Dual-write enabled for supply chain management entities. Refer to the [System requirements for dual-write](../../fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-system-req.md) to learn more

## Dependencies on dual-write and Power Apps portals

The Customer portal depends on Power Apps portals and dual-write, as shown in the following illustration.

![Customer portal dependencies](media/customer-portal-elements.png "Customer portal dependencies")

Unlike other features from Supply Chain Management, the template resides in Power Apps portals. Therefore, the Customer portal is limited by the functionality and capabilities that are provided by Power Apps portal and the entities in dual-write.

<a name="required-setup"></a>

## Required setup to enable the Customer portal

After you've made sure that you have the required licenses, you can set up dual-write as described in the [dual-write initial synchronization instructions](../../fin-ops-core/dev-itpro/data-entities/dual-write/initial-sync.md).

Be sure to enable the following entity mappings in dual-write:

- Sales Order Header
- Sales Order Details
- Accounts
- Contacts
- Products

After these entities are enabled, you can provision the Customer portal template.

## Provision the Customer portal

Before you provision the Customer portal, make sure that you've already completed the [required setup](#required-setup). Then, to provision the Customer portal, follow these steps.

1. Go to [make.powerapps.com](http://make.powerapps.com/).
2. Make sure that you're using the environment where you enabled dual-write.
3. On the **Create** tab, scroll down to the **Start from template** section, and select the template that is named **Supply Chain Management Customer**.
4. Follow the on-screen instructions.

After provisioning is completed, you can access the Customer portal in the **Your apps** section of the **Home** page.

> [!NOTE]
> If the dual-write solution isn't installed in the environment that you're working in, you will receive an error message, and the Customer portal won't be provisioned.

## Update the Customer portal

More functionality might be added to the Customer portal later. Any changes that Microsoft makes to the underlying solution components will automatically appear in your environment. However, changes in the configuration data won't automatically be present on the provisioned website. You will have to manually apply these changes by getting the code from the new template and merging it with the website that is provisioned in your environment.

## Resources

To learn how you can set up and customize the Customer portal, you should start by reviewing the following documentation for the underlying technologies:

- [Power Apps portals documentation](https://docs.microsoft.com/powerapps/maker/portals/overview)
- [Dual-write documentation](../../fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-home-page.md)

To effectively manage your portals, you must understand the Power Apps portals and Common Data Service lifecycle. For details, review the following resources:

- [About portal lifecycle](https://docs.microsoft.com/powerapps/maker/portals/admin/portal-lifecycle)
- [Upgrade a portal](https://docs.microsoft.com/powerapps/maker/portals/admin/upgrade-portal)
- [Migrate portal configuration](https://docs.microsoft.com/powerapps/maker/portals/admin/migrate-portal-configuration)
- [Solution Lifecycle Management: Dynamics 365 for Customer Engagement apps](https://www.microsoft.com/download/details.aspx?id=57777)
