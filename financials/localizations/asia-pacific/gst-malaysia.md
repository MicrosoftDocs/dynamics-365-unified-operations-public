---
# required metadata

title: Malaysia Goods and Services Tax
description: This article provides information about how to set up Goods and Services Tax (GST) for a Malaysian company and explains the functionality that Microsoft Dynamics AX provides for GST.
author: ShylaThompson
manager: AnnBe
ms.date: 2015-10-27 18 - 26 - 26
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: TaxGSTReliefCategory_MY, TaxGSTReliefGroup_MY, TaxGSTReportConfiguration_MY
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: ShylaThompson
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 10904
ms.assetid: e2f1f89f-b934-4d65-9bd8-66b79561df1b
ms.search.region: Malaysia
# ms.search.industry: 
ms.author: leguo
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Malaysia Goods and Services Tax

This article provides information about how to set up Goods and Services Tax (GST) for a Malaysian company and explains the functionality that Microsoft Dynamics AX provides for GST.

Goods and Services Tax (GST) is a multi-stage tax on domestic consumption. GST is charged on all taxable supplies of goods and services in Malaysia, except those that are explicitly exempted. GST is also charged on the importation of goods and services into Malaysia.

## Enabling the Malaysia GST features
You can enable the GST features in Microsoft Dynamics AX only if the country/region of the address of the legal entity is Malaysia.

### GST registration number

The GST registration number is printed on your tax invoices and on some reports. You maintain it in the address information for your legal entity. You must first define a registration type on the **Tax registration type** page. Make sure that the country/region code is **MYS**, and that the **Primary for country** check box is selected. Then, in the primary address of the legal entity, add the tax registration number for GST. Select the tax registration type that you defined, and then enter your GST registration number.

### General ledger parameters for GST

In the **Sales tax** section of the **General ledger parameters** page, specify the following GST parameters.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>GST invoice</strong></td>
<td><ul>
<li>Set the <strong>Use self-billed invoice</strong> slider to <strong>Yes </strong>if you must issue self-billed invoices under some circumstances.</li>
<li>In the <strong>GST invoice format</strong> field, select either <strong>Full invoice</strong> or <strong>Simplified invoice</strong> as the printing format for GST invoices. Most organizations use full invoices. However, in some case, the Director General can, upon written request, allow registered persons to issue simplified tax invoices to their customers.</li>
<li>Select either <strong>GST invoice</strong> or <strong>Invoice</strong> as the default invoice type that is used for sales orders, free text invoices, and project invoices. Most organizations use GST invoices.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>GST audit file</strong></td>
<td><ul>
<li>Specify the version of the GST audit file (GAF). This information is included in the GAF that is generated.</li>
<li>In the <strong>GST summary</strong> field group, specify the information to include in the GST summary text of a GST invoice.</li>
<li>In the <strong>Exempt GST print code</strong> field, specify the print code that is used for exempt GST codes.</li>
<li>Set the <strong>Include delimiter in summary text</strong> slider to <strong>Yes </strong>to include the delimiter in summary text.</li>
<li>Specify the delimiter to use on GST summary lines.</li>
<li>Set the <strong>Include tax code in summary text</strong> slider to <strong>Yes</strong> to include tax codes in summary text.</li>
<li>Set the <strong>Include tax value in summary text</strong> slider to <strong>Yes </strong>to include tax values in summary text.</li>
</ul></td>
</tr>
</tbody>
</table>

## Debit notes and credit notes
The GST Act specifies the requirements for issuing credit and debit notes for a supply or purchase. You can now create and manage debit notes and credit notes for sales orders, free text invoices, purchase orders, and project invoices. When you print debit notes and credit notes, you will see the following additional information:

-   The words “Debit note” or “Credit note” in a prominent place
-   The reasons that the debit note or credit note has been issued
-   The number and date of the original tax invoice

In standard Microsoft Dynamics AX, you can create a credit note for a sales order. For Malaysia, this functionality has been modified so that the invoice number and invoice date of the original invoice are included on the corresponding sales order lines. You can now follow the same steps to create a debit note, provided that it meets the following conditions:

