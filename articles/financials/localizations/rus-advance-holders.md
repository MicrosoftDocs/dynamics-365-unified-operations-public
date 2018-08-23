---
# required metadata
title: Advance holders for Russia
description: This topic provides information about registration and set up for advance holders for Russia. 
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


# Advance holders for Russia
[!include [banner](../includes/banner.md)]

# Set up parameters for advance holders 

1.  Click **Accounts payable** \> **Setup** \> **Accounts payable parameters**.
2.  Click **Advance holders**, and then in the **Advance holders** area, in the **Posting profile** field, select the default profile to complete transactions for advance holders.
    
    > [!NOTE]
    > For more information, see "Set up posting profiles for accounting vouchers".


3.  Select the **Set default advance holder** check box to set the current user as the advance holder.

4.  Select the **Advance holder sorting** check box to display the advance holders at the beginning of the list in the **Advance holders** page.

5.  Select the **Issue when balance is open** check box to allow issue of a cash advance to an advance holder who has an open positive balance.

6.  Select the **Automatic settlement** check box if automatic transactions settlement is required.

7.  Select the **Settlement by profile** check box to settle transactions only with an identical posting profile.

8.  In the **Name** field under the **Balance closing via cash** field group, select the cash slip journal code. This journal code is used to generate cash disbursement slips and reimbursement slips when closing an advance holder's balances through cash.
    

    > [!NOTE]
    > All journals are of the type **Cash**.

9.  In the **Cash** field, select the cash account to determine the vouchers that are used for closing the balances for the advance holder.

10.  In the **Name** field under the **Balance closing via bank** field group, select the journal code for transactions to close the balances through a bank.

11. In the **Account** type field, select **Bank** to close the balances for an advance holder through a bank.

12. In the **Account** field, select the bank account code to close the balances for an advance holder through a bank.

13. Click **Save** button or close the page.


## Set up an advance holder group 

You must create an advance holder group in order to group advance holders. For example, you can group advance holders by vouchers calculated in a single account.

1.  Click **Accounts payable** \> **Setup** \> **Advance holders** \> **Advance holder groups**.

2.  Click **New** button to create a new group or press **Edit** button to adjust an existing group.

3.  In the **Group** field, enter the code for the new group.

4.  In the **Description** field, enter the description of the advance holder group.

5.  In the **Offset account** field, select the general ledger offset account to be used for the advance holder group.

6.  Click **Save** button or close the form.


## Set up posting profiles for accounting vouchers 


You can set up the following posting profiles for an account of operations:

  - One ledger account for all advance holders.
  - A separate ledger account for each group of advance holders.
  - A separate ledger account for each advance holder.


1.  Click **Accounts payable** \> **Setup** \> **Advance holders** \> **Employee posting profiles**.

2.  Click **New** button to create a new posting frofile or press **Edit** button to adjust an existing posting profile.

3.  In the **Posting profile** field, enter the profile ID of the profile being processed.

4.  In the **Description** field, enter the description of the posting profile.

5.  Click the **Table restrictions** FastTab.

6.  In the **Allow empty dimension value** field, select the condition under which settlements that are related to accruals and closing payment operations can be processed if dimension values are not specified. The following options are available:
    
      - **No** – Transactions are not settled, whether the dimension values are specified or not.
      - **Auto** - Automatic transactions are settled, whether the dimension values are specified or not.
      - **Manual** – Manual transactions are settled, whether the dimension values are specified or not.
      - **Always** – All transactions are settled, whether the dimension values are specified or not.
    
   > [!NOTE]
   > This parameter lets you ignore the setting of dimensions when individual transactions are created.
    
7.  Click the **Setup** FastTab.

8.  Click **Add** button to create a new record for a posting profile details.

9.  In the **Valid for** field, select the level of grouping for setting up the posting profile from the following options:
    
      - **Table** – This option is set for only one advance holder.
    
      - **Group** – This option is set for a group of advance holders.
    
      - **All** – This option is set for all advance holders.

10.  In the **Reference** field, select the corresponding reference.

   > [!NOTE]
   > You can select this field only if you select **Table** or **Group** in the **Valid for** field.
    
 
