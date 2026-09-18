--- 
title: Create customer prepayment invoices
description: This article explains how to configure and process customer prepayment invoices
author: raynezou
ms.author: raynezou
ms.topic: how-to
ms.date: 09/08/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SalesTableListPage, SalesEditLines, SysQueryForm, SysRecurrence
ms.dyn365.ops.version: Version 7.0.0 
---

# Customer prepayment invoices

[!INCLUDE [banner](../../includes/banner.md)]

This article explains how to configure and process customer prepayment invoices.

## Types of prepayment processes

### Prepayment as a deposit

In this process, the buyer makes an initial partial payment to secure goods, services, or a contract. This partial payment is often referred to as a deposit. It's either a percentage or a fixed amount of the total value of the sales order. The prepayment invoice functions similarly to a billing document. The final invoice is issued later and reflects the full amount of the sales order.

### Prepayment invoice as a tax invoice

In this process, the seller issues a real prepayment invoice to the buyer. This invoice includes sales taxes, if they're applicable. The buyer pays the invoice amount up front. Then, when the payment is completed, the seller can proceed with the delivery of goods or services. Later, the official invoice is sent out. The value of this invoice is the total outstanding amount, which is the difference between the total sales order value and the total prepaid amount.

This article explains how to configure the **Customer prepayment invoice** feature and what the process looks like.

### Example of a customer prepayment invoice

A customer places an order for $10,000 and agrees to pay $3,000 as a prepayment. You issue the final invoice after you fully deliver the goods and services.

The following accounting entries are recorded:

- Prepayment invoice creation:

  - **Debit:** Accounts receivable: $3,000
  - **Credit:** Prepayment (Deposit): $3,000

- Payment of prepayment invoice:

  - **Debit:** Cash/Bank: $3,000
  - **Credit:** Accounts receivable: $3,000

- Apply the prepayment on customer invoice:

  - **Debit:** Prepayment (Deposit): $3,000
  - **Credit:** Accounts receivable: $3,000

- Final customer invoice creation:

  - **Debit:** Accounts receivable: $10,000
  - **Credit:** Revenue: $10,000

In this example, the final invoice includes the total order amount ($10,000) and corresponding tax entries. The customer should pay the open amount, which is the total invoice amount ($10,000) minus the prepaid amount ($3,000), or $7,000. The entries ensure that the prepayment is correctly recorded and offset against the final invoice when the goods or services are delivered.

## Set up Accounts receivable for customer prepayment invoices

To set up customer prepayment invoices, follow these steps:

1. Go to **Feature management**, and enable the **Prepayment customer invoice** feature.
2. Go to **Inventory management** \> **Setup** \> **Posting** \> **Posting** \> **Sales order** \> **Prepayment**.
3. Set up the default ledger account for posting. Set the type to **Customer prepayment**.
4. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
5. On the **Updates** tab, on the **Invoice** FastTab, in the **Prepayment** section:
    - Select the **Check mandatory sales order confirmation** parameter to create a prepayment invoice only if the sales order is confirmed.
    - Select the **Synchronous prepayment settlement** parameter to apply prepayments when invoicing sales orders without relying on the **Automated prepayment settlement posting** process automation job. This selection improves real-time visibility and accuracy in financial reporting.
    - Select the **Sales category** to determine the revenue account according to the posting settings.
6. On the **Ledger and sales tax** tab, on the **General** FastTab, in the **Prepayment invoice** section, in the **Prepayment application policy** field, select one of the following values:

    - **Notification** – Prepayments are manually applied. If the prepayment isn't applied, you receive a notification when you create the final invoice.
    - **Automatic** – Prepayments are automatically applied to the sales order if full payment is received and settles the prepayment invoice.

7. On the **Number sequences** tab, set up number sequences for the **Prepayment invoice**, **Prepayment invoice voucher**, **Prepayment invoice reversal**, and **Prepayment invoice reversal voucher** references.
8. Go to **System administration** \> **Setup**, and select **Process automations**.
9. Select **Initialize process automations**.
10. Update the interval for the process automation to one minute.

If you use Electronic reporting (ER), follow these additional steps.

1. Open the **Electronic reporting** workspace, and select the **Reporting configurations** tile. Then, on the **Configurations** pages, on the Action Pane, select **Exchange** \> **Load from XML file**.
2. Enable ER configurations.
3. Import the following files from Dataverse:

    - Customer prepayment invoice model xml
    - Customer prepayment invoice model mapping xml
    - Prepayment invoice template xml

4. In the **Electronic reporting** workspace, in the **Related links** section, select **Electronic reporting destination**.
5. Select **New**. Then, in the **Reference** field, select **Prepayment invoice template**.
6. Select **Settings** to enable the different destinations for reports.
7. Select **OK**.
8. Select the **Convert to PDF** checkbox to print the file in PDF format.
9. Go to **Accounts receivable** \> **Setup** \> **Forms** \> **Form setup**.
10. Go to the invoice and select the **Prepayment invoice template** in the dropdown list for the Prepayment invoice.
11. Save the page.

## Overview of the prepayment invoice process

The customer prepayment invoicing process includes the following steps:

1. Define a prepayment value on the sales order.
2. Confirm and post a prepayment invoice.
3. Settle the prepayment invoice.
4. Apply the prepayment invoice to the final invoice.

## Create a prepayment proposal

When you create a sales order, define the prepayment amount by following these steps:

