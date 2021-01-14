---
# required metadata

title: Use external data in cash flow forecasts (preview)
description: This topic describes the setup steps that you must complete so that external data can be entered or imported into cash flow forecasts.
author: rcarlson
manager: AnnBe
ms.date: 05/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalSetup, LedgerJournalTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 15721
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2020-06-08
ms.dyn365.ops.version: AX 10.0.12

---
# Use external data in cash flow forecasts (preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

External data can be entered or imported into cash flow forecasts. This topic describes the setup steps that are specific to the use of external data and that enable the external data to be included in a cash flow forecast.

## External data setup

Use the **External source** tab on the **Cash flow forecast setup** page (**Cash and bank management \> Cash flow forecasting**) to enter settings that support the use of external data in cash flow forecasts.

For more information about the setup, see [Cash flow forecasting](https://docs.microsoft.com/dynamics365/finance/cash-bank-management/cash-flow-forecasting).

To enter external data for cash flow forecasts, you can use the Open in Excel experience for entering and modifying external data. Select the **External data** button, and then select either **Add External Data** or **Edit existing external data**. When the Microsoft Excel file is opened, you can enter information in the following fields:

- **Entry ID**
- **Description** (optional)
- **External Source name** – Select one of the values in the list that you defined when you set up Finance Insights.
- **Legal Entity**
- **Date**
- **Amount in transaction currency**
- **Currency Code**
- **Default Dimension** (optional)
- **Document number** (optional)
- **Account number** (optional)
- **Account name** (optional)

## Importing external data by using the Data Management framework

You can import external data for cash flow forecasts by using the **Data Management** workspace and the entity that is named **Cash flow forecast external source entry**.

Additionally, if you must move setup data from one environment to another, the following entities area available for the setup tables that are required:

- Cash flow forecast external source setup
- Cash flow forecast external source legal entity setup

#### Privacy notice
Previews (1) might use less privacy and fewer security measures than the Dynamics 365 Finance and Operations service, (2) aren't included in the service level agreement (SLA) for this service, (3) should not be used to process personal data or other data that is subject to legal or regulatory compliance requirements, and (4) have limited support.
