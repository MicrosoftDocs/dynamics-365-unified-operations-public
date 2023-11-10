---
title: Format 1005 file for Colombia issue configuration
description: This article provides information about the required configuration for issuing the Format 1005 file for Colombia. 
author: Fhernandez0088 
ms.date: 11/10/2023 
ms.topic: articule
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Format 1005 file for Colombia issue configuration

This article will explain the necessary configurations to be done to issue a format 1009 file.
This report informs VAT generated in purchases, and sales devolutions.

## Prerequisites

To print the report, it is necessary to meet the following prerequisites: 
* The legal entity with an address in a country within the LATAM localization.
* Have both the country specific LATAM feature and the general feature activated.
* Import the configurations needed from the **Global** repository:
		* LTM Tax Report
		* Format 1005 file

See [ER download reports](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo?context=%2Fdynamics365%2Fcontext%2Ffinance) article.

* Configure ER parameters

See [ER configuration]( https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters) article.

## Configure application specific parameters for format 1005

Lookups and conditions are designed to allow you to choose the combination of documents classification ids. and tax codes used in the transactions that are shown in this report.

Once the prerequisites are met, follow these steps:
1. Go to **Organization administration > Workspaces > Electronic reporting**.
2. Select **Reporting configuration**.
3. On the left tree of content select **LTM Tax Report deployment > Format 1005**
4. In the top menu go to **Configurations > Application specific parameters > Setup**.
5. In the **Lookups** section select the first lookup “ApplicableInvoice”. This lookup will allow to select the document classes that are used for vendor invoices that contain VAT.
6. On the Conditions section select **Add**
7. In the **Lookup result** field, select **Yes**
8. In the **Document classification id.** field, select an option from the list. Select the appropriate document class (vendor invoices). 
9. On the **Conditions** section select **Add**
10. In the **Lookup result** field, select **No**
11. In the **Document classification id.** field, select **Blank**
12. On the **Conditions** section select **Add**
13. In the **Lookup result** field, select **No**
14. In the **Document classification id.** field, select **Not Blank**
15. In the **Lookups** section select “ApplicableDebitNote”:
16. On the Conditions section, Select **Add**
17. In the **Lookup result** field, select **Yes**
18. In the **Document classification id.** field, select an option from the list. Select the appropriate document class (vendor debit note). 
19. On the **Conditions** section select **Add**
20. In the **Lookup result** field, select **No**
21. In the **Document classification id.** field, select **Blank**
22. On the **Conditions** section select **Add**
23. In the **Lookup result** field, select **No**
24. In the **Document classification id.** field, select **Not Blank**

> [!NOTE]
> The document classes selected in this configuration must be used in the company transactions to be listed in this report.

25. In the **Lookups** section select “TaxType”:
26. On the **Conditions** section, Select **Add**
27. In the **Lookup result** field, select **Tax credit **.
28. In the **Tax code** field, select an option from the list that represents the VAT. 
29. On the Conditions section, Select **Add**
30. In the **Lookup result** field, select **Vat Return **.
31. In the **Tax code** field, select an option from the list that represents the VAT returns in sales returns. 
32. On the **Conditions** section select **Add**
33. In the **Lookup result** field, select **N/A**
34. In the ** the type of tax.** field, select **Blank**
35. On the **Conditions** section select **Add**
36. In the **Lookup result** field, select **N/A**
37. In the ** the type of tax** field, select **Not Blank**

> [!NOTE]
> The tax codes selected in this configuration must be used in the company transactions to be listed in this report.

38. In the **Lookups** section select “ApplicableCreditNote”:
39. On the Conditions section select **Add**
40. In the **Lookup result** field select **Yes**.
41. In the **Document classification id.** field, select an option from the list. Select the appropriate document class (vendor credit note). 
42. On the **Conditions** section select **Add**.
43. In the **Lookup result** field, select **No**.
44. In the **Document classification id.** field, select **Blank**.
45. On the **Conditions** section select **Add**.
46. In the **Lookup result** field, select **No**.
47. In the **Document classification id.** field, select **Not Blank**.

## Issue file 1005 format

1. Go to Tax > Inquiries and reports > LATAM > Tax reporting.
2. In the Format mapping field, select a **Format 1009**.
3. Select OK.
4. Select a date range.
6. Select OK.