1. From the sales order, go to **Invoice** > **Prepayment**, and select **Payment proposal**.
2. Select the prepayment type:

    - **Percentage** – If you select **Percentage**, the **Prepayment value** field is enabled. This field represents the percentage of the total sales order amount that is required as a prepayment. The **Total prepayment amount** field shows the calculated prepayment amount.
    - **Fixed** – If you select **Fixed**, the **Total prepayment amount** field is enabled, and you manually enter the prepayment amount. The amount that you enter can't exceed the sales order amount.

3. In the **Sales category** field, select the appropriate sales category that determines the revenue account according to the posting settings. By default, the sales category is automatically populated with the value chosen in **Accounts receivable parameters**.

## Generate a prepayment invoice

After you confirm the prepayment proposal, generate the prepayment invoice by following these steps:

1. Go to **Invoice** > **Prepayment**, and select **Prepayment invoice**.
2. Review and post the prepayment invoice. The page shows information about the overall prepayment invoice, including the customer invoice account, posting and due dates, prepayment invoice number, prepayment status, and prepayment amount.
3. Select **Post**. The system creates the open customer transaction, and the status of the prepayment invoice is **Pending**.
4. After you post the transaction, you can reverse it by using the **Reverse transaction** button on the action pane. You can select the **Reversal posting date**, **Reason code**, and **Reason comment** before the reversal is posted.

## Settle the prepayment invoice

When you receive the payment for the prepayment, post the customer payment journal to settle the prepayment invoice amount. After prepayment invoice settlement, the status of the prepayment invoice is **Received**, and **Apply prepayment** is available.

## Post the final invoice and apply the prepayment

1. From the Sales order, select **Apply prepayment**. In the **Select prepayments to apply** list, select the prepayment.
2. Select **Apply prepayment**.

    After you post the sales order invoice, the selected prepayment is applied to the invoice when the **Automated prepayment settlement posting** background process runs successfully.
    If **Synchronous prepayment settlement** is enabled in **Accounts receivable parameters**, this step happens in real-time.
3. Settle the remaining amount of the sales order invoice through a customer payment journal and show the outstanding amount.

As you issue the final invoice, expand the **Prepayment invoice** FastTab to verify the application of the prepayment.  

### Line level prepayment flow parameter

Starting in Dynamics 365 Finance version 10.0.49, the **Enable line level prepayment flow parameter** for customer prepayments on sales orders is available. This parameter provides organizations with greater flexibility by allowing prepayments to be calculated either at the sales order header level or at the individual sales order line level.

When you enable the parameter, you can choose whether a prepayment applies to the entire sales order or should be calculated and tracked separately for each sales order line.

The **Enable line level prepayment flow parameter** offers the following options:

- **Header** – Use this option to calculate the prepayment based on the total value of the sales order and when a single prepayment applies to the entire order.
- **Line** – Use this option to calculate the prepayment separately for each sales order line and to manage and track prepayments at a more granular level.
By using line-level prepayments, organizations can improve visibility into prepayment allocations, support more complex business requirements, and maintain a clearer relationship between prepayments and the corresponding sales order lines.

### Prerequisites

Before you use line-level prepayments, follow these steps:

1. In **Feature management**, enable the **Prepayment customer invoice** feature.
2. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
3. On the **Updates** tab, select **Invoice**.
4. Set **Enable line level prepayment flow** to **Yes**.

### End-to-end process

The following process illustrates the line-level prepayment flow:

1. Create a sales order that contains one or more sales lines.
2. Generate a prepayment proposal.
3. Select the Prepayment information level > Header/Line. Add the required prepayment percentage or amount for each sales order line.
4. Edit the prepayment percentage or amount.
5. Create the prepayment invoice.
6. Post the prepayment invoice.
7. Receive and post customer payment.
8. Apply the prepayment during final invoicing of the sales order.
The system maintains the underlying line-level allocation throughout the prepayment lifecycle while preserving standard customer payment and settlement processes.

### Changes with line-level prepayments

The line-level enhancement introduces changes in the following areas:

- Prepayment proposal - Users can review and manage prepayment information at the sales order line level instead of relying solely on a single header-level amount.
- Prepayment calculation - The system calculates prepayment amounts separately for each sales order line, providing detailed visibility into allocation and calculation results.
- Prepayment invoice generation - The prepayment invoice reflects the line-level calculation model while maintaining standard posting and settlement behavior.
- Reporting and analysis - Organizations can review prepayment amounts with greater detail and trace prepayment calculations back to the originating sales order lines.

### Header-level versus line-level calculation

When you select **Header** as the parameter, the system calculates the prepayment from the total sales order amount.
For example, a sales order contains:

|Sales line| Amount|
|------|-------|
|Product A|1,000|
|Product B |500|

Order total = 1,500
If a 20 percent prepayment is required, the system calculates:
Prepayment = 1,500 × 20% = 300
You manage the prepayment as a single amount for the sales order.

When you select **Line** as the parameter, the system evaluates each sales order line separately.

|Sales line| Amount| Prepayment % |Prepayment amount|
|------|-------|--------------|-----------------|
|------|-------|--------------|-----------------|
|------|-------|--------------|-----------------|
|------|-------|--------------|-----------------|
|------|-------|--------------|-----------------|
|------|-------|--------------|-----------------|
|Product A| 1,000| 20%| 200|
|Product B| 500 |20% |100|

Although the total prepayment remains 300, you maintain the calculation at the individual sales order line level.
