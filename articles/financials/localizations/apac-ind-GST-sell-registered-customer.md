---
# required metadata

title: Sales to a registered customer
description:  This topic provides informationabout sales to a registered customer.
author: EricWang
manager: RichardLuan
ms.date: 06/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: EricWang
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.4

---

# Sales to a registered customer

## Create a sales quotation

1. Click **Sales and marketing** \> **Sales quotation** \> **All quotations**.
2. Create a quotation for a taxable item for the registered customer.
3. Save the record.
4. Click **Tax information**

   ![](media/Capture06.PNG)

5. On the **GST** tab, validate the default values.

   ![](media/Capture07.PNG)

6. Click the **Customer tax information** tab

   ![](media/Capture08.PNG)

> [!NOTE]
> The company address and the customer address are in the same state. Therefore, this transaction is an intrastate transaction.
> Customer tax information is defined. Therefore, the dealer is a registered dealer.

7. On the Action Pane, on the **Quotation** tab, in the **Financials** group, click **Tax document**.
8. Select the **GST** node, and on the **Sales quotation and Tax details** FastTabs, review the tax applicability, tax attributes, and tax calculation. For example, you might see something similary to the following:

   Example:

   - Taxable value: 10,000.00

   - CGST: 10 percent

   - SGST: 10 percent

     ![](media/Capture09.PNG)

9. Click **Close**.
10. On the Action Pane, on the **Quotation** tab, in the **Generate** group, click **Send quotation**.
11. Click **OK** and then close the message.
12. On the Action Pane, on the **Follow up** tab, in the **Generate** group, click **Confirm**.
13. Click **OK**, close the message, and then close the pages.

## Create a sales order

1. Click **Accounts receivable** \> **Sales orders** \> **All sales orders**.
2. Select a record, and on the Action Pane, on the **Sales order** tab, in the **Maintain** group, click **Edit**.
3. Click **Tax information**.

   ![](media/Capture06.PNG)

4. Click the **GST** tab.

   ![](media/Capture07.PNG)

5. Click the **Customer tax information** tab.

   ![](media/Capture08.PNG)

6. Click **OK**, and on the Action Pane, on the **Sell** tab, in the **Tax** group, click **Tax document** to review the calculated taxes.

   ![](media/Capture09.PNG)

7. Click Close.

## Post the invoice

1. On the Action Pane, on the **Invoice** tab, in the **Generate** group, click **Invoice**.
2. In the **Quantity** field, select **All**.
3. Select the **Print invoice** check box.
4. Click **OK** and then click **Yes** to acknowledge the warning message.

## Validate the voucher

1. On the Action Pane, on the **Invoice** tab, in the **Journals** group, click **Invoice**.
2. Click **Voucher**.

- Financial entries for both the intrastate and interstate transactions

![](media/Annotation-2019-05-20-133425.png)
