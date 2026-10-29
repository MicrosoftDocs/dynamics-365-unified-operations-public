---
title: Business performance planning demo assets FAQ
description: Find answers to common questions about Business performance planning demo assets, security, Power BI template apps, configuration, updates, and troubleshooting.
author: twheeloc
ms.author: romainpham
ms.reviewer: twheeloc
ms.topic: faq
ms.date: 10/27/2026
ai-usage: ai-assisted
---

# Business performance planning demo assets FAQ

This article answers common questions about the Dynamics 365 Finance Business performance planning demo assets and the associated Power BI template apps. For initial installation and configuration, see [Get started with Business performance planning demo assets](bpp-get-started-demo.md).

## General

### What are the Business performance planning demo assets?

The demo assets provide preconfigured planning data, models, automation, and Power BI experiences for exploring Dynamics 365 Finance Business performance planning. They currently support:

- Financial planning and analysis
- Retail sales planning

The Power Platform environment contains the Business performance planning data model, demo data, Power Automate flows, connection references, and Power Query dataflows. The Power BI template apps provide the reporting, analysis, and interactive planning experiences.

### Which Power BI template apps are available?

You can install either or both of these template apps:

- Dynamics 365 Finance Business performance planning - Financial planning and analysis demo data
- Dynamics 365 Finance Business performance planning - Retail sales planning demo

### Do the Financial planning and analysis and Retail sales planning demos require separate environments?

No. You can connect both Power BI template apps to the same configured Business performance planning demo assets environment. Each template app is installed separately in Power BI.

### Are the demo assets intended for production planning?

No. The demo assets provide preconfigured scenarios and sample data for demonstrating and exploring Business performance planning. Don't treat the demo configuration as a production planning implementation or recommended production data model.

Design production implementations for the organization's planning requirements, data model, security, integrations, and planning processes.

### Can I use my own data with the demo assets?

The demo assets are designed to provide a preconfigured demonstration experience. You can modify the underlying Business performance planning model and data, but changes might affect the preconfigured Power BI reports, planning visuals, calculations, automation, and workflows.

For a production implementation, create a planning model that reflects your organization's requirements instead of treating the Demo Assets as a production template.

## Licensing

### What Dynamics 365 license do I need?

Users who perform planning operations require a Dynamics 365 Finance Premium license. For current licensing and product requirements, see [Microsoft Dynamics 365 Finance Business performance planning requirements](install-bpp2.md).

### What Power BI license do I need?

You need a Power BI Pro license to install a Business performance planning Power BI template app. Your Power BI administrator must also allow you to install template apps in the Power BI tenant.

### Does every user need Power BI Pro?

The user who installs the Power BI template app requires Power BI Pro. Licensing requirements for users who consume shared Power BI content depend on how the content is shared and how your Power BI environment is configured. For current requirements, see the Power BI licensing and sharing documentation.

### Does a Power BI Pro license give me access to Business performance planning?

No. Power BI licensing and Business performance planning authorization are separate. Users who perform planning operations still need:

- A Dynamics 365 Finance Premium license.
- An appropriate Business performance planning security role.
- Dimension security access to the required planning data.

## Security and data access

### Which Business performance planning role should I use for the demo?

For the complete interactive demo experience, assign users at least the Business performance planning contributor role. Users who only need to view reporting can use a more restrictive role.

For detailed role capabilities, see [Business performance planning security](bpp-security.md).

### Do users need to open the Business performance planning application to use the Power BI demo?

No. Users can interact with Business performance planning experiences through the Power BI template app without opening the Business performance planning model-driven application.

Administrators use the application to configure items such as dimension security. Users can also use it to explore or modify the underlying planning model.

### What controls which demo data a user can access?

Business performance planning uses dimension security. A Business performance planning administrator assigns users to dimension groups that provide access to the required dimension values.

For all Business performance planning visuals except Table edit, users need access to at least one dimension value for every dimension in the cube.

### Why can a user open the Power BI report but not see the expected planning data?

Access to a Power BI report doesn't automatically grant access to all Business performance planning data. Verify that:

- The user has the appropriate Business performance planning security role.
- The user is assigned to the appropriate dimension group.
- The dimension group provides access to the dimensions and dimension values used by the demo.

### Why can a user see planning data but not update it?

Check both the user's Business performance planning security role and dimension security. The user might:

- Have a read-only Business performance planning role.
- Have read-only access to the relevant dimension values.
- Lack permission for the planning operation being performed.

For detailed role and dimension security behavior, see [Set up security for Dynamics 365 Finance Business performance planning](bpp-security.md).

## Power BI template apps

### What is a Power BI template app?

A Power BI template app packages prebuilt Power BI content that users can install in their Power BI tenant and connect to a data source.

