## Using cash control limits
Cash control allows you to define a limit for preventing additional transactions from posting if no cash balance is available or if the transaction causes the balance to be reduced below the defined limit. Accounts payable vendor invoices and General ledger Advanced ledger entries are validated when they are created, edited, and posted. If the transaction’s posting would cause the related cash account’s balance to be reduced below the limit defined for the account, the user receives an error message and must change the account to continue.

You can also allow specified user groups to override cash control. If a user in a specified user group receives a warning that the cash balance for the account will be reduced below the limit, he or she can optionally choose to continue with posting the transaction. Users might override the cash control limit when the expenditure must be posted in advance of receiving the funds to cover it; or when an approved transfer must happen, but has not been entered or posted yet.

The cash control limit is compared to the cash control balance (cash account balance minus all posted, unpaid Accounts payable invoices). The limit is surpassed when the cash control balance is less than the cash control limit (threshold).

## Set up cash control

## Inititial setup
1. Go to **General leger > Ledger setup > General ledger parameters**.
2. In the Cash control validation section, choose the **Financial diemension set** that will be used to validate the cash control balances.
3. In the Cash control override field,choose the **User group** that can override cash control.  This will allow users that are in this security group to post transactions that exceed the cash control threshold.

## Set up cash control accounts 
1. Go to **General ledger > Ledger setup > Posting setup > Cash control** configuration.
2. Select the **Display account names** check box to view the account names for cash and Accounts payable accounts that you enter in the grid area.
3. Enter each cash account; it is recommended to add all valid cash account financial dimension strings. You can then specify which cash accounts are included in the cash control limitation.
4. In the **Cash account** field, enter the cash account financial dimension string. You must enter all of the account numbers.
5. Select the **Participate** check box to indicate that the cash account financial dimension string is subject to cash control. These cash accounts and the corresponding Accounts payable accounts are validated against the cash control configuration rules.
6. Optional: Enter the Accounts payable account financial dimension string used with vendor invoices (**Accounts payable** account field). You must enter a complete account number.
7. In the **Threshold** field, enter the amount that must remain in the cash account to pass validation. You can enter a negative number if the cash account is allowed to be overdrawn (more transactions paid than are in the account).

## View accounts in cash control
You can review the current balances of the accounts you defined in the Cash control configuration form. Go to **General ledger > Inquiries > Cash control inquiry**.
The inquiry includes the following information:
- Current cash account balance
- Balance of all posted, unpaid Accounts payable invoices applied to the cash account's corresponding Accounts payable account
- Cash control balance, which is the current cash account balance minus all of the posted, unpaid Accounts payable invoices and Advanced ledger entries
- Cash control threshold so you can compare the cash control balance to see if paying the Accounts payable invoices would put the cash account balance below the threshold

## Process transactions with cash control validation
Cash account balances are validated for Accounts payable invoices and Advanced ledger entries. The line item amount is validated against the cash and accounts payble accounts that the line's financial distributions are associated with.

[!Note] Budget control is seperate from cash control and can display unrelated errors.

If the cash threshold will be exceeded, the user receives an error message. The error prevents users from further processing of the invoice unless they are allowed to override cash control.

## Vendor invoice workflow

### When workflow is set up for autoposting
When using cash control functionality with Accounts payable vendor invoice workflow, and workflow is set up for autoposting, then at that step the system validates whether the submitting user has privileges to override the cash control threshold. 
If the invoice will exceed the cash control threshold:
- If the user does not have override privileges, an error message appears in workflow history for the related vendor invoice. For the invoice to be successfully processed through posting, either: 
- A user who has override privileges must resubmit the invoice, or
- The invoice must be changed so that a different cash account is used, or
- The cash control balance must be changed.
- If the user does have override privileges,  the invoice will be automatically posted as part of the workflow process.

### When workflow is not set up for autoposting
When using cash control functionality with Accounts payable vendor invoice workflow, and workflow is not set up for autoposting, then when the user submits an invoice to workflow:
- If the threshold will be exceeded and the user does not have privileges to override the cash control limit, an error message appears and the invoice cannot be submitted to workflow. For the invoice to be successfully submitted, either: 
- A user who has override privileges must resubmit the invoice, or
- The invoice must be changed so that a different cash account is used, or
- The cash control balance must be changed.
- If the user does have override privileges, the invoice can be submitted to workflow.
- Cash control validation is performed once again when the invoice is posted (because cash balances might have changed between the time that the invoice was submitted to workflow and the time of invoice posting).



