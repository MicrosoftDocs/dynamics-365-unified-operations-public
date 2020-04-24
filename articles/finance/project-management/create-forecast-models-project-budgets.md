---
# required metadata

title: Create forecast models for project budgets 
description: This article describes how to create a forecast model for remaining budgets.
author: RadhikaRS
manager: AnnBe
ms.date: 04/24/2020
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

# Create forecast models for project budgets 

 A project that is subject to budget control uses two types of budgets: the original budget and the remaining budget. When you create a project budget, you must specify the original and remaining budget forecast models that were created in the **Forecast models** page. Project budgets based on the specified models are created when you commit the project budget.

**Note:** A forecast model that is used for budget control can’t have a submodel or be used as a submodel.

1. Select **Project management and accounting** > **Setup** > **Forecasts**  > **Forecast models**
2. Select **New** to create a new forecast model, and then enter a **Model** ID number and a **Name** for the new model. 
3. Switch **Stopped** option to **Yes** to prevent any changes to the forecast lines for the forecast model. 
4. If the forecast lines that the model is associated with should generate cash flow forecasts in the general ledger, switch **Include in Cash flow forecasts** to **Yes.** 
5. To use the project date as the invoice date, slide **Forecast Invoice date** option to **Yes**. 
6. In the **Budget type** field, select one of the following model types:
   - **Original budget**: Use this for the original budget amounts that are committed when the initial budget is created and approved.
   - **Remaining budget**: Use this for the remaining budget amounts during the life of  the project. The balances in this forecast model are reduced by actual transactions and increased or decreased by budget revisions.
   - **Carry-forward**: Use this for carry-forward budget amounts for the project. Carry-forward is an optional process that can be run to transfer unused budget amounts from one fiscal year to another.
7. You can set the following options as required:
   - Turn on **Forecast invoice date** to use the project date as the invoice date.
   - Turn on **Forecast with WIP** to forecast based on work in progress, and then select the type of WIP. 
   - You can keep the default **Budget type** as **None** or enter a new type. The budget type cannot be changed after you change a record.     
   - **Note:**  If you change the default budget type, all other options will become unavailable for updates, and you cannot reuse this forecast model. 
    - You can also select **Automatic forecast reduction** and **Required sufficient remaining budget** options.



 

