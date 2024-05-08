---
title: Sales tax payments and rounding rules
description: Learn how the rounding rule setup on the Sales tax authorities works and rounding the sales tax balance during the Settle and post sales tax job.
author: kailiang
ms.author: kailiang
ms.topic: article
ms.date: 10/29/2021
ms.reviewer: kfend
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: TaxAuthority
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 7dcd3cf5-ebdf-4a9f-806c-1296c7da0331
---

# Sales tax payments and rounding rules

[!include [banner](../includes/banner.md)]

This article explains how the rounding rule setup on the Sales tax authorities works and rounding the sales tax balance during the Settle and post sales tax job.

Periodically, sales tax needs to be reported and paid to tax authorities. This action can be completed by running the Settle and post sales tax process on the **Sales tax** page. Sales tax for a period will be settled against the sales tax accounts, and the sales tax balance will be posted to the Sales tax settlement account. The sales tax balance, which is posted to the Sales tax settlement account, can be rounded as required by tax authorities by setting up a rounding rule on the **Sales tax** page. 

The rounding difference is posted to the Sales tax rounding account that is selected in the Accounts for automatic transactions field in the General ledger.

The below example illustrates how the rounding rule on Sales tax authority works.

## Examples

The total sales tax for a period shows a credit balance of -98,765.43. The legal entity collected more sales taxes than it paid. Therefore, the legal entity owes money to the tax authority. 

The legal entity wants to use a rounding method that rounds the balance to the nearest 1.00. The user who is responsible for sales tax accounting performs the following steps.

1. Click **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax authorities**.
2. On the **General** FastTab, in the **Rounding form** field, select **Normal**.
3. In the **Round-off** field, enter 1.00.
4. When it is time to pay the sales taxes to the tax authority, go to **Tax** > **Declarations** > **Sales tax** > **Settle and post sale tax**. On the sales tax settlement account, you can see that the tax liability amount of **98,765.43** is rounded to **98,765**.

The following table shows how an amount of 98,765.43 is rounded by using each rounding method that is available in the **Rounding form** field in the **Sales tax authorities** page.

> [!NOTE]                                                                                  
> If the round-off value is set as 0.00, then:
>
> - For normal rounding, the rounding behavior is the same as for **Round-off = 0.01**.
> - For the **Rounding form options**, **Downward**, **Rounding-up**, and **Own advantage**, the behavior is the same as for **Round-off = 1.00**.

| Rounding form option                | Round-off value = 0.01 | Round-off value = 0.10 | Round-off value = 1.00 | Round-off value = 100.00 | Round-off value = 0.00   |
|-------------------------------------|------------------------|------------------------|------------------------|--------------------------|--------------------------|
| Normal                              | 98,765.43              | 98,765.40              | 98,765.00              | 98,800.00                | 98,765.43                |
| Downward                            | 98,765.43              | 98,765.40              | 98,765.00              | 98,700.00                | 98,765.00                |
| Rounding-up                         | 98,765.43              | 98,765.50              | 98,766.00              | 98,800.00                | 98,766.00                |
| Own advantage, for a credit balance | 98,765.43              | 98,765.40              | 98,765.00              | 98,700.00                | 98,765.00                |
| Own advantage, for a debit balance  | 98,765.43              | 98,765.50              | 98,766.00              | 98,800.00                | 98,766.00                |

### Normal round, and round precision is 0.01

```<table>
  <tr>
    <td>Rounding
    </td>
    <td>Calculation process
    </td>
  </tr>
    <tr>
    <td>round(1.015, 0.01) = 1.02
    </td>
    <td>
      <ol>
        <li>round(1.015 / 0.01, 0) = round(101.5, 0) = 102
        </li>
        <li>102 * 0.01 = 1.02
        </li>
      </ol>
    </td>
  </tr>
    <tr>
    <td>round(1.014, 0.01) = 1.01
    </td>
    <td> <ol>
        <li>round(1.014 / 0.01, 0) = round(101.4, 0) = 101
        </li>
        <li>101 * 0.01 = 1.01
        </li>
      </ol>
    </td>
  </tr>
    <tr>
    <td>round(1.011, 0.02) = 1.02
    </td>
    <td> <ol>
        <li>round(1.011 / 0.02, 0) = round(50.55, 0) = 51
        </li>
        <li>51 * 0.02 = 1.02
        </li>
      </ol>
    </td>
  </tr>
    <tr>
    <td>round(1.009, 0.02) = 1.00
    </td>
    <td> <ol>
        <li>round(1.009 / 0.02, 0) = round(50.45, 0) = 50
        </li>
        <li>50 * 0.02 = 1.00
        </li>
      </ol>
    </td>
  </tr>
</table>
```

> [!NOTE]                                                                                  
> If you select Own advantage, the rounding is always to the advantage of the legal entity. 

For more information, see the following topics:
- [Sales tax overview](indirect-taxes-overview.md)
- [Create a sales tax payment](tasks/create-sales-tax-payment.md)
- [Create sales tax transactions on documents](tasks/create-sales-tax-transactions-documents.md)
- [View posted sales tax transactions](tasks/view-posted-sales-tax-transactions.md)
- [round Function](/previous-versions/dynamics/ax-2012/reference/aa850656(v=ax.60))




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
