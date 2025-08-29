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

This article explains how to set up and generate three withholding certificate formats for Colombia in Microsoft Dynamics 365 Finance. These formats include VAT withholdings, income withholdings, and ICA withholdings.

It includes information from vendor transactions like invoices, debit notes, and credit notes, and shows the calculated withholdings for income tax (FTE), industry and commerce tax (ICA), and value-added tax (IVA). These certificates are official documentation for the amounts withheld and reported to the DIAN. They ensure fiscal transparency and legal compliance.

## Prerequisites

Before generating the report, make sure the following prerequisites are met:

- The legal entity's address must be in Colombia.
- Enable the general Latin American (LATAM) feature and the country/region-specific LATAM feature for Colombia.
- Download the specific report configuration from the Dataverse configuration repository. For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

- Download the following formats from the Dataverse:
    - :::no-loc text="LTM Tax Report":::
    - :::no-loc text="LTM Tax Report mapping":::
    - :::no-loc text="COL Withholding Certificate FTE":::
    - :::no-loc text="COL Withholding Certificate ICA":::
    - :::no-loc text="COL Withholding Certificate IVA":::
   
- Configure the Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters for the Withholding certificate format for Colombia.
Follow these steps to configure application-specific parameters.

### Configure COL withholding certificate FTE format

1. In Dynamics 365 Finance, go to **Organization administration** > **Workspaces** > **Electronic reporting** and select **Reporting configurations** > **LTM Tax Report**.
1. Select the **COL Withholding Certificate FTE** format.
1. On the Action Pane, in the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendInvoiceIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all invoices document classes that are required for vendor transactions.
1. Ensure the report shows transactions that meet the configured conditions by setting the **Lookup result** fields to **No** and specifying both **Blank** and **Non-blank** conditions.
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

### Configure COL withholding certificate ICA format

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

### Configure COL withholding certificate IVA format

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
> The **Concept** column on the certificate shows the name of the ledger account used for the withholding tax line.

> [!NOTE]
> Use the tax codes and document classes configured in lookups in transactions beforehand to make them appear in the certificate formats.

## Generate the withholding certificate format for Colombia

To generate the certificate, follow these steps:

1. In Dynamics 365 Finance, go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
1. In the **Format mapping** field, enter or select the name of the format you need to generate (:::no-loc text="COL Withholding Certificate FTE":::, :::no-loc text="COL Withholding Certificate ICA":::, or :::no-loc text="COL Withholding certificate IVA":::), and then select **OK**.
1. In the **From date** and **To date** fields, enter the date range for the report.
1. Select **OK**.
