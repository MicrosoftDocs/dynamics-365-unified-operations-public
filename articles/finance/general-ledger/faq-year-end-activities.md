---
# required metadata

title: FAQ for year-end activities 
description: This topic has been compiled to assist with year-end closing activities. The document primarily focuses on questions that risen multiple times among General ledger and Accounts payable over the last year.
author: kweekley
manager: aolson
ms.date: 12/14/2020
ms.topic: index-page
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: Customer
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2020-12-14
ms.dyn365.ops.version: 10.0.14

---

# FAQ for year-end activities

This topic has been compiled to assist with year-end closing activities. The document primarily focuses on questions that risen multiple times among General ledger and Accounts payable over the last year. 

## General ledger:  Running year-end close vs Undoing year-end close
We have seen organizations run the year-end close but were actually performing an undo of the year-end close.  If the year-end close is finishing really quickly or the year end close produces no opening balances, validate the ‘Undo previous close’ setting on the year-end close dialog. 

General ledger – Period close – Year end close – Run fiscal close drop dialog

[![Run fiscal close drop dialog](./media/faq-2020-yr-end-01.png)](./media/faq-2020-yr-end-01.png)

If “Undo previous close” = Yes, the previous year-end close is being reversed. When running an undo, all closing balance and opening balance entries will be deleted, as if the year-end close never ran.  The vouchers are deleted.  The year-end close will not run again automatically.  You must initiate the year-end close again, this time changing Undo previous close = No. 

> [!Note]
> The closing balance entry is optionally created in the year being closed; only if the GL parameter “Create closing transactions during transfer” = Yes.  The opening balance entry is always created, as this is the beginning balance for the next year. 

 
## General ledger: Difference between Undo and Delete GL parameter for year-end close
Confusion exists over the difference between the “Undo previous close” (on the year-end close dialog) and the GL parameter “Delete close-of-year transactions during transfer”.  
General ledger – Period close – Year end close – Run fiscal close drop dialog
 

The “Undo previous close” found on the dialog of the year-end close process will delete all closing balance and opening balance entries, as if the year-end close had never been run.  The vouchers are deleted.  The year-end close will not run again automatically.  You must initiate the year-end close again, this time changing Undo previous close = No. 
General ledger – Ledger setup – General ledger parameters
 

The GL parameter “Delete close-of-year transactions during transfer” is only used when running (not Undoing) the year end close (Undo previous close = No).  If the GL parameter is set to Yes, all closing balance and opening balance entries will be deleted and the year-end close will run again.  This is used when the organization wants all transactions, including adjustments since the last year-end close, to be posted in a single accounting entry for the closing balance and opening balance entries. 
If this option is set to No, all closing balance and opening balance entries remain. They are not deleted. Instead, a new closing balance and opening balance entry will be created for only the delta or new transactions posted since the last year-end close for that fiscal year.  
NOTE:  The closing balance entry is optionally created in the year being closed; only if the GL parameter “Create closing transactions during transfer” = Yes.  The opening balance entry is always created, as this is the beginning balance for the next year. 



 
## General ledger: Performance considerations
There are numerous settings and changes that can be made to improve performance of the year-end close.  These should be evaluated to determine if they can be utilized to improve performance. 
Dimension sets
When running the year end close, each dimension set balance is rebuilt, having a direct impact on the performance.  We have encountered organizations that needlessly create dimension sets because they were used at one point or might be used at some point.  These unnecessary dimension sets are still rebuilt during the year end close, which adds time to the process. Please evaluate your dimension sets and delete any unnecessary dimension sets.  
The unnecessary dimension sets also impact the batch job “BudgetDimensionFocusInitializeBalance.”
General ledger – Chart of accounts – Dimensions – Financial dimension sets
 

### Year-end close template configuration
The year-end close template allows an organization to select the financial dimension level to maintain when transferring Profit and loss balances to retained earnings.  The settings allow an organization to maintain the detailed financial dimensions (Close all) when moving the balances to retained earnings or choose to ‘summarize’ the amounts to a single dimension value (Close single). This can be defined for each financial dimension. Please see the documentation for the year end close for more information on these settings.  
Each organization should evaluate their requirements and if possible, close as many dimensions as possible using ‘Close single’ to improve performance. By closing to a single dimension value (which can also be a blank value), less detail has to be calculated when determining the balances for retained earnings account entries.

 
## General ledger – Period close – Year end close
 
Performance improvements for rebuilding financial dimension sets (new feature)
A new feature has been added to 10.0.16 that improves the performance of the year-end close and consolidation.  This feature changes the rebuild of the dimension sets to only happen for the relevant time frame, where previously it would rebuild for all dates. For example, if running a year end close for 2020, it will only rebuild the balances for transactions within the fiscal year 2020.  And if running consolidation for a date range of Nov 1, 2020 to Nov 30, 2020, it will only rebuild the balances for that date range. 
Because this feature is considered a breaking change, it must be enabled through feature management.  Feature name:  Performance improvements for rebuilding financial dimension sets. 
 


 
## Accounts payable: 1099 2020 year-end reporting changes

