---
# required metadata

title: Budgeting home page
description: This topic provides an overview of the budgeting functionality components, budgeting tools, and reporting capabilities in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: twheeloc
manager: AnnBe
ms.date: 08/09/2017
ms.topic: index-page
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 106043
ms.assetid: 702f692e-ad1c-4798-8d3e-c3cf8591d3fa
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Budgeting home page

[!include[banner](../includes/banner.md)]


This topic provides an overview of the budgeting functionality components, budgeting tools, and reporting capabilities in Finance and Operations. 

Components of budgeting functionality
-------------------------------------

The resource planning cycle for a company typically consists of planning, budgeting, and forecasting activities.

[![Budgeting functionality components](./media/budgeting-functionality-components.jpg)](./media/budgeting-functionality-components.jpg)

The processes for both long-term strategic planning and annual budget planning are supported through a budget plan document. Budget plan documents are tightly integrated with Microsoft Excel. Users can configure unlimited monetary and quantitative scenarios, and can also define a budgeting organizational hierarchy to both support top-down and bottom-up budgeting methods. After a budget is established and approved in Finance and Operations, you convert the budget plan to a budget register entry. Budget register entries provide tools for maintaining the budget and for keeping amounts traceable through budget codes. Budget register entries let you revise original budgets, perform transfers, and carry forward budget amounts from the previous year. Based on the established budget, a company can enable budget control. The level of control depends on the organizational culture and the organization's level of maturity. Organizations that have low maturity might leave the budget “as is” and might be more reactive than proactive if a budget doesn't meet expectations. Other organizations might enable budget control policies that prevent users from purchasing if budget funds aren't available.

Finally, very mature organizations might establish an organizational culture where employees are educated about organizational targets and follow those targets through policies such as “Consider online meeting instead of a travel.” Finance and Operations includes a budget control framework that lets the company's management select either hard control (which prevents postings that would go over the budget) or soft control (where users are warned that they will exceed the available budget funds but can decide for themselves how to proceed). Finally, you can use rolling forecasts. A rolling forecast is a regular comparison of budget to actuals and is used to define how well the company operates against the budget. A rolling forecast is also used to identify trends. In Finance and Operations, rolling forecasts are supported, through a budget plan document, as initial planning activities. Rolling forecasts can be done in parallel with the planning for the upcoming budget cycle.

-   [Basic budgeting: Overview and configuration](basic-budgeting-overview-configuration.md)
-   [Budget control: Overview and configuration](budget-control-overview-configuration.md)
-   [Budget planning: Overview and configuration](budget-planning-overview-configuration.md)
-   [Position forecasting](position-forecasting.md)
-   [Budget planning justification documents](budget-planning-justification-docs.md)
-   [Microsoft Excel templates for budget planning](budget-planning-excel-templates.md)

## Budgeting tools in Finance and Operations
[![Budgeting tools](./media/budgeting-tools.jpg)](./media/budgeting-tools.jpg) 

Additional planning and budgeting capabilities are available across Finance and Operations and are integrated with ledger budgets.

-   **Workforce budgets** – Workforce budgeting includes detailed budget cost component planning for positions, compensation groups, and so on.
-   **Fixed assets budgets** – Based on fixed asset information, you can calculate planned depreciation and record other planned transactions that are related to fixed assets.
-   **Project budgets** – In the projects module, you can create detailed project forecasts. The projects forecasts will include details about the planned hours, expenses, fees, and items.
-   **Demand forecasting **– Based on historical transaction data, you can estimate future inventory demand and create demand forecasts.

For information about how to bring planning data from other modules into budget plans, see [Budget planning integration with other modules](budget-planning-integration-other-modules.md).

## User interface and reporting capabilities
In Finance and Operations, users can create budget plans either directly in the Finance and Operations client (by using a configurable budget plan document page) or through Excel. Excel provides several additional capabilities. For example, you can use external data as a source for a budget plan, do custom calculations, and use Microsoft PivotTable and charts. Most of the variables in the budget planning process can be configured. 

For example, you can define who does budgeting, what is budgeted, and what the process looks like. Although you can use Excel for budget planning, Finance and Operations is kept as a single source of truth and helps prevent budget control issues. Periodic processes can be used to bring initial data for budgeting into the budget plan. For reporting, Finance and Operations offers a set of standard inquiry pages that let you view and analyze budgeting data. Budget plan data can be accessed through Management Reporter, and separate budget plan scenarios can be displayed as columns on the Management Reporter report.






