---
# required metadata

title: Set up index rates
description: This topic lists the steps for setting up index rates, which are needed if your organization associates lease payment amounts with a set of index rates.  
author: moaamer
manager: Ann Beebe
ms.date: 07/20/2020
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
ms.search.validFrom: 2020-07-20
ms.dyn365.ops.version: 10.0.13

---

# Set up index rates (Preview)

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

If lease payments are dependent on an index, those index rate types can be added and maintained in the system. To revalue the lease payments from the **Index rate type** page, the index rate revaluation process will use the most recent index rate from the date of revaluation.

1. To add index rate types and index rates, open the **Index rate type** page (**Asset leasing > Setup > Index rate type**).
2. Click **New**. Enter the rate type, and the name of the index rate, in the respective fields.
3. To add a new index rate value, select the index rate type and click **Add**. Select the effective start date of the rate, and the rate value.

You'll need to select the index rate method either **Index rate value difference** or **Index rate value**. Select index rate value difference to calculate a new lease payment based on the difference between the index rate at commencement date and the most recent index rate. The index rate is defined in the **Index rate (%)** field. Select index rate value to calculate the lease payment using the percentage that's specified in the **Index rate (%)** field.
