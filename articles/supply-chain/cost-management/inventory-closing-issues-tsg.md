---
title: Inventory costing TSG
description: Access TSGs for inventory costing issues in Microsoft Dynamics 365 Supply Chain Management.
author: soumyamoydas
ms.author: soumyamoydas
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: faq
ms.date: 10/11/2025
ms.update-cycle: 1095-days
ms.custom: 
  - bap-template
  - evergreen
---

# Troubleshooting commonly experienced Inventory Closing/Recalculation/Reverse issues 

[!include [banner](../includes/banner.md)]

This is a troubleshooting guide for some common issues related to inventory closing, recalculation and reverse in Microsoft Dynamics 365 Supply Chain Management.

## “_Unable to edit a record in abc table_” - How to resolve the Inventory Closing/Recalculation/Reverse for this SQL issue?

This message signifies that some SQL issues have prevented further execution, due to which the batch job failed. Normally these issues can be deadlocks as multiple other processes are also executing at the same time, or SQL Server availability issues due to increased traffic, or due to insufficient and inappropriate indexing. Generally, these SQL issues are transient and shall be done away with retries.  

In case the issue persists after retrying, please contact Microsoft Support or your Partner. 

## “_Duplicate reverse is not allowed_” - What to do when Inventory Reverse ends with this error?  

This issue mainly occurs when user tries to execute the reversal/cancellation of multiple closing/recalculation vouchers at the same time. As shared in the best practices for Inventory Reverse, always execute the reversal of one voucher at a time, and only after its completion, proceed with further reversals, i.e., reversals should be carried out sequentially. This is a check used to prevent multiple reversals and thereby avoid any inventory & ledger data corruption due to concurrent updates of adjustments/settlements/postings. 

This issue can rarely occur if the previous reversal execution has not completed successfully, the batch job has ended in error, and user tries to execute a fresh reverse of the original voucher. This can be due to system issues, sudden crashes, system or SQL server unavailability, etc. In such cases, you can reach out to Microsoft Support or your Partner. 

## “_Fiscal period for abc is not open_” - What to do when Inventory Closing/Recalculation/Reverse ends with this error? 

Please verify the ledger calendar period status from _General Ledger_ -> _Calendars_ -> _Ledger calendars_ -> Select the required ledger period and then verify the period status for specific legal entities. Ideally, the period status should be “_Open_” to allow the posting of any adjustments/settlements. 

## “_Transaction abc cannot be reopened as it has already been pre-closed_” - What can be done when Inventory Closing/Recalculation/Reverse ends with this error? 

This issue can rarely occur if there are any data corruptions in the inventory transactions/adjustments, when pre-closing has posted settlements to financial transactions and closed them, instead of the non-financial transactions. One of the mitigations is to explicitly reset the settlements in those financial transactions and retry the closing process again. Please reach out to Microsoft Support or your Partner to fix this issue. 

## “_The entry for category x on project y cannot be posted/approved because it would cause the cost budget to be exceeded by z_” - What can be done when Inventory Closing/Recalculation/Reverse ends with this error? 

This issue can appear when the closing/recalculation/reverse adjusts/settles the project enabled inventory transactions, and such adjustments/settlements exceed the budget control price set for that specific project. As a temporary mitigation, please navigate to _Project management and accounting_ -> _Setup_ -> _Project management and accounting parameters_ -> _Cost control_ -> _Budget control_ -> Disable “_Use budget control_” 

Once disabled, resume the closing/recalculation/reverse voucher, and once the operation completes, enable the parameter back. 

For permanent mitigation, please try updating the project budget control cost as per the business requirement. 

## “_Only users in user group x can post in module y in the period containing the date z_” - What can be done when Inventory Closing/Recalculation/Reverse ends with this error? 

Please verify the ledger calendar period access level from _General Ledger_ -> _Calendars_ -> _Ledger calendars_ -> Select the required ledger period and then verify the access level for specific modules and legal entities. Default access level for all the modules is “_<All>_”. 

