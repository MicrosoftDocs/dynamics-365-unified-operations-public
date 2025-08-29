---
title: Printing configuration for the Withholding certificate format for Colombia
description: Learn how to set up and generate a Withholding certificate format for Colombia.
ms.date: 08/28/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
author: Fhernandez0088
ms.author: v-federicohe
---

# Printing configuration for the Withholding certificate format for Colombia

This article explains how to set up and generate the three withholding certificate formats for Colombia in Microsoft Dynamics 365 Finance. These formats correspond to VAT withholdings, Income withholdings and ICA Withholdings.

It includes information derived from vendor transactions such as invoices, debit notes, and credit notes, and reflects the calculated withholdings for income tax (FTE), industry and commerce tax (ICA), and value-added tax (IVA). These certificates serve as official documentation for the amounts withheld and reported to the DIAN, supporting both fiscal transparency and legal compliance.

## Prerequisites

Before you can generate the report, the following prerequisites must be met:

- The legal entity's address must be in Colombia.
- You must enable both the general Latin American (LATAM) feature and the country/region-specific LATAM feature for Colombia.
- You must download the specific report configuration from the Dataverse configuration repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

- The following formats must be downloaded from the Dataverse:
    - :::no-loc text="LTM Tax Report":::
    - :::no-loc text="LTM Tax Report mapping":::
    - :::no-loc text="COL Withholding Certificate FTE":::
    - :::no-loc text="COL Withholding Certificate ICA":::
    - :::no-loc text="COL Withholding certificate IVA":::
   
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters for the Withholding certificate format for Colombia.
To configure application-specific parameters, follow these steps.

### To configure COL Withholding Certificate FTE format: 

1. In Dynamics 365 Finance, go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations** \> **LTM Tax Report** 
1. Select the **COL Withholding Certificate FTE** format.
1. On the Action Pane, in the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendInvoiceIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all invoices document classes that are required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.
 1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendCreditNoteIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all Credit note document classes that are required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.
1. On the **Lookups** FastTab, select **TaxIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Tax code** field, select the tax codes that are used as income withholding tax.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.

### To configure COL Withholding Certificate ICA format: 

In Dynamics 365 Finance, go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations** \> **LTM Tax Report** 
1. Select the **COL Withholding Certificate ICA** format.
1. On the Action Pane, in the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendInvoiceIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all invoices document classes that are required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.
 1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendCreditNoteIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all Credit note document classes that are required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.
1. On the **Lookups** FastTab, select **TaxIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Tax code** field, select the tax codes that are used as ICA withholding tax .
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.

### To configure COL Withholding certificate IVA format: 

In Dynamics 365 Finance, go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations** \> **LTM Tax Report** 
1. Select the **COL Withholding certificate IVA** format.
1. On the Action Pane, in the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendInvoiceIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all invoices document classes that are required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.
 1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendCreditNoteIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all Credit note document classes that are required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.
1. On the **Lookups** FastTab, select **TaxIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Tax code** field, select the tax codes that are used as VAT withholding tax.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.

> [!NOTE]
> On the certificate, the **Concept** column will show the name of the ledger account being used for the withholding tax line.

> [!NOTE]
> The tax codes and document classes configured in lookups must be previously used in transactions to appear in the certificate formats.

## Generate the Withholding certificate format for Colombia.

To generate the certificate follow these steps.

1. In Dynamics 365 Finance, go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select the name of format that you need generate ( :::no-loc text="COL Withholding Certificate FTE"::: , :::no-loc text="COL Withholding Certificate ICA"::: or :::no-loc text="COL Withholding certificate IVA"::: ),  and then select **OK**.
1. In the **From date** and **To date** fields, specify the date range for the report.
1. Select **OK**.
