# (EEUR) Create and post vendor invoices with advance holder details 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2_

Use this procedure to create and post vendor invoices with advance holder details. The advance holder balances are posted to the employee balance account instead of the vendor balance account.

1.  Click **Accounts payable** \> **Common** \> **Purchase orders** \> **All purchase orders**.

2.  Press CTRL+N or click **Purchase order** to create a purchase order. For more information, see [Create a purchase order](create-a-purchase-order.md) and [(EEUR) Purchase orders (modified form)](https://technet.microsoft.com/en-us/library/jj710700\(v=ax.60\)).

3.  In the **Purchase order** form, on the **Action Pane**, click **Header view**, and then click the **Price and discount** FastTab.

4.  In the **Terms of payment** field, select the payment term. For more information, see [(EEUR) Terms of payment (modified form)](https://technet.microsoft.com/en-us/library/jj911004\(v=ax.60\)).
    

    > [!NOTE]
    > <P>Select a payment term that has the <STRONG>From advance holder</STRONG> check box selected in the <STRONG>Terms of payment</STRONG> form.</P>



5.  In the **Advance holder** field, select the advance holder for the purchase order.

6.  Click **Purchase** \> **Confirm** to confirm the purchase order.

7.  Click **Invoice** \> **Invoice** to create a vendor invoice for the purchase order.

8.  In the **Vendor invoice** form, in the **Invoice identification** field group, in the **Number** field, enter the invoice number.

9.  Click **Post** \> **Post** to select the posting settings and generate the invoice.
    
    You can view two vendor transactions with opposite amounts in the **Vendor transactions** form. For more information, see [(EEUR) Vendor transactions (modified form)](https://technet.microsoft.com/en-us/library/jj730985\(v=ax.60\)).

10. Close the form.

11. Click **Accounts payable** \> **Inquiries** \> **Advance holders** \> **Transactions**. In the **Advance holder transactions** form, you can view one advance holder transaction. For more information, see [(EEUR) Advance holder transactions (form)](https://technet.microsoft.com/en-us/library/jj910968\(v=ax.60\)).

12. Click **Voucher** to open the **Voucher transactions** form. The vendor balance account is replaced by the employee balance account, and the **Posting type** field is updated to **Employee balance**. For more information, see [Voucher transactions (form)](https://technet.microsoft.com/en-us/library/aa583215\(v=ax.60\)).

## See also

[(EEUR) Settle advance holder balances](eeur-settle-advance-holder-balances.md)

[(EEUR) Vendor invoice (modified form)](https://technet.microsoft.com/en-us/library/jj862346\(v=ax.60\))

  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

# (RUS) Close balances for an advance holder 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2_

You can close balances for an advance holder in one of the following ways:

  - Close via cash

  - Close via bank


> [!NOTE]
> <P>This topic has not been fully updated for Microsoft Dynamics AX 2012 R2.</P>



## Closing via cash

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

## Closing via bank

The procedure for closing balances through a bank is similar to closing through cash. You can set up the code for the journal and the bank on the **Advance holders** tab in the **Accounts payable parameters** form.


> [!NOTE]
> <P>In the <STRONG>Balance</STRONG> form, you must click <STRONG>Balance closing</STRONG>, and then select <STRONG>Close via bank</STRONG> to open the <STRONG>Close via bank</STRONG> report.</P>


  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

# (RUS) Print an advance report 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2_

Use this procedure to print an advance report. You can print an advance report after an advance invoice that is issued to an advance holder is settled.

1.  Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance reports**.

2.  Create and post an advance report.
    

    > [!NOTE]
    > <P>The amounts in the <STRONG>Advance reports</STRONG> form are recalculated on the date when the payment journal for the advance holder is posted.</P>



3.  Click **Print** to open the **Advance report** form.

4.  Click **OK** to print the advance report in Microsoft Excel format.

## See also

[(RUS) Advance reports (form)](https://technet.microsoft.com/en-us/library/jj733237\(v=ax.60\))

  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

# (EEUR) Settle advance holder balances 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2_

Use this procedure to settle advance holder balances. When you settle advance holder balances, journal entries for closing the advance holder balances are created in the general journal.

You can close balances for an advance holder in the following ways:

  - Close through cash. For more information, see [(RUS) Close via cash (form)](https://technet.microsoft.com/en-us/library/jj711592\(v=ax.60\)).

  - Close through a bank. For more information, see [(RUS) Close via bank (form)](https://technet.microsoft.com/en-us/library/jj665454\(v=ax.60\)).

## Close through cash

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
    > <P>After the slip journal is processed, if the amount in the <STRONG>Amount to be transferred.</STRONG> field is negative, a disbursement slip is generated for the advance holder when the balances are closed. If the amount in the <STRONG>Amount to be transferred.</STRONG> field is positive, a reimbursement slip is generated. For more information, see <A href="eeur-generate-a-cash-reimbursement-and-disbursement-slip.md">(EEUR) Generate a cash reimbursement and disbursement slip</A>.</P>



## Close through a bank

The procedure for closing balances through a bank is similar to the procedure for closing through cash. You can set up the code for the journal and the bank in the **Advance holders** area in the **Accounts payable parameters** form.


> [!NOTE]
> <P>In the <STRONG>Balance</STRONG> form, you must click <STRONG>Balance closing</STRONG>, and then select <STRONG>Close via bank</STRONG> to open the <STRONG>Close via bank</STRONG> form.</P>



## See also

[(EEUR) Create and post vendor invoices with advance holder details](eeur-create-and-post-vendor-invoices-with-advance-holder-details.md)

[(EEUR) Accounts payable parameters (modified form)](https://technet.microsoft.com/en-us/library/jj720358\(v=ax.60\))

  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

# (RUS) Complete the settlement for an advance holder 


_**Applies To:** Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2_

You can complete a manual settlement or periodic settlement for an advance holder. If you clear the **Automatic settlement** check box in the **Accounts payable parameters** form, you must settle the posting or closing transactions manually, or by using the periodic settlement function.

## Settle advance holder transactions manually

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

## Settle advance holder transactions periodically

Use this procedure to settle advance holder transactions periodically. When you use the periodic settlement function, all open transactions are settled in chronological order.

1.  Click **Accounts payable** \> **Periodic** \> **Advance holders** \> **Periodic settlement**.

2.  In the **Date of transaction.** field, select the advance holder transaction date. All transactions that are posted before this date are settled.

3.  Select the **Settlement by profile** check box to settle transactions that have identical posting profiles.

4.  Click **Select** to open the supplementary request setup to search for transactions for settlement.

5.  Click **OK** to settle the transactions.

## Cancel a periodic settlement

Use this procedure to cancel a periodic settlement for advance holder transactions.

1.  Click **Accounts payable** \> **Periodic** \> **Advance holders** \> **Periodic reverse**.

2.  In the **Date of transaction.** field, select the advance holder transaction date. All transactions that are settled before this date are reversed.

3.  Click **Select** to open the supplementary request setup to search for transactions to cancel the settlements for.

4.  Click **OK** to cancel the periodic settlement.

## See also

[(RUS) Periodic reverse (form)](https://technet.microsoft.com/en-us/library/jj678637\(v=ax.60\))

[(RUS) Advance holders (form)](https://technet.microsoft.com/en-us/library/jj665294\(v=ax.60\))

[(RUS) Transaction settlements (form)](https://technet.microsoft.com/en-us/library/jj711614\(v=ax.60\))

[(RUS) Accounts payable parameters (modified form)](https://technet.microsoft.com/en-us/library/jj923609\(v=ax.60\))

  
**Announcements:** To see known issues and recent fixes, use [Issue search](http://go.microsoft.com/fwlink/?linkid=389258) in [Microsoft Dynamics Lifecycle Services](http://go.microsoft.com/fwlink/?linkid=306505) (LCS).

