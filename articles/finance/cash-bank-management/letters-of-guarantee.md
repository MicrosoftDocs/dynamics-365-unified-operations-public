---
# required metadata

title: Letters of guarantee
description: This article provides information about letters of guarantee. In a letter of guarantee, a bank agrees to pay a specific amount of money to a person if one of the bank's customers defaults on a payment or obligation to that person. 
author: angelad116
ms.date: 10/24/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BankLGGuarantee
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 5c0b5e37-d51d-4a01-bb37-1882173abb9f
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Letters of guarantee

[!include [banner](../includes/banner.md)]

This article provides information about letters of guarantee. In a letter of guarantee, a bank agrees to pay a specific amount of money to a person if one of the bank's customers defaults on a payment or obligation to that person. 

A letter of guarantee is an agreement by a bank (the guarantor) to pay a set amount of money to some person (the beneficiary) if a bank customer (the principal) defaults on a payment or an obligation to the beneficiary. Letters of guarantee aren't transferable. They apply only to the beneficiary who is named in the agreement. The principal can request an increase or decrease in the value of a letter of guarantee, subject to the terms of the agreement. 

To liquidate a letter of guarantee, the beneficiary must submit the original letter of guarantee and inform the bank of the principal’s default before the expiration date. The bank then pays the amount that is due to the beneficiary's account, according to the terms in the letter of guarantee. The bank reserves a percentage of the payment as a margin. The percentage is agreed upon and specified in the terms of the agreement. 

You can create a code to track the purpose of a letter of guarantee. You can also specify the reasons that can be associated with a letter of guarantee when the letter is canceled. You can view the purpose codes and bank reasons on the **Payment purpose codes** and **Bank reasons** pages. 

You can use the **Letter of guarantee** page to complete these tasks:

-   Create correct ledger entries, and eliminate manual entry.
-   Record all monetary and nonmonetary transactions, and track balances of letters of guarantee.
-   Record and track the status and expiration of letters of guarantee.
-   Generate a report that lists the banks that are holding letters of guarantee.

The following table describes the actions that you can perform on a letter of guarantee.

| Action              | Purpose                                                                                                                   |
|---------------------|---------------------------------------------------------------------------------------------------------------------------|
| Submit to bank      | Submit the letter of guarantee request to the bank.                                                                       |
| Receive from bank   | After the bank agrees to the submitted request, collect the letter of guarantee from the bank.                            |
| Give to beneficiary | After you receive the letter of guarantee from the bank, provide the letter of guarantee to the beneficiary.              |
| Increase value      | If the beneficiary and the principal agree, increase the monetary value.                                                  |
| Decrease value      | If the beneficiary and the principal agree, decrease the monetary value.                                                  |
| Extend              | After you provide the letter of guarantee to the beneficiary, extend the period of validity, if an extension is required. |
| Cancel              | When the purpose that the letter of guarantee was requested for no longer applies, cancel the agreement.                  |
| Liquidate           | When the beneficiary presents the letter of guarantee to the bank, cash out the letter of guarantee.                      |


For more information, see the following topics:

[Letter of guarantee transaction](tasks/letter-guarantee-transaction.md)

[Set up bank facilities and posting profiles for letters of guarantee](tasks/set-up-bank-facilities-posting-profiles.md)




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