Two new regulatory features have been added for the 2020 1099 year-end changes. The first feature was released mid-year as a mandatory feature labeled “Apply changes to 1099-NEC and 1099-MISC forms for 2020” in Feature management. The purpose of this feature was to ensure that 1099 transactional data for the year 2020 could be tracked for the new 1099-NEC form. This feature added the 1099 fields to support the new 1099-NEC and updated the 1099-MISC fields. This update also upgraded vendor record data for the 1099 box information. 

The second regulatory feature is labeled “1099 statements updated for 2020 tax law” and it contains the following changes:
a.	1099-OID - IRS has converted the form to continuous use.
•	As such the year’s 3rd and 4th digit must be filled in when printed – use the Reporting year field’s 3rd and 4th digits from the Tax 1099 print options form.

b.	1099-NEC – A new form for 2020. This records non-employee compensation. 

c.	1099-MISC – Due to the creation of Form 1099-NEC, the IRS has revised Form 1099-MISC and rearranged box numbers for reporting certain income.
Changes in the reporting of income and the form’s box numbers are listed below.
•	Payer made direct sales of $5,000 or more (checkbox) in box 7.
•	Crop insurance proceeds are reported in box 9.
•	Gross proceeds to an attorney are reported in box 10.
•	Section 409A deferrals are reported in box 12.
•	Nonqualified deferred compensation income is reported in box 14.
•	Boxes 15, 16, and 17 report state taxes withheld, state identification number, and amount of income earned in the state, respectively.
d.	No changes to 1099-DIV or 1099-INT in 2020.
e.	Electronic filing – The format has changed to accommodate the new NEC form, and the MISC box changes described above. Publication for electronic filing requirements https://www.irs.gov/pub/irs-pdf/p1220.pdf

## Accounts payable: 1099 – How do I change the 1099 box and values for a vendor that wasn’t tracking 1099 information throughout the year?
Use the Update 1099 functionality (Accounts payable>Vendors>All vendors>Select a vendor>Vendor tab in ribbon>Update 1099) to go through previously paid invoice transactions to reassign the 1099 data appropriately according to the settings on the Tax 1099 tab on the Vendor form.

Can I run the Update 1099 for all my vendors at once? No, the Update 1099 routine is performed against a single vendor at a time. If this requirement is needed by your organization, please vote for the Idea titled “Batch Process for Update of Vendor's 1099 Data” located here:  https://experience.dynamics.com/ideas/idea/?ideaid=5493d608-350e-eb11-b5d9-0003ff68ded8

Accounts payable: 1099 – “Recalculate existing 1099 amounts” versus “Update all” in the Update 1099 utility.
The “Recalculate existing 1099 amounts” checkbox will reset the 1099 amount to the total paid values, when used in conjunction with the “Update all” checkbox. The “Recalculate existing 1099 amounts” checkbox only comes into play when there are partial 1099 values on the invoice or if it was modified on the Tax 1099 form. For example, assume you have an invoice valued at 1000.00, but the user manually types in a 1099 amount on the invoice of 500.00. When this is paid, 500.00 will be the 1099 amount paid. If you perform the recalculation routine, the system will change the 1099 amount to be 1000, which is the total that was paid.

Screenshot after payment of 1000, prior to running Update routine:
 

Screenshot after payment of 1000, after running Update 1099 routine. Marking both Update all and Recalculate existing 1099 amounts:
 
 



 
## Accounts payable: 1099 – Manually create 1099 transaction
There may be times an organization may need to manually create 1099 transactions that are not associated with an invoice. You can add manual 1099 transactions by navigating to Accounts payable>Periodic tasks >Tax 1099> Vendor settlement for 1099s. Select the button labeled “Manual 1099 transactions.” 

Manually created 1099 transactions are not updated with the Update all process or the Recalculate existing 1099 amounts processes in the Update 1099 utility.
Accounts payable: 1099 – Does Dynamics 365 Finance support the 1096 form? 

Dynamics 365 Finance doesn’t print the 1096 Annual Summary and Transmittal of U.S. Information Returns form.

## Accounts payable: 1099 – Public sector new feature 
A new public sector feature has been added to feature management, named Update 1099 information by main account. This feature lets you associate the 1099 values for a vendor by the main account in the accounting distribution, rather than the default account on the vendor record.

For more information, see [Set up vendors for 1099 reporting](../localizations/noam-usa-set-up-vndrs-1099-rprtg).

