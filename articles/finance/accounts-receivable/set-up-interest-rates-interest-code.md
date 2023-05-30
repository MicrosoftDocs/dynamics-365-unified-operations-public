---
# required metadata

title: Set up interest rates for an interest code
description: Interest codes contain settings that determine when interest is charged and how it is calculated on overdue accounts.
author: ShivamPandey-msft
ms.date: 02/17/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: Interest
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 3b945333-1eaf-4658-ab5a-1a7791a7eb40
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Set up interest rates for an interest code

[!include [banner](../includes/banner.md)]

Interest codes contain settings that determine when interest is charged and how it is calculated on overdue accounts.

You can set up a single interest code and apply it to multiple customer posting profiles, billing codes, or to specific invoice lines. When the interest code details are changed, all features that use the code will automatically implement the changes on new transactions. For each interest code, you can set up two types of rates:
-   Rates for interest earnings − These represent revenue that is earned by charging interest on invoices or interest notes.
-   Rates for interest payments − These represent a cost that is paid for interest on credit notes.

Both of these rate types can exist at the same time and in the same interest code. Interest rates can be based on three calculation types:
-   Interest by percentage.
-   Interest by amount.
-   Interest by range, which results in a single percentage or amount.

When an interest code is used to calculate interest, a separate interest note is created for each interest rate that is in effect during the time that the payment has exceeded the transaction due date. You use the **Earnings** tab on the **Interest code** page to set up interest rates for interest that you earn by charging interest. Use the **Payments** tab to set up interest rates for interest that you pay.

## Interest rates based on a percentage
You can set up interest rates that calculate a specified percentage.

- Interest amount applies to all currencies.
- Optional interest amount limits can be entered.
- **Percentage** is selected in the **Calculate interest based on** field on the **Set up Interest codes** page.

For example, to set up an interest code that assesses 5 percent interest for every two months that the invoice payment exceeds the transaction due date, you would enter 2 in the **Calculate interest every** field and select **Month**.

> [!NOTE] 
> The new algorithm for interest note calculation is added using Feature management. To use this algorithm, enable the **(GBL) Allow to calculate interest per day as yearly percent divided by 365** feature. For information about how to enable the feature, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
> 
> The formula for the calculation for the interest note amount is: 
>  
> Interest note amount = Amount owed * Yearly interest % / 365 * Number of days late
>  
> This feature is available in version 10.0.18 or later.    
 
## Interest rates based on amounts
You can set up interest rates that calculate a specified amount per currency.
- An interest amount is specified for each currency in the interest code.
- Optional interest amount limits can be entered.
- **Amount** is selected in the **Calculate interest based on** field on the **Set up Interest codes** page.

For example, to set up an interest code that assesses interest of 25.00 for every 20 days that the invoice payment exceeds the transaction due date, you would enter 20 in the **Calculate interest every** field and select **Day**.

## Interest rates based on ranges
You can set up interest rates that vary depending on the overdue amount, the number of days that the amount is late, or the number of months that the amount is late.
-   You can use the **Earnings by Currency** tab to define specific interest settings for each currency. This is also where you will define the range.
-   Use the **Ranges** button to add lines that represent the ranges that you want to set up. The **From** value represents the beginning of the range and the **Interest value** number represents either a percentage or an amount, depending on the selection in the **Calculate interest based on** field on the **Set up Interest codes** page.

## Example 1: Interest by range = Amount
You set up an interest code that assesses interest one time for every three months that the invoice payment exceeds the transaction due date. You want to base the calculation on a percentage interest value, according to stepped amount intervals. The interest value will be 1 percent for invoice amounts up to 1,000.00, 2 percent for amounts from 1,001.00 to 5,000.00, and 3 percent for amounts larger than 5,000.00. You set up the interest code field values as follows.

| **Field name**                  | **Field value** |
|---------------------------------|-----------------|
| **Interest code**               | 3M%ByAmt        |
| **Calculate interest every**    | 3/Month         |
| **Interest by range**           | Amount          |
| **Calculate interest based on** | Percentage      |

You set up the range information as follows.

| **From value** | **Interest value** |
|----------------|--------------------|
| 0              | 1                  |
| 1,001          | 2                  |
| 5,001          | 3                  |


## Example 2: Interest by range = Days

You set up an interest code that assesses interest one time for every 15 days that the invoice payment exceeds the transaction due date. You want to base the calculation on an amount interest value, according to stepped day intervals. The interest value will be 10.00 per 15 days during the first 60 days, 15.00 per 15 days during days 61 to 90, and 20.00 per 15 days from day 91 and after. You set up the interest code field values as follows.

| **Field name**                  | **Field value** |
|---------------------------------|-----------------|
| **Interest code**               | 15DAmtXDay      |
| **Calculate interest every**    | 15/Day          |
| **Interest by range**           | Days            |
| **Calculate interest based on** | Amount          |

You set up the range information as follows.

| **From value** | **Interest value** |
|----------------|--------------------|
| 0              | 10                 |
| 61             | 15                 |
| 91             | 20                 |


## Example 3: Interest by range = Months

You set up an interest code that assesses interest one time for every month that the invoice payment exceeds the transaction due date. You want to base the calculation on a percentage interest value, according to stepped month intervals. The interest value will be 1.5 percent per month for the first three overdue months, 2.0 percent per month for the second three months, and 2.5 percent per month for each month beyond the first six months. You set up the interest code field values as follows.

| **Field name**                  | **Field value** |
|---------------------------------|-----------------|
| **Interest code**               | 1M%ByMth        |
| **Calculate interest every**    | 1/Month         |
| **Interest by range**           | Months          |
| **Calculate interest based on** | Percentage      |

You set up the range information as follows.

| **From value** | **Interest value** |
|----------------|--------------------|
| 0              | 1.5                |
| 4              | 2                  |
| 7              | 2.5                |

## New versions
Interest codes are date effective. If you want to modify the interest rate, you can create a **new version** that is effective as of a future date.

To view different versions, you can use the **As of Date** menu choice to select the cutoff date. You can also select the **Display all records** to view all interest codes in the page.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
