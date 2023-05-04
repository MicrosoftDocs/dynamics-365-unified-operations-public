---
title: Payment methods
description: Each payment type that a retailer accepts must be configured when the system is set up. This article describes the payment types that you can set up and describes the process for setting them up.
author: BrianShook
ms.date: 11/03/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: global
ms.author: brshoo
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.custom: 15831
ms.assetid: 465893a5-6b4f-4c5f-b305-db071df2d33f
ms.search.industry: Retail
ms.search.form: RetailTenderTypeTable
---

# Payment methods

[!include [banner](includes/banner.md)]

Each payment type that a retailer accepts must be configured when the system is set up. This article describes the payment types that you can set up and describes the process for setting them up.

Retailers can accept various types of payment in exchange for the products and services that they sell. Although cash is the most common form of payment, retailers can also receive payment in the form of checks, cards, vouchers, and so on. Each payment type that the retailer accepts must be configured in Dynamics 365 Commerce when the system is set up. The following list describes each payment type that can be set up:

- **Cash** – Money in the physical form of currency, such as banknotes and coins. This currency can be either the company currency or the store's local currency.
- **Check** – A negotiable instrument that instructs payment of a specific amount of a specific currency, and that is drawn on a specific bank. A check is typically valid either indefinitely or for six months after the date of issue, unless another period of validity is specified. This period varies, depending on the bank that the check is drawn on. There are various kinds of checks, such as order checks, counter checks, bearer checks, and account payee checks. You can set up checks as a payment method for each store. Checks can be accepted in the currency that is defined at either the company level or the store level. You must set up checks as a payment method before you can accept a check as payment in a store.
- **Currency** – The primary form of payment other than the company's default currency. Coins and paper money are both forms of currency. The currency payment method represents all currency that is used. Before you can use this payment method, you must set up currencies and specify exchange information for the currencies.
- **Card** – All the kinds of cards that are used, such as debit cards and credit cards. It's a good idea to set up one card payment method at the organization level, to represent every kind of card. Then, at the store level, set up a payment method for each card or set of cards that is processed by using the same settings. You must set up the manufacturer cards that are available in the market, such as debit cards and credit cards, before you can accept the cards as payment in a store.
- **Credit memo** – Credit memos that are issued or redeemed at the point of sale. The credit memo can be a credit or a return credit memo that is issued against a return sale. If credit memos are only partially redeemed, the program issues a new credit memo for the new balance. The new credit memo has a new number. A credit memo can be used only one time, and the system keeps a record of all the numbers that are used. The record can be viewed on the **Credit memo table** page. A customer can't redeem more than the value of the credit memo.
- **Gift Card** – Gift cards that are issued and redeemed at the point of sale. Overpayment isn't allowed on gift cards. All gift cards should have card number mappings. 
- **Customer account** – Payments that can be charged to a customer account at the register at the time of the sale. You can also use this payment method to collect sales information or customer-specific discounts when the customer makes a payment by using another payment method. In this case, you must set up customer-specific information.
- **Loyalty points** – The points that customers accumulate through loyalty programs. If you create loyalty programs, customers can earn points and then redeem them in various ways. For example, in some loyalty programs, customers can redeem loyalty points in the form of a discount or even use them as a form of payment.

To set up payment methods, you must complete the following tasks.

1. Set up payment methods for an organization. Create the payment methods that are accepted by the whole organization.
2. Create organization-wide card types and card numbers. If credit cards or debit cards are accepted, you must create one payment method for cards, and then create the organization-wide card types and card numbers. See below section **Card Types** for additional information.
3. Set up store payment method. Associate payment methods with each store, and then enter the store-specific settings for each payment method.
4. Set up card payment methods for stores. For any card payment methods that the store accepts, complete the card setup.

## Card Types
To configure Card Types for the environment, follow these steps:

1. In Headquarters, navigate to **Retail and Commerce > Channel setup > Payment methods > Card types**.
2. In the **Electronic payment types** section, click **New**.
3. Fill out the **ID**, **Electronic payment name**, **Type**, and **Issuer** value for the record.

Next, the mapping parameters for the record must be set to properly associate the Card Type to the payment method used in a transaction for financial reporting in Dynamics. Two methods of mapping are offered:
 - **Processor mapping**: available when the feature management **Enhanced wallet support and payment improvements** feature is enabled. This mapping is used to map a card type when received from a designated payment connector and the returned issuer string from the payment gateway. See information about setting up Processor mapping [here](https://learn.microsoft.com/en-us/dynamics365/commerce/wallets#processor-payment-method-mapping).
 - **Card numbers**: this is a card bin range listing used to match the card number used at payment to the card type for processing and reporting in the Commerce system. 

The system uses the **Card numbers** mapping to check a **Card number from** value at the beginning of the number provided, to the **Card number to** value within the set length of the **Digits to identify** value.  

The below table represents an example set of **Card number** mappings, but is **not** an official prescribed set of values from Microsoft (as values can change by issuers). Your payment gateway service can advise further on recommended mappings. In many cases, a smaller range (1 or 2 digits) is less complex to implement and may catch broader card scenarios.

| Card ID   | Card number from | Card number to | Digits to identify |
| --------- | ---------------- | -------------- | ------------------ |
| AMEXPRESS | 37               | 37             | 2                  |
| DISCOVER  | 60               | 69             | 2                  |
| EUROCARD  | 4511             | 4512           | 4                  |
| EXTGIFT   | 6                | 6              | 1                  |
| GIFTCARD  | 9                | 9              | 1                  |
| LOYALTY   | 100000           | 200000         | 6                  |
| MAESTRO   | 56               | 56             | 2                  |
| MAESTRO   | 6                | 6              | 1                  |
| MASTER    | 5                | 5              | 1                  |
| VISA      | 4                | 4              | 1                  |
| VISA      | 4507             | 4508           | 4                  |
| VISAELEC  | 5802             | 5803           | 4                  |


Note that if using the **Processor mapping**, **Card numbers** is used as a backup if the processor mapping is unable to make a match. If neither match, a default can be set per store in the **General** tab, set for the **Electronic Payments: Default for unmapped processor payments** field. Otherwise, without a default set- the Commerce system will decline the authorization attempt protectively.

Additionally, when creating or updating the **Card numbers** in the Commerce system, be sure to run the **1070** (Channel configuration) and **1110** (Global configuration) distribution schedules. Allow 15 minutes after these jobs have completed to update the Retail Server cache in order for the changes take effect.

## Handle change tendering for payment methods

Some payment methods don't support direct change tendering if funds are due back to customers during point-of-sale transactions. Only the **Cash** and **Currency** payment methods can be used to tender change. 

To handle cases where change tendering is required during a transaction, but the payment method doesn't support it, you can define a **Change tender** payment method. When you set up store payment methods for the store, select the payment method to use. Then, in the **Change** section, in the **Change tender** field, enter a change tender payment option. For example, you can enter **1** to indicate that cash can be used as a change tender payment option.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
