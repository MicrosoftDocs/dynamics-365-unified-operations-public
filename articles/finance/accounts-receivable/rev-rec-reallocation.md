---
# required metadata

title: Revenue recognition reallocation 
description: Reallocation allows an organization to recalculate the revenue price when to the terms of a contractual sale are changed. The sales order documents are considered the contract for the purpose of recognizing revenue. This topic includes multiple scenarios that describe how to recognize revenue in specific situations.
author: kweekley
manager: aolson
ms.date: 12/21/2020
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
ms.search.validFrom: 2020-12-21
ms.dyn365.ops.version: 10.0.14

---

# Revenue recognition reallocation

Reallocation allows an organization to recalculate the revenue price when to the terms of a contractual sale are changed.  The sales order documents are considered the contract for the purpose of recognizing revenue. 

Your own organization must decide whether a reallocation is necessary. Adding a new line to a sales order, or adding a new sales order for the customer, might not constitute a change to the contract. The following scenarios might require a reallocation:

- Items on the sales order were added or removed by the customer after the order was fully or partially invoiced
- Multiple sales orders were entered for the same negotiated contract, whether the sales orders were in a confirmed or invoiced state

A customer returned or received a credit for an item after the original sales order has been fully or partially invoiced. A few important restrictions exist for the reallocation process:

- Reallocation can be run only once.  Therefore, it’s important to run this process only after all changes are finalized. 
- Reallocation is not permitted on any project sales orders.
- If multiple sales orders are involved, they must be for the same customer account.
- All sales orders reallocated must be in the same transaction currency. 
- The reallocation process cannot be reversed or undone after it is processed. 

## Reallocation setup
One parameter impacts the reallocation process. Because a reallocation can be performed on a sales order that is partially or fully invoiced, any prior accounting entries for the invoice must be corrected using the new, reallocated revenue prices. This is done by reversing the original invoice’s accounting entry and posting a new accounting entry based on the reallocated revenue prices. 

Each organization needs to decide whether the correction updates only General ledger or whether Accounts receivable will be updated, as well as General ledger.  This is determined by going to **Revenue recognition > Setup > General ledger parameters > Revenue recognition** and setting the “**Post invoice corrections to Accounts receivable** parameter as appropriate. The “appropriate” settings are specified in each of the four scenarios. 

[![General ledger parameters set to post invoice corrections](./media/01_RevRecScenarios.png)](./media/01_RevRecScenarios.png)

If Post invoice corrections to Accounts receivable is set to Yes, processing of the reallocation will result in the following:
- A credit document is created in the Accounts receivable module to reverse the invoice that needs correcting.
  - The credit document will reuse the original invoice number, but with a “-1” appended to the invoice number. 
  - The credit document is automatically settled against the original invoice. If the original invoice was already settled to another credit document/payment, the settlement will be reversed automatically.
  - The credit document will post to general ledger to reverse the accounting entry of the original invoice. It will reverse the accounting entry posted on the original invoice with the exception of the Inventory and COGS transaction entries.  
- A new invoice is created in the Accounts receivable module based on the new reallocated price amounts. 
  - The new invoice will reuse the original invoice number, but with a “-2” appended to the invoice number. 
  - The new invoice will automatically be settled to any credit document or payments that were previously settled with the original invoice.  
  - The new invoice will post to the general ledger using the new reallocation revenue price amounts. It will not post to Inventory and COGS again, since that is maintained on the original invoice’s accounting entry. 
 If the **Post invoice corrections to Accounts receivable** field is set to **No**, processing the reallocation will result in the following:
- A reversing accounting entry is posted to only General ledger.  All the accounting from the original invoice is reversed, except for the Inventory and COGS account entries.  
- A new accounting entry is posted to only general ledger base d on the new reallocation revenue prices.  It will not post to Inventory and COGS accounts again because those entries are maintained on the original invoice’s accounting entry. 
- The invoice in Customer transactions is not impacted or changed and will still reflect the original accounting entry.  There is no reference to the reversing or new accounting entries. 

