---
title: Configure printing for the Ecuador Sales book by establishment report
description: This article describes how to set up and use the Ecuador Sales book by establishment report
author: Fhernandez0088
ms.date: 01/03/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure printing for the Ecuador Sales book by establishment report

The **Ecuador Sales book by establishment** report is the record document used by businesses to keep a record of their sales transactions for each active establishment. Although specific VAT report requirements may vary from country/region to country/region, they generally include transaction date, customer information, and tax information details.

## Prerequisites

Before you can print the **Ecuador Sales book by establishment** report, the following prerequisites must be met: 

- The legal entity address must in a country within the LATAM localization, Ecuador in this case.
- Have both the LATAM country specific function and the general function are activated.
- Download the specific report configuration from Microsoft Dataverse repository. For more information, see [ER download reports](../global/workspace/gsw-import-er-config-dataverse.md).
- Configure the Electronic Reporting parameters. For more information, see [ER configuration](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must have sales invoices with LATAM information posted.
- You must configure the **Tax applications** of the **Sales points** used with an **”F”** for physical document and **”E”** for electronic document. For more information, see [Document classes for Latin America](ltm-core-document-class.md) article.

## Configure application-specific parameters.

Lookups and conditions are designed to allow you to select the combination of document classes IDs and sales tax codes that are used in sales transactions. The Ecuador applicable conditions are displayed.

1. Open the **Electronic Reporting** work area and select **Report Configurations**, and select  **LTM Tax Report**.
1. Select the **EC Sales book by establishment** report and then in the action pane, on the **Configuration** tab, in the **Application-specific parameters** group, select **Setup**.
1. In the **Lookups names**, select **IsApllicable**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **SalesId**. 
1. In the **Document classification Id (VoucherClassid)** field, select an option from the list. 
1. Repeat steps 5 and 6 for as many tax codes you need.
1. When you are done configuring, add two more lines in **Conditions**. In the **Lookup result** field select **NotApplicable** for both. Then in the **Document classification Id (VoucherClassid)** field select **Blank** as the last but one and **Not blank** for the last position.
1. Back to **Lookups names**, select **SalesPoint**.
1. In the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Sales Point Id** field, select an option from the list. 
1. Repeat steps 10 and 11 for as many sales points you need.
1. When finished configuring add two more lines in **Conditions**. In **Lookup result** field, select **No** for both. Then in **Sales Point Id (SalesPointid)** field select **Blank** as the last but one and **Not blank** for the last position.

> [!NOTE]
> VAT Sales books are formats that depend on the LTM tax report template. Therefore, it is important that sales points configured in this report are used in the posted transactions. The codes you select here must match the codes recorded in transactions.

## Run “EC Sales book by establishment” report

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the Format mapping field, select **EC Sales book by establishment** value.
1. Select **OK**.
1. In the **From** date field, enter a date.
1. In the **To** date field, enter a date.
1. Select **OK**.
eport
