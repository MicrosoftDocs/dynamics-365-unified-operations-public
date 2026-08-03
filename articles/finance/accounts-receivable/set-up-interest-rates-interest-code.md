---
title: Set up interest rates for an interest code
description: Interest codes contain settings that determine when interest is charged and how it is calculated on overdue accounts.
author: ShivamPandeyMSFT
ms.author: shpandey
ms.topic: article
ms.date: 07/31/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: Interest
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 3b945333-1eaf-4658-ab5a-1a7791a7eb40
---

# Set up interest rates for an interest code

[!include [banner](../includes/banner.md)]

Interest codes contain settings that determine when to charge interest and how to calculate it on overdue accounts.

Set up a single interest code and apply it to multiple customer posting profiles, billing codes, or specific invoice lines. When you change the interest code details, all features that use the code automatically implement the changes on new transactions. For each interest code, set up two types of rates:

- Rates for interest earnings − These rates represent revenue that you earn by charging interest on invoices or interest notes.
- Rates for interest payments − These rates represent a cost that you pay for interest on credit notes.

Both of these rate types can exist at the same time and in the same interest code. You can base interest rates on three calculation types:

- Interest by percentage.
- Interest by amount.
- Interest by range, which results in a single percentage or amount.

When you use an interest code to calculate interest, the system creates a separate interest note for each interest rate that is in effect during the time that the payment exceeds the transaction due date. Use the **Earnings** tab on the **Interest code** page to set up interest rates for interest that you earn by charging interest. Use the **Payments** tab to set up interest rates for interest that you pay.

## Interest rates based on a percentage

Set up interest rates that calculate a specified percentage.

- The interest amount applies to all currencies.
- You can enter optional interest amount limits.
- Select **Percentage** in the **Calculate interest based on** field on the **Set up Interest codes** page.

For example, to set up an interest code that assesses 5 percent interest for every two months that the invoice payment exceeds the transaction due date, enter 2 in the **Calculate interest every** field and select **Month**.

> [!NOTE]
> The new algorithm for interest note calculation is added by using Feature management. To use this algorithm, enable the **(GBL) Allow to calculate interest per day as yearly percent divided by 365** feature. For information about how to enable the feature, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
>
> The formula for the calculation for the interest note amount is:
> 
> Interest note amount = Amount owed * Yearly interest % / 365 * Number of days late
> 
> This feature is available in version 10.0.18 or later.

## Interest rates based on amounts

Set up interest rates that calculate a specified amount per currency.

- Specify an interest amount for each currency in the interest code.
- You can enter optional interest amount limits.
- Select **Amount** in the **Calculate interest based on** field on the **Set up Interest codes** page.

For example, to set up an interest code that assesses interest of 25.00 for every 20 days that the invoice payment exceeds the transaction due date, enter 20 in the **Calculate interest every** field and select **Day**.

## Interest rates based on ranges

Set up interest rates that vary depending on the overdue amount, the number of days that the amount is late, or the number of months that the amount is late.

- Use the **Earnings by Currency** tab to define specific interest settings for each currency. This is also where you define the range.
- Use the **Ranges** button to add lines that represent the ranges that you want to set up. The **From** value represents the beginning of the range and the **Interest value** number represents either a percentage or an amount, depending on the selection in the **Calculate interest based on** field on the **Set up Interest codes** page.

## Example 1: Interest by range = Amount

You set up an interest code that assesses interest one time for every three months that the invoice payment exceeds the transaction due date. You want to base the calculation on a percentage interest value, according to stepped amount intervals. The interest value is 1 percent for invoice amounts up to 1,000.00, 2 percent for amounts from 1,001.00 to 5,000.00, and 3 percent for amounts larger than 5,000.00. Set up the interest code field values as follows.

| **Field name**                  | **Field value** |
|---------------------------------|-----------------|
| **Interest code**               | 3M%ByAmt        |
| **Calculate interest every**    | 3/Month         |
| **Interest by range**           | Amount          |
| **Calculate interest based on** | Percentage      |

Set up the range information as follows.

| **From value** | **Interest value** |
|----------------|--------------------|
| 0              | 1                  |
| 1,001          | 2                  |
| 5,001          | 3                  |

## Example 2: Interest by range = Days

You set up an interest code that assesses interest one time for every 15 days that the invoice payment exceeds the transaction due date. You want to base the calculation on an amount interest value, according to stepped day intervals. The interest value is 10.00 per 15 days during the first 60 days, 15.00 per 15 days during days 61 to 90, and 20.00 per 15 days from day 91 and after. Set up the interest code field values as follows.

| **Field name**                  | **Field value** |
|---------------------------------|-----------------|
| **Interest code**               | 15DAmtXDay      |
| **Calculate interest every**    | 15/Day          |
| **Interest by range**           | Days            |
| **Calculate interest based on** | Amount          |

Set up the range information as follows.

| **From value** | **Interest value** |
|----------------|--------------------|
| 0              | 10                 |
| 61             | 15                 |
| 91             | 20                 |

## Example 3: Interest by range = Months

You set up an interest code that assesses interest one time for every month that the invoice payment exceeds the transaction due date. You want to base the calculation on a percentage interest value, according to stepped month intervals. The interest value is 1.5 percent per month for the first three overdue months, 2.0 percent per month for the second three months, and 2.5 percent per month for each month beyond the first six months. Set up the interest code field values as follows.

| **Field name**                  | **Field value** |
|---------------------------------|-----------------|
| **Interest code**               | 1M%ByMth        |
| **Calculate interest every**    | 1/Month         |
| **Interest by range**           | Months          |
| **Calculate interest based on** | Percentage      |

Set up the range information as follows.

| **From value** | **Interest value** |
|----------------|--------------------|
| 0              | 1.5                |
| 4              | 2                  |
| 7              | 2.5                |

## New versions

Interest codes are date effective. If you want to modify the interest rate, create a **new version** that is effective as of a future date.

To view different versions, use the **As of Date** menu choice to select the cutoff date. You can also select the **Display all records** to view all interest codes in the page.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
