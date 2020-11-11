---
# required metadata

title: Finance insights home page (preview)
description: This topic walks through the prerequisites and the broad steps that are required to use a trial version of Finance insights.
author: ShivamPandey-msft
manager: AnnBe
ms.date: 07/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.13

---
# Finance insights home page (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Finance insights provides configurable and extensible models to help you accurately and intelligently predict your company's cash flow, predict when you will receive payment for outstanding receivables, and generate a budget proposal that can speed up your budgeting process. All these features are based on intelligent machine learning models. When these new capabilities are combined with automation in vendor payments and collections, they provide a rich and intelligent financial system that drives decision making and helps you take action to respond effectively to current and anticipated business challenges.

Finance insights preview is available for trial deployments in the United States of America, Europe, and the United Kingdom. Microsoft is incrementally adding support for more regions.

Preview features can and should be turned on only in Tier-2 sandbox environments. Setup and artificial intelligence (AI) models that are created in a sandbox environment can't be migrated to a production environment. For more information, see [Supplemental Terms of Use for Microsoft Dynamics 365 Previews](https://docs.microsoft.com/dynamics365/legal/supp-dynamics365-preview#:~:text=Supplemental%20Terms%20of%20Use%20for%20Microsoft%20Dynamics%20365,%28governing%20your%20use%20of%20Microsoft%20Dynamics%20365%20Online%29.).

## Prerequisites

This section lists the requirements for using Finance insights. Wherever possible, links to sources of additional information are provided.

### Legal requirements

To apply for the preview program, fill out the [Finance insights Preview for Dynamics 365 Finance agreement](https://forms.office.com/FormsPro/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR56j8lZs0FdAvwT75_WNFyxUM1c0Uzc1RFpaU1RVTEwxVTNWUERPRThUSy4u).

### System requirements

A Tier-2 sandbox environment (multi-box) is required to preview Finance insights. For background information about environments, see [Environment planning](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/imp-lifecycle/environment-planning).

### Version requirements

This document applies to version 10.0.11 of Finance and Operations apps (Platform update 35), and later versions.

### Historical data requirements

At least one year's worth of customer invoices is required to correctly train the machine learning model that is used for the Customer payment predictions feature.

Sample data is available for demo systems that have the Contoso demo data set.

### Role and permission requirements

Changes will be made to Microsoft Dynamics 365 Finance, Microsoft Dynamics Lifecycle Services (LCS), Power Apps, and Azure. Correct permissions are required across these three environments. Here are some examples of the changes that will be made:

- A new environment will be created in Microsoft Power Platform.
- A storage account, key vault, and application will be created in Azure.
- The Active Directory tenant administrator will have to authorize the AI Builder application to access the data lake.
- The feature will be turned on in Dynamics 365.

Familiarity with the process of creating and managing resources in Azure, Common Data Service, and LCS will be helpful as you complete this process.

## Configure Finance insights

You must complete some configuration steps before you can use Finance insights. For more information about how to configure Finance insights, see [Configuration for Finance insights](configure-for-fin-insites.md).

## Create a data integrator project

Follow the steps in [Create a data integrator project](create-data-integrate-project.md) to create a data integrator project so that data flows back into Finance.

## Enable Finance insights capabilities

When you've completed the configuration steps and set up demo data, you must turn on and set up each capability that you plan to use: customer payment predictions, cash flow forecasting, and budget proposals.

### Enable customer payment predictions

If you are using demo data to test customer payment predictions, you may have to import additional demo data to create AI model successfully. Please follow the steps mentioned here: https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/bob-fi-admin-topics/articles/finance/finance-insights/set-up-demo-data.md to import demo data.

Follow the steps in [Enable customer payment predictions](enable-cust-paymnt-prediction.md) to build a machine learning model and use it with your organization's data to generate predictions about when customers are likely to pay outstanding invoices, and when specific invoices are likely to be paid.

### Enable cash flow forecasting

Follow the steps in [Enable cash flow forecasting](enable-cash-flow-forecasting.md) to build a machine learning model and use it with your organization's data to generate cash flow forecasts.

### Set up and use cash flow forecasting

For information about how to set up and use cash flow forecasting, see [Enable cash flow forecasting](enable-cash-flow-forecasting.md). For more information about how to use this capability, see [Cash flow forecasting](cash-flow-forecast-intro.md).

### Enable budget proposals

Follow the steps in [Enable budget proposals](enable-budget-proposal.md) to use a machine learning model with your organization's historical data to generate a budget proposal that can help you begin a budgeting process that is more effective than a manual process.

## Using Finance insights features

### Using Customer payment predictions

Customer payment predictions can help you collect proactively, learn how here: https://review.docs.microsoft.com/en-us/dynamics365/finance/finance-insights/enable-cust-paymnt-prediction?branch=bob-fi-admin-topics#using-the-customer-payment-predictions-feature

For information that can help you evaluate the effectiveness of the prediction model, see [Evaluate the initial customer payment prediction model](evaluate-payment-prediction.md). For information that can help you adjust the data that is used to build the prediction, to improve its effectiveness, see [Improve the prediction model](improve-model.md).

If you want to further understand the results from the AI model, please read: Understanding results of machine learning model: https://review.docs.microsoft.com/en-us/dynamics365/finance/finance-insights/confusion-matrix?branch=bob-fi-daves-blogs

### Using cash flow feature

Learn what’s new in cashflow forecasting here: What's new in cash flow forecasting: https://review.docs.microsoft.com/en-us/dynamics365/finance/finance-insights/cash-flow-forecast-intro?branch=bob-fi-intro-cashflow-forecasting

Learn how to import external data to include in your cashflow forecast here: External data: https://review.docs.microsoft.com/en-us/dynamics365/finance/finance-insights/external-data-in-cash-flow?branch=bob-finance-insites-external-data-in-cashflow

Learn how payment prediction can help you more accurately estimated your cash position here: Cash position: 

Learn how you can use forecasting using AI to project long term cash flow here: Cash flow forecast:https://review.docs.microsoft.com/en-us/dynamics365/finance/finance-insights/cash-position?branch=bob-fi-cash-position

Learn how you can save cash flow positions and cash flow forecasts and compare snapshot to actuals, here: Snapshots: https://review.docs.microsoft.com/en-us/dynamics365/finance/finance-insights/payment-snapshots?branch=bob-fi-cust-payment-snapshots

### Using Budget proposal

Learn how you can accelerate budget creation using intelligent budget proposal here: https://review.docs.microsoft.com/en-us/dynamics365/finance/finance-insights/budget-proposals?branch=bob-budget-proposals-thru-ai-ml

Demo data for budget proposal:


## Feedback and support

Please send an email to [Customer payment insights (Preview)](mailto:fiap@microsoft.com) if you are interested in providing feedback or need support.

## Privacy notice

Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.
