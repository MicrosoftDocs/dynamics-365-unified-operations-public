---
title: Set up index rates
description: Learn about how to set up index rates. Index rates are required if your organization associates lease payment amounts with a set of index rates.
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 06/23/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: AssetLeaseIndexRateType
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Set up index rates

[!include [banner](../includes/banner.md)]

If lease payments depend on an index, the index rate types can be added and maintained in the system. To revalue the lease payments from the **Index rate type** page, the index rate revaluation process uses the most recent index rate from the date of revaluation.

To add index rate types and index rates, follow these steps:

1. Go to **Asset leasing \> Setup \> Index rate type**.
1. Select **New**.
1. Enter the rate type and the name of the index rate in the appropriate fields.
1. To add a new index rate value, select the index rate type, and then select **Add**.
1. Select the effective start date of the rate, and select the rate value.

Select either **Index rate value difference** or **Index rate value** as the index rate method.

- Select the **Index rate value difference** method to calculate a new lease payment, based on the difference between the index rate on the start date and the most recent index rate. Define the index rate in the **Index rate (%)** field.
- Select the **Index rate value** method to calculate the lease payment by using the percentage that you specify in the **Index rate (%)** field.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
