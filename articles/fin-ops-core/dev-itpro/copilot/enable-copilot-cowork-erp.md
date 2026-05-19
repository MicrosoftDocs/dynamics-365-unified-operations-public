---
title: Enable the Dynamics 365 ERP apps plugin for Copilot Cowork (Frontier)
description: Learn how to enable the Dynamics 365 ERP apps plugin for Microsoft Copilot Cowork so that users in your organization can work with finance and operations data through Cowork.
author: anupams
ms.author: anupams
ms.reviewer: ilebedev
ms.topic: how-to
ms.date: 05/12/2026
ms.update-cycle: 180-days
ms.custom: bap-template
ms.collection:
  - bap-ai-copilot
audience: Application User
ms.search.region: Global
ms.search.form:
---

# Enable the Dynamics 365 ERP apps plugin for Copilot Cowork (Frontier)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
[!INCLUDE [cowork-preview](../../fin-ops/includes/cowork-preview.md)]

This article explains how to enable the Dynamics 365 ERP apps plugin for Microsoft 365 Copilot Cowork. After you enable the plugin, users in your organization can interact with finance and operations data through the Copilot Cowork agent experience.

The Dynamics 365 ERP apps plugin connects Copilot Cowork to your finance and operations environment through the [Dynamics 365 ERP MCP server](copilot-mcp.md). After you enable the plugin, users can ask Copilot Cowork to retrieve ERP data, perform operations, and orchestrate business workflows that span ERP systems, email, documents, and other Microsoft 365 services.

## Prerequisites

Before you can enable the Dynamics 365 ERP apps plugin for Copilot Cowork, ensure you meet the following prerequisites.

### Microsoft 365 tenant requirements

Set up your Microsoft 365 tenant for Copilot Cowork. This setup includes enrollment in the Frontier preview program and Copilot licensing. Learn more about setting up Copilot Cowork in [Get started with Copilot Cowork](/microsoft-365/copilot/cowork/get-started).

#### Enable the Copilot Dataverse setting

The Dynamics 365 ERP apps plugin requires that the Dataverse integration setting is enabled in the Microsoft 365 Admin Center. To enable it:

