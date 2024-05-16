---
title: Record leases in foreign currencies
description: Learn about how to record leases in currencies other than the accounting or reporting currency, including an outline on measurements for foreign currency leases.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 04/12/2021
ms.reviewer: kfend
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: AssetLeaseDetail
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Record leases in foreign currencies

[!include [banner](../includes/banner.md)]

Asset leasing accounts for leases that are in currencies other than the accounting currency or the reporting currency are established on the **Ledger setup** page. All leases should be entered in their transaction currency. In other words, they should be entered in the currency that is specified in the lease contract. This article explains how to record leases in currencies other than the accounting or reporting currency.

If you enter a lease in a foreign currency, the right-of-use (ROU) asset is depreciated in both the accounting currency and the reporting currency. These currencies are configured on the **Ledger setup** page. This behavior is also used in Fixed assets. When you create a lease in a foreign currency, select the transaction currency in the **Currency** field.

The exchange rate of the accounting currency is the default value in **Accounting currency exchange rate** field. The exchange rate of the reporting currency is the default value in the **Reporting currency exchange rate** field. These exchange rates were effective on the commencement date of the lease. The **Accounting currency exchange rate** and **Reporting currency exchange rate** fields, are in the **Financial and reporting exchange information** FastTab, on the **Lease details** page.

1. Select the **Fixed rate** check box to override the exchange rate that was automatically entered, and then enter the new rate.
2. In the other fields, enter the information that is required for the lease, and then select **Create schedules**.
3. On the new **Lease details** page, select **Books**.
4. On the **Lease book** page, on the **Financial and reporting exchange information** tab, verify the values of the **Accounting currency initial right-of-use asset** and **Reporting currency initial right-of-use asset** fields. Each of these fields shows the translated ROU asset balance in the corresponding currency. These fields are updated whenever you change any financial information. Select **Create schedules** before you confirm the payment schedule.

    The initial recognition journal entry records the ROU asset that uses the currency exchange rates that are listed on the lease. The journal entry also includes the values of the **Accounting currency initial right-of-use asset** and **Reporting currency initial right-of-use asset** fields.

## Subsequent measurement for foreign currency leases

The depreciation schedule shows the expected depreciation expense amounts in the reporting currency, the accounting currency, and the transaction currency.

To view the ROU asset balances and depreciation amounts in either the reporting currency or the accounting currency, open the **Asset depreciation schedule** page, and select the **Show accounting currency amounts** or **Show reporting currency amounts** check box.

When you create the depreciation expense journal entries against a lease that is denominated in a foreign currency, the entry uses the exchange rates that are listed on the lease. It also uses the values of the **Accounting currency initial right-of-use asset** and **Reporting currency initial right-of-use asset** fields.

The final depreciation expense amount can be calculated by using a slightly different exchange rate, so that the ROU asset is fully depreciated in both the accounting currency and the reporting currency.

If the lease has been reclassified as **Deferred rent**, the system automatically clears the exchange rates of the accounting and reporting currencies, if they have already been defined.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
