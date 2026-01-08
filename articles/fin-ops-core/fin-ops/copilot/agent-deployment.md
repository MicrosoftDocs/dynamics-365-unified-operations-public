---
title: Deploy and set up Dynamics 365 agents using the Agent deployment wizard
description: This article explains how IT administrators use the Agent deployment wizard in the Power Platform Admin Center to deploy and set up Microsoft Dynamics 365 agents in Dataverse environments.
author: cabeln
ms.author: cabeln
ms.topic: concept-article
ms.date: 01/07/2026
ms.update-cycle: 180-days
ms.custom:
ms.reviewer:  
audience: Administarors
ms.collection: 
 - bap-ai-copilot
---


# (Preview) Deploy Dynamics 365 agents using the Agent deployment wizard

[!include [preview-banner](../includes/preview-banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The Agent deployment wizard in Copilot Hub is the centralized deployment experience for Dynamics 365 agents. It guides administrators through a secure, validated process to deploy Microsoft‑provided agents into Power Platform and Dynamics 365 environments.
The wizard provides a consistent deployment experience across all Dynamics 365 agents, while agent‑specific configuration and setup guidance is documented separately for each agent.

> [!NOTE]
> Access the deployment wizard in the [Power Platform Admin Center](https://aka.ms/InstallD365Agents)
>
> A separate [public preview experience in Power Platform Admin Center](https://aka.ms/InstallD365AgentsPreview) provides early access to upcoming enhancements for the Agent deployment wizard.


:::image type="content" source="media/agent-deployment-wizard-ppac.png" alt-text="Dynamics 365 agent deployment wizard landing page." lightbox="media/copilot-help-welcome.png":::

## Purpose of the Agent deployment wizard

Dynamics 365 agents are shipped as managed solutions that depend on platform features, security roles, and environment configuration.

The Agent deployment wizard helps you:

- Discover all Dynamics 365 agents available for deployment
- Validate that a target environment is ready
- Apply required environment‑level configuration
- Deploy agents safely and consistently
- Monitor deployment status and troubleshoot failures

By using the wizard, you find a one stop guidance and deployment tool and ensure deployments comply with Power Platform governance, security, and lifecycle best practices.

## What the deployment wizard deploys

The deployment wizard is designed specifically for Microsoft‑provided Dynamics 365 agents, such as:

- [Supplier Communications agent](https://learn.microsoft.com/dynamics365/supply-chain/procurement/supplier-com-agent-setup)
- [Account Reconciliation agent](https://learn.microsoft.com/dynamics365/finance/general-ledger/configure-acct-recon-agent)
- [Expense agent](https://learn.microsoft.com/dynamics365/project-operations/expense/expense-agent-setup)
- [Time agent](https://learn.microsoft.com/dynamics365/project-operations/time/enable-time-entry-agent)
- [Approvals agent](https://learn.microsoft.com/dynamics365/project-operations/approvals/approvals-agent-admin-setup)

Each agent has its own deployment and post‑deployment guidance that explains functional setup, permissions, and usage. This article focuses only on the common deployment experience.

## Who should use this tool

This tool is intended for:

- IT teams responsible for environment readiness and rollout
- Power Platform administrators
- Agent administrators
- Dynamics 365 administrators

## Access the Agent deployment wizard

To access the deployment wizard:

1. Open [Copilot Hub in Power Platform Admin Center and select Dynamics 365](https://aka.ms/InstallD365Agents).
1. Select the target environment.
1. Choose a Dynamics 365 agent.
1. Select Add.
This action launches the Agent deployment wizard for the selected agent.

## Common deployment steps for Dynamics 365 agents

Deploying a Dynamics 365 agent using the Agent deployment wizard in Copilot Hub follows a consistent set of administrative tasks. While each agent requires additional, agent‑specific configuration, the steps below describe the common deployment flow that administrators complete for every agent.
These steps are typically completed once per agent, per environment.

### Check prerequisites

The deployment wizard first helps to validates that the target environment meets all required prerequisites for the selected agent.
This includes checking that the required applications and Dataverse packages for Copilot and agent assets are installed in the environment. In most cases, these packages are installed automatically as part of the deployment process.

Additional prerequisite validations include:

- Copilot enablement and generative AI feature settings
- Message consumption settings for Copilot
- Data Loss Prevention (DLP) policies
- Advanced connector policies, if applicable
- Virtual entity refresh, when required by the agent

Any missing, misconfigured, or blocked prerequisites are clearly surfaced in the wizard, along with guidance on how to resolve them before proceeding.

### Set up the agent identity

Each agent runs under a dedicated agent user identity. In this step, the administrator selects or creates this identity.

Typical tasks include:

- Identifying the agent user account
- Creating the agent identity in the Microsoft 365 admin center, if it does not already exist
- Assigning the required product licenses to the agent user
- Adding the agent user to the Dataverse environment
- Assigning the required Dataverse security roles

For Finance and Operations (FnO) agents, additional steps are required:

- Adding the agent user to the FnO environment
- Assigning the relevant FnO security roles

This ensures the agent has the correct permissions to access data and perform its intended actions.

### Connect the agent

The Connect agent step guides the administrator through configuring the required connections that allow the agent to interact with Dataverse and other services.

In this step, the administrator:

- Creates the required Dataverse connections using the agent identity
- Adds these connections to the agent’s connection references
- Verifies that all required connectors are approved under existing governance policies
- Activates all Power Automate flows used by the agent

Once completed, the agent is fully connected to the services it depends on.

### Configure mailboxes (if applicable)

Some agents rely on mailboxes to send or receive messages.

For such agents, the deployment wizard includes an optional Configure mailbox step, which helps administrators:

- Set up server-side synchronization for the required mailboxes
- Configure mailbox-related environment variables, if needed

This step only appears for agents that require mailbox integration.

### Enable the agent

The final step makes the agent available for use.

This typically includes:

- Publishing the agent bot in Copilot Studio
- Verifying that the agent is enabled and available in the target environment

For Finance and Operations agents, this step also includes:

- Enabling the required feature in FnO Feature Management

Once enabled, the agent is active and ready for use.

### Next steps

After completing these common deployment steps, follow the agent‑specific deployment guidance to configure business logic and bring the agent into service. These actions are performed in the business application using [agent management](agent-mgmt.md).

## Support and feedback

This feature is currently in preview. We welcome your feedback and will use it to improve the Agent deployment wizard. Report any issues or suggestions using the standard Dynamics 365 support channels.