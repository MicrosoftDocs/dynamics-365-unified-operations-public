---
title: Enable the Dynamics 365 ERP apps plugin for Copilot Cowork
description: Learn how to enable the Dynamics 365 ERP apps plugin for Microsoft Copilot Cowork so that users in your organization can work with finance and operations data through Cowork.
author: anupams
ms.author: anupams
ms.reviewer: johnmichalak
ms.topic: how-to
ms.date: 10/27/2026
ms.update-cycle: 180-days
ms.custom: bap-template
ms.collection:
  - bap-ai-copilot
audience: Application User
ms.search.region: Global
ms.search.form:
---

# Enable the Dynamics 365 ERP apps plugin for Copilot Cowork

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to enable the Dynamics 365 ERP apps plugin for Microsoft Copilot Cowork. After you enable the plugin, users in your organization can interact with finance and operations apps data through the Copilot Cowork agent experience.

The Dynamics 365 ERP apps plugin connects Copilot Cowork to your finance and operations apps environment through the [Dynamics 365 ERP MCP server](copilot-mcp.md). After you enable the plugin, users can ask Copilot Cowork to retrieve ERP data, perform operations, and orchestrate business workflows that span ERP systems, email, documents, and other Microsoft 365 services.

## Prerequisites

Before you can enable the Dynamics 365 ERP apps plugin for Copilot Cowork, ensure you meet the following prerequisites.

### Microsoft 365 tenant requirements

Before users can install and use the Dynamics 365 ERP apps plugin, ensure that:

- Each user has an active Microsoft 365 Copilot license.
- An administrator enabled Copilot Cowork in the Microsoft 365 admin center.
- Usage-based billing and Copilot Credits are configured for the users who use the plugin. A billing policy can override whether the plugin is discoverable. If the plugin is discoverable but billing isn't configured for a user, the user must request access.

Learn more about setting up Copilot Cowork in [Get started with Copilot Cowork](/microsoft-365/copilot/cowork/get-started).

Copilot Cowork uses Anthropic models as a subprocessor for some capabilities. This capability is off by default in the European Union (EU), European Free Trade Association (EFTA), and United Kingdom (UK), so administrators in those regions must enable it for their users. Anthropic models aren't available in government or sovereign clouds. Learn more in [Anthropic as a subprocessor for Microsoft Online Services](/microsoft-365/copilot/connect-to-ai-subprocessor).

#### Enable the Copilot Dataverse setting

The Dynamics 365 ERP apps plugin requires that the Dataverse integration setting is enabled in the Microsoft 365 Admin Center. To enable it:

