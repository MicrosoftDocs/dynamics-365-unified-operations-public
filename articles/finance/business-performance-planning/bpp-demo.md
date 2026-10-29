---
title: Learn about Business performance planning demo assets
description: Learn about the Dynamics 365 Finance Business planning performance demo assets and the Financial planning and analysis and Retail sales planning demo experiences.
ms.author: romainpham
author: twheeloc
ms.topic: concept-article
ms.date: 10/27/2026
ms.reviewer: twheeloc
---

# Business performance planning demo assets overview

The Dynamics 365 Finance Business performance planning demo assets are a set of preconfigured planning data, models, automation, and Power BI experiences that you can use to explore Business planning performance. They help partners, technical specialists, and customers understand how to implement enterprise planning scenarios by using Business planning performance and Power BI, without first creating a planning model and sample data from scratch.

The demo assets currently support two end-to-end planning experiences:

- Financial planning and analysis
- Retail sales planning

Use the demo assets for demonstration, evaluation, and learning. They aren't a production planning implementation or a production-ready template.

## Demo assets architecture

The demo experience has two main components: the Business planning performance demo assets package and the Power BI template apps. The connected Power BI experiences use planning data stored in Dataverse.

### Business planning performance demo assets

Install the Planning demo assets package in a Power Platform environment. It provides the shared planning foundation used by the demo experiences, including:

- Business planning performance dimensions.
- Planning cubes and tables.
- Representative sample data.
- Calculation and transformation logic.
- Connection references.
- Power Automate flows.
- Power Query Dataflows.
- Approval and workflow configuration.

### Power BI template apps

The interactive demo experiences are distributed separately as Power BI template apps. The following template apps are available:

| Power BI template app | Planning experience |
| --- | --- |
| Dynamics 365 Finance Business planning performance - Financial planning and analysis demo data | Financial budgeting, forecasting, workforce planning, OPEX planning, CAPEX planning, allocations, approvals, and P&L reporting. |
| Dynamics 365 Finance Business planning performance - Retail sales planning demo | Retail sales budgeting, driver-based forecasting, planning-status management, store and channel reporting, inventory analysis, and price-volume-mix analysis. |

You install the Power BI template apps in your Power BI tenant. You don't install them in or automatically tie them to the Power Platform environment where you deploy the demo assets. After you install a template app, you connect it to the Power Platform environment that contains the demo assets. You can install one or both template apps and connect them to the same demo assets environment.

## Financial planning and analysis demo

The Financial planning and analysis demo provides an example of a connected Financial planning and analysis planning process. The experience includes:

- Planning-status management and approvals.
- Account-based budgeting.
- Driver-based revenue planning.
- Operating expense planning.
- Workforce and compensation planning.
- HCM planning.
- Capital expenditure planning.
- Cost allocation.
- Consolidated P&L reporting.
- Variance analysis and commentary.

The demo combines direct planning in Business planning performance cubes with configured Power Automate flows and Power Query dataflows that transform selected planning inputs into reporting-ready outputs. For example, the workforce and CAPEX experiences use dataflows to transform detailed planning inputs into outputs that can be included in the consolidated P&L.

For more information, see [Business performance planning Financial planning and analysis demo](bpp-fpa.md).

### Retail sales planning demo

The Retail sales planning demo shows how Business planning performance can support retail planning and analysis by store and SKU. The experience combines planning interactions with Power BI reporting and diagnostic analysis, and it's organized around three activities:

- Track planning progress and retail performance.
- Plan retail sales budgets and driver-based forecasts.
- Diagnose inventory conditions and revenue variance.

The app includes six report pages:

| Activity | Report page |
| --- | --- |
| Track | Control tower |
| Track | Retail sales by store and channel |
| Plan | Retail sales budget |
| Plan | Retail sales driver planning |
| Diagnose | Weeks of inventory analysis |
| Diagnose | Price volume mix analysis |

To learn more, see [Business performance planning retail demo](bpp-retail.md).

#### Business planning performance capabilities in the demos

Depending on the demo experience, the demo assets illustrate Business planning performance capabilities such as:

- Planning directly in Power BI.
- Writing planning changes back to Dataverse.
- Matrix planning.
- Graphical planning.
- Table-based planning.
- Copying planning data between scenarios or periods.
- Driver-based forecasting.
- Top-down and bottom-up planning.
- Scenario comparison.
- Planning-status management.
- Approval workflows.
- Commentary.
- Dimension-based data access.
- Planning calculations and transformations.
- Connected planning and reporting.

Not every capability is used on every page. The Financial planning and analysis and Retail sales planning experiences illustrate different ways that Business planning performance capabilities can be combined to support a planning process.

The demo assets are especially useful when you need a consistent planning environment without first creating dimensions, cubes, data, reports, and automation from scratch.

#### Customization options

Explore the demo assets by changing planning data and assumptions through the connected Power BI experiences. Depending on the scenario, you can change items such as:

- Budget and forecast values.
- Driver assumptions.
- Workforce positions and compensation assumptions.
- Capital projects and asset assumptions.
- Allocation percentages.
- Planning statuses.
- Approval inputs.
- Commentary.

The connected demo assets environment stores your changes and can affect other users who use the same environment. You can also inspect the underlying Business planning performance model to understand how the demo is configured.

#### Limitations

The demo assets are designed for demonstration, evaluation, and learning. The sample data and planning logic are illustrative. The demo assets aren't:

- A production planning implementation.
- A recommended production data model.
- A reusable template that can connect to arbitrary customer data without configuration.
- A substitute for planning-model design, integration design, security design, accounting policies, or implementation validation.

Changes to the underlying model structure can affect:

- Power BI semantic-model relationships.
- Measures and calculations.
- Business planning performance visual configuration.
- Power Automate flows.
- Power Query dataflows.
- Report behavior.

Avoid removing or renaming dimensions, columns, tables, cubes, scenarios, or other objects used by the preconfigured demo experiences unless you also update their dependencies.

The demo assets don't provide a separate reset operation. To restore the demo assets to their initial state, uninstall the demo asset solutions, reinstall the Planning demo assets package, and configure the environment again.

For update, restore, uninstall, and troubleshooting guidance, see [Business performance planning demo assets FAQ](bpp-demo-faq.md).

#### Deployment overview

Deploying the demo assets involves the following stages:

1. Install Dynamics 365 Finance Business planning performance.
1. Install the Planning demo assets package.
1. Configure security and access for demo users.
1. Configure the required connection references.
1. Run the Demo data setup.
1. Configure the required cloud flows and dataflows.
1. Install the Power BI template app that you want to explore.
1. Connect the template app to the demo assets environment.

For the complete procedure, see [Get started with Business performance planning demo assets](bpp-get-started-demo.md).

#### Related content

- [Business performance planning Financial planning and analysis demo.md](bpp-fpa.md)
- [Business performance planning retail demo](bpp-retail.md)
- [Business performance planning demo assets FAQ](bpp-demo-faq.md)
