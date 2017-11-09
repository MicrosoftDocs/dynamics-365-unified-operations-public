You can reverse a fixed asset transaction, reverse direct and indirect taxes for
the transaction, and update general ledger accounts. Information about the
updated asset is displayed in the **Asset group balances** form for the selected
tax layer value model and depreciation.

You can reverse fixed asset acquisitions or acquisition adjustment transactions
on which VAT were calculated. The posted VAT tax codes should also be reversed
along with the fixed asset transaction entries. If the settlement process is
already run for the original transaction period, the tax amounts which were
posted to the VAT recoverable account at the time of posting the original
transaction should be reversed to the VAT payable account. All the indirect
taxes for India, other than the VAT tax type, that is calculated and posted to
the fixed asset at the time of posting the acquisition or acquisition adjustment
transaction, are reversed as is when a fixed asset acquisition or acquisition
adjustment transaction is reversed.

The **Companies Act depreciation** and the **Income tax Act depreciation** check
boxes must be selected in the **General ledger parameters** form.

*gls\_topic-not-updated-for-ax62*

>   Fixed assets Select a fixed asset line, and click Books \> Value models.

>   Select the value model with a tax layer in the **Value model** field.

>   Click **Transactions** to open the **Fixed asset transactions** form.

>   Select the transaction posted for acquisition to activate the **Reverse
>   transaction**.

>   Click **Reverse transaction** to open the **Transaction reversal** form.

>   Enter the **Reversal posting date**.

>   Click **OK** to reverse the transactions.

>   Value models

**Example 1**

You can post multiple journals to account for the acquisition of fixed assets.

| Journal  | Value model | Fixed asset group | Fixed asset number | Amount    | Date of acquisition |
|----------|-------------|-------------------|--------------------|-----------|---------------------|
| 0001\_FA | VM1         | FAG1              | FA-001             | 75,000.00 | 01/01/2009          |
| 0002\_FA | VM1         | FAG2              | FA-002             | 65,000.00 | 01/01/2009          |
| 0003\_FA | VM1         | FAG3              | FA-003             | 35,000.00 | 01/01/2009          |

When you post the journals for value model 1 (VM1), the **Asset group balances**
form displays the following details:

>   The amount INR 175,000.00 (75,000.00 + 65,000.00 + 35,000.00) is displayed
>   in the **Acquisition** field.

>   If you reverse the fixed asset FA-002 using the transaction reversal
>   functionality, the **Acquisition** field in the **Asset group balances**
>   form must display the amount as INR 110,000.00 (75,000.00 + 35,000.00).

>   The value of the reversed transaction must not be displayed in the **Asset
>   group balances** form.

**Example 2**

When the acquisition transaction that was reversed earlier is revoked, the
revoked transaction appears again in the **Asset group balances** form.

With reference to Example 1, if you revoke the reversal of fixed asset FA-002
using transaction reversal, the **Acquisition** field in the **Asset group
balances** form displays the amount as INR 175,000.00 (75,000.00 + 65,000.00 +
35,000.00)

>   The revoked transaction is updated back in the **Asset group balances**
>   form.
