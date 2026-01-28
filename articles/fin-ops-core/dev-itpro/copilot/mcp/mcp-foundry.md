---
title: Connect to the Dynamics 365 ERP MCP server with Microsoft Foundry
description: A guide for connecting an agent in Microsoft Foundry to the Dynamics 365 ERP MCP server
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 1/13/2026

---

# Connect to the Dynamics 365 ERP MCP server with Microsoft Foundry

This guide provides information on how to configure an agent in [Microsoft Foundry](/azure/ai-foundry/what-is-foundry?view=foundry) to work with the data and business logic of Dynamics 365 ERP applications by connecting to the Dynamics 365 ERP MCP server.

For more information on Microsoft Foundry, see [What is Microsoft Foundry?](/azure/ai-foundry/what-is-foundry?view=foundry), including links to getting started with agent development on the platform.

## Prerequisites

Before building an agent in Microsoft Foundry by using the **Dynamics 365 ERP MCP server**, make sure the **Dynamics 365 ERP MCP server** is enabled in your environment. For more information about enabling the server, see [Use Model Context Protocol for finance and operations apps](../copilot-mcp.md).

## Register an app in Microsoft Entra ID

### Step 1: Create a new app registration

1. Sign in to the [Azure portal](https://portal.azure.com) for your tenant.
1. Go to **App registrations**, and select **New registration**.
1. Enter a name like **Dynamics 365 ERP MCP agents**, or another name to identify the application.
1. Select an option for supported account types based on which accounts should access the server.
1. Select **Register**.

### Step 2: Define API permissions for the application

1. On the app registration, go to **Manage** > **API permissions**.
1. Select **Add a permission**.
1. On the **Microsoft APIs** tab, select **Dynamics ERP**.
1. Select **Delegated permissions**.
1. Select the following permission, and then select **Add permissions**.
  
| Permission | Description |
| ---------- | ----------- |
| mcp.tools | Access Microsoft Dynamics AX MCP tools as organization users |

### Step 3: Create a client secret

1. On the app registration, go to **Manage** > **Certificates & secrets**.
1. On the **Client secrets** tab, select **New client secret**.
1. Enter a description and your preferred expiration.
1. Select **Add**.
1. Copy the **Value** immediately. You can't access the value after the page is closed.

> [!NOTE]
> Keep the app registration open. You need to return to the page to get ID values and add a redirect URL generated later in the process.

## Configure Dynamics 365 finance and operations apps

### Step 1: Enable the MCP server

In the Dynamics 365 finance and operations apps client, make sure the **Dynamics 365 ERP Model Context Protocol server** feature is enabled in Feature management.

### Step 2: Grant permissions to the application

1. Go to **System administration** > **Setup** > **Microsoft Entra ID application** to open the **Microsoft Entra ID applications** page.
1. Select **New** on the action ribbon.
1. In the **Client ID** field of the new record, enter the **Application (client) ID** value of your new app, found on the **Overview** page of the Entra ID app registration.
1. In the **Name** field, enter a name for the registration.
1. In the **User ID** field, select a user that has the appropriate security role for permissions required for your agent to access in Dynamics 365 finance and operations apps.

### Step 3: Allow your new application to access the Dynamics 365 ERP MCP server

1. Go to **System administration** > **Setup** > **Allowed MCP clients** to open the **Allowed MCP clients** page.
1. Select **New** on the action ribbon.
1. Set the following values for the new record.

| Property | Value |
| -------- | ----- |
| **Name** | Provide a name for your MCP connection |
| **ClientId** | The **Application (client) ID** value of your new registered app from the Entra ID app registration |
| **Allowed** | `true` |

## Configure Microsoft Foundry

### Step 1: Add the MCP server as a custom tool

1. Go to [Microsoft Foundry](https://ai.azure.com).
1. Open your project, or create a new one.
1. Select **Build** to open the Agent builder.
1. On the navigation pane, select **Tools**.
1. Select **Connect a tool**.
1. On the **Custom** tab of the **Select a tool** dialog, select **Model Context Protocol (MCP)**, and then select **Create**.
1. In the **Add Model Context Protocol tool** dialog, enter the following detail, and then select **Connect**.

   | Property | Value |
   | -------- | ----- |
   | **Name** | Provide a unique name, like "Dynamics365ERP" |
   | **Remote MCP Server endpoint** | The URL of the remote MCP server for your Dynamics 365 finance and operations apps environment. This URL is formatted as `https://<your-environment-base-url>/mcp`. For example, `https://contoso.operations.dynamics.com/mcp`. |
   | **Authentication** | OAuth Identity Passthrough |
   | **Client ID** | Your Application (client) ID from your app registration configured in the previous steps |
   | **Client secret** | The **Value** of the client secret configured for your app registration |
   | **Token URL** | `https://login.microsoftonline.com/<your-tenant-ID>/oauth2/v2.0/token` |
   | **Auth URL** | `https://login.microsoftonline.com/<your-tenant-ID>/oauth2/v2.0/authorize` |
   | **Refresh URL** | `https://login.microsoftonline.com/<your-tenant-ID>/oauth2/v2.0/token` |
   | **Scopes** | `https://<your-environment-base-url>/.default` |

> [!NOTE]
> You can find your tenant ID on the **Overview** page of the Entra ID app registration created earlier.

### Step 2: Configure the redirect URL

1. On the **You've created a credential provider** dialog, copy the **Redirect URL** value.
1. Go back to the Entra ID app registration you created earlier.
1. Select **Authentication (Preview)** in the left navigation.
1. On the **Authentication (Preview)** page, select **Add Redirect URI**.
1. Select **Web**.
1. Enter the generated redirect URL in the **Redirect URI** field.
1. Under **Implicit grant and hybrid flows**, select both the options:
   - Access tokens (used for implicit flows)
   - ID tokens (used for implicit and hybrid flows)
1. Select **Configure**.

## Test the MCP connection

After you configure the MCP tool in Microsoft Foundry, you can create an agent to test the connection.

1. In the Agent Builder in Microsoft Foundry, select **Create agent**.
1. On the **Playground** tab, select a model from the available deployed models to manage the agent orchestration. Recommended models include `claude-sonnet-4-5` and `gpt-5-chat`.
1. Provide instructions in the **Instructions** field to guide the agent orchestration in using the MCP tools. See [Providing agent instructions](../build-agent-mcp.md#providing-agent-instructions) for more information.
1. **Save** the agent.
1. In the **Message the agent...** box, send a message. For example, send "Find the purchase requisition page."