-   It has a reference to the original invoices.
-   The total amount is positive.

For both debit notes and credit notes, you must provide a reason code on the sales order header. Similar functions are provided for free text invoices and purchase orders. In standard Microsoft Dynamics AX, you can create a credit note for a project invoice through the **Sales order** page. You can now also create a debit note for a project invoice.

## GST invoices
Tax invoices are the most important documents in the GST system. They contain details about the registered person and supply, the GST rate, and the amount of GST that is payable under the GST Act. A tax invoice resembles a commercial invoice or receipt, but it contains additional information that is specified by the GST Act. A tax invoice can contain details about more than one supply (taxable supply and exempt supply). In this case, the tax invoice (whether full or simplified) must clearly distinguish between the various supplies, and it must indicate separately the applicable tax values and any tax that is charged on each supply for GST purposes. You can modify the parameters for the GAF summary to configure the indicators that distinguish the various supplies. A sample tax invoice is provided that adds the following details to a standard sales invoice:

-   The words "Tax invoice" in a prominent place
-   The GST registration number
-   The GST summary

To print a GST invoice for a sales order, select **GST invoice** as the invoice type on the sales order header. However, to print a commercial invoice, select **Invoice** as the invoice type. You can also print simplified invoices for sales orders by changing the value of the **GST invoice format **general ledger parameter to **Simplified invoice**. A sample simplified invoice is provided. This invoice differs from the sample full tax invoice in that it omits the invoice title, and the name and address of the recipient. The same functionality is available for free text invoices.

### Relief clauses on invoices

When the Minister grants your customers relief from the payment of all or part of the tax on a taxable supply of goods or services, or any importation of goods or classes of goods, you should issue tax invoices that include a regulated relief clause. Before you can issue tax invoices that have relief clauses, you must set up GST relief categories and GST relief groups. You must then assign products to a relief category and customers to a relief group. After this setup is completed, you can create sales orders to sell the items that are in the relief categories to the customers who are in the corresponding relief groups. A relief clause will be printed on the GST invoice.

### Self-billed invoices

Under some circumstances, the value of a supply is determined by the person who receives the goods. Therefore, for GST purposes, the recipient of the goods is allowed to issue an invoice to himself or herself. This invoice is considered a tax invoice for the supply of goods or services to that person by another registered person. You can issue self-billed invoices only if you receive approval from the Director General. The reference number of the approval must be stated on the self-billed invoice. To print a self-billed invoice, the invoice type must be set to **GST invoice**, and you must enter the approval number on the purchase order header. On the invoice, you will see the following additional information:

-   The words “Self-billed invoice” in a prominent place
-   The approval number
-   The GST summary

## GST reports
The following out-of-box reports are available to provide details about debit notes, credit notes, supplies, and purchases:

-   Customer debit note and credit note list
-   Vendor debit note and credit note list
-   Supply list by tax code
-   Purchase list by tax code

Additionally, a configurable **GST report by configuration** report is provided to meet the following reporting requirements:

-   GST-03
-   GST summary sheet
-   Total acquisition and input tax
-   Total supply and output tax
-   Consolidated monthly record of total inputs and outputs of all group members for the taxable period

These reports are in different formats, but they all display monetary amounts (transaction amount and GST amount) for specific transactions. To meet these requirements, you can configure the report content and then generate various reports according to your report configurations. You must follow these steps to run the report:

1.  Define sales tax reporting codes.
2.  Map sales tax reporting codes to sales tax codes.
3.  Define the GST report configuration.
4.  Run the **GST report by configuration** report.

### Defining sales tax reporting codes

The **GST report by configuration** report takes advantage of reporting code functions in Microsoft Dynamics AX. Sales tax reporting codes collect the information for several sales tax codes onto one report line. In a typical setup, there is one sales tax reporting code for every calculated field on reports, and some predetermined reporting codes must be created. However, because you can now define your own report configurations and specify which reporting codes to use, no predetermined codes are required. No specific report layout has been introduced for Malaysia GST. You must use the **Default** report layout for your reporting codes.

### Mapping sales tax reporting codes to sales tax codes