The Business performance planning template apps include the semantic models, reports, and Business performance planning experiences used by the Financial planning and analysis and Retail Sales Planning demos.

### What's the difference between a template app and a workspace app?

A Power BI template app is designed for packaged distribution to other Power BI customers and tenants, including through Microsoft AppSource. A workspace app distributes content from a Power BI workspace to users in an organization.

The Business performance planning demo apps are distributed as Power BI template apps. For more information, see [Workspace apps in Power BI](/power-bi/consumer/end-user-apps).

### Where is the Power BI template app installed?

The template app is installed in the Power BI tenant associated with the account that performs the installation. Power BI also creates an associated workspace containing the artifacts included with the template app.

### Does installing the Power BI template app connect it automatically to my demo assets environment?

No. Installation and connection are separate operations. After installation, select **Connect your data** and provide the connection parameters for the Dataverse environment that contains the demo assets.

### Can the Power BI template app and demo assets be in different environments?

Yes. The template app is installed in your Power BI tenant, and the demo assets are installed in a Power Platform environment. The connection parameters determine which demo assets environment provides data to the template app.

### Can I install both Business performance planning template apps?

Yes. You can install both template apps and connect them to the same configured demo assets environment.

### Can I share an installed template app with other Power BI users?

Yes. After you install and configure the template app, use the standard Power BI sharing capabilities. Business performance planning doesn't introduce a separate Power BI sharing mechanism.

