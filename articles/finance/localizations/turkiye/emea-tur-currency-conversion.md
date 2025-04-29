---
title: Currency conversion (preview)
description: Learn how to use currency conversion in free text invoice and purchase order in the Republic of Türkiye. 
author: v-omerorhan 
ms.author: v-omerorhan 
ms.topic: overview 
ms.date: 04/25/2025 
ms.reviewer: johnmichalak
ms.search.region: Türkiye 
ms.search.validFrom: 2020-02-03 
ms.search.form: CurrencyConversion 
ms.dyn365.ops.version: 10.0.9 
ms.assetid: b2b22868-de68-439f-914c-78c6930b7340
---

# Currency conversion (preview)

[!INCLUDE[banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article explains how to use the currency conversion feature for Türkiye in Microsoft Dynamics 365 Finance.

In Türkiye, an order that is issued in Turkish Lira can be invoiced in a different currency. However, in accordance with local legislation, the invoice must also include the Turkish Lira equivalent, calculated using the Central Bank of the Republic of Türkiye (CBRT) exchange rate.
The tax amount must always be calculated, displayed, and reported in Turkish Lira. To ensure that tax amounts are calculated in Turkish Lira (TRY), **Sales tax currency** field must be set to **TRY** for all sales tax codes.

In Microsoft Dynamics 365 Finance, you can manually adjust the exchange rate for free text invoices and purchase orders. This functionality ensures that the total amount and tax amounts on the invoice and the purchase order are aligned in Turkish Lira.

## Currency conversion in free text invoice

This section explains how to use currency conversion in free text invoices.

To manually update the exchange rate in a **Free text invoice**, follow the steps below: 

1. Go to **Accounts payable** \> **Invoices** \> **All free text invoices**.
1. Select the free text invoice that you want to change exchange rate.
1. Change the currency in the **Currency** field if it is needed.
1. On the **Header** TabPage, in the **Payment** FastTab, in the **Fixed exchange rate** group;

    1. Enter the exchange rate manually in the **Exchange rate** field.
    1. Enter the exchange rate manually in the **Reporting exchange rate** field.

1. On the Dialog page, click **OK** to recalculate the free text invoice line amounts.
1. Click **Save**.
1. Click **Post**.

After you enter the exchange rates in the **Exchange rate** and **Reporting exchange rate** fields on the **Payment** FastTab, the **Exchange rate** field in the **Invoice** group under the **General** FastTab, and the **Reporting exchange rate** field in the **Reporting currency** group, will be automatically updated.
Similarly, when the invoice is posted, the invoice amount and tax amount will be updated based on the exchange rates entered on the invoice.

If the currency of the free text invoice is the same as the reporting currency, or if the free text invoice has already been posted, changes to the **Exchange rate** and **Reporting exchange rate** fields in the **Payment** FastTab will not be allowed.
When free text invoice is posted to ledger you can see the updated amounts in voucher transaction. 

## Currency conversion in purchase order

This section explains how to use currency conversion in purchase orders.

To manually update the exchange rate in a **Purchase order**, follow the steps below; 

1. Go to **Accounts payable** \> **Purchase order** \> **All purchase orders**.
1. Select a purchase order that you want to change exchange rate.
1. On the **Header** TabPage, in the **Price and discount** FastTab;

    1. Change the currency in the **Currency** field in the **Currency** group if it is needed.
    1. Enter the exchange rate manually in the **Exchange rate** field in the **Fixed exchange rate** group.
    1. Enter the exchange rate manually in the **Reporting exchange rate** field in the **Fixed exchange rate** group.

1. Click **Save**.
1. On the Dialog page, select a suitable option and click **OK** to recalculate the purchase order line amounts.
2. Click **Save**.

The currency update on the purchase order affects the **Exchange rate** and **Reporting currency fixed exchange rate** fields in the **Currency** group under the **Setup** FastTab on the **Header** TabPage of the vendor invoice page.  
After posting, the vendor invoice totals and voucher transaction totals are recalculated and displayed based on the updated exchange rates.

If the purchase order with an updated exchange rate includes any charges, the exchange rate change will also affect the charge amounts in both the vendor invoice and the accounting voucher transactions.


> [!NOTE]
> Negative values are not allowed in the **Exchange rate** and **Reporting exchange rate** fields in free text invoice and purchase order, and a warning message is displayed as below.
>
> _Field 'Exchange rate'(= -x) can only contain positive numbers._


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