There are pros and cons to updating General ledger only vs updating Accounts receivable and General ledger. We recommend that you evaluate the requirements for your organization to determine which option to use. By updating Accounts receivable and General ledger, the correct accounting entries will display on the new invoice and can be viewed from the document in Customer transactions.  Also, the settlement process will now use the updated accounting entries for posting any cash discounts and gains or losses. Some cons include that the credit document and new invoice will appear on customer statements and aging reports, just as any other customer invoice and credit document. The new documents have a description to indicate that they were created as the result of an accounting correction. 

## Perform a reallocation
The reallocation process can be started by selecting **Reallocate price with new order lines** from any sales order you need to reallocate or under Revenue recognition – Periodic tasks.  If opening the page from Periodic tasks, enter the appropriate filters such as the Customer account. 

[![Reallocate price with new order lines](./media/02_RevRecScenarios.png)](./media/02_RevRecScenarios.png)

The top grid is a list of the sales orders for the customer. You start by selecting the sales order(s) that need to be reallocated. Project sales orders and any sales order with a reallocation ID can’t be selected.  That is because project sales orders can’t be reallocated, and non-project sales orders can be reallocated only once. If a reallocation ID exists, that means the sales order is marked for reallocation by another user. 

After selecting one or more sales orders, the sales order lines display in the bottom grid. Select the sales order lines that need to be reallocated.  If you only select one sales order, that means you have lines on the same sales order that need to be reallocated.  This can occur when one of the sales order lines has already been invoiced and then a new line is added, or an existing line is removed or canceled. If a line has been removed, that line won’t display so it can’t be selected, but will still be considered when the reallocation process runs. 

After selecting the necessary sales order lines, use the buttons on the page as follows:

- **Update reallocation** – This button calculates the new revenue price amounts for the selected sales order lines. If a line had been removed or canceled, the reallocation will happen with only the existing lines selected. 

[![Sales order lines before reallocation before updating reallocation](./media/03_RevRecScenarios.png)](./media/03_RevRecScenarios.png)

The new amounts are shown in the **Reallocated amount** column in the sales order **Lines** grid. The reallocation has been processed but not yet calculated.

[![Sales order lines after reallocation](./media/04_RevRecScenarios.png)](./media/04_RevRecScenarios.png)

- **Process** – This button will process or post the reallocated revenue prices.  There is no way to reverse the reallocation after choosing Process. The reallocation will run automatically if the Update reallocation button wasn’t selected prior to selecting the Process button.
  - If none of the sales order lines have been invoiced, the Process button will update the revenue price amounts on any sales orders selected for the reallocation. 
  - If one or more sales order line has been invoiced, the Process button will post correcting accounting entries and correct the revenue schedule details created for the invoiced sales order line (if they exist).
- **Expected voucher** – This button will show a preview of the accounting entries created for any sales order lines that have been invoiced.  If none of the lines have been invoiced, nothing will display here.  The reallocation will run automatically if the Update reallocation button wasn’t selected prior to selecting the Expected voucher button.
- **Revenue reallocation** – This button will open a page displaying the revenue price allocation for all the selected lines. Nothing can be modified here.  It is used to show the line amounts used for performing the reallocation. 

[![Reallocation update showing line amounts used for reallocation](./media/05_RevRecScenarios.png)](./media/05_RevRecScenarios.png)

- **Reset data for selected customer** – This button is used to clear the data in the reallocation table for only the selected customer if the process was started and not completed. For example, if multiple sales order lines were marked for reallocation and the page was left open without selecting the **Process** button, the page could time out and the sales order lines would remain marked.  This means the lines wouldn’t be available for another user to complete the process. Sometimes the page may even open blank when this happens. This button can be used to clear unprocessed sales orders, and then allow any user to complete the reallocation process.
 ## Scenarios for reallocation


