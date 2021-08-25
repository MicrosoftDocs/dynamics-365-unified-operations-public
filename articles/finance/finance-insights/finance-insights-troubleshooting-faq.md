---
# required metadata

title: Troubleshoot Finance insights setup issues
description: This topic lists issues that can arise when you use Finance insights capabilities. It also lists the steps to resolve the issues.
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

# Troubleshoot Finance insights setup issues

[!include [banner](../includes/banner.md)]

This topic lists issues that can arise when you use Finance insights capabilities. It also lists the steps to resolve the issues. 

## Symptom: Why can’t I map the customer payment insights Data Integration (DI) template destination column?

### Resolution

You might be using a template for an earlier version. Before the release of version 10.0.17, preview customers configured the DI template, Customer payment insights results (CDS to Fin and Ops) using the Payment prediction result (preview), entity. After upgrading to 10.0.17 and later, you should complete that mapping using the Begin using the "Customer payment insights results (CDS to Fin and Ops 10.0.17+)" DI template. You might not be able to map the DI template destination column until the data management entity list is refreshed and the Payment prediction result entity is displayed. To refresh the entity list and display the payment prediction result, you'll complete steps in Dynamics 365 Finance, and in Dataverse (previously the CDS admin portal).

### In Microsoft Dynamics 365 Finance

Complete the following steps in Dynamics 365 Finance after upgrading.

1. Open the **Data management** page (**System administration > Workspaces > Data management**).

2. Select the **Framework parameters** tile, which opens the **Data import/export framework parameters** page.

3. Select **Entity settings**, and then click **Refresh entity list**.

4. Close the **Data import/export framework parameters** page.

5. On the **Data management** page click the **Data entities** tile.

6. Search for “Payment prediction result”. Verify that the payment prediction results entity is not the preview version, which would include the “(preview)” suffix. If you only see en entity for a preview version, contact Microsoft Support.

### On the CDS admin portal

Complete the following steps in the [Power Platform admin center]( https://admin.powerplatform.microsoft.com/environments) to update your data integration projects.

1. If you’re using a preview version of Finance insights, remove the DI project associated with the Customer payment insights results (CDS to Fin and Ops).

2. Complete the steps in the [Create a data integrator project](create-data-integrate-project.md) topic. Use the template "Customer payment insights results (CDS to Fin and Ops 10.0.17 and later)".

## Symptom: Why doesn’t the Cash forecast tab in the Cash flow forecast workspace show any data?

### Resolution

The cash flow forecasting function in Cash and bank management, and the Cash flow forecasts feature in Finance insights must be set up and enabled to correctly show the data in the workspace.  

The cash flow forecasting and liquidity accounts must be set up and enabled. For more information, see [Cash flow forecasting](../cash-bank-management/cash-flow-forecasting.md). If this setup has been completed and you’re not seeing the results you expect, see [Troubleshoot cash flow forecasting setup](../cash-bank-management/cash-flow-forecasting-tsg.md) for more information.

Next confirm that the **Cash and bank management > Setup > Finance Insights > Cash flow forecasts** feature has been enabled and the AI model has completed training. If the training has not been completed select **Forecast now** to initiate the model training.
