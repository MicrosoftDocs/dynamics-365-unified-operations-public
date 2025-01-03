---
title: Ecuador Sales book by establishment printing configuration
description: This article describes how to set up and use the “Ecuador Sales book by establishment” report
author: Fhernandez0088
ms.date: 01/03/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Ecuador Sales book by establishment printing configuration
The “Ecuador Sales book by establishment” report is the record document used by businesses to keep a record of their sales transactions for each active establishment. Although specific VAT reports requirements may vary from country/region to country/region, they generally include transaction date, customer information and tax information details.

## Prerequisites
To print the report, the following prerequisites must be met: 
* The legal entity address must in a country within the LATAM localization, Ecuador in this case.
* Have both the LATAM country specific function and the general function activated.
* Download the specific report configuration from Dataverse repository. 
[ER download reports]( https://learn.microsoft.com/dynamics365/finance/localizations/global/workspace/gsw-import-er-config-dataverse)
* Configure the Electronic Reporting parameters
 [ER configuration]( https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters)
* Must have sales invoices with LATAM information posted.
* You must configure the **tax applications** of the **sales points** used with an **”F”** for physical document and **”E”** for electronic document, see [Document classes for Latin America](  https://learn.microsoft.com/dynamics365/finance/localizations/iberoamerica/ltm-core-document-class) article.

## Configure application-specific parameters.
Lookups and conditions are designed to allow you to select the combination of document classes IDs and sales tax codes that are used in sales transactions. The Ecuador applicable conditions will be displayed.

1. Open the **Electronic Reporting** work area and select **Report Configurations**,and select  **LTM Tax Report**.
2. Select the “EC Sales book by establishment” report and then in the action pane, on the **Configuration** tab, in the **Application-specific parameters** group, select **Setup**.
3. In the **Lookups names**, select **IsApllicable**.
4. In the **Conditions** FastTab, select **Add**.
5. In the **Lookup result** field, select **SalesId**. 
6. In the **Document classification Id (VoucherClassid)** field, select an option from the list. 
7. Repeat steps 5 and 6 as many as many times as tax codes you need.
8. When you are done configuring add two more lines in **Conditions**. In the **Lookup result** field select **NotApplicable** for both. Then in the **Document classification Id (VoucherClassid)** field select **Blank** as the last but one and **Not blank** for the last position.
8. Back to **Lookups names**, select **SalesPoint**.
9. In the **Conditions** FastTab, select **Add**.
10. In the **Lookup result** field, select **Yes**.
11. In the **Sales Point Id** field, select an option from the list. 
12. Repeat steps 10 and 11 as many sales point you need.
13. When finished configuring add two more lines in **Conditions**. In **Lookup result* field select **No** for both. Then in **Sales Point Id (SalesPointid)** field select **Blank** as the last but one and **Not blank** for the last position.

>*VAT Sales books are formats that depend from the LTM tax report template. Therefore, it is important that sales points configured in this report are used in the posted transactions. The codes you select here must match the codes recorded in transactions*.

## Run “EC Sales book by establishment” report
1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
2. In the Format mapping field,select **EC Sales book by establishment** value.
3. Click **OK**.
4. In the **From** date field, enter a date.
5. In the **To** date field, enter a date.
6. Click **OK**.
