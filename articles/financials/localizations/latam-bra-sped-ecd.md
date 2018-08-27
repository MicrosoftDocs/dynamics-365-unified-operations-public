---
# required metadata

title: SPED ECD
description: This topic provides information on how to set up parameters for and generate SPED ECD text files.
author: ShylaThompson
manager: AnnBe
ms.date: 8/27/2018
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
# ms.custom: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Set up parameters for SPED ECD text files

This topic describes how to specify how Sistema Publico de Escrituração Digital (SPED) fiscal text files will be saved before you submit them to the federal tax authorities.

The SPED fiscal text files contain information about general ledger transactions, profit and loss information, and balance sheet information. The SPED ECD system is used by federal tax authorities to verify taxable profits of a company. 

### Set up requirements for SPED ECD tax statement

To set up requirements for SPED ECD fiscal text files, follow these steps:

1.  Click **Fiscal books** \> **Setup** \> **Tax statements parameters**. Click **SPED ECD**. On the **Setup parameters** FastTab, click **Open**.

2.  Select the company to generate the SPED ECD text file for.

3.  Select the financial dimension set that the format of the SPED ECD text file will be based on. The financial dimension set should include the main account and the cost center dimensions.

4.  Select the file location where the SPED ECD text file will be generated.

5.  The Booking type is assigned automatically depending on the type of fiscal organization. 
    
      - G – This booking is used to detail all of the ledger journal transactions.
    
      - S – This booking is used for the SCP company.

6.  Select the type of company situation from the following options, or leave the field blank to represent the regular situation:
    
      - **Division**
    
      - **Merger**
    
      - **Incorporation**
    
      - **Closing-down**
    
      - **Transformation**

7.  In the **Opening fiscal period** field, select from the following options:
    
      - **Regular**
    
      - **Opening**
    
      - **Split, Merge or Acquisition**
    
      - **Mandatory**

8.  Select the version of the SPED ECD text file format to generate.
    
9.  In the **Auditor registration number** field, enter the number of the company’s auditor.

10. Enter the auditor’s name.

11. Select the **Large company** check box if the company is a large company.
    


## Generate and validate the SPED ECD statement 

This topic describes how to generate and validate the text file for the digital accounting bookkeeping (SPED ECD) statement.

The SPED ECD statement requires organizations to calculate and report the taxable profits based on the following types of accounting records:

  - Journal registers and supporting records

  - General ledger and subledgers

  - Daily trial balances and balance sheets

### Generate and validate a SPED ECD text file

To generate and validate the text file for the SPED ECD statement, follow these steps:

1.  Click **Fiscal books** \> **Common** \> **SPED ECD** \> **Generate SPED ECD**.

2.  Select the fiscal organization to generate the SPED ECD file for.

3.  In the **From date** and **To date** fields, select the starting and ending dates of the ledger transactions to report on.

4.  Select the **Include accounting statements** check box to generate the Block J text file in addition to the SPED ECD file.

5.  Select the time period to calculate financial statement balances for.

6.  Enter the path where the files will be saved.

7.  In the **Booking number** field, enter the accounting book number.
    
    The **Booking type** field automatically displays the value of G (Livro Diario completo sem escrituracao auxiliary).

8.  Select the type of company situation from the following options, or leave the field blank to represent the regular situation:
    
      - **Division**
    
      - **Merger**
    
      - **Incorporation**
    
      - **Closing-down**
    
      - **Transformation**

9.  In the **Opening fiscal period** field, select from the following options:
    
      - **Regular**
    
      - **Opening**
    
      - **Split, Merge or Acquisition**
    
      - **Mandatory**

10. In the **Layout version** field, select the layout of the SPED ECD file.

11. In the **File type** field, select the type of file to generate from the following options:
    
      - **Original**
    
      - **Substitute with NIRE**
    
      - **Substitute without NIRE**
    
      - **Substitute with NIRE changes**
    
    Número de Identificação no Registro de Empresas (NIRE) is entered in the **Fiscal establishment** form on the **Tax registration** FastTab.

12. Click **OK** to generate the SPED ECD file.

13. Click **Fiscal books** \> **Common** \> **SPED ECD** \> **Validate SPED ECD**.

14. Click **OK** to validate the SPED ECD file.




## Additional resources

- [Generate the Sintegra tax statement](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/bra-parameters-tax/articles/financials/localizations/latam-bra-set-up-parameters-for-tax-statements.md)

