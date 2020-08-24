---
# required metadata

title: Record leases in foreign currencies
description: This topic lists the steps for recording leases in currencies other than the accounting or reporting currencies.
author: moaamer
manager: Ann Beebe
ms.date: 08/05/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-08-05
ms.dyn365.ops.version: 10.0.14
---

# Record leases in foreign currencies

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Asset leasing accounts for leases in currencies other than the accounting or reporting currencies established in Ledger setup. All leases should be entered in their transaction currency, or in other words, the currency denominated on the lease contract. This topic lists the steps for recording leases in currencies other than the accounting or reporting currencies.

When you enter a lease using a foreign currency, the right-of-use (ROU) asset will be depreciated in both the accounting currency and reporting currency. These currencies are configured in **Ledger setup**. This behavior is also used in Fixed assets. When you create a lease in a foreign currency, select the transaction currency from the **Currency** drop-down.

The default entry in the **Accounting currency exchange rate** field of the **Financial and reporting exchange information** tab, will be the currency exchange rate that was effective as of the commencement date of the lease. The commencement date applies to both the accounting currency and lease currency.

1. Select the **Fixed rate** check box to override the exchange rate that was entered automatically, and enter the new rate.
2. Enter the information you need for this lease in the other fields, and then click **Create schedules**.
3. On the newly created **Lease details** page, select **Books**.
4. On the **Lease book** page, review the information in the **Financial and reporting exchange information** tab to verify the values in the **Accounting currency initial right-of-use asset** and **Reporting currency initial right-of-use asset** fields. The values in these fields will be the translated right-of-use asset balance in each respective currency. These fields will be updated when you change any financial information. Click **Create schedules** before confirming the payment schedule.
5. The initial recognition journal entry will record the ROU asset that uses the currency exchange rates listed on the lease. The journal entry will also include the values shown in the **Accounting currency initial right-of-use asset** and **Reporting currency initial right-of-use asset** fields.

## Subsequent measurement for foreign currency leases
The depreciation schedule shows the expected depreciation expense amounts in the reporting currency and accounting currency in addition to the transaction currency.

To view the right-of-use asset balances and depreciation amounts in either the reporting or accounting currency, go to **Asset depreciation schedule** and select the **Show accounting currency amounts** or **Show reporting currency amounts** check box.

When you create the depreciation expense journal entries against a lease denominated in a foreign currency, the entry will be created using the exchange rates listed on the lease, and using the values shown in the **Accounting currency initial right-of-use asset** and the **Reporting currency initial right-of-use asset** fields.

The final depreciation expense amount can be calculated using a slightly different exchange rate to fully depreciate the ROU asset in both the accounting and reporting currencies.

If the lease has been reclassified as **Deferred rent**, the system will automatically clear the exchange rates of the accounting and reporting currencies, if they've  already been defined.