11.  In the **Summary account** field, select the account to reflect transactions for the advance holders.

12.  In the **Set** field, select the dimension focus for settlement control.
    
   > [!NOTE]
   > The specified dimension set indicates that dimension control is activated.

13.  Click **Save** button or close the form.


## Set up the terms of payment 

You must set up the terms of payment when you register the purchase of goods from a vendor through an advance holder. The advance holder makes the purchase.


1.  Click **Accounts payable** \> **Payment setup** \> **Terms of payment**.

2.  Click **New** button to create a new record or press **Edit** button to adjust an existing record.

3.  In the **Terms of payment** field, enter the code for the terms of payment.

4.  In the **Description** field, enter the description for the terms of payment.

5.  Click the **Setup** FastTab.

6.  In the **Payment method** field, select **C.O.D.**

7.  Select the **Cash payment** check box.

8.  Select the **From advance holder** check box.

9.  Click **Save** button or close the form.


## Set up the per diem expense rates 


Expense rates are used to generate an advance report for per diem expenses, and for automatic calculation of standard and over-rate amounts.


1.  Click Click **Accounts payable** \> **Setup** \> **Advance holders** \> **Expense rates**.

2.  Click **New** button to create a new expense or press **Edit** button to adjust an existing expense.

3.  In the **Expense** field, enter the expense code.

4.  In the **Description** field, enter the description for the expense code.

5.  In the **Rate** field, enter the standard established value for this expense.

6.  In the **Currency** field, select the currency code in which operations for this expense are registered.

7.  Click the **Setup** FastTab.

8.  In the **Main account** field under the **Rate** field group, select the accounting statement to reflect normal charges.

9.  In the **Main account** field under the **Over rate** field group, select the accounting statement to reflect over-rate charges.

10. In the **Sales tax group** field under the **Sales tax** field group and the **Taxes over norm** field group, select the sales tax group for calculating sales tax for sale and purchase on normal and over-rate amounts.

11. In the **Item sales tax group** field under the **Sales tax** field group and the **Taxes over norm** field group, select the item sales tax group for calculating sales tax for an item on normal and over-rate amounts.

12. If the amounts include sales tax, select the **Amounts includes. sales tax** check box under the **Sales tax** field group and the **Taxes over norm** field group.

13. In the **Posting over norm** field, select the over-norm expense posting operation.

14. Click the **Financial dimensions** FastTab.

15. Select the transaction dimensions values for the related dimensions in the **Financial dimensions** field group and in the **Financial dimensions over rate** field group.

16. Click **Save** button or close the form.


## About worker table numbers for advance holders 


A worker can be an employee or a contractor, and can hold several positions in an organization. An employee or a contractor can also be an advance holder who is accountable for the expense amount that is provided by the organization. To specify a worker as an advance holder, you must enter a unique worker ID in the **Worker ID** field in the **Worker** page. You must also select the **Advance holder** check box in the **Advance holders** form to indicate that the selected worker is an advance holder.

Transactions for these workers can be posted by using advance holder accounts. The worker ID that is specified for each advance holder can be used to track all advance holder transactions. This number is retrieved as an account number for advance holder transactions in the **General journals** and **Advance holder transactions** pages.


## Set up the advance holder 


1.  Click **Accounts payable** \> **Advance holders** \> **Advance holders**.
    
    > [!NOTE]
    > You cannot add or delete employees on the **Advance holders** page. Employees must be preliminary hired in **Human resources** module. In the **Employee posting profiles** page, you can set up the employee posting profile that is used to post advance holder balances.</P>

2. Select an employee, and then click **Edit** button.

3. Select the **Advance holder** check box to specify that the employee is an advance holder.

4. In the **Group** field, select the advance holder group that the employee belongs to.

5. In **Identity document** fields group provide an identification document details.
    
6. Click **Save** button or close the form.
  
    > [!NOTE]
    > If the **Advance holder sorting** option is set to **Yes** on the **Accounts payable parameters** page, the advance holders are displayed first in the list of employees on the **Advance holders** page.</P>
    
