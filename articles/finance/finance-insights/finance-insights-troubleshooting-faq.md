---
# required metadata

title: Troubleshoot Finance insights setup issues
description: This topic lists issues that can occur when you use Finance insights capabilities. It also explains how to fix those issues.
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

This topic lists issues that can occur when you use Finance insights capabilities. It also explains how to fix those issues.

## Symptom: Why can't I map the Customer payment insights Data Integration template destination column?

### Resolution

You might be using a template for an earlier version. Before the release of version 10.0.17, preview customers configured the **Customer payment insights results (CDS to Fin and Ops)** Data Integration (DI) template by using the **Payment prediction result (preview)** entity. After an upgrade to 10.0.17 and later, you should use the **Customer payment insights results (CDS to Fin and Ops 10.0.17 and later)** DI template to complete the mapping. You might not be able to map the DI template destination column until the data management entity list is refreshed and the **Payment prediction result** entity appears in it. To refresh the entity list and show the payment prediction result, you will complete steps in both Microsoft Dynamics 365 Finance and Dataverse (previously known as the Common Data Service \[CDS\] admin portal).

### In Finance

Follow these steps in Finance after you upgrade.

1. Go to **System administration \> Workspaces \> Data management**.
2. In the **Data management** workspace, select the **Framework parameters** tile.
3. On the **Data import/export framework parameters** page, select **Entity settings**, and then select **Refresh entity list**.
4. Close the **Data import/export framework parameters** page.
5. In the **Data management** workspace, select the **Data entities** tile.
6. Search for "Payment prediction result." Verify that the **Payment prediction result** entity isn't the preview version. The name of the preview version ends in "(preview)." If you see only the preview version of the entity, contact Microsoft Support.

### In Dataverse

Follow these steps in the [Power Platform admin center](https://admin.powerplatform.microsoft.com/environments) to update your data integration projects.

1. If you're using a preview version of Finance insights, remove the DI project that is associated with the **Customer payment insights results (CDS to Fin and Ops)** template.
2. Follow the steps in [Create a data integrator project](create-data-integrate-project.md). Use the **Customer payment insights results (CDS to Fin and Ops 10.0.17 and later)** template.

## Symptom: Why doesn't the Cash forecast tab in the Cash flow forecast workspace show any data?

### Resolution

The cash flow forecasting function in Cash and bank management and the Cash flow forecasts feature in Finance insights must be set up and enabled to correctly show data in the **Cash flow forecast** workspace.

First, set up and enable the cash flow forecasting and liquidity accounts. For more information, see [Cash flow forecasting](../cash-bank-management/cash-flow-forecasting.md). If this setup has been completed, but you don't see the results that you expect, see [Troubleshoot cash flow forecasting setup](../cash-bank-management/cash-flow-forecasting-tsg.md) for more information.

Next, confirm that the Cash flow forecasts feature in Finance insights (**Cash and bank management \> Setup \> Finance Insights \> Cash flow forecasts**) has been enabled, and that training of the AI model has been completed. If the training hasn't been completed, select **Forecast now** to start the model training process.
