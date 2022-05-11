---
# required metadata

title: Install, set up, and update the Customer portal
description: This topic provides licensing details and setup instructions for the Customer portal.
author: Henrikan
ms.date: 06/08/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: henrikan
ms.search.validFrom: 2020-04-22
ms.dyn365.ops.version: 10.0.13
---

# Install, set up, and update the Customer portal

[!include [banner](../includes/banner.md)]


## Licensing requirements

To implement the Customer portal, you must have the following licenses:

- **Power Apps portals** – This license is required to host the Customer portal. Portals are licensed based on usage. For more information, see the [Power Apps portals licensing requirements](/power-platform/admin/powerapps-flow-licensing-faq#portals).
- **Dual-write** – You must have the necessary licenses to enable dual-write for Supply Chain Management tables. For more information, see the [system requirements for dual-write](../../fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-system-req.md).

## Dependencies on dual-write and Power Apps portals

The Customer portal depends on Power Apps portals and dual-write, as shown in the following illustration.

![Customer portal dependencies.](media/customer-portal-elements.png "Customer portal dependencies")

Unlike other features from Supply Chain Management, the Customer portal template resides in Power Apps portals. Therefore, the Customer portal is limited by the functionality and capabilities that are provided by Power Apps portals and the tables in dual-write.

## <a name="required-setup"></a>Required setup to enable the Customer portal

After you've made sure that you have the required licenses, you can set up dual-write as described in the [dual-write initial synchronization instructions](../../fin-ops-core/dev-itpro/data-entities/dual-write/enable-entity-map.md).

Be sure to enable the following table mappings in dual-write:

- Sales Order Header
- Sales Order Details
- Accounts
- Contacts
- Products

After this setup is completed, you can provision the Customer portal template.

## Provision the Customer portal

Before you begin, make sure that you've already completed the [required setup](#required-setup). Then follow these steps to provision the Customer portal.

1. Go to [make.powerapps.com](https://make.powerapps.com/).
2. Make sure that you're using the environment where you enabled dual-write.
3. On the **Create** tab, scroll down to the **Start from template** section, and select the template that is named **Customer Portal**.
4. Follow the on-screen instructions.

After provisioning is completed, you can access the Customer portal in the **Your apps** section of the **Home** page.

> [!NOTE]
> If the dual-write solution isn't installed in the environment that you're working in, you will receive an error message, and the Customer portal won't be provisioned.

## Update the Customer portal

More functionality might be added to the Customer portal later. Any changes that Microsoft makes to the underlying solution components will automatically appear in your environment. However, the website that is provisioned in your environment won't automatically reflect changes that are made to the configuration data. You will have to manually apply those changes by getting the code from the new template and merging it with the provisioned website.

## Additional resources

To learn how you can set up and customize the Customer portal, you should start by reviewing the following documentation for the underlying technologies:

- [Power Apps portals documentation](/powerapps/maker/portals/overview)
- [Dual-write documentation](../../fin-ops-core/dev-itpro/data-entities/dual-write/dual-write-home-page.md)

To effectively manage your portals, you must understand the Power Apps portals and Microsoft Dataverse lifecycle. For more information, see the following resources:

- [About portal lifecycle](/powerapps/maker/portals/admin/portal-lifecycle)
- [Upgrade a portal](/powerapps/maker/portals/admin/upgrade-portal)
- [Migrate portal configuration](/powerapps/maker/portals/admin/migrate-portal-configuration)
- [Solution Lifecycle Management: Dynamics 365 for Customer Engagement apps](https://www.microsoft.com/download/details.aspx?id=57777)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]