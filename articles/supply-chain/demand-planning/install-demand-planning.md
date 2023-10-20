---
title: Install, enable, and set up the Demand planning app
description: This article describes how to install, enable, and set up the Demand planning app for Dynamics 365 Supply Chain Management.
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

# Install and enable the Demand planning app

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

This article describes how to install, enable, and set up the Demand planning app for Dynamics 365 Supply Chain Management. It explains how to use the Power Platform admin center to install the Demand planning application in your tenant and then shows how to set up the feature in Supply Chain Management.

## Prerequisites

To use Demand planning with Supply Chain Management, you must be running one of the following versions of Supply Chain Management:

- Supply Chain Management version 10.0.36, build 10.0.1695.83
- Supply Chain Management version 10.0.37, build 10.0.1725.60
- Supply Chain Management version 10.0.38 (any build) or later

## Install the Demand planning app in Power Platform admin center

> [!NOTE]
>
> You must install Demand planning on the same tenant as your Supply Chain Management environment to ensure data can be imported and exported using the built-in import and export profiles.

Follow these steps to install the Demand planning app in Power Platform admin center.

1. Sign into the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. Do one of the following steps:
    - Select the following link to go directly to the Demand planning install page: [Install Demand planning](https://go.microsoft.com/fwlink/?linkid=2247704).
    - In the Power Platform admin center, select **Resources > Dynamics 365 apps** from the left-side navigation pane. Then select **Demand planning (preview)** app and select **Install** from the top toolbar.
1. Select an environment, review the packages to be installed, and select the **I agree to the terms of service check** box.
1. Select **Install**.

## Enable and configure Demand planning in Dynamics 365 Supply Chain Management

Follow these steps to enable and configure Demand planning in Supply Chain Management.

1. Go to the [**Feature management**](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace and turn on the *(Preview) Demand Planning* feature.
1. Go to **System administration \> Setup \> Demand planning app parameters**.
1. Open the **General** tab.
1. In the **Demand planning app URL**, enter the URL where the Demand planning app is installed.
1. Go to **Master Planning \> Setup \> Master planning parameters**.
1. Open the **Number sequences** tab.
1. In the grid, find the line where **Reference** is *Demand forecast sequence number*. Then select the link in the **Number sequence** column for that row.
1. The details page for the selected number sequence opens. Expand the **Performance** FastTab and make the following settings:
    - **Preallocation** – Set to *Yes*.
    - **Quantity of numbers** – Set to *500*.
1. On the Action Pane, select **Save**.

## Security roles and duties

Demand planning features in Supply Chain Management are only available to users that have the required security roles and related duties. When you enable the feature in Supply Chain Management, it adds a privilege called *Demand planning informational tile*, which grants users access to a button that opens the Demand planning app from the home page of Supply Chain Management. The privilege is added to the out-of-box roles and duties listed in the following table. If you're using custom roles, you'll have to assign the privilege to them manually after enabling the feature.

| Role name | Duty |
|--|--|
| Production planner | Maintain forecasts |
| Production planner | Maintain firming of planned orders |
| Production manager | Enable forecast process |
| Production planner | Maintain forecast planning |
| Production planner | Maintain demand forecasts |
| Sales manager | Maintain demand forecast |
| Production manager | Enable the demand planning process |

The feature also adds a new system role and user. A record is inserted into the Microsoft Entra ID applications that enables data to be exchange between Demand planning and Supply Chain Management.

For a user to be able to access the Demand planning application, the user must be granted access to the Dataverse environment with the *Demand planning service role* or *System administrator*. If you're the administrator of your Power Platform environment, you can add the required users by selecting **Users** on the relevant environment.
