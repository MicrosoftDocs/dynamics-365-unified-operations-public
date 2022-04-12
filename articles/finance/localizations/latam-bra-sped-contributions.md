---
# required metadata

title: Set SPED EFD contributions 
description: This topic explains how to set up parameters and generate the SPED EFD - Contributions statement for Brazil. 
author: sndray
ms.date: 02/06/2020
ms.topic: article
ms.prod: 
ms.technology:

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Set SPED EFD contributions

[!include [banner](../includes/banner.md)]

The SPED EFD - Contributions statement is generated in the **Fiscal books** module. It gathers information about social contribution tax on gross revenue for the Social Integration Program (PIS) and the Contribution for Social Security Financing (COFINS).

Follow these steps to set up the requirements for SPED EFD - Contributions text files.

1. Select **Fiscal books** \> **Setup** \> **Tax statements parameters**.
2. Select **EFD - Contributions**, and then, on the **Setup parameters** FastTab, select **Open**.

    The **EFD – Contributions parameters** page appears, where you can enter the required information for SPED EFD - Contributions text files.

3. In the **Type of activity** field, select the activity type:

    - Industrial or equivalent
    - Services
    - Retail
    - Financial activity
    - Real estate activity
    - Others

4. Set the **Large company** option to **Yes** to identify the size of company. This option is used in SPED REINF statements.
5. In the **Layout version** field, select the version of the SPED EFD layout. 
6. In the **Legal entity type** field, select the type of legal entity.
7. In the **Company type** field, select the type of company:

    - PJ in general
    - PJ member of financial system
    - Insurance or capitalization societies or open-ended complementary pensions funds

8. In the **Legal nature** field, enter the code for the legal nature, according to the SPED EFD table.
9. Set the **CPRB** option to **Yes** to enable CPRB tax assessment. This option is used in SPED REINF statements.
10. In the **Tax classification code** field, select the tax classification code. This field is used in SPED REINF statements.
11. Set the **International agreement for exemption of fines** option to **Yes**.
12. In the **Assessment regimen** field, select the assessment schema that is used for SPED EFD - Contributions:

    - **Non cumulative** – Calculate assessments based on billings or debits and purchases and deductions or credits.
    - **Cumulative** – Calculate assessments based on billings that don't have any deductions or credits.
    - **Both** – Calculate assessments based on both the **Non cumulative** and **Cumulative** regimens.

13. In the **Booking and assessment criteria** field, select the criteria to use to book the tax credit.
14. In the **Type of assessment contribution** field, select the type of assessment contribution.
15. In the **Credit allocation method** field, select the method of credit allocation:

    - Direct
    - Proportional distribution

    This field is available only if you selected **Non cumulative** or **Both** in the **Assessment regimen** field.

16. In the **NFe and ECF options** field, select the reporting option for NFe transactions:

    - **Consolidated** – Consolidate all NFe transactions into one record on the C18X fiscal report.
    - **Detailed** – List all individual transactions on the fiscal report.

17. On the **Fiscal establishment** FastTab, enter the required SPED ECD information.
18. On the **Rule for taxation code** FastTab, select the taxation code and fiscal value to prevent records C100 and D100 from being generated.

## Special requirements for layout version 006 and later

### Record 0900

Record 0900 in the SPED EFD - Contributions text files is automatically generated to provide details about the revenue composition for the specified booking period. Generation of this record is mandatory when the original SPED EFD - Contributions file is transmitted after the regular delivery time (that is, after the tenth working day of the second month of the booking period).

The generated record is available in layout version 006 and later. Select this option when the SPED EFD - Contributions file is run.

### M410 (PIS) and M810 (COFINS)

Records M410 and M810 in the SPED EFD - Contributions text files are automatically generated for revenue transactions where a fiscal value is set to **2:Exempt** or **3:without debit/credit**.

The implementation of layout version 006 changes the way that field 02 (**NAT\_REC**) is determined. In this layout version, an additional configuration is used. In previous layout versions, specific fixed values were used.

## Prerequisites

Before you generate PIS and COFINS tax assessments and enable the generation of records M410 and M810 that have the correct revenue source determination, go to **Fiscal books** \> **Setup** \> **PIS and COFINS tables** \> **Revenue sources code**, and select the following parameters.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Revenue source type</td>
<td>Select the type of revenue source, according to the relationship that is included in the tables that provide details about the nature of revenue by tax situation (for example, tables 4.3.10 and 4.3.11). These tables are published by the tax authority.</td>
</tr>
<tr>
<td>Revenue source code</td>
<td>Enter the code for the revenue source.</td>
</tr>
<tr>
<td>Description</td>
<td>Enter a description of the revenue source code.</td>
</tr>
<tr>
<td>Valid from and to date</td>
<td>Enter the dates when this revenue source is applicable.</td>
</tr>
</tbody>
</table>

Go to **Fiscal books** \> **Setup** \> **PIS and COFINS tables** \> **Revenue source per item** to set up the revenue source determination.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Item code</td>
<td>Specify whether the revenue source determination applies to an item code, a group of items, or all items:
<ul>
<li><strong>Table</strong> – The source revenue applies to a single item code. If you select this option, select the item code in the <strong>Item relation</strong> field.</li>
<li><strong>Group</strong> – The source revenue applies to an item group. If you select this option, select the item group in the <strong>Item relation</strong> field.</li>
<li><strong>All</strong> – The source revenue applies to all items. If you select this option, leave the <strong>Item relation</strong> field blank.</li>
</ul>
</td>
</tr>
<tr>
<td>Item relation</td>
<td>If you selected <strong>Table</strong> in the <strong>Item code</strong> field, select the item code that is associated with the revenue source. If you selected <strong>Group</strong>, select an item group. If you selected <strong>All</strong>, leave this field blank.</td>
</tr>
</tbody>
</table>

## Generate a SPED EFD - Contributions text file

1. Go to **Fiscal books** \> **Common** \> **Booking period**.
2. Select the related booking period, and then select **Tax statements** \> **EFD Contributions** \> **Execute**.
3. In the **Type of situation** field, select the type of situation.
4. In the **File type** field, select **Original** or **Substitute**.
5. In the **Layout version** field, select the latest version that is available.
6. In the **Identification reason** field, select the related identification.
7. Set the **Late submission** option to **Yes** to generate record 0900.

> [!NOTE]
> To use batch processing, select **Batch**, and then specify the options for batch processing execution. You might use batch processing if the file should be generated later, or if it should be generated on a server instead of on your computer.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]