1. Go to the [Microsoft 365 Admin Center](https://admin.microsoft.com).
1. Navigate to **Copilot** > **Settings**.
1. Enable **Dataverse data available in Microsoft Copilot**.

Learn more in [Enable Microsoft 365 Admin Center Copilot Dataverse settings](/power-apps/maker/data-platform/data-platform-intelligence#enable-microsoft-365-admin-center-copilot-dataverse-settings).

> [!NOTE]
> After you enable the Dataverse setting, it can take up to one hour for the change to propagate due to caching. If the plugin still shows as disabled after enabling this setting, wait and try again later.

> [!IMPORTANT]
> The Dataverse setting controls whether the plugin is offered and eligible in Copilot Cowork. It doesn't control how the plugin accesses ERP data. If Dataverse is disabled, users see the plugin in Copilot Cowork but receive the message: *"Your admin has disabled this plugin."* This condition is common in EU countries or regions with Works Council requirements (such as Germany, France, and Sweden), where Dataverse might be disabled by default.

### Finance and operations apps license requirements

Each user who installs or uses the Dynamics 365 ERP apps plugin must have a qualifying Dynamics 365 license for finance and operations apps.

Qualifying licenses include:

- Dynamics 365 Finance
- Dynamics 365 Supply Chain Management
- Dynamics 365 Commerce or Retail
- Dynamics 365 Human Resources or Talent
- Dynamics 365 Operations
- Dynamics 365 Project Operations
- Applicable Attach, Government, Premium, trial, and Team Member variants of these licenses
- Legacy Dynamics AX or ERP full-user licenses
- Finance regulatory service licenses

The following licenses and add-ons don't qualify:

- On-premises ERP licenses
- Device-only plans
- Environment, sandbox, storage, or capacity add-ons
- Licenses for Dynamics 365 products that aren't finance and operations apps

### Finance and operations apps environment requirements

The Dynamics 365 ERP apps plugin uses the dynamic Dynamics 365 ERP MCP server. Your finance and operations apps environment must meet the following requirements:

- The product version must be at least 10.0.47, 10.0.46 PQU-2, or 10.0.45 PQU-7.
- The environment must be Tier 2 or above, or a Unified Developer Environment. Cloud Hosted Environments (CHE) and on-premises environments aren't supported.
- The **Dynamics 365 ERP Model Context Protocol server** feature must be enabled in Feature Management. The feature is enabled by default in supported environments.

> [!NOTE]
> The earlier static Dynamics 365 ERP MCP server, which has 13 predefined tools, retires on October 1, 2026. Copilot Cowork uses the dynamic Dynamics 365 ERP MCP server.

Learn more about the server requirements in [Use Model Context Protocol for finance and operations apps](copilot-mcp.md).

In addition to the standard MCP server prerequisites, you must allow the Copilot Cowork client app to access your MCP server. Learn more in [Step 2: Allow the Cowork client to access your MCP server](#step-2-allow-the-cowork-client-to-access-your-mcp-server).

### Finance and operations apps security requirements

Each user must have the appropriate security roles and privileges in the finance and operations apps environment. The Dynamics 365 ERP apps plugin exposes only the entities, forms, fields, actions, and business data that the authenticated user's finance and operations apps security roles permit.

## Enable the Dynamics 365 ERP apps plugin

After you meet the prerequisites, follow these steps to make the Dynamics 365 ERP apps plugin available to users.

### Step 1: Enable Copilot Cowork in your Microsoft 365 tenant

Ensure that Copilot Cowork is enabled for your organization, users have Microsoft 365 Copilot licenses, and usage-based billing and Copilot Credits are configured. If your organization is in the EU, EFTA, or UK, enable Anthropic models for your users. Learn more in [Get started with Copilot Cowork](/microsoft-365/copilot/cowork/get-started).

### Step 2: Allow the Cowork client to access your MCP server

To allow the Cowork client to access your MCP server, follow these steps:

1. Go to your finance and operations apps environment.
1. Confirm that the Dynamics 365 ERP MCP server is enabled. Learn more in [Use Model Context Protocol for finance and operations apps](copilot-mcp.md).
1. Open the **Allowed MCP Clients** page.
1. Add the Cowork Client App ID: `6ab48b67-cd74-4ad4-81af-5932984589be`.

Learn more in [Allowed MCP clients](mcp/mcp-security.md#allowed-mcp-clients).

> [!NOTE]
> Changes to the allowed MCP clients can take up to one minute to take effect.

### Step 3: Enable the Dynamics 365 ERP apps plugin and connect to your environment in Copilot Cowork

To enable the Dynamics 365 ERP apps plugin and connect to your environment in Copilot Cowork, follow these steps:

1. Open [Copilot Cowork](https://m365.cloud.microsoft).
1. Select the **+** button, select **Customize**, and then select **Discover**. To learn more about browsing and managing plugins, see [Use plugins with Copilot Cowork](/microsoft-365/copilot/cowork/cowork-plugins).
1. Locate the **Dynamics 365 ERP apps** plugin, and then select **Install**.
1. After the plugin shows **Installed**, confirm that it appears under **My plugins**.
1. Open the **Sources & Skills** panel.
1. Find the **Finance & Operations** connector, and then select **Configure**.
1. Select your compatible finance and operations apps environment.
1. Complete the sign-in or consent flow.

After you connect the environment, the plugin's tools become available in your conversations.

> [!IMPORTANT]
> The Dynamics 365 ERP apps plugin respects all existing security roles and data access permissions. Users can only access data through Copilot Cowork that they can already access through the finance and operations applications.

To remove a plugin that you installed, find it under **My plugins**, and then select **Uninstall**.

### Request access to the plugin

If an administrator or billing policy prevents installation, the plugin might show **Request access** instead of **Install**. Select **Request access** to send a request to your administrator. The action changes to **Requesting** while the request is submitted and then to **Check status**. The plugin shows **Unavailable** and can't be installed until the request is approved and the required licensing and billing policies are configured.

### Use an administrator-deployed plugin

An administrator can deploy the Dynamics 365 ERP apps plugin to selected users or groups from the Microsoft 365 admin center. An administrator-deployed plugin:

- Appears automatically under **My plugins**.
- Is labeled as managed by your organization.
- Can't be uninstalled by users.
- Still requires each user to configure and sign in to the **Finance & Operations** connector.

Administrator deployment doesn't bypass Microsoft 365 Copilot licensing, finance and operations apps licensing, usage-based billing, or finance and operations apps security requirements.

### Use the plugin on Copilot Cowork surfaces

After you install the plugin and configure the Finance & Operations connector, you can use it in Copilot Cowork on the web, in Outlook and Teams, in the Microsoft Copilot desktop app for Windows and Mac, and in the Microsoft Copilot mobile app. Use the Cowork web experience to install the plugin and configure its connector.

## Common issues

The following table describes common issues and their resolutions.

| Symptom | Cause | Resolution |
|---|---|---|
| Plugin shows *"Your admin has disabled this plugin."* | The Copilot Dataverse setting is disabled, or an administrator policy blocks the plugin. | Ask your Microsoft 365 tenant administrator to enable **Dataverse data available in Microsoft Copilot** under **Copilot** > **Settings**, or select **Request access** if that option is available. After the setting is enabled, allow up to one hour for the change to propagate. |
| Plugin isn't visible under **Discover** | The plugin isn't available to the user because of an administrator deployment policy, licensing, or billing configuration. | Verify that the user has Microsoft 365 Copilot and a qualifying finance and operations apps license, and that usage-based billing is configured. An administrator can deploy the plugin from the Microsoft 365 admin center. |
| Plugin shows *"You don't have a license to install this plugin."* | The user doesn't have a qualifying finance and operations apps license. | Assign a qualifying Dynamics 365 finance and operations apps license, allow the licensing change to propagate, and retry installation. |
| Plugin shows *"No compatible Dynamics environment found in your tenant."* | The environment isn't a supported cloud finance and operations apps environment, its metadata isn't available yet, the user doesn't have access to it, or the user doesn't have a qualifying finance and operations apps license. | Verify that the environment is Tier 2 or above or a Unified Developer Environment, runs a supported version, and isn't a CHE or on-premises environment. Confirm that the user has a qualifying license and access to the environment, and then retry after environment metadata is available. |
| Plugin shows *"Unable to connect"* after an environment is selected | The MCP server endpoint is unreachable, the Cowork client isn't authorized, or the user lacks the required finance and operations apps permissions. | Verify that the dynamic MCP server is enabled and accessible, that the user has the appropriate finance and operations apps security roles, and that the Cowork Client App ID (`6ab48b67-cd74-4ad4-81af-5932984589be`) is listed in **Allowed MCP Clients**. |

## Next steps

- [Use Copilot Cowork with Dynamics 365 ERP](../../fin-ops/copilot/use-copilot-cowork-erp.md)
- [Use Model Context Protocol for finance and operations apps](copilot-mcp.md)
- [Create AI tools with finance and operations business logic](copilot-ai-plugins.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
