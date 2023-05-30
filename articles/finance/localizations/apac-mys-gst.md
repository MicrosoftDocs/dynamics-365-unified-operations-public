---
# required metadata

title: Malaysian Goods and Services Tax (GST)/Sales and Service Tax (SST)
description: This article provides information about how to set up Goods and Services Tax (GST) and Sales and Service Tax (SST) for a Malaysian company.
author: mrolecki
ms.date: 08/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: TaxGSTReliefCategory_MY, TaxGSTReliefGroup_MY, TaxGSTReportConfiguration_MY
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: b14375b1-cb5e-4969-a5fd-3d6d2c8b6226
ms.search.region: Malaysia
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Malaysian Goods and Services Tax (GST)/Sales and Service Tax (SST)

[!include [banner](../includes/banner.md)]

This article provides information that will help you set up Goods and Services Tax (GST) and Sales and Service Tax (SST) for a Malaysian company. It also explains the functionality that is provided for GST/SST.

GST is a multi-stage tax on domestic consumption. GST is charged on all taxable supplies of goods and services in Malaysia, except those goods and services that are explicitly exempted. GST is also charged on the importation of goods and services into Malaysia.

The Malaysian government replaced GST with SST as of September 1, 2018. The GST regime has been in place since April 1, 2015.

## Enabling the Malaysian GST/SST features

You can enable the GST/SST features only if the country or region of the legal entity's address is Malaysia.

### GST/SST registration number

The GST/SST registration number is printed on your tax invoices and some reports. You maintain it in the address information for your legal entity. You must first define a registration type on the **Tax registration type** page. Make sure that the country/region code is **MYS**, and that the **Primary for country** checkbox is selected. Then, in the legal entity's primary address, add the tax registration number for GST/SST. Select the tax registration type that you defined, and then enter your GST/SST registration number.

### General ledger parameters for GST/SST

On the **General ledger parameters** page, on the **Sales tax** tab, on the **GST options** FastTab, specify the following GST parameters.

| Section | Parameters |
|---|---|
| GST invoice | <ul><li>**Use self-billed invoice** – Set this option to **Yes** if you must issue self-billed invoices in some circumstances.</li><li>**GST invoice format** – Select either **Full invoice** or **Simplified invoice** as the printing format for GST invoices. Most organizations use full invoices. However, in some case, the Director General can, upon written request, allow registered persons to issue simplified tax invoices to their customers.</li><li>**Invoice type** – Select **GST invoice**, **Invoice**, or **Service invoice** as the default invoice type for sales orders, free text invoices, and project invoices. Most organizations use GST invoices.</li></ul> |
| GST audit file | <ul><li>**GAF version** – Specify the version of the GST audit file (GAF). This information is included in the GAF that is generated.</li></ul> |
| GST summary | <p>Specify the information that should be includes in the GST summary text of a GST invoice:</p><ul><li>**Exempt GST print code** – Specify the print code that is used for exempt GST codes.</li><li>**Include delimiter in summary text** – Set the slider to **Yes** to include the delimiter in summary text.</li><li>**Delimiter** – Specify the delimiter to use on GST summary lines.</li><li>**Include tax code in summary text** – Set the slider to **Yes** to include tax codes in summary text.</li><li>**Include tax value in summary text** – Set the slider to **Yes** to include tax values in summary text.</li></ul> |

## Debit notes and credit notes

The GST Act specifies the requirements for issuing credit and debit notes for a supply or purchase. You can now create and manage debit notes and credit notes for sales orders, free text invoices, purchase orders, and project invoices. When you print debit notes and credit notes, you will see the following additional information:

-   The words “Debit note” or “Credit note” in a prominent place
-   The reasons why the debit note or credit note has been issued
-   The number and date of the original tax invoice

For Malaysia, the process for creating a credit note for a sales order has been modified so that the invoice number and invoice date of the original invoice are included on the corresponding sales order lines. You can now follow the same steps to create a debit note, provided that it meets the following conditions:

-   It has a reference to the original invoices.
-   The total amount is positive.

For both debit notes and credit notes, you must provide a reason code on the sales order header. Similar functions are provided for free text invoices and purchase orders. You can create a credit note for a project invoice from the **Sales order** page, and you can also create a debit note for a project invoice.

## GST invoices

Tax invoices are the most important documents in the GST system. They contain details about the registered person and supply, the GST rate, and the amount of GST that is payable under the GST Act. A tax invoice resembles a commercial invoice or receipt, but it contains additional information that is specified by the GST Act.

