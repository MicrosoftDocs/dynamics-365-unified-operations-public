---
# required metadata

title: GST integration for cash registers for India
description: This topic provides an overview of the cash register functionality that is available for India. It also provides guidelines for setting up the functionality.
author: EvgenyPopovMBS 
manager: annbe
ms.date: 01/31/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Retail, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
ms.search.industry: Retail
ms.author: v-pakris
ms.search.validFrom: 2018-1-31
ms.dyn365.ops.version: 7.3.1
---
# GST integration for cash registers for India

This topic provides a walkthrough of the features that are related to Goods and Services Tax (GST) in Microsoft Dynamics 365 for Retail. This document also highlights the effect of GST on various type of retail business transactions, and shows the accounting and posting of retail transactions with the receipt printed at the POS.

> [!NOTE]
> This topic applies to both Dynamics 365 for Finance and Operations, Enterprise edition, and to Dynamics 365 for Retail.

## Prerequisites 

- Set up GST for India in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. For more information, see [India Goods and Services Tax (GST)](../../financials/localizations/apac-ind-gst.md).
- Configure Retail channel components: to enable India-specific functionality, you must configure extensions for Retail channel components. For more information, see the [deployment guidelines](./apac-ind-loc-deployment-guidelines.md).
  
## India tax entities for Retail
The following table lists the navigation paths for the India tax entities in the **Dynamics 365 for Retail**.

| **India tax entities**              | **Navigation path in Dynamics 365 for Retail**                                |
|-------------------------------------|-------------------------------------------------------------------------------|
| Business verticals                  | Retail \> Channel setup \> Sales taxes \> Business verticals                  |
| Enterprise tax registration numbers | Retail \> Channel setup \> Sales taxes \> Enterprise tax registration numbers |
| GST reference number sequence group | Retail \> Channel setup \> Sales taxes \> GST reference number sequence group |
| HSN codes                           | Retail \> Channel setup \> Sales taxes \> HSN codes                           |
| Service accounting codes            | Retail \> Channel setup \> Sales taxes \> Service accounting codes            |
| Maintain setoff hierarchy profiles  | Retail \> Channel setup \> Sales taxes \> Maintain setoff hierarchy profiles  |
| VAT schedules                       | Retail \> Channel setup \> Sales taxes \> VAT schedules                       |
| Tax setup                           | Retail \> Channel setup \> Sales taxes \> Tax configuration \> Tax setup      |

> [!NOTE]
> The navigation paths for India tax entities are different in Retail than they are in Finance and operations. For information about the navigation paths in Finance and Operations, see [India Goods and Services Tax (GST)](../../financials/localizations/apac-ind-gst.md).

## Validate tax information for the retail store

The tax information for the Retail store comes from the selected retail warehouse as defined in the Warehouse master. The configured tax information from the store gets printed on the POS receipt and is updated on the retail sales order at the headquarter for the financial postings.

To see the tax information for a retail store, complete the following steps.

1.  Go to **Retail** \> **Channels** \> **Retail stores** \> **All retail stores**.
2.  Select a retail store.
3.  Click the **Tax information** FastTab.

## Configure Language texts and custom fields 

You can configure the **Language text** and **Custom fields** that are in the POS receipt formats. The default company of the user creating the receipt setup should be the same as the legal entity in which the language text setup is created. Alternatively, the same language texts should be created in both the default company of the user and the legal entity of the store for which the setup is being created.

### Set up POS language text

1.  Go to **Retail** \> **Channel** s**etup** \> **POS setup** \> **POS profile \> Language text**.
2.  Click the **POS** tab.
3.  Click **POS language text** FastTab.
4.  Select the language ID for the text. This should be the same as the language preference of the user.
5.  Enter a unique ID that is equal to or greater than 900001 in the **Text ID** field.
6.  Enter the language text in the **Text** field.

![Language text](media/apac-ind-gst-language-text.png)

### Create custom fields

When you create custom fields, the **Caption text ID** field values must correspond to the **Text ID** field value that you defined on the **Language text** page.

1.  Go to **Retail** \> **Channel setup** \> **POS setup** \> **POS profile \> Custom fields**.
2.  Enter a name for the field.
3.  Select the field type.
4.  Enter the **Caption text ID**. This is one of the language text **Text ID** values on the **Language text** page.  

  ![Custom fields](media/apac-ind-gst-custom-fields.png)

