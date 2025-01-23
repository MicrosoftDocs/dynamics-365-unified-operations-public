---
title: Enable and configure CLM integration (preview)
description: Learn how to configure the integration of Microsoft Dynamics 365 Supply Chain Management and third-party contract lifecycle management (CLM) providers.
author: ShriramSivasankaran
ms.author: shriramsiv
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
<!-- KFM: Preview until 10.0.43 GA -->

This article describes the configuration steps that must be completed to integrate Microsoft Dynamics 365 Supply Chain Management and third-party contract lifecycle management (CLM) providers. The configuration must be done in both Supply Chain Management and your CLM system before you can start to use the integration.

You can always manually configure the settings in Supply Chain Management as described in this article. However, in some cases, your CLM provider can remotely configure most of these settings instead. Learn more in [Establish a connection from a CLM system to Supply Chain Management](clm-establish-connection.md).

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.42 or later.
- The feature that is named *Integrate with external contract lifecycle management systems* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up CLM connection parameters

To set up the connection to your external CLM system, follow these steps.

1. Go to **Procurement and sourcing** \> **Setup** \> **CLM integration** \> **Contract management parameters**.
1. On the **Connection** tab, on the **General** FastTab, set the following fields:

    - **Connection name** – Enter a name to identify the CLM system.
    - **Base URL** – Enter the host name of the external CLM service.
    - **External navigation base URL** – Some CLM providers might require an extra URL, but most don't. Leave this field blank unless your CLM provider or Microsoft Support tells you to set it.

1. On the Action Pane, select **Save**.

## Set up external navigation links

External navigation links provide the capability to redirect users to an external CLM system where they can perform various actions. For example, they can create new contracts, edit existing contracts, and view contracts. These actions are optional, and the corresponding buttons appear on the contract page only after you configure the relevant external navigation links.

To configure external navigation links, follow these steps.

1. Go to **Procurement and sourcing** \> **Setup** \> **CLM integration** \> **Contract management parameters**.
1. On the **External navigation links** tab, on the toolbar, select **New**.
1. On the **New record** page, on the **General** FastTab, set the following fields:

    - **Navigation type** – Select one of the following values to specify the type of navigation link that you're setting up:

        - *New contract* – Settings for this record enable and configure the **New** button on the **All contracts** page.
        - *New contract from purchase agreement* – Settings for this record enable and configure the **New** button on the **Purchase agreements** page.
        - *Edit contract* – Settings for this record enable and configure the **Edit** button on the **All contracts** and **Purchase agreements** pages.
        - *Amend contract* – Settings for this record enable and configure the **Amend** button on the **All contracts** and **Purchase agreements** pages.
        - *View contract* – Settings for this record enable and configure the **View** button on the **All contracts** and **Purchase agreements** pages.

    - **Navigation name** – Enter a descriptive name for the record.
    - **Relative URL** – Enter the relative path from the base URL that is defined on the **Connections** tab to the page that should be opened when a user selects the button for the selected navigation type. You can view the full resulting URL in the **Absolute URL** field on the **Preview** FastTab.
    - **Action** – Select one of the following values to specify where the page should be opened when a user selects the button for the selected navigation type:

        - *Open in new tab* – Open the external page on a new browser tab.
        - *Open in existing tab* – Open the external page on the current browser tab.

1. On the **Navigation link query strings** FastTab, you can add any parameters that the CLM system requires to the URL. Use the toolbar buttons to add parameters to the grid, or remove them, as you require. For each parameter, set the following fields:

    - **Key** – Enter the key name of the parameter.
    - **Value** – Enter the value of the parameter. To include dynamic values, you can insert supported placeholders be selecting them in a dropdown list. Placeholders are formatted as `%placeholder_name%`. They are replaced with actual values at runtime. You can construct a value that combines multiple placeholders and static text.

        The placeholders that are available for selection in the dropdown list are determined by the current context. This context depends on the navigation type and is derived from either the contract record or the purchase agreement record.

1. On the Action Pane, select **Save**.
1. Continue to work until you finish setting up all the external navigation links that you need.

## Review the connection status

To review the current status of the connection between Supply Chain Management and the CLM system, follow these steps.

1. Go to **Procurement and sourcing** \> **Setup** \> **CLM integration** \> **Contract management parameters**.
1. On the **Connection** tab, select the **Connection status** FastTab. Here, the connection status is indicated through one of the following values:

    - *Not started* – The system hasn't yet tried to connect.
    - *Connection establishment failed* – The system tried to connect but failed.
    - *Connection established* – The connection was established, and a handshake between the two systems succeeded.
    - *Configuration failed* – The connection is working, but at least one of the external navigation links isn't working.
    - *Ready* – The integration is ready to be used.

The connection status is based on information that your CLM system submits through the Supply Chain Management API. Learn how to set up your CLM system to return a value for this status indicator in [Establish a connection from a CLM system to Supply Chain Management](clm-establish-connection.md).

## View and edit contract types

*Contract types* represent the types of external contracts that are either integrated with or accessible from Supply Chain Management. (Examples of external contracts include purchase contracts and non-disclosure contracts.) Contract types are used to help describe each contract that is listed on the [**All contracts** page](../clm-use.md). In most cases, the values are submitted and maintained exclusively by your CLM provider.

To view the names and descriptions of the various contract types that are integrated with your CLM system, go to **Procurement and Sourcing** \> **Setup** \> **CLM integration** \> **Contract types**. Although admins can add, edit, and remove values on the **Contract types** page, you typically should do so only at the direction of your CLM provider or Microsoft Support.
