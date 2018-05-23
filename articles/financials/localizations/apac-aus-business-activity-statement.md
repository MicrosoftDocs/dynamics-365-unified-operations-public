---
# required metadata

title: Business Activity Statement (BAS)
description: This topic provides information about the business activity statement (BAS) for Australia. The BAS is a form submitted to the Australian Taxation Office by all businesses to report their taxation obligations.          
author: ShylaThompson
manager: AnnBe
ms.date: 05/23/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 12641
ms.search.region: Australia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Business activity statement (BAS)

[!INCLUDE [banner](../includes/banner.md)]

This topic provides information about the business activity statement (BAS) for Australia. The BAS is a form submitted to the Australian Taxation Office by all businesses to report their taxation obligations.          

The business activity statement feature in Microsoft Dynamics 365 for Finance and Operations
is designed to help you fill out your Business Activity Statement, commonly known as the BAS. It is very similar to the Calculation Sheet that the Australian Taxation Office provides you when you receive your BAS form in the mail. The taxation liabilities in the BAS include the following:

-   GST amounts you owe the Australian Taxation Office from sales
-   GST amounts the Australian Taxation Office owes you from purchases
-   Pay-As-You-Go (PAYG) Tax Withheld
-   Pay-As-You-Go (PAYG) Instalment
-   Fringe Benefit Tax (FBT)

The following list provides an overview of the process to calculate GST and prepare the BAS in General ledger:

