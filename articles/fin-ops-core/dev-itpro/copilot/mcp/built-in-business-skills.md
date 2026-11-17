---
title: Create built-in business skills (preview)
description: Learn how developers create built-in business skills as Application Object Tree (AOT) elements in Visual Studio and deploy them with finance and operations apps so that agents can use them through the Dynamics 365 ERP MCP server.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 11/17/2026
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: twheeloc
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Create built-in business skills (preview)

[!INCLUDE [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Built-in business skills are [business skills](erp-business-skills.md) that developers create in Visual Studio as elements in the Application Object Tree (AOT). Microsoft, independent software vendors (ISVs), and customer developers can create built-in skills to give agents the process guidance that they need to work with the pages, data entities, tables, classes, and other objects in a solution. Agents retrieve built-in skills through the [Dynamics 365 ERP MCP server](../copilot-mcp.md) in the same way that they retrieve custom skills.

Built-in skills complement [AI descriptions](mcp-ai-descriptions.md). AI descriptions describe facts about individual data entities, fields, and forms. Built-in skills describe the business processes that use those objects.

## Why create built-in skills

A business skill often references pages, data entities, and other application objects by name. When you create a skill as an AOT element, the skill ships in the same deployable package as the application objects that it describes. This approach helps prevent version skew, where an application object changes but the skill that describes it isn't updated, or a skill is deployed that references an object that doesn't exist in the environment.

Built-in skills are a good fit for:

- General processes that apply to every organization that uses your solution.
- Guidance that depends on specific versions of the pages, data entities, and other objects in your solution.

To capture processes that are specific to your organization, or guidance that only certain users should have access to, create a custom business skill on the **Business skills (preview)** page instead. For more information, see [Create a business skill](erp-business-skills.md#create-a-business-skill).

## Built-in skills and security

Built-in skills are intended to describe general processes that don't contain private or sensitive information. You can't assign a built-in skill to a security role, either in the AOT or on the **Business skills (preview)** page. After you deploy a built-in skill, it's available to all users in the environment who work with agents through the Dynamics 365 ERP MCP server.

A built-in skill adds guidance only. It doesn't change which data entities, pages, or actions are available to an agent, and it doesn't change the agent's security permissions. The security roles of the agent's authenticated user still determine what the agent can access. For more information, see [Dynamic context](../copilot-mcp.md#dynamic-context).

> [!IMPORTANT]
> Don't include confidential, personal, customer-specific, or regulated information in a built-in skill. If a process requires guidance that only certain users should see, create a custom business skill, and share it with the appropriate security roles. For more information, see [Share a business skill](erp-business-skills.md#share-a-business-skill).

## Prerequisites

Before you create a built-in skill, ensure that you meet the following prerequisites:

- You have a development environment where you can build and deploy X++ code, such as a unified developer environment.
- You have write access to the model where the skill belongs. Typically, this model is the same model that contains the application objects that the skill describes. For more information about models, see [Models and packages](../../dev-tools/models.md).
- The business scenario for the skill is scoped, and the instruction content has an owner who keeps it accurate as the solution changes.
- The environment where you deploy the skill meets the [prerequisites for business skills](erp-business-skills.md#prerequisites).

## Structure of a built-in skill

A built-in skill is an AOT element of type `AxSkill`. Skill elements are stored in the `AxSkills` folder of a model, which follows the same pattern as other AOT element types. Each skill element is a container for the following content:

- **SKILL.md** (required) – The core instructions for the skill.
- **Resources** (optional) – Scripts, images, and other files that support the skill. Resources can be at the same level as the SKILL.md file or in any child folder.

The following example shows the structure of a skill element named `SalesOrderCreateSkill` in Visual Studio.

```text
AxSkills
└── SalesOrderCreateSkill          (AxSkill element)
    ├── SKILL.md                   (required instructions)
    ├── Scripts
    │   └── ValidateOrderLines.py
    └── Resources
        └── OrderEntryChecklist.png
```

## Step 1: Add a skill element to your project

1. In Visual Studio, open the project for the model where the skill belongs.
1. In **Solution Explorer**, right-click the project, and then select **Add** \> **New item**.
1. Select **Skill**, enter a name for the element, and then select **Add**.

The AOT element name is a developer-facing identifier only. Agents never see it at runtime. Agents identify the skill by the **Name** property that you set in the next step.

## Step 2: Set the skill properties

In the properties of the skill element, set the following properties.

| Property | Description |
| --- | --- |
| **Name** | The runtime identifier of the skill. Use lowercase kebab-case, and start the name with the abbreviation of the module that the skill applies to, such as `sales-`, `purch-`, `prod-`, or `req-`. For example, `sales-create-order`. The name must be unique across all business skills. |
| **Description** | A description of what the skill does and when an agent should use it. Agents use the description to discover the skill and decide whether it applies to a task, so make it specific. Include the requests that should trigger the skill and the related tasks that it shouldn't be used for. |

Both properties follow the [Agent Skills specification](https://agentskills.io/specification).

## Step 3: Write the skill instructions

Write the instructions for the skill in the SKILL.md file by using Markdown. Start the instructions at a level-2 heading (`##`). You set the skill name and description in the skill properties, so don't add them to the SKILL.md file.

Include only what an agent needs to complete the process, such as:

- Process steps and the order in which to complete them
- The pages, data entities, and actions to use
- Required fields and inputs, and what to do when an input isn't provided
- Decision points and business rules
- Guardrails, such as when to get confirmation from the user before the agent saves or posts data

Reference application objects, such as pages, data entities, and actions, rather than specific MCP tools. Let the agent choose which tools to use. For more guidance, see [Best practices for writing business skills](erp-business-skills.md#best-practices-for-writing-business-skills).

The following example shows the SKILL.md file for a skill that creates sales orders.

```markdown
## Create a sales order

### Inputs

- Customer account (required). If the user doesn't provide it, ask for it.
- Item numbers and quantities (required).
- Requested ship date (optional). If the user doesn't provide it, use the date that the system calculates.

### Steps

1. Confirm that the customer exists in the `CustomersV3` entity. If the customer is on hold for all
   transactions, stop, and tell the user that the order can't be created.
1. Create the sales order header for the customer from the **All sales orders** page. Don't change the
   default site, warehouse, or payment terms unless the user asks you to.
1. Add a line for each item. Confirm that each item number exists before you add the line.
1. If an item doesn't have enough on-hand inventory, tell the user, and ask whether to keep the line.

### Guardrails

- Summarize the order header and lines, and get confirmation from the user before you save the order.
- Don't confirm the sales order or post any documents unless the user explicitly asks you to.
- When the order is created, report the sales order number to the user.
```

## Step 4: Add resources

If the skill uses scripts, images, or other supporting files, add them to the skill element. In the skill properties, the **Instructions** property identifies the required SKILL.md file, and the **Resources** property lists the other files that ship with the skill.

Resources are deployed with the skill and are available to all users who can use the skill. Don't include sensitive information in resources.

## Step 5: Build, deploy, and verify the skill

Built-in skills ship in the same deployable package as the application objects that they describe. You don't need a separate pipeline to deploy them.

1. Build your model, and then deploy it to your environment. To deploy the skill to other environments, include the model in a deployable package. For more information, see [Create deployable packages of models](../../deployment/create-apply-deployable-package.md).
1. When the package is installed, a synchronization process adds the skill to the business skills catalog in the environment.
1. In the environment, go to **System administration** \> **Setup** \> **Business skills (preview)**. Verify that the skill appears in the list and that the **Source** field is set to **Built-in**.
1. From an MCP-compatible client that's connected to the Dynamics 365 ERP MCP server, enter prompts that should cause the agent to use the skill. Verify that the agent retrieves the skill and follows its instructions. Also enter prompts for related but different tasks, and verify that the agent doesn't use the skill.

## Customize a built-in skill in an environment

After a built-in skill is deployed, users can edit it on the **Business skills (preview)** page to create a version that fits their organization's processes. When a user edits a built-in skill, the **Source** field for the skill shows **Built-in (modified)**. A modified skill isn't updated when you deploy a new version of the base skill. Users can select **Restore** to discard their changes and return to the latest base version. For more information, see [Edit a built-in business skill](erp-business-skills.md#edit-a-built-in-business-skill).

## Troubleshoot built-in skills

| Issue | What to check |
| --- | --- |
| The skill doesn't appear on the **Business skills (preview)** page. | Make sure that the package that contains the skill is deployed to the environment and that the **(Preview) Business skills** feature is enabled. Then check whether the skill is in the `McpBusinessSkill` table. This table contains the skills that the synchronization process read from the AOT. |
| The skill appears on the page, but agents don't use it. | Make the **Description** property more specific about the tasks that the skill applies to, and include the requests that should trigger the skill. |
| Agents use the skill for tasks that it doesn't apply to. | Make the **Description** property more specific, and state the related tasks that the skill shouldn't be used for. |
| Changes to the skill don't appear after you deploy a new version. | If the **Source** field shows **Built-in (modified)**, a user edited the skill in the environment, and the modified version isn't updated. To use the latest base version, open the skill, and select **Restore**. |

## Related information

- [Business skills for Dynamics 365 ERP (preview)](erp-business-skills.md)
- [Use Model Context Protocol for finance and operations apps](../copilot-mcp.md)
- [Add AI descriptions for the Dynamics 365 ERP MCP server](mcp-ai-descriptions.md)
- [Models and packages](../../dev-tools/models.md)
