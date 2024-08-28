---
title: Set up exchange rates for currency transactions
description: Learn how to set up exchange rates for currency transactions in Russia, including a step-by-step process for setting up the loss or gain calculations.
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

# Set up exchange rates for currency transactions

[!include [banner](../../includes/banner.md)]

> [!Important]
> Exchange rates and amount difference settings are designed to correctly reflect exchange rate and amount differences in accounting and tax accounting. However, the amount difference has been canceled in accounting and tax accounting since 01.01.2007 - in accounting and since 01.01.2015 - in tax accounting. Nevertheless, the amount difference functionality still exists in Dynamics 365 Finance. This article describes that functionality.   

You use the **Currency revaluation accounts** page to set up the loss or gain calculation for currency exchange.

1. Select **General ledger** \> **Setup** \> **Currency** \> **Currency parameters**.
2. In the **Legal entities** field, select a company.
3. Set the **Activate parameters** option to **Yes** to activate the Russian revaluation parameters for the specified currency.
4. On the **General** FastTab, in the grid, select the main accounts to post the exchange rate profits or losses to.
5. On the **Sales/customers** FastTab, in the grid, select the main accounts to post the exchange rate profits or losses to.
6. In the **Expense code** field, select the expense code that corresponds to the transaction for an exchange rate adjustment that occurs when transactions are settled for a customer.
7. In the **Revenue code** field, select the revenue code that corresponds to the transaction for an exchange rate adjustment that occurs when transactions are settled for a customer.
8. On the **Purchases/Vendors** FastTab, in the grid, select the main accounts for vendor posting.
9. In the **Revenue code (currency conversion)** field, select the revenue code for a currency conversion transaction if the exchange adjustment is a profit.
10. In the **Expense code (currency conversion)** field, select the revenue code for a currency conversion transaction if the exchange adjustment is a loss.
11. On the **Purchases/Advance holders** FastTab, select the relevant main accounts for advance holder posting.
12. In the **Expense code** field, select the expense code that corresponds to the transaction for an exchange rate adjustment that occurs when transactions are settled for an advance holder.
13. In the **Revenue code** field, select the revenue code that corresponds to the transaction for an exchange rate adjustment that occurs when transactions are settled for an advance holder.

## Set up general ledger parameters for exchange adjustment

Use this procedure to set up the parameters for exchange adjustments of advance settlements on the **General ledger parameters** page.

1. Select **General ledger** \> **Setup** \> **General ledger parameters**.
2. In the **Foreign currency revaluation** field group, in the **Calculation method** field, select **Period grand total** as the calculation method for exchange differences.
3. Set the **Advance revaluation cancelation** option to **Yes** to cancel exchange adjustment during advance settlement.

## Settle partial payments for customers

Use this procedure to settle partial payment transactions for a customer. You can settle a partial payment against a specific invoice line, and you can settle open transactions by using a periodic settlement for customers. Exchange adjustment factures are created for the invoice lines that are settled.

1. Select **Accounts receivable** \> **Journals** \> **Payments** \> **Payment journal**.
2. Create or select a payment journal line, and then select **Lines** to open the **Customer payments** page.
3. Select **Settle transactions** to open the **Settle transactions** page.
4. Select the **Mark** check box to mark the transaction line for settlement.

    > [!IMPORTANT]
    > The **Mark lines on free text invoices and interest notes** check box must be selected on the **Settlement** tab of the **Accounts receivable parameters** page.

5. In the **Amount to settle** field, view or modify the partial payment that must be settled.
6. Select **OK** to settle the partial settlement for the customer.
7. Select **Post** \> **Post** to post the customer payment journal and settle the payment amount.

    > [!NOTE]
    > To verify that the exchange adjustment facture that is created has the same settled invoice amount on the **Facture journal** page, select the facture.

8. Select **Accounts receivable** \> **Periodic** \> **Sales book** \> **Sales books journal**.
9. Create a sales book that includes the settled facture amount and the exchange adjustment facture. You can verify that the invoice facture is included in the sales book for the settled amount.

