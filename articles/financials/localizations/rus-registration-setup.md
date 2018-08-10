# Set up parameters for advance holders 


1.  Click **Accounts payable** \> **Setup** \> **Accounts payable parameters**.


2.  Click **Advance holders**, and then in the **Advance holders** area, in the **Posting profile** field, select the default profile to complete transactions for advance holders.
    

    > [!NOTE]
    > <P>For more information, see "Set up posting profiles for accounting vouchers".</P>



3.  Select the **Set default advance holder** check box to set the current user as the advance holder.

4.  Select the **Advance holder sorting** check box to display the advance holders at the beginning of the list in the **Advance holders** form.

5.  Select the **Issue when balance is open** check box to allow issue of a cash advance to an advance holder who has an open positive balance.

6.  Select the **Settlement by profile** check box to settle transactions only with an identical posting profile.

7.  In the **Name** field under the **Balance closing via cash** field group, select the cash slip journal code. This journal code is used to generate cash disbursement slips and reimbursement slips when closing an advance holder's balances through cash.
    

    > [!NOTE]
    > <P>All journals are of the type <STRONG>Cash</STRONG>.</P>



8.  In the **Cash** field, select the cash account to determine the vouchers that are used for closing the balances for the advance holder.

9.  In the **Name** field under the **Balance closing via bank** field group, select the journal code for transactions to close the balances through a bank.

10. In the **Account** type field, select **Bank** to close the balances for an advance holder through a bank.

11. In the **Account** field, select the bank account code to close the balances for an advance holder through a bank.

12. Press CTRL+S or close the form.


## Set up an advance holder group 

You must create an advance holder group in order to group advance holders. For example, you can group advance holders by vouchers calculated in a single account.

1.  Click **Accounts payable** \> **Setup** \> **Advance holders** \> **Advance holder groups**.

2.  Press CTRL+N.

3.  In the **Group** field, enter the code for the new group.

4.  In the **Description** field, enter the description of the advance holder group.

5.  In the **Offset account** field, select the general ledger offset account to be used for the advance holder group.

6.  Press CTRL+S or close the form.


## Set up posting profiles for accounting vouchers 


You can set up the following posting profiles for an account of operations:


  - One ledger account for all advance holders.

  - A separate ledger account for each group of advance holders.

  - A separate ledger account for each advance holder.

<!-- end list -->

1.  Click **Accounts payable** \> **Setup** \> **Advance holders** \> **Employee posting profiles**.

2.  Click the **Overview** tab, and press CTRL+N.

3.  In the **Posting profile** field, enter the profile ID of the profile being processed.

4.  In the **Description** field, enter the description of the posting profile.

5.  Click the **Ledger accounts** tab.

6.  In the **Valid for** field, select the level of grouping for setting up the posting profile from the following options:
    
      - **Table** – This option is set for only one advance holder.
    
      - **Group** – This option is set for a group of advance holders.
    
      - **All** – This option is set for all advance holders.

7.  In the **Reference** field, select the corresponding reference.
    

    > [!NOTE]
    > <P>You can select this field only if you select <STRONG>Table</STRONG> or <STRONG>Group</STRONG> in the <STRONG>Valid for</STRONG> field.</P>



8.  In the **Summary account** field, select the account to reflect transactions for the advance holders.

9.  Press CTRL+S or close the form.


## Set up employee posting profiles for dimensions control for settlements 


Use this procedure to set up employee posting profiles for dimension control for settlements by using the **Employee posting profiles** form. Set up advance holder posting profiles for accruals and closing payment operations. These posting profiles can be adjusted for advance holder operation of payments and debts by using a dimension set for control for settlements.

1.  Click **Accounts payable** \> **Setup** \> **Advance holders** \> **Employee posting profiles**.

2.  Create a new employee posting profile. For more information, see "Set up posting profiles for accounting vouchers".

3.  Click the **Table restrictions** FastTab.

4.  In the **Allow empty dimension value** field, select the condition under which settlements that are related to accruals and closing payment operations can be processed if dimension values are not specified. The following options are available:
    
      - **No** – Transactions are not settled, whether the dimension values are specified or not.
    
      - **Auto** - Automatic transactions are settled, whether the dimension values are specified or not.
    
      - **Manual** – Manual transactions are settled, whether the dimension values are specified or not.
    
      - **Always** – All transactions are settled, whether the dimension values are specified or not.
    

    > [!NOTE]
    > <P>This parameter lets you ignore the setting of dimensions when individual transactions are created.</P>



5.  Click the **Setup** FastTab.

6.  In the **Set** field, select the dimension focus for settlement control.
    

    > [!NOTE]
    > <P>The specified dimension set indicates that dimension control is activated.</P>



## Set up the terms of payment 


You must set up the terms of payment when you register the purchase of goods from a vendor through an advance holder. The advance holder makes the purchase.


1.  Click **Accounts payable** \> **Setup** \> **Payment** \> **Terms of payment**.

2.  Click the **Overview** tab, and then press CTRL+N.

