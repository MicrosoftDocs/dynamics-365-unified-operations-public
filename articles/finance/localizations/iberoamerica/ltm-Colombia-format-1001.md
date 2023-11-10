---
title: Format 1001 file for Colombia issue configuration
description: This article provides information about the required configuration for issuing the Format 1001 file for Colombia. 
author: Fhernandez0088 
ms.date: 11/10/2023 
ms.topic: articule
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Format 1001 file for Colombia issue configuration

This article will explain the necessary configurations to be done to issue a format 1001 file.
This report informs the expenses paid to third parties and the taxes, and withholding taxes that those transactions generated.

## Prerequisites

To print the report, it is necessary to meet the following prerequisites: 
* The legal entity with an address in a country within the LATAM localization.
* Have both the country specific LATAM feature and the general feature activated.
* Import the configurations needed from the **Global** repository:
		* LTM Tax Report
		* Format 1001 file

See [ER download reports](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo?context=%2Fdynamics365%2Fcontext%2Ffinance) article.

* Configure ER parameters

 See [ER configuration]( https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters) article.

## Configure application specific parameters for format 1001

Lookups and conditions are designed to allow you to choose the combination of documents classification ids., tax codes, and ledger accounts used in the transactions that are shown in this report.

Once the prerequisites are met, follow these steps:
1. Go to **Organization administration > Workspaces > Electronic reporting**.
2. Select **Reporting configuration**.
3. On the left tree of content select **LTM Tax Report deployment > Format 1001**
4. In the top menu go to **Configurations > Application specific parameters > Setup**.
5. In the **Lookups** section select the first lookup “ApplicableInvoice”. This lookup will allow to select the document classes that are used for posting third party expenses.
6. On the Conditions section, Select **Add**
7. In the **Lookup result** field, select **Yes**
8. In the **Document classification id.** field, select an option from the list. Select the appropriate document class (usually vendor invoices or debit notes). 
9. In the **Conditions** section select **Add**
10. In the **Lookup result** field, select **No**
11. In the **Document classification id.** field, select **Blank**
12. On the **Conditions** section select **Add**
13. In the **Lookup result** field, select **No**
14. In the **Document classification id.** field, select **Not Blank**

> [!NOTE]
> The tax codes selected in this configuration must be used in the company transactions to be listed in this report.

15. In the **Lookups** section select “MainAccountGroup_NoDeduc”.
16. On the **Conditions** section select **Add**
17. In the **Lookup Result** field select **5007**.
18. In the **Tax code** field, select a ledger account from the list that represents not fixed assets. 
19. On the **Conditions** section, Select **Add**
20. In the **Lookup result** field, select **5008 **.
21. In the **Main account** field, select a ledger account from the list that represents fixed assets. 
22. In the **Conditions** section Select **Add**
23. In the **Lookup result** field, select **N/A**
24. In the ** the type of tax.** field, select **Blank**
25. In the **Concepts** section Select **Add**
26. In the **Lookup result** field, select **N/A**
27. In the ** the type of tax** field, select **Not Blank**
28. In the **Lookups** section select “MainAccountGroup”:
29. On the **Conditions** section select **Add**
30. In the **Lookup Result** field select **5007**.
31. In the **Tax code** field, select a ledger account from the list that represents not fixed assets. 
32. On the Conditions section, Select **Add**
33. In the **Lookup result** field, select **5008 **.
34. In the **Main account** field, select a ledger account from the list that represents fixed assets. 
35. In the **Conditions** section select **Add**
36. In the **Lookup result** field, select **N/A**
37. In the ** the type of tax.** field, select **Blank**
38. Select **Add**
39. In the **Lookup result** field, select **N/A**
40. In the ** the type of tax** field, select **Not Blank**
> [!NOTE]
> The ledger accounts selected in this configuration must be used in the company transactions to be listed in this report.

41. In the **Lookups** section select “TaxType”.
42. On the **Conditions** section, select **Add**
43. In the **Lookup result** field, select the following:

    * **COMUN:** VAT withholding practiced common regime.
    * **IDED:** VAT higher value of the deductible cost or expense
    * **INDED:** VAT higher value of the non-deductible cost or expense
    * **NO DOM:** VAT withholding practiced to foreign.
    * **RASUMC:** CREE withholding suffered.
    * **RECREE:** CREE withholding practiced.
    * **RETA:** income withholding tax suffered.
    * **RTPE:** income withholding tax practiced.
    * **SIMP:** VAT withholding suffered simplified regime.

44. In the **Tax code** field, select an option from the list. Select the appropriate tax code for each concept lookup result added. 
45. Select **Add**
46. In the **Lookup result** field, select **N/A**
47. In the **Tax code** field, select **Blank**
48. Select **Add**
49. In the **Lookup result** field, select **No**
50. In the **Tax code** field, select **Not Blank**

> [!NOTE]
> The tax codes selected in this configuration must be used in the company transactions to be listed in this report.

## Issue file 1001 format

1. Go to Tax > Inquiries and reports > LATAM > Tax reporting.
2. In the Format mapping field, select a **Format 1001**.
3. Select OK.
4. Select a date range.
6. Select OK.