## “_Another closing or adjustment has not finished yet_” - How to fix if Inventory Closing/Recalculation ends with this error? 

Some other closing or recalculation voucher execution might be progress when you are trying to execute another closing or recalculation. Please wait for the previous closing voucher to complete execution and post that you can execute another fresh closing or recalculation. 

## “_Account number for transaction type abc does not exist_” - What can be done when Inventory Closing/Recalculation/Reverse ends with this error? 

This issue is related to incorrect account setup in the inventory posting profiles. Please navigate to _Inventory Management_ -> _Setup_ -> _Posting Profile_. Select the required transaction and type, and verify whether any _Main Account_ is mentioned for that, corresponding to the available filters (if any). 

## “_Inventory closing cannot proceed because available physical on-hand inventory on item abc is currently negative, which is not allowed according to its item model group_” - What can be done when Inventory Closing/Recalculation/Reverse ends with this error? 

This can happen because of data corruption in the posted inventory transactions, when the on-hand physical/financial inventory becomes negative which is otherwise not allowed as per the item’s Item Model Group configuration. Ideally this error should be flagged out while posting transactions for an item which results in negative on-hand, and not during inventory closing/recalculation process. But if any manual intervention or data migration or direct database updates are done, these checks are skipped and hence the error is thrown during the stock closing process.

As the error already mentions the specific item, please go through the inventory transactions for that item and try to figure out the actual issue. If required, enable the negative physical/financial inventory, but final call should be taken as per your business requirements. Else manual adjustments can also be posted to balance out the inventory transactions resulting in negative inventory. Once these transactions are fixed, execute consistency check fix for that item from _System administration_ -> _Periodic tasks_ -> _Database_ -> _Fix error_ -> _Inventory management_ -> _Item_ -> Enable checkbox for _Inventory transactions_ and _On-hand_, then filter the exact item from the dialog. If required, this process can be executed as a batch process in the background. The final fix logs can be viewed from the batch job logs. Upon completion of this process, resume the closing/recalculation operation. 

## “_Batch task failed: Cannot select a record in Current client sessions (SysClientSessions). Sessionld: 0, 0. The SQL database has issued an error._” - How to resolve the Inventory Closing/Recalculation/Reverse for this SQL issue?

This issue can occur due to SQL Server unavailability, deadlocks, blockings or any other generic SQL limitation/error. Most of the time, these issues are transient and never cause any data corruption. Please retry the operation again. If the issue persists, please reach out to Microsoft Support or your Partner. 

## “_Close stock - processing level x with a total of y bundles_” - What can be done if inventory closing/recalculation ends with this error? 

This is a generic error thrown mostly in cases of business data corruption, manual changes in the decimal precision in the customized version, incorrect exchange rate configurations while posting source documents, etc. Try to trace the exact item, inventory transactions, etc. which would be responsible for this error. Then execute the consistency check for that item for _on-hand_ and _inventory transactions_, to verify whether there are data inconsistencies which can be corrected autonomously. If the issue persists, please reach out to Microsoft Support or your Partner. 

## Why are there no voucher postings for Inventory Closing/Recalculation despite having Inventory Settlements? 

There should be voucher postings for closing/recalculation if there are inventory settlements/adjustments (can be viewed from _Settlements_ tab after selecting the respective voucher from _Closing and Adjustment_ form). Please try to cross-check the posting profile setup from Inventory Management -> Setup -> Posting. 

Please confirm whether the batch job ended successfully or any errors can be traced from either _Batch Job_ or _Closing and Adjustment_ form. Also, check the status of the voucher whether the executed ended or it is still in progress.  

This issue can occur if account or ledger is not set up correctly, fiscal period is closed, fiscal period postings don’t have proper access level, project budgeting and cost control mismatch, system issues like sudden crashes or SQL availability issues, etc.  

Please try to trace the exact error from _Closing and Adjustment_ logs or _Batch Job_ logs and check the same in this FAQ or other public documentations, else please reach out to Microsoft Support or your Partner. 

