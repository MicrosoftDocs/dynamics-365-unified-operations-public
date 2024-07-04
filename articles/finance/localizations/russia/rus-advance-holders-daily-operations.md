---
title: Daily operations for advance holders in Russia
description: Learn about daily operations, such as handling cash and closing balances, for advance holders for Russia, including an outline on creating disbursement slips.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/01/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1
---

# Daily operations for advance holders in Russia

[!include [banner](../../includes/banner.md)]

This article provides information about daily operations for advance holders for Russia. These operations include handling cash and closing balances.

## Create and post disbursement slips for advance holders

Use this procedure to create and post disbursement slips that have advance holder details. The advance holder balances are posted to the related employee balance account.

1. Select **Cash and bank management** \> **Cash transactions** \> **Slip journal**.
2. Select **New** to create a slip journal. 
3. On the **Lines** page, in the **Offset account type** column, select **Advance holder**. Then select an advance holder in the **Offset account** column, and enter the amount in the **Credit** column.
4. Approve and post the disbursement slip. 
5. To inquire about the related transactions and advance holder balance, select **Accounts payable** \> **Advance holders** \> **Advance holders**, select an employee, and then select either **Transactions** or **Balance**.

## Create and post vendor invoices that have advance holder details

Use this procedure to create and post vendor invoices that have advance holder details. The advance holder balances are posted to the employee balance account instead of the vendor balance account.

1. Select **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
2. Select **New** to create a purchase order. For more information, see [Create a purchase order](../../../supply-chain/procurement/tasks/create-purchase-order.md).
3. On the **Purchase order** page, switch to the **Header** view.
4. On the **Price and discount** FastTab, in the **Terms of payment** field, select the payment terms.

    > [!NOTE]
    > Select payment terms where the **From advance holder** option is set to **Yes** on the **Terms of payment** page.

5. In the **Advance holder** field, select the advance holder for the purchase order.
6. Enter all the required line details, and then select **Purchase** \> **Actions** \> **Confirm** to confirm the purchase order.
7. Select **Invoice** \> **Generate** \> **Invoice** to create a vendor invoice for the purchase order.
8. On the **Vendor invoice** page, in the **Invoice identification** field group, in the **Number** field, enter the invoice number.
9. Select **Post** to post the invoice, and then close the page.
10. Select **Accounts payable** \> **Inquiries and reports** \> **Advance holders inquires and reports** \> **Transactions** to view related advance holder transactions.
11. Select **Voucher** to open the **Voucher transactions** page. The vendor balance account is replaced by the employee balance account, and the **Posting type** field is updated to **Employee balance**.

## Create and post advance reports

Use these procedures to create, modify, post, inquire about, and print advance reports.

### Create an advance report

1. Select **Accounts payable** \> **Advance holders** \> **Advance report**.
2. Select **New** to create an advance report. Alternatively, you can create an advance report directly from the **Advance holders** page by selecting **New** \> **Advance report**.
3. In the **Date** field, enter the advance report date.

    The advance report number is automatically generated in **Advance report** field, based on the number sequence that is defined in the parameters.

4. In the **Employee number** field group, select an advance holder.
5. In the **Advance purpose** field, enter the purpose of the advance.
6. Switch to the **Header** view.
7. On the **Options** FastTab, define confirmation dates.
8. On the **Officials** FastTab, define responsible managers.

### Generate advance report lines from expenses

1. Switch to the **Lines** view.
2. Select **Copy from expends** to open the **Create advance report lines** page. This page shows all the expense types that were previously defined in the parameters.
3. Select an expense line.
4. In the **Date** field, enter the date of the transaction.
5. In the **Document number** field, enter the number of the confirmed disbursement voucher.

    > [!NOTE]
    > The values in the **Document name**, **Rate**, and **Currency** fields are automatically taken from the expense rates dictionary.

6. In the **Quantity of days** field, enter the number of days of the business trip.
7. In the **To weekday** field, enter the daily expense amount.

    > [!NOTE]
    > The **Total amount** field shows the total expense amount.

8. Select **Save** to transfer the entries to the **Advance report** page.

    > [!NOTE]
    > The value in the **Ledger account** field is based on the setup of expense rate posting. If the actual expense exceeds the established rates, a supplementary line for the excess amount is created when the expenses are transferred to the advance report. In this situation, the **Over rate** check box is automatically selected. The **Line type** field of the advance report that is generated by using the **Copy from expends** function is set to **Expense**.

