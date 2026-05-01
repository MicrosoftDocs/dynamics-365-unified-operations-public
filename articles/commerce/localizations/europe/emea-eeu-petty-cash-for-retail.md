---
title: Petty cash management for Commerce for Eastern Europe
description: Learn how to set up and use cash management features in Microsoft Dynamics 365 Commerce for Eastern Europe.
author: EvgenyPopovMBS
ms.date: 02/26/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
ms.author: anupamar
ms.search.validFrom: 2018-10-31
ms.custom: 
  - bap-template
---

# Petty cash management for Commerce for Eastern Europe

[!include [banner](../../../finance/includes/banner.md)]

This article contains information about Eastern European localization specific for the commerce industry.

In accordance with the Eastern Europe accounting requirements, set up operations for cash accounts to automate the processes for receipts, cash documents, and cash reports. For more information, see [(EEUR) Set up parameters for cash management](/dynamicsax-2012/appuser-itpro/eeur-set-up-parameters-for-cash-management).

Retailers can accept various types of payment in exchange for the products and services that they sell. Although cash is the most common form of payment, retailers can also receive payment in the form of checks, cards, or vouchers. In Retail point of sale (POS), cash, credit card receipts, and other payments are processed through a cash office.

By using Cash management in Commerce, you can:

- Create a cash account for the selected payment method for each store.
- Use cash journals to post cash transactions and customer payments that are received at a retail POS.
- Aggregate transactions in a statement line when you post a statement. You can aggregate safe drops, bank drops, voucher transactions, remove tender transactions, float entry transactions, income transactions, expense transactions, customer payments, sales transactions, and return transactions.

All transactions that take place in POS are posted by using a ledger journal. Use cash payment journals, customer payment journals, and general journals to create and post the statements. For more information, see [Create, calculate, and post statements for a retail store](/dynamics365/unified-operations/retail/tasks/create-calculate-post-statement-retail-store).

On the **Posted statements** page, on the Action Pane, you can do the following tasks:

- Go to **Inquiries \> Cash payment journal** to access the cash payment journals that are related to the statement.
- Go to **Inquiries \> General journal** to access the ledger journals that are related to the statement, other than customer payments and cash payments.

## Set up for cash management for POS

Complete the following setup procedure before you use cash management:

- Set up a payment method for each payment type that the retailer accepts on the **Payment methods** page. You can use different payment methods for posting transactions in POS. For more information about payment methods, see [Payment methods](/dynamics365/unified-operations/retail/payment-methods).
- Set up parameters for cash operations.
- Set up a payment method for cash payments in a store.

### Set up parameters for cash operations

Set up parameters to create and post cash transactions in Commerce. Use cash payment journals, customer payment journals, or general journals to post sales transactions and payment transactions in the POS. You can aggregate transactions that have the same properties when you post a statement.

1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**. In the left pane, select **Posting**.
1. In the **Posting** area, on the **Aggregation** FastTab, set **Tender remove/float** to **Yes** to aggregate the remove tender transactions or float entry transactions that are associated with a statement line when you post the statement. A remove tender transaction is the remove tender transaction that you create when you withdraw cash from the POS cash drawer. A float entry transaction is the float entry transaction that you create when you deposit cash in the POS cash drawer.
1. Activate the individual parameters listed in the following list to aggregate the transactions that are associated with a statement line when you post the statement:

    - **Bank drop** – Aggregate bank transactions.
    - **Safe drop** – Aggregate safe transactions.
    - **Income/Expense transactions** – Aggregate income transactions or expense transactions.
    - **Voucher transactions** – Aggregate voucher transactions.
    - **Customer payments** – Aggregate customer payments.
    - **Sales and returns** – Aggregate sales and returns transactions.

1. On the **Payments** FastTab, select a default journal name for the following options:

    - **Customer payment journal** – This journal is used to post customer payments.
    - **Cash payment journal** – This journal is used to post cash payments.
    - **General journal** – This journal is used to post transactions other than cash payments and customer payments.

### Set up a payment method for cash payments in a store

Use the following procedure to set up a payment method for cash payments in a store.

1. Go to **Retail and Commerce > Channels > Stores > All stores**.
1. On the **All stores** list page, select the store to set up a payment method for.
1. On the Action Pane, on the **Set up** tab, in the **Set up** group, select **Payment methods**.
1. On the **Payment method** page, create or select a payment method.
1. On the **Posting** FastTab, in the **Account** field group, in the **Account type** field, select **Cash account**.

    > [!NOTE]
    > You can select **Cash account** in the **Account type** field only if you select **Normal** or **Tender remove/float** in the **Function** field.

1. In the **Account number** field, select a cash account number for the payment method.
1. In the **Tender remove/float** field group, in the **Offset account** field, select the offset account to post remove tender or float entry transactions for the payment method.

> [!NOTE]
> You must set up offset accounts for both the cash tender payment method and the remove tender or float entry payment method for a store. This setup creates balanced general ledger entries for remove tender or float entry transactions.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
