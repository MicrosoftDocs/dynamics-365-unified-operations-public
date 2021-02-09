# TDS parameter activation

Activate the parameters for the TDS feature in the **General** **ledger** **parameters** form.

Follow the steps below to set up TDS parameters.

[![Direct taxes (tab)](./media/apac-ind-TDS-1.png)](./media/apac-ind-TDS-1.png)

​                          

1. Click the **Direct** **taxes** tab. Under the **Tax** **Deducted** **at** **Source** field group, select the **Activate** **TDS** check box to activate the TDS functionality. Select the **Activate** **TDS** check box to activate the forms and fields for the TDS functionality.

2. Select the **Invoice** check box to activate fields to calculate and deduct TDS at the invoice-level.

3. Select the **Payment** check box to activate fields to calculate and deduct TDS at the payment-level.
4. Under the **Overlook** **threshold** field group, in the **Exceeding** **threshold** **limit** field, select the type of message to display if the cumulative transaction amount exceeds the threshold limit for the first time when the **Overlook** **threshold** check box is selected for the TDS component attached to the withholding tax group. The options are:

-  **None**: No message is displayed.

-  **Error**: An error message is displayed and the transaction cannot be posted.

-  **Warning**: A warning message is displayed. Click **Yes** to calculate TDS on the selected transaction amount. Click **No** to cancel the posting and calculation of TDS. If you click **No**, the transaction can be posted only when the **Overlook** **threshold** check box is cleared for the TDS component attached to the withholding tax group. TDS will be calculated for the selected transaction along with all transactions for which TDS has not been deducted earlier.

5. Click the **Number** **sequences** tab. For **Withholding** **tax** **payment** reference type in the **Reference** field, select the number sequence code in the **Number** **sequence** **code** field. The number sequence code is used to generate voucher numbers for the periodic TDS settlement process.

[![Number sequences (tab)](./media/apac-ind-TDS-2.png)](./media/apac-ind-TDS-2.png)



>   [!Note]
>
>   Click Tax > Declarations  > Withholding tax > Withholding tax payment to run the periodic TDS settlement  process.  

6.  Close the form.

