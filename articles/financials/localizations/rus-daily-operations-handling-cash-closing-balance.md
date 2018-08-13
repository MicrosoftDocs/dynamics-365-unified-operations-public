---
# required metadata
title: Create and post vendor invoices with advance holder details 
description: This topic provides information on daily operations like handing cash and closing balance for advance holders for Russia. 
author: ShylaThompson
manager: AnnBe
ms.date: 10/28/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 
			
# optional metadata
# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1
---


# Create and post vendor invoices with advance holder details 


Use this procedure to create and post vendor invoices with advance holder details. The advance holder balances are posted to the employee balance account instead of the vendor balance account.

1.  Click **Accounts payable** \> **Common** \> **Purchase orders** \> **All purchase orders**.

2.  Press CTRL+N or click **Purchase order** to create a purchase order. For more information, see [Create a purchase order](../supply-chain/procurement/tasks/create-purchase-order).

3.  In the **Purchase order** form, on the **Action Pane**, click **Header view**, and then click the **Price and discount** FastTab.

4.  In the **Terms of payment** field, select the payment term. 
    

    > [!NOTE]
    > <P>Select a payment term that has the <STRONG>From advance holder</STRONG> check box selected in the <STRONG>Terms of payment</STRONG> form.</P>



5.  In the **Advance holder** field, select the advance holder for the purchase order.

6.  Click **Purchase** \> **Confirm** to confirm the purchase order.

7.  Click **Invoice** \> **Invoice** to create a vendor invoice for the purchase order.

8.  In the **Vendor invoice** form, in the **Invoice identification** field group, in the **Number** field, enter the invoice number.

9.  Click **Post** \> **Post** to select the posting settings and generate the invoice.
    
    You can view two vendor transactions with opposite amounts in the **Vendor transactions** form. 

10. Close the form.

11. Click **Accounts payable** \> **Inquiries** \> **Advance holders** \> **Transactions**. In the **Advance holder transactions** form, you can view one advance holder transaction. 

12. Click **Voucher** to open the **Voucher transactions** form. The vendor balance account is replaced by the employee balance account, and the **Posting type** field is updated to **Employee balance**.



## Close balances for an advance holder 


You can close balances for an advance holder in one of the following ways:

  - Close via cash

  - Close via bank



### Closing via cash

1.  Click **Accounts payable** \> **Inquiries** \> **Advance holders** \> **Balance**.

2.  In the **To date** field, enter the date to obtain advance holder balances.

3.  Click **Balance closing**, and then select **Close via cash**.

4.  In the **Date of payment** field, enter the date of payment.

5.  In the **Amount to be transferred** field, enter the balance amount while closing.
    

    > [!NOTE]
    > <P>The amount indicated in the <STRONG>Amount</STRONG> field in the <STRONG>Balance</STRONG> form is displayed by default.</P>



6.  Select the **Automatic** check box to create and post the slip journal automatically.
    

    > [!NOTE]
    > <P>If the <STRONG>Automatic</STRONG> check box is cleared, a journal will be created automatically, and the journal number is displayed. This journal must be posted manually.</P>



7.  Click **OK** to generate the slip journal.
    

    > [!NOTE]
    > <P>After the slip journal is processed, either a disbursement slip (if the amount in the <STRONG>Amount to be transferred</STRONG> field is negative) will be generated, or a reimbursement slip (if the amount in the <STRONG>Amount to be transferred</STRONG> field is positive) will be generated for the advance holder when the balances are closed.</P>



8.  Press CTRL+S or close the form.

### Closing via bank

The procedure for closing balances through a bank is similar to closing through cash. You can set up the code for the journal and the bank on the **Advance holders** tab in the **Accounts payable parameters** form.


> [!NOTE]
> <P>In the <STRONG>Balance</STRONG> form, you must click <STRONG>Balance closing</STRONG>, and then select <STRONG>Close via bank</STRONG> to open the <STRONG>Close via bank</STRONG> report.</P>


## Print an advance report 


Use this procedure to print an advance report. You can print an advance report after an advance invoice that is issued to an advance holder is settled.

1.  Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance reports**.

2.  Create and post an advance report.
    

    > [!NOTE]
    > <P>The amounts in the <STRONG>Advance reports</STRONG> form are recalculated on the date when the payment journal for the advance holder is posted.</P>



3.  Click **Print** to open the **Advance report** form.

4.  Click **OK** to print the advance report in Microsoft Excel format.


## Settle advance holder balances 


