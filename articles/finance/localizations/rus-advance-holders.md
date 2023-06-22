---
title: Russia advance holders overview
description: This article explains how to register and set up advance holders for Russia.
author: mrolecki
ms.date: 07/25/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Russia
ms.author: mrolecki
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1
ms.collection: get-started
ms.search.form: HcmWorkerAdvHolderTableListPage_RU, HcmWorkerAdvHolderTable_RU
---

# Russia advance holders overview
[!include [banner](../includes/banner.md)]

## Set up parameters for advance holders

1. Select **Accounts payable** \> **Setup** \> **Accounts payable parameters**.
2. On the **Advance holders** tab, in the **Posting profile** field, select the default posting profile that should be used to complete transactions for advance holders.

    > [!NOTE]
    > For more information, see the "Set up posting profiles for accounting vouchers" section later in this article.

3. Set the **Set default advance holder** option to **Yes** to set the current user as the advance holder.
4. Set the **Advance holder sorting** option to **Yes** to show advance holders at the top of the grid on the **Advance holders** page.
5. Set the **Issue when balance is open** option to **Yes** to allow cash advances to be issued to advance holders who have an open positive balance.
6. Set the **Automatic settlement** option to **Yes** if automatic transactions settlement is required.
7. Set the **Settlement by profile** option to **Yes** to settle transactions only with an identical posting profile.
8. On the **Balance closing** FastTab, under **Balance closing via cash**, in the **Name** field, select the cash slip journal code. This journal code is used to generate cash disbursement slips and reimbursement slips when an advance holder's balances are closed through cash.

    > [!NOTE]
    > All journals are of the **Cash** type.

9. In the **Cash** field, select the cash account to determine the vouchers that are used to close the balances for the advance holder.
10. Under **Balance closing via bank**, in the **Name** field, select the journal code for transactions to close the balances through a bank.
11. In the **Account type** field, select **Bank** to close the balances for an advance holder through a bank.
12. In the **Main account** field, select the bank account code to close the balances for an advance holder through a bank.
13. On the **Number sequences** tab, define number sequences codes for the following references:

    - Advance report
    - Advance report voucher
    - Settlement voucher
    - Exchange adjustment voucher (Advance holders)

14. Select **Save**, or close the page.

## Set up an advance holder group

You must create an advance holder group to group advance holders. For example, you can group advance holders by vouchers that are calculated in a single account.

1. Select **Accounts payable** \> **Setup** \> **Advance holders** \> **Advance holder groups**.
2. Select **New** to create a new advance holder group or **Edit** to adjust an existing group.
3. In the **Group** field, enter the code for the advance holder group.
4. In the **Description** field, enter a description of the advance holder group.
5. In the **Offset account** field, select the general ledger offset account to use for the advance holder group.
6. Select **Save**, or close the page.

## Set up posting profiles for accounting vouchers

You can set up the following posting profiles for an account of operations:

- One ledger account for all advance holders
- A separate ledger account for each group of advance holders
- A separate ledger account for each advance holder

1. Select **Accounts payable** \> **Setup** \> **Advance holders** \> **Employee posting profiles**.
2. Select **New** to create a new posting profile or **Edit** to adjust an existing profile.
3. In the **Posting profile** field, enter the profile ID of the posting profile that is being processed.
4. In the **Description** field, enter a description of the posting profile.
5. On the **Table restrictions** FastTab, in the **Allow empty dimension value** field, select the condition under which settlements that are related to accruals and closing payment operations can be processed if dimension values aren't specified. The following options are available:

    - **No** – Transactions aren't settled, regardless of whether the dimension values are specified.
    - **Auto** – Automatic transactions are settled, regardless of whether the dimension values are specified.
    - **Manual** – Manual transactions are settled, regardless of whether the dimension values are specified.
    - **Always** – All transactions are settled, regardless of whether the dimension values are specified.

    > [!NOTE]
    > This field lets you ignore the values of dimensions when individual transactions are created.

6. On the **Setup** FastTab, select **Add** to create a new record for posting profile details.
7. In the **Valid for** field, select the level of grouping for the setup of the posting profile. The following options are available:

    - **Table** – This option is set for only one advance holder.
    - **Group** – This option is set for a group of advance holders.
    - **All** – This option is set for all advance holders.

8. In the **Reference** field, select the corresponding reference.

    > [!NOTE]
    > You can select a value in this field only if you selected **Table** or **Group** in the **Valid for** field.

9. In the **Summary account** field, select the account that should reflect transactions for the advance holders.
10. In the **Set** field, select the dimension focus for settlement control.

    > [!NOTE]
    > The specified dimension set indicates that dimension control is activated.

11. Select **Save**, or close the page.

## Set up the terms of payment

You must set up the terms of payment when you register the purchase of goods from a vendor through an advance holder. The advance holder makes the purchase.

1. Select **Accounts payable** \> **Payment setup** \> **Terms of payment**.
2. Select **New** to create a new terms of payment record or **Edit** to adjust an existing record.
3. In the **Terms of payment** field, enter the code for the terms of payment.
4. In the **Description** field, enter a description of the terms of payment.
5. On the **Setup** FastTab, in the **Payment method** field, select **C.O.D.**
6. Set the **Cash payment** option to **Yes**.
7. Set the **From advance holder** option to **Yes**.
8. Select **Save**, or close the page.

## Set up the per diem expense rates

Expense rates are used to generate an advance report for per diem expenses. They are also used for automatic calculation of standard and over-rate amounts.

1. Select **Accounts payable** \> **Setup** \> **Advance holders** \> **Expense rates**.
2. Select **New** to create a new expense or **Edit** to adjust an existing expense.
3. In the **Expense** field, enter the expense code.
4. In the **Description** field, enter a description of the expense.
5. In the **Rate** field, enter the standard established value for this expense.
6. In the **Currency** field, select the currency code that operations for this expense are registered in.
7. On the **Setup** FastTab, under **Rate**, in the **Main account** field, select the accounting statement that should reflect normal charges.
8. Under **Over rate**, in the **Main account** field, select the accounting statement that should reflect over-rate charges.
9. Under both **Sales tax** and **Taxes over norm**, in the **Sales tax group** field, select the sales tax group that should be used to calculate sales tax for sales and purchases on normal and over-rate amounts.
10. Under both **Sales tax** and **Taxes over norm**, in the **Item sales tax group** field, select the item sales tax group that should be used to calculate sales tax for an item on normal and over-rate amounts.
11. If the amounts include sales tax, under both **Sales tax** and **Taxes over norm**, set the **Amounts includes sales tax** option to **Yes**.
12. Under **Taxes over norm**, in the **Posting over norm** field, select the operation that should be used to post over-norm expenses.
13. On the **Financial dimensions** FastTab, under both **Financial dimensions** and **Financial dimensions over rate**, select the transaction dimension values for the related dimensions.
14. Select **Save**, or close the page.

## Worker table numbers for advance holders

A worker can be an employee or a contractor, and can hold several positions in an organization. An employee or a contractor can also be an advance holder who is accountable for the expense amount that the organization provides. To specify a worker as an advance holder, you must enter a unique worker ID in the **Worker ID** field on the **Worker** page. You must also set the **Advance holder** option to **Yes** on the **Advance holders** page, to indicate that the selected worker is an advance holder.

Transactions for these workers can be posted by using advance holder accounts. The worker ID that is specified for each advance holder can be used to track all advance holder transactions. This number is retrieved as an account number for advance holder transactions on the **General journals** and **Advance holder transactions** pages.

## Set up the advance holder

[Advance holders overview](emea-advance-holders.md#create-an-advance-holder)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
