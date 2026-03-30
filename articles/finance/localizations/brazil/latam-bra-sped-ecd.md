---
title: SPED ECD
description: Learn how to set up and generate SPED ECD text files, including an outline on setting up requirements for the SPED ECD tax statement.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/04/2026
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2017-12-31
---

# SPED ECD

[!include [banner](../../includes/banner.md)]

## Set up parameters for SPED ECD text files

This section explains how to specify how to save Sistema Publico de Escrituração Digital (SPED) fiscal text files before you submit them to the federal tax authorities.

The SPED fiscal text files contain information about general ledger transactions, profit and loss information, and balance sheet information. The federal tax authorities use the SPED Escrituração Contábil Digital (ECD) system to verify a company's taxable profits.

### Set up requirements for the SPED ECD tax statement

To set up requirements for SPED ECD fiscal text files, follow these steps:

1. Select **Fiscal books** > **Setup** > **Tax statements parameters**.
1. Select **SPED ECD**, and then on the **Setup parameters** FastTab, select **Open**.
1. Select the company to generate the SPED ECD text file for.
1. Select the financial dimension set that the format of the SPED ECD text file should be based on. The financial dimension set should include the main account and the cost center dimensions.
1. Select the location where the SPED ECD text file should be generated.

    The booking type is assigned automatically, based on the type of fiscal organization:

    - **G** – The booking is used for all the ledger journal transactions.
    - **S** – The booking is used for the SCP company.

1. Select the type of company situation. The following options are available. Alternatively, leave the field blank to represent the regular situation.

    - Division
    - Merger
    - Incorporation
    - Closing-down
    - Transformation

1. In the **Opening fiscal period** field, select one of the following options:

    - Regular
    - Opening
    - Split, Merge or Acquisition
    - Mandatory

1. Select the version of the SPED ECD text file format to generate.
1. In the **Auditor registration number** field, enter the number of the company's auditor.
1. Enter the auditor's name.
1. Set the **Large company** option to **Yes** if the company is a large company.

## Generate and validate the SPED ECD statement

This section explains how to generate and validate the text file for the digital accounting bookkeeping (SPED ECD) statement.

For the SPED ECD statement, organizations must calculate and report their taxable profits based on the following types of accounting records:

- Journal registers and supporting records
- General ledger and subledgers
- Daily trial balances and balance sheets

### Generate and validate a SPED ECD text file

To generate and validate the text file for the SPED ECD statement, follow these steps:

1. Select **Fiscal books** > **Common** > **SPED ECD** > **Generate SPED ECD**.
1. Select the fiscal organization to generate the SPED ECD file for.
1. In the **From date** and **To date** fields, select the start and end dates of the ledger transactions to report on.
1. Set the **Include accounting statements** option to **Yes** to generate the Block J text file in addition to the SPED ECD file.
1. Select the period to calculate financial statement balances for.
1. Enter the path where the files should be saved.
1. In the **Book number** field, enter the accounting book number.

    The **Booking type** field is automatically set to **G** (Livro Diario completo sem escrituracao auxiliary).

1. Select the type of company situation. The following options are available. Alternatively, leave the field blank to represent the regular situation.

    - Division
    - Merger
    - Incorporation
    - Closing-down
    - Transformation

1. In the **Opening fiscal period** field, select one of the following options:

    - Regular
    - Opening
    - Split, Merge or Acquisition
    - Mandatory

1. In the **Layout version** field, select the layout of the SPED ECD file.
1. In the **File type** field, select the type of file to generate:

    - Original
    - Substitute with NIRE
    - Substitute without NIRE
    - Substitute with NIRE changes

    Enter the Número de Identificação no Registro de Empresas (NIRE) on the **Tax registration** FastTab of the **Fiscal establishment** page.

1. Select **OK** to generate the SPED ECD file.
1. Select **Fiscal books** > **Common** > **SPED ECD** > **Validate SPED ECD**.
1. Select **OK** to validate the SPED ECD file.

## Additional resources

[Generate the Sintegra tax statement](/dynamicsax-2012/appuser-itpro/bra-generate-the-sintegra-tax-statement)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
