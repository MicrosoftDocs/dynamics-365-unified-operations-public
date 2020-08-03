---
# required metadata

title: Finance Insights administration (preview)
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
# Finance Insights administration (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Finance Insights public preview is available to for trial deployments in the United Stated of America, Europe and United Kingdom. We are incrementally adding support in additional regions.

Public preview features should only be enabled on Tier 2 sandbox environments. Setup and AI models created in sandbox environment may not be migrated to a production environment. Please read Supplemental Terms of Use for Microsoft Dynamics 365 Previews for more details.

## System requirements
A Tier 2 Sandbox environment (multi-box) is required to preview Finance Insights. For more background on environments, please see [Environment planning](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/imp-lifecycle/environment-planning).

## Legal requirements
To apply for the preview program, please fill out [Finance Insights Preview for Dynamics 365 Finance agreement](https://forms.office.com/FormsPro/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR56j8lZs0FdAvwT75_WNFyxUM1c0Uzc1RFpaU1RVTEwxVTNWUERPRThUSy4u).   

## Version information
This document applies to Finance and Operations 10.0.11 (PU35) or after.

### Historical data needs
At least one year of customer invoices is needed to properly train the machine learning model used for customer payment predictions. 

Sample data is available for demo systems that have the Contoso demo data set on them. 

## Prerequisites
Changes will be made to Microsoft Dynamics 365 for Finance, PowerApps, and Azure.  Proper permissions will be required across these three environments. For example:

- A new environment will be created in the Power Platform.
- A storage account, key vault, and application will be created in Azure.
- The AI Builder application will need to be authorized to access the data lake by the Active Directory tenant administrator.
- Feature will be enabled in Dynamics 365.

Familiarity with creating and managing resources in Azure, CDS, and Lifecycle Services (LCS) will be  helpful for completing this process.

## Deploy the F&O environment

Complete the following steps to deploy the Dynamics 365 Finance and Operations envrionment. 

1. Create or update an F&O environment in LCS. The environment needs App Version 10.0.11/Platform Update 35 or later versions.
2. The environment must be an HA environment in Sandbox (also known as a Tier-2 environment).  Please see [Environment planning](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/imp-lifecycle/environment-planning) for more details.
3. If using Contoso demo data, additional sample data is required to use payment predictions, cashflow forecasting, and budget forecasting.  Please follow the steps at <TBD> to add the sample data needed (content for payment predictor at [Financials R&D All](https://microsoft.sharepoint.com/:f:/t/FinancialsRDAll909/Essk-ZaYVvxPrKNIHmbJNS8BWKCMxcMsubO_NVxECcsLfg?e=iwOR9e)

### Set up the data lake
Complete the steps described in [Azure Data Lake overview](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/azure-data-lake-overview) to set up an Azure Data Lake Storage and supporting resources in your Azure subscription.

### Configure entity store
Complete the steps described in [Make Entity store available as a Data Lake](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/entity-store-data-lake) to set up the entity store that uses the Azure resources from the previous step.

### Configure CDS resources and Power AI
Complete the steps described in <TBD> to configure the required CDS resources (content at Configure CDS and Configure AI builder integrator).

### Enable customer payment predictions
Complete the steps described in <TBD> to configure the required CDS resources (content at Enable Customer Payment Predictions… potentially embed the content).

### Create data integrator project
After creating a model in the previous step, create a data integrator project to flow data back into Dynamics 365 for Finance by completing the steps in <TBD> (content at Create Data Integrator Project).  

### Understand and improve initial payment predictor model
See [Evaluate the initial customer payment prediction model](https://review.docs.microsoft.com/en-us/dynamics365/finance/finance-insights/evaluate-payment-prediction?branch=bob-fi-evaluate-payment-prediction) for information that can help you evaluate the effectiveness of the prediction model, or [Improve the prediction model](https://review.docs.microsoft.com/en-us/dynamics365/finance/finance-insights/improve-model?branch=bob-fi-improve-model) for information help you adjust the data that's used to build the predcition so improve its effectiveness. 

Follow the guides at <TBD> to understand and improve the initial payment predictor model (contact at https://microsoft.sharepoint.com/:w:/t/AIforOAG/EahnJjqfQBlMrKRX4oYe_uUBpgtY9UsPXzeU17ERbIrEqA?e=FvJF0f and https://microsoft.sharepoint.com/:w:/t/AIforOAG/EbAsTOn26blNrFQLzMh8VgMBLHcqhxO8I1VfKrURUEP29w?e=8j3tPm).

### Enable cashflow forecasting
Complete the steps described in <TBD> to enable cashflow forecasting (content at Enable Cashflow forecasting… potentially embed the content).

### Setup and use cashflow forecasting
Follow the steps described in <TBD> to setup and use cashflow forecasting. For more information, see [Set up Cash flow forecasting]() 
(content at https://microsoft.sharepoint.com/:w:/t/FinancialsRDAll909/ER8QIZ77pnBArbigDMiJx0EBlAYLh8cfTIaBeUVOzKCHtg?e=8xMqK6).

### Provide feedback to Microsoft
Part of your commitment as part of this preview program is to provide feedback to Microsoft.  Please complete the relevant portions of <TBD>.  Multiple users at your company can fill out the survey if they have participated in any step of the process or evaluated the feature. The steps to complete are lised in the [Setting up Finance Insights](https://microsoft.sharepoint.com/:w:/t/AIforOAG/EXwSu5F8R2VLvYcjp20ct_oBmoZXpqz0l9L1OcaNoyPNrA?e=tLBOjI) document. 

