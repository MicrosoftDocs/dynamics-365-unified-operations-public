---
# required metadata

title: Business activity statement 
description: This topic provides information about the business activity statement (BAS) for Australia. The BAS is a form that all businesses submit to the Australian Taxation Office to report their taxation obligations.
author: ShylaThompson
manager: AnnBe
ms.date: 06/15/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 12641
ms.search.region: Australia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Business activity statement

[!include [banner](../includes/banner.md)]

This topic provides information about the business activity statement (BAS) for Australia. The BAS is a form that all businesses submit to the Australian Taxation Office to report their taxation obligations.

The Business activity statement feature is designed to help you fill out your BAS. It resembles the calculation worksheet that the Australian Taxation Office provides when you receive the BAS form in the mail. The BAS includes the following taxation liabilities:

- Goods and Services Tax (GST) amounts that you owe the Australian Taxation Office from sales
- GST amounts that the Australian Taxation Office owes you from purchases
- Pay-As-You-Go (PAYG) Tax Withheld
- PAYG Instalment
- Fringe Benefit Tax (FBT)

Here is an overview of the process for calculating GST and preparing the BAS in General ledger.

1. [Set up GST prerequisites](apac-aus-business-activity-statement.md#prerequisites).
2. [Set up report boxes](tasks/add-bas-report-boxes.md). You must set up BAS report boxes to report other non-GST tax liabilities and credits for a specific GST settlement period.
3. Post the BAS to the tax authorities for a specific GST settlement period, and settle it.
4. Process payments to the tax authorities.
5. Manually adjust journals, so that non-GST transactions that were posted to the BAS reconciliation account are transferred to the correct ledger account.
6. [Print and review GST reports](apac-aus-business-activity-statement.md#generate-the-australian-bas).

## Prerequisites

<table>
<thead>
<tr class="header">
<th>Category</th>
<th>Prerequisite</th>
</tr>
</thead>
<tbody>
<tr>
<td>Country/region</td>
<td>The primary address for the legal entity must be in Australia.</td>
</tr>
<tr>
<td>Download Electronic reporting (ER) configurations.</td>
<td>Before you can set up or generate the BAS, you must download the <strong>BAS (AU)</strong> configuration from Microsoft Dynamics Lifecycle Services (LCS) by using the <strong>Electronic reporting</strong> workspace. For more information, see <a href="https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs?toc=/fin-and-ops/toc.json">Download Electronic reporting configurations from Lifecycle Services</a>.</td>
</tr>
<tr>
<td>General ledger parameters</td>
<td>
<ul>
<li>On the <strong>General ledger parameters</strong> page, set the <strong>Apply sales tax taxation rules</strong> option to <strong>No</strong>.</li>
<li>On the <strong>Sales tax</strong> tab, in the <strong>Australian BAS Format mapping</strong> field, select <strong>BAS(AU)</strong>.</li>
</ul>
</td>
</tr>
<tr>
<td>General setup</td>
<td>
<ul>
<li>Create an additional BAS reconciliation account.</li>
<li><a href="../general-ledger/tasks/set-up-ledger-posting-groups-sales-tax.md">Create ledger posting groups</a>.</li>
<li>Set up the sales tax authority for GST.</li>
<li>Create settlement periods.</li>
<li><a href="#gst-reporting-codes">Set up sales tax reporting codes for GST</a>.</li>
<li><a href="../general-ledger/tasks/set-up-sales-tax-codes.md">Set up sales tax codes</a>.</li>
<li><a href="tasks/set-up-reason-codes-australia-bas.md">Set up reason codes for the BAS</a>.</li>
<li>Set up reason codes for BAS fringe benefits.</li>
<li><a href="../general-ledger/tasks/set-up-withholding-tax.md">Set up withholding tax codes and groups</a>.</li>
</ul>
</td>
</tr>
<tr>
<td>Create and save the BAS XML file.</td>
<td>You will use this file when you generate and print the BAS. For more information, see a <a href="apac-aus-business-activity-statement.md#sample-xml-file">sample XML file</a>.</td>
</tr>
</tbody>
</table>

## GST reporting codes

For the BAS report layout, the various amounts must be reported in specific ways and in specific places, specific fields are added together, and sales tax codes are linked to reporting codes in specific ways. The GST reporting codes refer to a field number on the tax report for the report layout. The codes are linked by associating a GST code with a specific reporting code on the **Report setup** FastTab of the **Sales tax codes** page.

For a quarterly BAS format, the following reporting codes must be set up. These reporting codes are associated with fields that appear on the BAS report. You can set up the reporting codes on the **Sales tax reporting codes** page (**Tax \> Setup \> Sales tax \> Sales tax reporting codes**).

| Report layout | Reporting code | Report text                                                                | Field on the BAS report |
|---------------|----------------|----------------------------------------------------------------------------|-------------------------|
| Default       | 1              | G1 Total sales & income and other supplies                                 | G1                      |
| Default       | 2              | G2 GST free exports                                                        | G2                      |
| Default       | 3              | G3 Other GST free supplies                                                 | G3                      |
| Default       | 4              | G4 Input taxed sales & income and other supplies                           | G4                      |
| Default       | 7              | G7 Adjustment payable                                                      | G7                      |
| Default       | 9              | G9 and 1A Goods and services tax payable                                   | G9 and 1A               |
| Default       | 10             | G10 Capital acquisitions                                                   | G10                     |
| Default       | 11             | G11 Other acquisitions                                                     | G11                     |
| Default       | 13             | G13 Acquisitions for making input taxed sales & income and other supplies  | G13                     |
| Default       | 14             | G14 Acquisitions with no GST in the price                                  | G14                     |
| Default       | 15             | Non-income tax deductible acquisitions                                     | G15                     |
| Default       | 18             | G18 Adjustment (credit)                                                    | G18                     |
| Default       | 101            | 1C Wine equalization tax payable                                           | 1C                      |
| Default       | 102            | 1D Wine equalization tax refundable                                        | 1D                      |
| Default       | 201            | 1E Luxury car tax payable                                                  | 1E                      |
| Default       | 202            | 1F Luxury car tax refundable                                               | 1F                      |
| Default       | 400            | 4 Pay As You Go Withholding                                                | 4                       |
| Default       | 501            | 5A Pay As You Go Instalment                                                | 5A                      |
| Default       | 502            | 5B Credit arising from reduced Pay As You Go instalment                    | 5B                      |
| Default       | 601            | 6A Fringe benefit tax instalment                                           | 6A                      |
| Default       | 602            | 6B Credit arising from fringe benefits tax instalment                      | 6B                      |
| Default       | 700            | 7 Deferred company/ fund instalment                                        | 7                       |
| Default       | 701            | 7A Deferred GST on imports                                                 | 7A                      |
| Default       | 31             | W1 Total of salary, wages and other payments                               | W1                      |
| Default       | 32             | W2 Amounts withheld from salary, wages and other payments                  | W2                      |
| Default       | 33             | W3 Amounts withheld from investment distributions where no TFN is quoted   | W3                      |
| Default       | 34             | W4 Amounts withheld from payment of invoices where no ABN is quoted        | W4                      |
| Default       | 51             | T1 Instalment income                                                       | T1                      |
| Default       | 52             | T2 Commissioner's instalment rate                                          | T2                      |
| Default       | 53             | T3 New varied instalment rate                                              | T3                      |
| Default       | 54             | T4 Reason for variation                                                    | T4                      |
| Default       | 61             | F1 ATO-calculated fringe benefits tax instalment                           | F1                      |
| Default       | 62             | F2 Estimated total fringe benefits tax payable                             | F2                      |
| Default       | 63             | F3 Varied fringe benefits tax instalment                                   | F3                      |
| Default       | 64             | F4 Reason for fringe benefits tax variation                                | F4                      |
| Default       | 140            | A1 Document identification number                                          | A1                      |
| Default       | 1013           | G13 Acquisitions for making input taxed sales, income and other supplies   | G13                     |
| Default       | 1014           | G14 Capital acquisitions with no GST in the price                          | G14                     |
| Default       | 1015           | G15 Capital acquisitions for private use or with non-income tax deductions | G15                     |

> [!NOTE]
> Reporting codes 5 and 6 are missing from the table because those two codes are used for calculated fields on the BAS report.

## Generate the Australian BAS

1. Go to **Tax \> Declarations \> Sales tax \> Australian BAS**.
2. In the **Settlement period** field, select the settlement period.
3. In the **From date** field, enter a date.
4. In the **Transaction date** field, enter a date.
5. Select or clear the **Post and settle GST** check box.
6. Select **OK**.

    When ER is set up for the BAS, the **Print Australian BAS** page is available. You can use this page to generate the E-BAS statement.

    ![Print Australian BAS page](media/apac-aus-print-bas.png)

7. Set the **Generate E-BAS** option to **Yes**.
8. On the **Select a file** page, select the XML file to use, and then select **OK**.

## Sample XML file

Create an XML file that contains the following information.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<DATA>
        <field ID="fA1">BAS1</field>
        <field ID="fF1"></field>
        <field ID="fT2"></field>
        <field ID="f7"></field>
        <field ID="f7A"></field>
        <field ID="fA3">1/4/2017</field>
        <field ID="fA4">30/4/2017</field>
        <field ID="fMANUAL_MODE">true</field>
    <FIELD_LIST>
    </FIELD_LIST> 
</DATA>
```

Before you use the XML file, be sure to change the values for the fields that are used, so that they are appropriate for your company. Here are the values for each field.

```xpp
case 'fA1' : // Document Identification Number
case 'fF1' : // FringeATO
case 'fT2' : // PaygCommRate
case 'f7'  : // Deferred Instalment
case 'f7A' : // deferred gst On Imported goods
case 'fA3' : // fromDate
case 'fA4' : // toDate
case 'fMANUAL_MODE' : // manualMode
```

> [!NOTE]
> The dates must be in dd/mm/yyyy format.

## Additional resources

[Electronic reporting overview](../../dev-itpro/analytics/general-electronic-reporting.md)
