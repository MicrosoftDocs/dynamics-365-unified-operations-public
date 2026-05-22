---
title: Calculation of tax exemption
description: Learn about functionality for tax exemption calculations in Microsoft Dynamics 365 Commerce point of sale (POS) and call center. 
author: BrianShook
ms.date: 02/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-01-01
ms.custom: 
  - bap-template
---

# Calculation of tax exemption

[!include [banner](../../finance/includes/banner.md)]

This article describes functionality for tax exemption calculations in Microsoft Dynamics 365 Commerce point of sale (POS) and call center.

## Key terms

| Term | Description |
|---|---|
| B2B | An abbreviation for "business to business." It's used to indicate sales between businesses, as opposed to sales between a retailer and an individual. |
| VAT | Value-added tax that is included in the price of a product. |

## Adjust prices for tax exemptions when the price includes tax

Microsoft Dynamics 365 Commerce version 10.0.13 and later includes a feature called **Enable tax exemption for the 'price includes sales tax' scenario**. When you enable this feature, an option called **Calculate price inclusive tax exempt** appears on the **General** FastTab for store and call center settings. If you set this option to **Yes**, the system adjusts prices in tax-inclusive scenarios when the transaction or specific taxes in the transaction are exempt. When you use store-based taxes, you can apply these exemptions by using tax overrides. When you use customer-based taxes at the store, the system automatically applies the exemptions based on the customer's tax settings.

The call center and stores also support this setting for orders that you create.

:::image type="content" source="../media/CalcPriceInc.png" alt-text="Screenshot of setting the Calculate price inclusive tax exempt option to adjust prices in tax-exempt scenarios.":::

## Set up price reductions for tax exemptions

The following steps show how to test this capability in demo data scenarios. The setup steps for other data sets are similar.

1. Go to **Retail and Commerce** > **Channels** > **Stores** > **All stores**.
1. Select the **San Francisco** store. To open the store details, select the **Retail Channel Id** value for the store.
1. Select **Edit**.
4. On the **General** FastTab, set the **Calculate price inclusive tax exempt** option to **Yes**.
5. Set the **Price includes tax** option to **Yes**.
6. Select **Save**.
7. Enter **Sales tax groups** in the search field to open the **Sales tax groups** page.
8. Select **New**, and enter a name for the sales tax group.
9. On the **Setup** FastTab, select **Add**.
10. On the drop-down list in the **Sales tax code** column, select **RP\_CAST**, and then select the **Exempt** check box.
11. Select **Save**.
12. Enter **Sales tax overrides** in the search field to open the **Sales tax overrides** page.
13. Select **New**, and enter a name for the sales tax override.
14. Set the status to **Enable**.
15. In the **Override type** field, select **Sales tax group**.
16. In the **From** field, select **Any tax group**.
17. In the **To** field, select **Specified tax group**.
18. In the **From tax group** field, select **CA**.
19. In the **To tax group** field, select the sales tax group that created earlier.
20. Select **Save**.
21. Enter **Sales tax override groups** in the search field to open the **Sales tax override groups** page.
22. Select the **Default** group, and then select **Edit**.
23. Select **Add**, and then select the sales tax override that you created earlier.
24. Select **Save**.
25. Enter **Distribution schedules** in the search box to open the **Distribution schedules** page.
26. Select schedule job **9999**, and then select **Run now**.
1. When the jobs complete synchronization, open the POS.

    > [!NOTE]
    > Tax details for the channel might be cached. To observe the changes after they synchronize to the channel database, close the point of sale application and relaunch it.

28. Add item **91050** to a transaction.
29. Select **Tax overrides**, and then select **Override transaction tax**.
30. Select the sales tax override that you created earlier. The tax is reduced to 0 (zero), and the price for the line items is reduced to reflect the tax exemption.

Alternatively, set the **Use customer based tax** option for the store to **Yes** and then assign the sales tax group that you create directly to the customer. When you add the customer to a transaction, the prices are reduced to reflect that customer's tax-exempt status.

### Check customers for exemptions when tax is exclusive of price

Some retail verticals, such as liquor stores, sell goods to individuals and other businesses in cash-and-carry transactions. However, in many cases, transactions that involve different customer segments have different requirements for taxation. For example, when a liquor store sells goods to some businesses, those specific businesses might be exempt from sales taxes that usually apply to the items. In all other cases, regular sales tax applies.

To support this scenario, set the **Calculate customer tax exempt** option for the store to **Yes**. Then, when you add a customer to a transaction, the POS checks the taxes that are applicable to that customer. If the customer's tax settings have a tax code that is marked as **Exempt**, but tax is applicable to the transaction, the tax is treated as exempt for the transaction and isn't added to the transaction.

The **Calculate customer tax exempt** option applies to stores where the price doesn't include tax. The exemption calculation is also supported if the **Use destination based tax** option for the store is set to **Yes**.

### Set up tax exemption calculations for customers

The following steps show how to test this capability in demo data scenarios. The setup steps for other data sets are similar.

1. Go to **Retail and Commerce** > **Channels** > **Stores** > **All stores**.
1. Select the **San Francisco** store. To open the store details, select the **Retail Channel Id** value for the store.
1. Select **Edit**.
1. On the **General** FastTab, set the **Calculate customer tax exempt** option to **Yes**.
1. Select **Save**.
1. Enter **Sales tax groups** in the search field to open the **Sales tax groups** page.
1. Select **New**, and enter a name for the sales tax group.
1. On the **Setup** FastTab, select **Add**.
1. On the drop-down list in the **Sales tax code** column, select **RP_CAST**, and then select the **Exempt** check box.
1. Select **Save**.
1. Go to **Retail and Commerce** > **All customers**.
1. Select account ID **004009** for **Matthew Tolley**.
1. Select **Edit**.
1. On the **Invoice and delivery** FastTab, in the **Sales tax group** field, select the sales tax group that you created earlier.
1. Select **Save**.
1. Enter **Distribution schedules** in the search field to open the **Distribution schedules** page.
1. Select schedule job **9999**, and then select **Run now**.
1. When the jobs complete synchronization, open the POS.
1. Add item **91050** to a transaction. The total due is **$75.06**.
1. Add **Matthew Tolley** to the transaction. Taxes are recalculated to reflect this customer's exemption.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
