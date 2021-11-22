---
# required metadata

title: Configure fiscal books
description: This topic explains how to configure fiscal books. Fiscal books help you consolidate fiscal and statutory books into electronic files, so that you can fulfill the requirements under SPED.
author:  v-gonode
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  FBTaxStatement_BR
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.custom: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author:  kfend
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update
---

# Configure fiscal books

[!include [banner](../includes/banner.md)]

Fiscal books can help you create the fiscal establishment's tax assessment, tax payment, and tax reporting through Sistema Publico de Escrituração Digital (SPED), the Public Digital Bookkeeping System. The SPED files provide detailed information about the tax assessments and tax payments on transactions that have goods, fixed assets, and services, and also transactions in the general ledger. 

## Set up requirements for SPED fiscal text files

> [!NOTE]
> Before you configure your SPED fiscal text file, you must import the **SPED model** data model and the **EFD ICMS IPI - nnn (BR)** file configuration from the **Electronic reporting** module. In Electronic reporting, you can download both the model and the file configuration from the repository that is published by Microsoft. Alternatively, you can get an updated version from Microsoft Dynamics Lifecycle Services (LCS).

1. On the **Tax statements parameters** page, click **New from electronic reporting**.
2. Enter a name for the tax statement.
3. Select **SPED model** as the name of the model mapping and **EFD ICMS IPI - nnn (BR)** as the format mapping.

## Set up requirements for GIA text files

> [!NOTE]
> Before you configure your Guia de Informação e Apuração (GIA) text file, you must import the **SPED model** data model and the **GIA** file configuration from Electronic reporting. In Electronic reporting, you can download both the model and the file configuration from the repository that is published by Microsoft. Alternatively, you can get an updated version from LCS.

1. On the **Tax statements parameters** page, click **New from electronic reporting**.
2. Enter a name for the tax statement.
3. Select **SPED model** as the name of the model mapping and **GIA** as the format mapping.

## Set up requirements for GIA-ST text files

> [!NOTE]
> Before you configure your GIA-ST text file, you must import the **SPED model** data model and the **GIA-ST** file configuration from Electronic reporting. In Electronic reporting, you can download both the model and the file configuration from the repository that is published by Microsoft. Alternatively, you can get an updated version from LCS.

1. On the **Tax statements parameters** page, click **New from electronic reporting**.
2. Enter a name for the tax statement.
3. Select **SPED model** as the name of the model mapping and **GIA-ST** as the format mapping.

## Set up requirements for SPED contributions text files

> [!NOTE]
> Before you configure your SPED contributions text file, you must import the **SPED model** data model and the **EFD Contributions - nnn (BR)** file configuration from Electronic reporting. In Electronic reporting, you can download both the model and the file configuration from the repository that is published by Microsoft. Alternatively, you can get an updated version from LCS.

1. On the **Tax statements parameters** page, click **New from electronic reporting**.
2. Enter a name for the tax statement.
3. Select **SPED model** as the name of the model mapping and **EFD Contributions - nnn (BR)** as the format mapping.

## Set up adjustment codes for ICMS taxes on fiscal documents

1. On the **Adjustment and information for fiscal documents** page, in the **Identification** field, enter an adjustment code. Then enter a description of the adjustment code.
2. Select appropriate values in the **State**, **Classification**, **Assessment type**, **Responsibility**, **Tax payment type** and **Source of the tax** fields.

    The **Adjustment code** field is filled automatically, based on the values of the other fields on the page.

3. Enter the occurrence code for the GIA fiscal obligation.
4. Enter the first and last dates that the adjustment codes apply.
5. On the **Payment** FastTab, select the **Other debit** check box to create an additional tax adjustment payment that isn't included in the periodic payment.
6. On the **Posting** FastTab, in the **Company accounts** field, select the legal entity where the tax adjustment transactions should be posted.
7. In the **Sales tax code** field, select the tax code that should be used to select the accounts receivable or accounts payable account. The account that is selected depends on whether the tax adjustment is a debit or a credit. 
8. Select the main account that should be used to post the revenue or expense part of the adjustment transaction.

## Set up adjustment codes for ICMS tax

1. On the **ICMS and ICMS-ST adjustment codes table** page, in the **Identification** field, enter an adjustment code. Then enter a description of the adjustment code.
2. Select a state.
3. Select the tax type: 

    - **ICMS** – The adjustment code is used for federal Imposto sobre Circulação de Mercadorias e Serviços (ICMS) tax.
    - **ICMS-ST** – The adjustment code is used for federal ICMS-ST tax.
    - **ICMS-DIFF** – The adjustment code is used for federal ICMS-DIFF tax.

4. Select a classification, and enter an occurrence code.

    The **Adjustment code** field is filled automatically, based on the values of the other fields on the page.

