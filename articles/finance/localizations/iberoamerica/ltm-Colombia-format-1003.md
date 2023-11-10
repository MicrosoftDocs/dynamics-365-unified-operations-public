---
title: Format 1003 file for Colombia issue configuration
description: This article provides information about the required configuration for issuing the Format 1003 file for Colombia. 
author: Fhernandez0088 
ms.date: 11/10/2023 
ms.topic: articule
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Format 1003 file for Colombia issue configuration

This article will explain the necessary configurations to be done to issue a format 1009 file.
This report informs withholding taxes that were suffered by the company in a period of time and the entities that practiced them.

## Prerequisites

To print the report, it is necessary to meet the following prerequisites: 
* The legal entity with an address in a country within the LATAM localization.
* Have both the country specific LATAM feature and the general feature activated.
* Import the configurations needed from the **Global** repository:
		* LTM Tax Report
		* Format 1003 file

See [ER download reports](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo?context=%2Fdynamics365%2Fcontext%2Ffinance) article.

* Configure ER parameters

 [ER configuration]( https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters)

## Configure application specific parameters for format 1003

Lookups and conditions are designed to allow you to choose the combination of documents classification ids., tax codes, and ledger accounts used in the transactions that are shown in this report.

Once the prerequisites are met, follow these steps:
1. Go to **Organization administration > Workspaces > Electronic reporting**.
2. Select **Reporting configuration**.
3. On the left tree of content select **LTM Tax Report deployment > Format 1003**
4. In the top menu go to **Configurations > Application specific parameters > Setup**.
5. In the **Lookups** section select the first lookup “ApplicableInvoice”. This lookup will allow to select the document classes that are used for posting third sales transactions.
6. On the Conditions section, Select **Add**
7. In the **Lookup result** field, select **Yes**
8. In the **Document classification id.** field, select an option from the list. Select the appropriate document class (usually sales invoices or debit notes). 
9. On the **Conditions** section select **Add**
10. In the **Lookup result** field, select **No**
11. In the **Document classification id.** field, select **Blank**
12. On the **Conditions** section select **Add**
13. In the **Lookup result** field, select **No**
14. In the **Document classification id.** field, select **Not Blank**

> [!NOTE]
> The document classes selected in this configuration must be used in the company transactions to be listed in this report.

15. In the **Lookups** section select “Concept”.
16. On the **Conditions** section select an option of the following **Add**
17. In the **Lookup Result** field select an option of the following (add as many as needed):

    * **1301**: Withholding for salaries, benefits, and other labor payments.
    * **1302**: Sales withholdings.
    * **1303**: Withholding taxes for services.
    * **1304**: Withholding taxes for fees.
    * **1305**: Withholding taxes for commissions.
    * **1306**: Withholding taxes for interest and financial returns.
    * **1307**: Withholding taxes for leases.
    * **1308**: Withholding taxes for other concepts.
    * **1309**: sales tax withholdings.
    * **1310**: Withholding for dividends and participations. Not including the value reported in concept 1320.
    * **1311**: Withholding taxes for the sale of fixed assets of natural persons
    * **1312**: Withholding taxes for deposits from debit and credit cards.
    * **1313**: Withholding taxes for lotteries, raffles, bets and similar.
    * **1314**: Withholding taxes for stamp taxes.

18. In the **Tax code** field, select a tax code from the list that represents the concept selected.  
19. On the conditions section select **Add**
20. In the **Lookup result** field, select **N/A**
21. In the ** the type of tax.** field, select **Blank**.
22. On the conditions section select **Add**.
23. In the **Lookup result** field, select **N/A**.
24. In the ** the type of tax** field, select **Not Blank**.

> [!NOTE]
> The tax codes selected in this configuration must be used in the company transactions to be listed in this report.


## Issue file 1003 format

1. Go to Tax > Inquiries and reports > LATAM > Tax reporting.
2. In the Format mapping field, select a **Format 1003**.
3. Select OK.
4. Select a date range.
6. Select OK.
