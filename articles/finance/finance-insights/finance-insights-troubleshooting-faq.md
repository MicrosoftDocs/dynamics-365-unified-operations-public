---
# required metadata

title: Troubleshoot Finance insights setup issues
description: This article lists issues that can occur when you use Finance insights capabilities. It also explains how to fix those issues.
author: panolte
ms.date: 02/11/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2021-08-20
ms.dyn365.ops.version: AX 10.0.20

---

# Troubleshoot Finance insights setup issues

[!include [banner](../includes/banner.md)]

This article lists issues that can occur when you use Finance insights capabilities. It also explains how to fix those issues.

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

## Symptom: When I try to open AI Builder by using the links on the Customer payment predictions setup page, why do I receive the following error message: "Sorry, there's been a disconnect"?

### Resolution

Dynamics 365 Finance users must have a Microsoft Power Apps user account for the environment, and that user account must have the System customizer role. The Microsoft Power Apps system administrator can create the user account and assign the role. You can then go to <https://make.preview.powerapps.com/>, sign in by using that user account, and try the links again.

## Symptom: Why doesn't the Cash forecast tab in the Cash flow forecast workspace show any data?

### Resolution

The cash flow forecasting function in Cash and bank management and the Cash flow forecasts feature in Finance insights must be set up and enabled to correctly show data in the **Cash flow forecast** workspace.

First, set up and enable the cash flow forecasting and liquidity accounts. For more information, see [Cash flow forecasting](../cash-bank-management/cash-flow-forecasting.md). If this setup has been completed, but you don't see the results that you expect, see [Troubleshoot cash flow forecasting setup](../cash-bank-management/cash-flow-forecasting-tsg.md) for more information.

Next, confirm that the Cash flow forecasts feature in Finance insights (**Cash and bank management \> Setup \> Finance Insights \> Cash flow forecasts**) has been enabled, and that training of the AI model has been completed. If the training hasn't been completed, select **Forecast now** to start the model training process.

## Symptom: Why isn't the Install a new add-in button visible in Microsoft Dynamics Lifecycle Services?

### Resolution

First, verify that the **Environment Manager** or **Project Owner** role is assigned to the signed-in user in the **Project security role** field in Microsoft Dynamics Lifecycle Services (LCS). Installation of the new add-ins requires one of these project security roles.

If the correct project security role is assigned to you, you might have to refresh your browser window to see the **Install new add-in** button.

## Symptom: The Finance insights add-in doesn't seem to be installing. Why is that?

### Resolution

The following steps should have been completed.

- Verify that you have **System administrator** and **System Customizer** access in the Power Portal admin center.
- Verify that a Dynamics 365 Finance or equivalent license is applied to the user who is installing the add-in.
- Verify that the following Azure AD app is registered in Azure AD: 

    | Application                  | App ID           |
    | ---------------------------- | ---------------- |
    | Microsoft Dynamics ERP Microservices CDS | 703e2651-d3fc-48f5-942c-74274233dba8 | 
  
    To verify the application is registered in Azure AD, check the **All Applications** list. For more details, see [View enterprise applications](/azure/active-directory/manage-apps/view-applications-portal).
  
    If the application isn't registered in Azure AD, contact support.

## Symptom: Error, “We didn’t’ find any data for the selected filter range. Please select a different filter range and try again.” 

### Resolution

Check the data integrator setup to validate that it's functioning as expected and upserting the data from AI Builder back to Finance.  
For more information, see [Create a data integration project](../finance-insights/create-data-integrate-project.md).

## Symptom: Customer payment prediction training failed and the AI Builder error states, "Prediction should have only 2 distinct outcome values to train the model. Map to two outcomes and retrain", "Training report issue: IsNotMinRequiredDistinctNonNullValues".

### Resolution

This error indicates that there are not enough historical transactions in the last year that represent each category described in the **On-time**, **Late**, and **Very late** categories. To resolve this error, adjust the **Very late** transaction period. If adjusting the **Very late** transaction period doesn't fix the error, **Customer payment predictions** is not the best solution to use as it needs data in each category for training purposes.

For more information about how to adjust the **On-time**, **Late**, and **Very late** categories, see [Enable customer payment predictions](../finance-insights/enable-cust-paymnt-prediction.md).

## Symptom: Model training failed

### Resolution

The **Cash flow forecast** model training requires data that contains 100 or more transactions that span more than a year. We recommend that you have at least two years of data with more than 1,000 transactions.

The **Customer payment predictions** feature requires more than 100 transactions in the previous six to nine months. The transactions can include free text invoices, sales orders, and customer payments. This data must be spread across the **On-time**, **Late**, and **Very late** settings defined on the **Configuration** page.    

The **Budget proposal** feature requires a minimum of three years of budget or actual data. This solution uses three to ten years of data in the projections. More than three years will provide better results. The data itself works best when there is variation in the values. If the data contains all constant data, such as a lease expense, the training may fail because the lack of variation doesn’t require AI to project the amounts.

## Symptom: Error message states, that the "Table with name, 'msdyn_paypredpredictionresultentities' does not exist. The remote server returned an error: (404) Not Found…"

### Resolution

The environment has reached the Data Lake Services maximum table limit. For more information about the limit, see the **Enable near real-time data changes** section of the article, [Export to Azure Data Lake overview](../../fin-ops-core/dev-itpro/data-entities/Azure-Data-Lake-GA-version-overview.md).
