---
title: Connect to the Dynamics 365 ERP MCP server with VS Code
description: A guide for connecting an agent in Visual Studio Code to the Dynamics 365 ERP MCP server
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 12/17/2025

---

# Connect to the Dynamics 365 ERP MCP server with Visual Studio Code

The Model Context Protocol (MCP) is an open standard for connecting agent clients to various data systems like Dynamics 365 finance and operations apps. One of the benefits of the standard protocol is the ability to use the MCP server with any agent client that supports the standard. This guide provides information on how to configure GitHub Copilot in Visual Studio Code to connect to the Dynamics 365 ERP MCP server.

For more information on MCP support in Visual Studio Code, see [Use MCP servers in VS Code](https://code.visualstudio.com/docs/copilot/customization/mcp-servers).

## Prequisites
Before building an agent in Visual Studio Code with the **Dynamics 365 ERP MCP server**, you must complete the following:
1. Ensure the **Dynamics 365 ERP MCP server** is enabled in your environment. Learn more about enabling the server in [Use Model Context Protocol for finance and operations apps](../copilot-mcp.md).
2. Ensure the `VSCode` client ID is allowed in the **Allowed MCP clients** list. Learn more in [Allowed MCP clients](../copilot-mcp.md#allowed-MCP-clients).
3. Install the latest version of [Visual Studio Code](https://code.visualstudio.com/download).
4. Enable access to [Copilot](https://code.visualstudio.com/docs/copilot/setup).

## Configure the MCP server
Follow the steps below to connect Visual Studio Code to the MCP server.

1. In Visual Studio Code, run command (Ctrl + Shift + P), and select **MCP: Add Server...**.
2. Select **HTTP (HTTP or Server-Sent Events)** to connect to the remote MCP server.
3. In the **URL of the MCP server** input, enter `<Finance-and-Operations-base-URL-value>/mcp`. For example: `https://contoso.operations.dynamics.com/mcp`.
4. Provide a **Server ID** value, or accept the default.
5. Once the Server ID is entered, the mcp.json file is created with the server configuration. This configuration shows the server status and the number of tools retrieved from the server. You can also start or restart the connection to the server as needed.
6. When the server is started, you then need to authenticate to the server using the credentials for your finance and operations apps environment. When the dialog displays stating that the MCP server definition wants to authenticate to the environment, select **Allow**. You will then need to enter your credentials for the environment that will be used to connect to the MCP server from Visual Studio Code.

## Configure the agent chat
After configuring Visual Studio Code to connect to the MCP server, you can use the agent chat with GitHub Copilot to prompt the agent and receive responses from the Dynamics 365 ERP MCP server.

1. In Visual Studio Code, run command (Ctrl + shift + P) and select **Chat: Open Chat**.
2. In the chat pane, select **Agent** from the mode selection list.
3. In the **Model** selection list, select your preferred model. The recommended model for the Dynamics 365 ERP MCP server is **Claude Sonnet 4.5**.
4. Select the tools that you want to use for the agent.
   - In the agent chat box, select the **Configure tools** icon.
   - Uncheck all tools you don't want to use for the agent. For example, uncheck the Built-In tools that aren't needed for your agent.
5. Begin prompting in the chat box.
