---
# required metadata

title: Foreign currency sale, purchase and transfer
description: The article describes the functionality for registering the transactions for the sale, purchase and transfer of currency.
author: anasyash
manager: AnnBe
ms.date: 09/25/2018
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
ms.author: anasyash
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# <enter title here>

[!include [banner](../includes/banner.md)]

# Foreign currency sale, purchase and transfer

Finance and Operations lets you complete the following tasks:
- Register transactions for the sale, purchase and transfer of currency which is carried out using the ledger account **Money transfers in transit**
- Automatically calculate the profit/loss amounts because of currency conversion for currency sale/purchase (the currency exchange rate of the Central Bank and the exchange rate of the legal entity’s bank on the date of currency transfer are considered for calculation). Automatically create the transactions on profit / loss from conversion (purchase / sale of currency),
- Automatically generate the transactions on the unrealized exchange rate difference, because of different exchange rates on the currency transactions dates.
- Print currency transfer order.

<give here links to places in this document>
     Set up (Setting up currency sale and purchase.)
     Currency sale (Create a currency sale transaction)
     Currency purchase (Create a currency purchase transaction)
     Currency transfer (Create a currency transfer transaction)

## Setting up currency sale and purchase.

Complete the following tasks to calculate the exchange adjustment and profit or loss on the Remittance en route account:
- [Set up an exchange rate](#set-up-an-exchange-rate)
- [Set up a bank which is used in currency conversion transactions](#set-up-a-bank-which-is-used-in-currency-conversion-transactions)
- [Set up a bank transaction type](#set-up-a-bank-transaction-type)
- [Set up a method of payment](#set-up-a-method-of-payment)
- [Set up a number sequence](#set-up-a-number-sequence)
- [Set up a bank account](#set-up-a-bank-account)


### Set up an exchange rate

Use the **Currency revaluation accounts** page to set up the loss or gain calculation for currency exchange.

1.	Go to **General ledger > Currencies > Currency parameters**.
2.	In the **Legal entities** field, select a company.
3.	On the **Purchases/Vendors** FastTab, define 

- ledger accounts for currency conversion: **Conversion gain** and **Conversion loss**.
- revenue and income codes for currency conversion: **Revenue code (currency conversion)**, **Expense code (currency conversion)**.


### Set up a bank which is used in currency conversion transactions

Use the **Banks** page to associate the vendor account with bank which will be used in currency sale or purchase transactions.

1.	Go to **Cash and bank management > Setup > Bank groups**. Create a new bank or choose existing.
2.	On the **General** FastTab, in the **Vendor account** field, select the vendor account.

When you associate a bank with the vendor, the buttons **Transactions**, **Functions > Settle open transactions**, **Functions > Closed transactions editing** are available in the Action page.

### Set up a bank transaction type

Use the **Bank transaction types** page to set up a bank transaction type for currency sale, purchase, and transfer transactions.

1.	Go to **Cash and bank management > Setup > Bank transaction types**. Create a new bank transaction type. 
2.	In the **Transaction extended type** field, select the currency transfer type from the following options: “Currency sale”, “Currency purchase”, “Currency transfer”
3.	In the **Vendor posting profile** field, select the vendor posting profile for the money in transit posting.

### Set up a method of payment

Use the **Methods of payment** page to set up a method of payment for currency sale, purchase or transfer.

1.	Go to **Accounts payable > Setup > Payment setup > Methods of payment**. Create a new line.
2.	On the **General** FastTab, In the **Account type** field, select “Bank” and in the **Payment account** field, select the bank account from which the currency is transferred for this method of payment. 
3.	In the **Bank transaction type** field, select the bank transaction type for currency sale, purchase or transfer.
4.	On the **File formats** FastTab, in the **Export format** field, select “Currency transfer order”.
Note. If “Currency transfer order” is not available, click **Setup** to open the **File formats for methods of payment** page.
On the **Export** tab, in the **Available** list, select “Currency transfer order”.

### Set up a bank account

Use the **Bank accounts** page to set up specific information for currency sale / purchase.

1.	Go to **Cash and bank management > Bank accounts**. Create a new bank account or choose existing.
2.	On the **Payment management** FastTab, in the **Order template (currency purchase)** and **Order template (currency sale)** fields, select the Microsoft Office Word template.

Find more details in the topic https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/rus-local-settings-req-bank-mod/articles/financials/localizations/rus-local-settings-requisites-bank-module.md


### Set up a number sequence

Use the **Cash and bank management parameters** page to assign a number sequence for currency transactions. 

1.	Go to **Cash and bank management > Setup > Cash and bank management parameters**.
2.	On the **Number sequences** tab, in the Number sequence code field, select the number sequence for the reference **Currency transfer order**

## Create a currency sale transaction

### Create a foreign currency sale transaction

1.	Go to **Accounts payable > Payments > Payment journal**. Create a new payment journal.
2.	Click **Lines** and create a new journal line.
In the **Account** field, select the vendor account number which is associated with Bank account used for currency conversion transactions.
3.	In the **Debit** field, enter the transaction amount in currency which is ordered to be sold.
4.	In the **Currency** field, specify the currency code which is ordered to be sold.
5.	In the **Offset account type** and **Offset account** fields, select “Bank” and the Bank account.
6.	In the **Method of payment** field, select the method of payment for the currency sale created earlier.
7.	On the **Bank** tab, in the **Bank transaction type** field, validate the value, which is automatically filled from the Method of payment, or select the transaction type for the currency sale transaction.
8.	On the **Payment** tab, validate the vendor posting profile in the **Posting profile** field. It should contain the profile for posting on ledger account “money in transit”.
9.	Click **Generate payments**. 
10.	Select **Export format**, and then in the **Export format** field, select **Currency transfer order**. Or Select **Method of payment** and select the method of payment for currency sale.
11.	In the **Bank account** field, select the bank account for the payment. Click **OK**. 
12.	In the opened **Bank currency transfer** dialog and fill required information:
<add here screenshot Bank currency transfer>

| **Field** | **Comment** |
|----------|----------|
| **Worker** | Select the worker responsible for currency sale |
| **Transit account** | Select the bank account where rubles for sold currency should be received (result of currency conversion). Template for printing currency sales order is taken from this bank account |
|**Currency** | Choose currency of money to be received on transit account after foreign currency sale |
| **Bank exchange rate** | Identify currency exchange rate of currency conversion, for printing in the currency sale order |
| **Supplier account**, **Purchase agreement** | Select information about contract in currency which is the basis for currency sale transaction |
| **Print Document** | Enable parameter to print Currency sale order along with payment generation |

13.	Click **OK**. The Payment status field of the payment journal line is updated as **Sent**. 
The **Transit account**, **Foreign counteragent**, **Contracts group**, and **Contract of the deal** fields are updated on the **Payment** tab.
14.	Click **Print > Currency sale order** to print the currency sales order. The report contains the following information:
15.	Validate and post the journal


### Create transactions for bank commission and received currency as result of foreign currency sale.

After you have posted payment order for currency sale, you can register bank commission and received currency (rubles) as result from the currency conversion. 

1.	Go to **Accounts payable > Payments > Payment journal**. Create new journal. Click **Lines**
2.	Create a new line for bank commission withdrawal. Fill the fields in line:

| **Field** | **Description** |
|-----------|---------------|
|**Account** | Select the vendor account used on the previous step in currency sale transaction |
|**Credit** | Enter the bank commission amount |
| **Currency** | Select the currency of bank commission |
|**Offset account type**| Select **Ledger** |
|**Offset account**| Select the Ledger account for bank commission losses |.
|Tab **Bank** | |
|**Bank transaction type**| Select the transaction type with extended type **Currency sale** |
|Tab **Payment** | |
|**Posting profile** | Review that the value equals to the profile for posting on ledger account “money in transit”|

3.	Create a new line for received currency. Fill the fields in line:

| **Field** | **Description** |
|-----------|---------------|
|**Account** | Select the vendor account used on the previous step in currency sale transaction |**Credit** | Enter the amount of received currency|
|**Currency**| Select the accounting currency which is a currency received as result of foreign currency sale. The selected currency must be equal to accounting currency|
|**Offset account type**| Select **Bank** |
|**Offset account**| Select the Bank account to which the accounting currency is received |
|Tab **Bank** | |
|**Bank transaction type**| Select the transaction type with extended type **Currency sale** |
|Tab **Payment**, group of fields **Currency conversion**| | |
| **Currency** | Select the currency which was sold. The selected currency must differ from the accounting currency |
| **Bank exchange rate** | Enter the bank exchange rate which was applied for foreign currency sale. |
|Tab **Payment** | |
|**Posting profile** | Review that the value equals to the profile for posting on ledger account “money in transit”|

4.	Post the journal.

### Post settlement of currency sale transactions

Post settlement of currency sale transactions to generate profit and loss transactions from the currency sale and currency exchange difference transactions.

1.	Go to **Cash and bank management > Setup > Bank groups** to open list of banks.
2.	Select a bank, and then click **Functions > Settle open transactions** to settle currency sale transactions.
3.	In the **Settlement posting date** field, select the posting date type: **Latest date**, **Today’s date** or **Selected date**, enter the posting date manually if you have chosen the latter.
4.	Review transactions to be settled: 

     -	Tab **Overview** contains information specific to currency sale the fields **Transit account** and **Bank account - inflow**:

          Positive transactions have in the field **Transit account** the value equal to the transit bank account which was defined by user on the dialog **Bank currency transfer** in the field **Transit account** for currency sale transaction.

          Negative transactions have in the field **Bank account - inflow** the value equal to the bank account to which the accounting currency amount is received as result of the foreign currency sale transaction.

          Values in these fields should be equal in transactions marked for settlement. 

-	Tab **General** contains information specific to currency sale, in the group of fields **Currency conversion**

5.	Mark transactions for settlement. The following information is validated during settlement:

     -	Both transactions have **Transaction type** of extended type **Currency sale**
     -	The value in the field **Currency** of group **Currency conversion** on tab **General** of positive transaction (foreign currency sale) is equal to the value in the field **Currency** on tab **Overview** of negative transaction (accounting currency receipt as result of foreign currency sale)
     -	The bank account number specified in the **Transit account** field of positive transaction is equal to the account number specified in the field **Bank account - inflow** of negative transaction.

6.	Click **Post**. As result, the following transactions are generated:
     -	Unrealized currency exchange difference (if the currency exchange rate of sold foreign currency on the date of currency sale differs from the currency exchange rate of sold foreign currency on the accounting currency receipt date)
     -	Currency sale profit or loss (in case of bank exchange rate of sold foreign currency differs from the Central bank exchange rate of sold foreign currency on the date of accounting currency receipt transaction)

7.	You can review the generated transactions in the page **Bank groups** by clicking the **Transactions** button.
8.	You can also post unsettlement of transactions. In the page **Bank groups** click **Functions >> Closed transitions editing**, mark transactions and click **Reverse**.



## Create a currency purchase transaction

### Create a transaction of rubles movement for currency purchase

1.	Go to **Accounts payable > Payments > Payment journal**. Create a new payment journal.
2.	Click **Lines** and create a new journal line. 

|**Field** | **Description** | 
|----------|-----------------|
|**Account**| Select the vendor account number which is associated with Bank account used for currency conversion transactions. This value is filled automatically when the bank account is selected in the **Offset account** field and if **Debit** field has amount and **Bank transaction type** contains the transaction of extended type Value |
| **Debit**, **Currency** | Enter the transaction amount in accounting currency which is rubles and the code of accounting currency|
| **Offset account type**, **Offset account** |  Select “Bank” and the Bank account where from rubles are moved for currency purchase|.
| **Method of payment** | Select the method of payment for the currency purchase created earlier|
| Tab **Bank** | |
| **Bank transaction type** | Validate the value, which is automatically filled from the **Method of payment**, or select the transaction type for the currency purchase transaction|
| Tab **Payment** ||
| **Posting profile** | Validate the value, which should contain the profile for posting on ledger account “money in transit”|

3.	Click **Generate payments**.
4.	Select **Method of payment** and select the method of payment for currency purchase.
5.	In the **Bank account** field, select the bank account for the payment. Click **OK**.
6.	In the opened **Bank currency transfer** dialog and fill required information:

|**Field**|	**Comment**|
|---------|---------|
|**Worker**|	Select the worker responsible for currency purchase|
|**Transit account**|	Select the bank account where foreign currency purchased should be received (result of currency conversion)|
|**Currency**|	Choose currency of money to be received on transit account after foreign currency purchase|
|**Bank exchange rate**|	Identify currency exchange rate of currency conversion, for printing in the currency purchase order|
|**Supplier account**, **Purchase agreement**|	Select information about contract in currency which is the basis for currency purchase transaction|
|**Print Document**|	Enable parameter to print Currency purchase order along with payment generation|

7.	Click **OK**. The Payment status field of the payment journal line is updated as **Sent**. 

     The **Transit account**, **Foreign counteragent**, **Contracts group**, and **Contract of the deal** fields are updated on the **Payment** tab.

     The following is validated during currency purchase order generation: 
     -	Currency of **Transit account** is not equal to the accounting currency. 
     -	Currency of **Transit account** is equal to the currency chosen in the **Bank currency transfer** dialog.
     -	Currency of the payment journal line is accounting currency.

8.	Click **Print > Currency purchase order** to print the currency purchase order (the template is taken from the transit bank account of **Bank currency transfer** dialog).
9.	Validate and post the journal

### Create transactions for bank commission and received currency as result of foreign currency purchase.

After you have posted payment order for currency purchase, you can register bank commission and received foreign currency as result from the currency conversion. 

1.	Go to **Accounts payable > Payments > Payment journal**. Create new journal. Click **Lines**
2.	Create a new line for bank commission withdrawal. Fill the fields in line:

| **Field** | **Description** |
|-----------|---------------|
|**Account** | Select the vendor account used on the previous step in currency purchase transaction |
|**Credit** | Enter the bank commission amount |
| **Currency** | Select the currency of bank commission |
|**Offset account type**| Select **Ledger** |
|**Offset account**| Select the Ledger account for bank commission losses |.
|Tab **Bank** | |
|**Bank transaction type**| Select the transaction type with extended type **Currency purchase** |
|Tab **Payment** | |
|**Posting profile** | Review that the value equals to the profile for posting on ledger account “money in transit” |

3.	Create a new line for received currency. Fill the fields in line:

| **Field** | **Description** |
|-----------|---------------|
|**Account** | Select the vendor account used on the previous step in currency purchase transaction |**Credit** | Enter the amount of received foreign currency|
|**Currency**| Select the code of the purchased currency|
|**Offset account type**| Select **Bank** |
|**Offset account**| Select the Bank account to which the foreign currency is received. Bank of this bank account should have a relation for the vendor account chosen in the field **Account** |
|Tab **Bank** | |
|**Bank transaction type**| Select the transaction type with extended type **Currency purchase** |
|Tab **Payment**, group of fields **Currency conversion**| | |
| **Currency** | Select the accounting currency which is used for foreign currency purchase|
| **Bank exchange rate** | Enter the bank exchange rate which was applied for foreign currency purchase |
|Tab **Payment** | |
|**Posting profile** | Review that the value equals to the profile for posting on ledger account “money in transit”|

4.   Post the journal.
The following criteria are validated during posting:
     -	The transaction currency must not be equal to the accounting currency of the company.
     -	The currency code in the field **Currency** on the **Payment** tab is equal to the accounting currency of the company.
     -	The fields **Currency** and **Bank exchange rate** on the **Payment** must be filled out.

### Post settlement of currency purchase transactions

Post settlement of currency purchase transactions to generate profit and loss transactions from the currency purchase

1.	Go to **Cash and bank management > Setup > Bank groups** to open list of banks.
2.	Select a bank, and then click **Functions > Settle open transactions** to settle currency purchase transactions.
3.	Mark transactions for settlement. The following information is validated during settlement:

     -    Both transactions have **Transaction type** of extended type **Currency purchase**
     -	The value in the field **Currency** of group **Currency conversion** on tab **General** of foreign currency purchase transaction is equal to the value in the field **Currency** on tab **Overview** of transaction for foreign currency receipt.
     -	The bank account number specified in the **Transit account** field of foreign currency purchase transaction is equal to the bank account where the foreign currency is received.

4.	Click **Post**. As result, the transaction for profit or loss from the currency purchase is generated (in case of bank exchange rate of purchased foreign currency differs from the Central bank exchange rate of purchased foreign currency on the date of foreign currency receipt)

5.	You can review the generated transactions on the page **Bank groups** by clicking the **Transactions** button.
6.	You can also post unsettlement of transactions. In the page **Bank groups** click **Functions >> Closed transitions editing**, mark transactions and click **Reverse**.


## Create a currency transfer transaction

### Create a currency movement for currency transfer

1.	Go to **Accounts payable > Payments > Payment journal**. Create a new payment journal.
2.	Click **Lines** and create a new journal line. 

|**Field** | **Description** | 
|----------|-----------------|
|**Account**| Select the vendor account number which is associated with Bank account used for currency conversion transactions
| **Debit**, **Currency** | Enter the transaction amount and currency code for currency transfer|
| **Offset account type**, **Offset account** | Select “Bank” and the Bank account where from the currency transfer is generated. The bank of the selected bank account must be associated with the vendor account chosen in the field “Account”|.
| **Method of payment** | Select the method of payment for the currency transfer created earlier|
| Tab **Bank** | |
| **Bank transaction type** | Validate the value, which is automatically filled from the **Method of payment**, or select the transaction type for the currency transfer transaction|
| Tab **Payment** ||
| **Posting profile** | Validate the value, which should contain the profile for posting on ledger account “money in transit” |

3.	Validate and post the journal

### Create transactions for bank commission and result of currency transfer

1.	Go to **Accounts payable > Payments > Payment journal**. Create new journal. Click **Lines**
2.	Create a new line for bank commission withdrawal. Fill the fields in line:

| **Field** | **Description** |
|-----------|---------------|
|**Account** | Select the vendor account related to bank account of currency transfer |
|**Credit** | Enter the bank commission amount |
| **Currency** | Select the currency of bank commission |
|**Offset account type**| Select **Ledger** |
|**Offset account**| Select the Ledger account for bank commission losses |.
|Tab **Bank** | |
|**Bank transaction type**| Select the transaction type with extended type **Currency transfer** |
|Tab **Payment** | |
|**Posting profile** | Review that the value equals to the profile for posting on ledger account “money in transit” |

3.	Create a new line for receiving transferred currency

| **Field** | **Description** |
|-----------|---------------|
|**Account** | Select the vendor account related to bank account used in currency transfer| |**Credit** | Enter the amount of transferred currency|
|**Currency**| Select the code of the transferred currency|
|**Offset account type**| Select **Bank** |
|**Offset account**| Select the Bank account to which the foreign currency is received. Bank of this bank account should have a relation for the vendor account chosen in the field **Account** |
|Tab **Bank** | |
|**Bank transaction type**| Select the transaction type with extended type **Currency transfer** |
|Tab **Payment** | |
|**Posting profile** | Review that the value equals to the profile for posting on ledger account “money in transit” |

4.	Post the journal.

### Post settlement of currency transfer transactions

Post settlement of currency purchase transactions to generate currency exchange difference transactions.

1.	Go to **Cash and bank management > Setup > Bank groups** to open list of banks.
2.	Select a bank, and then click **Functions > Settle open transactions** to settle currency purchase transactions.
3.	Mark transactions for settlement. The following information is validated during settlement:

     -	Both transactions have **Transaction type** of extended type **Currency transfer**
     -	Currency codes of transactions are equal

4.	Click **Post**. As result, the exchange rate difference transaction is generated. Ledger accounts for currency exchange difference are taken from the **Realized gain** and **Realized loss* accounts of the currency parameters setup.

5.	You can review the generated transactions on the page **Bank groups** by clicking the **Transactions** button.
6.	You can also post unsettlement of transactions. In the page **Bank groups** click **Functions >> Closed transitions editing**, mark transactions and click **Reverse**.
