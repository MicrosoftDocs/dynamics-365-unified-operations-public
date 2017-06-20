---
# required metadata

title: [Topic name]
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: [author's GitHub alias]
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: [Pick one: Application User/Developer/IT Pro]
# ms.devlang: 
# ms.reviewer: [Content Strategist microsoft alias]
# ms.search.scope: [Which Operations client to show this topic as help for, to be set by content strategist, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: [author's Microsoft alias]
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

Set up requirements for SPED fiscal text files:
1.	Click Fiscal books > Setup > Tax statements parameters. Select SPED Fiscal, on the Setup parameters FastTab, click Open.
2.	In the SPED fiscal parameters form, for each fiscal establishment, select a profile presentation. For the current release, only the A profile presentation is supported.
3.	Select 1.06 or 1.07 or 1.08 or 1.09 as the version of the SPED fiscal text file format to generate. Note: To generate the SPED fiscal text file for the year 2013, select 1.06. To generate the SPED fiscal text file for the year 2014, select 1.07. To generate the SPED fiscal text file for the year 2015, select 1.08. To generate the SPED fiscal text file for the year 2016, select 1.09.
4.	Select the type of activity to include in the SPED fiscal text file. The following options are available: Industrial or equivalent – Select this option to include information for activities related to industries, for example manufacturing of goods; or Others – Select this option for all other types of activities.

Set up adjustment codes for ICMS taxes on fiscal documents
1.	Click Fiscal books > Setup > Tax adjustment codes > Adjustment and information for fiscal documents.
2.	In the Adjustment and information for fiscal documents form, enter an adjustment code in the Identification field and a description of the adjustment code.
3.	Select a state.
4.	Select a classification from the following options: 0 – Credit; 1 – Other credits; 2 – Debit reversal; 3 – Debits; 4 – Other debits; 5 – Credit reversal; 6 - Deduction; 7 – Special debits; 9 – Information.
5.	Select an assessment type from the following options: Own operation; Operation ST; Other assessments; Assessment 1 block 1900; Assessment 2 block 1900; Assessment 3 block 1900; Informative.
6.	Select a responsibility from the following options: Own; Optional; Informative.
7.	Select a tax payment type from the following options: 0: Collection; 1: Spontaneous collecting; 2: Collection by infraction; 3: Fiscal incentive; 9: Informative.
8.	Select source of the tax from the following options: 0: Goods; 1: Transportation; 2: Communication; 3: Electric power; 9: Informative.
The Adjustment code field is filled in automatically, based on the entries in other fields in this form.
9.	Enter the occurrence code for the GIA fiscal obligation.
10.	In the Valid from and Valid to fields, enter the first and last dates that the adjustment codes are applicable.
11.	On the Payment FastTab, select the Other debit check box if you want to create an additional tax adjustment payment that is not included in the periodic payment.
12.	On the Posting FastTab, in the Company accounts field, select the legal entity where the tax adjustment transactions will be posted.
13.	In the Sales tax code field, select the tax code that will be used to select the accounts receivable or accounts payable account. The account that is selected depends on whether the tax adjustment is a debit or credit. 
14.	Select the main account that will be used to post the revenue or expense part of the adjustment transaction.
15.	To create another adjustment code, click New, and then repeat steps 2 through 14.

Set up adjustment codes for ICMS tax
1.	Click Fiscal books > Setup > Tax adjustment codes > ICMS, ICMS-ST and ICMS-DIFF adjustment codes table.
2.	In the ICMS and ICMS-ST adjustment codes table form, enter an adjustment code in the Identification field and a description of the adjustment code.
3.	Select a state.
4.	Select a tax type from the following options: ICMS – The adjustment code is used for federal ICMS tax; ICMS-ST – The adjustment code is used for federal ICMS-ST tax; ICMS-DIFF – The adjustment code is used for federal ICMS-DIFF tax.
5.	Select a classification from the following options: 0: Other debits; 1: Credits reversal; 2: Other credits; 3: Debits reversal; 4: Deductions of tax balance; 5: Specials debits; 9: Information.
6.	Enter an occurrence code.
The Adjustment code field is filled in automatically, based on the entries in the other fields in this form.
7.	In the Valid from and Valid to fields, enter the first and last dates that the adjustment codes are applicable for.
8.	In the GIA field group, select an occurrence code.
9.	On the Payment FastTab, select the Other debit check box if you want to create an additional tax adjustment payment that is not included in the periodic payment.
10.	On the Posting FastTab, in the Company accounts field, select the legal entity where the tax adjustment transactions will be posted.
11.	In the Sales tax code field, select the tax code that will be used to select the accounts receivable or accounts payable account. The account that is selected depends on whether the tax adjustment is a debit or credit. 
12.	Select the main account that will be used to post the revenue or expense part of the adjustment transaction.
13.	To create another adjustment code, click New, and then repeat steps 2 through 12.

Set up adjustment codes for IPI taxes
1.	Click Fiscal books > Setup > Setup > Tax adjustment codes > IPI adjustment codes table.
2.	In the IPI adjustment codes table form, enter an adjustment code. The first character must be 0 for a credit adjustment or 1 for a debit adjustment.
3.	Enter a description.
4.	If the adjustment code will be used to report the reversal of a previously reported IPI tax amount, select the Reversal adjustment code check box.
5.	In the Valid from and Valid to fields, enter the first and last dates that the adjustment code is applicable.
6.	To create another adjustment code, click New, and then repeat steps 2 through 5.

Set up observation codes to adjust ICMS or ICMS-ST amounts
1.	Click Fiscal books > Setup > Observation codes.
2.	In the Observation codes form, enter an observation code.
3.	Enter a description.
4.	To enter another observation code, click New, and then repeat steps 2 and 3.

Set up fiscal books parameters per state
1.	Click Fiscal books > Setup > Fiscal books parameters per state.
2.	Select a state.
3.	If the ICMS tax amounts can be adjusted on fiscal documents, select the By fiscal document check box, and then select the default adjustment code and observation code.
4.	If the ICMS tax amounts cannot be adjusted on fiscal documents, clear the By fiscal document check box, and then select the default adjustment code.
5.	To automatically calculate an ICMS credit installment when an outgoing transaction is created, select the Calculate installment for outgoing transactions check box.
6.	To set up fiscal books parameters for other states, repeat steps 2 through 5.

Set up a fiscal organization
1.	Click Fiscal books > Setup > Fiscal organization.
2.	In the Root fiscal establishment field, select a fiscal organization that is used for SPED contributions.
3.	On the Fiscal establishment FastTab, fiscal establishments are automatically added to the list if they have the same nine digits of the CNPJ/CPF number as the fiscal organization that is selected in the Root fiscal establishment field. To remove a fiscal establishment that has been added to the list, click Remove. To add other fiscal establishments from other legal entities, click Add.
4.	On the Company social contract FastTab, enter the archive date of the company’s constitution contract and the company’s conversion.
5.	On the SCP FastTab, select the type of SCP company: Not participant as SCP partner; Participant as SCP partner; SCP.
6.	Introduce the SCP code when you selected SCP company type.
7.	On the Related SCP FastTab, click Add to enter the name and code of SCP related company. Note: This information is enabled if you selected Participant as SCP partner.
8.	On the Legal representative FastTab, click Add to enter the name of the company’s legal representative.
9.	Enter the CPF registration number and the role of the legal representative. To add another legal representative, click Add. To remove a legal representative that has been added to the list, click Remove.
10.	On the Independent auditors FastTab, click Add to enter the name of the auditor and the registration number.
11.	To remove an independent auditor that has been added to the list, click Remove. Note: This option is available when the Large company check box has been selected.

Set up a fixed asset group
1.	Click Fixed assets > Setup > Fixed asset groups.
2.	Click New to create a fixed asset group. Enter a unique identifier and name.
3.	Click Value models and create the value models that will apply to all the fixed assets that are assigned to the fixed asset group. Note: You must enter a value in the Fixed asset group field when you create a fixed asset. Default values for other fields for the fixed asset are inherited from the fixed asset group. These include the value model and its posting layers and depreciation profiles. In the Fixed asset group/value model form, you can view the posting layer of the value model that is created for the fixed asset group.
4.	Close the Fixed asset group/value model form.
5.	Click Depreciation books and create the depreciation books that will apply to all fixed assets that are assigned to the fixed asset group.
6.	On the General tab in the Fixed asset groups form, select values in the Number sequence code fields, as necessary. If you set up number sequences for the automatic numbering of fixed assets, select the Autonumber fixed assets check box, and select the number sequence for the fixed asset group in the Number sequence code field. If you set up number sequences for the automatic numbering of bar codes, select the Autonumber bar codes check box, and select the number sequence for bar codes in the Bar code number sequence field.

Set up requirements for SPED EFD - Contributions
1.	Click Fiscal books > Setup > Tax statements parameters. Select EFD - Contributions. On the Setup parameters FastTab, click Open.
2.	In the EFD – Contributions parameters form, enter the required SPED EFD - Contributions information.
3.	In the Type of activity field, select the activity type from the following options: Industrial or equivalent Industrial; Services; Retail; Financial activity; Real estate activity; Others.
4.	In the Version field, select the version of the SPED EFD - Contributions layout.
5.	Select the type of legal entity.
6.	In the Assessment regimen field, select the assessment schema that is used for SPED EFD - Contributions from the following options: Non cumulative – Calculate assessments based on billing or debits and purchases and deductions or credits; Cumulative – Calculate assessments based on billings that don’t have any deductions or credits; Both – Calculate assessments based on both the Non cumulative and Cumulative regimens.
7.	In the Booking and assessment criteria field, select the criteria to use to book the tax credit. For Dynamics 365 for Operations, only the Detailed option is supported.
8.	Select the type of assessment contribution. For Dynamics 365 for Operations, only the Basic tax value contribution is supported.
9.	In the Credit allocation method field, select the method of credit allocation: Direct or Proportional distribution.
This field is available if Non cumulative or Both are selected in the Assessment regimen field.
10.	In the NFe and ECF options field, select the NFe transaction reporting option from the following options: Consolidated – Consolidate all NFe transactions into one record on the C18X fiscal report; Detailed – List all individual transactions on the fiscal report.
11.	On the Fiscal establishment FastTab, enter the required SPED ECD information.

Set up requirements for SPED ECD tax statement
1.	Click Fiscal books > Setup > Tax statements parameters. Click SPED ECD. On the Setup parameters FastTab, click Open.
2.	Select the company to generate the SPED ECD text file for.
3.	Select the financial dimension set that the format of the SPED ECD text file will be based on. The financial dimension set should include the main account and the cost center dimensions.
4.	Select the file location where the SPED ECD text file will be generated.
5.	The Booking type is assigned automatically depending on the type of fiscal organization: G – This booking is used to detail all of the ledger journal transactions; S – This booking is used for the SCP company.
6.	Select the type of company situation from the following options, or leave the field blank to represent the regular situation: Division; Merger; Incorporation; Closing-down; Transformation.
7.	In the Opening fiscal period field, select from the following options: Regular; Opening; Split, Merge or Acquisition; Mandatory.
8.	Select the version of the SPED ECD text file format to generate: For Dynamics 365 for Operations, Version 2.00 is supported until fiscal year 2013; For Dynamics 365 for Operations, Version 3.00 is supported from fiscal year 2014; For Dynamics 365 for Operations, Version 4.00 is supported from fiscal year 2015; For Dynamics 365 for Operations, Version 5.00 is supported from fiscal year 2016.
9.	In the Auditor registration number field, enter the number of the company’s auditor.
10.	Enter the auditor’s name.
11.	Select the Large company check box if the company is a large company. Note: The steps 9, 10 and 11 are not available when Version 3.0 is selected. This information has been changed and included in the configuration of fiscal organization.

Set up accountant information for tax booking
1.	Click Organization administration > Setup > Brazil > Accountant details.
2.	In the Accountants form, enter the full name of the accountant.
3.	In the CPF field, enter the Cadastro da pessoa fisica, the tax registration number of accountant.
4.	In the CNPJ field, enter the Cadastro Nacional da Pessoa Jurídica, the tax registration number of the legal entity.
5.	In the CRC field, enter the registration number of the accountant in the Conselho regional de Contabilidade, the Regional accounting Council.
6.	Click Add, and then enter the address for the accountant.
7.	To add another accountant, click New and then repeat steps 2 through 6.


[!include[banner](../includes/banner.md)]