Before values can be calculated and displayed on reports, you must specify a relevant sales tax reporting code for each tax code that is used in the sales tax payment process. On the **Report setup** tab, set a sales tax reporting code in one or more fields for each tax code.

### Defining the GST report configuration

You can create report configurations to meet your reporting requirements. Before you create a report configuration, you must determine what types of transactions to include. For example, if you create a configuration for GST returns, you can include the following types of transactions.

GST report configuration name

Type of transaction

Transaction amount

GST amount

GST-03

Bad Debt Recovered

18

Bad Debt Relief

17

Total Input Tax (Inclusive of Bad Debt Relief & other Adjustments)

62

Total Output Tax (Inclusive of Bad Debt Recovered & other Adjustments)

52

Total Value of Capital Goods Acquired

16

Total Value of Exempt Supplies

12

Total Value of Export Supplies

11

Total Value of Goods Imported Under Approved Trader Scheme

14

Total Value of GST Suspended under item 14

15

Total Value of Local Zero-Rated Supplies

10

Total Value of Standard Rated Acquisition

61

Total Value of Standard Rated Supply

51

Total Value of Supplies Granted GST Relief

13

You must use different tax codes for those transactions. The way that reporting codes are mapped to these tax codes and then selected in the report configurations varies, depending on your overall reporting requirements. For example, a report shows the transaction amounts on your invoices, debit notes, and credit notes separately. Therefore, you map the various reporting codes (1001 for invoices, 1002 for debit notes, and 1003 for credit notes) to specific tax codes. Meanwhile, if you must display, for example, Total Value of Standard Rated Supply in GST-03, credit notes, debit notes, and invoices aren't differentiated. Therefore, you must select **1001**, **1002**, and **1003** for the transaction amounts.

### Running the GST report by configuration report

After you book your transactions and define your report configurations, you can run the **GST report by configuration** report. You must provide following parameters:

-   **Settlement period:** Specify the settlement period to generate the report for.
-   **From date:** The first date in the interval for this settlement period.
-   **Report configuration:** Select one of the report configurations that you've defined.

GAF
---

Royal Malaysian Customs Department (MRCD) will periodically audit your business to make sure that you are making correct tax declarations. For auditing purposes, you can generate a GAF in XML format. The GAF contains a detailed breakdown of business transactions. It mainly contains the following information for a taxable period:

-   Company information
-   Purchases
-   Supplies
-   Ledger transactions
-   Footer (Summary)

Certain business data should be captured in AX to generate the GAF.   For the section "Company information", the GAF version is needed in "General ledger parameters".   For "Purchases" section,  when importing Goods from oversea vendors, the declaration number should be captured for each vendor invoice. Besides normal sales order and purchases orders, more transactions should be regarded as "Purchase" or "Supply" in GAF.  For instance,  when you make payment to vendors and you also need to pay bank fees to banks. As per Malaysia GST regulations, GST will be applied to the bank charge. Bank will provide GST invoice to you and  you are able to claim the GST input tax. When generating the GAF file, tax authority is expecting to see the bank charges are regarded as "purchases" in GAF.  In such cases, AX should enable users capture the required GAF information. You are now able to capture "Organization number" for a bank group. It will be defaulted to payment fee transactions of corresponding banks. And you can enter required GAF information for various journals and payment fees as per your business needs.  You also can preview the supply and purchase records where GST applies and you can edit or add relevant information in the "GAF purchase and supply review" page.  You need make sure you mark the "GST" check box on the Sales tax codes page for each of your GST tax codes. To generate the GAF, click **Tax** &gt; **Declarations** &gt; **Sales tax** &gt; **Generate GAF file**, and provide the following required information:

-   **Settlement period:** Specify the settlement period to generate the GAF for.
-   **From date:** The first date in the interval for this settlement period.
-   **Creation date:** The GAF creation date. This information will appear in the company section of the GAF.
-   **Posting layer:** Specify which posting layers to generate the GAF from. The posting layers affect the ledger transactions that are included in the GAF.

You should run the “Settle and post sales tax” process before you generate the GAF for a period. Only those transactions that are included in a sales tax payment will be included in the GAF.

