---
title: Report 1007 for Colombia configuration
description: This article provides information about the required configuration for issuing the Format 1007 file for Colombia.  
author: Fhernandez0088 
ms.date: 11/10/2023 
ms.topic: articule
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Format 1007 file for Colombia issue configuration

This article will explain the necessary configurations to be done to issue a format 1007 file.
The format 1007 file informs the revenue received in a span of time by the company.

## Prerequisites

To print the report, it is necessary to meet the following prerequisites: 
* The legal entity address must be set in Colombia.
* Have both the country specific LATAM globalization feature and the general LATAM feature enabled.
* Import the configurations needed from the **Global** repository: 
	* LTM Tax Report
	* Format 1007 format

See [Download ER Configuration]( https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo?context=%2Fdynamics365%2Fcontext%2Ffinance) article.

* Configure ER parameters

See [ER configuration]( https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters) article.


## Configure application specific parameters

Lookups and conditions are designed to allow you to choose the combination of documents classification ids. and sales tax codes used in the transactions.

Once the prerequisites are met, follow these steps:
1. Go to **Organization administration > Workspaces > Electronic reporting**.
2. Select **Reporting configuration**.
3. On the left tree of content select **LTM Tax Report deployment > Format 1007**
4. In the top menu go to **Configurations > Application specific parameters > Setup**.

5. In the **Lookups** section select the first lookup “InvoiceAndCreditNoteIsApplicable”. This lookup will allow to select the document classes that are used for invoices and credit notes transactions that contain the company revenue.
6. On the **Conditions** section select **Add**
7. In the **Lookup result** field, select **Yes**
8. In the **Document classification id.** field, select an option from the list. Select the appropriate document class. 
9. On the **Conditions** section select **Add**
10. In the **Lookup result** field, select **No**
11. In the **Document classification id.** field, select **Blank**
12. On the **Conditions** section select **Add**
13. In the **Lookup result** field, select **No**
14. In the **Document classification id.** field, select **Not Blank**

> [!NOTE]
> The document classes selected in this configuration must be used in the company transactions to be listed in this report.

15. In the **Lookups** section select “MainAccountGroup”:
16. On the **Conditions** section, select **Add**
17. In the **Lookup result** field, select a concept:
* 4001: common activities revenue.
* 4002: other activities revenue.
* 4003: financial interest revenue.
* 4004: mortgage interest revenue.
18. In the **Main Account** field, select an option from the list. 
19. On the **Conditions** section select **Add**.
20. In the **Lookup result** field, select **N/A**.
21. In the **Main account** field, select **Blank**.
22. On the **Conditions** section select **Add**
23. In the **Lookup result** field, select **N/A**.
24. In the **Main account** field, select **Not Blank**.

> [!NOTE]
> The ledger accounts selected in this configuration must be used in the company transactions to be listed in this report.

## Issue format 1007 file:

1. Go to Tax > Inquiries and reports > LATAM > Tax reporting.
2. In the Format mapping field, select a **Format 1007**.
3. Select OK.
4. Select a date range.
6. Select OK.
