---
# required metadata

title: Set up index rates
description: This topic explains how to set up index rates. Index rates are required if your organization associates lease payment amounts with a set of index rates.
author: moaamer
ms.date: 04/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetLeaseIndexRateType
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14

---

# Set up index rates

[!include [banner](../includes/banner.md)]

If lease payments depend on an index, the index rate types can be added and maintained in the system. To revalue the lease payments from the **Index rate type** page, the index rate revaluation process uses the most recent index rate from the date of revaluation.

To add index rate types and index rates, follow these steps.

1. Go to **Asset leasing \> Setup \> Index rate type**.
2. Select **New**.
3. In the appropriate fields, enter the rate type and the name of the index rate.
4. To add a new index rate value, select the index rate type, and then select **Add**.
5. Select the effective start date of the rate, and select the rate value.

You must select either **Index rate value difference** or **Index rate value** as the index rate method.

- Select the **Index rate value difference** method to calculate a new lease payment, based on the difference between the index rate on the start date and the most recent index rate. The index rate is defined in the **Index rate (%)** field.
- Select the **Index rate value** method to calculate the lease payment by using the percentage that is specified in the **Index rate (%)** field.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
