---
# required metadata

title: 
description: 
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

# Currency sale and purchase

The functionality allows you to do the following:
- Register the transactions for the sale, purchase and transfer of currency which is carried out using the ledger account "Money transfers in transit";
- Automatically calculate the profit / loss amounts because of currency conversion for currency sale/purchase (the currency exchange rate of the Central Bank and the exchange rate of the legal entity’s bank on the date of currency transfer are considered for calculation). Automatically create the transactions on profit / loss from conversion (purchase / sale of currency),
- Automatically generate the transactions on the unrealized exchange rate difference, if the exchange rate of the sold currency on the currency sale date differs from the rate of this currency on the date when rubles received for sold currency.
- Print currency transfer order.

## Setting up currency sale and purchase.

Complete the following tasks to calculate the exchange adjustment and profit or loss on the Remittance en route account:
- Set up an exchange rate
- Set up a bank transaction type
- Set up a method of payment
- Set up a number sequence
- Set up a bank
- Set up a bank account


### Set up an exchange rate

Use the **Currency revaluation accounts** page to set up the loss or gain calculation for currency exchange.

1.	Go to **General ledger > Currencies > Currency parameters**.
2.	In the **Legal entities** field, select a company.
3.	On the **General** FastTab, in the **Ledger posting** grid, select the main accounts to post the exchange rate profits or losses for ledger transactions.
4.	On the **Sales/customers** FastTab, in the **Customer posting** grid, select the main accounts to post the exchange rates profits or losses for customer transactions.
5.	In the **Expense code** field, select the expense code that corresponds to the transaction for an exchange rate loss that occurs when transactions are settled for a customer. 
6.	In the **Revenue code** field, select the revenue code that corresponds to the transaction for an exchange rate profit that occurs when transactions are settled for a customer. 
7.	On the **Purchases/Vendors** FastTab, in the **Vendor posting** grid, select the main accounts for vendor posting.
8.	In the **Revenue code (currency conversion)** field, select the revenue code for a currency conversion transaction if the exchange adjustment is a profit.
9.	In the **Expense code (currency conversion)** field, select the revenue code for a currency conversion transaction if the exchange adjustment is a loss.
10.	On the **Purchases/Advance holders** FastTab, select the relevant main accounts for advance holder posting.
11.	In the **Expense code** field, select the expense code that corresponds to the transaction for an exchange rate loss that occurs when transactions are settled for an advance holder.
12.	In the **Revenue code** field, select the revenue code that corresponds to the transaction for an exchange rate profit that occurs when transactions are settled for an advance holder.


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