3.  In the **Terms of payment** field, enter the code for the terms of payment.

4.  In the **Description** field, enter the description for the terms of payment.

5.  Click the **Setup** tab.

6.  In the **Payment method** field, select **C.O.D.**

7.  Select the **Cash payment** check box.

8.  Select the **From advance holder** check box.

9.  Press CTRL+S or close the form.


## Set up the per diem expense rates 


Expense rates are used to generate an advance report for per diem expenses, and for automatic calculation of standard and over-rate amounts.


1.  Click Click **Accounts payable** \> **Setup** \> **Advance holders** \> **Expense rates**.

2.  Press CTRL+N to create an expense record.

3.  In the **Expense** field, enter the expense code.

4.  In the **Description** field, enter the description for the expense code.

5.  In the **Currency** field, select the currency code in which operations for this expense are registered.

6.  In the **Rate** field, enter the standard established value for this expense.

7.  Click the **Setup** tab.

8.  In the **Posting over norm** field, select the over-norm expense posting operation.

9.  In the **Main account** field under the **Rate** field group, select the accounting statement to reflect normal charges.

10. In the **Main account** field under the **Over rate** field group, select the accounting statement to reflect over-rate charges.

11. In the **Sales tax group** field under the **Sales tax** field group and the **Taxes over norm** field group, select the sales tax group for calculating sales tax for sale and purchase on normal and over-rate amounts.

12. In the **Item sales tax group** field under the **Sales tax** field group and the **Taxes over norm** field group, select the item sales tax group for calculating sales tax for an item on normal and over-rate amounts.

13. If the amounts include sales tax, select the **Amounts includes. sales tax** check box under the **Sales tax** field group and the **Taxes over norm** field group.

14. Click the **Dimensions** tab.

15. In the **Department**, **Cost center**, and **Purpose** fields, select the transaction dimension from the corresponding dimensions form.

16. Press CTRL+S or close the form.



## About worker table numbers for advance holders 


A worker can be an employee or a contractor, and can hold several positions in an organization. An employee or a contractor can also be an advance holder who is accountable for the expense amount that is provided by the organization. To specify a worker as an advance holder, you must enter a unique worker ID in the **Worker ID** field in the **Worker** form. You must also select the **Advance holder** check box in the **Advance holders** form to indicate that the selected worker is an advance holder.

Transactions for these workers can be posted by using advance holder accounts. The worker ID that is specified for each advance holder can be used to track all advance holder transactions. This number is retrieved as an account number for advance holder transactions in the **General journals** and **Advance holder transactions** forms.


## Set up a worker table number for an advance holder 

Use this procedure to set up a worker table number for a worker. You can view the details of employees in the **Employment history** form, and you can identify the employees as advance holders.

1.  Click **Human resources** \> **Common** \> **Workers** \> **Workers**.

2.  On the **Action Pane**, click **Hire new worker**.

3.  Enter the first, middle, and last names of the person who you are hiring to fill the position. 

4.  In the **Worker ID** field, enter the unique internal number that is used to identify advance holders.

5.  In the **Worker type** field, select the type of worker.

6.  In the **Employment start date** and **Employment end date** fields, enter the start date and end date of the worker’s employment.

7.  Click **Employment history** to view the details of employees.

8.  Close the form.

9.  Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance holders**.

10. Select a worker record, and then select the **Advance holder** check box to specify that the worker is an advance holder.


## Set up the advance holder 


1.  Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance holders**.
    

    > [!NOTE]
    > <P>You cannot add or delete employees in the <STRONG>Advance holders</STRONG> form.</P>



2.  Select the **Advance holder** check box to activate the employee as an advance holder.

3.  In the **Group** field, select the advance holder group to identify the advance holder in the group of advance holders.
    

    > [!NOTE]
    > <P>If the <STRONG>Advance holder sorting</STRONG> check box is selected in the <STRONG>Accounts payable parameters</STRONG> form, the advance holders are displayed at the beginning of the list in the <STRONG>Advance holders</STRONG> form.</P>



## Set up advance holders 

Use this procedure to set up advance holders from the directory of workers.

1.  Click **Accounts payable** \> **Common** \> **Advance holders** \> **Advance holders**.
    

    > [!NOTE]
    > <P>You cannot add or delete employees in the <STRONG>Advance holders</STRONG> form. You can create employees in the <STRONG>Worker</STRONG> form. In the <STRONG>Employee posting profiles</STRONG> form, you can set up the employee posting profile that is used to post advance holder balances.</P>



2.  Select the **Advance holder** check box to mark a worker as an advance holder.

3.  In the **Group** field, select the advance holder group that the worker belongs to. 
    

    > [!NOTE]
    > <P>If the <STRONG>Advance holder sorting</STRONG> check box is selected in the <STRONG>Accounts payable parameters</STRONG> form, the advance holders are displayed first in the list in the <STRONG>Advance holders</STRONG> form. You can also select the default employee posting profile in the <STRONG>Posting profile</STRONG> field.</P>
    
