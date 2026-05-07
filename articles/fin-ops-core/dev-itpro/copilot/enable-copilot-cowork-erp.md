---
title: Enable the Dynamics 365 ERP apps plugin for Copilot Cowork
description: Learn how to enable the Dynamics 365 ERP apps plugin for Microsoft Copilot Cowork so that users in your organization can work with finance and operations data through Cowork.
author: anupams
ms.author: anupams
ms.reviewer: ilebedev
ms.topic: how-to
ms.date: 05/07/2026
ms.update-cycle: 180-days
ms.custom: bap-template
ms.collection:
  - bap-ai-copilot
audience: Application User
ms.search.region: Global
ms.search.form:
---

# Enable the Dynamics 365 ERP apps plugin for Copilot Cowork

[!include [banner](../includes/banner.md)]

This article describes how to enable the Dynamics 365 ERP apps plugin for Microsoft Copilot Cowork so that users in your organization can interact with finance and operations data through the Cowork agent experience.

The Dynamics 365 ERP apps plugin connects Copilot Cowork to your finance and operations environment through the [Dynamics 365 ERP MCP server](copilot-mcp.md). After the plugin is enabled, users can ask Cowork to retrieve ERP data, perform operations, and orchestrate business workflows that span ERP systems, email, documents, and other Microsoft 365 services.

## Prerequisites

Before you can enable the Dynamics 365 ERP apps plugin for Copilot Cowork, the following prerequisites must be met.

### Microsoft 365 tenant requirements

Your Microsoft 365 tenant must be set up for Copilot Cowork. This includes enrollment in the Frontier preview program, Copilot licensing, and enabling Dataverse at the tenant level. For complete setup instructions, see [Get started with Copilot Cowork](/microsoft-365/copilot/cowork/get-started).

> [!NOTE]
> The Dynamics 365 ERP apps plugin requires that the Dataverse integration setting is enabled in the Microsoft 365 Admin Center. If Dataverse is disabled, users see the plugin in the Cowork catalog but receive the message: *"Disabled by your organization's administrator."* This is particularly common in EU countries with Works Council requirements (such as Germany, France, and Sweden), where Dataverse may be disabled by default.

### Finance and operations environment requirements

Your finance and operations environment must have the Dynamics 365 ERP MCP server enabled. For complete setup instructions, including app version requirements, environment tier requirements, and feature enablement steps, see [Use Model Context Protocol for finance and operations apps](copilot-mcp.md).

In addition to the standard MCP server prerequisites, the Copilot Cowork client app must be allowed access to your MCP server:

- Open the **Allowed MCP Clients** page in your finance and operations environment.
- Add the following client app ID:

  **Cowork Client App ID:** `6ab48b67-cd74-4ad4-81af-5932984589be`

For more information, see [Allowed MCP clients](copilot-mcp.md#allowed-mcp-clients).

## Enable the plugin

After the prerequisites are met, follow these steps to make the Dynamics 365 ERP apps plugin available to users.

### Step 1: Enable Copilot Cowork in your M365 tenant

Ensure that your organization is enrolled in the Frontier preview program and that Copilot Cowork is enabled. For details, see [Get started with Copilot Cowork](/microsoft-365/copilot/cowork/get-started).

### Step 2: Allow the Cowork client to access your MCP server

1. Open your finance and operations environment.
2. Confirm that the Dynamics 365 ERP MCP server is enabled. For instructions, see [Use Model Context Protocol for finance and operations apps](copilot-mcp.md).
3. Open the **Allowed MCP Clients** page.
4. Add the Cowork Client App ID: `6ab48b67-cd74-4ad4-81af-5932984589be`.

### Step 3: Enable the plugin and connect to your environment in Cowork

1. Open [Copilot Cowork](https://m365.cloud.microsoft).
2. Open the **Browse plugins** dialog. For details on browsing and managing plugins, see [Use plugins with Copilot Cowork](/microsoft-365/copilot/cowork/cowork-plugins).
3. Under **All Plugins**, locate the **Dynamics 365 ERP Apps** plugin.
4. Select **Add to Cowork** to acquire the plugin.
5. After the plugin is acquired, select the **gear icon** next to the Dynamics 365 ERP Apps plugin to open the connector settings.
6. Select your finance and operations environment from the list of available environments.
7. Complete the sign-in or consent flow if prompted.

After the environment is connected, the plugin's tools become available in your conversations.

> [!IMPORTANT]
> The Dynamics 365 ERP apps plugin respects all existing security roles and data access permissions. Users can only access data through Cowork that they can already access through the finance and operations application.

## Troubleshooting

The following table describes common issues and their resolutions.

| Symptom | Cause | Resolution |
|---|---|---|
| Plugin shows *"Disabled by your organization's administrator"* | Dataverse is disabled at the tenant level in the Microsoft 365 Admin Center. | Ask your M365 tenant administrator to enable Dataverse. This is particularly common in EU tenants where Works Council policies may require explicit admin opt-in. |
| Plugin isn't visible in the Cowork catalog | The Aether feature flight for D365 packages isn't enabled for your tenant, or Frontier isn't enabled. | Verify that your tenant is enrolled in the [Frontier preview program](https://adoption.microsoft.com/en-us/copilot/frontier-program/). Contact Microsoft support to verify that the D365 packages flight is enabled. |
| Plugin is available but no environments are listed | No finance and operations environments were found through the BAP discovery API. | Verify that your finance and operations environment is properly provisioned, that the MCP server feature is enabled, and that the user has access to the environment. |
| Plugin shows *"Unable to connect"* after selecting an environment | The On-Behalf-Of (OBO) token resolution failed, or the MCP server endpoint is unreachable. | Verify that the MCP server is enabled and accessible, that the user has appropriate security roles, and that the Cowork Client App ID (`6ab48b67-cd74-4ad4-81af-5932984589be`) is listed in **Allowed MCP Clients**. |

## Integration availability

When a user opens Copilot Cowork, the system automatically checks whether the Dynamics 365 ERP apps plugin is available. This check evaluates the following conditions in order:

1. **Tenant admin consent** &ndash; Is Dataverse enabled at the tenant level?
2. **Feature flight** &ndash; Is the D365 packages flight enabled for the tenant?
3. **Authentication** &ndash; Can an On-Behalf-Of token be acquired for the user?
4. **Environment discovery** &ndash; Are there finance and operations environments available through BAP?

If any check fails, the plugin is marked as unavailable, and the corresponding reason is communicated to the user.

## Next steps

- [Use Copilot Cowork with Dynamics 365 ERP](../../fin-ops/copilot/use-copilot-cowork-erp.md)
- [Use Model Context Protocol for finance and operations apps](copilot-mcp.md)
- [Create AI tools with finance and operations business logic](copilot-ai-plugins.md)
