---
title: Inventory On-hand mobile app
description: Learn about the function of the Inventory On-hand mobile app and how to onboard it, including prerequisites and system requirements.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 02/11/2025
ms.custom: 
  - bap-template
---

# Inventory On-hand mobile app (Preview)

[!include [banner](../../includes/banner.md)]

> [!IMPORTANT]
>  The Inventory On-hand mobile app is now being released as a [sample app](https://github.com/microsoft/scmsamples-InventoryOnHand). The sample app is identical to the existing first-party app, but it is distributed through GitHub rather than through Power Platform Admin Center. You can fork the GitHub repository so you can customize it as needed for your scenarios. The first-party mobile app is deprecated and will be removed. Previously installed instances of the first-party mobile app will continue to work. For more information, see [Removed or deprecated features in Dynamics 365 Supply Chain Management](../get-started/ removed-deprecated-features-scm-updates.md).

The Inventory On-hand mobile app lets you query and view product inventory in Microsoft Dynamics 365 Supply Chain Management by using a mobile device. It was built by using Power Apps.

The app lets you perform the following tasks:

- Search product inventory by entering a product ID or name.
- Filter products and inventory by site, warehouse, location, batch, and default product dimensions.
- Filter products and inventory by inventory status and inventory quantity range.
- Specify your regular sites and locations to prioritize the search range.
- Switch among legal entities to check cross-organization inventory.

This article describes how administrators can prepare your Supply Chain Management and Dataverse environments to support the Inventory On-hand mobile app. It also describes how to install the app on your mobile devices.

## Prerequisites

Before you can start to onboard the Inventory On-hand mobile app, you must meet the requirements that are outlined in this section.

### System requirements

To run the latest Inventory On-hand mobile app, you must be using Supply Chain Management version 10.0.40 or later.

### Set up Dataverse for your Supply Chain Management environment

The mobile app uses [Dataverse virtual tables that are connected to Supply Chain Management](../../fin-ops-core/dev-itpro/power-platform/virtual-entities-overview.md). Therefore, a Dataverse environment must be integrated with your Supply Chain Management environment. If Dataverse isn't already set up for your environment, follow the instructions in [Microsoft Power Platform integration with finance and operations apps](../../fin-ops-core/dev-itpro/power-platform/overview.md).

When you create the Dataverse environment where you want to install the Inventory On-hand mobile app, be sure to enable Dynamics 365 apps.

The [Power Apps component framework feature](/power-apps/developer/component-framework/component-framework-for-canvas-apps#enable-the-power-apps-component-framework-feature) must be enabled for your environment.

## <a name="install-in-dataverse"></a>Install the mobile app in Dataverse

Please refer to [steps](https://github.com/microsoft/scmsamples-InventoryOnHand) for detail.

## Share the mobile app and assign security roles

After the mobile app solution is installed in your Dataverse environment, you must share it with your users. The Inventory On-hand mobile app is a canvas app. To share it, follow the instructions in [Share an app](/power-apps/maker/canvas-apps/share-app#share-an-app).

The security roles that can access and query on-hand inventory through the mobile app are inherited from your Supply Chain Management setup. Therefore, any user (such as a sales manager, warehouse manager, or production manager) that has the security roles required to access the on-hand inventory list in Supply Chain Management can also query and view that data in the Inventory On-hand mobile app. For more information about how to set up roles and security in Supply Chain Management, see [Security roles](../../fin-ops-core/dev-itpro/sysadmin/role-based-security.md#security-roles).

## Open the Inventory On-hand mobile app

Follow these steps to use the Inventory On-hand mobile app on a mobile device.

1. Open the Power Apps mobile app, and sign in by using the same corporate account that you use to sign in to Supply Chain Management.
1. Use the **Search** field to search for *Inventory on-hand mobile app*. Because the app is a canvas app, you can add it to your favorites list in Power Apps by swiping left on it after you find it.
1. Open the Inventory On-hand mobile app, and start to use it.
1. The first time that you open the app, you can go to the settings and select a legal entity. You can also set the default site and warehouse where you usually work. These settings are especially useful for store managers.
1. When you search for products and inventory, the app first searches in the default site and warehouse. On the result page, you can easily switch between a full search and a search in the default site and warehouse.

## Clear the Power Apps cache on a mobile device after an update of the back-end setup

If the back-end setup is updated in Supply Chain Management after you install the Power Apps mobile app on a mobile device (for example, if the legal entity setup is changed), you might have to clear the cache in Power Apps to update the local setup data. Power Apps then reloads the settings that otherwise might not take effect until the cache is cleared.

Follow these steps to clear the Power Apps cache on a mobile device.

1. Sign in to the Power Apps mobile app.
1. In the upper left of the page, select the image for your user account to open the settings menu.
1. Select **Clear cache** to open the **Clear cache** dialog box.
1. Select **Confirm**.

## Frequently asked questions

### What platforms and mobile devices are supported?

The Inventory On-hand mobile app runs within the Power Apps mobile app. All platforms supported by the Power Apps mobile app can also run the Inventory On-hand mobile app. Learn more in [System requirements, limits, and configuration values for Power Apps](/power-apps/limits-and-config).

### Why don't I see anything when I sign in to the app?

If you don't see any features in the app, you probably lack the permissions required to access them. Access is controlled by the security roles assigned to your user account in Supply Chain Management. The roles you need are the same as those required to access the on-hand inventory list in Supply Chain Management. Learn more in [Security roles](../../fin-ops-core/dev-itpro/sysadmin/role-based-security.md#security-roles).

### Can I customize and extend the app?

Yes. You can customize and extend the app in downloaded repository.

### Does the app support offline mode?

No, the Inventory On-hand mobile app doesn't currently support offline mode.

### Is there multi-language support?

Yes, the Inventory On-hand mobile app is available in all the same languages as Supply Chain Management. The language is set according to your mobile device settings.