1. Go to the [Microsoft 365 Admin Center](https://admin.microsoft.com).
1. Navigate to **Copilot** > **Settings**.
1. Enable **Dataverse data available in Microsoft 365 Copilot**.

Learn more in [Enable Microsoft 365 Admin Center Copilot Dataverse settings](/power-apps/maker/data-platform/data-platform-intelligence#enable-microsoft-365-admin-center-copilot-dataverse-settings).

> [!NOTE]
> After you enable the Dataverse setting, it can take up to one hour for the change to propagate due to caching. If the plugin still shows as disabled after enabling this setting, wait and try again later.

> [!IMPORTANT]
> If Dataverse is disabled, users see the plugin in the Copilot Cowork catalog but receive the message: *"Disabled by your organization's administrator."* This condition is common in EU countries or regions with Works Council requirements (such as Germany, France, and Sweden), where Dataverse might be disabled by default.

#### Dataverse user role requirement

Each user who uses the Dynamics 365 ERP apps plugin must have at least one role assigned in Dataverse. To assign the required role:

1. Open the [Power Platform Admin Center](https://admin.powerplatform.microsoft.com).
1. Go to **Environment Management** and select your environment.
1. Go to **Settings** > **Users**.
1. Find the user and ensure that the **Finance and Operations Basic User** role is assigned. This role is available as part of the Finance and Operations Virtual Entities Dataverse package.

### Finance and operations environment requirements

Your finance and operations environment must have the Dynamics 365 ERP MCP server enabled. Learn about setup instructions, including app version requirements, environment tier requirements, and feature enablement steps in [Use Model Context Protocol for finance and operations apps](copilot-mcp.md).

In addition to the standard MCP server prerequisites, you must allow the Copilot Cowork client app to access your MCP server. Learn more in [Step 2: Allow the Cowork client to access your MCP server](#step-2-allow-the-cowork-client-to-access-your-mcp-server).

## Enable the Dynamics 365 ERP apps plugin

After you meet the prerequisites, follow these steps to make the Dynamics 365 ERP apps plugin available to users.

### Step 1: Enable Copilot Cowork in your Microsoft 365 tenant

Ensure that your organization is enrolled in the Frontier preview program and that Copilot Cowork is enabled. Learn more in [Get started with Copilot Cowork](/microsoft-365/copilot/cowork/get-started).

### Step 2: Allow the Cowork client to access your MCP server

To allow the Cowork client to access your MCP server, follow these steps:

1. Go to your finance and operations environment.
1. Confirm that the Dynamics 365 ERP MCP server is enabled. Learn more in [Use Model Context Protocol for finance and operations apps](copilot-mcp.md).
1. Open the **Allowed MCP Clients** page.
1. Add the Cowork Client App ID: `6ab48b67-cd74-4ad4-81af-5932984589be`.

Learn more in [Allowed MCP clients](copilot-mcp.md#allowed-mcp-clients).

### Step 3: Enable the Dynamics 365 ERP apps plugin and connect to your environment in Copilot Cowork

To enable the Dynamics 365 ERP apps plugin and connect to your environment in Copilot Cowork, follow these steps:

1. Open [Copilot Cowork](https://m365.cloud.microsoft).
1. Open the **Browse plugins** dialog. Learn more about browsing and managing plugins in [Use plugins with Copilot Cowork](/microsoft-365/copilot/cowork/cowork-plugins).
1. In **All Plugins**, locate the **Dynamics 365 ERP Apps** plugin.
1. Select **Add to Cowork** to acquire the plugin.
1. After you acquire the plugin, open the connector settings (the gear icon next to the Dynamics 365 ERP Apps plugin).
1. Select your finance and operations environment from the list of available environments.
1. Complete the sign-in or consent flow if prompted.

After you connect the environment, the plugin's tools become available in your conversations.

> [!IMPORTANT]
> The Dynamics 365 ERP apps plugin respects all existing security roles and data access permissions. Users can only access data through Copilot Cowork that they can already access through the finance and operations applications.

## Common issues

The following table describes common issues and their resolutions.

| Symptom | Cause | Resolution |
|---|---|---|
| Plugin shows *"Disabled by your organization's administrator"* | The Copilot Dataverse setting is disabled in the Microsoft 365 Admin Center. | Ask your Microsoft 365 tenant administrator to enable the **Dataverse data available in Microsoft 365 Copilot** setting in the [Microsoft 365 Admin Center](https://admin.microsoft.com) under **Copilot** > **Settings**. Learn more in [Enable Copilot Dataverse settings](/power-apps/maker/data-platform/data-platform-intelligence#enable-microsoft-365-admin-center-copilot-dataverse-settings). After enabling, allow up to one hour for the change to propagate. |
| Plugin isn't visible in the Copilot Cowork catalog | Your tenant isn't enrolled in the Frontier preview program, or the Dynamics 365 ERP apps package isn't enabled for your tenant. | Verify that your tenant is enrolled in the [Frontier preview program](https://adoption.microsoft.com/en-us/copilot/frontier-program/). If the plugin is still not visible, contact Microsoft support. |
| Plugin is available but no environments are listed | No finance and operations environments were found. | Verify that your finance and operations environment is properly provisioned, that the MCP server feature is enabled, and that you have access to the environment. |
| Plugin shows *"Unable to connect"* after selecting an environment | The MCP server endpoint is unreachable or the Copilot Cowork client isn't authorized. | Verify that the MCP server is enabled and accessible, that you have appropriate security roles including the **Finance and Operations Basic User** role in Dataverse, and that the Cowork Client App ID (`6ab48b67-cd74-4ad4-81af-5932984589be`) is listed in **Allowed MCP Clients**. |

## Next steps

- [Use Copilot Cowork with Dynamics 365 ERP](../../fin-ops/copilot/use-copilot-cowork-erp.md)
- [Use Model Context Protocol for finance and operations apps](copilot-mcp.md)
- [Create AI tools with finance and operations business logic](copilot-ai-plugins.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