1.  [Set up GST prerequisites](apac-aus-business-activity-statement.md#prerequisites) 
2.  [Set up report boxes](tasks/add-bas-report-boxes.md) - You must set up BAS report boxes to report other non-GST tax liabilities and credits for a particular GST settlement periods.
3.  Post and settle Australian BAS to tax authorities for a particular GST settlement period.
4.  Process payments to tax authorities.
5.  Manually adjust journals to transfer non-GST transactions posted to the BAS reconciliation account to the correct ledger account.
6.  [Print and review GST reports](apac-aus-business-activity-statement.md#generate-the-australian-bas).

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
<td>The primary address for the legal entity must be in the following countries/regions: Australia.</td>
</tr>
<tr>
  <td>Download Electronic reporting configurations</td>
  <td>Before you can set up or generate BAS, you must download the <strong>BAS (AU)</strong> configuration from Lifecycle Services using the Electronic reporting workspace. For more information, see <a href="https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs?toc=/fin-and-ops/toc.json">Download Electronic reporting configurations from Lifecycle Services</a>.</td>
</tr>
<tr>
<td>General ledger parameters</td>
  <td><ul>
    <li>Set the <strong>Apply sales tax taxation rules</strong> option to <strong>No</strong> on the <strong>General ledger parameters </strong> page.</li>
    <li>In the <strong>Sales tax</strong> area, select <strong>BAS(AU)</strong> for the <strong>Australian BAS Format mapping</strong> field.</li>
    </ul>
</td>
</tr>
<tr>
  </tr>
  <tr>
    <td>Create an additional BAS reconciliation account</td>
    <td></td>
  </tr>
    <tr>
    <td><a href="../general-ledger/tasks/set-up-ledger-posting-groups-sales-tax.md">Create ledger posting groups.</a></td>
    <td></td>
  </tr>
    <tr>
    <td>Set up the GST sales tax authority</td>
    <td></td>
  </tr>
    <tr>
    <td>Create settlement periods</td>
    <td></td>
  </tr>
    <tr>
    <td><a href="#gst-reporting-codes">Set up sales tax reporting codes for GST</a></td>
    <td></td>
  </tr>
    <tr>
    <td><a href="../general-ledger/tasks/set-up-sales-tax-codes.md">Set up sales tax codes</a></td>
    <td></td>
  </tr>
    <tr>
    <td><a href="tasks/set-up-reason-codes-australia-bas.md">Set up reason codes for Australia BAS</a></td>
    <td></td>
  </tr>
  <tr>
    <td>Set up BAS fringe benefit reason codes</td>
    <td></td>
  </tr>
  <tr>
    <td><a href="../general-ledger/tasks/set-up-withholding-tax.md">Set up withholding tax codes and groups</a></td>
    <td></td>
  </tr>
  <tr>
    <td>Create and save the BAS XML file</td>
    <td>This is the file that you'll use when you generate and print the Australian BAS. See a <a href="apac-aus-business-activity-statement#sample-xml-file">sample XML file</a> for more information.</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

## GST reporting codes

The BAS report layout is specific about how and where different amounts should be reported, about the fields that are added together and about linking the Sales tax codes to the particular reporting codes. The GST reporting codes refer to a field number on the tax report for the report layout. The codes are linked by associating a GST code to a particular reporting code on the **Report setup** FastTab on the **Sales tax codes** page.

Based on a quarterly BAS format, the following reporting codes must be set up. These reporting codes are associated with the field that appears on the BAS report. You can set up the reporting codes on the **Sales tax reporting codes** page (**Tax > Setup > Sales tax > Sales tax reporting codes**).

| Report Layout | Reporting Code | Report Text                                                                | Field in BAS report |
|---------------|----------------|----------------------------------------------------------------------------|---------------------|
| Default       | 1              | G1 Total sales & income and other supplies                                 | G1                  |
| Default       | 2              | G2 GST free exports                                                        | G2                  |
| Default       | 3              | G3 Other GST free supplies                                                 | G3                  |
| Default       | 4              | G4 Input taxed sales & income and other supplies                           | G4                  |
| Default       | 7              | G7 Adjustment payable                                                      | G7                  |
| Default       | 9              | G9 and 1A Goods and services tax payable                                   | G9 and 1A           |
| Default       | 10             | G10 Capital acquisitions                                                   | G10                 |
| Default       | 11             | G11 Other acquisitions                                                     | G11                 |
| Default       | 13             | G13 Acquisitions for making input taxed sales & income and other supplies  | G13                 |
| Default       | 14             | G14 Acquisitions with no GST in the price                                  | G14                 |
| Default       | 15             | Non-income tax deductible acquisitions                                     | G15                 |
| Default       | 18             | G18 Adjustment (credit)                                                    | G18                 |
| Default       | 101            | 1C Wine equalization tax payable                                           | 1C                  |
| Default       | 102            | 1D Wine equalization tax refundable                                        | 1D                  |
| Default       | 201            | 1E Luxury car tax payable                                                  | 1E                  |
| Default       | 202            | 1F Luxury car tax refundable                                               | 1F                  |
| Default       | 400            | 4 Pay As You Go Withholding                                                | 4                   |
| Default       | 501            | 5A Pay As You Go Instalment                                                | 5A                  |
| Default       | 502            | 5B Credit arising from reduced Pay As You Go instalment                    | 5B                  |
| Default       | 601            | 6A Fringe benefit tax instalment                                           | 6A                  |
| Default       | 602            | 6B Credit arising from fringe benefits tax instalment                      | 6B                  |
| Default       | 700            | 7 Deferred company/ fund instalment                                        | 7                   |
| Default       | 701            | 7A Deferred GST on imports                                                 | 7A                  |
| Default       | 31             | W1 Total of salary, wages and other payments                               | W1                  |
| Default       | 32             | W2 Amounts withheld from salary, wages and other payments                  | W2                  |
| Default       | 33             | W3 Amounts withheld from investment distributions where no TFN is quoted   | W3                  |
| Default       | 34             | W4 Amounts withheld from payment of invoices where no ABN is quoted        | W4                  |
| Default       | 51             | T1 Instalment income                                                       | T1                  |
| Default       | 52             | T2 Commissioner’s instalment rate                                          | T2                  |
| Default       | 53             | T3 New varied instalment rate                                              | T3                  |
| Default       | 54             | T4 Reason for variation                                                    | T4                  |
| Default       | 61             | F1 ATO-calculated fringe benefits tax instalment                           | F1                  |
| Default       | 62             | F2 Estimated total fringe benefits tax payable                             | F2                  |
| Default       | 63             | F3 Varied fringe benefits tax instalment                                   | F3                  |
| Default       | 64             | F4 Reason for fringe benefits tax variation                                | F4                  |
| Default       | 140            | A1 Document identification number                                          | A1                  |
| Default       | 1013           | G13 Acquisitions for making input taxed sales, income and other supplies   | G13                 |
| Default       | 1014           | G14 Capital acquisitions with no GST in the price                          | G14                 |
| Default       | 1015           | G15 Capital acquisitions for private use or with non-income tax deductions | G15                 |

> [!NOTE] 
> The reporting code numbers 5 and 6 are missing. This is because these two codes are used for calculated fields on the BAS report.

## Generate the Australian BAS
1.	Go to **Tax > Declarations > Sales tax > Australian BAS**.
2.	In the **Settlement period** field, select the settlement period.
3.	In the **From date** field, enter a date.
4.	In the **Transaction date** field, enter a date.
5.	Select or clear the **Post and settle GST check box**.
7.	Click **OK**.
8.	When Electronic Reporting is set up for Australian BAS, the **Print Australian BAS** page is available for you to generate the E-BAS statement.

![Print Australian BAS](media/apac-aus-print-bas.png)

9. Set the **Generate E-BAS** option to be **Yes**.
10. On the **Select a file** page, select the xml file to use and click **OK**.

## Sample XML file

Create an XML file with the following information.

```
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
Before using the XML file, be sure to change the values for each of the fields being used so that they are appropriate for your company. The value for each field is listed below: 
            
            case 'fA1' : // Document Identification Number
            case 'fF1' : // FringeATO
            case 'fT2' : // PaygCommRate
            case 'f7'  : // Deferred Instalment
            case 'f7A' : //deferred gst On Imported goods
            case 'fA3' : //fromDate
            case 'fA4' : //toDate
            case 'fMANUAL_MODE' : //manualMode
                
> [!NOTE]
> The dates must be in dd/mm/yyyy format.

## Additional resources
[Electronic reporting overview](../../dev-itpro/analytics/general-electronic-reporting.md)