### Generate advance report lines from sources

1. Switch to the **Lines** view.
2. Select **Copy from sources** to open the **Create lines** page. This page shows a list of the advance holder's documents (credit transactions) where the date coincides with the advance report date.

    > [!NOTE]
    > In the upper pane, the **Source type** field shows the identification type of the original document. The source for the **Facture** type is the purchase order, and the source for the **Accounts payable** type is the vendor transaction. The **Amount in transaction currency** field shows the total amount in the secondary currency of the transaction, the **Currency** field shows the currency code, and the **Amount** field shows the amount in the company's standard currency. In the lower pane, the **Number** field shows the number of the vendor's facture. The **Description** field shows the item name. The **Currency** field shows the voucher currency, the **Amount in transaction currency** field shows the line amount, and the **Sales tax amount in currency** field shows the sales tax amount.

3. In the upper pane, select the **Mark** check boxes to select the documents that should be copied.
4. Select **OK** to transfer the expense data to the advance report.

    In the **Document number** field of the advance report, the number of the source facture is copied if the **Line Type** field of the advance report is set to **Facture**. If the **Line Type** field is set to **Vendor**, the number of the transaction is copied.

    > [!NOTE]
    > You can't edit the **Amount**, **Currency**, and **Main account** fields.

### Manually generate advance report lines

Use this procedure to manually generate and post advance report lines. You can distribute the expense amount among different ledger dimensions. You can then view the ledger entries and verify the distribution of the expense amount.

1. On the **Advance report lines** FastTab, select **Add line** to create a line.
2. In the **Disbursement date** field, enter the date of the document that describes the expense.
3. In the **Document number** field, enter the number of the confirming document.
4. In the **Document name** field, enter the name of the confirming document.
5. In the **Currency** field, select the currency that is used for the transaction.
6. In the **Amount** field, enter the amount that is spent for the transaction.

    > [!NOTE]
    > The amount should be positive. Don't enter a negative amount on advance report lines. Instead, select **Rejection** or **Close via cash**/**Close via bank**.

8. In the **Confirmed amount of advance report** field, enter the confirmed expense for the advance report.
9. In the **Main account** field, select the general ledger account that the expense belongs to.
10. Select **Distribute amounts** to open the **Accounting distributions** page.
11. In the **Distributed by** field, select whether amounts should be distributed by extended price or discount percentage. You can create distributions in the following ways:

    - To create multiple distributions that have the same quantity, percentage, or amount distribution, select **Split** for each distribution. Select a ledger account for each distribution, and then select **Distribute equally**.
    - To create one distribution at a time, select **Split**. Select the ledger account to distribute the invoice line to, and then enter the quantity, percentage, or amount to distribute. For example, if you selected **Percent** in the **Distributed by** field, enter a percentage in the **Percent** field.

11. Select **Save**, and then close the **Accounting distributions** page.
12. On the **Line details** FastTab, on the **Setup** tab, in the **Sales tax group** field, select the code for the sales tax group for the advance report.
13. In the **Item sales tax group** field, select the code for the item sales tax group for the advance report.
14. Set the **Prices include sales tax** option to **Yes** to indicate that the amount on the advance report includes sales tax.

### Post an advance report

Use this procedure to post an advance report when all the advance report header and lines details are completed.

- On the Action Pane, select **Post** \> **Post** to post the advance report.

### Print an advance report

Use this procedure to print an advance report that has been posted. You can print an advance report after an advance invoice that is issued to an advance holder is settled.

> [!NOTE]
> The amounts on the **Advance reports** page are recalculated on the date when the payment journal for the advance holder is posted.

1. On the Action Pane, select **Print** \> **Print** to open the **Advance report** page.
2. Select **OK** to print the advance report in Microsoft Excel format.

### Reject an advance report

You can reject advance reports that have been posted and that have a status of **Posted**. These reports should not have been settled. Factures aren't created for these reports.

1. Select an advance report, and then, on the Action Pane, select **Post** \> **Rejection**.
2. Select **Yes** to confirm the action.
3. The status of the advance report is set to **Rejected**.

    > [!NOTE]
    > When an advance report is rejected, reversed transactions are created for the advance holder. The **Reversed** option is automatically set to **Yes** on the **Advance holder transactions** page. The transactions are automatically settled and reversed.

