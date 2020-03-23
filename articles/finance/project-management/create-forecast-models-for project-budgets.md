---
# required metadata

title: Create forecast models for project budgets 
description: This article describes how to create a forecast model for remaining budget for budget contraol.
author: RadhikaRS
manager: AnnBe
ms.date: 03/22/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Service industries
ms.author: v-radsh
ms.dyn365.ops.version: 7.0
ms.search.validFrom: 2019-01-15
---

# Create forecast models for project budgets 

[!include [banner](../includes/banner.md)]

A project that is subject to budget control uses two types of budgets: the original budget and the remaining budget. When you create a project budget, you must specify the original and remaining budget forecast models that were created in the **Forecast models** page. Project budgets based on the specified models are created when you commit the project budget.

**Note:** A forecast model that is used for budget control can’t have a submodel or be used as a submodel.

1. Select **Project management and accounting** > **Setup** > **Forecasts**  > **Forecast models**.
2.  Select **New** to create a new forecast model, and then enter a **Model** ID number and a **Name** for the new model. 
3. Switch **Stopped** option to **Yes** to prevent any changes to the forecast lines for the forecast model. 
4. If the forecast lines that the model is associated with should generate cash flow forecasts in the general ledger, switch **Include in Cash flow forecasts** to **Yes.** 
5. In the **Budget type** field, select one of the following model types:
   - **Original budget**: Use this for the original budget amounts that are committed when the initial budget is created and approved. 
   - **Remaining budget**: Use this for the remaining budget amounts during the life of the project. The balances in this forecast model are reduced by actual transactions and increased or decreased by budget revisions. 
   - **Carry-forward**: Use this for carry-forward budget amounts for the project. Carry-forward is an optional process that can be run to transfer unused budget amounts from one fiscal year to another. 
6. Optional: On the **Project** tab, FastTab, select the options that you want to use for the invoice date or for forecasting Work in Progress (WIP).

1. **Important:** You can’t change the budget type after you change a record. 

**See also**

[Copy forecast model transactions](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/copy-forecast-model-transactions)

[Set up a forecast model](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/set-up-a-forecast-model)

[About setting up a project budget](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/about-setting-up-a-project-budget)

[Configure project budget control](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/configure-project-budget-control)

[Create and submit an original project budget](https://docs.microsoft.com/en-us/dynamicsax-2012/appuser-itpro/create-and-submit-an-original-project-budget)

 
