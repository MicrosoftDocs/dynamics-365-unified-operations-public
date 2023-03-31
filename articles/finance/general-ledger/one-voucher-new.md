---
# required metadata

title: One voucher 2
description: One voucher for financial journals lets you enter multiple subledger transactions in the context of a single voucher.
author: kweekley
ms.date: 04/05/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalSetup, LedgerParameters, AssetProposalDepreciation
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 14091
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2018-03-16
ms.dyn365.ops.version: 8.0.2

---

# One voucher 1
[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]


## What is One voucher?
Due to the flexibility of financial journals, you can enter a single voucher (which represents one transaction) with multiple customers, vendors, fixed assets, 
projects, or bank accounts. Microsoft refers to this functionality as One voucher. The One voucher scenarios do NOT include transactions that include Ledger accounts 
only, which posts to general ledger and not subledgers such as accounts receivable, fixed assets, bank, etc. 

There are two categories of One voucher examples:
 - The voucher contains multiple transactions entered as a single transaction. Here are some examples*:
  - Multiple vendor payments are entered on each line (no offset account) with the payments sum  offset to a bank account entered on one line. Payments summarization   is done to update the bank subledger as a summarized amount to match the bank account statement, while still recording each vendor transaction in detail in the   Accounts payable subledger. The same scenario is also found on the Customer payment side. 
  - Multiple fixed assets are acquired in a single voucher. This is often done when entering beginning balances for the fixed asset module. 
 - The voucher contains one transaction, which impacts multiple non-Ledger account types. Here are some examples*:
   - Bank transfers
   - Netting vendor/customer (same party) balances
   - Transferring a balance from customer A to customer B
   - Vendor invoice with multiple ‘lines’ containing fixed assets or projects
*Not an exhaustive list

The examples given for each category represent valid business requirements. Sometimes these business requirements can’t be met any other way; the organization is required to enter the transaction(s) as One voucher. But other times there are valid options for how these business requirements can be met. The transactions can be entered differently or use another feature. 

## Issues with One voucher
Using the One voucher functionality to meet business requirements could cause issues. Various processes, transaction reversals, and inquiries/reports require transaction details. That detail can’t be determined from the current data model when multiple transactions are entered in summary into one voucher. Also, detail can’t always be determined clearly within knowing the ‘transaction type’ being entered. This is due to the flexibility of journals, especially when entered through the general journal. 

Some scenarios might still work correctly, depending on your organization's setup.  The following areas are where you may see issues:
 - Settlement -  If more than one vendor or customer exists on a voucher, the accounting created during settlement can be incorrectly allocated to financial dimensions. For more information about issues that can occur during settlement, see Single voucher with multiple customer or vendor records.
 - Tax calculation – If more than one voucher or customer exists on a voucher, the tax calculation can be incorrect. 
 - Transaction reversal – If more than one subledger account type exists on the voucher, the reversal of a single subledger transaction may post an incorrect   accounting entry for the reversal within general ledger. For example, if you acquire multiple assets in one voucher then reverse the acquisition of only one asset,   the general ledger accounting will be incorrect for the reversal. 
 - Reporting and inquiries - If you include more than one subledger account type (vendor, customer, etc) on a voucher, reports/inquiries will only show the first   account value found. See the following example for details. 

For example, you post the following multi-line vendor invoice, which contains four projects which represent the ‘lines’ on the invoice. This is a common business 
requirement for those organizations that use journals extensively.

[![Multiline voucher.](./media/Journal-voucher1.png)](./media/Journal-voucher1.png)
 
Three of the four projects posted to the same main account 601500. If you open the Accounting source explorer to view details about posted transactions for that main 
account, notice that the Project ID is 000057 for all three lines. This is a known limitation of using One voucher. The detail won't correctly link each line to the appropriate project on the journal so the ‘first one found’ is always shown on reports and inquiries. 

[![Example of projects.](./media/Project2.png)](./media/Project2.png)
 
### How to enter a transaction as One voucher
In order to enter a One voucher transaction, go to **General ledger > Ledger setup > General ledger parameters** and set the **Allow multiple transactions within one voucher** field to **Yes**. 

[![General ledger paramenters.](./media/GL-parameters3.png)](./media/GL-parameters3.png)

 
You can enter a One voucher transaction on the **Journal names** page and setting the **New voucher** field to:
-  **One voucher number only**. Every line that you add to the journal is now included in the same voucher, and those lines would contain more than one customer, vendor, bank, fixed asset or project.
-  **In connection with balance**. Enter a multiline voucher where there's no offset account and the lines contain more than one customer, vendor, bank, fixed asset or project. 
-  **In connection with balance**. Enter a single-line voucher where both the account and the offset account contain a subledger account type, such as Vendor/Vendor, Customer/Customer, Vendor/Customer, or Bank/Bank.

### Does my business scenario require One voucher?
The following scenarios have been identified as to why customers use the One voucher functionality or reasons why they use it. Some of these business requirements can 
be met only by using One voucher. However, for many scenarios, alternatives are available. 

