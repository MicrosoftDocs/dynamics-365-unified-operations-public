---
# required metadata

title: Payment methods
description: Each payment type that a retailer accepts must be configured when the system is set up. This article describes the payment types that you can set up and describes the process for setting them up.
author: MargoC
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: MargoC
ms.search.scope: AX 7.0.0, Operations, Core, Retail
# ms.tgt_pltfrm: 
ms.custom: 15831
ms.assetid: 465893a5-6b4f-4c5f-b305-db071df2d33f
ms.search.region: global
ms.search.industry: Retail
ms.author: yabinl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Payment methods

[!include[banner](includes/banner.md)]


Each payment type that a retailer accepts must be configured when the system is set up. This article describes the payment types that you can set up and describes the process for setting them up.

Retailers can accept various types of payment in exchange for the products and services that they sell. Although cash is the most common form of payment, retailers can also receive payment in the form of checks, cards, vouchers, and so on. Each payment type that the retailer accepts must be configured in Dynamics 365 for Retail when the system is set up. The following list describes each payment type that can be set up in Dynamics 365 for Retail:

-   **Cash** – Money in the physical form of currency, such as banknotes and coins. This currency can be either the company currency or the store's local currency.
-   **Check** – A negotiable instrument that instructs payment of a specific amount of a specific currency, and that is drawn on a specific bank. A check is typically valid either indefinitely or for six months after the date of issue, unless another period of validity is specified. This period varies, depending on the bank that the check is drawn on. There are various kinds of checks, such as order checks, counter checks, bearer checks, and account payee checks. You can set up checks as a payment method for each store. Checks can be accepted in the currency that is defined at either the company level or the store level. You must set up checks as a payment method before you can accept a check as payment in a store.
-   **Currency** – The primary form of payment other than the company's default currency. Coins and paper money are both forms of currency. The currency payment method represents all currency that is used. Before you can use this payment method, you must set up currencies and specify retail exchange information for the currencies.
-   **Card** – All the kinds of cards that are used, such as debit cards and credit cards. It's a good idea to set up one card payment method at the organization level, to represent every kind of card. Then, at the store level, set up a payment method for each card or set of cards that is processed by using the same settings. You must set up the manufacturer cards that are available in the market, such as debit cards and credit cards, before you can accept the cards as payment in a store.
-   **Credit memo** – Credit memos that are issued or redeemed at the point of sale. The credit memo can be a credit or a return credit memo that is issued against a return sale. If credit memos are only partially redeemed, the program issues a new credit memo for the new balance. The new credit memo has a new number. A credit memo can be used only one time, and the system keeps a record of all the numbers that are used. The record can be viewed on the **Credit memo table** page. A customer can't redeem more than the value of the credit memo.
-   **Gift Card** – Gift cards that are issued and redeemed at the point of sale. Overpayment isn't allowed on gift cards.
-   **Customer account** – Payments that can be charged to a customer account at the register at the time of the sale. You can also use this payment method to collect sales information or customer-specific discounts when the customer makes a payment by using another payment method. In this case, you must set up customer-specific information.
-   **Loyalty points** – The points that customers accumulate through loyalty programs. If you create loyalty programs, customers can earn points and then redeem them in various ways. For example, in some loyalty programs, customers can redeem loyalty points in the form of a discount or even use them as a form of payment.

To set up payment methods, you must complete the following tasks.

1.  Set up payment methods for an organization. Create the payment methods that are accepted by the whole organization.
2.  Create organization-wide card types and card numbers. If credit cards or debit cards are accepted, you must create one payment method for cards, and then create the organization-wide card types and card numbers.
3.  Set up store payment method. Associate payment methods with each store, and then enter the store-specific settings for each payment method.
4.  Set up card payment methods for stores. For any card payment methods that the store accepts, complete the card setup.




