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
