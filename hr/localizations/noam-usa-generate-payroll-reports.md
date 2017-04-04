---
# required metadata

title: Generate payroll reports
description: This topic describes the standard payroll reports that Dynamics 365 for Operations provides to help you with payroll processing and government reporting. Use these standard reports to create pay statements and W-2 forms that you can issue to your workers, validate payroll taxes and benefit amounts, and complete federal and state regulatory reports.
author: rschloma
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 31
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 220994
ms.assetid: 92b0da78-1c42-46f7-b1a2-334d75e625f3
ms.search.region: USA
# ms.search.industry: 
ms.author: brpotter
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Generate payroll reports

This topic describes the standard payroll reports that Dynamics 365 for Operations provides to help you with payroll processing and government reporting. Use these standard reports to create pay statements and W-2 forms that you can issue to your workers, validate payroll taxes and benefit amounts, and complete federal and state regulatory reports.

This topic describes functionality that is available only if the **Payroll - USA** configuration key is selected.

## Payroll standard reports
The following table summarizes when and why you use each report.

| Report                                   | Every pay period                                                                                                       | Quarterly                                                                                                                       | Annually                                                                                               | As required                                                                                     |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| Pay statements                           | After you generate the payroll payment journal, use this report to print pay statements that you can issue to workers. |                                                                                                                                 |                                                                                                        | Use this report to reprint pay statements for workers.                                          |
| Benefit register                         | Use this report to validate the benefit amounts that were calculated during payroll processing.                        |                                                                                                                                 |                                                                                                        | Use this report to validate the benefit amounts that were calculated during payroll processing. |
| Worker payment register                  | To comply with auditing best practices, use this report every pay period to validate data and sign off on pay runs.    |                                                                                                                                 |                                                                                                        |                                                                                                 |
| Tax register                             | Use this report to validate the tax amounts that were calculated during payroll processing.                            | Use this report to validate the tax amounts that were calculated during payroll processing.                                     | Use this report to validate the tax amounts that were calculated during payroll processing.            | Use this report to validate the tax amounts that were calculated during payroll processing.     |
| State quarterly wage and tax preparation |                                                                                                                        | Use the information on this report when you prepare the quarterly wage and tax forms for state unemployment taxes.              |                                                                                                        |                                                                                                 |
| Form 941 preparation                     |                                                                                                                        | Use the information in this form when you prepare the quarterly report of payroll taxes for the Internal Revenue Service (IRS). |                                                                                                        |                                                                                                 |
| Form 940 preparation                     |                                                                                                                        |                                                                                                                                 | Use the information on this report when you prepare the annual federal unemployment tax (FUTA) return. |                                                                                                 |
| Form W-2 reconciliation                  |                                                                                                                        |                                                                                                                                 | Use this report to balance Form W-2s and run validation before you issue Form W-2s to workers.         | Use this report to balance Form W-2s and run validation before you issue Form W-2s to workers.  |
| Form W-2                                 |                                                                                                                        |                                                                                                                                 | Use this report to create Form W-2s that you can issue to workers.                                     | Use this report to create Form W-2s that you can issue to workers.                              |
| Electronic Form W-2                      |                                                                                                                        |                                                                                                                                 | Use this report to file Form W-2s with the Social Security Administration.                             |                                                                                                 |