For more information, see [Share reports and dashboards from an app](/power-bi/explore-reports/end-user-app-view#share-reports-and-dashboards-from-an-app).

### Can I install the same template app more than once?

Power BI manages template app installation and workspace behavior. For more information, see [Current installation](/power-bi/collaborate-share/service-template-apps-install-distribute).

### Can I connect the template app to another demo assets environment?

Yes. Update the connection parameters to reference the other Dataverse environment, update the data-source credentials if required, and refresh the semantic model. The demo assets must already be installed and configured in the target environment.

## Power BI connection and refresh

### What connection information do I need?

The template apps prompt you for **Server** and **Database**. Both values come from the **Environment URL** of the Power Platform environment where the demo assets are installed. Find the Environment URL in the Power Platform admin center under the environment details.

For example, if the Environment URL is `operations-xpna-demo.crm3.dynamics.com`, use:

| Parameter | Value |
| --- | --- |
| **Server** | `operations-xpna-demo.crm3.dynamics.com` |
| **Database** | `operations-xpna-demo` |

### Where can I find the server value?

The **Server** value is your Dataverse organization URL without the `https://` prefix. To find it:

1. Go to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. Select **Manage** > **Environments**.
1. Select the environment where the Demo Assets are installed.
1. Under **Details**, find **Environment URL**.
1. Copy the Environment URL.
1. If the URL includes `https://`, remove that prefix.

| Environment URL | Server |
|---|---|
| `https://operations-xpna-demo.crm3.dynamics.com` | `operations-xpna-demo.crm3.dynamics.com` |

### Where can I find the Database value?

The **Database** value is the first part of the Environment URL before the first period (`.`).

| Environment URL | Database |
|---|---|
| `operations-xpna-demo.crm3.dynamics.com` | `operations-xpna-demo` |

For the Environment URL `operations-xpna-demo.crm3.dynamics.com`, enter:

- **Server:** `operations-xpna-demo.crm3.dynamics.com`
- **Database:** `operations-xpna-demo`

> [!TIP]
> Find the Environment URL in the Power Platform admin center under your environment's **Details** section. Use the full Environment URL without `https://` for **Server**, and use the part before the first period (`.`) for **Database**.

### Which authentication method should I use?

Use your organizational account to authenticate to the Dataverse data source. If Power BI prompts for an authentication method, use **OAuth2**. If Power BI prompts for a privacy level, use **Organizational**.

### Why does the semantic model refresh fail?

Verify the following items:

1. The **Server** value matches the Environment URL without `https://`.
1. The **Database** value matches the part of the Environment URL before the first period (`.`).
1. The data-source credentials are valid.
1. The account can authenticate to the Dataverse environment.
1. The demo assets setup completed successfully.
1. The expected demo data exists.

After you correct the issue, refresh the semantic model again.

### The reports don't show data. What should I check?

In the configuration, confirm the following items in order:

1. The template app is connected to the intended Demo Assets environment.
1. The **Server** and **Database** parameters are correct.
1. The semantic model refresh completed successfully.
1. The expected demo data exists.
1. The demo assets setup completed successfully.
1. The user has the required Business performance planning security role and dimension access.

This sequence helps distinguish a Power BI connection problem from a Business performance planning security problem.

## Demo assets configuration

### Why does XPnA demo data setup fail?

Verify that:

- You configured all four demo data connection references.
- You selected the correct environment in the **Refresh a dataflow** action.
- You selected a valid demo assets dataflow.
- You saved the flow after you configured it.

After you resolve the issue, run **XPnA demo data setup** again.

### Why can't I turn on a demo assets cloud flow?

Verify that:

- You configured the required connection references.
- **XPnA demo data setup** completed successfully.
- You opened and saved the flow before you tried to turn it on.

Saving the flow applies the configured connection references and environment-specific values. After you save the flow, select **Turn on** again.

### Why can't a dataflow find all the expected Dataverse tables?

Verify the **OrgUrl** parameter and the Dataverse connection. If only some tables appear, refresh the connection and allow Power Query to finish loading the available tables.

Also verify that Business performance planning and the Planning Demo Assets package are installed in the environment referenced by **OrgUrl**.

### Should I change the dataflow destination mappings?

No, not normally. The demo assets package includes preconfigured destination and column mappings. Before you change a mapping, verify that:

- The dataflow points to the correct Dataverse environment.
- The expected Business performance planning tables are available.
- The correct destination table is selected.

### How do I change the Financial planning and analysis or Retail approver?

You provide the approver email addresses when you run **XPnA demo data setup**. To change an approver, update the applicable configuration and run **XPnA demo data setup** again.

For more information, see [Get started with Business performance planning demo assets](bpp-get-started-demo.md).

## Updates, restore, and uninstall

### How do I update the Planning demo assets package?

You must remove the existing demo asset solutions before you install the latest package.

1. Follow the applicable #how-do-i-uninstall-the-demo-assets.
1. Go to the <https://admin.powerplatform.microsoft.com>.
1. Open the environment where Business performance planning is installed.
1. Under **Resources**, select **Dynamics 365 apps**.
1. Select **Install app**.
1. Search for the Planning demo assets package.
1. Install the latest package.
1. Configure the demo assets again. For more information, see [Get started with Business performance planning demo assets](bpp-get-started-demo.md).

### How do I update a Power BI template app?

Power BI manages template app updates. For more information, see [Install, share, and update template apps in your organization](/power-bi/collaborate-share/service-template-apps-install-distribute).

If an updated Business performance planning template app requires an updated demo assets package, update the demo assets before you reconnect and refresh the template app.

### How do I restore the demo assets to their initial state?

The demo assets don't provide a separate reset operation. To restore them:

1. Follow the applicable #how-do-i-uninstall-the-demo-assets.
1. Go to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. Open the environment where Business performance planning is installed.
1. Under **Resources**, select **Dynamics 365 apps**.
1. Select **Install app**.
1. Search for the Planning Demo Assets package.
1. Install the package.
1. Configure the demo assets again. For more information, see [Get started with Business performance planning demo assets](bpp-get-started-demo.md).

> [!IMPORTANT]
> Uninstalling the demo assets removes the demo data, tables, and related configuration. Changes made to the demo assets are lost.

### How do I uninstall the demo assets?

Use the procedure for the demo assets release that's installed in your environment.

#### Demo assets 1.16

Remove these managed solutions:

- Microsoft XPnA demo data anchor
- Dynamics extended planning and analysis demo data

To uninstall demo assets 1.16, follow these steps:

1. Go to the [Power Apps maker portal](https://make.powerapps.com).
1. Select the environment where the demo assets are installed.
1. Select **Solutions**.
1. Select **Managed**.
1. Search for **demo**.
1. Delete **Microsoft XPnA demo data anchor**.
1. Delete **Dynamics extended planning and analysis demo data**.
1. Wait for both solutions to be successfully removed.

#### Demo assets 1.17

Remove these managed solutions:

- Microsoft XPnA demo data anchor
- Dynamics extended planning and analysis demo data
- Dynamics extended planning and analysis demo data support

To uninstall demo assets 1.17, follow these steps:

1. Go to the [Power Apps maker portal](https://make.powerapps.com).
1. Select the environment where the Demo Assets are installed.
1. Select **Solutions**.
1. Select **Managed**.
1. Search for **demo**.
1. Delete **Microsoft XPnA demo data anchor**.
1. Delete **Dynamics extended planning and analysis demo data**.
1. Delete **Dynamics extended planning and analysis demo data support**.
1. Wait for all three solutions to be successfully removed.

> [!NOTE]
> **Microsoft XPnA demo data anchor** is a lightweight solution that's used to identify whether the demo assets are installed and can typically be removed quickly.
>
> **Dynamics extended planning and analysis demo data** contains the demo data, tables, and related assets. Uninstalling this solution can take approximately 20 minutes.

If you can't delete a solution, identify and remove dependencies or customizations that reference components installed by the Demo Assets solutions.