## Receipt format

You can use **Receipt format designer** to add custom fields to the appropriate receipt sections. For more information, see [Receipt templates and printing](../receipt-templates-printing.md).

1.  Click **Retail** \> **Channel setup** \> **POS setup** \> **POS profile** \> **Receipt formats**.
2.  Select a receipt format for the **Receipt** receipt type and make the required changes.

    ![Receipt format design](media/apac-ind-gst-receipt-format.png)

## Update receipt profiles 

After you create a receipt format, you can assign that format to a receipt profile.

To update a receipt profile, complete the following steps:

1. Click **Retail** \> **Setup** \> **POS** \> **Receipt profile**.
2. Select the receipt profile to update.
3. Click **Edit**.
4. For each receipt type in the list, select a receipt format.

## Update POS invoice number 

You can reconcile the POS receipt number with the invoice number for customer retail transactions. If you have selected **Yes** for the **Update POS invoice number** option (**Posting** tab) on the **Retail parameters** page, the POS receipt number is populated in the **Transaction id** field for corresponding Retail sales orders.

You can select **Yes** for the **Update POS invoice number** option only if the existing receipt number format includes the store number and terminal number. The following screenshot shows a POS functionality profile with receipt numbering that includes the store number and the terminal number.

![POS functionality profiles](media/apac-ind-gst-pos-functionality-profile.png)

## Run a distribution schedule 

To sync Tax Engine (GTE) data from headquarters to the POS database, a job is added to the **Distribution schedule** page. To verify the job exists and to run the job, complete the following steps.

1.  Click **Retail** \> **Periodic** \> **Data distribution** \> **Distribution schedule**.
2.  Verify that a new job, **1180**, has been added for **Generic tax engine**.
3.  Run all the jobs (**9999**).

## Example scenarios 

The following example scenarios will help you to better understand the cash register functionality for India.

### Sell to a registered customer 

Sales to a registered customer are known as B2B sales. If the store location’s state and place of supply state (customer address) are the same, then the transaction becomes an intrastate sale and CGST & SGST are payable. If the store location’s state and place of supply (customer address) are in different states, then the transaction becomes an interstate sale and IGST is payable.

> [!NOTE]
> Customer address with the registration number are required fields for these transactions.

#### Complete a customer order

1.  Log into the POS.
2.  Enter the items, and then click **Enter**.

![POS customer order](media/apac-ind-gst-pos-customer-order.png)

3. Validate GST calculations considering the rate defined in the tax setup.

| **Item/Service** | **Unit price** | **Tax rates**    | **CGST** | **SGST**    |
|------------------|----------------|------------------|----------|-------------|
| M0001            | 10,000.00      | CGST12%, SGST11% | 1,200.00 | 1,100.00    |
| M0002            | 5,000.00       | CGST10%, SGST10% | 500.00   | 500.00      |
| S0001            | 1,200.00       | CGST11%, SGST5%  | 132.00   | 60.00       |
|                  | 16,200.00      |                  | 1,832.00 | 1,660.00    |
| Total amount     |                |                  |          | 19,692.00   |

4.  Click **Orders** > **Create customer order**.
5.  Click **Add customer** to select the customer account.
6.  Click **Pick up all**.
7.  Select the **Store** and **Pick-up date**.
8.  Click **OK**.

 ![POS Customer order](./media/apac-ind-gst-pos-customer-order2.png)

  >  [!NOTE]
  >  In this example, Store location state is Delhi and Customer address state is Delhi. Both are of same state and hence intrastate GST is calculated.

9.  Click **Exact**, to process the deposit payment.
10. Validate the receipt
    1.  Click **Show journal**.
    2.  Select the transactions.
    3.  Click **Receipt**.

   ![Receipt example](media/apac-ind-gst-receipt.png)

11. Validate the sales order and tax document at Retail Headquarters
    1.  Go to **Retail** \> **Customers** \> **All sales orders**.
    2.  Select the sales order.
    3.  On the Action Pane, on the **Sell** tab, in the **Tax** group, click **Tax
    document**.

  ![Tax document](media/apac-ind-gst-tax-document.png)

