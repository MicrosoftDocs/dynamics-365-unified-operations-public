---
# required metadata

title: Finance insights home page
description: Finance insights provides configurable and extensible models to help you accurately and intelligently predict your company's cash flow, predict when you will receive payment for outstanding receivables, and generate a budget proposal that can speed up your budgeting process. All these features are based on intelligent machine learning models.
author: ShivamPandey-msft
ms.date: 01/27/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: AX 10.0.13

---
# Finance insights home page

[!include [banner](../includes/banner.md)]

Finance insights provides configurable and extensible solutions to help you intelligently predict your company's cash flow, predict when you may receive payment for outstanding receivables, and generate a budget proposal that can help speed up your budgeting process. These features use intelligent machine learning templates to build models using data you provide (including data from a third party such as consumer report information from a bureau). These intelligent capabilities inform decision making and helps you take action to respond effectively to current and anticipated business challenges. You are responsible for any data used with, or output from, Finance insights.

> [!NOTE]
> Finance insights is available for deployment in the United States of America, Canada, the United Kingdom, Europe, Asia Pacific, Japan, Australia, and New Zealand. Microsoft is incrementally adding support for more regions.

## Prerequisites

This section lists the requirements for using Finance insights. Wherever possible, links to sources of additional information are provided.

### System requirements

A Tier-2 environment (multi-box) is required to preview Finance insights. For background information about environments, see [Environment planning](../../fin-ops-core/fin-ops/imp-lifecycle/environment-planning.md).

### Version requirements

This article applies to Microsoft Dynamics 365 Finance version 10.0.21 and later.

### License requirements

Finance insights uses AI Builder credits to create financial predictions. All the necessary licenses for this are included with the tenant license. Each Dynamics 365 Finance tenant is provided 20,000 AI Builder credits each month. If additional credits are required for business needs, they can be purchased directly from AI Builder.

### Historical data requirements

At least one year's worth of customer invoices is required to correctly train the machine learning model that is used for the Customer payment predictions feature. Three years of historical data are recommended for cash flow forecasts. Three years of historical budget and/or actuals are recommended for intelligent budget proposals.

## Configure Finance insights

You must complete configuration steps before you can use Finance insights. For more information about how to configure Finance insights, see [Configuration for Finance insights](configure-for-fin-insites.md).

## Create a data integrator project

You'll need to create a data integrator project so that data that the machine learning model generates can flow into Dynamics 365 Finance. For the steps to create that project, see [Create a data integrator project](create-data-integrate-project.md).

## Enable Finance insights capabilities

When you've completed the configuration steps and set up demo data, you must turn on and set up each capability that you plan to use: customer payment predictions, cash flow forecasting, and budget proposals.

### Enable Customer payment predictions
If you are using demo data to test customer payment predictions, you may have to import additional demo data to create your AI model successfully. 

To enable Customer payment predictions, you must complete a set of steps to build a machine learning model that uses your organization's data to generate predictions about when customers are likely to pay outstanding invoices and when specific invoices are likely to be paid. For more information and the specific steps to complete, see [Enable customer payment predictions](enable-cust-paymnt-prediction.md). 

### Enable Cash flow forecasting
To enable Cash flow forecasting, you must complete a set of steps to build a machine learning model that uses your organization's data to generate cash flow forecasts. For more information and the specific steps to complete, see [Enable cash flow forecasting](enable-cash-flow-forecasting.md).

### Enable budget proposals

The Budget proposals feature uses a machine learning model along with your organization's historical data to generate a budget proposal. The generated proposal can help you begin a budgeting process that is more effective and efficient than a manual process. For the specific steps to enable this feature, see [Enable budget proposals](enable-budget-proposal.md). 

## Using Finance insights features

### Using Customer payment predictions

- To learn how Customer payment predictions can provide the information that is required to proactively begin collection activities, see [Use Customer payment predictions](use-customer-payment-predictions.md).
- For information that can help you evaluate the effectiveness of the prediction model after you've started using the feature, see [Evaluate the initial customer payment prediction model](evaluate-payment-prediction.md).
- For information that can help you adjust the data that is used to build the prediction and thereby improve its effectiveness, see [Improve the prediction model](improve-model.md).
- To learn more about the results of AI prediction models, see [Results of machine learning models](confusion-matrix.md).

### Using Cash flow forecasts

The Cash flow forecast capability can help you more accurately estimate your cash position. The intelligent cash flow forecasting is built on top of the existing cash flow forecasting functionality in Dynamics 365 Finance. To review the existing capability, see [Cash flow forecasting](../cash-bank-management/cash-flow-forecasting.md).

- To learn about the new capabilities in Cash flow forecasts, see [Cash flow forecast](cash-flow-forecast-intro.md).
- For information about importing external data to include in your cashflow forecast here, see [Use external data in cash flow forecasts](external-data-in-cash-flow.md). 
- For information about how to use an AI model to project near term cash flow, see [Cash position](cash-position.md).
- For information about saving cash flow positions and cash flow forecasts as snapshots, and to compare a snapshot to actuals, see [Snapshots overview](payment-snapshots.md).

### Using Budget proposal

For information about accelerating the creation of a budget, see [Budget proposals](budget-proposals.md). 

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
