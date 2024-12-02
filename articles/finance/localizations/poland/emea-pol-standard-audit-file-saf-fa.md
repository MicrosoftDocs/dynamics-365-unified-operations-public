---
title: SAF VAT invoices file - JPK_FA
description: This article explains how users in legal entities in Poland can generate a SAF VAT invoices file - JPK_FA in XML format.
author: liza-golub
ms.author: egolub
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 11/26/2024
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2016-11-30
ms.search.form: LedgerParameters, TaxAuthority, TaxReportCollection, TaxTable
ms.dyn365.ops.version: Version 1611
ms.assetid: b85c4019-f682-45bf-9a0d-c7549a2f1274
---

# SAF VAT invoices file - JPK_FA

[!include [banner](../../includes/banner.md)]

This article explains how to set up Microsoft Dynamics 365 Finance to configure and generate a SAF VAT invoices file - JPK_FA for legal entities that have a primary address in Poland.

SAF Invoice File (JPK_FA) is a standardized electronic format that enables businesses to submit detailed records of issued sales invoices directly to Polish tax authorities. The file that is generated in this format, SAF VAT invoices file - JPK_FA, includes comprehensive information about invoice data, such as buyer and seller details, transaction dates, amounts, and value-added tax (VAT) rates. Therefore, it ensures transparency and facilitates tax audits.

A SAF VAT invoices file - JPK_FA must be submitted whenever Polish tax authorities request one. It must be submitted electronically through the Polish tax authority's portal.

## Setup

Before you can generate a SAF VAT invoices file - JPK_FA, you must complete the following setup.

