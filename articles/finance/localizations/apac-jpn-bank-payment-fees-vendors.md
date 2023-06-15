---
# required metadata

title: Bank payment fees covered by vendors in Japan
description: This article answers some of the frequently asked questions about bank payment fees that are covered by vendors in Japan.
author: EricWangChen
ms.date: 03/21/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PaymFeeBankRule_JP, VendPaymFeeGroup_JP, VendPaymModeFee
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: aa8a8ef3-1e5e-4174-817b-3b98e1e51509
ms.search.region: Japan
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Bank payment fees covered by vendors in Japan

[!include [banner](../includes/banner.md)]

In Japan, the bank payment fees are usually covered by vendors (the receiving party). This article answers some of the frequently asked questions about bank payment fees that are covered by vendors.

When you make payments to a vendor, the bank payment fees can be covered by you or by the vendor. When the vendor covers the bank payment fees, you can set up the process in such a way that bank payment fees are automatically deducted from each payment that the company makes to the vendor. Complete the following tasks to set up and calculate the bank payment fees for a vendor:

1.  Indicate that the vendor covers the bank payment fees.
2.  Create a payment rule to calculate the bank payment fees that are deducted from payments that the company makes to the vendor.
3.  Set up a payment fee by using the payment rule.
4.  Create and post a payment for the vendor who pays the bank payment fees.
5.  Generate the payment file.

## Can I specify criteria that I can use to calculate bank payment fees?
Yes. On the **Bank rules for payment fee** page, you can create a bank rule to set up criteria that you can use to calculate payment fees. After you create the bank rule, you can use it to set up a payment fee on the **Payment fee** page. For example, you can create the following rules for bank accounts.

| Condition for the rule                               | ID                | Third party bank group | Relationship | Company bank group |
|------------------------------------------------------|-------------------|------------------------|--------------|--------------------|
| Bank accounts in the same bank                       | Bank\_Same        | Bank code              | =            | Bank code          |
| Bank accounts in different branches of the same bank | Branch\_Different | Bank code              | =            | Bank code          |
|                                                      |                   | Branch code            | &lt;&gt;     | Branch code        |
| Bank accounts in different banks                     | Bank\_Diff        | Bank code              | &lt;&gt;     | Bank code          |

## Can I set up a rule to compare values?
Yes. You can set up a rule to compare the value that you specify in the **Value** field to the filter value that you select in the **Third party bank group** field on the **Bank rules for payment fee** page. For example, to create a bank rule that applies to a bank that has a bank code of 001, select **Bank code** in the **Third party bank group** field, select **=** in the **Relationship** field, and then enter **001** in the **Value** field.

| Condition for the rule                     | Third party bank group | Relationship | Value |
|--------------------------------------------|------------------------|--------------|-------|
| A bank account that is assigned to a value | Bank code              | =            | 001   |

## How can I calculate the consumption tax on the bank payment fees?
To calculate the consumption tax on the bank payment fees, set up the following information on the **General** tab of the **Payment fee setup** page:

-   Specify whether the payment amounts in the **Fee amount** field include taxes. To include sales tax in the fee amount, on the **Payment journal** page, on the **Setup** tab, select the **Amounts include sales tax** check box.
-   In the **Method of payment** field, select the payment method.
-   In the **Percentage/Amount** field, select **Percent**.
-   In the **Fee amount** field, specify the payment fee percentage.
-   In the **Minimum** and **Maximum** fields, set the payment threshold.

## How can I differentiate bank accounts from the same bank?
To differentiate two different bank accounts within the same bank, you can use the bank group as a filter for the bank rule. On the **Bank rules for payment fee** page, in the **Third party bank group** and **Company bank group** fields, select **Bank groups**. Then, in the **Relationship** field, select **&lt;&gt;**.

## Additional resources
- [Generate and post payment fee](./tasks/post-payment-fee.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