## Calculate the exchange rate difference for a customer

You can use the **Foreign currency revaluation** page to calculate the exchange rate difference for a customer. The exchange adjustment is calculated at the end of a period, based on the rate that is specified on the period end date.

1. Select **Accounts receivable** \> **Periodic tasks** \> **Foreign currency revaluation**.
2. Select **Foreign currency revaluation** to create a foreign currency revaluation for the accounting period.
3. In the **Method** field, select **Standard**.
4. In the **Considered date** field, select the date when the open transaction should be adjusted. The same date is used to post the adjusted transaction.
5. In the **Date of rate** field, select the date that determines the exchange rate that is used to revalue the voucher.
6. In the **Transaction text** field, enter the text that describes the exchange adjustment transaction.

    > [!NOTE]
    > If you leave this field blank, it's automatically filled with the standard text for exchange rate correction and the number of the revaluated document.

7. In the **Notes** field, enter any additional information about the transaction.
8. In the **Use posting profile from** field, select where the posting profile for the transaction is selected from:

    - **Posting** − The profile of the posted open transaction is used for the exchange adjustment.
    - **Select** − The profile that is selected in the **Posting profile** field is used for the exchange adjustment.

    If you selected the **Posting profile** value in the **Use posting profile from** field, you should select a posting profile in the **Posting profile** field. The exchange adjustment transaction posting is based on the selected posting profile.

9. In the **Dimension** field, select the dimensions that are posted to the exchange adjustment transactions:

    - **None** – In the exchange adjustment voucher, the line dimension doesn't depend on the dimension in the original voucher.
    - **Table** – In the exchange adjustment voucher, the line dimension is inherited from the dimension of the customer account.
    - **Posting** – In the exchange adjustment voucher, the line dimension is inherited from the dimension in the original voucher.

10. Set the **Print** option to **Yes** to print the report.
11. Select **Records to include** to specify the criteria for exchange adjustment, as you require.
12. Select **OK** to revalue the selected transaction.
13. On the **Foreign currency revaluation** page, select **Voucher** to open the **Voucher transactions** page, where you can view the resulting ledger transactions for exchange adjustment.
14. Press Ctrl+S, or close the page.
15. On the **Foreign currency revaluation** page, select **Transactions** to open the **Customer transactions** page, where you can view the resulting customer transactions for exchange adjustment.
16. Press Ctrl+S, or close the page.
17. On the **Foreign currency revaluation** page, select **Simulation** to open the **Simulation** page.

    > [!IMPORTANT]
    > The **Simulation** button is available only if you select **Standard** in the **Calculation method** field on the **Ledger** tab of the **General ledger parameters** page.

18. In the **Method** field, select a method for exchange adjustment.
19. In the **Considered date** field, select the voucher posting date.
20. In the **Date of rate** field, select the exchange date.
21. Select **Select** to define the customer account, currency, and fixed rate.
22. Select **OK** to show the customer transaction details on the **Simulation** page.
23. Select **Distribution** to specify the report output.
24. Select **OK** to generate the **Customer - foreign currency revaluation simulation** report.

## Set up amount difference parameters for exchange rates
 > [!NOTE]
 > Amount differences are canceled  in tax accounting from 1.1.2015 in Russia.

An original facture can be corrected if the currency values change during the shipment of goods. After the facture is corrected, the company verifies that the total of the correction is equal to the total of the amount difference. An amount difference facture is generated when a purchase or sales transaction is settled under the following conditions:

- The invoice currency and the company currency differ.
- The payment currency is equal to the company currency.
- The exchange rate of the invoice currency on the invoice date differs from the exchange rate on the payment date.
- The amount difference affects the company's liability for value-added tax (VAT).

Any amount difference facture that is generated is processed independently of other factures, and is included in the sales book and purchase book. You can then print the amount difference facture and the original facture that was adjusted based on the amount difference.

