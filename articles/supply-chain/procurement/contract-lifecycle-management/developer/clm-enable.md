---
title: Enable and configure CLM integration (preview)
description: This article describes the configuration steps that are required for integrating Microsoft Dynamics 365 Supply Chain Management and third-party contract lifecycle management providers
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: CLMIntegrationParameters
ms.topic: how-to
ms.date: 10/25/2024
ms.custom: 
  - bap-template
---

# Enable and configure CLM integration (preview)

[!include [banner](../../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.43 GA  -->

This article describes the configuration steps that are required for integrating Microsoft Dynamics 365 Supply Chain Management and third-party contract lifecycle management (CLM) providers. The configuration must be performed in Supply Chain Management and your CLM system before you can start using the integration.

You can always configure these settings manually in Supply Chain Management as described here, but in some cases your CLM provider can instead make most of these settings remotely (learn more in [Establish a connection from a CLM system to Supply Chain Management (preview)](clm-establish-connection.md)).

## Prerequisites

To use the features that are described in this article, you must be running Supply Chain Management version 10.0.42 or later.

## Enable the feature

If your system doesn't already include the features described in this article, go to [Feature management overview](../../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and turn on the *(Preview) Integrate with external contract lifecycle management systems* feature.

## Set up CLM connection parameters

Set up the connection to your external CLM system by following these steps.

1. Go to **Procurement and sourcing** \> **Setup** \> **CLM integration** \> **Contract management parameters**.
1. Open the **Connection** tab.
1. Expand the **General** FastTab and make the following settings:
    - **Connection name** – Enter a name to identify the CLM system.
    - **Base URL** – Enter the host name of the external CLM service. <!--KFM: We should explain a bit more about how these two URLs are different and/or used. -->
    - **External navigation base URL** – Enter the host name for external navigation. If this parameter isn't provided, the system uses the **Base URL** instead.
1. On the Action Pane, select **Save**.

## Set up external navigation links

External navigation links provide the capability to redirect a user to an external CLM system, where they can perform various actions such as create new contract, edit an existing contract, view a contract, and so on. These actions are optional, and corresponding buttons on the contract page are only shown after you've configured the relevant external navigation links.

To configure external navigation links, follow these steps.

1. Go to **Procurement and sourcing** \> **Setup** \> **CLM integration** \> **Contract management parameters**.
1. Open the **External navigation links** tab.
1. On the tab toolbar, select **New**.
1. The **New record** page opens. On the **General** FastTab, make the following settings:
    - **Navigation type** – Identify the type of navigation link you're setting up. Select one of the following values:
        - *New contract* – Settings for this record enable and configure the **New** button on the **All contracts** page.
        - *New contract from purchase agreement* – Settings for this record enable and configure the **New** button on the **Purchase agreements** page.
        - *Edit contract* – Settings for this record enable and configure the **Edit** button on the **All contracts** and **Purchase agreements** pages.
        - *Amend contract* – Settings for this record enable and configure the **Amend** button on the **All contracts** and **Purchase agreements** pages.
        - *View contract* – Settings for this record enable and configure the **View** button on the **All contracts** and **Purchase agreements** pages.  
    - **Navigation name** – Enter a descriptive name for this record.
    - **Relative URL** – Enter the relative path from the **Base URL** defined on the **Connections** tab to the page that should open when a user selects the button for the selected **Navigation type**. To see the full resulting URL, expand the **Preview** FastTab and inspect the **Absolute URL** field.
    - **Action** – Choose where the page should open when a user selects the button for the selected **Navigation type**. Select one of the following values:
       - *Open in new tab* – Open the external page in a new browser tab.
       - *Open in existing tab* – Open the external page in current browser tab.
1. The **Navigation link query strings** FastTab lets you add parameters to the URL, as required by the CLM system. Use the toolbar buttons to add or remove parameters in the grid as needed. For each parameter, make the following settings:
    - **Key** – Enter the key name of the parameter.
    - **Value** – Enter the value for the parameter. You can include dynamic values by entering placeholders formatted as `%placeholder_name%`, which are replaced with an actual value at runtime. A drop-down list lets you select from the supported placeholders. You construct a value that combines multiple placeholders and static text. The placeholders included in the drop-down list are determined by the current context, which depends on the **Navigation type**, and is derived from either the contract or purchase agreement record.
1. On the Action Pane, select **Save**.
1. Continue working until you have set up all of the external navigation links you need.

## Check the connection status

To inspect the current status of the connection between Supply Chain Management and the CLM system, follow these steps:

1. Go to **Procurement and sourcing** \> **Setup** \> **CLM integration** \> **Contract management parameters**.
1. Open the **Connection** tab.
1. Expand the **Connection status** FastTab. Here, the connection status is indicated using one of the following values:
    - *Not started* – The system hasn't tried to connect yet.
    - *Connection establishment failed* – The system attempted to connect, but failed.
    - *Connection established* – The connection was established and a handshake between the two systems succeeded.
    - *Configuration failed* – The connection is working, but at least one of the external navigation links isn't working.
    - *Ready* – The integration is ready for use.

The connection status is based on information submitted by your CLM system through the Supply Chain Management API. Learn more about how to set up your CLM system to return a value for this status indicator in [Establish a connection from a CLM system to Supply Chain Management](clm-establish-connection.md).
