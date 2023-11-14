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

This article explains how to setup and configure information so that you can issue a format 1001 file. The Format 1001 file report provides a list of expenses paid to third parties and the taxes and withholding taxes that those transactions generated.

## Prerequisites

Before you print this report, the following prerequisites must be met:

- The legal entity with an address in a country within the LATAM localization.
- Have both the country specific LATAM feature and the general feature activated.
- Import the configurations needed from the **Global** repository:

   - LTM Tax Report
   - Format 1001 file

    For more information, see [ER download reports](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Configure the Electronic reporting (ER) parameters. To learn more, see [ER configuration](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters for format 1001

Lookups and conditions are designed so you can choose the combination of documents classification IDs, tax codes, and ledger accounts used in the transactions that are shown in this report.

After the prerequisites are met, follow these steps:

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting** and select **Reporting configuration**.
2. On the left, select **LTM Tax Report deployment** > **Format 1001**.
3. On the Action Pane, select **Configurations** > **Application specific parameters** > **Setup**.
4. In the **Lookups** section, select the first lookup **ApplicableInvoice**. Use this lookup to select the document classes that are used for posting third party expenses.
5. In the Conditions section, select **Add**

   1. In the **Lookup result** field, select **Yes**
   2. In the **Document classification id.** field, select an option from the list. Select the appropriate document class (usually vendor invoices or debit notes). 

6. In the **Conditions** section select **Add**.

    1. In the **Lookup result** field, select **No**
    2. In the **Document classification id.** field, select **Blank**

7. On the **Conditions** section select **Add**

    1. In the **Lookup result** field, select **No**
    2. In the **Document classification id.** field, select **Not Blank**

    > [!NOTE]
    > The tax codes selected in this configuration must be used in the company transactions to be listed in this report.
    
8. In the **Lookups** section select **MainAccountGroup_NoDeduc**.
9. On the **Conditions** section select **Add**

    1. In the **Lookup Result** field select **5007**.
    2. In the **Tax code** field, select a ledger account from the list that represents non-fixed assets. 

10. On the **Conditions** section, Select **Add**.

    1. In the **Lookup result** field, select **5008**.
    2.  In the **Main account** field, select a ledger account from the list that represents fixed assets. 

11. In the **Conditions** section Select **Add**.

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Blank**.

12. In the **Concepts** section Select **Add**.

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Not Blank**.

13. In the **Lookups** section select **MainAccountGroup**.
14. On the **Conditions** section select **Add**.

    1. In the **Lookup Result** field select **5007**.
    2. In the **Tax code** field, select a ledger account from the list that represents not fixed assets. 

15. In the **Conditions** section, select **Add**.

    1. In the **Lookup result** field, select **5008**.
    2. In the **Main account** field, select a ledger account from the list that represents fixed assets. 

16. In the **Conditions** section select **Add**.

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Blank**.
    3. Select **Add**.
    4. In the **Lookup result** field, select **N/A**.
    5. In the **Type of tax** field, select **Not Blank**.

    > [!NOTE]
    > The ledger accounts selected in this configuration must be used in the company transactions to be listed in this report.

17. In the **Lookups** section select **TaxType**.
18. In the **Conditions** section, select **Add**

    1. In the **Lookup result** field, select the following:

       - **COMUN:** VAT withholding practiced common regime.
       - **IDED:** VAT higher value of the deductible cost or expense.
       - **INDED:** VAT higher value of the non-deductible cost or expense.
       - **NO DOM:** VAT withholding practiced to foreign.
       - **RASUMC:** CREE withholding suffered.
       - **RECREE:** CREE withholding practiced.
       - **RETA:** income withholding tax suffered.
       - **RTPE:** income withholding tax practiced.
       - **SIMP:** VAT withholding suffered simplified regime.
  
    2. In the **Tax code** field, select an option from the list. Select the appropriate tax code for each concept lookup result added.
    3. Select **Add**, and in the **Lookup result** field, select **N/A**.
    4. In the **Tax code** field, select **Blank**.
    5. Select **Add**, and in the **Lookup result** field, select **No**.
    6. In the **Tax code** field, select **Not Blank**.

    > [!NOTE]
    > The tax codes selected in this configuration must be used in the company transactions that are listed in this report.

## Issue file 1001 format

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
2. In the **Format mapping** field, select **Format 1001**.
3. Select **OK**.
4. Select a date range and then select **OK**.


