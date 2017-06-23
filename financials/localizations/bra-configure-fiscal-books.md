---
# required metadata

title: Configure fiscal books
description: Fiscal books can help you consolidate fiscal and statutory books into electronic files to fulfill requirements under SPED, Public Digital Bookkeeping System (Sistema Publico de Escrituração Digital).
author:  v-gonode
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer: twheeloc
# ms.search.scope: 
# ms.custom: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author:  v-gonode
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Enterprise edition, July 2017 update
---
[!include[banner](../includes/banner.md)]

Fiscal books can help you consolidate fiscal and statutory books into electronic files to fulfill requirements under SPED, Public Digital Bookkeeping System (Sistema Publico de Escrituração Digital). SPED provides detailed information about the fiscal documents that are related to services and goods, calculations of profits, logistical operations, and financial transactions. 

Set up requirements for SPED fiscal text files:
1.	On the **Tax statements parameters** page, select **SPED Fiscal**, click **Open**.
2.	For each fiscal establishment, select a profile presentation. 
> [!NOTE]
> For the Microsoft Dynamics for Finance and Operations, Enterprise edition, only the A profile presentation is supported.
3.	Select 1.06 or 1.07 or 1.08 or 1.09 as the version of the SPED fiscal text file format to generate. 
> [!NOTE]
> To generate the SPED fiscal text files for the following years:
 - For 2013, select 1.06
 - For 2014, select 1.07
 - For 2015, select 1.08
 - For 2016, select 1.09
4.	Select from the following activities to include in the SPED fiscal text file: 
 - **Industrial or equivalent** – Select this option to include information for activities related to industries, for example manufacturing of goods.
  - **Others** – Select this option for all other types of activities.

Set up adjustment codes for ICMS taxes on fiscal documents
1.	On the **Adjustment and information for fiscal documents** page, enter an adjustment code in the **Identification** field and a description of the adjustment code.
2.	Select a **State**, **Classification**, **Assessment type**, **Responsibility**, **Tax payment type** and **Source of the tax**
The **Adjustment code** field is filled in automatically, based on the entries in other fields in this page.
3.	Enter the occurrence code for the GIA fiscal obligation.
4.	Enter the first and last dates that the adjustment codes are applicable.
5.	On the **Payment** FastTab, select the **Other debit** check box if you want to create an additional tax adjustment payment that is not included in the periodic payment.
6.	On the **Posting** FastTab, in the **Company accounts** field, select the legal entity where the tax adjustment transactions will be posted.
7.	In the ***Sales tax code** field, select the tax code that will be used to select the accounts receivable or accounts payable account. The account that is selected depends on whether the tax adjustment is a debit or credit. 
8.	Select the main account that will be used to post the revenue or expense part of the adjustment transaction.

Set up adjustment codes for ICMS tax
1.	On the **ICMS and ICMS-ST adjustment codes table** page, enter an adjustment code in the **Identification** field and a description of the adjustment code.
2.	Select a state.
3.	Select a tax type from the following options: 
- ICMS – The adjustment code is used for federal ICMS tax
- ICMS-ST – The adjustment code is used for federal ICMS-ST tax
- ICMS-DIFF – The adjustment code is used for federal ICMS-DIFF tax.
4.	Select a classification and enter an occurrence code.
The **Adjustment code** field is filled in automatically, based on the entries in the other fields in this page.
5.	Enter the first and last dates that the adjustment codes are applicable for.
6.	In the **GIA** field group, select an occurrence code.
7.	On the **Payment** FastTab, select the **Other debit** option if you want to create an additional tax adjustment payment that is not included in the periodic payment.
8.	On the **Posting** FastTab, in the **Company accounts** field, select the legal entity where the tax adjustment transactions will be posted.
9.	In the **Sales tax code** field, select the tax code that will be used to select the accounts receivable or accounts payable account. The account that is selected depends on whether the tax adjustment is a debit or credit. 
10.	Select the main account that will be used to post the revenue or expense part of the adjustment transaction.

Set up adjustment codes for IPI taxes
1.	On the **IPI adjustment codes table** page, enter an adjustment code. The first character must be 0 for a credit adjustment or 1 for a debit adjustment.
2.	Enter a description.
3.	If the adjustment code will be used to report the reversal of a previously reported IPI tax amount, select the **Reversal adjustment code** option.
4.	Enter the first and last dates that the adjustment code is applicable.

You can set up observation codes to adjust ICMS or ICMS-ST amounts on the **Oberservation codes** page.


