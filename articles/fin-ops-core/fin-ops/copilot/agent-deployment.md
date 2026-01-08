---
title: How to deploy and setup Agents in Data Verse
description: This article describes how to use the agent deployment wizard for IT admins in the Power Platform Admin center  
author: cabeln
ms.author: cabeln
ms.topic: concept-article
ms.date: 01/07/2026
ms.update-cycle: 180-days
ms.custom:
ms.reviewer:  
audience: Application User
ms.collection: 
 - bap-ai-copilot
---


# (Preview) Deploy Dynamics 365 agents using the Agent deployment wizard

[!include [preview-banner](../includes/preview-banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The Agent deployment wizard in Copilot Hub is the centralized deployment experience for Dynamics 365 agents. It guides administrators through a secure, validated process to deploy Microsoft‑provided agents into Power Platform and Dynamics 365 environments.
The wizard provides a consistent deployment experience across all Dynamics 365 agents, while agent‑specific configuration and setup guidance is documented separately for each agent.

Access the deployment wizard in the [Power Platform Admin Center](https://aka.ms/InstallD365Agents)

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

## Common deployment steps


