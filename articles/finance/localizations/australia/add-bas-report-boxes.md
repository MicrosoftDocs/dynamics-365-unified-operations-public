---
title: Add BAS report boxes and generate the Australia Business Activity Statement BAS
description: This article describes how to add BAS report boxes and generate the BAS in Australia with Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 03/11/2025
ms.reviewer: johnmichalak
ms.search.region: Australia
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransVendInvoice, DefaultDashboard, LedgerJournalTransVendPaym, VendOpenTrans, TaxGroupLookup, TaxItemGroupLookup, CustFreeInvoice, CustTableLookup, CustPostInvoiceJob, TaxReportExtraFields, SrsReportViewerForm
ms.custom: 
  - bap-template
---
# Add BAS report boxes and generate the Australia Business Activity Statement BAS

[!include [banner](../../includes/banner.md)]

This article describes how to add BAS report boxes and generate the BAS in Australia with Microsoft Dynamics 365 Finance.

The following procedures walk you through how to add business activity statements (BAS) report boxes and generate the BAS in Australia. The procedures were created using the demo data company 'USMF' with a primary legal entity address in Australia.

## Prerequisites

Before you can execute the following procedures, you must define the additional BAS reconciliation account, create BAS PAYG reason codes, create BAS fringe benefit reason codes, create sales tax reporting codes, and create withholding tax groups with required purchase and sales transactions.

## Add BAS report boxes and print the Australia BAS

To add BAS report boxes and print the Australia BAS, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Declarations \> Sales tax \> Additional BAS report boxes**.
1. Select **New**.
1. In the **Settlement period** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **From date** field, enter a date.
1. In the **To date** field, enter a date.
1. In the **Document identification number** field, enter the activity statement unique document identification number.
1. Select the **Cover page** tab.
1. In the **7 Deferred installment** field, enter a number.
1. In the **7A Deferred GST on imports field**, enter a number.
1. In the **1G Credit for wholesale sales tax** field, enter a number.
1. In the **5B Credit from PAYG** field, enter a number.
1. In the **6B Credit fringe benefits tax** field, enter a number.
1. Select the **Back cover page** tab.
1. In the **W1 Total payroll** field, enter a number for total salary, wages and other payments.  
1. In the **W-2 Withheld from payroll** field, enter a number for the total amount you withheld from salaries, wages, and other payments. This value includes payments to contractors under a voluntary agreement shown in box **W1**.  
1. In the **W3 Withheld from investment where no TFN** field, enter a number. The W3 value covers other types of withholding such as interest, dividends, unit trust, or other investment distributions provided with a TFN (includes a nonresident), and any payments made to foreign residents. 
1. In the **W4 Withheld from invoices where no ABN** field, enter the total amount you withheld from payments to suppliers who didn't quote their ABN.  
1. In the **T1 Installment income** field, calculate your installment income for the quarter and enter that number.  
1. In the **T2 Installment rate** field, enter a number representing the T2 Installment rate. The rate is either the installment rate determined by the Australian Taxation Office, or the most recent varied rate if you varied the installment rate in a previous quarter in the same income year.    
1. In the **T3 New varied installment rate** field, enter a number if you want to vary your installment rate.    
1. In the **T4 Reason for variation** field, select the drop-down button to open the lookup. If you vary your installment rate, select a reason from the list that best describes why and then enter the appropriate code.  
1. In the list, select the link in the selected row.
1. In the **F1 ATO fringe benefit** field, enter a number. If you pay fringe benefits tax (FBT) quarterly, a predetermined installment value is shown.  
1. In the **F2 Estimated total fringe benefits** field, enter a number that represents the estimated total FBT liability for the year.  
1. In the **F3 Varied fringe benefits tax** field, enter a number that represents the amount of the varied FBT installment.  
1. In the **F4 Reason for variation** field, select the drop-down button to open the lookup. If the FBT installment amount has been varied, select the reason, and then enter the corresponding code.  
1. In the list, select the link in the selected row.
1. In the **7C Fuel tax credit over claim** field, enter a number that represents any adjustments to fuel tax credits that decrease your entitlement.  
1. In the **7D Fuel tax credit** field, enter a number that represents the amount of fuel tax credits that can be claimed depends on your business activities. For example, business activities might include acquiring, manufacturing, or importing taxable fuel into Australia, or when you use the fuel you manufactured. Enter any adjustments or corrections that increase your entitlements to fuel tax credits.  
1. On the Action Pane, select the **Action Pane** tab.
1. Select **Additional BAS report boxes \> Print Australian BAS**.
1. Validate the Australian BAS report.  

## Generate the Australian BAS

To generate the Australian BAS, follow these steps.

1. In Dynamics 365 Finance, go to **Tax \> Declarations \> Sales tax \> Australian BAS**.
1. In the **Settlement period** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **From date** field, enter a date value.
1. In the **Transaction date** field, enter a date value.
7. Select or clear the **Post and settle GST** checkbox.
8. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
