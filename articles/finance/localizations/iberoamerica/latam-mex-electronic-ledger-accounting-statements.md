---
title: Electronic ledger accounting statements
description: Learn how to set up and generate the general ledger XML files that all companies in Mexico are required to report to the Mexican tax authorities (SAT).
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2016-02-28
ms.search.form: ERSolutionTable, LedgerConsolidateAccountGroup, LedgerJournalTable, LedgerJournalTransVendInvoice, LedgerParameters, MainAccount, MainAccountConsolidateAccount, VendEditInvoice, VendPaymMode, VendTransInvoicePool
ms.assetid: b4a95c26-a49d-4a1d-bf70-90f457df2ddf
---

# Electronic ledger accounting statements

[!include [banner](../../includes/banner.md)]

This article explains how to set up and generate the general ledger XML files that all companies in Mexico must report to the Mexican tax authorities (SAT) every month.

All companies in Mexico must report ledger accounting statements to the Mexican tax authorities (Servicio de Administración Tributaria \[SAT\]) every month. Annex 24 of Miscellaneous Tax Resolution requires that you submit general ledger XML files. You can generate the following XML files for each company:

- Chart of accounts
- Monthly Trial Balance
- Journal transactions, together with the related subledger transactions (Comprobante Fiscal Digital a través de Internet \[CFDI\], Comprobante Fiscal Digital \[CFD\], and other operations)
- Auxiliary ledger account

This functionality is available only when the country/region of the company is defined as MEX.

## Prerequisites

Before you start generating the XML files that SAT requires, make sure you have the following prerequisites in place. Parameters determine how the data appears in the XML files, and you must provide all of them. Missing parameters can cause inconsistencies or incorrect validations in the government validation tool.

1. Set up main account parameters.
2. Set up a Parent\_Account to identify the level of account.
3. Set up total accounts in all levels.
4. Set up SAT account group.
5. Create consolidation account group for SAT.
6. Assign main account to SAT group and level accounts.
7. Set up Method of payments and Bank accounts.
8. Assign SAT method of payments.
9. Assign SAT bank code in routing number field.

### Chart of accounts

Per government requirements, the Chart of accounts XML file must include specific information that you configure in advance to prevent inconsistencies when the XML file is generated and validated. Set the following parameters to configure this information:

- **Parent main account:** Use the **&lt;SubCtaDe&gt;** tag in the XML file to specify the account of the previous level. In this case, use the **Parent account** country/region field in the configuration of the chart of accounts.
- **Account level:** Use the **&lt;Nivel&gt;** tag in the XML file to specify the level of the government account group. Localize the functionality of the **Consolidation account group** field under **Additional consolidation accounts** to specify the level of the government account group.
- **Debit and Credit indicator:** Use the **&lt;Natur&gt;** tag in the XML file to specify the debit and credit indicator of the main account. The following rules are defined:
  - **D-Debit**
    - Main Account type = Cost, Asset
    - Main Account type:  If Profit & Loss and DB/CR proposal = Debit
    - Main Account type: If Balance and DB/CR proposal = Debit
    - Main Account type: If Profit & Loss and DB/CR proposal = Blank
    - Main Account type: If Balance and DB/CR proposal = Blank
  - **A-Credit**
    - Account type : Revenue, Liability
    - Account type AX: If Profit & Loss and DB/CR proposal = Credit
    - Account type AX: If Balance and DB/CR proposal = Credit
- **Totals amount in all levels:** Configure the **Totals** value in the chart of accounts to enable generation of a Monthly Trial Balance XML file that includes the related totals amounts in all levels of the hierarchy.

### SAT account group

The Chart of accounts XML file includes a **&lt;CodAgrup&gt;** tag that you use to specify the related government account group for the reported account. The government publishes a table on the government portal. To meet this requirement, use the Consolidation account groups functionality, which you use to configure the mapping between your company chart of accounts and the government account group. Then, when you generate the report, you're asked to indicate which consolidated account group is used to specify the government grouping.

### Payment methods

In specific situations, the government might request that you deliver a Journal transaction XML file that details all accounting transactions and the document that originated them. When these transactions are related to vendor payments, you must specify the type of payment in the **&lt;OtrMetododePago&gt;** node and the **&lt;MetPagPol&gt;** attribute by using a specific table that the government publishes. Select **Accounts payable** > **Payment setup** > **Methods of payment**, and assign the SAT payment method to the company's method of payment.

### Bank transactions

The Journal transaction XML file must include all bank transfer transactions that post to the general ledger. Include additional information in the **&lt;Transferencias&gt;** node. Use the **&lt;BancoOriNal&gt;** and **&lt;BancoDestNal&gt;** attributes to provide the government bank code. Select **Cash and bank management** > **Bank accounts**, and use the **Routing number** field to set up this information.

### Invoice identification

The Journal transaction XML file also requires that you identify the invoice number when you issue and receive an invoice. Per Mexican legislation, you can represent this invoice number in various ways, depending on how you delivered the invoice:

