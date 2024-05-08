--- 
title: Establish customer payment terms
description: Learn how to establish customer payment terms and how they're connected to setting up due dates and payment discounts for customers.
author: aprilolson
ms.author: aolson
ms.topic: how-to
ms.date: 02/06/2024
ms.custom:
ms.reviewer: twheeloc   
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: PaymDay, PaymTerm, CashDisc
ms.dyn365.ops.version: Version 7.0.0 
---

# Establish customer payment terms

Payment terms determine how you manage due dates and payment discounts. Dynamics 365 Finance includes payment methods that businesses often use. You can add any payment methods that your organization prefers.

When you assign payment terms to customers, those terms will always be used on the sales and purchase documents you create for them. The document dates on sales and purchase documents are used to calculate due dates for payments.

> [!NOTE] 
> If needed, you can change the terms on the sales or purchase document, such as if you want a particular customer to pay you within 7 days rather than the default 14 days.
> 
> Changing the terms on the document doesn't change the default payment term assigned to the customer. The same payment terms are available for sales and purchase documents.

Establishing payment terms includes three primary steps:

1. Set up a **Payment day**, you create an expected day of the week (Monday, Tuesday) or specific day of the month (5th, 10th) for your customers to submit payments.
2. Define your **Payment terms** calculates due dates for your customer's payments.
3. Set up **Discount dates** to indicate the final date in which a customer can receive a discount for your products.

When you post an invoice, Dynamics 365 Finance calculates the payment discounts and payment discount dates based on the payment terms.

Similarly, when you post a credit memo, Dynamics 365 Finance calculates payment discounts based on the payment terms. It calculates the discount on credit memos in the same way as discounts on invoices. When you apply a credit memo to an invoice, Dynamics 365 Finance reduces the discount amount for the invoice by the credit memo's discount amount.

## Payment day setup procedure

To define the payment days to be used for customer payment terms, follow these steps: 
1. Go to **Accounts receivable > Payments setup > Payment days**. The setup for the **Terms of payment** is shared for **Accounts receivable** and **Accounts payable**. If you have already defined it in one module, it's available in other modules.
2. Select **New**.
3. Create a payment day if your terms of payment require a specific day of the week (Monday, Tuesday) or a specific date of the month (5th, 10th).
4. Fill in the **Payment day**, **Description**, and **Week/Month** fields as needed.
   > [!NOTE]
   > In the **Day of month** field, enter a date. The date should be entered as a number, such as '10'.
5. Click **Save**.

## Set up payment terms 
Terms of payment are used to define how due dates are calculated. 

To define payment terms, including the payment method and payment day, follow these steps: 
1. Go to **Accounts receivable > Payments setup > Terms of payment**.
2. Select **New**.
   > [!NOTE]
   > If the **Terms of payment** is **Cash**, the **Cash payment** field on the **Terms of payment** page must be **No**.

3. In the **Terms of payment** field, enter an ID.
4. In the **Description** field, enter a description of the payment terms.
5. Select a **Payment method** and **Payment day**.
     - **Payment method** defines the start of how the due will be calculated. For example, **Net** is used if the due date is always a set number of months or days after the invoice date. **COD** can be used to when payment is required upon invoice, so a due date wouldn't be calculated.
     - **Payment day** can be set to a specific day of the week or date are included in the calculation. Depending on your terms of payment, you may enter a quantity in **Months** or **Days**. Or you can use the **Payment schedule** or **Payment day** to add to the end of the **Payment method**. If you're using a **Payment calendar**, you can define how the due date is determined when the calculated date lands on a non-workday. The initial due date is calculated using calendar days. If the calculated date lands on a non-workday, you can adjust the calculated due date to either the next working date or earlier working day.
6. Click **Save**.

## Set up cash discounts 

To set up a cash discount calculates discount dates for customer payment terms, follow these steps:
1. Go to **Accounts receivable > Payments setup > Cash discounts**. Select **New**.
2. In the **Cash discount** field, enter an ID.
3. In the **Description** field, enter a description of the cash discount.
4. In the **Discount percentage** field, enter a cash discount percentage.
   > [!NOTE]
   > If a tiered cash discount is available, select the **Next discount code** that is relevant after this new cash discount.
5. In the **Main account for customer discounts** field, enter the main account to which the cash discount sends customer invoices.
6. In the **Discount offset accounts** field, select an option. 
     - Select **Accounts on the invoice lines** to post the cash discount to the same asset/expense main account on the lines of the vendor invoice.
     - Select **Use main account for vendor invoices** to post the cash discount to the main account defined in **Main account for vendor invoices**.
7. In the **Main account for vendor discounts** field, enter the main account to post the cash discount for vendor invoices.
8. Click **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
