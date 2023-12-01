---
title: Install, enable, and set up the Demand planning app (preview)
description: This article describes how to install, enable, and set up the Demand planning app for Microsoft Dynamics 365 Supply Chain Management.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/19/2023
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

## Install the Demand planning app in Power Platform admin center

> [!IMPORTANT]
> You must install Demand planning on the same tenant as your Supply Chain Management environment to ensure that the built-in import and export profiles can be used to import and export data.
>
> Due to a current technical limitation, you can't install Demand planning on your tenant's default environment.

Follow these steps to install the Demand planning app in Power Platform admin center.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. Select **Resources** \> **Dynamics 365 apps** on the left navigation pane. Select the **Demand planning (preview)** app, and then select **Install** on the top toolbar.
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

## Security roles and duties

Demand planning features in Supply Chain Management are available only to users who have the required security roles and related duties. When you enable the feature in Supply Chain Management, it adds a privilege that's named *Demand planning informational tile*. This privilege grants users access to a button that opens the Demand planning app from the home page of Supply Chain Management. The privilege is added to the out-of-box roles and duties that are listed in the following table. If you're using custom roles, you must manually assign the privilege to them after you enable the feature.

| Role name | Duty |
|---|---|
| Production planner | Maintain forecasts |
| Production planner | Maintain firming of planned orders |
| Production manager | Enable forecast process |
| Production planner | Maintain forecast planning |
| Production planner | Maintain demand forecasts |
| Sales manager | Maintain demand forecast |
| Production manager | Enable the demand planning process |

The feature also adds a new system role and user. A record that's inserted into the Microsoft Entra ID applications enables data to be exchange between Demand planning and Supply Chain Management.

To access the Demand planning app, users must be granted access to the Dataverse environment through *Demand planning service role* or *System administrator*. If you're the administrator of your Microsoft Power Platform environment, you can add the required users by selecting **Users** on the relevant environment.
