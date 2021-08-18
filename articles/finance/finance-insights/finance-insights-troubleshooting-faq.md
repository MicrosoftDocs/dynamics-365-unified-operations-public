---
# required metadata

title: Troubleshoot Finance insights setup
description: This topic describes the Cash flow forecasting capability.
author: panolte
ms.date: 08/20/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: ["14151", "intro-internal"]
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2021-08-20
ms.dyn365.ops.version: AX 10.0.20

---

# Troubleshoot Finance insights setup

[!include [banner](../includes/banner.md)]

This topic raises questions about issues that can arise when using Finance insights capabilities, along with their resolutions. 

## Symptom: Why can’t I map the customer payment insights Data Integration (DI) template destination column?

## Resolution

Prior to 10.0.17, preview customers configured the DI template Customer payment insights results (CDS to Fin and Ops) using the Payment prediction result (preview) entity. After upgrading to 10.0.17 and later, you should should complete this mapping using the begin using the "Customer payment insights results (CDS to Fin and Ops 10.0.17+)" DI template. You might not be able to map the DI template destination column until the data management entity list is refreshed and the Payment prediction result entity is displayed.

To resolve this change in Dynamics 365 Finance, complete the following steps after upgrading:

1. Navigate to **System administration > Workspaces > Data management**.

2. Click the **Data import/export framework parameters** tile.

3. Click the **Entity settings**, and then click **Refresh entity list**.

4. Close the **Data import/export framework parameters** page.

5. On the Data management page click the **Target entities** tile.

6. Search for “Payment prediction result” there should one row without a “(preview)” suffix.
   Next, in the [CDS admin portal]( https://admin.powerplatform.microsoft.com/environments), complete the following steps. 

1 If you’re using a preview version of Finance insights, remove the DI project associated with the Customer payment insights results (CDS to Fin and Ops).

2. Follow the steps in the [Create a data integrator project](create-data-integrate-project.md) and use the "Customer payment insights results (CDS to Fin and Ops 10.0.17+)" template.

## Symptom: Why doesn’t the Cash forecast tab in the Cash flow forecast workspace show any data?

## Resolution

The cash flow forecasting function in Cash and bank management and the Cash flow forecasts in Finance insights must be set up and enabled to correctly show the data in the workspace.  

First the cash flow forecasting and liquidity accounts must be set up and enabled. For more information, see [Cash flow forecasting]( https://docs.microsoft.com/en-us/dynamics365/finance/cash-bank-management/cash-flow-forecasting.md). If this setup has been completed and you’re not seeing the results you expect, see [Troubleshoot cash flow forecasting setup]( https://docs.microsoft.com/en-us/dynamics365/finance/cash-bank-management/cash-flow-forecasting-tsg.md) for more information. 

Next confirm that the **Cash and bank management > Setup > Finance Insights > Cash flow forecasts** feature has been enabled and the AI Model has completed training.  If this training has not been completed select **Forecast now** to initiate the model training. 