Use this procedure to set up parameters for amount differences for exchange rates. When you post an exchange adjustment transaction, it's posted to the ledger account that is defined on the **Currency revaluation accounts** page. All adjustments are posted to ledger accounts. You must set the posting rules, and you must set the taxable parameter for a positive or negative amount difference.

1. Select **General ledger** \> **Setup** \> **Currency** \> **Currency parameters**.
2. On the **General** FastTab, set the **Amount difference in tax accounting before 01.01.2015** option to **Yes** to consider amount differences in the calculation of tax accounting registers.
3. On the **Sales/customers** FastTab, in the **Expense code** field, select the expense code to use as a tax dimension for the exchange adjustment transaction if the exchange adjustment is a loss.

    > [!IMPORTANT]
    > The **Sales/customers** FastTab is available only if you select **Incremental** or **Period grand total** in the **Calculation method** field on the **General ledger parameters** page.

4. The settlement transactions might cause exchange adjustment losses and profits. In the **Main account** field, select the main account for the Realized loss or Realized gain account, and the Unrealized loss or Unrealized gain account, that these exchange adjustment losses and profits are posted to.

    > [!IMPORTANT]
    > This field is required if you select **Deviation from the cost price** in the **Ledger posting** field. The Unrealized loss or Unrealized gain account is used when revaluation of foreign currency is done.

5. In the **Customer tax dimension** field group, in the **Revenue code** field, select the revenue code for the exchange adjustment transaction if the exchange adjustment is a profit.
6. In the **Sales taxes** field, select **Tax** to specify that the realized profit or loss of purchase tax is subject to VAT.

    > [!IMPORTANT]
    > Amount difference factures are created only if the **Sales taxes** field for a positive or negative amount difference is set to **Tax**.

7. On the **Purchases/Vendors** FastTab, in the **Expense code** field, select the expense code to use as a tax dimension for the amount difference transaction if the amount difference is a loss.

    > [!IMPORTANT]
    > The **Purchases/Vendors** tab is available only if you select **Incremental** or **Period grand total** in the **Calculation method** field on the **General ledger parameters** page.

8. In the **Revenue code** field, select the revenue code to use for the transaction if the amount difference that the settlement produces is a profit.
9. In the **Sales taxes** field, select **Tax** to specify that the realized profit or loss of purchase tax is subject to VAT.

    > [!IMPORTANT]
    > Amount difference factures are created only if the **Sales taxes** field for a positive or negative amount difference is set to **Tax**.

10. In the **Main account** fields, select the ledger account that the exchange adjustment transactions for losses and profits are posted to.

    > [!IMPORTANT]
    > This field is required if you select **Deviation from the cost price** in the **Ledger posting** field.

## Set up accounts payable parameters for amount differences

You use the **Accounts payable parameters** page to set up accounts payable parameters for amount differences. Facture amount differences are included in a separate list that is created in the purchase book for the specified period. This list contains the cancellation of the source facture and the new facture that is recalculated at payment.

> [!NOTE]
> If more than one payment is made during a tax period, the recalculated facture amount is the total of the recalculated payments. If all the payments belong to the same tax period that the invoice belongs to, the total facture is reflected in the purchase book.

1. Select **Accounts payable** \> **Setup** \> **Accounts payable parameters**.
2. On the **Ledger and sales tax** tab, on the **Purchase book** FastTab, set the **Amount difference in additional list** option to **Yes** to include the amount differences in an additional list in the purchase book.

## Amount difference factures for sales and purchase orders

Before you can generate an amount difference facture, you must create and post a facture for a purchase order or sales order. After you post the facture, you settle the facture transactions to generate the amount differences, based on the exchange rates.

Amount difference factures are corrections for factures. Based on the amount differences, the original factures are shown in the sales book (for sales original invoices) and purchase book (for purchase original invoices). In the sales book, they appear as separate lines. However, they have the same facture identifier and the same date as the original facture. In the purchase book, they appear as a total line, where the sum of the amount differences is added to the original facture amount.

