---
# required metadata

title: Cash flow forecast (preview)
description: This topic describes the Cash flow forecasting capability.
author: ShivamPandey-msft
manager: AnnBe
ms.date: 05/19/2020
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
# ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 14151
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2020-05-19
ms.dyn365.ops.version: AX 10.0.12

---

# Cash flow forecast (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Cash flow is critical to any business. Even profitable companies can face insolvency if they don't maintain the cash flow to meet immediate needs. The cash flow forecasting capability in Finance insights can help companies monitor and manage their cash balances effectively. This feature uses machine learning to help businesses forecast cash flows more accurately than they have previously. It can also help managers make decisions that optimize opportunities in the context of their current cash position. 

For most companies, managing cash flow and running cash flow forecasting is a tedious, repetitive, and manual process. Most companies rely on Microsoft Excel solutions that have varying degrees of complexity. The challenges of accurately forecasting cash flow include the following:

- Data isn't available to decision makers because it's scattered in multiple places, including: 
  - The accounting or enterprise resource planning system
  - Financial planning software
  - Excel
  - Additional software applications 
- Forecasting is based on internal knowledge that resides in "silos" within each domain or department.
- Measuring the accuracy of cash flow forecasting after the financials have been realized is uncertain and difficult.
	
## Details of the Cash flow forecasts capability
The Cash flow forecasts feature includes the following functionality. 

- Makes it easy to integrate cash flow data from external systems to Dynamics 365 Finance. Cash flow forecasts can also use the data import-export framework. This framework makes it easy to integrate with Excel OData. You can also combine data from multiple sources to create a comprehensive cash flow solution. 

- Introduces intelligent cash position. Cash position is created  based on customer’s payment behavior to predict when a company can expect cash to arrive in their accounts. It also analyzes the historical patterns of paying vendors, to predict when future invoices and orders are likely to be paid. 

- Introduces intelligent cash flow forecasting for long-term forecasting, using time series forecasting through automated integration with AI Builder.

- Provides the ability to save specific cash flow position or forecasts, edit them, and then easily compare and measure the forecast performance to the actual financials.

- Enables what-if analysis through snapshot comparison. For example, you can create multiple snapshots that represent optimistic, pessimistic, and the most realistic views of your cash flow, and then compare and view the differences.

- Provides the ability to view the cash flow forecast in multiple currencies, across legal entities, and filter and view cash flow related to a bank account. 

- Lets you filter and view bank accounts that are related to financial dimensions.

The cash flow forecasting functionality in Dynamics 365 Finance will empower your organization to transform tedious, complex, yet repetitive cash flow projection to a simple, automated process. Automating the most tedious aspects of cash flow forecasting lets you focus on critical decision making to drive desired business outcomes.

## Setting up Dimensions for Cash flow forecasting
A new tab on the **Cash flow forecasting setup** page lets you control what financial dimensions to use for filtering in the **Cash flow forecasting** workspace. This tab will only appear when the Cash flow forecasts feature is enabled. 

On the **Dimensions** tab, choose from the list of dimensions to use for filtering, and use the arrow keys to move them to the right-hand column. Only two dimensions can be selected for filtering cash flow forecast data. 

#### Privacy notice
Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.
