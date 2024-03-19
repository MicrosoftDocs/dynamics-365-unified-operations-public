---
title: Install, enable, and set up the Demand planning app (preview)
description: This article describes how to install, enable, and set up the Demand planning app for Microsoft Dynamics 365 Supply Chain Management.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 02/24/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Install, enable, and set up the Demand planning app (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

This article describes how to install, enable, and set up the Demand planning app for Microsoft Dynamics 365 Supply Chain Management. It explains how to use Power Platform admin center to install the Demand planning app in your tenant and set up the feature in Supply Chain Management.

## Prerequisites

To use Demand planning with Supply Chain Management, you must be running one of the following versions of Supply Chain Management:

- Supply Chain Management version 10.0.36, build 10.0.1695.83
- Supply Chain Management version 10.0.37, build 10.0.1725.60
- Supply Chain Management version 10.0.38 (any build) or later

> [!IMPORTANT]
> **The Demand planning app no longer supports Supply Chain Management "Cloud hosted" environments.**
>
> As of February 28, 2024, the Demand planning app no longer supports Supply Chain Management environments of type "Cloud hosted". Thereafter, you can no longer import, export, or synchronize data between the Demand planning app and Supply Chain Management environments of this type.
>
> If you are running a "Cloud hosted" environment of Supply Chain Management and wish to continue using Demand planning, then you must switch to a Supply Chain Management environment of type "Tier-2" or above or set up a [unified development environment](/power-platform/developer/unified-experience/finance-operations-dev-overview). You must then create new import and export profiles in your Demand planning app and configure them to connect to your new Supply Chain Management environment.

## Install the Demand planning app in Power Platform admin center

> [!IMPORTANT]
> You must install Demand planning on the same tenant as your Supply Chain Management environment to ensure that the built-in import and export profiles can be used to import and export data.
>
> Due to a current technical limitation, you can't install Demand planning on your tenant's default environment.

Follow these steps to install the Demand planning app in Power Platform admin center.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. Select **Resources** \> **Dynamics 365 apps** on the left navigation pane.
1. Search for and select the app named *Dynamics 365 Demand Planning Application*.
1. Select **Install** on the top toolbar.
1. Select an environment, review the packages that will be installed, and select the **I agree to the terms of service** checkbox.
1. Select **Install**.

## Enable and configure Demand planning in Supply Chain Management

Follow these steps to enable and configure Demand planning in Supply Chain Management.

1. In the [**Feature management**](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace, turn on the *(Preview) Demand Planning* feature.
1. Go to **System administration** \> **Setup** \> **Demand planning app parameters**.
1. On the **General** tab, in the **Demand planning app URL** field, enter the URL where the Demand planning app is installed.
1. Go to **Master Planning** \> **Setup** \> **Master planning parameters**.
1. On the **Number sequences** tab, in the grid, find the row where the **Reference** field is set to *Demand forecast sequence number*. Then select the link in the **Number sequence** column for that row.
1. On the details page for the selected number sequence, on the **Performance** FastTab, set the following field:

    - **Preallocation** – Set this option to *Yes*.
    - **Quantity of numbers** – Set the value to *500*.

1. On the Action Pane, select **Save**.
1. You must now refresh the data entity list in Supply Chain Management to ensure that data imports and exports between Supply Chain Management and Demand planning will work correctly. Follow these steps:
    1. Go to **System administration \> Workspaces \> Data management**.
    1. Select the **Framework parameters** tile.
    1. Open the **Entity settings** tab.
    1. Select **Refresh entity list**.
