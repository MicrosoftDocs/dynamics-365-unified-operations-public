---
# required metadata

title: Project forecasts and budgets
description: 
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ForecastModel, ProjYearEndProcess
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 23501
ms.assetid: 4e6d1384-19a2-4232-b3f3-d2590c218bd7
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Project forecasts and budgets

[!include[banner](../includes/banner.md)]




Microsoft Dynamics 365 for Operations provides two ways to manage and control your projects: project forecasts and project budgets. 

Use project forecasting if your organization has an operational perspective, and if it focuses on revenues and costs that are derived from specific transactions. Use project budgeting if your organization focuses more on the financial amounts. 

Both project forecasts and project budgets use forecast models to hold the projected transaction amounts. 

Each method has its advantages. You should consider the following points before you select a method for your organization.

|                           |                                                                                                                                                                                                                                                         |                                                                                                                                                                         |
|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                           | **Project forecasting**                                                                                                                                                                                                                                 | **Project budgeting**                                                                                                                                                   |
| **Period allocation**     | You can't explicitly allocate transactions over a fiscal period. Instead, the forecast, and the control of the forecast, are based on the life of the project. Because forecasts are based on a specific date, you must infer the period from the date. | You can allocate transactions over the whole project or a fiscal period. If you allocate over a period, you can carry unused amounts forward to the next fiscal period. |
| **Viewing transactions**  | You can view transactions in the forecast forms, where you see the forecasts for the whole company and for all projects, regardless of the hierarchy. To focus on a particular project, you must filter the data.                                       | You can view budgeted transactions for a single project hierarchy. Therefore, you can view transaction details for a parent project or its subprojects.                 |
| **Transaction variables** | When you enter forecast transactions, you can use every attribute that exists for an actual transaction. This allows for greater detail in the forecast. For example, you can enter details for quantities, workers, items, or line properties.         | When you enter budget details, you can use only amounts, categories, and activities.                                                                                    |
| **Security**              | Forecasting is based on transactions that you enter in the forecast forms and involves no process control mechanism. Any worker who has permissions for a forecast form can revise information without approval.                                        | Budgeting uses the workflow system, which enables change management and lets you keep a history of the revisions.                                                       |
| **Entry types**           | Forecast transaction entries are based on the number of units, and on cost and sales unit prices.                                                                                                                                                       | Budget details are based on amounts, which are split between costs and revenues.                                                                                        |
| **Forecast models**       | Because each forecast must be associated with a model, you can create multiple forecast models and also set up submodels.                                                                                                                               | Project budgeting limits the forecast models that are used for budgeting. Fewer forecast models can help increase consistency in projections.                           |
| **Cost overruns**         | You can only allow or disallow the entry of transactions that will cause a cost overrun.                                                                                                                                                                | Project budgeting provides additional control options for users. You can allow warnings and overruns.                                                                   |
| **Control**               | Forecast control is performed by using forecast reduction. Actual amounts are subtracted from forecast transaction balances without any audit trail. This can make it more difficult to trace where the actual transactions occurred.                   | In project budget control, actual amounts are subtracted from amounts in the remaining budget. This allows for a clearer audit trail.                                   |

## Project forecasts
When you use project forecasting, you can enter forecast transactions in forecast forms for each transaction type. Every attribute that is available for an actual transaction can be used for a forecast transaction—for example, line profitability, line attributes, workers, or descriptions. You can also project how long after you incur a cost you will invoice a customer. 

Project forecasting transactions are based on units and amounts. 

You must associate each project forecast with a forecast model. When you enter a forecast transaction, a forecast model is automatically suggested. The forecast model acts as a container for the forecast transactions. 

You can designate forecast models as submodels for a model. This lets you forecast by region, time period, or department. You can copy the forecast transactions in a model to create a new model, and you can also transfer the transactions to the general ledger. Because there is a one-to-one relationship between a forecast and a model, each forecast model makes up a separate budget for a project. 

Forecast models can use forecast reduction as the control mechanism for projects. In forecast reduction, actual transactions reduce forecast transaction balances. However, because forecast reduction is applied to the highest project in the hierarchy, it provides a limited view of changes in the forecast. For example, if a worker is associated with a subproject, the actual transactions for the worker are posted to the parent project. This can make it difficult to track changes, because you can't easily determine which transaction in which subproject caused a reduction to the forecast amount. Therefore, it's a good idea to create a copy of a forecast model for forecast reduction to use. You can then use reports to view what was originally forecasted. 

You can revise, copy, delete, or transfer project forecasts to a general ledger budget. However, there is no process control. Any worker who has permission for a forecast form can make revisions without review.

-   **Revise **– You can revise a forecast transaction in the same forms where the original entries were made.
-   **Copy or delete** – When you copy forecast transactions, you copy the transaction lines of one forecast model to another forecast model. When you delete a forecast, you delete the forecast transactions from a forecast model. To limit the forecast transactions that are copied or deleted, select specific transaction types and dates. This lets you copy or delete only specific parts of a forecast.
-   **Transfer** – When you transfer a project forecast to a general ledger budget, you transfer the forecast transactions of a forecast model to a general ledger budget. You can overwrite any previously transferred transactions in the general ledger budget that you transfer your project forecast to.

## Project budgets
Project budgeting is a simpler method than forecasting, although it does integrate with forecast models. It uses a single entry form for original budget details and revisions, and allows for projections that are based only on amount, category, or activity. 

In project budgeting, all original budgets and revisions must be sent to a project workflow for approval. Workflows give you increased control over the process and create a change history record. 

Project budgeting resembles general ledger budgeting, but is faster and easier to set up. Many of the options in general ledger budgeting, such as number sequences or currency, do not have to be set up separately for projects.

Project budgets are automatically associated with two forecast models, one for original budget and one for remaining budget. Therefore, reports that are based on forecast models can use budget data. When a project budget is committed, the system creates forecast transactions based on the associated models, which are used for reporting and control purposes.

## Forecast models
Forecast models have a single-layer hierarchy. This means that one project forecast must be associated with one forecast model.

If you use project forecasting, you can identify models as submodels. You can then create forecasts by department, time period, or region. For example, you can create a forecast model for a year, and then create submodels for the Northeast, Southeast, Northwest, and Southwest regional forecasts that regional heads submit. By selecting different options in the available reports, you can view information by total forecast or by submodel.



