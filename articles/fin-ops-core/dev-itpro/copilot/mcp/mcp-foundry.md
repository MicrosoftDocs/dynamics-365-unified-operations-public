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

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This guide provides information on how to configure an agent in [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-foundry?view=foundry) to work with the data and business logic of Dynamics 365 ERP applications by connecting to the Dynamics 365 ERP MCP server.

## Prequisites
Before building an agent in Microsoft Foundry with the **Dynamics 365 ERP MCP server**, you must ensure the **Dynamics 365 ERP MCP server** is enabled in your environment. Learn more about enabling the server in [Use Model Context Protocol for finance and operations apps](./copilot-mcp.md).

## Register an app in Microsoft Entry ID
1. Create a new app registration.
   - Sign in to the [Azure portal](https://portal.azure.com) for your tenant.
   - Navigate to **App registrations**, and select **New registration**.
   - Provide a name like **Dynamics 365 ERP MCP agents**, or another name to identify the application.
   - Select an option for supported account types based on which accounts should be able to access the server.
   - Select **Register**.
2. Define API permissions for the application.
   - On the app registration, navigate to **Manage** >> **API permissions**.
   - Click **Add a permission**.
   - On the **Microsoft APIs** tab, select **Dynamics ERP**.
   - Select **Delegated permissions**.
   - Select the following permissions, then select **Add permissions**.
  
   | Permission | Description |
   | ---------- | ----------- |
   | AX.FullAccess | Access Dynamics AX online as organization users |
   | CustomService.FullAccess | Access Dynamics AX Custom Service |
   | mcp.tools | Access Microsoft Dynamics AX MCP tools as organization users |
   | Odata.FullAccess | Access Dynamics AX data |

3. Create a client secret
   - On the app registration, navigate to **Manage** >> **Certificates & secrets**.
   - On the **Client secrets** tab, select **New client secret**.
   - Provide a description like **Microsoft Foundry agents** and your preferred expiration.
   - Select **Add**.
   - Copy the **Value** immediately. The value won't be available after the form is closed.

Leave the app registration open. You will need to return to the page to get ID values and add a redirect URL generated later in the process.

## Configure Dynamics 365 finance and operations apps
1. In the Dynamics 365 finance and operations apps client, ensure the **Dynamics 365 ERP Model Context Protocol server** feature is enabled in Feature Management.
2. Grant permissions to the application.
   - Open the **Microsoft Entra ID applications** form (System administration >> Setup >> Microsoft Entra ID applications).
   - Select **New** on the action ribbon.
   - In the **Client ID** field of the new record, enter the **Application (client) ID** value of your new app, found on the **Overview** page of the Entra ID app registration.
   - In the **Name** field, provide a name for the registration.
   - In the **User ID** field, select a user that has the appropriate security role for permissions required for your agent to access in Dynamics 365 finance and operations apps.
3. Allow your new application to access the Dynamics 365 ERP MCP server.
   - Open the **Allowed MCP clients** form (System administration >> Setup >> Allowed MCP clients).
   - Select **New** on the action ribbon.
   - In the **Name** field of the new record, enter a name for your MCP connection.
   - In the **ClientId** field, enter the **Application (client) ID** value of your new registered app from the Entra ID app registration.
   - Set the **Allowed** value to **true**.

## Configure Microsoft Foundry

### Add the MCP server as a custom tool
1. Navigate to [Microsoft Foundry](ai.azure.com).
2. Open your project, or create a new one.
3. Select **Build** to open the Agent Builder.
4. On the navigation pane, select **Tools**.
5. Select **Connect a tool**.
6. On the **Custom** tab of the **Select a tool** dialog, select **Model Context Protocol (MCP)**, then select **Create**.
7. In the **Add Model Context Protocol tool** dialog, enter the following detail, then click **Connect**.

   | Property | Value |
   | -------- | ----- |
   | **Name** | Provide a unique name, like "Dynamics365ERP" |
   | **Remote MCP Server endpoint** | The URL of the remote MCP server for your Dynamics 365 finance and operations apps environment. This is formatted as `https://<your-environment-base-url>/mcp`. For example, `https://contoso.operations.dynamics.com/mcp`. |
   | **Authentication** | OAuth Identity Passthrough |
   | **Client ID** | Your Application (client) ID from your app registration configured in the previous steps |
   | **Client secret** | The client secret configured for your app registration |
   | **Token URL** | `https://login.microsoftonline.com/<your-tenant-ID>/oauth2/v2.0/token` -- Note: You can find your tenant ID on the **Overview** page of the Entra ID app registration. |
   | **Auth URL** | `https://login.microsoftonline.com/<your-tenant-ID>/oauth2/v2.0/authorize` |
   | **Refresh URL** | `https://login.microsoftonline.com/<your-tenant-ID>/oauth2/v2.0/token` |
   | **Scopes** | `https://<your-environment-base-url>/.default` |

### Configure the Redirect URL
After configuring the MCP server in Microsoft Foundry, a redirect URL is generated that must be configured for your Entra ID app registration.

1. On the **You've created a credential provider** dialog, copy the **Redirect URL** value.
2. Navigate back to the Entra ID app registration you created earlier.
3. Select **Authentication (Preview)** on the left navigation.
4. On the **Authentication (Preview)** page, select **Add Redirect URI**.
5. Select **Web**.
6. Enter the generated redirect URL in the **Redirect URI** field.
7. Under **Implicit grant and hybrid flows**, select both the following options:
   - Access tokens (used for implicit flows)
   - ID tokens (used for implicit and hybrid flows)
8. Select **Configure**.

## Test the MCP connection
With the MCP tool configured in Microsoft Foundry, you can now create an agent to test the connection.

1. In the Agent Builder in Microsoft Foundry, select **Create agent**.
2. On the **Playground** tab, select a model from the available deployed models to manage the agent orchestration. Recommended models include `claude-sonnet-4-5` and `gpt-5-chat`.
3. Provide instructions in the **Instructions** field to guide the agent orchestration in using the MCP tools. See [Providing agent instructions](../copilot/build-agent-mcp.md) for more information.
4. **Save** the agent.
5. In the **Message the agent...** box, send a message. For example, send "Find the Purchase Requsition form."
