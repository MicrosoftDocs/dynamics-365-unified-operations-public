---
# required metadata

title: Foreign currency sales, purchases, and transfers
description: This topic describes the functionality for registering transactions for the sale, purchase, and transfer of currency.
author: anasyash
ms.date: 02/20/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Foreign currency sales, purchases, and transfers

[!include [banner](../includes/banner.md)]

Dynamics 365 Finance lets you perform the following tasks:

- Register transactions for a sale, purchase, or transfer of foreign currency that is done by using the **Money transfers in transit** ledger account.
- Automatically calculate the profit/loss amounts that are caused by the foreign currency conversion for a sale or purchase of foreign currency. (The calculation considers the foreign currency exchange rate of the Central Bank and the exchange rate of the legal entity's bank on the date of the foreign currency transfer.) Also automatically generate transactions for profit/loss from the foreign currency conversion.
- Automatically generate transactions for the unrealized exchange rate difference that is caused when the exchange rates on the foreign currency transaction dates differ.
- Print a foreign currency transfer order.


## Set up the sale, purchase and transfer of foreign currency

Here is an overview of the tasks that you must complete to set up the system to calculate the exchange adjustment and the profit/loss on the **Remittance en route** account:

- [Set up an exchange rate](#set-up-an-exchange-rate)
- [Set up a bank to use for foreign currency conversion transactions](#set-up-a-bank-to-use-for-foreign-currency-conversion-transactions)
- [Set up a bank transaction type](#set-up-a-bank-transaction-type)
- [Set up a method of payment](#set-up-a-method-of-payment)
- [Set up a number sequence](#set-up-a-number-sequence)
- [Set up a bank account](#set-up-a-bank-account)

### Set up an exchange rate

Use the **Currency revaluation accounts** page to set up the calculation of profit/loss amounts for foreign currency conversion.

1. Go to **General ledger \> Currencies \> Currency parameters**.
2. In the **Legal entities** field, select a company.
3. On the **Purchases/Vendors** FastTab, define the following ledger accounts for currency conversion: **Conversion gain** and **Conversion loss**.
4. Define the following revenue and income codes for foreign currency conversion: **Revenue code (currency conversion)** and **Expense code (currency conversion)**.

### Set up a bank to use for foreign currency conversion transactions

Use the **Banks** page to associate a vendor account with the bank that should be used for foreign currency sale or purchase transactions.

1. Go to **Cash and bank management \> Setup \> Bank groups**.
2. Create a bank, or select an existing bank.
3. On the **General** FastTab, in the **Vendor account** field, select the vendor account.

When you associate a vendor account with a bank, the **Transactions** button on the Action Pane becomes available. The **Settle open transactions** and **Closed transaction editing** options on the **Functions** menu button also become available.

### Set up a bank transaction type

Use the **Bank transaction types** page to set up a bank transaction type for foreign currency sale, purchase, and transfer transactions.

1. Go to **Cash and bank management \> Setup \> Bank transaction types**.
2. Create a bank transaction type.
3. In the **Transaction extended type** field, select one of the following foreign currency transfer types: **Currency sale**, **Currency purchase**, or **Currency transfer**.
4. In the **Vendor posting profile** field, select the vendor posting profile that should be used to post to the **Money transfers in transit** ledger account.

### Set up a method of payment

Use the **Methods of payment** page to set up a method of payment for the sale, purchase, or transfer of foreign currency.

1. Go to **Accounts payable \> Payment setup \> Methods of payment**.
2. Create a method of payment.
3. On the **General** FastTab, in the **Account type** field, select **Bank**.
4. In the **Payment account** field, select the bank account to transfer foreign currency from for this method of payment.
5. In the **Bank transaction type** field, select the bank transaction type for the sale, purchase, or transfer of foreign currency.
6. On the **File formats** FastTab, in the **Export format** field, select **Currency transfer order**.

    > [!NOTE]
    > If the **Currency transfer order** option isn't available, select **Setup** to open the **File formats for methods of payment** page. On the **Export** tab, in the **Available** list, select **Currency transfer order**, and then select the right arrow button to add the format to the **Selected** list.

### Set up a bank account

Use the **Bank accounts** page to set up specific information for the sale or purchase of foreign currency.

1. Go to **Cash and bank management \> Bank accounts \> Bank accounts**.
2. Create a bank account, or select an existing bank account.
3. On the **Payment management** FastTab, in the **Order template (currency sale)** and **Order template (currency purchase)** fields, select the Microsoft Word template.

For more information, see [Set up Bank accounts (Russia)](./rus-local-settings-requisites-bank-module.md).

### Set up a number sequence

Use the **Cash and bank management parameters** page to assign a number sequence for foreign currency transactions.

1. Go to **Cash and bank management \> Setup \> Cash and bank management parameters**.
2. On the **Number sequences** tab, in the **Number sequence code** field for the **Currency transfer order** reference, select a number sequence.

## Foreign currency sales

### Create a foreign currency sale transaction

1. Go to **Accounts payable \> Payments \> Payment journal**.
2. Create a payment journal.
3. Select **Lines**, and create a journal line.
4. On the **List** tab, in the **Account** field, select the vendor account that is associated with the bank account that is used for foreign currency conversion transactions.
5. In the **Debit** field, enter the transaction amount in the foreign currency that must be sold.
6. In the **Currency** field, enter the code for the foreign currency that is ordered to be sold.
7. In the **Offset account type** field, select **Bank**.
8. In the **Offset account** field, select the bank account.
9. In the **Method of payment** field, select the method of payment that you created earlier for the sale of foreign currency.
10. On the **Bank** tab, in the **Bank transaction type** field, validate the value that is automatically filled in based on the method of payment, or select the transaction type for the foreign currency sale transaction.
11. On the **Payment** tab, in the **Posting profile** field, verify that the value equals the profile that is used to post to the **Money transfers in transit** ledger account.
12. Select **Generate payments**.
13. In the **Generate payments** dialog box, select the **Export format** option, and then, in the **Export format** field, select **Currency transfer order**. Alternatively, select the **Method of payment** option, and then, in the **Method of payment** field, select the method of payment for the foreign currency sale.
14. In the **Bank account** field, select the bank account for the payment.
15. Select **OK**.
16. In the **Bank currency transfer** dialog box, enter the required information.

    | Field              | Description |
    |--------------------|-------------|
    | Worker             | Select the worker who is responsible for the foreign currency sale. |
    | Transit account    | Select the bank account where rubles should be received for the foreign currency that is sold (the result of the foreign currency conversion). The template that will be used to print a foreign currency sales order is taken from this bank account. |
    | Currency           | Select the currency code that should be received in the transit bank account after the foreign currency sale. |
    | Bank exchange rate | Identify the foreign currency exchange rate for the foreign currency conversion. This information will be printed on the foreign currency sale order. |
    | Supplier account   | Select information about the contract in foreign currency that is the basis for the foreign currency sale transaction. |
    | Purchase agreement | Select information about the contract in foreign currency that is the basis for the foreign currency sale transaction. |
    | Print Document     | Set the option to "Yes" to print a foreign currency sale order when payments are generated. |



17. Select **OK**.

    On the payment journal line, the value of the **Payment status** field is updated to **Sent**.

    On the **Payment** tab, the fields **Transit account**, **Foreign counteragent**, **Contracts group**, and **Contract of the deal** are updated.

18. Select **Print \> Currency sale order** to print the foreign currency sales order. The report contains the following information:
19. Validate and post the journal.

### Create transactions for the bank commission and the local currency (rubles) amount that is received as a result of the foreign currency sale

After you post the payment order for a foreign currency sale, you can register the bank commission and the local currency that is received as a result of the foreign currency conversion. (In this case, Russian rubles are received.)

1. Go to **Accounts payable \> Payments \> Payment journal**.
2. Create a payment journal.
3. Select **Lines**, create a journal line for the bank commission withdrawal, and enter the following information.

    | Tab     | Field                 | Description |
    |---------|-----------------------|-------------|
    | List    | Account               | Select the vendor account that you used for the foreign currency sale transaction in the previous procedure. |
    |         | Credit                | Enter the amount of the bank commission. |
    |         | Currency              | Select the currency of the bank commission. |
    |         | Offset account type   | Select **Ledger**. |
    |         | Offset account        | Select the ledger account for bank commission losses. |
    | Bank    | Bank transaction type | Select the transaction type that has the **Currency sale** extended type. |
    | Payment | Posting profile       | Verify that the value equals the profile that is used to post to the **Money transfers in transit** ledger account. |

4. Create a journal line for the received local currency, and enter the following information.

    | Tab     | Field                                              | Description |
    |---------|----------------------------------------------------|-------------|
    | List    | Account                                            | Select the vendor account that you used for the foreign currency sale transaction in the previous procedure. |
    |         | Credit                                             | Enter the amount of accounting currency (rubles) that is received. |
    |         | Currency                                           | Select the accounting currency, which is the currency that is received as a result of the foreign currency sale (rubles). |
    |         | Offset account type                                | Select **Bank**. |
    |         | Offset account                                     | Select the bank account where the accounting currency is received. |
    | Bank    | Bank transaction type                              | Select the transaction type that has the **Currency sale** extended type. |
    | Payment | Currency (under **Currency conversion**)           | Select the foreign currency that was sold. This foreign currency code must differ from the accounting currency. |
    |         | Bank exchange rate (under **Currency conversion**) | Enter the bank exchange rate that was applied to the foreign currency sale. |
    |         | Posting profile                                    | Verify that the value equals the profile that is used to post to the **Money transfers in transit** ledger account. |

5. Post the journal.

### Post the settlement of foreign currency sale transactions

You post the settlement of foreign currency sale transactions to generate profit/loss transactions from them and from the foreign currency exchange difference transactions.

1. Go to **Cash and bank management \> Setup \> Bank groups**.
2. Select a bank, and then select **Functions \> Settle open transactions** to settle foreign currency sale transactions.
3. In the **Settlement posting date** field, select the posting date type: **Latest date**, **Today's date**, or **Selected date**.
4. If you selected **Selected date** in the **Settlement posting date** field, manually enter the posting date.
5. Review the transactions that will be settled:

    - On the **Overview** tab, the **Transit account** and **Bank account - inflow** fields are specific to the foreign currency sale:

        - For positive transactions, the value of the **Transit account** field equals the transit bank account that was selected for the foreign currency sale transaction in the **Transit account** field in the **Bank currency transfer** dialog box.
        - For negative transactions, the value of the **Bank account - inflow** field equals the bank account where the accounting currency amount is received as a result of the foreign currency sale transaction.

        The values of these fields should be equal for transactions that are marked for settlement.

    - On the **General** tab, the fields in the **Currency conversion** section are specific to the foreign currency sale.

6. Mark transactions for settlement.

    During settlement, the following information is validated:

    - The transaction type of both transactions must have the **Currency sale** extended type.
    - The value of the **Currency** field in the **Currency conversion** section of the **General** tab for the positive transaction (the foreign currency sale) must equal the value of the **Currency** field on the **Overview** tab for the negative transaction (the accounting currency receipt that is a result of the foreign currency sale).
    - The bank account that is specified in the **Transit account** field for the positive transaction must equal the bank account that is specified in the **Bank account - inflow** field for the negative transaction.

7. Select **Post**. The following transactions are generated:

    - Unrealized foreign currency exchange difference (if, for the foreign currency that is sold, the foreign currency exchange rate on the date of the foreign currency sale differs from the foreign currency exchange rate on the accounting currency receipt date)
    - Foreign currency sale profit or loss (if, for the foreign currency that is sold, the bank exchange rate differs from the Central Bank exchange rate on the date of the accounting currency receipt transaction)

8. You can review the transactions that are generated. On the **Bank groups** page, select **Transactions**.
9. You can also post an unsettlement of the transactions. On the **Bank groups** page, select **Functions \> Closed transitions editing**, mark transactions, and then select **Reverse**.

## Foreign currency purchases

### Create a transaction of rubles movement for a foreign currency purchase

1. Go to **Accounts payable \> Payments \> Payment journal**.
2. Create a payment journal.
3. Select **Lines**, create a journal line, and enter the following information.

    | Tab     | Field                 | Description |
    |---------|-----------------------|-------------|
    | List    | Account               | Select the vendor account that is associated with the bank account that is used for foreign currency conversion transactions. If you enter an amount in the **Debit** field, and if the **Bank transaction type** field is set to the transaction type of the **Value** extended type, this field is automatically filled in when you select a bank account in the **Offset account** field. |
    |         | Debit                 | Enter the transaction amount in the accounting currency (rubles). |
    |         | Currency              | Enter the code for the accounting currency (rubles). |
    |         | Offset account type   | Select **Bank**. |
    |         | Offset account        | Select the bank account that rubles are moved from for the foreign currency purchase. |
    |         | Method of payment     | Select the method of payment that you created earlier for the purchase of foreign currency. |
    | Bank    | Bank transaction type | Validate the value that is automatically filled in based on the method of payment, or select the transaction type for the foreign currency purchase transaction. |
    | Payment | Posting profile       | Verify that the value equals the profile that is used to post to the **Money transfers in transit** ledger account. |

4. Select **Generate payments**.
5. In the **Generate payments** dialog box, select the **Method of payment** option, and then, in the **Method of payment** field, select the method of payment for the foreign currency purchase.
6. In the **Bank account** field, select the bank account for the payment.
7. Select **OK**.
8. In the **Bank currency transfer** dialog box, enter the required information.

    | Field              | Description |
    |--------------------|-------------|
    | Worker             | Select the worker who is responsible for the foreign currency purchase. |
    | Transit account    | Select the bank account where the foreign currency that is purchased should be received (the result of the foreign currency conversion). |
    | Currency           | Select the foreign currency code that should be received in the transit bank account after the foreign currency purchase. |
    | Bank exchange rate | Identify the foreign currency exchange rate for the foreign currency conversion. This information will be printed on the currency purchase order. |
    | Supplier account   | Select information about the contract in foreign currency that is the basis for the foreign currency purchase transaction. |
    | Purchase agreement | Select information about the contract in foreign currency that is the basis for the foreign currency purchase transaction. |
    | Print Document     | Set the option to "Yes" to print a foreign currency purchase order when payments are generated. |

9. Select **OK**.

    On the payment journal line, the **Payment status** field is updated to **Sent**.

    On the **Payment** tab, the **Transit account**, **Foreign counteragent**, **Contracts group**, and **Contract of the deal** fields are updated.

    During generation of the foreign currency purchase order, the following information is validated:

    - The currency code of the transit bank account must differ from the accounting currency.
    - The currency code of the transit bank account must equal the currency code that is selected in the **Bank currency transfer** dialog box.
    - The currency code of the payment journal line must be the accounting currency.

10. Select **Print \> Currency purchase order** to print the foreign currency purchase order. (The template is taken from the transit bank account that is selected in the **Bank currency transfer** dialog box.)
11. Validate and post the journal.

### Create transactions for the bank commission and the foreign currency amount that is received as a result of the foreign currency purchase

After you post the payment order for a foreign currency purchase, you can register the bank commission and the foreign currency amount that is received as a result of the foreign currency conversion.

1. Go to **Accounts payable \> Payments \> Payment journal**.
2. Create a payment journal.
3. Select **Lines**, create a journal line for the bank commission withdrawal, and enter the following information.

    | Tab     | Field                 | Description |
    |---------|-----------------------|-------------|
    | List    | Account               | Select the vendor account that you used for the foreign currency purchase transaction in the previous procedure. |
    |         | Credit                | Enter the amount of the bank commission. |
    |         | Currency              | Select the currency code of the bank commission. |
    |         | Offset account type   | Select **Ledger**. |
    |         | Offset account        | Select the ledger account for bank commission losses. |
    | Bank    | Bank transaction type | Select the transaction type that has the **Currency purchase** extended type. |
    | Payment | Posting profile       | Verify that the value equals the profile that is used to post to the **Money transfers in transit** ledger account. |

4. Create a journal line for the received foreign currency, and enter the following information.

    | Tab     | Field                                              | Description |
    |---------|----------------------------------------------------|-------------|
    | List    | Account                                            | Select the vendor account that you used for the foreign currency purchase transaction in the previous procedure. |
    |         | Credit                                             | Enter the amount of foreign currency that is received. |
    |         | Currency                                           | Select the code for the foreign currency that is purchased. |
    |         | Offset account type                                | Select **Bank**. |
    |         | Offset account                                     | Select the bank account where the foreign currency is received. The bank of this bank account should have a relation for the vendor account that you selected in the **Account** field. |
    | Bank    | Bank transaction type                              | Select the transaction type that has the **Currency purchase** extended type. |
    | Payment | Currency (under **Currency conversion**)           | Select the accounting currency that is used for the foreign currency purchase. |
    |         | Bank exchange rate (under **Currency conversion**) | Enter the bank exchange rate that was applied to the foreign currency purchase. |
    |         | Posting profile                                    | Verify that the value equals the profile that is used to post to the **Money transfers in transit** ledger account. |

5. Post the journal.

    During posting, the following information is validated:

    - The transaction currency code must differ from the company's accounting currency.
    - The currency code that is selected in the **Currency** field on the **Payment** tab must equal the company's accounting currency.
    - Values must be entered in the **Currency** and **Bank exchange rate** fields on the **Payment** tab.

### Post the settlement of foreign currency purchase transactions

You post the settlement of foreign currency purchase transactions to generate profit/loss transactions from them.

1. Go to **Cash and bank management \> Setup \> Bank groups**.
2. Select a bank, and then select **Functions \> Settle open transactions** to settle foreign currency purchase transactions.
3. Mark transactions for settlement.

    During settlement, the following information is validated:

    - The transaction type of both transactions must have the **Currency purchase** extended type.
    - The value of the **Currency** field in the **Currency conversion** section of the **General** tab for the foreign currency purchase transaction must equal the value of the **Currency** field on **Overview** tab for the transaction for the foreign currency receipt.
    - The bank account that is specified in the **Transit account** field for the foreign currency purchase transaction must equal the bank account where the foreign currency is received.

4. Select **Post**. The transaction for profit or loss from the foreign currency purchase is generated (if, for the foreign currency that is purchased, the bank exchange rate differs from the Central Bank exchange rate on the date of the foreign currency receipt).
5. You can review the transactions that are generated. On the **Bank groups** page, select **Transactions**.
6. You can also post an unsettlement of transactions. On the **Bank groups** page, select **Functions \> Closed transitions editing**, mark transactions, and then select **Reverse**.

## Foreign currency transfers

### Create a foreign currency movement for a foreign currency transfer

1. Go to **Accounts payable \> Payments \> Payment journal**.
2. Create a payment journal.
3. Select **Lines**, create a journal line, and enter the following information.

    | Tab     | Field                 | Description |
    |---------|-----------------------|-------------|
    | List    | Account               | Select the vendor account number that is associated with the bank account that is used for currency conversion transactions. |
    |         | Debit                 | Enter the transaction amount for the foreign currency transfer. |
    |         | Currency              | Enter the code for the currency that is transferred. |
    |         | Offset account type   | Select **Bank**. |
    |         | Offset account        | Select the bank account that the foreign currency transfer is generated from. The bank of this bank account must be associated with the vendor account that you selected in the **Account** field. |
    |         | Method of payment     | Select the method of payment that you created earlier for the transfer of foreign currency transfer. |
    | Bank    | Bank transaction type | Validate the value that is automatically filled in based on the method of payment, or select the transaction type for the foreign currency transfer transaction. |
    | Payment | Posting profile       | Verify that the value equals the profile that is used to post to the **Money transfers in transit** ledger account. |

4. Validate and post the journal.

### Create transactions for the bank commission and the result of the foreign currency transfer

1. Go to **Accounts payable \> Payments \> Payment journal**.
2. Create a payment journal.
3. Select **Lines**, create a journal line for the bank commission withdrawal, and enter the following information.

    | Tab     | Field                 | Description |
    |---------|-----------------------|-------------|
    | List    | Account               | Select the vendor account that is related to the bank account that is used for the foreign currency transfer. |
    |         | Credit                | Enter the amount of the bank commission. |
    |         | Currency              | Select the currency code of the bank commission. |
    |         | Offset account type   | Select **Ledger**. |
    |         | Offset account        | Select the ledger account for bank commission losses. |
    | Bank    | Bank transaction type | Select the transaction type that has the **Currency transfer** extended type. |
    | Payment | Posting profile       | Verify that the value equals the profile that is used to post to the **Money transfers in transit** ledger account. |

4. Create a journal line for receiving the transferred foreign currency, and enter the following information.

    | Tab     | Field                 | Description |
    |---------|-----------------------|-------------|
    | List    | Account               | Select the vendor account that is related to the bank account that is used for the foreign currency transfer. |
    |         | Credit                | Enter the amount of the foreign currency transfer. |
    |         | Currency              | Select the code for the currency that is transferred. |
    |         | Offset account type   | Select **Bank**. |
    |         | Offset account        | Select the bank account where the foreign currency is received. The bank of this bank account should have a relation for the vendor account that you selected in the **Account** field. |
    | Bank    | Bank transaction type | Select the transaction type that has the **Currency transfer** extended type. |
    | Payment | Posting profile       | Verify that the value equals the profile that is used to post to the **Money transfers in transit** ledger account. |

5. Post the journal.

### Post the settlement of foreign currency transfer transactions

You post the settlement of foreign currency purchase transactions to generate foreign currency exchange difference transactions.

1. Go to **Cash and bank management \> Setup \> Bank groups**.
2. Select a bank, and then select **Functions \> Settle open transactions** to settle foreign currency purchase transactions.
3. Mark transactions for settlement.

    During settlement, the following information is validated:

    - The transaction type of both transactions must have the **Currency transfer** extended type.
    - The currency codes of the transactions must be equal.

4. Select **Post**. The exchange rate difference transaction is generated. Ledger accounts for the foreign currency exchange difference are taken from the **Realized gain** and **Realized loss** accounts that are specified in the setup of foreign currency parameters.
5. You can review the transactions that are generated. On the **Bank groups** page, select **Transactions**.
6. You can also post an unsettlement of transactions. On **Bank groups** page, select **Functions \> Closed transitions editing**, mark transactions, and then select **Reverse**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]