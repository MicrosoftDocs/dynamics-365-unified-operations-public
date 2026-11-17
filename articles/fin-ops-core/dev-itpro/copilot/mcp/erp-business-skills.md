---
title: Business skills for Dynamics 365 ERP (preview)
description: Learn how to create, share, and manage business skills that guide agents working with finance and operations apps through Dynamics 365 ERP MCP and Work IQ.
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

# Business skills for Dynamics 365 ERP (preview)

[!INCLUDE [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Business skills let your organization capture how work gets done in Dynamics 365 finance and operations apps and make that expertise available to agents through the [Dynamics 365 ERP MCP server](../copilot-mcp.md) and [Business Applications in Work IQ](/power-apps/maker/data-platform/business-applications-work-iq). A business skill is a reusable set of instructions that describes the policies, terminology, approval rules, legal entity practices, exception handling, and task-specific guidance that an agent should follow when it completes a business process.

Business skills address two related problems:

- An agent can reach the data and business logic in finance and operations apps that it needs, but without process guidance, it might still choose an inefficient or incorrect path to complete a task.
- Many organizations rely on process knowledge that lives with experienced users rather than in a governed, reusable form.

When you capture this knowledge as business skills, you create governed guidance assets that improve the quality of agent responses and reduce the need to add the same guidance to the instructions of each agent. You create and manage business skills centrally in finance and operations apps. You then share them by security role and legal entity, so the right guidance is available to the right users in the agents and Copilot experiences that they use.

## Types of business skills

Finance and operations apps support two types of business skills.

| Type | Description |
| --- | --- |
| **Built-in** | Skills that developers create as objects in the Application Object Tree (AOT). Microsoft, independent software vendors (ISVs), and customer developers can create built-in skills that help agents work with the pages, code, data entities, tables, and other objects that ship with a solution. Built-in skills are deployed as part of the package that contains the solution. |
| **Custom** | Skills that users in your organization create in finance and operations apps to define your own processes and procedures. |

Both types of skills appear on the **Business skills (preview)** page. The **Source** field identifies the type of each skill. For more information about how developers create built-in skills, see [Create built-in business skills](built-in-business-skills.md).

### Where agents can use business skills

Agents can access business skills that you create and manage in finance and operations apps through the following channels.

| Channel | Description |
| --- | --- |
| **Dynamics 365 ERP MCP server** | Agents that connect to the Dynamics 365 ERP MCP server from an MCP-compatible client, such as Microsoft Copilot Studio, Microsoft Foundry, or Visual Studio Code, can retrieve business skills along with the data and business logic of finance and operations apps. For more information, see [Use Model Context Protocol for finance and operations apps](../copilot-mcp.md). |
| **Business Applications in Work IQ** | Business Applications in Work IQ brings data, processes, and operational context from business applications into Microsoft Copilot and agents. Copilot experiences and agents that use Business Applications in Work IQ can access business skills from finance and operations apps. For more information, see [Business Applications in Work IQ](/power-apps/maker/data-platform/business-applications-work-iq). |

You define a skill once, and every agent that the user works with through these channels can use it. The same sharing settings determine which skills are available to a user in each channel.

### How business skills work

Each business skill has a **Description** that tells the agent when the skill applies. When an agent works on a task, it uses the skill descriptions to identify skills that are relevant to the task. The agent then retrieves the instructions of the relevant skills and adds them to its context. In the Dynamics 365 ERP MCP server, agents use the `iq_read_skill` tool to retrieve a skill. Agents always retrieve the latest version of the skill in the environment.

Business skills add guidance only. They don't change which tools, data entities, pages, or actions are available to an agent, and they don't change the agent's security permissions. The security roles of the agent's authenticated user determine what the agent can access. Built-in skills are available to all users. A user can retrieve only the custom business skills that are shared with them. For more information, see [Share a business skill](#share-a-business-skill) and [Dynamic context](../copilot-mcp.md#dynamic-context).

## Prerequisites

Before you use business skills, make sure that you meet the following prerequisites:

- Your environment meets the [prerequisites for the Dynamics 365 ERP MCP server](../copilot-mcp.md#prerequisites).
- The **Business skills(preview)** feature is enabled in [Feature management](../../../fin-ops/get-started/feature-management/feature-management-overview.md).
- To use business skills through Business Applications in Work IQ, Business Applications in Work IQ is set up for your environment. For more information, see [Set up Business Applications in Work IQ](/power-platform/admin/business-applications-work-iq/quickstart).
- To share skills with security roles, you're assigned the **Business skill maintainer** security role.

### Create a business skill

You can create a custom business skill in any of the following ways:

- [Create a skill on the Business skills (preview) page](#create-a-skill-on-the-business-skills-preview-page)
- [Create a skill from a Task recorder recording](#create-a-skill-from-a-task-recorder-recording)
- [Create a skill with an agent](#create-a-skill-with-an-agent)

### Create a skill on the Business skills (preview) page

1. Go to **System administration** \> **Setup** \> **Business skills (preview)**.
1. Select **New**.
1. In the **Name** field, enter a unique name for the skill.
1. In the **Description** field, enter a description that states what the skill does and when it applies. Agents use the description to decide whether the skill matches a task, so make it specific. For more information, see [Best practices for writing business skills](#best-practices-for-writing-business-skills).
1. In the **Instructions** section, on the **Markdown** tab, enter the instructions for the skill in Markdown format. Select the **Preview** tab to review how the instructions render.
1. Optionally, in the **Resources** section, add supporting files for the skill.
1. Select **Save**.

#### Example business skill

The following example shows a custom business skill that an accounts receivable team uses to produce a consistent weekly analysis of customer balances.

**Name:** `ar-analysis`

**Description:**

```text
Perform an accounts receivable analysis from Dynamics 365 Finance. Use when the user says "perform an AR analysis",
"analyze accounts receivable", "AR aging report", "review open receivables", "who owes us money", or "collections analysis".
Pulls aged balances and open transactions, ranks debtors, scores collection risk, and summarizes the results.
Do NOT use for AP/vendor analysis, sales forecasting, or financial statements.
```

**Instructions:**

```markdown
# AR analysis

## Workflow

1. **Scope.** Confirm the legal entity (default: the session company). Report in the accounting currency.
   Include all customers that have a nonzero balance.
1. **Get the data.** Confirm the structure of each data entity before you query it. Never guess entity,
   field, or enum names.
   - If the aging date in the `CustAgedBalances` entity is stale, run the "age customer balances" action with the
     `30_60_90_180` aging period definition and today's date, and then query again. If the action fails,
     label all figures as "latest available snapshot."
   - Use the aging buckets in `CustAgedBalances`. Don't calculate aging yourself.
   - Get hold status, credit limit, and payment terms from the `CustomersV3` entity, and get open transactions
     from the `CustTransactions` entity for invoice counts, the oldest due date, and the collection letter level.
1. **Rank debtors** by balance in descending order. Show the top 10. Calculate the share of total AR that
   the top three customers represent.
1. **Score risk** for each customer:

   | Signal | Points |
   |---|---|
   | Over credit limit | +40 |
   | Collection letter level 3 or higher / level 1-2 | +30 / +15 |
   | Oldest invoice more than 3 years / more than 1 year | +25 / +15 |
   | Balance more than $200,000 / more than $100,000 | +20 / +10 |
   | More than 90% of the balance in the oldest bucket | +15 |

   Label customers that score 80 or higher as **High risk**.
1. **Summarize the results.** Start with a two-sentence executive summary, followed by key figures for
   total AR, open invoices, and the percentage in the oldest bucket. Then show the top debtors, high-risk
   customers, and the aging distribution. Calculate all numbers exactly. Don't estimate.
1. **Propose actions** only after you present the summary. Don't update any records without confirmation
   from the user.
```

### Create a skill from a Task recorder recording

If you want a skill to follow a step-by-step process through pages in the application, use Task recorder to record the navigation path and save the steps as a business skill. For more information about Task recorder, see [Task recorder resources](../../user-interface/task-recorder.md).

1. On the navigation bar, select **Settings** (the gear symbol), and then select **Task recorder**.
1. Select **Create recording**.
1. Enter a name for the recording. This name becomes the name of the new skill.
1. Enter a description for the recording. This description becomes the description of the new skill.
1. Select **Start**, and then complete the steps of the process in the application.
1. When you're finished, select **Stop**, and then select **Save as business skill**.
1. In the **Create business skill** pane, review the name, version, description, and generated instructions, and make any changes that you need.
1. Select **Save**, or select **Save and open** to open the new skill on the **Business skills (preview)** page.

### Create a skill with an agent

You can also use an agent that's connected to the Dynamics 365 ERP MCP server to create a business skill from a task that the agent completes. This approach is often the fastest way to create an effective skill, because you refine the result with the agent before you write anything down.

1. **Do the task first.** Open an agent that's connected to the Dynamics 365 ERP MCP server, and prompt it to perform the task that you want the skill to support. For example:

    *Perform an accounts receivable analysis for customer Contoso Retail. Include their current balance, aging buckets, overdue invoices, payment history over the last 12 months, and any credit limit concerns.*

    The agent calls the appropriate tools, retrieves the data, and returns an initial answer. The first answer is rarely exactly what you want.

1. **Refine the result through conversation.** Continue to prompt the agent until the output is exactly what a business user expects to receive. Each correction becomes a requirement in the skill. For example:

    - **Correct the data scope:** *Only include posted invoices.* or *Exclude intercompany transactions.*
    - **Add missing analysis:** *Also calculate days sales outstanding and compare it to the same period last year.*
    - **Shape the output:** *Present the aging buckets as a table with columns for Current, 1-30, 31-60, 61-90, and 90+.* or *Flag anything more than 60 days overdue in a separate risk section.*
    - **Set the tone and audience:** *Write this for a credit manager, not a developer. Don't use technical field names.*

1. **Ask the agent to write the skill.** When the response is correct, ask the agent to convert the session into a reusable business skill. For example:

    ```text
    Now write a reusable business skill based on the task we just completed. Capture it as a set of
    clear, step-by-step instructions that another agent could follow to reproduce this result for any
    customer, not just this one. Specifically:

    - Give the skill a short, descriptive name and a one-sentence description of what it does and when
      it should be used.
    - List any inputs the skill needs from the user, such as the customer account, and note what should
      happen if an input isn't provided.
    - Write the instructions as numbered steps, and name the specific ERP objects, such as data entities,
      pages, and actions, that you used at each step, including any filters or criteria we applied during
      our conversation. Don't reference specific MCP tool names.
    - Include the output format we landed on, such as the section order, table columns, and summary
      style, so results are consistent every time.
    - Note any business rules, edge cases, or exclusions we established.
    - Keep the instructions generalized and parameterized. Don't hard-code this customer's name or any
      values specific to this run.
    - Optimize the instructions for the fewest number of tool calls needed to get a consistent result.
    ```

1. **Review and save the skill.** Review the skill that the agent returns. Then create a new skill on the **Business skills (preview)** page, and paste the name, description, and instructions into the corresponding fields. For more information, see [Create a skill on the Business skills (preview) page](#create-a-skill-on-the-business-skills-preview-page).

### Share a business skill

Business skills often contain processes and procedures that you don't want to share outside the teams that manage those processes. For example, some internal human resources policies might not be shared broadly across the company. Similarly, you don't want any user to be able to create a skill and share it with a team in a way that changes how that team's agents behave. Carefully consider which users can create and share skills, and with whom they can share them.

To share a business skill with security roles, assign the **Business skill maintainer** security role to a user. For more information about security roles, see [Role-based security](../../sysadmin/role-based-security.md).

To share a business skill, follow these steps:

1. Go to **System administration** \> **Setup** \> **Business skills (preview)**, and open the skill that you want to share.
1. On the Action Pane, select **Manage access**.
1. In the **Manage access** pane, in the **Sharing with roles** section, select one of the following values:

    - **Owner only** – The skill is available only to the owner of the skill.
    - **Selected roles** – The skill is available only to users who are assigned the security roles that you add to the list. Select **Add** to add a security role. You can only share a skill with security roles that you're assigned.
    - **Everyone** – The skill is available to all users. This option is available only to system administrators.

1. In the **Sharing with legal entities** section, in the **Legal entity sharing** field, select whether the skill is available in all legal entities or only in selected legal entities. If you select **Selected legal entities**, select **Add** to add each legal entity where the skill is available.
1. Select **OK**.

> [!NOTE]
> Sharing is available only for custom business skills. You can't share built-in skills with specific security roles.

To transfer ownership of a skill to another user, open the skill, and then select **Change owner** on the Action Pane.

### Edit a built-in business skill

You can edit a built-in skill to create a custom version that fits your organization's processes. When you edit a built-in skill, the **Source** field for the skill shows **Built-in (modified)**.

> [!IMPORTANT]
> A modified built-in skill isn't updated when a new version of the base built-in skill is deployed to your environment. Periodically compare your modified skills to the latest base versions. Modifications to a skill affect all users of the skill. You're responsible for testing, validating, and maintaining modifications you make to built-in skills.

To discard your changes and return to the base version of a built-in skill, open the skill on the **Business skills (preview)** page, and then select **Restore**.

### Best practices for writing business skills

Write business skills for an AI reader. Every part of a skill uses space in the agent's context, so include only the guidance that helps the agent complete the task correctly.

- **Build skills around business jobs and outcomes, not individual pages.** A skill should describe how to complete a business task, such as an AR analysis or a vendor onboarding, rather than how to use a single page.
- **Write a precise description.** The description determines when the agent uses the skill. State what the skill does, the phrases or requests that trigger it, and the related tasks that it shouldn't be used for.
- **Include high-value guidance.** Focus on standard operating procedures, required validations, business rules, intrinsic behavior of finance and operations apps, and common pitfalls that the agent is likely to encounter. Add links to deeper references when needed.
- **Reference ERP objects, not MCP tools.** Describe the data entities, pages, and actions that the agent should work with, and let the agent choose the tools to use. Don't name specific MCP tools in a skill. Tool names and capabilities can change, and the agent's tool selection adapts to the objects and tasks that you describe.
- **Let the agent discover object details.** Instruct the agent to confirm the structure of data entities and pages rather than guessing field, enum, or control names.
- **Scale safety to risk.** Favor read and draft steps. Require validation and user confirmation before the agent posts or updates data.
- **Keep skills lightweight, coherent, and composable.** Create several focused skills rather than one large skill that covers many processes.
- **Generalize the instructions.** Use parameters, such as a customer account or legal entity, instead of values from a specific run.
- **Don't include sensitive information.** Don't include demo data, customer data, confidential information, personal information, or regulated information in a skill.

### Responsible use

Use business skills to encode legitimate business processes, terminology, approval rules, and legal entity guidance. Don't use business skills to bypass approvals, controls, security roles, segregation of duties requirements, compliance requirements, or other organizational policies. Don't create skills that are inaccurate, misleading, unlawful, or discriminatory.

Business skills contain instructions and guidance that your organization creates. Your organization is responsible for the content of its skills, for reviewing skills before they're shared, and for keeping skills accurate as processes change. Business skills and agent responses don't constitute legal, regulatory, tax, or compliance advice. Review AI-generated output and actions before you rely on them for business decisions.

## Related information

- [Create built-in business skills](built-in-business-skills.md)
- [Business Applications in Work IQ](/power-apps/maker/data-platform/business-applications-work-iq)
- [Use Model Context Protocol for finance and operations apps](../copilot-mcp.md)
- [Build an agent with Dynamics 365 ERP MCP](../build-agent-mcp.md)
- [Security for Dynamics 365 ERP MCP](mcp-security.md)
- [Add AI descriptions for the Dynamics 365 ERP MCP server](mcp-ai-descriptions.md)