Set up fiscal books parameters per state
1.	On the **Fiscal books parameters per state** page, select a state.
2.	If the ICMS tax amounts can be adjusted on fiscal documents, select the **By fiscal document** option, and then select the default adjustment code and observation code.
3.	If the ICMS tax amounts cannot be adjusted on fiscal documents, clear the **By fiscal document** option, and then select the default adjustment code.
4.	To automatically calculate an ICMS credit installment when an outgoing transaction is created, select the **Calculate installment for outgoing transactions** option.

Set up a fiscal organization
1.	On the **Fiscal organization** page. in the **Root fiscal establishment** field, select a fiscal organization that is used for SPED contributions.
2.	On the **Fiscal establishment** FastTab, fiscal establishments are automatically added to the list if they have the same nine digits of the CNPJ/CPF number as the fiscal organization that is selected in the **Root fiscal establishment** field. To remove a fiscal establishment that has been added to the list, click **Remove**. 
3.	On the **Company social contract** FastTab, enter the archive date of the company’s constitution contract and the company’s conversion.
4.	On the **SCP** FastTab, select the type of SCP company from the following options: 
 - Not participant as SCP partner
 - Participant as SCP partner
 - SCP
5.	On the **Related SCP** FastTab, click **Add** to enter the name and code of SCP related company. 
> [!Note]
> This information is enabled if you selected Participant as SCP partner.
6.	On the **Legal representative** FastTab, click **Add** to enter the name of the company’s legal representative.
7.	Enter the CPF registration number and the role of the legal representative. 
8.	On the **Independent auditors** FastTab, click **Add** to enter the name of the auditor and the registration number.
9.	To remove an independent auditor that has been added to the list, click **Remove**. 
> [!NOTE] 
> This option is available when the **Large company** option has been selected.

You can set up a fixed asset group on the Fixed asset groups page.

Set up requirements for SPED EFD - Contributions
1. On the **Tax statements parameters** page, select **EFD - Contributions**, click **Open**.
2. Enter the required SPED EFD - Contributions information.
3.	In the **Type of activity** field, select the activity type. 
4.	In the **Version** field, select the version of the SPED EFD - Contributions layout.
5.	Select the type of legal entity.
6.	In the **Assessment regimen** field, select the assessment schema that is used for SPED EFD - Contributions from the following assessments: 
 - **Non cumulative – Calculate** - based on billing or debits and purchases and deductions or credits
  - **Cumulative – Calculate** - based on billings that don’t have any deductions or credits
  - **Both** – Calculate assessments based on both the Non cumulative and Cumulative regimens
7.	In the **Booking and assessment criteria** field, select the criteria to use to book the tax credit. 
> [!NOTE]
> For Dynamics 365 for Operations, only the Detailed option is supported.
8.	Select the type of assessment contribution. 
> [!NOTE]
> For Dynamics 365 for Operations, only the Detailed option is supported.
9.	In the **Credit allocation method** field, select the method of credit allocation: Direct or Proportional distribution.
This field is available if **Non cumulative** or **Both** are selected in the **Assessment regimen** field.
10.	In the **NFe and ECF options** field, select the NFe transaction reporting option from the following options: 
- **Consolidated** – Consolidate all NFe transactions into one record on the C18X fiscal report
 - **Detailed** – List all individual transactions on the fiscal report
11.	On the **Fiscal establishment** FastTab, enter the required SPED ECD information.

Set up requirements for SPED ECD tax statement
1.	On the **Tax statements parameters** page, click **SPED ECD**. On the **Setup parameters** FastTab, click **Open**.
2.	Select the company to generate the SPED ECD text file for.
3.	Select the financial dimension set that the format of the SPED ECD text file will be based on. The financial dimension set should include the main account and the cost center dimensions.
4.	Select the file location where the SPED ECD text file will be generated.
5.	The Booking type is assigned automatically depending on the type of fiscal organization: G – This booking is used to detail all of the ledger journal transactions; S – This booking is used for the SCP company.
6.	Select the type of company situation from the following options, or leave the field blank to represent the regular situation.
7.	In the **Opening fiscal period** field, select from the following options: Regular; Opening; Split, Merge or Acquisition; Mandatory.
8.	Select the version of the SPED ECD text file format to generate: 
 - For Dynamics 365 for Operations, Version 2.00 is supported until fiscal year 2013
  - For Dynamics 365 for Operations, Version 3.00 is supported from fiscal year 2014
  - For Dynamics 365 for Operations, Version 4.00 is supported from fiscal year 2015
  - For Dynamics 365 for Operations, Version 5.00 is supported from fiscal year 2016.
9.	In the **Auditor registration number** field, enter the number of the company’s auditor.
10.	Enter the auditor’s name.
11.	Select the **Large company** option if the company is a large company. 
> [!NOTE] Steps 9, 10 and 11 are not available when Version 3.0 is selected. This information has been changed and included in the configuration of fiscal organization.

You can set up accountant information for tax booking on the **Accountant details** page.




