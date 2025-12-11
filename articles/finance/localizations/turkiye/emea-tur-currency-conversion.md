---
title: Use currency conversion
description: Learn how to use currency conversion on free text invoices and purchase orders for the Republic of Türkiye in Microsoft Dynamics 365 Finance. 
author: v-omerorhan 
ms.author: v-omerorhan 
ms.topic: how-to
ms.date: 07/30/2025 
ms.reviewer: johnmichalak
ms.search.region: Türkiye 
ms.search.validFrom: 2020-02-03 
ms.search.form: CurrencyConversion 
ms.assetid: b2b22868-de68-439f-914c-78c6930b7340
---

# Use currency conversion

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to use currency conversion on free text invoices and purchase orders for the Republic of Türkiye in Microsoft Dynamics 365 Finance. 

In Türkiye, an order that is issued in Turkish lira can be invoiced in a different currency. However, according to local legislation, the invoice must also include the equivalent amount in Turkish lira. This amount must be calculated by using the exchange rate of the Central Bank of the Republic of Türkiye (CBRT).

The tax amount must always be calculated, shown, and reported in Turkish lira. To ensure that tax amounts are calculated in Turkish lira, the **Sales tax currency** field must be set to **TRY** for all sales tax codes.

In Finance, you can manually adjust the exchange rate on free text invoices and purchase orders. This functionality ensures that the total amount and tax amounts on the invoice and the purchase order are aligned in Turkish lira.

## Currency conversion on free text invoices

This section explains how to use currency conversion on free text invoices.

To manually update the exchange rate on a free text invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Invoices** \> **All free text invoices**.
1. Select the free text invoice that you want to change the exchange rate for.
1. In the **Currency** field, change the currency as required.
1. On the **Header** tab, on the **Payment** FastTab, in the **Fixed exchange rate** section, set the following fields:

    - **Exchange rate** – Manually enter the exchange rate.
    - **Reporting exchange rate** – Manually enter the exchange rate.

1. In the dialog that appears, select **OK** to recalculate the line amounts on the free text invoice.
1. Select **Save**.
1. Select **Post**.

After you enter the exchange rates in the **Exchange rate** and **Reporting exchange rate** fields on the **Payment** FastTab, the following fields on the **General** FastTab are automatically updated:

- **Exchange rate** (in the **Invoice** section)
- **Reporting exchange rate** (in the **Reporting currency** section)

When the invoice is posted, the invoice amount and tax amount are updated based on the exchange rates that you entered on the invoice.

If the currency of the free text invoice is the same as the reporting currency, or if the free text invoice was already posted, you can't change the value of the **Exchange rate** and **Reporting exchange rate** fields on the **Payment** FastTab.

When the free text invoice is posted to the ledger, you can view the updated amounts in the voucher transactions.

## Currency conversion on purchase orders

This section explains how to use currency conversion on purchase orders.

To manually update the exchange rate on a purchase order, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Purchase orders** \> **All purchase orders**.
1. Select the purchase order that you want to change the exchange rate for.
1. On the **Header** tab, on the **Price and discount** FastTab, in the **Currency** section, in the **Currency** field, change the currency as required.
1. In the **Fixed exchange rate** section, set the following fields:

    - **Exchange rate** – Manually enter the exchange rate.
    - **Reporting exchange rate** – Manually enter the exchange rate.

1. Select **Save**.
1. In the dialog that appears, select a suitable option, and then select **OK** to recalculate the line amounts on the purchase order.
1. Select **Save**.

The currency update on the purchase order affects the **Exchange rate** and **Reporting currency fixed exchange rate** fields in the **Currency** section on the **Setup** FastTab on the **Header** tab of the vendor invoice page.  

After posting, the vendor invoice totals and voucher transaction totals are recalculated based on the updated exchange rates.

If the purchase order that has an updated exchange rate includes any charges, the exchange rate change also affects the charge amounts on the vendor invoice and in the accounting voucher transactions.

> [!NOTE]
> - Negative values aren't allowed in the **Exchange rate** and **Reporting exchange rate** fields for free text invoices and purchase orders. If you enter negative values in these fields, you receive the following warning message: **Field 'Exchange rate'(= -x) can only contain positive numbers**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