## Why are there no voucher postings for Inventory Reversal despite having voucher postings for original Inventory Closing/Recalculation voucher? 

This is unusual behavior and could occur if the system encounters a failure during the reversal/cancellation process.  

Please navigate to the related batch job in _Batch Jobs_ form and check for job progress and error logs. Also navigate to the reverse voucher from _Closing and Adjustment_ form, select it, and view the _Log_ details.  

If the issue persists, please reach out to Microsoft or your Partner for further support. 

## Why are my inventory transactions posted at a different cost price than the one I have mentioned? 

Please note that issue transactions are usually posted at the running average cost, and the receipt transactions are posted at the cost specified during posting the document line, or the latest activated cost price. 

The system estimates this running average cost price for an item by using the following formula: _Estimated price = (Physical amount + Financial amount) ÷ (Physical quantity + Financial quantity)_. This cost varies depending on whether "_Include physical value_" is enabled or not.

For more details on running average cost price, please refer [this guide](https://learn.microsoft.com/en-us/dynamics365/supply-chain/cost-management/running-average-cost-price).

## Why is item cost inflated? 

Pricing several inventory issue transactions without having enough receipt transactions can cause estimates of the running average cost to be inflated. This is normally observed when “_Include physical value_” is enabled in conjunction to the enablement of “_Negative physical inventory_” in the _Item model group_. If “_Include physical value_” is disabled but this issue is still observed, please check whether “_Negative financial inventory_” is enabled. 

For more details on running average cost price, please refer [this guide](https://learn.microsoft.com/en-us/dynamics365/supply-chain/cost-management/running-average-cost-price).

## Why does the cost change after running inventory closing/recalculation? 

Inventory closing/recalculation is meant to adjust the on-hand and inventory transactions. Hence, post these operations, it is expected that the cost adjusted/settled would modify resultant cost of the inventory transactions. 

For further details on the calculations, please refer to the relevant sections in public documentation. 

## Why am I finding already closed inventory transactions being reopened and settled/adjusted again? 

This behavior is by design and might be observed for items using Weighted Average (Date) as the valuation model.  

As per the design of carrying out settlements/adjustments through inventory closing/recalculation, a summarized transaction is created each for all issues and receipts separately, and these summarized transactions settle/adjust issues to receipts. Now, post-closing, if any manual adjustment is posted to any inventory transaction which was involved in any of the previous summarized transactions, and a fresh closing/recalculation is executed, then correspondingly all the inventory transactions which made up the summarized transaction contributing to the settlement/adjustment process, would be reopened and re-settled/re-adjusted.  

## I am getting incorrect/abnormal inventory costs reported for an item. How can we use the system to initially check/fix the issue for us? 

Please execute consistency check (for an item) from _System administration_ -> _Periodic tasks_ -> _Database_ -> _Check/Fix error_ -> _Inventory management_ -> _Item_ -> Enable checkbox for _Inventory transactions_ and _On-hand_, then filter the exact item from the _dialog_. If required, this process can be executed as a batch process in the background. The final check/fix logs can be viewed from the batch job logs or in the notification panel. Once this is completed and if the valuation method for that item is periodic, it would be better to execute recalculation to adjust the on-hand as per the valuation method.  

## Why does my ledger Trial Balance differ from Inventory Value post execution of closing/recalculation/reverse? 

Please verify whether the closing/recalculation/reverse execution has been completed successfully and whether voucher postings are present. Cross check the status of batch job with the voucher execution status. Once verified, rebuild the trial balance for the specific account where you are observing the differences. 

If the issue persists, this means there might be inconsistency between the general ledger and inventory postings. Try generating potential conflicts report to trace the items resulting in conflicts.  

Next, inventory value report can be generated for those specific items to trace the inconsistent inventory transactions. Consistency check shall be executed for those items for on-hand and inventory transactions to check whether it resolves the data inconsistencies. If the consistency check fix makes any changes to the inventory postings, execute inventory closing again and rebuild the trial balances to check whether the balance matches now.  

In case none of these help, please reach out to Microsoft Support or your partner. 