4. Close the page.
5. Select **Accounts payable** \> **Advance holders** \> **Advance holders**.
6. Select **Transactions** to open the **Advance holder transactions** page.
7. Select a transaction, select **Voucher**, and verify that the **Correction** option is automatically set to **Yes**.

You can verify the distribution of expenses for the reversed transaction. Reversed or storno accounting transactions are distributed like the original transactions. However, the distributions for reversed or storno accounting transactions have a negative sign.

## Close balances for an advance holder

You can close balances for an advance holder through cash or a bank.

### Close balances through cash

1. Select **Accounts payable** \> **Inquiries and reports** \> **Advance holders inquiries and reports** \> **Balance**.
2. In the **To date** field, enter the date to get advance holder balances for.
3. Select **Close via cash** to open the **Close via cash** page.
4. In the **Date of payment** field, enter the date of payment.
5. In the **Amount to be transferred** field, enter the balance amount during closing.

    > [!NOTE]
    > By default, this field shows the amount from the **Amount** field on the **Balance** page.

6. Set the **Automatic** option to **Yes** to automatically create and post the slip journal.

    > [!NOTE]
    > If you set the **Automatic** option to **No**, a journal is automatically created, and the journal number is shown. You must then manually post this journal.

7. Select **OK** to generate the slip journal.

    > [!NOTE]
    > After the slip journal is processed, either a disbursement slip or a reimbursement slip is generated for the advance holder when the balances are closed. If the amount in the **Amount to be transferred** field is negative, a disbursement slip is generated. If the amount in the **Amount to be transferred** field is positive, a reimbursement slip is generated.

8. Close the page.

### Close balances through a bank

The procedure for closing balances through a bank resembles the previous procedure for closing balances through cash. However, in step 3, you select **Close via bank** instead of **Close via cash**. You can set up the code for the journal and the bank on the **Advance holders** tab on the **Accounts payable parameters** page.

## Complete the settlement for an advance holder

You can complete either a manual settlement or a periodic settlement for an advance holder. If you set the **Automatic settlement** option to **No** on the **Accounts payable parameters** page, you must settle the posting or closing transactions either manually or by using the periodic settlement function.

### Manually settle advance holder transactions

Use this procedure to manually settle advance holder transactions.

1. Select **Accounts payable** \> **Advance holders** \> **Advance holders**.
2. Select an advance holder.
3. Select **Settle** \> **Settle open transactions** to open the **Open-transaction editing in several currencies** page. The upper pane shows debit transactions for the advance holder, and the lower pane shows credit transactions.
4. In the upper and lower panes, select the **Mark** check boxes to select transactions. The **Balance** field shows the balances after the transactions are settled.
5. Select **Update** to complete the settlement.
6. Close the page.
7. On the **Advance holders** page, select **Settlements** to open the **Transaction settlements** page, where you can verify the completed settlements.

    > [!NOTE]
    > If exchange adjustments occur when advance holder transactions are settled, exchange adjustment transactions are generated from the settlement. The exchange rate adjustment is shown in the **Exchange rate adjustment amount** field on the **Transaction settlements** page.

8. Close the page.
9. Select **Accounts payable** \> **Advance holders** \> **Advance reports**.
10. Select the advance report that is created for the selected advance holder.
11. On the **Financials** tab, select **View distributions** to verify that the distribution of the expense amount is correct.

### Periodically settle advance holder transactions

Use this procedure to periodically settle advance holder transactions. When you use the periodic settlement function, all open transactions are settled in chronological order.

1. Select **Accounts payable** \> **Periodic tasks** \> **Advance holders** \> **Periodic settlement**.
2. In the **Date of transaction** field, select the advance holder transaction date. All transactions that were posted before this date will be settled.
3. Set the **Settlement by profile** option to **Yes** to settle transactions that have identical posting profiles.
4. On the **Records to include** FastTab, define additional filtering for settlement.
5. Select **OK** to settle the transactions.

### Cancel a periodic settlement

Use this procedure to cancel a periodic settlement for advance holder transactions.

1. Select **Accounts payable** \> **Periodic tasks** \> **Advance holders** \> **Periodic reverse**.
2. In the **Date of transaction** field, select the advance holder transaction date. All transactions that were settled before this date will be reversed.
3. On the **Records to include** FastTab, define additional filtering for the transactions to cancel settlements for.
4. Select **OK** to cancel the periodic settlement.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
