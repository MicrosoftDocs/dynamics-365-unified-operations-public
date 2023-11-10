---
title: Format 1009 file for Colombia issue configuration
description: This article provides information about the required configuration for issuing a Format 1009 file for Colombia. 
author: Fhernandez0088 
ms.date: 11/10/2023 
ms.topic: articule
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Format 1009 file for Colombia issue configuration

This article will explain the necessary configurations to be done to issue a format 1009 file.
This report informs the company’s liabilities from a period of time.

## Prerequisites

To print the report, it is necessary to meet the following prerequisites: 
* The legal entity with an address in a country within the LATAM localization.
* Have both the country specific LATAM globalization feature and the general LATAM feature enabled.
* Import the configurations needed from the **Global** repository:
		* LTM Tax Report
		* Format 1009 file

See [ER download reports](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo?context=%2Fdynamics365%2Fcontext%2Ffinance) article.

* Configure ER parameters.

See [ER configuration]( https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters) article.

## Configure application specific parameters for format 1009 file.

Lookups and conditions are designed to allow you to choose the combination of documents classification ids. and ledger account numbers used in the transactions that are shown in this report.

Once the prerequisites are met, follow these steps:
1. Go to **Organization administration > Workspaces > Electronic reporting**.
2. Select **Reporting configuration**.
3. On the left tree of content select **LTM Tax Report deployment > Format 1009**
4. In the top menu go to **Configurations > Application specific parameters > Setup**.

5. In the **Lookups** section select the first lookup “IsApplicable”. This lookup will allow to select the document classes that are used for vendor invoices, credit notes, debit notes, and payments transactions.
6. On the **Conditions** section select **Add**.
7. In the **Lookup result** field, select **Yes**.
8. In the **Document classification id.** field, select an option from the list. Select the appropriate document class (vendor invoices, credit notes, debit notes and vendor payments). 
9. On the **Conditions** section select **Add**.
10. In the **Lookup result** field, select **No**.
11. In the **Document classification id.** field, select **Blank**
12. On the **Conditions** section select  **Add**
13. In the **Lookup result** field, select **No**
14. In the **Document classification id.** field, select **Not Blank**

> [!NOTE]
> The document classes selected in this configuration must be used in the company transactions to be listed in this report.

15. In the **Lookups** section select “MainAccountGroups”:
16. On the **Conditions** section, select **Add**
17. In the **Lookup result** field, select a concept:

    * **2201**: liabilities with national vendors.
    * **2202**: liabilities with related companies, shareholders, and partners.
    * **2203**: financial liabilities.
    * **2204**: liabilities for taxes, levies, and fees.
    * **2206**: other liabilities
    * **2207**: total liabilities determined by an actuarial calculation.
    * **2208**: liabilities supported by a document with a certain date.
    * **2209**: liabilities of insurance companies.
    * **2211**: liabilities for judicial deposits.
    * **2212**: liability for deferred income for award points awarded in loyalty training programs.
    * **2213**: liability for deferred income contemplated in the E.T. art.23-1.
    * **2214**: liabilities for parafiscal contributions, health, pension, and severance pay.
    * **2215**: labor liabilities held by the worker, without layoffs.

18. In the **Main Account** field, select a ledger account from the list. 
19. On the **Conditions** section select **Add**.
20. In the **Lookup result** field, select **N/A**.
21. In the **Main account** field, select **Blank**.
22. On the **Conditions** section select **Add**
23. In the **Lookup result** field, select **N/A**.
24. In the **Main account** field, select **Not Blank**.

> [!NOTE]
> The ledger accounts selected in this configuration must be used in the company transactions to be listed in this report.

## Run file 1009 format

1. Go to Tax > Inquiries and reports > LATAM > Tax reporting.
2. In the Format mapping field, select a **Format 1009**.
3. Select OK.
4. Select a date range.
6. Select OK.