5. Enter the first and last dates that the adjustment codes apply.
6. In the **GIA** field group, select an occurrence code.
7. On the **Payment** FastTab, select the **Other debit** option to create an additional tax adjustment payment that isn't included in the periodic payment.
8. On the **Posting** FastTab, in the **Company accounts** field, select the legal entity where the tax adjustment transactions should be posted.
9. In the **Sales tax code** field, select the tax code that should be used to select the accounts receivable or accounts payable account. The account that is selected depends on whether the tax adjustment is a debit or a credit. 
10.	Select the main account that should be used to post the revenue or expense part of the adjustment transaction.

## Set up adjustment codes for IPI taxes

1. On the **IPI adjustment codes table** page, enter an adjustment code. The first character must be **0** (zero) for a credit adjustment or **1** for a debit adjustment.
2. Enter a description.
3. If the adjustment code will be used to report the reversal of an Imposto sobre Produtos Industrializados (IPI) tax amount that was previously reported, select the **Reversal adjustment code** option.
4. Enter the first and last dates that the adjustment code applies.

On the **Observation codes** page, you can set up observation codes to adjust ICMS or ICMS-ST amounts.

## Set up fiscal books parameters per state

1. On the **Fiscal books parameters per state** page, select a state.
2. If the ICMS tax amounts can be adjusted on fiscal documents, select the **By fiscal document** option, and then select the default adjustment code and observation code.

    If the ICMS tax amounts can't be adjusted on fiscal documents, clear the **By fiscal document** option, and then select the default adjustment code.

3. To automatically calculate an ICMS credit installment when an outgoing transaction is created, select the **Calculate installment for outgoing transactions** option.

## Set up a fiscal organization

1. On the **Fiscal organization** page, in the **Root fiscal establishment** field, select a fiscal organization that is used for SPED contributions.
2. On the **Fiscal establishment** FastTab, fiscal establishments are automatically added to the list if they have the same nine-digit Cadastro Nacional de Pessoas Jurídicas (CNPJ)/Cadastro de Pessoas Físicas (CPF) number as the fiscal organization that you selected in the **Root fiscal establishment** field. To remove a fiscal establishment that has been added to the list, click **Remove**. 
3. On the **Company social contract** FastTab, enter the archive date of the company’s constitution contract and the company’s conversion.
4. On the **SCP** FastTab, select the type of Sociedade em Conta de Participação (SCP) company: 

    - Not participant as SCP partner
    - Participant as SCP partner
    - SCP

5. On the **Related SCP** FastTab, click **Add** to enter the name and code of an SCP-related company. 

    > [!NOTE]
    > This information is available if you selected **Participant as SCP partner** as they type of SCP company.

6. On the **Legal representative** FastTab, click **Add** to enter the name of the company’s legal representative.
7. Enter the CPF registration number and the role of the legal representative. 
8. On the **Independent auditors** FastTab, click **Add** to enter the name of the auditor and the registration number.
9. To remove an independent auditor that has been added to the list, click **Remove**. 

    > [!NOTE] 
    > This option is available when the **Large company** option is selected.

On the **Fixed asset groups** page, you can set up a fixed asset group.

## Set up requirements for the SPED ECD tax statement

1. On the **Tax statements parameters** page, click **SPED ECD**. Then, on the **Setup parameters** FastTab, click **Open**.
2. Select the company to generate the SPED Escrituração Contábil Digital (ECD) text file for.
3. Select the financial dimension set that the format of the SPED ECD text file should be based on. The financial dimension set should include the main account and the cost center dimensions.
4. Select the file location where the SPED ECD text file should be generated.

    The booking type is assigned automatically, based on the type of fiscal organization:
    
    - **G** – The booking is used for all the ledger journal transactions.
    - **S** – The booking is used for the SCP company.

5. Select the type of company situation, or leave the field blank if it should represent the regular situation.
6. In the **Opening fiscal period** field, select one of the following options: **Regular**, **Opening**, **Split, Merge or Acquisition**, or **Mandatory**.
7. Select the file layout version of the SPED ECD text file format to generate. The following file layout versions for ECD are currently supported:

    - Version 2.00 for SPED ECD until fiscal year 2013
    - Version 3.00 for SPED ECD until fiscal year 2014
    - Version 4.00 for SPED ECD until fiscal year 2015
    - Version 5.00 for SPED ECD until fiscal year 2016

8. In the **Auditor registration number** field, enter the number of the company’s auditor.
9. Enter the auditor’s name.
10.	If the company is a large company, select the **Large company** option. 

> [!NOTE]
> The fields for steps 8, 9, and 10 aren't available when version 3.0 is selected. This information has been changed and is included in the configuration of the fiscal organization.

On the **Accountant details** page, you can set up accountant information for tax booking.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]