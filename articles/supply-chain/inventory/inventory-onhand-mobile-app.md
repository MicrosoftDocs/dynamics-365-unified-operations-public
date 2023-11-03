---
title: Inventory Onhand mobile app
description: This article describes the function of Inventory onhand mobile power app and how to onboard the app.
author: yufeihuang
ms.date: 11/02/2023
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2023-10-02
ms.dyn365.ops.version: 10.0.38
---

# Inventory Onhand Mobile App

The inventory onhand mobile app is an power app that allows you to conviniently query and view Dynamics 365 Supplly Chain Management product inventory via mobile applications. It provides the following capabilities.
* Search product inventory by entering product ID or names
* Filter products and inventory by site, warehouse, location and batch and default product dimensions
* Filter products and inventory by inventory status and inventory quantity range
* Specify your regular sites & location to prioritize the searching range
* Switch among different legal entities to check cross-org inventory

# Onboard the Inventory Onhand mobile app

[!include [banner](../../includes/banner.md)]

This article describes how administrators can prepare your Microsoft Dynamics 365 Supply Chain Management and Dataverse environments to support the Inventory Onhand mobile app. It also describes how to install the app on your mobile devices.

## Prerequisites

Before you can start to onboard the Inventory Onhand mobile app, you must meet the requirements that are outlined in this section.

### System requirements

To run the latest Inventory Onhand mobile app, you must be using Supply Chain Management version 10.0.38 or later.

### Set up Dataverse for your Supply Chain Management environment

The mobile app uses [Dataverse virtual tables that are connected to Supply Chain Management](../../../fin-ops-core/dev-itpro/power-platform/virtual-entities-overview.md). Therefore, a Dataverse environment must be integrated with your Supply Chain Management environment. If Dataverse isn't already set up for your environment, follow the instructions in [Microsoft Power Platform integration with finance and operations apps](../../../fin-ops-core/dev-itpro/power-platform/overview.md).

When you create the Dataverse environment where you want to install the app, be sure to enable Dynamics 365 apps.

The [Power Apps component framework feature](/power-apps/developer/component-framework/component-framework-for-canvas-apps#enable-the-power-apps-component-framework-feature) must be enabled for your environment.

## <a name="install-in-dataverse"></a>Install the mobile app in Dataverse

You must install the Inventory Onhand mobile app in your Dataverse environment to enable users to access it when they sign in by using the Power Apps mobile app. The installation process also sets up the required user roles and other dependencies in Dataverse.

Follow these steps to install the Inventory Onhand mobile app in Dataverse.

1. Go to ["Dynamics 365 Inventory Onhand mobile application" in Microsoft AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.d365-scm-TBD).
1. Select **Get it now**.
1. Follow the instructions on your screen to install the app in the Dataverse environment that is connected to your target Supply Chain Management environment.

## Grant access to the mobile app in Dataverse

After the mobile app solution is installed in your Dataverse environment, you must share it with your users. The Inventory Onhand mobile app is a canvas app. To share it, follow the instructions in [Share an app](/power-apps/maker/canvas-apps/share-app#share-an-app).

The security roles that can access and query the inventory onhand through the mobile app are inherited from Dynamics 365 SCM. That means if a user can access the inventory onhand list in Dynamics 365 SCM (for example, with sales manager, warehouse manager or production manager), the user will also be able to query and view inventory data view the Inventory Onhand Mobile app. 

For more information about how to set up roles and security in Supply Chain Management, see
[Security roles](../../../fin-ops-core/dev-itpro/sysadmin/role-based-security.md#security-roles).


## Install and open the Inventory Onhand mobile app

Follow these steps to install and use the Inventory Onhand mobile app on a mobile device.

1. Install the Power Apps mobile app by following the instructions in [Install the Power Apps mobile app](/power-apps/mobile/run-powerapps-on-mobile).
1. Open the Power Apps mobile app, and sign in by using the same corporate account that you use to sign in to Supply Chain Management.
1. Use the **Search** field to search for *Inventory on-hand mobile app*. Because it's a canvas app, you can add it to your favorites list in Power Apps by swiping left on it after you find it.
1. Open the Inventory Onhand mobile app, and start to use it.
1. For the first time opening the app, you can go to settings and select an legal entity to start with. You also get the option to set your default site&warehouse where you normally work. This is especially useful for store managers.
1. The default site&warehouse will be first looked at when searching for product and inventory, and you also get to switch between a full search or a default site&warehouse search easily on the result display screen

## Clear the Power Apps cache on a mobile device after an update of the back-end setup

If the back-end setup is updated in Supply Chain Management after you install the Power Apps mobile app on a mobile device (for example, if the legal entity setup is changed), you might have to clear the cache in Power Apps to update the local setup data. Power Apps will then be able to reload the settings that otherwise might not take effect until the cache is cleared.

Follow these steps to clear the Power Apps cache on a mobile device.

1. Sign in to the Power Apps mobile app.
1. Select the image for your user account in the upper left of the page to open the settings menu.
1. Select **Clear cache** to open the **Clear cache** dialog box.
1. Select **Confirm**.