|Scenario|	One voucher required?	|Alternative|
|---------|----------------------|-----------------|
|Vendor payment summarization - An organization communicates a list of vendors/amounts to its bank. The bank uses this list to pay the vendors on the organization's behalf. Each vendor payment must post in detail to Accounts payable, but the sum of the payments posts to the bank account as a single withdrawal.|	No|	Starting on Dynamics 365 Finance version 10.0.32, there's the feature **Ability to post detailed vendor and customer payments, but summarize amounts to bank account**. For more information, see [Post detailed vendor and customer payments](summary-payment.md). |
|Customer payment summarization - Customer payments are deposited as a lump sum on the bank account. Each customer payment must post in detail to AR, but the sum of the payments posts to the bank account as a single deposit.|	No| Starting on Dynamics 365 Finance version 10.0.32, the feature **Ability to post detailed vendor and customer payments, but summarize amounts to bank account**.|
|Vendor/Customer invoice – An invoice is entered for a single customer or vendor, but additional lines represent the lines of the invoice and have multiple fixed assets or projects.| 	Yes	|     |
|Customer prepayment payment journal that has taxes on multiple "lines" - A customer makes a prepayment for an order. The lines of the order have different taxes. The prepayment customer payment must contain the customer on multiple lines so taxes can be calculated for each line.|	Yes|  |	
|Customer reimbursement - If the Reimbursement periodic task is run from Accounts receivable, it creates a transaction to move the balance from a customer to a vendor. The vendor is the same party as the customer. 	|Yes	|    |
|Fixed asset maintenance: Catch-up depreciation, split asset, calculate depreciation on disposal - The catch-up deprecation, splitting an asset and calculating depreciation for asset disposal all used create a single voucher. |	No	|Starting on Dynamics 365 Finance version 10.0.21 and later, fixed assets transactions for catch-up depreciation, splitting an asset, and calculating depreciation for the disposal of an asset will be created using different voucher numbers.|
|Bills of exchange and promissory notes -  Bills of exchange and promissory notes move the customer or vendor balance from one Accounts receivable or Accounts payable 
ledger account to another, based on the state of the payment. Because the same customer/vendor is always used within the voucher, no reporting issues exist.|Yes|   |	
|Netting – If a customer and vendor are the same party, the balances for a vendor and customer are netted against each other. This approach minimizes the exchange of money between an organization and the customer/vendor party.|	Yes/No	|Netting can be accomplished by entering the increase and decrease in separate vouchers, and then posting the offset to a clearing ledger account. For some organizations, this requires too much overhead and they choose to use One voucher instead. |
|Transfer balances - An organization might have to transfer a balance from one vendor to another vendor, either because of a mistake or because another vendor has taken over the liability. Transfers of this type also occur for account types such as Customer and Bank.|	Yes/No	|Balance transfers from one account (vendor, customer, bank, and so on) to another account can be done through separate vouchers, and the offset can be posted to a clearing ledger account. For some organizations, this requires too much overhead and they choose to use One voucher instead.| 
|Settle multiple unposted payments to the same invoice - This scenario is typically found in organizations where customers can use multiple methods of payment to pay for purchases. In this scenario, the organization must be able to record multiple unposted payments and settle them against the customer invoice.|	No	|A new feature was added in Microsoft Dynamics 365 Finance that enables multiple unposted payments to be settled against a single invoice.| 
|Country-specific features - The Single Administrative Document (SAD) feature for Poland currently requires transactions be grouped together, and this is done using the voucher number. There may be additional country-specific features that require the One voucher functionality.|	Yes	|    |
|Mechanism to group transactions from a business event - An organization has a single business event that triggers multiple transactions. The accounting department wants to view the accounting entries together for easier auditing. A similar scenario is where bank transactions are recorded in Finance through a file received from the bank. Organizations often want to group together those transactions by using the bank statement number in the file. |	No|	While grouping transactions together is a valid scenario, the voucher number must never be used for this purpose. Vouchers represent individual transactions, and never a group of transactions. Transactions can be grouped by other fields such as the journal batch number or the document number.|
|Enter beginning balances - Organizations often enter beginning balances for subledger accounts (vendors, customers, fixed assets, and so on) as one voucher transaction. | No	|Beginning balances for each subledger account must be entered as separate vouchers, and the offset can be posted to a clearing ledger account, which is offset by the beginning balance for general ledger.|
|Correct the accounting entry of a posted document - An organization might have to correct the Accounts receivable or Accounts payable ledger account for a posted invoice. The invoice is correct, so it shouldn’t be reversed. |	Yes/No	|If a correction must be made to the Accounts receivable or Accounts payable ledger account, an adjustment can be made directly to the ledger account. This approach requires that the adjustment be made during a "down time," so that the ledger account can temporarily allow manual entry. One con of this approach is that the vendor/customer to ledger reconciliation reports will show a difference going in/out. The net amount is zero. |
|Post in summary to the general ledger - Organizations often want to post to the general ledger in summary to minimize the amount of data. However, those organizations typically still require that the transaction details be maintained. When posting is done in summary through a single voucher, the transaction details aren't known and can't be maintained.|	No|	Because the transaction details are lost, organizations must not use One voucher to post in summary if details are required for reporting.|
|"The system allows it" - Organizations often use the One voucher functionality merely because the system lets them use it, without understanding the implications.|No|	This is never a valid reason to use the functionality if it’s not required for another business requirement. |

### The future of One voucher
Because of the issues that can occur when One voucher is used, the following options are being explored:
 - New features will continue to be introduced if there's a better way to accomplish the business scenario. For example, on Dynamics 365 Finance version 10.0.32, a new feature was introduced that allow payments to be entered as separate vouchers, but still update the bank account in summary. As features are added, they're documented in the Alternative columns above for each business scenario.
 - Some transactions may continue to be entered through the journal, within one voucher, but additional data could be tracked to correctly identify transactional details.
 - Another option may be a combination of new features while still entering transactions for the business scenarios within the journal using a single voucher. 

Depending on the approach for each business scenario, it may be only portions of the One voucher functionality that will be deprecated.

As new features are introduced, your organization must continuously evaluate whether the option **Allow multiple transactions within one voucher** on the **General ledger parameter** page can be turned off. We recommend not using One voucher for integrations, unless you require the functionality for one of the documented functional gaps.

After all the functional gaps are filled, Microsoft will communicate what portions of One voucher will be deprecated. If some portions are deprecated, it won't be 
effective for at least one year after all features are introduced and a communication is made to all customers. 