A tax invoice can contain details about more than one supply (taxable supply and exempt supply). In this case, the tax invoice must clearly distinguish between the various supplies. This requirement applies to both full and simplified tax invoices.

The tax invoice must also separately indicate the applicable tax values and any tax that is charged on each supply for GST purposes. By modifying the parameters for the GAF summary, you can configure the indicators that distinguish the various supplies.

A sample tax invoice is provided that adds the following details to a standard sales invoice:

-   The words "Tax invoice" in a prominent place
-   The GST registration number
-   The GST summary

To print a GST invoice for a sales order, on the sales order header, select **GST invoice** as the invoice type. However, to print a commercial invoice, select **Invoice** as the invoice type. You can also print simplified invoices for sales orders by changing the value of the **GST invoice format** field on the **General ledger parameters** page to **Simplified invoice**. A sample simplified invoice is provided. This invoice differs from the sample full tax invoice in that it omits the invoice title, and the name and address of the recipient. The same functionality is available for free text invoices.

The Sales Tax and Service Tax were governed the Sales Tax Act 2018 and the Service Tax Act 2018. The Sales Tax was a federal consumption tax that was imposed on a wide variety of goods, whereas the Service Tax was levied on customers who consumed some taxable services. According to those acts, any amount that is expressed in a currency other than the Malaysian ringgit must also be expressed in Malaysian ringgit. The selling rate of the prevailing exchange in Malaysia at the time of the sale of taxable goods is used.

### Relief clauses on invoices

When the Minister grants your customers relief from the payment of all or part of the tax on a taxable supply of goods or services, or any importation of goods or classes of goods, you should issue tax invoices that include a regulated relief clause. Before you can issue tax invoices that include relief clauses, you must set up GST relief categories and GST relief groups. You must then assign products to a relief category and customers to a relief group. After you've completed this setup, you can create sales orders to sell the items that are in the relief categories to the customers who are in the corresponding relief groups. A relief clause will be printed on the GST invoice.

### Self-billed invoices

In some circumstances, the value of a supply is determined by the person who receives the goods. Therefore, for GST purposes, the recipient of the goods is allowed to issue an invoice to themself. This invoice is considered a tax invoice for the supply of goods or services to that person by another registered person. You can issue self-billed invoices only if you receive approval from the Director General. The reference number of the approval must be stated on the self-billed invoice. You can print a self-billed invoice only if the invoice type is set to **GST invoice**. You must also enter the approval number on the purchase order header. On the invoice, you will see the following additional information:

-   The words “Self-billed invoice” in a prominent place
-   The approval number
-   The GST summary

## GST reports

The following out-of-box reports provide details about debit notes, credit notes, supplies, and purchases:

-   Customer debit note and credit note list
-   Vendor debit note and credit note list
-   Supply list by tax code
-   Purchase list by tax code

Additionally, a configurable **GST report by configuration** report is provided to meet the following reporting requirements:

-   GST-03
-   GST summary sheet
-   Total acquisition and input tax
-   Total supply and output tax
-   Consolidated monthly record of total inputs and outputs of all group members for the taxable period

These reports have different formats, but they all display monetary amounts (transaction amount and GST amount) for specific transactions. To meet these requirements, you can configure the report content and then generate various reports according to your report configurations. To run the report, follow these steps.

1.  Define sales tax reporting codes.
2.  Map sales tax reporting codes to sales tax codes.
3.  Define the GST report configuration.
4.  Run the **GST report by configuration** report.

### Defining sales tax reporting codes

The **GST report by configuration** report takes advantage of reporting code functions in Dynamics 365 Finance. Sales tax reporting codes collect the information for several sales tax codes onto one report line. In a typical setup, there is one sales tax reporting code for every calculated field on reports, and some predetermined reporting codes must be created. However, because you can now define your own report configurations and specify which reporting codes to use, no predetermined codes are required. No specific report layout has been introduced for Malaysia GST. You must use the **Default** report layout for your reporting codes.

### Mapping sales tax reporting codes to sales tax codes

Before values can be calculated and shown on reports, you must specify a relevant sales tax reporting code for each tax code that is used in the sales tax payment process. On the **Report setup** tab, set a sales tax reporting code in one or more fields for each tax code.

### Defining the GST report configuration

You can create report configurations to meet your reporting requirements. Before you create a report configuration, you must determine what types of transactions to include. For example, if you create a configuration for GST returns, you can include the following types of transactions.

