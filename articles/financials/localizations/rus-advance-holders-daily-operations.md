---
# required metadata
title: Daily operations for advance holders in Russia
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

# Daily operations for advance holders in Russia

[!include [banner](../includes/banner.md)]

## Create and post disbursement slips for advance holders 

Use this procedure to create and post disbursement slips with advance holder details. The advance holder balances are posted to the related employee balance account.

1.  Click **Cash and bank management** \> **Cash transactions** \> **Slip journal**.

2.  Select **New** to create a slip journal. For more information, see **Register reimbursement or disbursement slips** chapter in [Cash - Setup and daily cash operations](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/rus-set-daily-cash-op/articles/financials/localizations/rus-setup-daily-cash-operations.md).

3.  In the **Lines** form, select **Advance holder** in **Offset account type** column, then in **Offset account** column select an advance holder and in **Credit** coulmn enter the amount.

4. Approve and post the disbursement slip. For more information, see **Post a cash voucher with cash reimbursements and cash disbursements** chapter in [Cash - Setup and daily cash operations](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/rus-set-daily-cash-op/articles/financials/localizations/rus-setup-daily-cash-operations.md).

5. To inqure the related transactions and advance holder balance select **Transactions** or **Balance** forms in **Accounts payable** \> **Advance holders** \> **Advance holders** for the selected employee.

## Create and post vendor invoices with advance holder details 

Use this procedure to create and post vendor invoices with advance holder details. The advance holder balances are posted to the employee balance account instead of the vendor balance account.

1.  Click **Accounts payable** \> **Purchase orders** \> **All purchase orders**.

2.  Select **New** to create a purchase order. For more information, see [Create a purchase order](../../supply-chain/procurement/tasks/create-purchase-order.md).

3.  In the **Purchase order** form, select **Header** view mode, and then click the **Price and discount** FastTab.

4.  In the **Terms of payment** field, select the payment term. 
    
    > [!NOTE]
    > <P>Select a payment term that has the <STRONG>From advance holder</STRONG> check box selected in the <STRONG>Terms of payment</STRONG> form.</P>

5.  In the **Advance holder** field, select the advance holder for the purchase order.

6.  Enter all the required lines details and click **Purchase** \> **Actions** \> **Confirm** to confirm the purchase order.

7.  Click **Invoice** \> **Generate** \> **Invoice** to create a vendor invoice for the purchase order.

8.  In the **Vendor invoice** form, in the **Invoice identification** field group, in the **Number** field, enter the invoice number.

9.  Click **Post** to post the invoice.and close the form.

10. Click **Accounts payable** \> **Inquiries and reports** \> **Advance holders inquires and reports** \> **Transactions** to view related advance holder transactions. 

11. Click **Voucher** to open the **Voucher transactions** form. The vendor balance account is replaced by the employee balance account, and the **Posting type** field is updated to **Employee balance**.


## Create and post advance reports 

Use this procedure to create, modify, post, inquire and print advance reports.

### Create advance report

1.  Click **Accounts payable** \> **Advance holders** \> **Advance report**.

2. Select **New** to create an advance report. Alternatively, you can create a new advance report directly from **Advance holders** form - select **New** \> **Advance report**.

3. Enter advance report date in **Date** field

4. Advance report number will be automatically generated in **Advance report** field based on the number sequence defined in the parameters.

5. Select an advance holder in **Employee number** field group.

6. Enter the purpose of the advance in **Advance purpose**  field

7. In **Header** view mode select **Options** FastTab to define confirmation dates and **Officials** FastTab to define responcible managers.

### Generate advance report lines from expenses

1. Click **Accounts payable** \> **Advance holders** \> **Advance report** and swith to **Lines** view mode.

2. Click **Copy from expends** to open **Create advance report lines** form. In this form you can see all the expense types previously defined in the parameters.

3. Select an expense line. In the **Date** field, enter the date of the transaction.

4. In the **Document number** field, enter the number of the confirmed disbursement voucher.
   > [!NOTE]
   > <P>The entries in the <STRONG>Document name</STRONG>, <STRONG>Rate</STRONG>, and <STRONG>Currency</STRONG> fields are automatically displayed from the expense rates dictionary.</P>

5. In the **Quantity of days** field, enter the number of days of the business trip.

6. IIn the **To weekday** field, enter the daily expense amount.
   > [!NOTE]
   > <P>The <STRONG>Total amount</STRONG> field displays the total expense amount.</P>

7. Click **Save** to transfer the entries to the **Advance report** form.
   > [!NOTE]
   > <P>The entry in the <STRONG>Ledger account</STRONG> field is displayed according to the expense rate posting setup. If the actual expense is more than the established rates, then a supplementary line for the excess amount is created when the expenses are transferred to the advance report. In this situation, the <STRONG>Over rate</STRONG> check box is selected automatically. The <STRONG>Line type</STRONG> field of the advance report that is generated by using the <STRONG>Copy from expends</STRONG> function displays the value <STRONG>Expense</STRONG>.</P>

## Closing balances for an advance holder 

You can close balances for an advance holder via cash or bank.

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
    > <P>After the slip journal is processed, if the amount in the <STRONG>Amount to be transferred.</STRONG> field is negative, a disbursement slip is generated for the advance holder when the balances are closed. If the amount in the <STRONG>Amount to be transferred.</STRONG> field is positive, a reimbursement slip is generated.</P>



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