Use this procedure to settle advance holder balances. When you settle advance holder balances, journal entries for closing the advance holder balances are created in the general journal.

You can close balances for an advance holder in the following ways:

  - Close through cash. 
  - Close through a bank. 

### Close through cash

1.  Click **Accounts payable** \> **Inquiries** \> **Advance holders** \> **Balance**.

2.  In the **To date** field, enter the date to obtain advance holder balances.

3.  Click **Balance closing**, and then select **Close via cash**.

4.  In the **Date of payment** field, enter the date of payment.

5.  In the **Amount to be transferred.** field, enter the balance amount while closing.
    

    > [!NOTE]
    > <P>The amount that is indicated in the <STRONG>Amount</STRONG> field in the <STRONG>Balance</STRONG> form is displayed by default.</P>



6.  Select the **Automatic** check box to create and post the slip journal automatically.
    

    > [!NOTE]
    > <P>If the <STRONG>Automatic</STRONG> check box is cleared, a journal is created automatically, and the journal number is displayed. You can also enter advance holder transactions manually by using the general journal or the slip journal.</P>



7.  Click **OK** to generate the slip journal.
    

    > [!NOTE]
    > <P>After the slip journal is processed, if the amount in the <STRONG>Amount to be transferred.</STRONG> field is negative, a disbursement slip is generated for the advance holder when the balances are closed. If the amount in the <STRONG>Amount to be transferred.</STRONG> field is positive, a reimbursement slip is generated. For more information, see <A href="./eeur-generate-a-cash-reimbursement-and-disbursement-slip.md">(EEUR) Generate a cash reimbursement and disbursement slip</A>.</P>



### Close through a bank

The procedure for closing balances through a bank is similar to the procedure for closing through cash. You can set up the code for the journal and the bank in the **Advance holders** area in the **Accounts payable parameters** form.


> [!NOTE]
> <P>In the <STRONG>Balance</STRONG> form, you must click <STRONG>Balance closing</STRONG>, and then select <STRONG>Close via bank</STRONG> to open the <STRONG>Close via bank</STRONG> form.</P>

 

## Complete the settlement for an advance holder 


You can complete a manual settlement or periodic settlement for an advance holder. If you clear the **Automatic settlement** check box in the **Accounts payable parameters** form, you must settle the posting or closing transactions manually, or by using the periodic settlement function.

### Settle advance holder transactions manually

Use this procedure to settle advance holder transactions manually.

1.  Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance holders**.

2.  Select an advance holder.

3.  Click **Functions** \> **Settle open transactions** to open the **Open-transaction editing in several currencies** form. The upper pane displays debit transactions for an advance holder, and the lower pane displays credit transactions.

4.  In the upper and lower panes, select the **Mark** check box to select the transactions. The **Balance** field displays the balances after the transactions are settled.

5.  Click **Update** to complete the settlement.

6.  Close the form.

7.  In the **Advance holders** form, click **Settlements** to open the **Transaction settlements** form. You can verify the completed settlements in this form.
    

    > [!NOTE]
    > <P>If exchange adjustments occur when advance holder transactions are settled, exchange adjustment transactions are generated from the settlement. The exchange rate adjustment is displayed in the <STRONG>Exchange rate adjustment amount</STRONG> field in the <STRONG>Transaction settlements</STRONG> form.</P>



8.  Close the form.

9.  Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance reports**.

10. Double-click the advance report that is created for the selected advance holder.

11. On the **Financials** tab, click **View distributions** to verify that the distribution of the expense amount is correct.

### Settle advance holder transactions periodically

Use this procedure to settle advance holder transactions periodically. When you use the periodic settlement function, all open transactions are settled in chronological order.

1.  Click **Accounts payable** \> **Periodic** \> **Advance holders** \> **Periodic settlement**.

2.  In the **Date of transaction.** field, select the advance holder transaction date. All transactions that are posted before this date are settled.

3.  Select the **Settlement by profile** check box to settle transactions that have identical posting profiles.

4.  Click **Select** to open the supplementary request setup to search for transactions for settlement.

5.  Click **OK** to settle the transactions.

### Cancel a periodic settlement

Use this procedure to cancel a periodic settlement for advance holder transactions.

1.  Click **Accounts payable** \> **Periodic** \> **Advance holders** \> **Periodic reverse**.

2.  In the **Date of transaction.** field, select the advance holder transaction date. All transactions that are settled before this date are reversed.

3.  Click **Select** to open the supplementary request setup to search for transactions to cancel the settlements for.

4.  Click **OK** to cancel the periodic settlement.