12. Recall and process the customer order
  1.  Login to POS.
  2.  Click **Recall order**.
  3.  Search for the order and Select the order.
  4.  Click **Picking and packing** \> **Pickup**
  5.  Click **Select all** and then **Pickup.**

   ![Process a customer order](media/apac-ind-gst-process-customer-order.png)

13. Click **Exact,** to process the payment.
14. Validate the receipt.

    ![Receipt example](media/apac-ind-gst-receipt-2.png)

15. Validate the voucher transactions
    1.  Go to **Retail \> Customers \> All sales orders**.
    2.  Select the sales order.
    3.  On the Action Pane, on the **Invoice** tab, click **Invoice journals**.
    4.  Click **Voucher**.

|Ledger account name      |Debit amount (Rs.)|Credit amount (Rs.)|
|-------------------------|------------------|-------------------|
|Customer account         |         19,692.00|                   |
|   CGST payable account  |                  |           1,832.00|
|   SGST payable account  |                  |           1,660.00|
|   Sales account         |                  |          16,200.00|


   5.  Click **Tax document.**
   6.  Validate the receipt number is updated as the **Transaction id**.

![Tax document](media/apac-ind-gst-tax-document2.png)

### Sale of taxable goods to a consumer 

Sales to unregistered customer are known as B2C sales. There is no difference in computation of tax for a B2B and B2C sales. Customer shall be selected as **Consumer**, if the customer master is maintained with the address in the Retail Headquarters.

1.  Login into POS.
2.  Enter an Item, and then click **Enter**.
3.  Click **Add customer**, and select the customer account

  ![Example transaction](media/apac-ind-gst-example-trx.png)

  >  [!NOTE]
  > In this example, Store location state is Delhi and Customer address state is Bangalore. Both are of different state and hence interstate GST gets computed.

4.  Click **Exact,** to process the payment.
5. Validate the receipt.
    1.  Click **Show journal**.
    2.  Select the transactions.
    3.  Click **Receipt**.

 ![Receipt validation](media/apac-ind-gst-receipt-validation.png)

6. Validate the retail sales invoice in Retail Headquarters
    1.  Go to **Retail** \> **Retail IT** \> **Data distribution**.
    2.  Run job **P-0001** (**Channel transactions**).
    3.  Close the form.

7. Post the statement
    1.  Go to **Retail** \> **Channels \> Retail stores** \> **Open statements**.
    2.  Create a statement.
    3.  Click **Calculate statement** and then **Post statement**.

8. Validate voucher transactions
    1.  Go to **Retail** \> **Customers** \> **All sales orders**.
    2.  Select the sales invoice.
    3.  Click **Sales order lines** \> **Tax information** button
    4.  Verify the Location (Store address) and the Customer address in the respective tabs.

    ![Tax information](media/apac-ind-gst-tax-info.png)

    5.  Click **OK**.
    6.  On the Action Pane, on the **Invoice** tab, click **Invoice journals**.
    7.  Click **Voucher**.

    |Ledger account name     |Debit amount (Rs.)|Credit amount (Rs.)|
    |------------------------|------------------|-------------------|
    |Customer account        |         12,500.00|                   |
    |   IGST payable account |                  |           2,500.00|
    |   Sales account        |                  |          10,000.00|

    8.  Click **Tax document**.
    9.  Validate the receipt number is updated as the **Transaction id**.

### Sale of taxable goods to an anonymous customer where GST is price-inclusive

1. Define price-inclusiveness at the retail store.
    1.  Go to **Retail** \> **Channels** \> **Retail stores \> All retail stores.**
    2.  Select a retail store.
    3.  Set the **Price include sales tax** option to **Yes**.
2. Run the distribution schedule.
    1.  Go to **Retail** \> **Retail IT** \> **Data distribution**.
    2.  Run the job, to update the changes in the POS database.
    3. Close the page.
3. Enter a transaction.
    1.  Login into POS.
    2.  Enter an item, and then click **Enter**. For this example, use an item that has a Taxable value = 10000.00; CGST – 12% ; SGST – 11%.

![Transaction example](media/apac-ind-gst-trx-example.png)

4.  Click **Exact,** to process the payment.
5. Validate the receipt.