You can recalculate the cost of the original facture so that the amount difference is considered. In the additional list, the original facture amount has a negative sign, and the recalculated facture amount has a positive sign. You can print the amount differences from the **Facture journal** page in the following ways:

- Include all amount difference factures.
- Include only selected amount difference factures.

### Example

The following example shows how amount differences are calculated for a contract.

The cost of the received goods is 100 standard units, and the tax accounting period is monthly. Payments are made in Russian rubles (RUB) by using the currency rate on the payment date.

If the currency rate is 32 RUB for one standard unit, two invoice lines are created, as shown in the following table.

| Standard units | Invoice amount | VAT percent | Standard units (including VAT percentage) | Invoice amount (including VAT percentage) |
|----------------|----------------|-------------|-------------------------------------------|-------------------------------------------|
| 40             | 1,280          | 18          | 6.10                                      | 195.20                                    |
| 60             | 1,920          | 10          | 5.45                                      | 174.20                                    |

If the currency rate changes from 32 RUB to 28 RUB, the payment for the received goods also changes. For 20 standard units, the payment becomes 560 RUB. Therefore, during transaction settlement, an amount difference (28 – 32) is generated and appears on the facture lines. You can also calculate the total cost and total tax for every tax code.

If *A* is the corrected number of standard units, based on the amount difference for the first facture line, here is the proportion for the VAT calculation:

20:100 = A:40

Therefore, A = 20 × 40 ÷ 100 = 8.

Therefore, the correction for the first line is 8 × (28 – 32) = –32 RUB.

If *B* is the corrected number of standard units, based on the amount difference for the second facture line, here is the proportion for the VAT calculation:

20:100 = B:60

Therefore, B = 20 × 60 ÷ 100 = 12.

Therefore, the correction for the second line is 12 × (28 – 32) = –48 RUB.

VAT is applied to the amount difference. For VAT at 18 percent, the value is (32 ÷ 118) × 18 = 4.88 RUB. For VAT at 10 percent, the value is (48 ÷ 110) × 10 = 4.36 RUB.

## Create an amount difference facture and link it to an original sales invoice

Use the following procedures to create an amount difference facture and link it to an original sales invoice.

### Create an amount difference facture for a sales order

1. Select **Accounts receivable** \> **Common** \> **Sales orders** \> **All sales orders**.
2. To post a facture for a sales order, create the sales order, and then, on the **Setup** FastTab, select **Sales tax group** and **Item sales tax group**. 
3. Select **Accounts receivable** \> **Journals** \> **Payments** \> **Payment journal**.
4. Create a journal, and enter the required details.
5. Select **Lines** to open the **Journal voucher** page.
6. In the **Account** field, select the customer account that the sales invoice is posted for.
7. Select **Functions** \> **Settlement** to open the **Settle open transactions** page.
8. Select the **Mark** check box to mark the sales invoice line to settle.
9. Close the page.
10. Select **No** to retain the original journal amount.
11. Select **Post** \> **Post** to post the journal.

### Link an amount difference facture to an original sales invoice

1. Select **Accounts receivable** \> **Inquiries** \> **Journals** \> **Invoice journal**.
2. Select the invoice line to include the amount difference for in the sales book, and then select **Create facture** \> **Update facture** to open the **Update facture** page.

    > [!IMPORTANT]
    > In the sales book, the facture date and facture number must be the same as the facture date and facture number of the original facture.

3. In the lower pane, select the **To facture** check box to mark the facture for update.
4. Select **Posting** \> **Update** to update the facture with the amount difference.
5. Close the pages.
6. Select **Accounts receivable** \> **Inquiries** \> **Journals** \> **Facture**.
7. Select the posted facture, and then select **Amount difference** tab.

    > [!NOTE]
    > The source facture ID is shown in the **Facture source** field.

8. Select the **Include in book** check box to update the amount difference facture in the sales book.
9. Select **Print**.
10. Set the **Included only** option to **Yes** to print the original facture together with only the selected amount difference factures. If you set this option to **No**, all amount difference factures are printed together with the original facture.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