- Regular invoice (non-electronic). You must include the **Series** and **Invoice number**.
- CFD: You must include the **UUID** of an electronic invoice CFD.
- CFDI:  You must include the **UUID** of an electronic invoice CFD.

Users can now include this information in transactions that they generate from the following areas:

- Purchase invoice
- Vendor invoice (non–purchase order)
- Invoice register
- Invoice journal
- Invoice approval
- Invoice pool

### Electronic reporting

This feature uses Electronic reporting configuration (ER), where you define each XML file format by using the model and format designer for electronic reporting.

Download the latest versions of the ER configuration models and formats from **LCS shared asset library**:

1. Electronic ledger accounting model MX
1. Auxiliary Ledger XML MX (format)
1. Chart of Account XML MX (format)
1. Journal XML MX (format)
1. Trial Balance XML MX (format)

Next, import these files into Dynamics 365 Finance.

1. Go to **Organization administration** > **Electronic Reporting** > **Configurations**.
1. Select **Exchange** > **Load from XML file**, and then select **OK** to confirm. Repeat this action for each XML file.

After you update the repository in your environment with the recently loaded files, identify these formats in the general ledger parameters. Select **General ledger** > **Ledger setup** > **General ledger parameters**. In the **Electronic reporting mapping** field group, select the format to use to generate the XML files.

## Generate electronic ledger accounting files

Select **General ledger** > **Inquire and reports** > **Ledger reports** > **Electronic ledger accounting statement** to generate the required XML files and download them to your environment. The following table describes the parameters that you must set.

| | |
|---|---|
| **SAT consolidation account group** | Select the consolidation account group that you previously configured to identify the SAT account group. |
| **Period** | Select the period for the report. The selected date includes all general ledger transactions for the selected month. |
| **Closing transactions** | Use this slider to indicate if the closing transactions should be included as transactions in the Monthly Trial Balance XML file. Switch this slider to **No** to exclude closing transactions from the Monthly Trial balance XML file. |
| **Trial Balance** | Select this check box to generate the Chart of account and Monthly Trial Balance XML files for the specified period. |
| **Delivery type** | Specify the type of delivery: Normal, Complementary. |
| **Update date** | Specify the updated date of a complementary delivery. |
| **Ledger entries** | Use this slider to indicate if the Journal transaction XML file is generated for the specified period. |
| **Auxiliary ledger** | Use this slider to indicate if the Auxiliary ledger XML file is generated for the specified period. |
| **Request type** | Select this option to identify the type of request when the **Ledger entries** or **Auxiliary ledger** slider is set to **Yes**. |
| **Order number** | Enter the order number that the government tax authority assigned, if the request type is **Control** or **Compulsive control**. |
| **Process Number** | Enter the process number that the government tax authority assigned, if the request type is **Return** or **Compensation**. |

## Produce Mexican electronic ledger accounting report (MX-00020)

This task walks through all necessary steps to configure the generation of electronic ledger accounting XML files by using the Electronic Reporting tool. You need to download the higher version of ER model and configurations from LCS shared library-GER configurations.

- Model: Electronic ledger accounting model MX
- Format file: Chart of account XML(MX)
- Format file: Trial Balance XML (MX). Monthly Trial Balance
- Format file: Journals XML (MX). Journal transactions, together with the related subledger transactions (Comprobante Fiscal Digital a través de Internet [CFDI], Comprobante Fiscal Digital [CFD], and other operations)
- Format file: Auxiliary ledger XML (MX)

### Import a configuration including XML formats

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. In the **Configuration providers** list, select **Set active** on the Microsoft provider box.
    - If the Microsoft provider is already the active provider, you can skip this step.  
1. Select **Reporting configurations**.
1. Select **Exchange** and choose the option **Load from XML file**.
1. Select and browse the XML model file you previously downloaded from LCS, and then select **OK** to confirm.
1. Repeat steps 4 and 5 to import the rest of XML file formats.
    - You see one model and the four XML formats that you previously imported.    

### Configure general ledger parameters for electronic reporting mapping

1. Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
1. In the **Trial balance** field, select the drop-down button to open the lookup.
1. In the list, select the Trial Balance XML format.
1. In the list, select the link in the selected row.
1. In the Auxiliary ledger field, select the drop-down button to open the lookup.
1. In the list, selecy the Auxiliary ledger XML format
1. In the Ledger entries field, select the drop-down button to open the lookup.
1. In the list, select the Journal XML format
1. In the list, select the link in the selected row.
1. In the Chart of accounts field, select the drop-down button to open the lookup.
1. In the list, select the Chart of Account XML format.
1. Select Save.

### Generate XML files

1. Go to General ledger > Inquiries and reports > Ledger reports > Electronic ledger accounting statement.
1. In the SAT consolidation account group field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the Period field, enter a date.
1. Check or uncheck the Trial Balance opcion
    - This option generates the Chart of Account and Trial Balance XML files.  
1. Select or clear the Ledger entries check box.
1. Select or clear the Auxiliary ledger check box.
1. In the Request type field, select an option.
1. In the Order number field, type a value.
1. Select OK.

## Additional resources

[CFDI layout version 3.3](latam-mex-cfdi-3-3.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
