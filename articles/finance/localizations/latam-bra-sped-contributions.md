---
# required metadata

title: Set SPED EFD Contributions 
description: This topic explains how to set up parameters and generate for SPED EFD Contributions for Brazil. 
author: ShylaThompson
manager: AnnBe
ms.date: 08/27/2018
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
# ms.custom: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

SPED EFD Contributions is an specific statement generated from Fiscal books module that gathers information about Social Contribution tax on Gross Revenue for Social Integration Program (PIS) and  Social Security Financing program (COFINS).


# Set up requirements for SPED EFD - Contributions

To set up requirements for SPED EFD – Contributions text files, follow these steps.

1.  Select **Fiscal books** \> **Setup** \> **Tax statements parameters**.
2.  Select **EFD - Contributions**, and then, on the **Setup parameters** FastTab, select **Open**.

    The **EFD – Contributions parameters** page appears, where you can enter the required information for SPED EFD - Contributions text files.

3.  In the **Type of activity** field, select the activity type:

    - Industrial or equivalent
    - Services
    - Retail
    - Financial activity
    - Real estate activity
    - Others
4.  Set the **Large company** option to **Yes** to identify the size of company. This option is used in SPED REINF statements.
5.  In the **Layout version** field, select the version of the SPED EFD - 
6.  In the **Legal entity type** field, select the type of legal entity.
7.  In the **Company type** field, select the type of company:

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

18. On the **Rule for taxation code** FastTab, select  the taxation code and fiscal value to avoid the generation of records C100 and D100. 

# Special requirements for version 006 and later

## Record 0900

Record 0900 in SPED EFD - Contributions text file is automatically generated to detail the composition of the revenues for the specified booking period. The generation of this record is mandatory whenever the original SPED EFD-Contributions file is transmitted
after the regular delivery time (after the 10th working day of the 2nd month of booking period)

The generation of this record is available from layout version 006 and select this option during the execution of SPED EFD-Contributions file.


## M410 (PIS) and M810 (Cofins)
Record **M410** and **M810** in SPED EFD - Contributions text files is automatically generated for those revenue transactions with fiscal value set to 2:Exempt or 3:without debit/credit. 

The implementation of layout 006 introduces changes in the determination of field 02 (NAT_REC) by introducing an additional configuration instead of  using specific fixed values as defined in previous layout versions.

### Prerequisites
Before to generate PIS and COFINS tax assessment and  enable the generation of records M410 and M810 with the correct revenue source determination , go to **Fiscal books > Setup > PIS and COFINS tables > Revenue sources code**, and select the following parameters:

<table>
  <tr>
    <th>Field</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Revenue source type</td>
    <td>Select the type of revenue source according to the relationship included in the tables for detailing the nature of revenue by tax situation, for example tables 4.3.10, 4.3.11, etc. These tables are published by the tax authority.</td>
  </tr>
  <tr>
    <td>Revenue source code</td>
    <td>Enter the revenue source code</td>
  </tr>
  <tr>
    <td>Description</td>
    <td>Enter a description of revenue source code</td>
  </tr>
  <tr>
    <td>Valid from and to date</td>
    <td>Enter the valid dates where this revenue source is applicable for.</td>
  </tr>
</table>

Go to **Fiscal books > Setup > PIS and COFINS tables > Revenue source per item** to specify the setup of revenue source determination.

<table>
  <tr>
    <th>Field</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Item code</td>
    <td>Specify whether the revenue source determination applies to a item code, a group of items, or all items:</td>
  </tr>
  <tr>
    <td></td>
    <td>Table – The source revenue applies to a single item code. Select the item code in the Item relation field.</td>
  </tr>
  <tr>
    <td></td>
    <td>Group – The source revenue applies to an item group. Select the item group in the Item relation field.</td>
  </tr>
  <tr>
    <td></td>
    <td>All – The source revenue applies to all items. Leave the Item relation field blank.</td>
  </tr>
  <tr>
    <td>Item relation</td>
    <td>If Table is selected in the item code field, select the item code that is associated with the revenue source. If Group is selected, select a item group. If All is selected, leave this field blank.</td>
  </tr>
</table>


## Generate an EFD contributions text file

1.	Go to **Fiscal books > Common > Booking period, select the related booking period and then select the **Tax statements > EFD Contributions > Execute**
2.	In the **Type of situation** field, select the type of situation.
4.	In the **File type** field, select either **Original** or **Substitute** .
6.	In the **Layout version** field, select that latest version available. 
7.	In the **Identification reason** field, select the related indentification
8.  Set Late submition as **Yes** to generate the record 0900. 

Note: Select the **Batch** action and specify the options for batch processing execution. You might use batch processing if the file should be generated later or on a server instead of on your computer.

