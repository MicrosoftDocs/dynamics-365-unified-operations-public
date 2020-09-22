---
# required metadata

title: Finance Insights home page (preview)
description: This topic walks through the prerequisites and the broad steps required for using a trial version of Finance Insights. 
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
# Finance Insights home page (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Finance Insights provides configurable and extensible models to help you accurately and intelligently predict your company’s cash flow, predict when you'll receive payment for outstanding receivables, and generate a budget proposal that can speed up your budgeting process. All these features are based on intelligent, machine learning models. These new capabilities, paired with automation in vendor payments and collections, provide a rich and intelligent financial system to drive decision making and help you take actions that respond effectively to current and anticipated business challenges.

Finance Insights preview is available to for trial deployments in the United Stated of America, Europe and United Kingdom. We are incrementally adding support in additional regions.

Public preview features should only be enabled on Tier 2 sandbox environments. Setup and AI models created in sandbox environment can't be migrated to a production environment. See [Supplemental Terms of Use for Microsoft Dynamics 365 Previews](https://docs.microsoft.com/dynamics365/legal/supp-dynamics365-preview#:~:text=Supplemental%20Terms%20of%20Use%20for%20Microsoft%20Dynamics%20365,%28governing%20your%20use%20of%20Microsoft%20Dynamics%20365%20Online%29.) for more information.

## Prerequisites

A list of the requirements for using Finance Insights follows, along with links to sources of additional information where possible. 

### Legal requirements
To apply for the preview program, please fill out [Finance Insights Preview for Dynamics 365 Finance agreement](https://forms.office.com/FormsPro/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR56j8lZs0FdAvwT75_WNFyxUM1c0Uzc1RFpaU1RVTEwxVTNWUERPRThUSy4u).   

### System requirements
A Tier 2 Sandbox environment (multi-box) is required to preview Finance Insights. For more background on environments, please see [Environment planning](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/imp-lifecycle/environment-planning).

### Version information
This document applies to Finance and Operations 10.0.11 (PU35) or after.

### Historical data needs
At least one year of customer invoices is needed to properly train the machine learning model used for customer payment predictions. 

Sample data is available for demo systems that have the Contoso demo data set on them. 

### Roles and permissions
Changes will be made to Microsoft Dynamics 365 for Finance, Lifecycle Services, PowerApps, and Azure. Proper permissions will be required across these three environments. For example:

- A new environment will be created in the Power Platform.
- A storage account, key vault, and application will be created in Azure.
- The AI Builder application will need to be authorized to access the data lake by the Active Directory tenant administrator.
- Feature will be enabled in Dynamics 365.

Familiarity with creating and managing resources in Azure, CDS, and Lifecycle Services (LCS) will be helpful for completing this process.

## Configuring Finance Insights 

Some configuration steps must be completed to use Finance Insights. For more information about the procedures that configure Finance Insights see [Configuration for Finance Insights](configure-for-fin-insites.md).

### Configure CDS and Azure resouces
Complete the steps described in [Configuration for Finance Insights](configure-for-fin-insites.md) to configure CDS and Azure resources.

### Create data integrator project
Create a data integrator project to flow data back into Dynamics 365 for Finance by completing the steps in [Create data integrator project](create-data-integrate-project.md).  

## Enable Finance Insights capabilities

When you've completed the configuration steps and set up demo data, you must also enable each of the capabilities that you plan to use, Cash flow forecasts, Customer payment predictions, and Budget proposals. 

### Enable customer payment predictions
Complete the steps described in [Enable Customer payment predictions](enable-cust-paymnt-prediction.md) to build and use a machine learning model along with your organization's data to generate predictions of when customers are likely to pay outstanding invoices, as well as predictions of when specific invoices are likely to be paid.

### Enable cashflow forecasting
Complete the steps described in [Enble Cash flow forecasts](enable-cash-flow-forecasting.md) to build and use a machine learning model along with your organization's data to generate cash flow forecasts.
  
### Enable Budget proposals
Complete the steps described in [Enable Budget proposals](enable-budget-proposal.md) to use a machine learning model along with your organization's historical data to generate a budget proposal that help you begin your budgeting process with effectiveness than a manual process provides. 

### Setup and use Cash flow forecasting
To see the steps to set up and use cash flow forecasting, see [Enable Cash flow forecasting](enable-cash-flow-forecasting.md). To learn more about how to use this capability, see [Cash flow forecasting](cash-flow-forecast-intro.md).

## Understand and improve initial payment predictor model

See [Evaluate the initial customer payment prediction model](evaluate-payment-prediction.md) for information that can help you evaluate the effectiveness of the prediction model, or [Improve the prediction model](improve-model.md) for information help you adjust the data that's used to build the predcition so improve its effectiveness.

#### Privacy notice
Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.
