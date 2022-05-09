---
# required metadata

title: SPED ECD
description: This topic explains how to set up and generate SPED ECD text files.
author: ShylaThompson
ms.date: 08/27/2018
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

# SPED ECD

[!include [banner](../includes/banner.md)]

## Set up parameters for SPED ECD text files

This section explains how to specify how Sistema Publico de Escrituração Digital (SPED) fiscal text files should be saved before you submit them to the federal tax authorities.

The SPED fiscal text files contain information about general ledger transactions, profit and loss information, and balance sheet information. The federal tax authorities use the SPED Escrituração Contábil Digital (ECD) system to verify taxable a company's profits. 

### Set up requirements for the SPED ECD tax statement

To set up requirements for SPED ECD fiscal text files, follow these steps.

1.  Select **Fiscal books** \> **Setup** \> **Tax statements parameters**.
2.  Select **SPED ECD** on the left, and then, on the **Setup parameters** FastTab, select **Open**.
3.  Select the company to generate the SPED ECD text file for.
4.  Select the financial dimension set that the format of the SPED ECD text file should be based on. The financial dimension set should include the main account and the cost center dimensions.
5.  Select the location where the SPED ECD text file should be generated.

    The booking type is assigned automatically, based on the type of fiscal organization:

    -  **G** – The booking is used for all the ledger journal transactions.
    -  **S** – The booking is used for the SCP company.

6.  Select the type of company situation. The following options are available. Alternatively, leave the field blank to represent the regular situation.

    -  Division
    -  Merger
    -  Incorporation
    -  Closing-down
    -  Transformation

7.  In the **Opening fiscal period** field, select one of the following options:

    -  Regular
    -  Opening
    -  Split, Merge or Acquisition
    -  Mandatory

8.  Select the version of the SPED ECD text file format to generate.
9.  In the **Auditor registration number** field, enter the number of the company's auditor.
10. Enter the auditor's name.
11. Set the **Large company** option to **Yes** if the company is a large company.

## Generate and validate the SPED ECD statement 

This section explains how to generate and validate the text file for the digital accounting bookkeeping (SPED ECD) statement.

For the SPED ECD statement, organizations must calculate and report on their taxable profits, based on the following types of accounting records:

- Journal registers and supporting records
- General ledger and subledgers
- Daily trial balances and balance sheets

### Generate and validate a SPED ECD text file

To generate and validate the text file for the SPED ECD statement, follow these steps.

1.  Select **Fiscal books** \> **Common** \> **SPED ECD** \> **Generate SPED ECD**.
2.  Select the fiscal organization to generate the SPED ECD file for.
3.  In the **From date** and **To date** fields, select the start and end dates of the ledger transactions to report on.
4.  Set the **Include accounting statements** option to **Yes** to generate the Block J text file in addition to the SPED ECD file.
5.  Select the period to calculate financial statement balances for.
6.  Enter the path where the files should be saved.
7.  In the **Book number** field, enter the accounting book number.

    The **Booking type** field is automatically set to **G** (Livro Diario completo sem escrituracao auxiliary).

8.  Select the type of company situation. The following options are available. Alternatively, leave the field blank to represent the regular situation.

    -  Division
    -  Merger
    -  Incorporation
    -  Closing-down
    -  Transformation

9.  In the **Opening fiscal period** field, select one of the following options:

    -  Regular
    -  Opening
    -  Split, Merge or Acquisition
    -  Mandatory

10. In the **Layout version** field, select the layout of the SPED ECD file.
11. In the **File type** field, select the type of file to generate:

    -  Original
    -  Substitute with NIRE
    -  Substitute without NIRE
    -  Substitute with NIRE changes

    The Número de Identificação no Registro de Empresas (NIRE) is entered on the **Tax registration** FastTab of the **Fiscal establishment** page.

12. Select **OK** to generate the SPED ECD file.
13. Select **Fiscal books** \> **Common** \> **SPED ECD** \> **Validate SPED ECD**.
14. Select **OK** to validate the SPED ECD file.

## Additional resources

[Generate the Sintegra tax statement](/dynamicsax-2012/appuser-itpro/bra-generate-the-sintegra-tax-statement)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
