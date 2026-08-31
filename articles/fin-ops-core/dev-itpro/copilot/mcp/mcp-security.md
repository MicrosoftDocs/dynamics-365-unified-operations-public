---
title: Security for Dynamics 365 ERP MCP
description: Learn how authentication, authorization, business logic, and data handling work with the Dynamics 365 ERP MCP server
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom:
  - bap-template
ms.date: 8/17/2026

---

# Security for Dynamics 365 ERP MCP

[!INCLUDE [banner](../../../../includes/banner.md)]

The Dynamics 365 ERP MCP server lets agent clients connect to Dynamics 365 finance and operations apps through the Model Context Protocol (MCP). The interaction model is different from traditional integrations because requests are initiated through an AI assistant, but the security model doesn't change. MCP requests are governed by the same authentication, authorization, business logic, and data controls that apply to other finance and operations app experiences.

## Security model

The MCP server is built on the same foundation as the existing API integration framework for finance and operations apps. It doesn't create a separate security boundary or grant permissions independently from the application. Instead, it evaluates each request in the context of the authenticated user and the finance and operations environment that the user is connected to.

The security model has four important properties:

- Requests are authenticated before an MCP operation is attempted.
- Finance and operations security, not the MCP server, enforces authorization.
- Business logic, validations, and workflows aren't bypassed.
- The MCP server doesn't store customer data.

### Authentication

Every MCP request requires an authenticated user. The MCP server doesn't provide an anonymous or shared-service path for accessing finance and operations data.

Operations run under the authenticated user's identity and security context in finance and operations apps. An action that an agent takes through the MCP server is therefore attributable to the user who initiated the request, similar to an action that the same user takes in the finance and operations client.

The authenticated identity depends on the agentic pattern:

- For chat or delegated agents, set the agent configuration to run on behalf of the user who is chatting with the agent.
- For autonomous agents, no human user chats with the agent at the time of the request. The autonomous agent has its own identity, and that identity is the authenticated user making the request.

In both cases, permissions are applied based on the identity that's used for user authentication.

### Allowed MCP clients

Administrators can also control which agent clients are allowed to connect to the MCP server. When you enable the Dynamics 365 ERP MCP server in your environment, choose which agent platforms can access the server. By default, only the following platforms can access the MCP server:

| Platform | Client ID |
| -------- | --------- |
| Microsoft Copilot Studio | 7ab7862c-4c57-491e-8a45-d52a7e023983 |
| Visual Studio Code | aebc6443-996d-45c2-90f0-388ff96faa56 |
| Microsoft Cowork | 6ab48b67-cd74-4ad4-81af-5932984589be |
| Finance Agent | 8c1a9936-578e-4d13-9bd9-9afe53ef7de8 |
| Finance Agent (Sydney) | fb8d773d-7ef8-4ec0-a117-179f88add510 |

Grant access to any other agent platforms that need to access the MCP server. To add new agent platforms, complete the following steps:

1. Register the application in Microsoft Entra ID. For more information, see [Register an application in Microsoft Entra ID](/entra/identity-platform/quickstart-register-app).
1. Add the registered client ID value in the **Allowed MCP clients** form, and set the **Allowed** property to `true`.

### Authorization and access control

The security configuration of finance and operations apps enforces authorization. When a user connects to the MCP server, the server calls finance and operations APIs by using the user's credentials. The roles, duties, privileges, record-level security, and data security policies assigned to that user apply to every request.

The MCP server doesn't elevate privilege. A user's access to finance and operations apps through the MCP server applies the same security roles, duties, and privileges that are assigned to the user in the finance and operations security configuration. The authenticated user can never do more through the MCP server than they're able to do through the finance and operations application client.

If administrators want to change what a user can access or modify through the MCP server, they should update the same security roles, duties, privileges, and policies that they use for other finance and operations channels.

### Business logic and validation

The MCP server isn't an execution bridge into the database. Operations go through standard finance and operations APIs, such as OData endpoints, custom services, and server APIs. The MCP server doesn't use direct database access to read or modify business data.

Because the MCP server uses the same application APIs as other supported channels, finance and operations business logic is preserved. Validations, workflows, and server-side business rules run as they do when the user works in the finance and operations client or when another integration channel calls the same APIs. A transaction that would be rejected in the application client is also rejected when attempted through the MCP server.

### Deployment and data handling

The MCP server runs within the finance and operations environment that the organization configures for MCP access. The MCP server isn't a separate shared service that stores finance and operations business data outside the environment.

The MCP server acts as a pass-through API layer between the MCP client and finance and operations apps. It returns results to the calling client for the duration of the request, but doesn't store customer data. Customer data remains in finance and operations apps and remains subject to the organization's existing retention, compliance, and data governance controls. The MCP server doesn't change where finance and operations business data is mastered or retained. Any data movement or retention outside the customer's finance and operations environment would be dependent on the data storage and retention policies of the agent client (for example, Microsoft Copilot Studio, Claude, Microsoft Foundry), and/or the client's access to other external systems. Ensure you audit the agent client's permissions to move data to other systems and the data retention policies.

Organizations also control which AI service and agent client they use with the MCP server. For example, an organization can configure an MCP client to use Azure OpenAI Service within its own compliance boundary instead of using a public assistant service.

### Administrators

- Review the roles, duties, and privileges assigned to users who access finance and operations apps through MCP clients.
- Use the **Allowed MCP clients** configuration to control which agent clients can connect to the MCP server.
- Configure the agent client and AI service according to the organization's compliance and data handling requirements.
- Review agent instructions to ensure agents don't encourage users to attempt actions that are outside their assigned finance and operations responsibilities.
