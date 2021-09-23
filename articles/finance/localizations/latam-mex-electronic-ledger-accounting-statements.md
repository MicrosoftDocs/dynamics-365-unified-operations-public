---
# required metadata

title: Electronic ledger accounting statements
description: This article explains how to set up and generate the general ledger XML files that all companies in Mexico are required to report to the Mexican tax authorities (SAT) on a monthly basis.
author: sndray
ms.date: 12/07/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, LedgerConsolidateAccountGroup, LedgerJournalTable, LedgerJournalTransVendInvoice, LedgerParameters, MainAccount, MainAccountConsolidateAccount, VendEditInvoice, VendPaymMode, VendTransInvoicePool
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 265314
ms.assetid: b4a95c26-a49d-4a1d-bf70-90f457df2ddf
ms.search.region: Mexico
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Electronic ledger accounting statements

[!include [banner](../includes/banner.md)]

This article explains how to set up and generate the general ledger XML files that all companies in Mexico are required to report to the Mexican tax authorities (SAT) on a monthly basis.

All companies in Mexico are required to report ledger accounting statements to the Mexican tax authorities (Servicio de Administración Tributaria \[SAT\]) every month. Annex 24 of Miscellaneous Tax Resolution requires that you submit general ledger XML files. You can generate the following XML files per company:

-   Chart of account
-   Monthly Trial Balance
-   Journal transactions, together with the related subledger transactions (Comprobante Fiscal Digital a través de Internet \[CFDI\], Comprobante Fiscal Digital \[CFD\], and other operations)
-   Auxiliary ledger account

This functionality is available only when the country/region of the company is defined as MEX. 

## Prerequisites
The following process lists the prerequisites that must be in place before you start to generate the XML files that SAT requires. Parameters determine how the data will be exposed in the XML files, and all of them are required. Missing parameters can cause inconsistencies or incorrect validations in the government validation tool.

1.  Set up main account parameters.
2.  Set up a Parent\_Account to identify the level of account.
3.  Set up total accounts in all levels.
4.  Set up SAT account group.
5.  Create consolidation account group for SAT.
6.  Assign main account to SAT group and level accounts.
7.  Set up Method of payments and Bank accounts.
8.  Assign SAT method of payments.
9.  Assign SAT bank code in routing number field.



### Chart of accounts

Per government requirements, the Chart of account XML file must include specific information that you must configure in advance to prevent inconsistencies when the XML file is generated and validated. Set the following parameters to configure this information:

- **Parent main account:** The **&lt;SubCtaDe&gt;** tag in the XML file is used to specify the account of the previous level. In this case, we use a **Parent account** country/region field in the configuration of the chart of accounts.
- **Account level:** The **&lt;Nivel&gt;** tag in the XML file is used to specify the level of the government account group. We localized the functionality of the **Consolidation account group** field under **Additional consolidation accounts** to specify the level of the government account group.
- **Debit and Credit indicator:** The **&lt;Natur&gt;** tag in the XML file is used to specify the debit and credit indicator of the main account. The following rules have been defined:
  - **D-Debit**
    -   Main Account type = Cost, Asset
    -   Main Account type:  If Profit & Loss and DB/CR proposal = Debit
    -   Main Account type: If Balance and DB/CR proposal = Debit
    -   Main Account type: If Profit & Loss and DB/CR proposal = Blank
    -   Main Account type: If Balance and DB/CR proposal = Blank
  - **A-Credit**
    -   Account type : Revenue, Liability
    -   Account type AX: If Profit & Loss and DB/CR proposal = Credit
    -   Account type AX: If Balance and DB/CR proposal = Credit
- **Totals amount in all levels:** Configure the **Totals** value in the chart of accounts to enable generation of a Monthly Trial Balance XML file that includes the related totals amounts in all levels of the hierarchy.

### SAT account group

The Chart of account XML file includes a **&lt;CodAgrup&gt;** tag that is used to specify the related government account group for the reported account. The government has published a table on the government portal. To meet this requirement, you must use the Consolidation account groups functionality, which lets you configure the mapping between your company chart of account and the government account group. Then, when you generate the report, you will be asked to indicate which consolidated account group is used to specify the government grouping.

### Payment methods

In specific situations, the government might request that you deliver a Journal transaction XML file that details all accounting transactions and the document that originated them. When these transactions are related to vendors payments, you must specify the type of payment in the **&lt;OtrMetododePago&gt;** node and the **&lt;MetPagPol&gt;** attribute by using a specific table that is published by the government. Click **Accounts payable** &gt; **Payment setup** &gt; **Methods of payment**, and assign the SAT payment method to the company's method of payment.

### Bank transactions

The Journal transaction XML file must include all bank transfer transactions that are posted to the general ledger where some additional information is required in a specific node **&lt;Transferencias&gt;** and their attributes **&lt;BancoOriNal&gt;** and **&lt;BancoDestNal&gt;** is required to inform the government bank code. Click **Cash and bank management** &gt; **Bank accounts**, and use the **Routing number** field to set up this information.

### Invoice identification

The Journal transaction XML file also requires that you identify the invoice number when an invoice is issued and received. Per Mexican legislation, this invoice number can be represented in various ways, depending on how the invoice was delivered:

-   Regular invoice (non-electronic). You must include the **Series** and **Invoice number**.
-   CFD: You must include the **UUID** of an electronic invoice CFD.
-   CFDI:  You must include the **UUID** of an electronic invoice CFD.

Users can now include this information in transactions that are generated from the following areas:

-   Purchase invoice
-   Vendor invoice (non–purchase order)
-   Invoice register
-   Invoice journal
-   Invoice approval
-   Invoice pool

### Electronic reporting

This feature is based on Electronic reporting configuration (ER), where each XML file format is defined by using the model and format designer for electronic reporting. 