|GST report configuration name| Type of transaction| Transaction amount| GST amount|
|-----------------------------|--------------------|-------------------|-----------|
|GST-03|Bad Debt Recovered|18| |
| |Bad Debt Relief|17| |
| |Total Input Tax (Inclusive of Bad Debt Relief & other Adjustments)| |62|
| |Total Output Tax (Inclusive of Bad Debt Recovered & other Adjustments)| |52|
| |Total Value of Capital Goods Acquired|16| |
| |Total Value of Exempt Supplies|12| |
| |Total Value of Export Supplies|11| |
| |Total Value of Goods Imported Under Approved Trader Scheme|14| |
| |Total Value of GST Suspended under item 14| |15|
| |Total Value of Local Zero-Rated Supplies|10| |
| |Total Value of Standard Rated Acquisition|61| |
| |Total Value of Standard Rated Supply|51| |
| |Total Value of Supplies Granted GST Relief|13| |

You must use different tax codes for those transactions. The way that reporting codes are mapped to these tax codes and then selected in the report configurations varies, depending on your overall reporting requirements. For example, a report shows the transaction amounts on your invoices, debit notes, and credit notes separately. Therefore, you map the various reporting codes (1001 for invoices, 1002 for debit notes, and 1003 for credit notes) to specific tax codes. However, if you must show a transaction such as Total Value of Standard Rated Supply in GST-03, credit notes, debit notes, and invoices aren't differentiated. Therefore, you must select **1001**, **1002**, and **1003** for the transaction amounts.

### Running the GST report by configuration report

After you book your transactions and define your report configurations, you can run the **GST report by configuration** report. You must provide following parameters:

-   **Settlement period** – Specify the settlement period to generate the report for.
-   **From date** – The first date in the interval for this settlement period.
-   **Report configuration** – Select one of the report configurations that you've defined.

## GAF

Royal Malaysian Customs Department (MRCD) will periodically audit your business to make sure that you're making correct tax declarations. For auditing purposes, you can generate a GAF in XML format. The GAF contains a detailed breakdown of business transactions. It mainly contains the following information for a taxable period:

-   Company information
-   Purchases
-   Supplies
-   Ledger transactions
-   Footer (Summary)

For the GAF to be generated, specific business data must be captured.

For the "Company information" section, the GAF version must be specified on the **General ledger parameters** page. 

For the "Purchases" section, when goods are imported from overseas vendors, the declaration number should be captured for each vendor invoice. In the GAF, transactions besides regular sales orders and purchases orders should be considered purchases or supply. For example, you make payment to vendors, and you must also pay bank fees to banks. Per Malaysia GST regulations, GST will be applied to the bank charge. The bank will provide a GST invoice to you, and you can claim the GST input tax. The tax authority will expect to see that the bank charges are considered purchases in the GAF that is generated. In such cases, Finance lets users capture the required GAF information. You can now capture the organization number for a bank group. By default, payment fee transactions of corresponding banks will be used. You can also enter required GAF information for various journals and payment fees, according to your business requirements. For example, you can enter GAF information for expense type journals in Project management and accounting, expense type service order lines, or expenses on expense reports. If any miscellaneous charges are applied to a free text invoice or vendor invoice, the GAF information is inherited from the document. You also can preview the supply and purchase records where GST applies, and you can edit or add relevant information on the **GAF purchase and supply review** page. You must make sure that you select the **GST** check box on the **Sales tax codes** page for each of your GST tax codes.

To generate the GAF, click **Tax** &gt; **Declarations** &gt; **Sales tax** &gt; **Generate GAF file**, and provide the following required information:

-   **Settlement period** – Specify the settlement period to generate the GAF for.
-   **From date** – The first date in the interval for this settlement period.
-   **Creation date** – The GAF creation date. This information will appear in the company section of the GAF.
-   **Posting layer** – Specify which posting layers to generate the GAF from. The posting layers affect the ledger transactions that are included in the GAF.

You should run the **Settle and post sales tax** process before you generate the GAF for a period. The GAF will include only those transactions that are included in a sales tax payment.

## Additional resources
- [Generate GAF files in the required format ](./tasks/my-00010-gst-gaf-files-required-format.md)
- [Manage customer Debit note and Credit note for GST](./tasks/my-00003-manage-customer-debit-note-credit-note-gst.md)
- [Manage vendor Debit note and Credit note for GST](./tasks/my-00004-manage-vendor-debit-note-credit-note-gst.md)
- [Print GST customer invoices with a relief clause](./tasks/my-00006-02-print-gst-customer-invoices-relief-clause.md)
- [Print GST tax invoices](./tasks/my-00005-print-gst-tax-invoices.md)
- [Set up GST relief clauses](./tasks/my-00006-01-gst-relief-clauses.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