1. [Import Electronic reporting (ER) configurations](#er-import).
1. [Set up the ER format in General ledger parameters](#er-format-setup).
1. [Set up sales tax authorities](#tax-authorities).
1. [Set up sales tax reporting codes](#tax-codes).
1. [Configure application-specific parameters for the format of the report](#asp-setup).

### <a id="er-import"></a>Import ER configurations

In Finance, import the following ER configurations from Dataverse. Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../../localizations/global/workspace/gsw-import-er-config-dataverse.md).

| ER configuration name | Type | Description |
|---|---|---|
| Standard Audit File (SAF-T) | Model | The common data model for different audit reports. |
| Standard Audit File model mapping | Model mapping | The model mapping that provides general source mapping for several electronic reports for Poland. |
| SAF Poland | Format | The XML format that represents a parent format for several JPK formats for Poland. |
| VAT Invoices (PL) | Format | VAT Invoices SAF-T for Poland, JPK_FA. |

Import the most recent versions of the configurations. The version description usually includes the number of the Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

> [!IMPORTANT]
> After all the ER configurations from the previous table are imported, set the **Default for model mapping** option to **Yes** for the **Standard Audit File model mapping** configuration.

### <a id="er-format-setup"></a>Set up the ER format in General ledger parameters

To set up the ER format in General ledger parameters, follow these steps.

1. Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
1. On the **Standard Audit File for Tax (SAT-T)** tab, in the **SAF VAT invoices** field, select the **VAT Invoices (PL)** ER format.

### <a id="tax-authorities"></a>Set up sales tax authorities

You can find general information about how to set up a sales tax authority in [Set up sales tax authorities](../../general-ledger/tasks/set-up-sales-tax-authorities.md).

To generate a SAF VAT invoices file - JPK_FA as an XML file in the required format for the appropriate tax authority, you must set up the report layout for sales tax authorities.

To set up the report layout for sales tax authorities, follow these steps.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax authorities**.
1. Set the **Report layout** field to **Default**.
1. Select the same sales tax authority for the sales tax settlement period that will be used for the sales tax codes.

### <a id="tax-codes"></a>Set up sales tax reporting codes

A reporting code is an integer value. Reporting codes should be numbered according to the company's rules. You can find general information about how to set up sales tax reporting codes in [Set up sales tax reporting codes](../../general-ledger/tasks/set-up-sales-tax-reporting-codes.md). You can find general information about how to report tax by reporting codes in [Tax reporting by reporting codes](../../localizations/europe/emea-vat-reporting.md).

We recommend that you vary the codes by tax direction. For example, use a five-digit code. For all outgoing transactions, which should be reflected in the first part of the VAT scheme, set the codes so that they are less than or equal to 19999. Then, for all incoming transactions, which should be reflected in the second part of the VAT scheme, set the codes so that they are greater than or equal to 20000. In this way, you simplify the setup for reports and for data export that is based on tax transactions that are aggregated by reporting codes.

Here is an example that shows how you can use sales tax reporting codes to generate a SAF VAT sales and purchase register - JPK_VAT. For this example, reporting codes are in the format *ABBCC*. This format consists of the following parts:

- **A** – The transaction direction. The value is **1** for outgoing transactions, **2** for incoming transactions, or **3** for corrections.
- **BB** – The tax code. The numbering is sequential among all tax codes.
- **CC** – The transaction type number within a tax code, as explained in the following table.

    | Transaction type | Transaction type number |
    |---|---|
    | Taxable Sales | 01 |
    | Tax-free sales | 02 |
    | Sales tax payable | 03 |
    | Taxable sales credit note | 04 |
    | Tax exempt sales credit note | 05 |
    | Sales tax on sales credit note | 06 |
    | Taxable purchases | 07 |
    | Tax-free purchase | 08 |
    | Sales tax receivable | 09 |
    | Taxable import | 10 |
    | Offset taxable import | 11 |
    | Use tax | 12 |
    | Offset use tax | 13 |
    | Taxable purchase credit note | 14 |
    | Tax exempt purchase credit note | 15 |
    | Sales tax on purchase credit note | 16 |
    | Taxable import credit note | 17 |
    | Offset taxable import credit note | 18 |

The following table shows the sales tax codes and sales tax reporting codes for this example.

<table>
<thead>
<tr>
<th>Sales tax code</th>
<th>Sales tax reporting code</th>
<th>Description</th>
<th>Tag name in SAF-T VAT</th>
<th>Sign in SAF-T VAT</th>
</tr>
</thead>
<tbody>
<tr>
<td rowspan="4">ExportCust</td>
<td>10101</td>
<td>Taxable sales</td>
<td>K_11</td>
<td>-</td>
</tr>
<tr>
<td>10102</td>
<td>Tax-free sale</td>
<td>K_11</td>
<td>-</td>
</tr>
<tr>
<td>10104</td>
<td>Taxable sales credit note</td>
<td>K_11</td>
<td>-</td>
</tr>
<tr>
<td>10105</td>
<td>Tax exempt sales credit note</td>
<td>K_11</td>
<td>-</td>
</tr>
<tr>
<td rowspan="2">Art100</td>
<td>10201</td>
<td>Taxable sales</td>
<td>K_12</td>
<td>-</td>
</tr>
<tr>
<td>10204</td>
<td>Taxable sales credit note</td>
<td>K_12</td>
<td>-</td>
</tr>
<tr>
<td rowspan="5">VAT22_23</td>
<td>10301</td>
<td>Taxable sales</td>
<td>K_19</td>
<td>-</td>
</tr>
<tr>
<td>10302</td>
<td>Tax-free sale</td>
<td>K_10</td>
<td>-</td>
</tr>
<tr>
<td>10303</td>
<td>Sales tax payable</td>
<td>K_20</td>
<td>-</td>
</tr>
<tr>
<td>10304</td>
<td>Taxable sales credit note</td>
<td>K_19</td>
<td>-</td>
</tr>
<tr>
<td>10306</td>
<td>Sales tax on sales credit note</td>
<td>K_20</td>
<td>-</td>
</tr>
<tr>
<td rowspan="5">VAT7_8</td>
<td>10401</td>
<td>Taxable sales</td>
<td>K_17</td>
<td>-</td>
</tr>
<tr>
<td>10402</td>
<td>Tax-free sale</td>
<td>K_10</td>
<td>-</td>
</tr>
<tr>
<td>10403</td>
<td>Sales tax payable</td>
<td>K_18</td>
<td>-</td>
</tr>
<tr>
<td>10404</td>
<td>Taxable sales credit note</td>
<td>K_17</td>
<td>-</td>
</tr>
<tr>
<td>10406</td>
<td>Sales tax on sales credit note</td>
<td>K_18</td>
<td>-</td>
</tr>
<tr>
<td rowspan="5">VAT5</td>
<td>10501</td>
<td>Taxable sales</td>
<td>K_15</td>
<td>-</td>
</tr>
<tr>
<td>10502</td>
<td>Tax-free sale</td>
<td>K_10</td>
<td>-</td>
</tr>
<tr>
<td>10503</td>
<td>Sales tax payable</td>
<td>K_16</td>
<td>-</td>
</tr>
<tr>
<td>10504</td>
<td>Taxable sales credit note</td>
<td>K_15</td>
<td>-</td>
</tr>
<tr>
<td>10506</td>
<td>Sales tax on sales credit note</td>
<td>K_16</td>
<td>-</td>
</tr>
<tr>
<td rowspan="3">VAT0</td>
<td>10601</td>
<td>Taxable sales</td>
<td>K_13</td>
<td>-</td>
</tr>
<tr>
<td>10602</td>
<td>Tax-free sale</td>
<td>K_10</td>
<td>-</td>
</tr>
<tr>
<td>10604</td>
<td>Taxable sales credit note</td>
<td>K_13</td>
<td>-</td>
</tr>
<tr>
<td rowspan="4">ART129</td>
<td>10701</td>
<td>Taxable sales</td>
<td>K_14</td>
<td>-</td>
</tr>
<tr>
<td>10702</td>
<td>Tax-free sale</td>
<td>K_14</td>
<td>-</td>
</tr>
<tr>
<td>10704</td>
<td>Taxable sales credit note</td>
<td>K_14</td>
<td>-</td>
</tr>
<tr>
<td>10705</td>
<td>Tax exempt sales credit note</td>
<td>K_14</td>
<td>-</td>
</tr>
<tr>
<td rowspan="4">IntraEUGoods</td>
<td>10801</td>
<td>Tax-free sale</td>
<td>K_21</td>
<td>-</td>
</tr>
<tr>
<td>10810</td>
<td>Taxable import</td>
<td>K_23</td>
<td>+</td>
</tr>
<tr>
<td>10811</td>
<td>Taxable sales (Reverse charge)</td>
<td>K_23</td>
<td>-</td>
</tr>
<tr>
<td>10812</td>
<td>Use tax</td>
<td>K_24</td>
<td>+</td>
</tr>
<tr>
<td rowspan="2">ExportOfGoods</td>
<td>10901</td>
<td>Tax-free sale</td>
<td>K_22</td>
<td>-</td>
</tr>
<tr>
<td>10905</td>
<td>Tax exempt sales credit note</td>
<td>K_22</td>
<td>-</td>
</tr>
<tr>
<td rowspan="2">SpecialProc-XII</td>
<td>11303</td>
<td>Sales tax payable</td>
<td>Not applicable, JPK_FA only</td>
<td>-</td>
</tr>
<tr>
<td>11306</td>
<td>Sales tax on sales credit note</td>
<td>Not applicable, JPK_FA only</td>
<td>-</td>
</tr><tr>
<td rowspan="4">ImportOfGoodsART33</td>
<td>20207</td>
<td>Taxable import</td>
<td>K_45</td>
<td>+</td>
</tr>
<tr>
<td>11010</td>
<td>Offset Taxable import</td>
<td>K_25</td>
<td>-</td>
</tr>
<tr>
<td>20209</td>
<td>Use tax</td>
<td>K_46</td>
<td>+</td>
</tr>
<tr>
<td>11012</td>
<td>Offset use tax</td>
<td>K_26</td>
<td>-</td>
</tr>
<tr>
<td rowspan="5">ImportOfServices</td>
<td>20207</td>
<td>Taxable import</td>
<td>K_45</td>
<td>+</td>
</tr>
<tr>
<td>11110</td>
<td>Offset Taxable import</td>
<td>K_27</td>
<td>-</td>
</tr>
<tr>
<td>11117</td>
<td>Taxable sales (Reverse charge)</td>
<td>K_27</td>
<td>+</td>
</tr>
<tr>
<td>20209</td>
<td>Use tax</td>
<td>K_46</td>
<td>+</td>
</tr>
<tr>
<td>11112</td>
<td>Offset use tax</td>
<td>K_28</td>
<td>-</td>
</tr>
<tr>
<td rowspan="5">ImportART28</td>
<td>20207</td>
<td>Taxable import</td>
<td>K_45</td>
<td>+</td>
</tr>
<tr>
<td>11210</td>
<td>Offset Taxable import</td>
<td>K_29</td>
<td>-</td>
</tr>
<tr>
<td>11119</td>
<td>Taxable sales (Reverse charge)</td>
<td>K_29</td>
<td>+</td>
</tr>
<tr>
<td>20209</td>
<td>Use tax</td>
<td>K_46</td>
<td>+</td>
</tr>
<tr>
<td>11212</td>
<td>Offset use tax</td>
<td>K_30</td>
<td>-</td>
</tr>
<tr>
<td rowspan="4">ReverseCharge</td>
<td>11301</td>
<td>Taxable sales</td>
<td>K_34</td>
<td>-</td>
</tr>
<tr>
<td>11302</td>
<td>Sales tax payable</td>
<td>K_35</td>
<td>-</td>
</tr>
<tr>
<td>11304</td>
<td>Taxable sales credit note</td>
<td>K_34</td>
<td>-</td>
</tr>
<tr>
<td>11306</td>
<td>Sales tax on sales credit note</td>
<td>K_35</td>
<td>-</td>
</tr>
<tr>
<td rowspan="4">FixedAssetPurch</td>
<td>20107</td>
<td>Taxable purchases</td>
<td>K_43</td>
<td>+</td>
</tr>
<tr>
<td>20109</td>
<td>Sales tax receivable</td>
<td>K_44</td>
<td>+</td>
</tr>
<tr>
<td>20115</td>
<td>Taxable purchase credit note</td>
<td>K_43</td>
<td>+</td>
</tr>
<tr>
<td>20116</td>
<td>Sales tax on purchase credit note</td>
<td>K_47</td>
<td>+</td>
</tr>
<tr>
<td rowspan="4">GoodServPurch</td>
<td>20207</td>
<td>Taxable purchases</td>
<td>K_45</td>
<td>+</td>
</tr>
<tr>
<td>20209</td>
<td>Sales tax receivable</td>
<td>K_46</td>
<td>+</td>
</tr>
<tr>
<td>20215</td>
<td>Taxable purchase credit note</td>
<td>K_45</td>
<td>+</td>
</tr>
<tr>
<td>20216</td>
<td>Sales tax on purchase credit note</td>
<td>K_48</td>
<td>+</td>
</tr>
<tr>
<td rowspan="2">CorrATR89b1</td>
<td>30101</td>
<td>Sales tax payable</td>
<td>K_49</td>
<td>+</td>
</tr>
<tr>
<td>30109</td>
<td>Sales tax receivable</td>
<td>K_49</td>
<td>+</td>
</tr>
<tr>
<td rowspan="2">CorrATR89b4</td>
<td>30201</td>
<td>Sales tax payable</td>
<td>K_50</td>
<td>+</td>
</tr>
<tr>
<td>30209</td>
<td>Sales tax receivable</td>
<td>K_50</td>
<td>+</td>
</tr>
</tbody>
</table>

For invoices that aren't paid within 150 days, an **Overdue debt VAT** periodic task can be applied. In this case, the same reporting codes that are used for **K_44** and/or **K_46** can be used. The system automatically interprets transactions for reporting in **K_49** (Overdue invoice) and **K_50** (Paid overdue invoice).

Initially, the configuration is an example of a SAF VAT invoices file - JPK_FA that is based on the reporting codes from the table earlier in this article. If you must adapt the configuration to another set of reporting codes, use the configuration to derive the format.

1. In the configuration tree, select the format. Then select **Create configuration**.
1. Select the **Derive from name** option, enter the name and description of the new format, and then select **Create configuration**. The format that is created is a copy of the parent format.
1. Select the new format, and then select **Designer**.
1. Update the format with your reporting codes.

    The **Format designer** page is divided into two parts. The left side shows a format structure. (In the case of the VAT register, this structure is an XML scheme.) The right side shows a data model (data).

1. On the right side of the page, select **Mapping** to view the data model. The data model includes all the fields for all the SAF-T reports. The **VAT invoices** format includes several parts that have different data sources.
1. Data under the **Faktura** tag is mapped mostly to the **Model** \> **SourceDocuments** \> **\$Invoices** node. Scroll down the tree to find and select the node.
1. Under the **Invoices** node, find the **list_P_** calculated fields, and use the formula designer to update their formulas with your reporting codes.

    The **Formula designer** page shows the data model, where you can select fields or record lists. The right side of the page shows all the functions that you can implement. Learn more about the formula designer in [Formula designer in Electronic reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting-formula-designer.md).

1. The values for tags under the **StawkiPodatku** tag are constants. For each tag under the **StawkiPodatku** tag, select the value node (string). Then, on the **Format** tab on the right side of the page, set up the value in the **Value** field. No other modifications to the format are needed.
1. Save and close the format.
1. On the **Configurations** page, on the **Versions** FastTab, complete the format by selecting **Change status** \> **Complete**.

### <a id="asp-setup"></a>Configure application-specific parameters for the format of the report

To correctly report some of the important tags on the report, define the application-specific parameters.

1. On the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. Select the version of the format that you're going to use, and then set up the values for each lookup in the list on the right.

    | Name | Short description (English) | Short description (Polish) | Description (English) | Description (Polish) |
    |---|---|---|---|---|
    | [TaxFree_LOOKUP](#tax-free-lookup) | Tax-free | Tax free | Non-taxable transactions for the supply of goods and services outside the country/region. These transactions are exempt from taxation. | Niepodlegające opodatkowaniu-transakcje dostawy towarów oraz świadczenia usług poza terytorium kraju; zwolnione z opodatkowania. |
    | [TaxExemptReason_LOOKUP](#tax-exempt-lookup) | Tax-exempt reason | Przyczyna lub podstawa zwolnienia z podatku lub jego zmniejszenia | When the delivery of goods or the provision of services is exempt from tax in accordance with article 43, paragraph 1; article 113, sections 1 and 9; or provisions that are issued on the basis of article 82, paragraph 3. | W przypadku dostawy towarów lub świadczenia usług zwolnionych od podatku na podstawie art. 43 ust. 1, art. 113 ust. 1 i 9 albo przepisów wydanych na podstawie art. 82 ust. 3. |
    | [ItemType_LOOKUP](#item-type-lookup) | Type of item | Rodzaj przedmiotu | Delivery of second-hand goods, works of art, collector's items, and antiques for which the tax base is constituted in accordance with article 120, paragraph 4, margin 5. New means of transport are the subject of intra-community supply. | Dostawy towarów używanych, dzieł sztuki, przedmiotów kolekcjonerskich i antyków, dla których podstawę opodatkowania stanowi zgodnie z art. 120 ust. 4 i 5 marża; W przypadku gdy przedmiotem wewnątrzwspólnotowej dostawy są nowe środki transportu. |
    | [SpecialProcedures_LOOKUP](#special-procedures-lookup) | Special procedures referred to in section XII | Procedury specjalne, o których mowa w sekcji XII | A case of special procedures that are referred to in section XII in chapters 6a, 7, and 9 of the VAT Act. | Stawka podatku od wartości dodanej w przypadku procedur szczególnych, o których mowa w dziale XII w rozdziałach 6a, 7 i 9 ustawy VAT. |

#### <a id="tax-free-lookup"></a>TaxFree_LOOKUP

As of version 2 of the SAF VAT invoices file - JPK_FA, the value of the **P_12** field can report the following values in addition to the tax rate and **zw** (reverse charge):

- **oo** – Reverse charge as part of domestic transactions.
- **np** – For transactions for the delivery of goods and provision of services outside the country/region.

Go to **Tax** \> **Setup** \> **Sales tax** \> **Sales tax exempt codes** to set up and use specific exempt codes for sales tax codes that are set up as exempt in sales tax groups at **Tax** \> **Indirect tax** \> **Sales tax** \> **Sales tax groups**. In this way, you can distinguish tax transactions by these exempt codes in the report.

For the purposes of the report, you must define which exempt codes must be reported with the given values of the **P_12** tag. Select the **VAT Invoices (PL)** format, and then, on the Action Pane, on the **Configurations** tab, in the **Application specific parameters** group, select **Setup**. For the latest version of the configuration, on the **Lookups** FastTab, select **TaxFree_LOOKUP**. Then, on the **Conditions** FastTab, define conditions for the following lookup results.

| Lookup result | Exempt codes |
|---|---|
| np | Select the exempt codes that are used for sales tax transactions for the delivery of goods and provision of services outside the country/region. If there is more than one exempt code of this type, you must add a line for each additional exempt code that is used for transactions for the delivery of goods and provision of services outside the country/region. |
| zw | Select **Not blank**. All other transactions that are exempt, but that the reason isn't considered for, are reported as reverse charges as part of domestic transactions. This line must be the last line in the list. You can verify that it's the last line by looking at the value in the **Line** column. |

> [!NOTE]
> Tax transactions that are marked as **Reverse charge** are reported as **oo**. No additional setup is required.

After you complete the setup for the **TaxFree_LOOKUP** lookup field and are ready to set up the next lookup field, select **Save**.

#### <a id="tax-exempt-lookup"></a>TaxExemptReason_LOOKUP

Conditions for **TaxExemptReason_LOOKUP** are sales tax exempt codes that are defined in Finance (**Tax** \> **Setup** \> **Sales tax** \> **Sales tax exempt codes**) and then used in sales tax groups when tax transactions are posted. If no lines on an invoice have sales tax exemptions, the **P_19** field is reported with a value of **False**, and the **P_19A**, **P_19B**, and **P_19C** tags are omitted.

- **P_19A** indicates the provision of the act that was issued, based on which the taxpayer applies tax exemption.
- **P_19B** indicates the provision of Directive 2006/112/EC, which exempts the supply of goods or such services from such tax.
- **P_19C** indicates that the supply of goods or services benefits from the exemption on another legal basis.

As the last condition in the list, specify an **Inne** or **Other** result that has the value **Not blank** in the **Tax exempt code** column.

After you complete the setup for the **TaxExemptReason_LOOKUP** lookup field and are ready to set up the next lookup field, select **Save**.

#### <a id="item-type-lookup"></a>ItemType_LOOKUP

Conditions for **ItemType_LOOKUP** are sales tax codes that are defined in Finance (**Tax** \> **Setup** \> **Sales tax** \> **Sales tax codes**) and then used when tax transactions are posted. This lookup setup affects the reporting of **P_106E_3A** and **P_22** elements.

The following values are available for the setup of **ItemType_LOOKUP**.

| Name | Description (English) | Description (Polish) | Setup |
|---|---|---|---|
| SecondHandGoods | Deliveries of second-hand goods for which the tax base is constituted in accordance with article 120, paragraph 4, margin 5 | Dostawy towarów używanych dla których podstawę opodatkowania stanowi zgodnie z art. 120 ust. 4 i 5 marża | Specify sales tax codes that are used for transactions that are related to second-hand goods. After this setup is completed, an invoice that has tax transactions that use the specified **procedura marży - towary używane** tax code are reported in **P_106E_3A**. |
| ArtWorks | Deliveries of works of art for which the tax base is constituted in accordance with article 120, paragraph 4, margin 5 | Dostawy dzieł sztuk dla których podstawę opodatkowania stanowi zgodnie z art. 120 ust. 4 i 5 marża | Specify the sales tax codes that are used for transactions that are related to works of art. After this setup is completed, an invoice that has tax transactions that use the specified **procedura marży - dzieła sztuki** tax code are reported in **P_106E_3A**. |
| CollectorAntiques | Deliveries of collector's items and antiques, for which the tax base is constituted in accordance with article 120, paragraph 4, margin 5 | Dostawy przedmiotów kolekcjonerskich i antyków, dla których podstawę opodatkowania stanowi zgodnie z art. 120 ust. 4 i 5 marża | Specify the sales tax codes that are used for transactions that are related to collector's items and antiques. After this setup is completed, an invoice that has tax transactions that use the specified **procedura marży - przedmioty kolekcjonerskie i antyki** tax code are reported in **P_106E_3A**. |
| Transport | Intra-community delivery of new means of transport | Wewnątrzwspólnotowa dostawa nowych środków transportu | Specify the sales tax codes that are used for transactions that are related to intra-community delivery of new means of transport. After this setup is completed, an invoice that has tax transactions that use the specified **P_22** tax code are reported with a value of **True**. |
| Other | Other | Inne | Specify **Not blank** in the **Tax code** field. This value must be last in the list of values. This value must be mandatory for the lookup. |

When you finish configuring the values of the lookup fields, set the **State** field to **Completed**, save your changes, and then close the page.

If any lookup field doesn't have at least one **Not blank** value, an error occurs when the report is run. The error message states that the application-specific parameters are missing.

#### <a id="special-procedures-lookup"></a>SpecialProcedures_LOOKUP

Conditions for **SpecialProcedures_LOOKUP** are sales tax codes that are defined in Finance (**Tax** \> **Setup** \> **Sales tax** \> **Sales tax codes**) and then used when tax transactions are posted. This lookup setup affects the reporting of **FakturaWiersz** \> **P_12_XII** and **Zamowienie** \> **P_12Z_XII** elements.

The following values are available for the setup of **SpecialProcedures_LOOKUP**.

| Name | Description (English) | Description (Polish) | Setup |
|---|---|---|---|
| SpecialProc (XII) | Special procedures referred to in section XII | Procedury specjalne, o których mowa w sekcji XII | Specify the sales tax codes that are used for transactions that are related to the special procedures that are referred to in section XII in chapters 6a, 7, and 9 of the VAT Act. After this setup is completed, an invoice that has tax transactions that use the specified tax code is reported with a tax rate in the **\<P_12_XII\>** and **\<P_12Z_XII\>** fields of the report. |
| Other | Other | Inne | Specify **Not blank** in the **Tax code** field. This value must be last in the list of values. This value must be mandatory for this lookup. |

When you finish configuring the values of the lookup fields, set the **State** field to **Completed**, save your changes, and then close the page.

If any lookup field doesn't have at least one **Not blank** value, an error occurs when the report is run. The error message will state that the application-specific parameters are missing.

## Generate a SAF VAT invoices file - JPK_FA

To generate a SAF VAT invoices file - JPK_FA, go to **General ledger** \> **Inquiries and reports** \> **Standard Audit File for Tax (SAF-T)** \> **SAF VAT invoices**, set the following parameters, and then select **OK**.

| Parameter | Description |
|---|---|
| From date | Specify the first date to export reporting data for. |
| To date | Specify the last date to export reporting data for. |
| Authority identification | In the list, select the identifier of the tax authority to use in the export file. |
| Invoice ID From/To | Specify a range of invoice IDs to limit the invoices that are selected for data export. |
| Currency code | Specify the code of the currency that you want to generate the report for. Only invoices in the specified currency are included on the report. To generate a report for all currencies in one file, leave the field blank. |

You can specify additional selection parameters by selecting **Filter** on the **Records to include** tab.

## Using a batch job to generate a SAF VAT invoices file - JPK_FA

A SAF VAT invoices file - JPK_FA for a long period, such as a month or a quarter, can include a large amount of data and take a long time to be generated. Therefore, we recommend that you use batch jobs. The dialog box for every SAF report includes a **Run in the background** tab where you can set up report generation in batch mode. Set the **Batch processing** option to **Yes**. Learn more about batch processing in [Batch processing overview](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md).

To review batch jobs or find a generated file, follow these steps.

1. Go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.
1. Find a line that is related to your job, and then select **Show log**. If nothing is shown, no messages were produced when the file was generated.
1. To view a file, select **Show files**, find the file that you need, and then select **Open**.

When an electronic report is generated in batch mode, you can find related batch information and the generated output file as an attachment by going to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.

Learn more about how to configure a destination for each ER format configuration and its output component in [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

## Implementation details

In version 3 of the SAF VAT invoices file - JPK_FA, invoices that have different document currencies can be reported in the same file. For this purpose, the **Currency** parameter in the dialog box for the **SAF VAT invoices (Poland)** report is optional. If you specify a currency, the report includes only invoices that have that currency. If you don't specify a currency, the report is generated for all invoices.

### <P_14x> tags

According to the requirements of version 3 of the report, if an invoice is posted in a currency that differs from **PLN**, the **\<P_13x\>**, **\<P_14x\>**, and **\<P_15\>** tags must represent the amounts in the invoice currency, and the new **\<P_14xW\>** tags must represent related amounts in the **PLN** currency. It's assumed that **PLN** is defined as the currency for the sales tax codes that are used for transactions that will be included on the report. Based on this assumption, if the document currency on an invoice differs from the currency that is set up in the sales tax codes that are used in the tax transactions of that document, the system reports additional **\<P_14xW\>** tags. The amount is in the sales tax code currency (because the currency is assumed to be **PLN**).

### <P_18A> tag

According to the requirements of the report, the **\<P_18A\>** tag for an invoice must be reported as **True** when the split payment mechanism is applied for that invoice on a mandatory basis. To determine whether the split payment mechanism was applied to the invoice, the system checks the **Split payment** and **Voluntary split payment** properties of the customer's posted transactions (**CustTrans** table). Transactions where the **Split payment** property is applied but the **Voluntary split payment** property isn't applied are reported with a **True** value in the **\<P_18A\>** tag of the report. Learn more about the **Split payment** and **Voluntary split payment** properties in [KB4584165](https://support.microsoft.com/topic/a-country-specific-update-for-poland-to-support-split-payments-automation-0441375f-8b0e-24f7-370e-f8dc5d0760ec).

### <P_22> tag

The **\<P_22\>** tag is reported with a value of **True** according to the setup of the sales tax codes in **ItemType_LOOKUP** where **Result** = **Transport** in the application-specific parameters of the **VAT Invoices (PL)** format.

### <P_106E_3> and <P_106E_3A> tags

According to the requirements of the report, the **\<P_106E_3\>** tag must be reported as **True** for the delivery of second-hand goods, works of art, collector's items, and antiques for which the taxable base is in accordance with article 120, paragraph 4, margin 5. When the **\<P_106E_3\>** tag is reported with a value of **True**, the **\<P_106E_3A\>** tag must represent related values.

| Value of the \<P_106E_3A\> tag | Description (English) | Description (Polish) | How Finance distinguishes the tag |
|---|---|---|---|
| procedura marży - towary używane | Deliveries of second-hand goods for which the tax base is constituted in accordance with article 120, paragraph 4, margin 5 | Dostawy towarów używanych dla których podstawę opodatkowania stanowi zgodnie z art. 120 ust. 4 i 5 marża | According to the setup of sales tax codes in **ItemType_LOOKUP** where **Result** = **SecondHandGoods** in the application-specific parameters of the **VAT Invoices (PL)** format | 
| procedura marży - dzieła sztuki | Deliveries of works of art for which the tax base is constituted in accordance with article 120, paragraph 4, margin 5 | Dostawy dzieł sztuki, przedmiotów kolekcjonerskich i antyków, dla których podstawę opodatkowania stanowi zgodnie z art. 120 ust. 4 i 5 marża | According to the setup of sales tax codes in **ItemType_LOOKUP** where **Result** = **ArtWorks** in the application-specific parameters of the **VAT Invoices (PL)** format |
| procedura marży - przedmioty kolekcjonerskie i antyki | Deliveries of collector's items and antiques for which the tax base is constituted in accordance with article 120, paragraph 4, margin 5 | Dostawy przedmiotów kolekcjonerskich i antyków, dla których podstawę opodatkowania stanowi zgodnie z art. 120 ust. 4 i 5 marża | According to the setup of sales tax codes in **ItemType_LOOKUP** where **Result** = **CollectorAntiques** in the application-specific parameters of the **VAT Invoices (PL)** format |

### Zamowienie and ZamowienieCtrl nodes

According to the requirements of version 3 of the report, the **Zamowienie** node must represent the orders or contracts that are referred to in article 106f, paragraph 1, item 4 of the Act (for advance invoices) in the currency that the advance invoice was issued in (Zamówienia lub umowy, o których mowa w art. 106f ust. 1 pkt 4 ustawy (dla faktur zaliczkowych) w walucie, w której wystawiono fakturę zaliczkową).

To meet this requirement, the system collects information from the database for the lines of sales orders and free text invoices that are linked to the advance invoices that are included on the report. It then provides the following information from those lines.

| Tag name | Description (English) | Description (Polish) | How Finance collects the information |
|---|---|---|---|
| P_7Z | Name (type) of the good or service | Nazwa (rodzaj) towaru lub usługi | The value that is stored on the line of the sales order or free text invoice in the Finance database |
| P_8AZ | Unit of measure of the ordered goods or scope of service | Miara zamówionego towaru lub zakres usługi | The value of the unit of measure that is stored on the line of the sales order or free text invoice in the Finance database (If the field is empty, **usługa** is used.) |
| P_8BZ | Quantity of ordered goods or scope of service | Ilość zamówionego towaru lub zakres usługi | The value of the quantity that is stored on the line of the sales order or free text invoice in the Finance database |
| P_9AZ | Net unit price | Cena jednostkowa netto | The value of the price that is stored on the line of the sales order or free text invoice in the Finance database |
| P_11NettoZ | Value of the ordered goods or services without the amount of tax | Wartość zamówionego towaru lub usługi bez kwoty podatku | The value of the tax base amount that is calculated for the line of the sales order or free text invoice, based on the quantity that is stored on the line (**P_8BZ**) |
| P_11VatZ | Tax amount on ordered goods or services | Kwota podatku od zamówionego towaru lub usługi | The value of the tax amount that is calculated for the line of the sales order or free text invoice, based on the quantity that is stored on the line (**P_8BZ**) |
| P_12Z | Tax rate | Stawka podatku | The calculated value of the tax rate, based on the tax setup on the line of the sales order or free text invoice (sales tax group and item sales tax group) |

With respect to the values that are reported for the lines of sales orders or free text invoices, the value of the **WartoscZamowienia** tag of the **Zamowienie** node is calculated as the sum of calculated values for the tax base amount and the tax amount (**P_11NettoZ** + **P_11VatZ**) for all document lines.

The value of the **WartoscZamowien** tag of the **ZamowienieCtrl** node is calculated as the sum of **WartoscZamowienia** tag values for all the documents that are reported in the **Zamowienie** node.