You need to download the following latest versions of the ER configurations models and formats from **LCS shared asset library**
1.  Electronic ledger accounting model MX
2.  Auxiliary Ledger XML MX (format)
3.  Chart of Account XML MX (format)
4.  Journal XML MX (format)
5.  Trial Balance XML MX (format)

Next, you need to import the above files in Dynamics 365 Finance. 

1. **Organization administration > Electronic Reporting > Configurations**
2. **Exchange > Load from XML file** and **OK** to confirm. You need to repeat this action for each XML file.


After the repository is updated in your environment with the recently files loaded, you must identify these formats in the general ledger parameters. Click **General ledger** &gt; **Ledger setup** &gt; **General ledger parameters**, and then, in the **Electronic reporting mapping** field group, select the format to use to generate the XML files.

## Generate electronic ledger accounting files
Click **General ledger** &gt; **Inquire and reports** &gt; **Ledger reports** &gt; **Electronic ledger accounting statement** to generate the required XML files and download them to your environment. The following table describes the parameters that you must set.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>SAT consolidation account group</strong></td>
<td>Select the consolidation account group that you previously configured to identify the SAT account group.</td>
</tr>
<tr class="even">
<td><strong>Period</strong></td>
<td>Select the period for the report. The selected date will include all general ledger transactions for the selected month.</td>
</tr>
<tr class="odd">
<td><strong>Closing transactions</strong></td>
<td>This slider indicates if the closing transactions should be included as transactions in the Monthly Trial Balance XML file. Switch this slider to <strong>No</strong> to exclude closing transactions from the Monthly Trial balance XML file.</td>
</tr>
<tr class="even">
<td><strong>Trial Balance</strong></td>
<td>Select this check box to generate the Chart of account and Monthly Trial Balance XML files for the specified period.</td>
</tr>
<tr class="odd">
<td><strong>Delivery type</strong></td>
<td>Specify the type of delivery:
<ul>
<li>Normal</li>
<li>Complementary</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Update date</strong></td>
<td>Specify the updated date of a complementary delivery.</td>
</tr>
<tr class="odd">
<td><strong>Ledger entries</strong></td>
<td>This slider indicates if the Journal transaction XML file is generated for the specified period.</td>
</tr>
<tr class="even">
<td><strong>Auxiliary ledger</strong></td>
<td>This slider indicates if the Auxiliary ledger XML file is generated for the specified period.</td>
</tr>
<tr class="odd">
<td><strong>Request type</strong></td>
<td>Select this option to identify the type of request when the <strong>Ledger entries</strong> or <strong>Auxiliary ledger</strong> slider is set to <strong>Yes</strong>.</td>
</tr>
<tr class="even">
<td><strong>Order number</strong></td>
<td>Enter the order number that was assigned by the government tax authority, if the request type is <strong>Control</strong> or <strong>Compulsive control</strong>.</td>
</tr>
<tr class="odd">
<td><strong>Process Number</strong></td>
<td>Enter the process number that was assigned by the government tax authority, if the request type is <strong>Return</strong> or <strong>Compensation</strong>.</td>
</tr>
</tbody>
</table>


## Produce Mexican electronic ledger accounting report (MX-00020)

This task walks through all necessary steps to configure the generation of electronic ledger accounting XML files by using the Electronic Reporting tool. You need to download the higher version of ER model and configurations from LCS shared library-GER configurations.

-   Model: Electromic ledger accounting model MX 
-   Format file: Chart of account XML(MX)
-   Format file: Trial Balance XML (MX). Monthly Trial Balance
-   Format file : Journals XML (MX). Journal transactions, together with the related subledger transactions (Comprobante Fiscal Digital a través de Internet \[CFDI\], Comprobante Fiscal Digital \[CFD\], and other operations)
-   Format file: Auxiliary ledger XML (MX) 


### Import a configuration including XML formats
1. Go to Organization administration > Workspaces > Electronic reporting.
2. In the Configuration providers list, click Set active on the Microsoft provider box.
    * If the Microsoft provider is already the active provider, you can skip this step.  
3. Click Reporting configurations
4. Click Exchange and select the option Load from XML file
5. Select and browse the XML model file previously downloaded from LCS and then click OK to confirm
6. Repeat the steps 4 and 5 to import the rest of XML file formats
    * You will be able to see one (1) model and the four (4) XML formats that you previously imported.  

### Configure general ledger parameters for electronic reporting mapping
1. Go to General ledger > Ledger setup > General ledger parameters.
2. In the Trial balance field, click the drop-down button to open the lookup.
3. In the list, select the Trial Balance XML format
4. In the list, click the link in the selected row.
5. In the Auxiliary ledger field, click the drop-down button to open the lookup.
6. In the list, selecy the Auxiliary ledger XML format
7. In the Ledger entries field, click the drop-down button to open the lookup.
8. In the list, select the Journal XML format
9. In the list, click the link in the selected row.
10. In the Chart of accounts field, click the drop-down button to open the lookup.
11. In the list, select the Chart of Account XML format.
12. Click Save.

### Generate XML files
1. Go to General ledger > Inquiries and reports > Ledger reports > Electronic ledger accounting statement.
2. In the SAT consolidation account group field, click the drop-down button to open the lookup.
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. In the Period field, enter a date.
6. Check or uncheck the Trial Balance opcion
    * This option generates the Chart of Account and Trial Balance XML files.  
7. Select or clear the Ledger entries check box.
8. Select or clear the Auxiliary ledger check box.
9. In the Request type field, select an option.
10. In the Order number field, type a value.
11. Click OK.


## Additional resources

- [CFDI layout version 3.3](latam-mex-cfdi-3-3.md)




[!INCLUDE[footer-include](../../includes/footer-banner.md)]