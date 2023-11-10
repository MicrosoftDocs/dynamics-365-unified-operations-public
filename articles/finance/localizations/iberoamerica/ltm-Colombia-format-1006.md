---
title: Format 1006 file for Colombia issue configuration
description: This article provides information about the required configuration for issuing the Format 1006 file for Colombia. 
author: Fhernandez0088 
ms.date: 11/10/2023 
ms.topic: articule
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Format 1006 file for Colombia issue configuration

This article will explain the necessary configurations to be done to issue a format 1006 file.
This report informs VAT generated in sales, purchase devolutions and consumption taxes.

## Prerequisites

To print the report, it is necessary to meet the following prerequisites: 
* The legal entity with an address in a country within the LATAM localization.
* Have both the country specific LATAM feature and the general feature activated.
* Import the configurations needed from the **Global** repository:
		* LTM Tax Report
		* Format 1006 file

See [ER download reports](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo?context=%2Fdynamics365%2Fcontext%2Ffinance) article.

* Configure ER parameters

 See [ER configuration]( https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters) article.

## Configure application specific parameters for format 1006

Lookups and conditions are designed to allow you to choose the combination of documents classification ids. and tax codes used in the transactions that are shown in this report.

Once the prerequisites are met, follow these steps:
1. Go to **Organization administration > Workspaces > Electronic reporting**.
2. Select **Reporting configuration**.
3. On the left tree of content select **LTM Tax Report deployment > Format 1006**
4. In the top menu go to **Configurations > Application specific parameters > Setup**.
5. In the **Lookups** section select the first lookup “ApplicableCreditNote”. This lookup will allow to select the document classes that are used for purchases devolutions that contain VAT.
6. On the **Conditions** section select **Add**
7. In the **Lookup result** field, select **Yes**
8. In the **Document classification id.** field, select an option from the list. Select the appropriate document class (sales credit notes). 
9. On the **Conditions** section select **Add**.
10. In the **Lookup result** field, select **No**.
11. In the **Document classification id.** field, select **Blank**.
12. On the **Conditions** section select **Add**.
13. In the **Lookup result** field, select **No**.
14. In the **Document classification id.** field, select **Not Blank**.

> [!NOTE]
> The document classes selected in this configuration must be used in the company transactions to be listed in this report.

15. In the **Lookups** section select “TaxType”:
16. On the **Conditions** section select **Add**.
17. In the **Lookup Result** field select **Consumption tax**.
18. In the **Tax code** field, select an option from the list that represents consumption taxes. 
19. On the Conditions section, Select **Add**.
20. In the **Lookup result** field, select **Generated Tax **.
21. In the **Tax code** field, select an option from the list that represents the VAT generated in sales. 
22. On the Conditions section, Select **Add**.
23. In the **Lookup result** field, select **Tax Refund **.
24. In the **Tax code** field, select an option from the list that represents the VAT returns in purchases returns. 
25. On the **Conditions** section select **Add**.
26. In the **Lookup result** field, select **N/A**.
27. In the ** the type of tax.** field, select **Blank**.
28. On the **Conditions** section select **Add**.
29. In the **Lookup result** field, select **N/A**.
30. In the ** the type of tax** field, select **Not Blank**.

> [!NOTE]
> The tax codes selected in this configuration must be used in the company transactions to be listed in this report.

31. In the **Lookups** section select “ApplicableInvoice”:
32. On the Conditions section select **Add**.
33. In the **Lookup result** field, select **Yes**.
34. In the **Document classification id.** field, select an option from the list. Select the appropriate document class (purchase invoices). 
35. On the **Conditions** section select **Add**.
36. In the **Lookup result** field, select **No**.
37. In the **Document classification id.** field, select **Blank**
38. On the **Conditions** section select **Add**.
39. In the **Lookup result** field, select **No**.
40. In the **Document classification id.** field, select **Not Blank**.

> [!NOTE]
> The document classes selected in this configuration must be used in the company transactions to be listed in this report.

## Issue file 1006 format

1. Go to Tax > Inquiries and reports > LATAM > Tax reporting.
2. In the Format mapping field, select a **Format 1006**.
3. Select OK.
4. Select a date range.
6. Select OK.
