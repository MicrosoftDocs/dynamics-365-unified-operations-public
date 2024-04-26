---
title: Credit statistics FAQ
description: Access answers to some frequently asked questions about credit statistics, including questions about calculating and using days sales outstanding.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 10/15/2023
ms.reviewer: twheeloc 
audience: Application User
ms.search.scope: Core, Operations
ms.search.region: Global
ms.search.validFrom: 2023-10-15
ms.search.form: 
ms.dyn365.ops.version: 10.0.35
---

# Credit statistics FAQ

This article answers some frequently asked questions about running the **Calculate balance statistics** periodic task. This feature is found at **Credit and collections** \> **Periodic tasks** \> **Credit management**. When you view the **All customers** or **Aged balances** page, many credit statistics are calculated in the **Related information** FactBox.

## How is DSO (days sales outstanding) calculated and used?

DSO (days sales outstanding) can be calculated for two different time periods. On the **Credit and collections parameters** page, enter the values for DSO1 and DSO2 in months. For example, if you want to view the DSO for the last 12 months and the last six months, enter **12** in the **DSO1** field and **6** in the **DSO2** field.

The following formula is used to calculate DSO:

(*Outstanding balance* &divide; *Total credit sales*) &times; *Number of days*

Here's an explanation of the formula:

- *Outstanding balance* – The total open Accounts receivable amount for the customer, regardless of invoice dates. You can view this amount on the **Balance** page. Go to **Accounts receivable** \> **Customers** \> **All customers**, select the customer account, and then, on the **Customer** tab, select **Balance**.
- *Total credit sales* – The total of Accounts receivable invoices between today's date and *x* number of months in the past, depending on the DSO1 and DSO2 months that are defined in Credit and collections parameters. This example uses 12 months and six months. You can verify the total sales by using the Customer invoice journal. Go to **Accounts receivable** \> **Inquiries and reports** \> **Invoices** \> **Invoice journal**, and select the customer and a date range.
- *Number of days* – The number of days in the past *x* months, depending on the DSO1 and DSO2 months that are defined in Credit and collections parameters. For example, today is October 11, and DSO2 is defined as six months (in the past), or April 11. Therefore, the number of days between October 11 and April 11 is 183. For a DSO of 12 months, use 365 days (or 366 for a leap year).

> [!NOTE]
> If the **Customer since** field on the **Credit and collections** FastTab of the **Customer** page is set to a date that's later than the DSO date, the date in the **Customer since** field is used to calculate the number of days. For example, the **Customer since** date is May 1, which is after the DSO date of April 11. In this case, the number of days is 163 instead of 183.

### DSO calculation example

For the customer Fabrikam, Inc., the outstanding balance is $50,000, and the total credit sales are $150,000. The **Customer since** field is set to January 1, 2022 (01/01/2022).

- DSO1 (12 months) = (50,000 &divide; 150,000) &times; 365 = 121.67.
- DSO2 (six months) = (50,000 &divide; 150,000) &times; 183 = 61.00.

If the **Customer since** field is set to January 2, 2023 (01/02/2023), DSO (12 months) = (50,000 &divide; 150,000) &times; 283 = 94.33.

## Why aren't the average payment days being calculated? The customer has invoices and payments that have been settled together.

- Go to **Cash and bank management parameters** \> **General** \> **General**, and make sure that a value is entered in the **Not sufficient funds** field.
- The invoice date and payment date must be at least one day apart. Otherwise, the average is 0 (zero).