![Receipt example](media/apac-ind-gst-receipt-3.png)

6. Validate the retail sales invoice in Retail Headquarters.
    1.  Go to **Retail** \> **Retail IT** \> **Data distribution**.
    2.  Run job **P-0001** (**Channel transactions**).
    3.  Close the page.
7. Post the statement.
    1.  Go to **Retail \> Channels \> Retail stores \> Open statements.**
    2.  Create a statement.
    3.  Click **Calculate statement** and then **Post statement**.
8. Validate voucher transactions.
    1.  Go to **Retail \> Customers \> All sales orders**.
    2.  Select the sales invoice.
    3.  On the Action Pane, on the **Invoice** tab, click **Invoice journals**.
    4.  Click **Voucher**.

    |Ledger account name     |Debit amount (Rs.)|Credit amount (Rs.)|
    |------------------------|------------------|-------------------|
    |Customer account        |         10,000.00|                   |
    |   CGST payable account |                  |             975.61|
    |   SGST payable account |                  |             894.31|
    |   Sales account        |                  |           8,130.08|

    5.  Click **Tax document.**
    6.  Validate the **Transaction id** is updated as per the GST number sequence defined in **the GST reference number sequence group**.

![Tax document transaction ID](media/apac-ind-gst-tax-doc-trx-id.png)

### Sales of exempted good 

1.  Login to POS.
2.  Enter an exempted item.

![Exempted item transaction](media/apac-ind-gst-exempted-item-trx.png)

1.  Click **Exact**, to process the payment.

**Validate the receipt**

1.  Click **Show journal**.
2.  Select the transactions.
3.  Click **Receipt**.

![Receipt example.png](media/apac-ind-gst-receipt-4.png)

**Validate the retail sales invoice at Retail Headquarters**

1.  Go to **Retail** \> **Retail IT** \> **Data distribution**.
2.  Run job **P-0001** (**Channel transactions**).
3.  Close the form.

**Post the statement**

1.  Go to **Retail** \> **Channels \> Retail stores** \> **Open statements**.
2.  Create a statement.
3.  Click **Calculate statement** and then **Post statement**

**Validate the voucher transactions**

1.  Go to **Retail** \> **Customers** \> **All sales orders**.
2.  Select the sales invoice.
3.  On the Action Pane, on the **Invoice** tab, click **Invoice journals**.
4.  Click **Voucher**.

|Ledger account name|Debit amount (Rs.)|Credit amount (Rs.)|
|-------------------|------------------|-------------------|
|Customer account|    12,000.00||
|   Sales - Finished Goods||   12,000.00|

1.  Click **Tax document**.
2.  Verify that the **Exempt** option is set to **Yes**.

### Return transaction with GST

1.  Login to POS.
2.  Click **Show journal**.
3.  Select the transaction and Click **Return**.
4.  Click **Select all** and then **Return**.
5.  Verify the GST computation is as per the selected original transactions to
    be returned.

![POS return transaction](media/apac-ind-gst-return-trx.png)

1.  Click **Exact**.

**Validate the receipt**

1.  Click **Show journal**.
2.  Select the transactions.
3.  Click **Receipt**.

[Receipt example](media/apac-ind-gst-receipt-5.png)

**Validate the retail sales invoice at Retail Headquarters**

1.  Go to **Retail \> Retail IT \> Data distribution**.
2.  Run job P-0001 (Channel transactions).
3.  Close the form.

**Post the statement**

1.  Go to **Retail \> Channels \> Retail stores \> Open statements**.
2.  Create a statement.
3.  Click **Calculate statement** and then **Post statement**.

**Validate the voucher transactions**

1.  Go to **Retail \> Customers \> All sales orders**.
2.  Select the sales invoice.
3.  On the Action Pane, on the **Invoice** tab, click **Invoice journals**.
4.  Click **Voucher**.

|Ledger account name     |Debit amount (Rs.)|Credit amount (Rs.)|
|------------------------|------------------|-------------------|
|Customer account        |                  |12,500.00          |
|   IGST payable account |2,500.00          |                   |
|   Sales account        |10,00.00          |                   |

1.  Click **Tax document**.
2.  Validate the return receipt number is updated as the **Transaction id**.
